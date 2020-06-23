---
title: 'Vlastní kodér zpráv: Vlastní kodér textu'
description: Pomocí této ukázky můžete implementovat vlastní kodér textových zpráv pomocí WCF. Tento kodér podporuje všechna kódování znaků podporovaná platformou pro interoperabilitu.
ms.date: 03/30/2017
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
ms.openlocfilehash: 88ddc79e6cc1df654aea851cedb0e60c6fbcd017
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246269"
---
# <a name="custom-message-encoder-custom-text-encoder"></a>Vlastní kodér zpráv: Vlastní kodér textu

Tato ukázka předvádí, jak implementovat vlastní kodér textových zpráv pomocí Windows Communication Foundation (WCF).

> [!WARNING]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`

<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>Technologie WCF podporuje pouze kódování UTF-8, UTF-16 a big-endian Unicode. Kodér pro vlastní textovou zprávu v této ukázce podporuje všechna kódování znaků podporovaná platformou, která se můžou vyžadovat pro interoperabilitu. Ukázka se skládá z programu klientské konzoly (. exe), knihovny služeb (. dll) hostované službou Internetová informační služba (IIS) a knihovnou kodéru textové zprávy (. dll). Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď. Kontrakt je definován `ICalculator` rozhraním, které zpřístupňuje matematické operace (sčítání, odčítání, násobení a dělení). Klient provádí synchronní požadavky na určitou matematickou operaci a služba odpovídá výsledku. Klient i služba používají `CustomTextMessageEncoder` místo výchozího <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> .

Implementace vlastního kodéru se skládá z objektu pro vytváření kodéru zpráv, kodér zprávy, elementu vazby kódování zprávy a obslužné rutiny konfigurace a znázorňuje následující:

- Vytváření vlastního kodéru a továrny kodéru

- Vytvoření prvku vazby pro vlastní kodér.

- Použití vlastní konfigurace vazeb pro integraci vlastních elementů vazby.

- Vývoj vlastní obslužné rutiny konfigurace umožňující konfiguraci souboru vlastního elementu vazby.

## <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Pomocí následujícího příkazu nainstalujte ASP.NET 4,0.

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).

3. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).

4. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).

## <a name="message-encoder-factory-and-the-message-encoder"></a>Objekt pro vytváření a kodér zpráv

Když <xref:System.ServiceModel.ServiceHost> je otevřen kanál klienta nebo, komponenta čas návrhu `CustomTextMessageBindingElement` vytvoří `CustomTextMessageEncoderFactory` . Továrna vytvoří `CustomTextMessageEncoder` . Kodér zpráv funguje v režimu streamování i v režimu vyrovnávací paměti. Používá <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter> ke čtení a zápisu zpráv v uvedeném pořadí. Na rozdíl od optimalizovaných čtecích zařízení XML a zapisovačů WCF podporujících jenom UTF-8, UTF-16 a big-endian Unicode tyto čtečky a zapisovače podporují všechna kódování podporovaná platformou.

Následující příklad kódu ukazuje CustomTextMessageEncoder.

```csharp
public class CustomTextMessageEncoder : MessageEncoder
{
    private CustomTextMessageEncoderFactory factory;
    private XmlWriterSettings writerSettings;
    private string contentType;

    public CustomTextMessageEncoder(CustomTextMessageEncoderFactory factory)
    {
        this.factory = factory;

        this.writerSettings = new XmlWriterSettings();
        this.writerSettings.Encoding = Encoding.GetEncoding(factory.CharSet);
        this.contentType = $"{this.factory.MediaType}; charset={this.writerSettings.Encoding.HeaderName}";
    }

    public override string ContentType
    {
        get
        {
            return this.contentType;
        }
    }

    public override string MediaType
    {
        get
        {
            return factory.MediaType;
        }
    }

    public override MessageVersion MessageVersion
    {
        get
        {
            return this.factory.MessageVersion;
        }
    }

    public override Message ReadMessage(ArraySegment<byte> buffer, BufferManager bufferManager, string contentType)
    {
        byte[] msgContents = new byte[buffer.Count];
        Array.Copy(buffer.Array, buffer.Offset, msgContents, 0, msgContents.Length);
        bufferManager.ReturnBuffer(buffer.Array);

        MemoryStream stream = new MemoryStream(msgContents);
        return ReadMessage(stream, int.MaxValue);
    }

    public override Message ReadMessage(Stream stream, int maxSizeOfHeaders, string contentType)
    {
        XmlReader reader = XmlReader.Create(stream);
        return Message.CreateMessage(reader, maxSizeOfHeaders, this.MessageVersion);
    }

    public override ArraySegment<byte> WriteMessage(Message message, int maxMessageSize, BufferManager bufferManager, int messageOffset)
    {
        MemoryStream stream = new MemoryStream();
        XmlWriter writer = XmlWriter.Create(stream, this.writerSettings);
        message.WriteMessage(writer);
        writer.Close();

        byte[] messageBytes = stream.GetBuffer();
        int messageLength = (int)stream.Position;
        stream.Close();

        int totalLength = messageLength + messageOffset;
        byte[] totalBytes = bufferManager.TakeBuffer(totalLength);
        Array.Copy(messageBytes, 0, totalBytes, messageOffset, messageLength);

        ArraySegment<byte> byteArray = new ArraySegment<byte>(totalBytes, messageOffset, messageLength);
        return byteArray;
    }

