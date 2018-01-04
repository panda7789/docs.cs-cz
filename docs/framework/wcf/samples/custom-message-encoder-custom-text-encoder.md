---
title: "Vlastní kodér zpráv: Vlastní kodér textu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54e2b87a9e104ea61c32b06ffc604fc864283f3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="custom-message-encoder-custom-text-encoder"></a>Vlastní kodér zpráv: Vlastní kodér textu
Tento příklad ukazuje, jak implementovat pomocí kodéru zprávy vlastní text [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
> [!WARNING]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`  
  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podporuje jenom kódování UTF-8, UTF-16 a Big Endean Unicode. Kodér zpráv vlastní text v této ukázce podporuje všechny podporované platformy kódování znaků, které mohou být potřebné pro spolupráci. Ukázka se skládá z klientské konzoly program (.exe), služba knihovny (DLL) hostované Internetové informační služby (IIS) a text zprávy kodér knihovny (DLL). Služba se implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi. Kontrakt je definována `ICalculator` rozhraní, která zpřístupňuje matematické operace (přidat, odečíst, násobit a dělit). Klient podá synchronní požadavky a odpovědi služby s výsledkem dané matematické operace. Klient a služba používá `CustomTextMessageEncoder` místo výchozího <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.  
  
 Implementace vlastní kodér se skládá z objekt kodér zpráv, kodéru zprávy, zprávu kódování prvku vazby a obslužnou rutinu konfigurace a ukazuje následující:  
  
-   Vytváření vlastní kodér a kodér objekt pro vytváření.  
  
-   Vytváření pro vlastní kodér prvku vazby.  
  
-   Pomocí konfigurace vlastních vazeb pro integraci prvky vlastní vazby.  
  
-   Vývoj vlastní konfigurace obslužná rutina umožní konfiguraci souboru elementu vlastní vazby.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="message-encoder-factory-and-the-message-encoder"></a>Zpráva kodér tovární nastavení a kodér zpráv  
 Když <xref:System.ServiceModel.ServiceHost> nebo klienta otevření kanálu, komponentu dobu návrhu `CustomTextMessageBindingElement` vytvoří `CustomTextMessageEncoderFactory`. Vytvoří objekt factory `CustomTextMessageEncoder`. Kodér zpráv pracuje v režimu datového i režim s vyrovnávací pamětí. Použije <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter> číst a zapisovat zprávy v uvedeném pořadí. Oproti optimalizované XML čtení a zápis z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podporující pouze ve formátu UTF-8, UTF-16 a Big-Endean Unicode tyto čtečky a zapisovače podporují všechny kódování podporovaná platforma.  
  
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
        this.contentType = string.Format("{0}; charset={1}",   
            this.factory.MediaType, this.writerSettings.Encoding.HeaderName);  
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
  
 Následující příklad kódu ukazuje, jak vytvořit objekt pro vytváření kodér zpráv.  
  
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
 Prvky vazeb povolit konfiguraci [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] běhu zásobníku. Použít vlastní kodér zpráv v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace, prvku vazby je vyžadována, vytvoří objekt factory kodér zpráv s požadovaným nastavením na příslušné úrovni v zásobníku spuštění.  
  
 `CustomTextMessageBindingElement` Je odvozena z <xref:System.ServiceModel.Channels.BindingElement> základní třídy a dědí z <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> třídy. To umožňuje dalších [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] součásti, které uznává tento element vazby jako zprávu kódování prvku vazby. Implementace <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> vrátí instanci objektu pro vytváření odpovídající kodér zpráv s požadovaným nastavením.  
  
 `CustomTextMessageBindingElement` Se zobrazí nastavení pro `MessageVersion`, `ContentType`, a `Encoding` prostřednictvím vlastnosti. Kodér podporuje verze Soap11Addressing a Soap12Addressing1. Výchozí hodnota je Soap11Addressing1. Výchozí hodnota `ContentType` je "text/xml". `Encoding` Vlastnost můžete nastavit hodnotu kódování požadované znaků. Ukázka klient a služba používá kódování ISO 8859-1 (Latin1) znaků, který není podporována <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Následující kód ukazuje, jak programově vytvořit vazbu pomocí kodéru zpráv vlastní text.  
  
```  
ICollection<BindingElement> bindingElements = new List<BindingElement>();  
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();  
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();  
bindingElements.Add(textBindingElement);  
bindingElements.Add(httpBindingElement);  
CustomBinding binding = new CustomBinding(bindingElements);  
```  
  
## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a>Přidání podpory Metadata do zprávy kódování vazby – Element  
 Žádný typ, který je odvozen od <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> je zodpovědný za aktualizace na verzi protokolu SOAP vazby v dokumentu WSDL vygenerovaný pro službu. K tomu je potřeba implementace `ExportEndpoint` metodu <xref:System.ServiceModel.Description.IWsdlExportExtension> rozhraní a pak úprava generovaného WSDL. V této ukázce `CustomTextMessageBindingElement` používá logice WSDL export z `TextMessageEncodingBinidngElement`.  
  
 Tato ukázka je konfigurace klienta ručně nakonfigurovat. Svcutil.exe nelze použít ke generování konfigurace klienta, protože `CustomTextMessageBindingElement` neexportuje výraz zásad k popisu své chování. Měli byste obecně implementovat <xref:System.ServiceModel.Description.IPolicyExportExtension> rozhraní na element vlastní vazby pro export assertion vlastní zásadu, která popisuje chování nebo funkce, které jsou implementované prvku vazby. Příklad toho, jak exportovat výraz zásad pro element vlastní vazby, naleznete v části [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) ukázka.  
  
## <a name="message-encoding-binding-configuration-handler"></a>Obslužná rutina konfigurace vazby kódování zprávy  
 V předchozí části ukazuje, jak použít kodér zpráv vlastní text prostřednictvím kódu programu. `CustomTextMessageEncodingBindingSection` Implementuje konfigurace obslužná rutina, která vám umožní určit použití kodéru zprávy vlastní text v konfiguračním souboru. `CustomTextMessageEncodingBindingSection` Třída odvozená z <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> třídy. `BindingElementType` Vlastnost informuje konfigurační systém typu vazby elementu, který chcete vytvořit pro tento oddíl.  
  
 Všechna nastavení definované `CustomTextMessageBindingElement` jsou zveřejněné jako vlastnosti v `CustomTextMessageEncodingBindingSection`. <xref:System.Configuration.ConfigurationPropertyAttribute> Pomáhá v mapování atributy prvků konfigurace pro vlastnosti a nastavení výchozí hodnoty, pokud není nastavený atribut. Po hodnoty z konfigurace načíst a použít pro vlastnosti typu, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> metoda je volána, který převede vlastnosti na konkrétní instanci prvku vazby.  
  
 Tato obslužná rutina konfigurace mapuje následující reprezentace v souboru App.config nebo Web.config pro službu nebo klienta.  
  
```xml  
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />  
```  
  
 Příklad používá kódování ISO 8859-1.  
  
 K použití této konfigurace obslužné rutiny, které musí být zaregistrován pomocí následující konfigurace elementu.  
  
```xml  
<extensions>  
    <bindingElementExtensions>  
        <add name="customTextMessageEncoding" type="   
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection,   
                  CustomTextMessageEncoder" />  
    </bindingElementExtensions>  
</extensions>  
```  
  
## <a name="see-also"></a>Viz také
