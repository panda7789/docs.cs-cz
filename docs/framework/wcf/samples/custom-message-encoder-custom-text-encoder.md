---
title: 'Vlastní kodér zpráv: Vlastní kodér textu'
ms.date: 03/30/2017
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
ms.openlocfilehash: 88aeeb4f1d09795b768441d2a572d959f27e0226
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145108"
---
# <a name="custom-message-encoder-custom-text-encoder"></a>Vlastní kodér zpráv: Vlastní kodér textu

Tato ukázka ukazuje, jak implementovat vlastní kodér textových zpráv pomocí Windows Communication Foundation (WCF).

> [!WARNING]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`

WCF <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> podporuje pouze Kódování Unicode UTF-8, UTF-16 a big-endian. Kodér vlastních textových zpráv v této ukázce podporuje všechna kódování znaků podporovaná platformou, která mohou být vyžadována pro interoperabilitu. Ukázka se skládá z programu klientské konzole (.exe), knihovny služeb (.dll) hostované Internetovou informační službou (IIS) a knihovny kodérů textových zpráv (.dll). Služba implementuje smlouvu, která definuje vzor komunikace požadavek odpověď. Kontrakt je definován `ICalculator` rozhraním, které zpřístupňuje matematické operace (Přidat, Odečíst, Násobit a Rozdělit). Klient provádí synchronní požadavky na danou operaci matematiky a odpovědi služby s výsledkem. Klient i služba `CustomTextMessageEncoder` používá místo <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>výchozí .

Vlastní implementace kodéru se skládá z továrny kodéru zpráv, kodéru zpráv, prvku vazby kódování zpráv a obslužné rutiny konfigurace a ukazuje následující:

- Vytvoření zakázkové továrny na kodér a kodér.

- Vytvoření prvku vazby pro vlastní kodér.

- Použití vlastní konfigurace vazby pro integraci vlastních prvků vazby.

- Vývoj vlastní obslužné rutiny konfigurace umožňující konfiguraci souboru prvku vlastní vazby.

## <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Nainstalujte ASP.NET 4.0 pomocí následujícího příkazu.

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

3. Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

## <a name="message-encoder-factory-and-the-message-encoder"></a>Továrna kodéru zpráv a kodér zpráv

Při <xref:System.ServiceModel.ServiceHost> otevření kanálu nebo klienta vytvoří `CustomTextMessageBindingElement` součást `CustomTextMessageEncoderFactory`času návrhu . Factory vytvoří `CustomTextMessageEncoder`. Kodér zpráv pracuje jak v režimu streamování, tak v režimu ve vyrovnávací paměti. Používá <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter> číst a psát zprávy v uvedeném pořadí. Na rozdíl od optimalizovaných čteček XML a zapisovačů WCF, které podporují pouze UTF-8, UTF-16 a big-endian Unicode, tyto čtečky a spisovatelé podporují všechny kódování podporované platformou.

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

Následující příklad kódu ukazuje, jak vytvořit továrnu kodéru zpráv.

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

## <a name="message-encoding-binding-element"></a>Element vazby kódování zpráv

Elementy vazby umožňují konfiguraci zásobníku wcf za běhu. Chcete-li použít vlastní kodér zpráv v aplikaci WCF, je vyžadován element vazby, který vytvoří továrnu kodérů zpráv s příslušným nastavením na příslušné úrovni v zásobníku za běhu.

Odvozuje `CustomTextMessageBindingElement` ze <xref:System.ServiceModel.Channels.BindingElement> základní třídy a <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> dědí z třídy. To umožňuje ostatním komponentám WCF rozpoznat tento element vazby jako prvek vazby kódování zpráv. Implementace <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> vrátí instanci továrny odpovídající hoké kodéru zpráv s příslušným nastavením.

Zpřístupňuje `CustomTextMessageBindingElement` nastavení `MessageVersion` `ContentType`pro `Encoding` , a prostřednictvím vlastností. Kodér podporuje verze Soap11Addressing a Soap12Addressing1. Výchozí hodnota je Soap11Addressing1. Výchozí hodnota `ContentType` je "text/xml". Vlastnost `Encoding` umožňuje nastavit hodnotu požadovaného kódování znaků. Ukázkový klient a služba používá kódování znaků ISO-8859-1 (Latin1), <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> které wcf nepodporuje.

Následující kód ukazuje, jak programově vytvořit vazbu pomocí vlastního kodéru textových zpráv.

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();
bindingElements.Add(textBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
```

## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a>Přidání podpory metadat do prvku vazby kódování zpráv

Jakýkoli typ, který <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> je odvozen od je zodpovědný za aktualizaci verze soap vazby v dokumentu WSDL generované pro službu. To se provádí implementací `ExportEndpoint` <xref:System.ServiceModel.Description.IWsdlExportExtension> metody na rozhraní a potom úpravou generované WSDL. V této ukázce `CustomTextMessageBindingElement` používá logiku `TextMessageEncodingBindingElement`exportu WSDL z .

Pro tuto ukázku je konfigurace klienta ručně nakonfigurována. Svcutil.exe nelze použít ke generování konfigurace `CustomTextMessageBindingElement` klienta, protože neexportuje kontrolní výraz zásady k popisu jeho chování. Obecně byste měli <xref:System.ServiceModel.Description.IPolicyExportExtension> implementovat rozhraní na vlastní prvek vazby exportovat vlastní kontrolní výraz zásady, který popisuje chování nebo schopnosti implementované elementem vazby. Příklad, jak exportovat kontrolní výraz zásady pro vlastní prvek vazby, naleznete v části [Transport: UDP.](../../../../docs/framework/wcf/samples/transport-udp.md)

## <a name="message-encoding-binding-configuration-handler"></a>Obslužná rutina konfigurace vazby kódování zpráv
V předchozí části se ukazuje, jak používat vlastní kód textové zprávy programově. Implementuje `CustomTextMessageEncodingBindingSection` obslužnou rutinu konfigurace, která umožňuje určit použití vlastního kodéru textových zpráv v konfiguračním souboru. Třída `CustomTextMessageEncodingBindingSection` je odvozena <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> od třídy. Vlastnost `BindingElementType` informuje konfigurační systém o typu prvku vazby, který má být pro tuto část vytvořit.

Všechna nastavení definovaná `CustomTextMessageBindingElement` písmenem jsou vystaveny `CustomTextMessageEncodingBindingSection`jako vlastnosti v rozhraní . Pomáhá <xref:System.Configuration.ConfigurationPropertyAttribute> při mapování atributů konfiguračního prvku na vlastnosti a nastavení výchozích hodnot, pokud atribut není nastaven. Po hodnoty z konfigurace jsou načteny a použity <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> na vlastnosti typu, metoda je volána, která převede vlastnosti na konkrétní instance prvku vazby.

Tato obslužná rutina konfigurace se mapuje na následující reprezentaci v souboru App.config nebo Web.config pro službu nebo klienta.

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
