---
title: 'Vlastní kodér zpráv: Kompresní kodér'
ms.date: 03/30/2017
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
ms.openlocfilehash: 80dd29569897be501d76024a081f38ec5add4ff7
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716852"
---
# <a name="custom-message-encoder-compression-encoder"></a><span data-ttu-id="97815-102">Vlastní kodér zpráv: Kompresní kodér</span><span class="sxs-lookup"><span data-stu-id="97815-102">Custom Message Encoder: Compression Encoder</span></span>

<span data-ttu-id="97815-103">Tato ukázka předvádí, jak implementovat vlastní kodér pomocí platformy Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="97815-103">This sample demonstrates how to implement a custom encoder using the Windows Communication Foundation (WCF) platform.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="97815-104">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="97815-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="97815-105">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="97815-105">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="97815-106">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="97815-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="97815-107">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="97815-107">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`

## <a name="sample-details"></a><span data-ttu-id="97815-108">Podrobnosti ukázky</span><span class="sxs-lookup"><span data-stu-id="97815-108">Sample Details</span></span>

<span data-ttu-id="97815-109">Tato ukázka se skládá z programu klientské konzoly (. exe), samoobslužného programu konzoly služby (. exe) a knihovny kodéru kompresního kodéru (. dll).</span><span class="sxs-lookup"><span data-stu-id="97815-109">This sample consists of a client console program (.exe), a self-hosted service console program (.exe) and a compression message encoder library (.dll).</span></span> <span data-ttu-id="97815-110">Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď.</span><span class="sxs-lookup"><span data-stu-id="97815-110">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="97815-111">Kontrakt je definován rozhraním `ISampleServer`, které zpřístupňuje základní operace s odezvou řetězce (`Echo` a `BigEcho`).</span><span class="sxs-lookup"><span data-stu-id="97815-111">The contract is defined by the `ISampleServer` interface, which exposes basic string echoing operations (`Echo` and `BigEcho`).</span></span> <span data-ttu-id="97815-112">Klient provádí synchronní požadavky na danou operaci a odpověď služby, a to opakováním zprávy zpátky klientovi.</span><span class="sxs-lookup"><span data-stu-id="97815-112">The client makes synchronous requests to a given operation and the service replies by repeating the message back to the client.</span></span> <span data-ttu-id="97815-113">Aktivita klientů a služeb je viditelná v oknech konzoly.</span><span class="sxs-lookup"><span data-stu-id="97815-113">Client and service activity is visible in the console windows.</span></span> <span data-ttu-id="97815-114">Záměrem této ukázky je Ukázat, jak napsat vlastní kodér a Ukázat dopad komprimace zprávy na kabel.</span><span class="sxs-lookup"><span data-stu-id="97815-114">The intent of this sample is to show how to write a custom encoder and demonstrate the impact of compression of a message on the wire.</span></span> <span data-ttu-id="97815-115">Můžete přidat instrumentaci do kodéru kompresních zpráv, abyste mohli vypočítat velikost zprávy, čas zpracování nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="97815-115">You can add instrumentation to the compression message encoder to calculate message size, processing time, or both.</span></span>

> [!NOTE]
> <span data-ttu-id="97815-116">V .NET Framework 4 byla na klientovi WCF povolena automatická dekomprese, pokud server odesílá komprimovanou odpověď (vytvořenou pomocí algoritmu, jako je GZip nebo deflate).</span><span class="sxs-lookup"><span data-stu-id="97815-116">In the .NET Framework 4, automatic decompression has been enabled on a WCF client if the server is sending a compressed response (created with an algorithm such as GZip or Deflate).</span></span> <span data-ttu-id="97815-117">Pokud je služba hostitelem webu v rámci služby IIS (Internet Information Server), je možné službu IIS nakonfigurovat tak, aby odesílala komprimovanou odpověď.</span><span class="sxs-lookup"><span data-stu-id="97815-117">If the service is Web-hosted in Internet Information Server (IIS), then IIS can be configured for the service to send a compressed response.</span></span> <span data-ttu-id="97815-118">Tato ukázka se dá použít, pokud je potřeba provést kompresi a dekompresi jak v klientovi, tak ve službě, nebo pokud je tato služba v místním prostředí hostovaná.</span><span class="sxs-lookup"><span data-stu-id="97815-118">This sample can be used if the requirement is to do compression and decompression on both the client and the service or if the service is self-hosted.</span></span>

<span data-ttu-id="97815-119">Ukázka ukazuje, jak sestavit a integrovat vlastní kodér zpráv do aplikace WCF.</span><span class="sxs-lookup"><span data-stu-id="97815-119">The sample demonstrates how to build and integrate a custom message encoder into a WCF application.</span></span> <span data-ttu-id="97815-120">Knihovna GZipEncoder. dll je nasazena s klientem i službou.</span><span class="sxs-lookup"><span data-stu-id="97815-120">The library GZipEncoder.dll is deployed with both the client and the service.</span></span> <span data-ttu-id="97815-121">Tato ukázka také ukazuje dopad komprimace zpráv.</span><span class="sxs-lookup"><span data-stu-id="97815-121">This sample also demonstrates the impact of compressing messages.</span></span> <span data-ttu-id="97815-122">Kód v souboru GZipEncoder. dll ukazuje následující:</span><span class="sxs-lookup"><span data-stu-id="97815-122">The code in GZipEncoder.dll demonstrates the following:</span></span>

- <span data-ttu-id="97815-123">Vytváření vlastního kodéru a továrny kodéru</span><span class="sxs-lookup"><span data-stu-id="97815-123">Building a custom encoder and encoder factory.</span></span>

- <span data-ttu-id="97815-124">Vývoj prvku vazby pro vlastní kodér.</span><span class="sxs-lookup"><span data-stu-id="97815-124">Developing a binding element for a custom encoder.</span></span>

- <span data-ttu-id="97815-125">Použití vlastní konfigurace vazeb pro integraci vlastních elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="97815-125">Using the custom binding configuration for integrating custom binding elements.</span></span>

- <span data-ttu-id="97815-126">Vývoj vlastní obslužné rutiny konfigurace umožňující konfiguraci souboru vlastního elementu vazby.</span><span class="sxs-lookup"><span data-stu-id="97815-126">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>

<span data-ttu-id="97815-127">Jak bylo uvedeno dříve, existuje několik vrstev, které jsou implementovány ve vlastním kodéru.</span><span class="sxs-lookup"><span data-stu-id="97815-127">As indicated previously, there are several layers that are implemented in a custom encoder.</span></span> <span data-ttu-id="97815-128">Pro lepší ilustraci vztahu mezi jednotlivými vrstvami je v následujícím seznamu zjednodušené pořadí událostí pro spuštění služby:</span><span class="sxs-lookup"><span data-stu-id="97815-128">To better illustrate the relationship between each of these layers, a simplified order of events for service start-up is in the following list:</span></span>

1. <span data-ttu-id="97815-129">Spustí se server.</span><span class="sxs-lookup"><span data-stu-id="97815-129">The server starts.</span></span>

2. <span data-ttu-id="97815-130">Informace o konfiguraci jsou čteny.</span><span class="sxs-lookup"><span data-stu-id="97815-130">The configuration information is read.</span></span>

    1. <span data-ttu-id="97815-131">Konfigurace služby registruje obslužnou rutinu vlastní konfigurace.</span><span class="sxs-lookup"><span data-stu-id="97815-131">The service configuration registers the custom configuration handler.</span></span>

    2. <span data-ttu-id="97815-132">Hostitel služby je vytvořen a otevřen.</span><span class="sxs-lookup"><span data-stu-id="97815-132">The service host is created and opened.</span></span>

    3. <span data-ttu-id="97815-133">Vlastní prvek konfigurace vytvoří a vrátí vlastní prvek vazby.</span><span class="sxs-lookup"><span data-stu-id="97815-133">The custom configuration element creates and returns the custom binding element.</span></span>

    4. <span data-ttu-id="97815-134">Vlastní prvek vazby vytvoří a vrátí objekt pro vytváření kodéru zpráv.</span><span class="sxs-lookup"><span data-stu-id="97815-134">The custom binding element creates and returns a message encoder factory.</span></span>

3. <span data-ttu-id="97815-135">Byla přijata zpráva.</span><span class="sxs-lookup"><span data-stu-id="97815-135">A message is received.</span></span>

4. <span data-ttu-id="97815-136">Objekt pro vytváření kodéru zpráv vrátí kodér zpráv pro čtení ve zprávě a vypíše odpověď.</span><span class="sxs-lookup"><span data-stu-id="97815-136">The message encoder factory returns a message encoder for reading in the message and writing out the response.</span></span>

5. <span data-ttu-id="97815-137">Vrstva kodéru je implementována jako objekt pro vytváření tříd.</span><span class="sxs-lookup"><span data-stu-id="97815-137">The encoder layer is implemented as a class factory.</span></span> <span data-ttu-id="97815-138">Pouze objekt pro vytváření tříd kodéru musí být veřejně vystavený pro vlastní kodér.</span><span class="sxs-lookup"><span data-stu-id="97815-138">Only the encoder class factory must be publicly exposed for the custom encoder.</span></span> <span data-ttu-id="97815-139">Objekt factory je vrácen prvkem vazby, když je vytvořen objekt <xref:System.ServiceModel.ServiceHost> nebo <xref:System.ServiceModel.ChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="97815-139">The factory object is returned by the binding element when the <xref:System.ServiceModel.ServiceHost> or <xref:System.ServiceModel.ChannelFactory%601> object is created.</span></span> <span data-ttu-id="97815-140">Kodéry zpráv mohou pracovat v režimu vyrovnávací paměti nebo streamování.</span><span class="sxs-lookup"><span data-stu-id="97815-140">Message encoders can operate in a buffered or streaming mode.</span></span> <span data-ttu-id="97815-141">Tato ukázka demonstruje režim vyrovnávací paměti i režim streamování.</span><span class="sxs-lookup"><span data-stu-id="97815-141">This sample demonstrates both buffered mode and streaming mode.</span></span>

<span data-ttu-id="97815-142">Pro každý režim je k dispozici doprovodný `ReadMessage` a metoda `WriteMessage` třídy abstract `MessageEncoder`.</span><span class="sxs-lookup"><span data-stu-id="97815-142">For each mode there is an accompanying `ReadMessage` and `WriteMessage` method on the abstract `MessageEncoder` class.</span></span> <span data-ttu-id="97815-143">Většina práce kódování probíhá v těchto metodách.</span><span class="sxs-lookup"><span data-stu-id="97815-143">A majority of the encoding work takes place in these methods.</span></span> <span data-ttu-id="97815-144">Ukázka zalomí stávající textové a binární kodéry zpráv.</span><span class="sxs-lookup"><span data-stu-id="97815-144">The sample wraps the existing text and binary message encoders.</span></span> <span data-ttu-id="97815-145">To umožňuje, aby vzorek mohl delegovat čtení a zápis kabelových reprezentace zpráv do vnitřního kodéru a umožňuje kompresnímu kodéru komprimaci nebo dekomprimaci výsledků.</span><span class="sxs-lookup"><span data-stu-id="97815-145">This allows the sample to delegate the reading and writing of the wire representation of messages to the inner encoder and allows the compression encoder to compress or decompress the results.</span></span> <span data-ttu-id="97815-146">Vzhledem k tomu, že není k dispozici žádný kanál pro kódování zpráv, je to jediný model pro použití více kodérů ve službě WCF.</span><span class="sxs-lookup"><span data-stu-id="97815-146">Because there is no pipeline for message encoding, this is the only model for using multiple encoders in WCF.</span></span> <span data-ttu-id="97815-147">Jakmile se zpráva dekomprimuje, Výsledná zpráva se předá zásobníku pro zpracování zásobníku kanálů.</span><span class="sxs-lookup"><span data-stu-id="97815-147">Once the message has been decompressed, the resulting message is passed up the stack for the channel stack to handle.</span></span> <span data-ttu-id="97815-148">Během komprese se výsledná komprimovaná zpráva zapisuje přímo do poskytnutého datového proudu.</span><span class="sxs-lookup"><span data-stu-id="97815-148">During compression, the resulting compressed message is written directly to the stream provided.</span></span>

<span data-ttu-id="97815-149">Tato ukázka používá pomocné metody (`CompressBuffer` a `DecompressBuffer`) k provedení převodu z vyrovnávací paměti na datové proudy pro použití třídy `GZipStream`.</span><span class="sxs-lookup"><span data-stu-id="97815-149">This sample uses helper methods (`CompressBuffer` and `DecompressBuffer`) to perform conversion from buffers to streams to use the `GZipStream` class.</span></span>

<span data-ttu-id="97815-150">Třídy `ReadMessage` a `WriteMessage` vyrovnávací paměti využívají třídu `BufferManager`.</span><span class="sxs-lookup"><span data-stu-id="97815-150">The buffered `ReadMessage` and `WriteMessage` classes make use of the `BufferManager` class.</span></span> <span data-ttu-id="97815-151">Kodér je přístupný jenom přes objekt pro vytváření kodéru.</span><span class="sxs-lookup"><span data-stu-id="97815-151">The encoder is accessible only through the encoder factory.</span></span> <span data-ttu-id="97815-152">Třída abstract `MessageEncoderFactory` poskytuje vlastnost s názvem `Encoder` pro přístup k aktuálnímu kodéru a metodě s názvem `CreateSessionEncoder` pro vytvoření kodéru, který podporuje relace.</span><span class="sxs-lookup"><span data-stu-id="97815-152">The abstract `MessageEncoderFactory` class provides a property named `Encoder` for accessing the current encoder and a method named `CreateSessionEncoder` for creating an encoder that supports sessions.</span></span> <span data-ttu-id="97815-153">Takový kodér se dá použít ve scénáři, kde kanál podporuje relace, je uspořádaný a spolehlivý.</span><span class="sxs-lookup"><span data-stu-id="97815-153">Such an encoder can be used in the scenario where the channel supports sessions, is ordered and is reliable.</span></span> <span data-ttu-id="97815-154">Tento scénář umožňuje optimalizaci v každé relaci dat zapsaných do tohoto drátu.</span><span class="sxs-lookup"><span data-stu-id="97815-154">This scenario allows for optimization in each session of the data written to the wire.</span></span> <span data-ttu-id="97815-155">Pokud to není žádoucí, základní metoda by neměla být přetížena.</span><span class="sxs-lookup"><span data-stu-id="97815-155">If this is not desired, the base method should not be overloaded.</span></span> <span data-ttu-id="97815-156">Vlastnost `Encoder` poskytuje mechanismus pro přístup k kodéru bez relací a výchozí implementace metody `CreateSessionEncoder` vrací hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="97815-156">The `Encoder` property provides a mechanism for accessing the session-less encoder and the default implementation of the `CreateSessionEncoder` method returns the value of the property.</span></span> <span data-ttu-id="97815-157">Vzhledem k tomu, že ukázka zabalí existující kodér, aby poskytoval kompresi, implementace `MessageEncoderFactory` přijímá `MessageEncoderFactory`, která představuje objekt pro vytváření vnitřních kodérů.</span><span class="sxs-lookup"><span data-stu-id="97815-157">Because the sample wraps an existing encoder to provide compression, the `MessageEncoderFactory` implementation accepts a `MessageEncoderFactory` that represents the inner encoder factory.</span></span>

<span data-ttu-id="97815-158">Teď, když je definice kodéru a kodéru definovaná, se dají použít spolu s klientem a službou WCF.</span><span class="sxs-lookup"><span data-stu-id="97815-158">Now that the encoder and encoder factory are defined, they can be used with a WCF client and service.</span></span> <span data-ttu-id="97815-159">Tyto kodéry však musí být přidány do zásobníku kanálů.</span><span class="sxs-lookup"><span data-stu-id="97815-159">However, these encoders must be added to the channel stack.</span></span> <span data-ttu-id="97815-160">Třídy můžete odvodit z tříd <xref:System.ServiceModel.ServiceHost> a <xref:System.ServiceModel.ChannelFactory%601> a přepsat `OnInitialize` metody a přidat tuto továrnu kodéru ručně.</span><span class="sxs-lookup"><span data-stu-id="97815-160">You can derive classes from the <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.ChannelFactory%601> classes and override the `OnInitialize` methods to add this encoder factory manually.</span></span> <span data-ttu-id="97815-161">Objekt pro vytváření kodéru můžete také zveřejnit pomocí vlastního elementu vazby.</span><span class="sxs-lookup"><span data-stu-id="97815-161">You can also expose the encoder factory through a custom binding element.</span></span>

<span data-ttu-id="97815-162">Chcete-li vytvořit nový vlastní element vazby, odvodit třídu z třídy <xref:System.ServiceModel.Channels.BindingElement>.</span><span class="sxs-lookup"><span data-stu-id="97815-162">To create a new custom binding element, derive a class from the <xref:System.ServiceModel.Channels.BindingElement> class.</span></span> <span data-ttu-id="97815-163">Existuje však několik typů prvků vazby.</span><span class="sxs-lookup"><span data-stu-id="97815-163">There are, however, several types of binding elements.</span></span> <span data-ttu-id="97815-164">Chcete-li zajistit, aby byl prvek vlastní vazby rozpoznán jako prvek vazby kódování zprávy, je nutné implementovat také <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="97815-164">To ensure that the custom binding element is recognized as a message encoding binding element, you also must implement the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.</span></span> <span data-ttu-id="97815-165"><xref:System.ServiceModel.Channels.MessageEncodingBindingElement> zpřístupňuje metodu pro vytvoření nového objektu pro vytváření nových zpráv (`CreateMessageEncoderFactory`), který je implementován pro vrácení instance odpovídajícího objektu pro vytváření kodéru zpráv.</span><span class="sxs-lookup"><span data-stu-id="97815-165">The <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> exposes a method for creating a new message encoder factory (`CreateMessageEncoderFactory`), which is implemented to return an instance of the matching message encoder factory.</span></span> <span data-ttu-id="97815-166">Kromě toho <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> obsahuje vlastnost, která označuje verzi adresování.</span><span class="sxs-lookup"><span data-stu-id="97815-166">Additionally, the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> has a property to indicate the addressing version.</span></span> <span data-ttu-id="97815-167">Vzhledem k tomu, že tato ukázka zabalí existující kodéry, ukázková implementace také zalomí existující prvky vazby kodéru a převezme prvek vazby vnitřního kodéru jako parametr konstruktoru a zpřístupní jej prostřednictvím vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="97815-167">Because this sample wraps the existing encoders, the sample implementation also wraps the existing encoder binding elements and takes an inner encoder binding element as a parameter to the constructor and exposes it through a property.</span></span> <span data-ttu-id="97815-168">Následující vzorový kód ukazuje implementaci třídy `GZipMessageEncodingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="97815-168">The following sample code shows the implementation of the `GZipMessageEncodingBindingElement` class.</span></span>

