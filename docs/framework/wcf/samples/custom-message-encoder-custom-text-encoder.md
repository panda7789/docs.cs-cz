---
title: 'Vlastní kodér zpráv: Vlastní kodér textu'
ms.date: 03/30/2017
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
ms.openlocfilehash: aeb1690d7ead9116bd9c4afe3c64d65d8f51ad50
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43800690"
---
# <a name="custom-message-encoder-custom-text-encoder"></a><span data-ttu-id="8be82-102">Vlastní kodér zpráv: Vlastní kodér textu</span><span class="sxs-lookup"><span data-stu-id="8be82-102">Custom Message Encoder: Custom Text Encoder</span></span>
<span data-ttu-id="8be82-103">Tento příklad ukazuje, jak implementovat vlastní text kodéru zprávy pomocí služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="8be82-103">This sample demonstrates how to implement a custom text message encoder using Windows Communication Foundation (WCF).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="8be82-104">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="8be82-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8be82-105">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="8be82-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8be82-106">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="8be82-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8be82-107">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="8be82-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`  
  
 <span data-ttu-id="8be82-108"><xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> Služby WCF podporuje jenom kódování UTF-8, UTF-16 a velké objemy Endean Unicode.</span><span class="sxs-lookup"><span data-stu-id="8be82-108">The <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of WCF supports only the UTF-8, UTF-16 and Big Endean Unicode encodings.</span></span> <span data-ttu-id="8be82-109">Vlastní text v této ukázce podporoval všechny podporované platformy kódování znaků, které mohou být požadovány pro spolupráci.</span><span class="sxs-lookup"><span data-stu-id="8be82-109">The custom text message encoder in this sample supports all platform-supported character encoding that may be required for interoperability.</span></span> <span data-ttu-id="8be82-110">Ukázka se skládá z programu klienta konzoly (.exe), služba knihovny (.dll) hostované v Internetové informační služby (IIS) a text zprávy kodér knihovna (.dll).</span><span class="sxs-lookup"><span data-stu-id="8be82-110">The sample consists of a client console program (.exe), a service library (.dll) hosted by Internet Information Services (IIS) and a text message encoder library (.dll).</span></span> <span data-ttu-id="8be82-111">Služba implementuje kontrakt, který definuje vzor komunikace požadavek odpověď.</span><span class="sxs-lookup"><span data-stu-id="8be82-111">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="8be82-112">Smlouva je definován `ICalculator` rozhraní, které zveřejňuje matematických operací (Přidat odečíst, násobení a dělení).</span><span class="sxs-lookup"><span data-stu-id="8be82-112">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="8be82-113">Klient podá synchronní žádosti a odpovědi služby s výsledkem dané matematické operace.</span><span class="sxs-lookup"><span data-stu-id="8be82-113">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="8be82-114">Klient a služba používá `CustomTextMessageEncoder` místo výchozího <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="8be82-114">Both client and service uses the `CustomTextMessageEncoder` instead of the default <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span>  
  
 <span data-ttu-id="8be82-115">Implementace vlastní kodér skládá objekt pro vytváření kodéru zpráv, kodéru zprávy, zprávu kódování element vazby a obslužné rutiny konfiguračního a ukazuje následující:</span><span class="sxs-lookup"><span data-stu-id="8be82-115">The custom encoder implementation consists of a message encoder factory, a message encoder, a message encoding binding element and a configuration handler, and demonstrates the following:</span></span>  
  
-   <span data-ttu-id="8be82-116">Vytváření vlastních encoder a kodér objekt pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="8be82-116">Building a custom encoder and encoder factory.</span></span>  
  
-   <span data-ttu-id="8be82-117">Vytvořit element vazby pro vlastní kodér.</span><span class="sxs-lookup"><span data-stu-id="8be82-117">Creating a binding element for a custom encoder.</span></span>  
  
-   <span data-ttu-id="8be82-118">Pomocí konfigurace vlastních vazeb pro integraci elementů vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="8be82-118">Using the custom binding configuration for integrating custom binding elements.</span></span>  
  
