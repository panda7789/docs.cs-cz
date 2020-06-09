---
title: 'Vlastní kodér zpráv: Vlastní kodér textu'
ms.date: 03/30/2017
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
ms.openlocfilehash: b60fa2a84520ad208d435a0c9284c19b5de8e989
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600604"
---
# <a name="custom-message-encoder-custom-text-encoder"></a><span data-ttu-id="5505d-102">Vlastní kodér zpráv: Vlastní kodér textu</span><span class="sxs-lookup"><span data-stu-id="5505d-102">Custom Message Encoder: Custom Text Encoder</span></span>

<span data-ttu-id="5505d-103">Tato ukázka předvádí, jak implementovat vlastní kodér textových zpráv pomocí Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5505d-103">This sample demonstrates how to implement a custom text message encoder using Windows Communication Foundation (WCF).</span></span>

> [!WARNING]
> <span data-ttu-id="5505d-104">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="5505d-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5505d-105">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="5505d-105">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="5505d-106">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="5505d-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5505d-107">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="5505d-107">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`

<span data-ttu-id="5505d-108"><xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>Technologie WCF podporuje pouze kódování UTF-8, UTF-16 a big-endian Unicode.</span><span class="sxs-lookup"><span data-stu-id="5505d-108">The <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of WCF supports only the UTF-8, UTF-16 and big-endian Unicode encodings.</span></span> <span data-ttu-id="5505d-109">Kodér pro vlastní textovou zprávu v této ukázce podporuje všechna kódování znaků podporovaná platformou, která se můžou vyžadovat pro interoperabilitu.</span><span class="sxs-lookup"><span data-stu-id="5505d-109">The custom text message encoder in this sample supports all platform-supported character encodings that may be required for interoperability.</span></span> <span data-ttu-id="5505d-110">Ukázka se skládá z programu klientské konzoly (. exe), knihovny služeb (. dll) hostované službou Internetová informační služba (IIS) a knihovnou kodéru textové zprávy (. dll).</span><span class="sxs-lookup"><span data-stu-id="5505d-110">The sample consists of a client console program (.exe), a service library (.dll) hosted by Internet Information Services (IIS), and a text message encoder library (.dll).</span></span> <span data-ttu-id="5505d-111">Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď.</span><span class="sxs-lookup"><span data-stu-id="5505d-111">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="5505d-112">Kontrakt je definován `ICalculator` rozhraním, které zpřístupňuje matematické operace (sčítání, odčítání, násobení a dělení).</span><span class="sxs-lookup"><span data-stu-id="5505d-112">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="5505d-113">Klient provádí synchronní požadavky na určitou matematickou operaci a služba odpovídá výsledku.</span><span class="sxs-lookup"><span data-stu-id="5505d-113">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="5505d-114">Klient i služba používají `CustomTextMessageEncoder` místo výchozího <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="5505d-114">Both client and service uses the `CustomTextMessageEncoder` instead of the default <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span>

<span data-ttu-id="5505d-115">Implementace vlastního kodéru se skládá z objektu pro vytváření kodéru zpráv, kodér zprávy, elementu vazby kódování zprávy a obslužné rutiny konfigurace a znázorňuje následující:</span><span class="sxs-lookup"><span data-stu-id="5505d-115">The custom encoder implementation consists of a message encoder factory, a message encoder, a message encoding binding element and a configuration handler, and demonstrates the following:</span></span>

- <span data-ttu-id="5505d-116">Vytváření vlastního kodéru a továrny kodéru</span><span class="sxs-lookup"><span data-stu-id="5505d-116">Building a custom encoder and encoder factory.</span></span>

- <span data-ttu-id="5505d-117">Vytvoření prvku vazby pro vlastní kodér.</span><span class="sxs-lookup"><span data-stu-id="5505d-117">Creating a binding element for a custom encoder.</span></span>

- <span data-ttu-id="5505d-118">Použití vlastní konfigurace vazeb pro integraci vlastních elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="5505d-118">Using the custom binding configuration for integrating custom binding elements.</span></span>

- <span data-ttu-id="5505d-119">Vývoj vlastní obslužné rutiny konfigurace umožňující konfiguraci souboru vlastního elementu vazby.</span><span class="sxs-lookup"><span data-stu-id="5505d-119">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5505d-120">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="5505d-120">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="5505d-121">Pomocí následujícího příkazu nainstalujte ASP.NET 4,0.</span><span class="sxs-lookup"><span data-stu-id="5505d-121">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="5505d-122">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5505d-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="5505d-123">Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5505d-123">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="5505d-124">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5505d-124">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="message-encoder-factory-and-the-message-encoder"></a><span data-ttu-id="5505d-125">Objekt pro vytváření a kodér zpráv</span><span class="sxs-lookup"><span data-stu-id="5505d-125">Message Encoder Factory and the Message Encoder</span></span>

<span data-ttu-id="5505d-126">Když <xref:System.ServiceModel.ServiceHost> je otevřen kanál klienta nebo, komponenta čas návrhu `CustomTextMessageBindingElement` vytvoří `CustomTextMessageEncoderFactory` .</span><span class="sxs-lookup"><span data-stu-id="5505d-126">When the <xref:System.ServiceModel.ServiceHost> or the client channel is opened, the design time component `CustomTextMessageBindingElement` creates the `CustomTextMessageEncoderFactory`.</span></span> <span data-ttu-id="5505d-127">Továrna vytvoří `CustomTextMessageEncoder` .</span><span class="sxs-lookup"><span data-stu-id="5505d-127">The factory creates the `CustomTextMessageEncoder`.</span></span> <span data-ttu-id="5505d-128">Kodér zpráv funguje v režimu streamování i v režimu vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="5505d-128">The message encoder operates both in the streaming mode and the buffered mode.</span></span> <span data-ttu-id="5505d-129">Používá <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter> ke čtení a zápisu zpráv v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="5505d-129">It uses the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to read and write the messages respectively.</span></span> <span data-ttu-id="5505d-130">Na rozdíl od optimalizovaných čtecích zařízení XML a zapisovačů WCF podporujících jenom UTF-8, UTF-16 a big-endian Unicode tyto čtečky a zapisovače podporují všechna kódování podporovaná platformou.</span><span class="sxs-lookup"><span data-stu-id="5505d-130">As opposed to the optimized XML readers and writers of WCF that support only UTF-8, UTF-16 and big-endian Unicode, these readers and writers support all platform-supported encoding.</span></span>

<span data-ttu-id="5505d-131">Následující příklad kódu ukazuje CustomTextMessageEncoder.</span><span class="sxs-lookup"><span data-stu-id="5505d-131">The following code example shows the CustomTextMessageEncoder.</span></span>

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

<span data-ttu-id="5505d-132">Následující příklad kódu ukazuje, jak vytvořit objekt pro vytváření kodéru zpráv.</span><span class="sxs-lookup"><span data-stu-id="5505d-132">The following code example shows how to build the message encoder factory.</span></span>

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

## <a name="message-encoding-binding-element"></a><span data-ttu-id="5505d-133">Element vazby kódování zprávy</span><span class="sxs-lookup"><span data-stu-id="5505d-133">Message Encoding Binding Element</span></span>

<span data-ttu-id="5505d-134">Prvky vazby umožňují konfiguraci zásobníku run-time služby WCF.</span><span class="sxs-lookup"><span data-stu-id="5505d-134">The binding elements allow the configuration of the WCF run-time stack.</span></span> <span data-ttu-id="5505d-135">Chcete-li použít vlastní kodér zpráv v aplikaci WCF, je vyžadován prvek vazby, který vytvoří objekt pro vytváření kodéru zpráv s odpovídajícím nastavením na příslušné úrovni v zásobníku run-time.</span><span class="sxs-lookup"><span data-stu-id="5505d-135">To use the custom message encoder in a WCF application, a binding element is required that creates the message encoder factory with the appropriate settings at the appropriate level in the run-time stack.</span></span>

<span data-ttu-id="5505d-136">Je `CustomTextMessageBindingElement` odvozen ze <xref:System.ServiceModel.Channels.BindingElement> základní třídy a dědí z <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="5505d-136">The `CustomTextMessageBindingElement` derives from the <xref:System.ServiceModel.Channels.BindingElement> base class and inherits from the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> class.</span></span> <span data-ttu-id="5505d-137">To umožňuje jiným komponentám WCF rozpoznat tento prvek vazby jako prvek vazby kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="5505d-137">This allows other WCF components to recognize this binding element as being a message encoding binding element.</span></span> <span data-ttu-id="5505d-138">Implementace <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> vrátí instanci odpovídajícího objektu pro vytváření kodéru zpráv s příslušným nastavením.</span><span class="sxs-lookup"><span data-stu-id="5505d-138">The implementation of <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> returns an instance of the matching message encoder factory with appropriate settings.</span></span>

<span data-ttu-id="5505d-139">`CustomTextMessageBindingElement`Zpřístupňuje nastavení pro `MessageVersion` , `ContentType` a `Encoding` prostřednictvím vlastností.</span><span class="sxs-lookup"><span data-stu-id="5505d-139">The `CustomTextMessageBindingElement` exposes settings for `MessageVersion`, `ContentType`, and `Encoding` through properties.</span></span> <span data-ttu-id="5505d-140">Kodér podporuje verze Soap11Addressing i Soap12Addressing1.</span><span class="sxs-lookup"><span data-stu-id="5505d-140">The encoder supports both Soap11Addressing and Soap12Addressing1 versions.</span></span> <span data-ttu-id="5505d-141">Výchozí hodnota je Soap11Addressing1.</span><span class="sxs-lookup"><span data-stu-id="5505d-141">The default is Soap11Addressing1.</span></span> <span data-ttu-id="5505d-142">Výchozí hodnota `ContentType` je "text/XML".</span><span class="sxs-lookup"><span data-stu-id="5505d-142">The default value of the `ContentType` is "text/xml".</span></span> <span data-ttu-id="5505d-143">`Encoding`Vlastnost umožňuje nastavit hodnotu požadovaného kódování znaků.</span><span class="sxs-lookup"><span data-stu-id="5505d-143">The `Encoding` property allows you to set the value of the desired character encoding.</span></span> <span data-ttu-id="5505d-144">Ukázkový klient a služba používá kódování znaků ISO-8859-1 (Latin1), které není podporováno službou <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> WCF.</span><span class="sxs-lookup"><span data-stu-id="5505d-144">The sample client and service uses the ISO-8859-1 (Latin1) character encoding, which is not supported by the <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of WCF.</span></span>

<span data-ttu-id="5505d-145">Následující kód ukazuje, jak programově vytvořit vazbu pomocí vlastního kodéru textových zpráv.</span><span class="sxs-lookup"><span data-stu-id="5505d-145">The following code shows how to programmatically create the binding using the custom text message encoder.</span></span>

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();
bindingElements.Add(textBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
```

## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a><span data-ttu-id="5505d-146">Přidání podpory metadat k elementu vazby kódování zprávy</span><span class="sxs-lookup"><span data-stu-id="5505d-146">Adding Metadata Support to the Message Encoding Binding Element</span></span>

<span data-ttu-id="5505d-147">Jakýkoli typ, který je odvozen z, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> je zodpovědný za aktualizaci verze vazby SOAP v dokumentu WSDL vygenerovaného pro službu.</span><span class="sxs-lookup"><span data-stu-id="5505d-147">Any type that derives from <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> is responsible for updating the version of the SOAP binding in the WSDL document generated for the service.</span></span> <span data-ttu-id="5505d-148">To se provádí implementací `ExportEndpoint` metody na <xref:System.ServiceModel.Description.IWsdlExportExtension> rozhraní a následným úpravou vygenerovaného WSDL.</span><span class="sxs-lookup"><span data-stu-id="5505d-148">This is done by implementing the `ExportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlExportExtension> interface and then modifying the generated WSDL.</span></span> <span data-ttu-id="5505d-149">V této ukázce `CustomTextMessageBindingElement` používá exportní LOGIKU WSDL z `TextMessageEncodingBindingElement` .</span><span class="sxs-lookup"><span data-stu-id="5505d-149">In this sample, the `CustomTextMessageBindingElement` uses the WSDL export logic from the `TextMessageEncodingBindingElement`.</span></span>

<span data-ttu-id="5505d-150">V této ukázce je konfigurace klienta konfigurována ručně.</span><span class="sxs-lookup"><span data-stu-id="5505d-150">For this sample, the client configuration is hand configured.</span></span> <span data-ttu-id="5505d-151">Nemůžete použít Svcutil. exe ke generování konfigurace klienta, protože `CustomTextMessageBindingElement` neexportuje kontrolní výraz zásady pro popsání jeho chování.</span><span class="sxs-lookup"><span data-stu-id="5505d-151">You cannot use Svcutil.exe to generate the client configuration because the `CustomTextMessageBindingElement` does not export a policy assertion to describe its behavior.</span></span> <span data-ttu-id="5505d-152">Obecně byste měli implementovat <xref:System.ServiceModel.Description.IPolicyExportExtension> rozhraní na vlastní element vazby pro export kontrolního výrazu vlastní zásady, který popisuje chování nebo funkci implementovanou prvkem vazby.</span><span class="sxs-lookup"><span data-stu-id="5505d-152">You should generally implement the <xref:System.ServiceModel.Description.IPolicyExportExtension> interface on a custom binding element to export a custom policy assertion that describes the behavior or capability implemented by the binding element.</span></span> <span data-ttu-id="5505d-153">Příklad exportu kontrolního výrazu zásady pro vlastní prvek vazby naleznete v ukázce [Transport: UDP](transport-udp.md) .</span><span class="sxs-lookup"><span data-stu-id="5505d-153">For an example of how to export a policy assertion for a custom binding element, see the [Transport: UDP](transport-udp.md) sample.</span></span>

## <a name="message-encoding-binding-configuration-handler"></a><span data-ttu-id="5505d-154">Obslužná rutina konfigurace vazby kódování zprávy</span><span class="sxs-lookup"><span data-stu-id="5505d-154">Message Encoding Binding Configuration Handler</span></span>
<span data-ttu-id="5505d-155">V předchozí části se dozvíte, jak programově používat vlastní kodér textových zpráv.</span><span class="sxs-lookup"><span data-stu-id="5505d-155">The previous section shows how to use the custom text message encoder programmatically.</span></span> <span data-ttu-id="5505d-156">`CustomTextMessageEncodingBindingSection`Implementuje obslužnou rutinu konfigurace, která umožňuje určit použití vlastního kodéru textových zpráv v rámci konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="5505d-156">The `CustomTextMessageEncodingBindingSection` implements a configuration handler that allows you to specify the use of a custom text message encoder within a configuration file.</span></span> <span data-ttu-id="5505d-157">`CustomTextMessageEncodingBindingSection`Třída je odvozena z <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="5505d-157">The `CustomTextMessageEncodingBindingSection` class derives from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="5505d-158">`BindingElementType`Vlastnost informuje konfigurační systém typu elementu vazby, který má být pro tento oddíl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="5505d-158">The `BindingElementType` property informs the configuration system of the type of binding element to create for this section.</span></span>

<span data-ttu-id="5505d-159">Všechna nastavení definovaná nástrojem `CustomTextMessageBindingElement` jsou vystavena jako vlastnosti v `CustomTextMessageEncodingBindingSection` .</span><span class="sxs-lookup"><span data-stu-id="5505d-159">All of the settings defined by `CustomTextMessageBindingElement` are exposed as the properties in the `CustomTextMessageEncodingBindingSection`.</span></span> <span data-ttu-id="5505d-160"><xref:System.Configuration.ConfigurationPropertyAttribute>Pomoc při mapování atributů elementů konfigurace na vlastnosti a nastavení výchozích hodnot, pokud atribut není nastaven.</span><span class="sxs-lookup"><span data-stu-id="5505d-160">The <xref:System.Configuration.ConfigurationPropertyAttribute> assists in mapping the configuration element attributes to the properties and setting default values if the attribute is not set.</span></span> <span data-ttu-id="5505d-161">Poté, co jsou hodnoty z konfigurace načteny a aplikovány na vlastnosti typu, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> je volána metoda, která převede vlastnosti na konkrétní instanci elementu vazby.</span><span class="sxs-lookup"><span data-stu-id="5505d-161">After the values from configuration are loaded and applied to the properties of the type, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> method is called, which converts the properties into a concrete instance of a binding element.</span></span>

<span data-ttu-id="5505d-162">Tato obslužná rutina konfigurace mapuje následující reprezentace v App. config nebo Web. config pro službu nebo klienta.</span><span class="sxs-lookup"><span data-stu-id="5505d-162">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>

```xml
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />
```

<span data-ttu-id="5505d-163">Ukázka používá kódování ISO-8859-1.</span><span class="sxs-lookup"><span data-stu-id="5505d-163">The sample uses the ISO-8859-1 encoding.</span></span>

<span data-ttu-id="5505d-164">Chcete-li použít tuto obslužnou rutinu konfigurace, musí být zaregistrována pomocí následujícího konfiguračního prvku.</span><span class="sxs-lookup"><span data-stu-id="5505d-164">To use this configuration handler it must be registered using the following configuration element.</span></span>

```xml
<extensions>
    <bindingElementExtensions>
        <add name="customTextMessageEncoding" type="
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection,
                  CustomTextMessageEncoder" />
    </bindingElementExtensions>
</extensions>
```