```csharp
public sealed class GZipMessageEncodingBindingElement
                        : MessageEncodingBindingElement //BindingElement
                        , IPolicyExportExtension
{

    //We use an inner binding element to store information
    //required for the inner encoder.
    MessageEncodingBindingElement innerBindingElement;

        //By default, use the default text encoder as the inner encoder.
        public GZipMessageEncodingBindingElement()
            : this(new TextMessageEncodingBindingElement()) { }

    public GZipMessageEncodingBindingElement(MessageEncodingBindingElement messageEncoderBindingElement)
    {
        this.innerBindingElement = messageEncoderBindingElement;
    }

    public MessageEncodingBindingElement InnerMessageEncodingBindingElement
    {
        get { return innerBindingElement; }
        set { innerBindingElement = value; }
    }

    //Main entry point into the encoder binding element.
    // Called by WCF to get the factory that creates the
    //message encoder.
    public override MessageEncoderFactory CreateMessageEncoderFactory()
    {
        return new
GZipMessageEncoderFactory(innerBindingElement.CreateMessageEncoderFactory());
    }

    public override MessageVersion MessageVersion
    {
        get { return innerBindingElement.MessageVersion; }
        set { innerBindingElement.MessageVersion = value; }
    }

    public override BindingElement Clone()
    {
        return new
        GZipMessageEncodingBindingElement(this.innerBindingElement);
    }

    public override T GetProperty<T>(BindingContext context)
    {
        if (typeof(T) == typeof(XmlDictionaryReaderQuotas))
        {
            return innerBindingElement.GetProperty<T>(context);
        }
        else
        {
            return base.GetProperty<T>(context);
        }
    }

    public override IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)
    {
        if (context == null)
            throw new ArgumentNullException("context");

        context.BindingParameters.Add(this);
        return context.BuildInnerChannelFactory<TChannel>();
    }

    public override IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)
    {
        if (context == null)
            throw new ArgumentNullException("context");

        context.BindingParameters.Add(this);
        return context.BuildInnerChannelListener<TChannel>();
    }

    public override bool CanBuildChannelListener<TChannel>(BindingContext context)
    {
        if (context == null)
            throw new ArgumentNullException("context");

        context.BindingParameters.Add(this);
        return context.CanBuildInnerChannelListener<TChannel>();
    }

    void IPolicyExportExtension.ExportPolicy(MetadataExporter exporter, PolicyConversionContext policyContext)
    {
        if (policyContext == null)
        {
            throw new ArgumentNullException("policyContext");
        }
       XmlDocument document = new XmlDocument();
       policyContext.GetBindingAssertions().Add(document.CreateElement(
            GZipMessageEncodingPolicyConstants.GZipEncodingPrefix,
            GZipMessageEncodingPolicyConstants.GZipEncodingName,
            GZipMessageEncodingPolicyConstants.GZipEncodingNamespace));
    }
}
```

