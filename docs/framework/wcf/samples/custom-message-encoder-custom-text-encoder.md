---
title: 'Vlastní kodér zpráv: Vlastní kodér textu'
ms.date: 03/30/2017
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
ms.openlocfilehash: 54cba7eb5ff743d4fddc37a824e05a376880d6d9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832317"
---
# <a name="custom-message-encoder-custom-text-encoder"></a>Vlastní kodér zpráv: Vlastní kodér textu
Tento příklad ukazuje, jak implementovat vlastní text kodéru zprávy pomocí služby Windows Communication Foundation (WCF).  
  
> [!WARNING]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`  
  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> Služby WCF podporuje jenom kódování UTF-8, UTF-16 a velké objemy Endean Unicode. Vlastní text v této ukázce podporoval všechny podporované platformy kódování znaků, které mohou být požadovány pro spolupráci. Ukázka se skládá z programu klienta konzoly (.exe), služba knihovny (.dll) hostované v Internetové informační služby (IIS) a text zprávy kodér knihovna (.dll). Služba implementuje kontrakt, který definuje vzor komunikace požadavek odpověď. Smlouva je definován `ICalculator` rozhraní, které zveřejňuje matematických operací (Přidat odečíst, násobení a dělení). Klient podá synchronní žádosti a odpovědi služby s výsledkem dané matematické operace. Klient a služba používá `CustomTextMessageEncoder` místo výchozího <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.  
  
 Implementace vlastní kodér skládá objekt pro vytváření kodéru zpráv, kodéru zprávy, zprávu kódování element vazby a obslužné rutiny konfiguračního a ukazuje následující:  
  
-   Vytváření vlastních encoder a kodér objekt pro vytváření.  
  
-   Vytvořit element vazby pro vlastní kodér.  
  
-   Pomocí konfigurace vlastních vazeb pro integraci elementů vlastní vazby.  
  
-   Vývoj vlastní obslužnou rutinu umožní konfiguraci souboru vlastní prvek vazby.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="message-encoder-factory-and-the-message-encoder"></a>Objekt pro vytváření zpráv Encoder a kodér zprávy  
 Když <xref:System.ServiceModel.ServiceHost> nebo klient otevření kanálu, složku času návrhu `CustomTextMessageBindingElement` vytvoří `CustomTextMessageEncoderFactory`. Vytvoří objekt pro vytváření `CustomTextMessageEncoder`. Kodér zprávy funguje v režim tvorby datového proudu ve vyrovnávací paměti režimu i. Používá <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter> ke čtení a zápisu zprávy v uvedeném pořadí. Na rozdíl od optimalizované XML čtečky a zapisovače služby WCF, které podporují jenom kódování UTF-8, UTF-16 a Big-Endean Unicode podporují tyto čtečky a zapisovače kódování všechny podporované platformy.  
  
 Následující příklad kódu ukazuje, CustomTextMessageEncoder.  
  
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
 Elementy vazby umožňují konfiguraci zásobníku za běhu WCF. Pokud chcete použít vlastní kodér zpráv v aplikaci WCF, je vyžadován element vazby, který vytvoří objekt pro vytváření kodéru zpráv s požadovaným nastavením na příslušné úrovni v zásobníku za běhu.  
  
 `CustomTextMessageBindingElement` Je odvozen od <xref:System.ServiceModel.Channels.BindingElement> základní třídy a dědí z <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> třídy. To umožňuje dalších součástí WCF rozpoznat tento element vazby jako element vazby kódování zprávy. Provádění <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> vrací instanci odpovídající objekt factory kodéru zpráv s požadovaným nastavením.  
  
 `CustomTextMessageBindingElement` Poskytuje nastavení pro `MessageVersion`, `ContentType`, a `Encoding` prostřednictvím vlastnosti. Kodér podporuje Soap11Addressing a Soap12Addressing1 verze. Výchozí hodnota je Soap11Addressing1. Výchozí hodnota `ContentType` je "text/xml". `Encoding` Vlastnost umožňuje nastavit hodnotu požadovaného znaku kódování. Ukázka klient a služba používá kódování ISO-8859-1 (Latin1) znaků, která není podporována <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> služby WCF.  
  
 Následující kód ukazuje, jak prostřednictvím kódu programu vytvořit vazbu pomocí kodéru zpráv vlastní text.  
  
```  
ICollection<BindingElement> bindingElements = new List<BindingElement>();  
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();  
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();  
bindingElements.Add(textBindingElement);  
bindingElements.Add(httpBindingElement);  
CustomBinding binding = new CustomBinding(bindingElements);  
```  
  
## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a>Přidání podpory metadat pro Element vazby kódování zprávy  
 Libovolný typ, který je odvozen od <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> je zodpovědný za automatickou aktualizaci verze vazba SOAP v dokumentu WSDL vygenerovaný pro službu. Uděláte to pomocí implementace `ExportEndpoint` metodu <xref:System.ServiceModel.Description.IWsdlExportExtension> rozhraní a následnou úpravou generovaného WSDL. V této ukázce `CustomTextMessageBindingElement` používá logiky exportu WSDL z `TextMessageEncodingBinidngElement`.  
  
 Konfigurace klienta pro tuto ukázku je ručně nakonfigurovat. Nelze pomocí Svcutil.exe lze generovat konfiguraci klienta, protože `CustomTextMessageBindingElement` neexportuje kontrolní výraz zásad popsat její chování. Obecně by měly implementovat <xref:System.ServiceModel.Description.IPolicyExportExtension> rozhraní na vlastní prvek vazby pro export kontrolní výraz vlastní zásadu, která popisuje chování nebo funkce implementované element vazby. Příklad toho, jak exportovat kontrolní výraz zásad pro vlastní prvek vazby, najdete v článku [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) vzorku.  
  
## <a name="message-encoding-binding-configuration-handler"></a>Obslužné rutiny konfiguračního vazby kódování zprávy  
 V předchozím oddílu ukazuje, jak používat vlastní text kodér zprávy prostřednictvím kódu programu. `CustomTextMessageEncodingBindingSection` Implementuje konfigurace obslužnou rutinu, která vám umožní určit pomocí kodéru vlastní textové zprávy v konfiguračním souboru. `CustomTextMessageEncodingBindingSection` Třída odvozena z <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> třídy. `BindingElementType` Vlastnost informuje systém konfigurace typ elementu vazby k vytvoření této části.  
  
 Všechna nastavení definované `CustomTextMessageBindingElement` jsou vystaveny jako vlastnosti `CustomTextMessageEncodingBindingSection`. <xref:System.Configuration.ConfigurationPropertyAttribute> Pomáhá při mapování atributů elementu konfigurace vlastností a nastavení výchozí hodnoty, pokud není nastaven atribut. Po hodnoty z konfigurace jsou načítány a použity pro vlastnosti typu, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> metoda je volána, který převede na konkrétní instance elementu vazby vlastnosti.  
  
 Tato obslužná rutina konfigurace mapuje následující reprezentaci v souboru App.config nebo Web.config pro službu nebo klienta.  
  
```xml  
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />  
```  
  
 Ukázka používá kódování ISO-8859-1.  
  
 Použití této konfigurace obslužné rutiny, které musí být registrována pomocí následující element konfigurace.  
  
```xml  
<extensions>  
    <bindingElementExtensions>  
        <add name="customTextMessageEncoding" type="   
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection,   
                  CustomTextMessageEncoder" />  
    </bindingElementExtensions>  
</extensions>  
```  
  