-   <span data-ttu-id="8be82-119">Vývoj vlastní obslužnou rutinu umožní konfiguraci souboru vlastní prvek vazby.</span><span class="sxs-lookup"><span data-stu-id="8be82-119">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8be82-120">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="8be82-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="8be82-121">Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="8be82-121">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="8be82-122">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8be82-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="8be82-123">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8be82-123">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="8be82-124">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8be82-124">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="message-encoder-factory-and-the-message-encoder"></a><span data-ttu-id="8be82-125">Objekt pro vytváření zpráv Encoder a kodér zprávy</span><span class="sxs-lookup"><span data-stu-id="8be82-125">Message Encoder Factory and the Message Encoder</span></span>  
 <span data-ttu-id="8be82-126">Když <xref:System.ServiceModel.ServiceHost> nebo klient otevření kanálu, složku času návrhu `CustomTextMessageBindingElement` vytvoří `CustomTextMessageEncoderFactory`.</span><span class="sxs-lookup"><span data-stu-id="8be82-126">When the <xref:System.ServiceModel.ServiceHost> or the client channel is opened, the design time component `CustomTextMessageBindingElement` creates the `CustomTextMessageEncoderFactory`.</span></span> <span data-ttu-id="8be82-127">Vytvoří objekt pro vytváření `CustomTextMessageEncoder`.</span><span class="sxs-lookup"><span data-stu-id="8be82-127">The factory creates the `CustomTextMessageEncoder`.</span></span> <span data-ttu-id="8be82-128">Kodér zprávy funguje v režim tvorby datového proudu ve vyrovnávací paměti režimu i.</span><span class="sxs-lookup"><span data-stu-id="8be82-128">The message encoder operates both in the streaming mode and the buffered mode.</span></span> <span data-ttu-id="8be82-129">Používá <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter> ke čtení a zápisu zprávy v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="8be82-129">It uses the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to read and write the messages respectively.</span></span> <span data-ttu-id="8be82-130">Na rozdíl od optimalizované XML čtečky a zapisovače služby WCF, které podporují jenom kódování UTF-8, UTF-16 a Big-Endean Unicode podporují tyto čtečky a zapisovače kódování všechny podporované platformy.</span><span class="sxs-lookup"><span data-stu-id="8be82-130">As opposed to the optimized XML readers and writers of WCF that support only UTF-8, UTF-16 and Big-Endean Unicode these readers and writers support all platform supported encoding.</span></span>  
  
 <span data-ttu-id="8be82-131">Následující příklad kódu ukazuje, CustomTextMessageEncoder.</span><span class="sxs-lookup"><span data-stu-id="8be82-131">The following code example shows the CustomTextMessageEncoder.</span></span>  
  
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
  
 <span data-ttu-id="8be82-132">Následující příklad kódu ukazuje, jak vytvořit objekt pro vytváření kodéru zpráv.</span><span class="sxs-lookup"><span data-stu-id="8be82-132">The following code example shows how to build the message encoder factory.</span></span>  
  
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
  