<span data-ttu-id="97815-169">Všimněte si, že `GZipMessageEncodingBindingElement` třída implementuje rozhraní `IPolicyExportExtension`, aby se tento element vazby mohl exportovat jako zásada v metadatech, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="97815-169">Note that `GZipMessageEncodingBindingElement` class implements the `IPolicyExportExtension` interface, so that this binding element can be exported as a policy in metadata, as shown in the following example.</span></span>

```xml
<wsp:Policy wsu:Id="BufferedHttpSampleServer_ISampleServer_policy">
    <wsp:ExactlyOne>
      <wsp:All>
        <gzip:text xmlns:gzip=
        "http://schemas.microsoft.com/ws/06/2004/mspolicy/netgzip1" />
       <wsaw:UsingAddressing />
     </wsp:All>
   </wsp:ExactlyOne>
</wsp:Policy>
```

<span data-ttu-id="97815-170">Třída `GZipMessageEncodingBindingElementImporter` implementuje rozhraní `IPolicyImportExtension`, tato třída importuje zásady pro `GZipMessageEncodingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="97815-170">The `GZipMessageEncodingBindingElementImporter` class implements the `IPolicyImportExtension` interface, this class imports policy for `GZipMessageEncodingBindingElement`.</span></span> <span data-ttu-id="97815-171">Pomocí nástroje Svcutil. exe lze importovat zásady do konfiguračního souboru, aby bylo možné zpracovávat `GZipMessageEncodingBindingElement`, do Svcutil. exe. config by se měly přidat následující.</span><span class="sxs-lookup"><span data-stu-id="97815-171">Svcutil.exe tool can be used to import policies to the configuration file, to handle `GZipMessageEncodingBindingElement`, the following should be added to Svcutil.exe.config.</span></span>

```xml
<configuration>
  <system.serviceModel>
    <extensions>
      <bindingElementExtensions>
        <add name="gzipMessageEncoding"
          type=
            "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
      </bindingElementExtensions>
    </extensions>
    <client>
      <metadata>
        <policyImporters>
          <remove type=