    public override void WriteMessage(Message message, Stream stream)
    {
        XmlWriter writer = XmlWriter.Create(stream, this.writerSettings);
        message.WriteMessage(writer);
        writer.Close();
    }
}
```

Následující příklad kódu ukazuje, jak vytvořit objekt pro vytváření kodéru zpráv.

```csharp
public class CustomTextMessageEncoderFactory : MessageEncoderFactory
{
    private MessageEncoder encoder;
    private MessageVersion version;
    private string mediaType;
    private string charSet;

    internal CustomTextMessageEncoderFactory(string mediaType, string charSet,
        MessageVersion version)
    {
        this.version = version;
        this.mediaType = mediaType;
        this.charSet = charSet;
        this.encoder = new CustomTextMessageEncoder(this);
    }

    public override MessageEncoder Encoder
    {
        get
        {
            return this.encoder;
        }
    }

    public override MessageVersion MessageVersion
    {
        get
        {
            return this.version;
        }
    }

    internal string MediaType
    {
        get
        {
            return this.mediaType;
        }
    }

    internal string CharSet
    {
        get
        {
            return this.charSet;
        }
    }
}
```

## <a name="message-encoding-binding-element"></a>Element vazby kódování zprávy

Prvky vazby umožňují konfiguraci zásobníku run-time služby WCF. Chcete-li použít vlastní kodér zpráv v aplikaci WCF, je vyžadován prvek vazby, který vytvoří objekt pro vytváření kodéru zpráv s odpovídajícím nastavením na příslušné úrovni v zásobníku run-time.

Je `CustomTextMessageBindingElement` odvozen ze <xref:System.ServiceModel.Channels.BindingElement> základní třídy a dědí z <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> třídy. To umožňuje jiným komponentám WCF rozpoznat tento prvek vazby jako prvek vazby kódování zprávy. Implementace <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> vrátí instanci odpovídajícího objektu pro vytváření kodéru zpráv s příslušným nastavením.

`CustomTextMessageBindingElement`Zpřístupňuje nastavení pro `MessageVersion` , `ContentType` a `Encoding` prostřednictvím vlastností. Kodér podporuje verze Soap11Addressing i Soap12Addressing1. Výchozí hodnota je Soap11Addressing1. Výchozí hodnota `ContentType` je "text/XML". `Encoding`Vlastnost umožňuje nastavit hodnotu požadovaného kódování znaků. Ukázkový klient a služba používá kódování znaků ISO-8859-1 (Latin1), které není podporováno službou <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> WCF.

Následující kód ukazuje, jak programově vytvořit vazbu pomocí vlastního kodéru textových zpráv.

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();
bindingElements.Add(textBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
```

## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a>Přidání podpory metadat k elementu vazby kódování zprávy

Jakýkoli typ, který je odvozen z, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> je zodpovědný za aktualizaci verze vazby SOAP v dokumentu WSDL vygenerovaného pro službu. To se provádí implementací `ExportEndpoint` metody na <xref:System.ServiceModel.Description.IWsdlExportExtension> rozhraní a následným úpravou vygenerovaného WSDL. V této ukázce `CustomTextMessageBindingElement` používá exportní LOGIKU WSDL z `TextMessageEncodingBindingElement` .

V této ukázce je konfigurace klienta konfigurována ručně. Nemůžete použít Svcutil.exe k vygenerování konfigurace klienta, protože `CustomTextMessageBindingElement` neexportuje kontrolní výraz zásady pro popsání jeho chování. Obecně byste měli implementovat <xref:System.ServiceModel.Description.IPolicyExportExtension> rozhraní na vlastní element vazby pro export kontrolního výrazu vlastní zásady, který popisuje chování nebo funkci implementovanou prvkem vazby. Příklad exportu kontrolního výrazu zásady pro vlastní prvek vazby naleznete v ukázce [Transport: UDP](transport-udp.md) .

## <a name="message-encoding-binding-configuration-handler"></a>Obslužná rutina konfigurace vazby kódování zprávy
V předchozí části se dozvíte, jak programově používat vlastní kodér textových zpráv. `CustomTextMessageEncodingBindingSection`Implementuje obslužnou rutinu konfigurace, která umožňuje určit použití vlastního kodéru textových zpráv v rámci konfiguračního souboru. `CustomTextMessageEncodingBindingSection`Třída je odvozena z <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> třídy. `BindingElementType`Vlastnost informuje konfigurační systém typu elementu vazby, který má být pro tento oddíl vytvořen.

Všechna nastavení definovaná nástrojem `CustomTextMessageBindingElement` jsou vystavena jako vlastnosti v `CustomTextMessageEncodingBindingSection` . <xref:System.Configuration.ConfigurationPropertyAttribute>Pomoc při mapování atributů elementů konfigurace na vlastnosti a nastavení výchozích hodnot, pokud atribut není nastaven. Poté, co jsou hodnoty z konfigurace načteny a aplikovány na vlastnosti typu, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> je volána metoda, která převede vlastnosti na konkrétní instanci elementu vazby.

Tato obslužná rutina konfigurace mapuje následující reprezentace v App.config nebo Web.config pro službu nebo klienta.

```xml
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />
```

Ukázka používá kódování ISO-8859-1.

Chcete-li použít tuto obslužnou rutinu konfigurace, musí být zaregistrována pomocí následujícího konfiguračního prvku.

```xml
<extensions>
    <bindingElementExtensions>
        <add name="customTextMessageEncoding" type="
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection,
                  CustomTextMessageEncoder" />
    </bindingElementExtensions>
</extensions>
```