## <a name="message-encoding-binding-element"></a><span data-ttu-id="8be82-133">Element vazby kódování zprávy</span><span class="sxs-lookup"><span data-stu-id="8be82-133">Message Encoding Binding Element</span></span>  
 <span data-ttu-id="8be82-134">Elementy vazby umožňují konfiguraci zásobníku za běhu WCF.</span><span class="sxs-lookup"><span data-stu-id="8be82-134">The binding elements allow the configuration of the WCF run-time stack.</span></span> <span data-ttu-id="8be82-135">Pokud chcete použít vlastní kodér zpráv v aplikaci WCF, je vyžadován element vazby, který vytvoří objekt pro vytváření kodéru zpráv s požadovaným nastavením na příslušné úrovni v zásobníku za běhu.</span><span class="sxs-lookup"><span data-stu-id="8be82-135">To use the custom message encoder in a WCF application, a binding element is required that creates the message encoder factory with the appropriate settings at the appropriate level in the run-time stack.</span></span>  
  
 <span data-ttu-id="8be82-136">`CustomTextMessageBindingElement` Je odvozen od <xref:System.ServiceModel.Channels.BindingElement> základní třídy a dědí z <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="8be82-136">The `CustomTextMessageBindingElement` derives from the <xref:System.ServiceModel.Channels.BindingElement> base class and inherits from the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> class.</span></span> <span data-ttu-id="8be82-137">To umožňuje dalších součástí WCF rozpoznat tento element vazby jako element vazby kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="8be82-137">This allows other WCF components to recognize this binding element as being a message encoding binding element.</span></span> <span data-ttu-id="8be82-138">Provádění <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> vrací instanci odpovídající objekt factory kodéru zpráv s požadovaným nastavením.</span><span class="sxs-lookup"><span data-stu-id="8be82-138">The implementation of <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> returns an instance of the matching message encoder factory with appropriate settings.</span></span>  
  
 <span data-ttu-id="8be82-139">`CustomTextMessageBindingElement` Poskytuje nastavení pro `MessageVersion`, `ContentType`, a `Encoding` prostřednictvím vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8be82-139">The `CustomTextMessageBindingElement` exposes settings for `MessageVersion`, `ContentType`, and `Encoding` through properties.</span></span> <span data-ttu-id="8be82-140">Kodér podporuje Soap11Addressing a Soap12Addressing1 verze.</span><span class="sxs-lookup"><span data-stu-id="8be82-140">The encoder supports both Soap11Addressing and Soap12Addressing1 versions.</span></span> <span data-ttu-id="8be82-141">Výchozí hodnota je Soap11Addressing1.</span><span class="sxs-lookup"><span data-stu-id="8be82-141">The default is Soap11Addressing1.</span></span> <span data-ttu-id="8be82-142">Výchozí hodnota `ContentType` je "text/xml".</span><span class="sxs-lookup"><span data-stu-id="8be82-142">The default value of the `ContentType` is "text/xml".</span></span> <span data-ttu-id="8be82-143">`Encoding` Vlastnost umožňuje nastavit hodnotu požadovaného znaku kódování.</span><span class="sxs-lookup"><span data-stu-id="8be82-143">The `Encoding` property allows you to set the value of the desired character encoding.</span></span> <span data-ttu-id="8be82-144">Ukázka klient a služba používá kódování ISO-8859-1 (Latin1) znaků, která není podporována <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> služby WCF.</span><span class="sxs-lookup"><span data-stu-id="8be82-144">The sample client and service uses the ISO-8859-1 (Latin1) character encoding, which is not supported by the <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of WCF.</span></span>  
  
 <span data-ttu-id="8be82-145">Následující kód ukazuje, jak prostřednictvím kódu programu vytvořit vazbu pomocí kodéru zpráv vlastní text.</span><span class="sxs-lookup"><span data-stu-id="8be82-145">The following code shows how to programmatically create the binding using the custom text message encoder.</span></span>  
  
```  
ICollection<BindingElement> bindingElements = new List<BindingElement>();  
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();  
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();  
bindingElements.Add(textBindingElement);  
bindingElements.Add(httpBindingElement);  
CustomBinding binding = new CustomBinding(bindingElements);  
```  
  
## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a><span data-ttu-id="8be82-146">Přidání podpory metadat pro Element vazby kódování zprávy</span><span class="sxs-lookup"><span data-stu-id="8be82-146">Adding Metadata Support to the Message Encoding Binding Element</span></span>  
 <span data-ttu-id="8be82-147">Libovolný typ, který je odvozen od <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> je zodpovědný za automatickou aktualizaci verze vazba SOAP v dokumentu WSDL vygenerovaný pro službu.</span><span class="sxs-lookup"><span data-stu-id="8be82-147">Any type that derives from <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> is responsible for updating the version of the SOAP binding in the WSDL document generated for the service.</span></span> <span data-ttu-id="8be82-148">Uděláte to pomocí implementace `ExportEndpoint` metodu <xref:System.ServiceModel.Description.IWsdlExportExtension> rozhraní a následnou úpravou generovaného WSDL.</span><span class="sxs-lookup"><span data-stu-id="8be82-148">This is done by implementing the `ExportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlExportExtension> interface and then modifying the generated WSDL.</span></span> <span data-ttu-id="8be82-149">V této ukázce `CustomTextMessageBindingElement` používá logiky exportu WSDL z `TextMessageEncodingBinidngElement`.</span><span class="sxs-lookup"><span data-stu-id="8be82-149">In this sample, the `CustomTextMessageBindingElement` uses the WSDL export logic from the `TextMessageEncodingBinidngElement`.</span></span>  
  
 <span data-ttu-id="8be82-150">Konfigurace klienta pro tuto ukázku je ručně nakonfigurovat.</span><span class="sxs-lookup"><span data-stu-id="8be82-150">For this sample, the client configuration is hand configured.</span></span> <span data-ttu-id="8be82-151">Nelze pomocí Svcutil.exe lze generovat konfiguraci klienta, protože `CustomTextMessageBindingElement` neexportuje kontrolní výraz zásad popsat její chování.</span><span class="sxs-lookup"><span data-stu-id="8be82-151">You cannot use Svcutil.exe to generate the client configuration because the `CustomTextMessageBindingElement` does not export a policy assertion to describe its behavior.</span></span> <span data-ttu-id="8be82-152">Obecně by měly implementovat <xref:System.ServiceModel.Description.IPolicyExportExtension> rozhraní na vlastní prvek vazby pro export kontrolní výraz vlastní zásadu, která popisuje chování nebo funkce implementované element vazby.</span><span class="sxs-lookup"><span data-stu-id="8be82-152">You should generally implement the <xref:System.ServiceModel.Description.IPolicyExportExtension> interface on a custom binding element to export a custom policy assertion that describes the behavior or capability implemented by the binding element.</span></span> <span data-ttu-id="8be82-153">Příklad toho, jak exportovat kontrolní výraz zásad pro vlastní prvek vazby, najdete v článku [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="8be82-153">For an example of how to export a policy assertion for a custom binding element, see the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
## <a name="message-encoding-binding-configuration-handler"></a><span data-ttu-id="8be82-154">Obslužné rutiny konfiguračního vazby kódování zprávy</span><span class="sxs-lookup"><span data-stu-id="8be82-154">Message Encoding Binding Configuration Handler</span></span>  
 <span data-ttu-id="8be82-155">V předchozím oddílu ukazuje, jak používat vlastní text kodér zprávy prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="8be82-155">The previous section shows how to use the custom text message encoder programmatically.</span></span> <span data-ttu-id="8be82-156">`CustomTextMessageEncodingBindingSection` Implementuje konfigurace obslužnou rutinu, která vám umožní určit pomocí kodéru vlastní textové zprávy v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="8be82-156">The `CustomTextMessageEncodingBindingSection` implements a configuration handler that allows you to specify the use of a custom text message encoder within a configuration file.</span></span> <span data-ttu-id="8be82-157">`CustomTextMessageEncodingBindingSection` Třída odvozena z <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="8be82-157">The `CustomTextMessageEncodingBindingSection` class derives from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="8be82-158">`BindingElementType` Vlastnost informuje systém konfigurace typ elementu vazby k vytvoření této části.</span><span class="sxs-lookup"><span data-stu-id="8be82-158">The `BindingElementType` property informs the configuration system of the type of binding element to create for this section.</span></span>  
  
 <span data-ttu-id="8be82-159">Všechna nastavení definované `CustomTextMessageBindingElement` jsou vystaveny jako vlastnosti `CustomTextMessageEncodingBindingSection`.</span><span class="sxs-lookup"><span data-stu-id="8be82-159">All of the settings defined by `CustomTextMessageBindingElement` are exposed as the properties in the `CustomTextMessageEncodingBindingSection`.</span></span> <span data-ttu-id="8be82-160"><xref:System.Configuration.ConfigurationPropertyAttribute> Pomáhá při mapování atributů elementu konfigurace vlastností a nastavení výchozí hodnoty, pokud není nastaven atribut.</span><span class="sxs-lookup"><span data-stu-id="8be82-160">The <xref:System.Configuration.ConfigurationPropertyAttribute> assists in mapping the configuration element attributes to the properties and setting default values if the attribute is not set.</span></span> <span data-ttu-id="8be82-161">Po hodnoty z konfigurace jsou načítány a použity pro vlastnosti typu, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> metoda je volána, který převede na konkrétní instance elementu vazby vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8be82-161">After the values from configuration are loaded and applied to the properties of the type, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> method is called, which converts the properties into a concrete instance of a binding element.</span></span>  
  
 <span data-ttu-id="8be82-162">Tato obslužná rutina konfigurace mapuje následující reprezentaci v souboru App.config nebo Web.config pro službu nebo klienta.</span><span class="sxs-lookup"><span data-stu-id="8be82-162">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>  
  
```xml  
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />  
```  
  
 <span data-ttu-id="8be82-163">Ukázka používá kódování ISO-8859-1.</span><span class="sxs-lookup"><span data-stu-id="8be82-163">The sample uses the ISO-8859-1 encoding.</span></span>  
  
 <span data-ttu-id="8be82-164">Použití této konfigurace obslužné rutiny, které musí být registrována pomocí následující element konfigurace.</span><span class="sxs-lookup"><span data-stu-id="8be82-164">To use this configuration handler it must be registered using the following configuration element.</span></span>  
  
```xml  
<extensions>  
    <bindingElementExtensions>  
        <add name="customTextMessageEncoding" type="   
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection,   
                  CustomTextMessageEncoder" />  
    </bindingElementExtensions>  
</extensions>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8be82-165">Viz také</span><span class="sxs-lookup"><span data-stu-id="8be82-165">See Also</span></span>