"System.ServiceModel.Channels.MessageEncodingBindingElementImporter, System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
          <extension type=
"Microsoft.ServiceModel.Samples.GZipMessageEncodingBindingElementImporter, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
        </policyImporters>
      </metadata>
    </client>
  </system.serviceModel>
</configuration>
```

<span data-ttu-id="97815-172">Nyní, když existuje odpovídající element vazby kompresního kodéru, lze programově připojit ke službě nebo klientovi pomocí vytvoření nového vlastního objektu vazby a přidáním vlastního elementu vazby, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="97815-172">Now that there is a matching binding element for the compression encoder, it can be programmatically hooked into the service or client by constructing a new custom binding object and adding the custom binding element to it, as shown in the following sample code.</span></span>

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
GZipMessageEncodingBindingElement compBindingElement = new GZipMessageEncodingBindingElement ();
bindingElements.Add(compBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
binding.Name = "SampleBinding";
binding.Namespace = "http://tempuri.org/bindings";
```

<span data-ttu-id="97815-173">I když je to pro většinu scénářů uživatelů dostačující, podpora konfigurace souboru je kritická, pokud by služba byla hostována na webu.</span><span class="sxs-lookup"><span data-stu-id="97815-173">While this may be sufficient for the majority of user scenarios, supporting a file configuration is critical if a service is to be Web-hosted.</span></span> <span data-ttu-id="97815-174">Aby bylo možné podporovat scénář pro hostování webu, je nutné vyvinout vlastní obslužnou rutinu konfigurace, aby bylo možné v souboru konfigurovat vlastní prvek vazby.</span><span class="sxs-lookup"><span data-stu-id="97815-174">To support the Web-hosted scenario, you must develop a custom configuration handler to allow a custom binding element to be configurable in a file.</span></span>

<span data-ttu-id="97815-175">Můžete vytvořit obslužnou rutinu konfigurace pro element vazby na vrcholu konfiguračního systému.</span><span class="sxs-lookup"><span data-stu-id="97815-175">You can build a configuration handler for the binding element on top of the configuration system.</span></span> <span data-ttu-id="97815-176">Obslužná rutina konfigurace elementu vazby musí být odvozena od třídy <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>.</span><span class="sxs-lookup"><span data-stu-id="97815-176">The configuration handler for the binding element must derive from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="97815-177"><xref:System.ServiceModel.Configuration.BindingElementExtensionElement.BindingElementType?displayProperty=nameWithType> informuje konfigurační systém typu elementu vazby, který se má pro tento oddíl vytvořit.</span><span class="sxs-lookup"><span data-stu-id="97815-177">The <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.BindingElementType?displayProperty=nameWithType> informs the configuration system of the type of binding element to create for this section.</span></span> <span data-ttu-id="97815-178">Všechny aspekty `BindingElement`, které lze nastavit, by měly být zveřejněny jako vlastnosti v odvozené třídě <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>.</span><span class="sxs-lookup"><span data-stu-id="97815-178">All aspects of the `BindingElement` that can be set should be exposed as properties in the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class.</span></span> <span data-ttu-id="97815-179"><xref:System.Configuration.ConfigurationPropertyAttribute> pomáhá při mapování atributů elementů konfigurace na vlastnosti a nastavení výchozích hodnot, pokud chybí atributy.</span><span class="sxs-lookup"><span data-stu-id="97815-179">The <xref:System.Configuration.ConfigurationPropertyAttribute> assists in mapping the configuration element attributes to the properties and setting default values if attributes are missing.</span></span> <span data-ttu-id="97815-180">Poté, co jsou hodnoty z konfigurace načteny a aplikovány na vlastnosti, je volána metoda <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A?displayProperty=nameWithType>, která převede vlastnosti na konkrétní instanci elementu vazby.</span><span class="sxs-lookup"><span data-stu-id="97815-180">After the values from configuration are loaded and applied to the properties, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A?displayProperty=nameWithType> method is called, which converts the properties into a concrete instance of a binding element.</span></span> <span data-ttu-id="97815-181">Metoda <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A?displayProperty=nameWithType> slouží k převodu vlastností v odvozené třídě <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> na hodnoty, které mají být nastaveny u nově vytvořeného prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="97815-181">The <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A?displayProperty=nameWithType> method is used to convert the properties on the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class into the values to be set on the newly created binding element.</span></span>

<span data-ttu-id="97815-182">Následující vzorový kód ukazuje implementaci `GZipMessageEncodingElement`.</span><span class="sxs-lookup"><span data-stu-id="97815-182">The following sample code shows the implementation of the `GZipMessageEncodingElement`.</span></span>

```csharp
public class GZipMessageEncodingElement : BindingElementExtensionElement
{
    public GZipMessageEncodingElement()
    {
    }

//Called by the WCF to discover the type of binding element this
//config section enables
    public override Type BindingElementType
    {
        get { return typeof(GZipMessageEncodingBindingElement); }
    }

    //The only property we need to configure for our binding element is
    //the type of inner encoder to use. Here, we support text and
    //binary.
    [ConfigurationProperty("innerMessageEncoding",
                         DefaultValue = "textMessageEncoding")]
    public string InnerMessageEncoding
    {
        get { return (string)base["innerMessageEncoding"]; }
        set { base["innerMessageEncoding"] = value; }
    }

    //Called by the WCF to apply the configuration settings (the
    //property above) to the binding element
    public override void ApplyConfiguration(BindingElement bindingElement)
    {
        GZipMessageEncodingBindingElement binding =
                (GZipMessageEncodingBindingElement)bindingElement;
        PropertyInformationCollection propertyInfo =
                    this.ElementInformation.Properties;
        if (propertyInfo["innerMessageEncoding"].ValueOrigin !=
                                     PropertyValueOrigin.Default)
        {
            switch (this.InnerMessageEncoding)
            {
                case "textMessageEncoding":
                    binding.InnerMessageEncodingBindingElement =
                      new TextMessageEncodingBindingElement();
                    break;
                case "binaryMessageEncoding":
                    binding.InnerMessageEncodingBindingElement =
                         new BinaryMessageEncodingBindingElement();
                    break;
            }
        }
    }

    //Called by the WCF to create the binding element
    protected override BindingElement CreateBindingElement()
    {
        GZipMessageEncodingBindingElement bindingElement =
                new GZipMessageEncodingBindingElement();
        this.ApplyConfiguration(bindingElement);
        return bindingElement;
    }
}
```

<span data-ttu-id="97815-183">Tato obslužná rutina konfigurace mapuje následující reprezentace v App. config nebo Web. config pro službu nebo klienta.</span><span class="sxs-lookup"><span data-stu-id="97815-183">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>

```xml
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />
```

<span data-ttu-id="97815-184">Chcete-li použít tuto obslužnou rutinu konfigurace, musí být registrována v rámci elementu [\<System. serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) , jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="97815-184">To use this configuration handler, it must be registered within the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, as shown in the following sample configuration.</span></span>

```xml
<extensions>
    <bindingElementExtensions>
       <add
           name="gzipMessageEncoding"
           type=
           "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement,
           GZipEncoder, Version=1.0.0.0, Culture=neutral,
           PublicKeyToken=null" />
      </bindingElementExtensions>
</extensions>
```

<span data-ttu-id="97815-185">Při spuštění serveru se v okně konzoly zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="97815-185">When you run the server, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="97815-186">V okně stiskněte klávesu ENTER, aby se server vypnul.</span><span class="sxs-lookup"><span data-stu-id="97815-186">Press ENTER in the window to shut down the server.</span></span>

```console
Press Enter key to Exit.

        Server Echo(string input) called:
        Client message: Simple hello

        Server BigEcho(string[] input) called:
        64 client messages
```

<span data-ttu-id="97815-187">Když spustíte klienta nástroje, v okně konzoly se zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="97815-187">When you run the client, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="97815-188">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="97815-188">Press ENTER in the client window to shut down the client.</span></span>

```console
Calling Echo(string):
Server responds: Simple hello Simple hello

Calling BigEcho(string[]):
Server responds: Hello 0

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="97815-189">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="97815-189">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="97815-190">Pomocí následujícího příkazu nainstalujte ASP.NET 4,0:</span><span class="sxs-lookup"><span data-stu-id="97815-190">Install ASP.NET 4.0 using the following command:</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="97815-191">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="97815-191">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="97815-192">Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="97815-192">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="97815-193">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="97815-193">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="97815-194">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="97815-194">The samples may already be installed on your machine.</span></span> <span data-ttu-id="97815-195">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="97815-195">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="97815-196">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="97815-196">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="97815-197">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="97815-197">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`
