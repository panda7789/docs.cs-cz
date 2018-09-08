---
title: 'Vlastní kodér zpráv: Kompresní kodér'
ms.date: 03/30/2017
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
ms.openlocfilehash: b70875e385fa32256476f6d1ae53e8cc1f5ff9de
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44179244"
---
# <a name="custom-message-encoder-compression-encoder"></a><span data-ttu-id="a0aff-102">Vlastní kodér zpráv: Kompresní kodér</span><span class="sxs-lookup"><span data-stu-id="a0aff-102">Custom Message Encoder: Compression Encoder</span></span>
<span data-ttu-id="a0aff-103">Tento příklad ukazuje, jak implementovat vlastní kodér na platformě Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a0aff-103">This sample demonstrates how to implement a custom encoder using the Windows Communication Foundation (WCF) platform.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a0aff-104">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="a0aff-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a0aff-105">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="a0aff-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a0aff-106">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="a0aff-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a0aff-107">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="a0aff-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="sample-details"></a><span data-ttu-id="a0aff-108">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a0aff-108">Sample Details</span></span>  
 <span data-ttu-id="a0aff-109">Tento příklad se skládá z programu konzoly klienta (.exe), v místním prostředí služby konzolový program (.exe) a komprese zprávy kodér knihovny (.dll).</span><span class="sxs-lookup"><span data-stu-id="a0aff-109">This sample consists of a client console program (.exe), a self-hosted service console program (.exe) and a compression message encoder library (.dll).</span></span> <span data-ttu-id="a0aff-110">Služba implementuje kontrakt, který definuje vzor komunikace požadavek odpověď.</span><span class="sxs-lookup"><span data-stu-id="a0aff-110">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="a0aff-111">Smlouva je definován `ISampleServer` rozhraní, které zpřístupňuje základní řetězec přečtou operací (`Echo` a `BigEcho`).</span><span class="sxs-lookup"><span data-stu-id="a0aff-111">The contract is defined by the `ISampleServer` interface, which exposes basic string echoing operations (`Echo` and `BigEcho`).</span></span> <span data-ttu-id="a0aff-112">Klient podá synchronní žádosti pro danou operaci a odpovědi služby opakováním zprávy zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="a0aff-112">The client makes synchronous requests to a given operation and the service replies by repeating the message back to the client.</span></span> <span data-ttu-id="a0aff-113">Činnost klienta a služby je viditelný v oknech konzoly.</span><span class="sxs-lookup"><span data-stu-id="a0aff-113">Client and service activity is visible in the console windows.</span></span> <span data-ttu-id="a0aff-114">Záměrem tohoto příkladu je ukazují, jak psát vlastní kodér a předvádět dopady kompresi zpráv na lince.</span><span class="sxs-lookup"><span data-stu-id="a0aff-114">The intent of this sample is to show how to write a custom encoder and demonstrate the impact of compression of a message on the wire.</span></span> <span data-ttu-id="a0aff-115">Přidat instrumentaci na kompresní kodér zprávy k výpočtu velikosti zpráv a doba zpracování.</span><span class="sxs-lookup"><span data-stu-id="a0aff-115">You can add instrumentation to the compression message encoder to calculate message size, processing time, or both.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0aff-116">V rozhraní .NET Framework 4 Automatická dekomprese byla zapnuta klienta WCF na serveru je odesílání zkomprimovanou odpověď (vytvořenou pomocí algoritmu, jako je například GZip nebo Deflate).</span><span class="sxs-lookup"><span data-stu-id="a0aff-116">In the .NET Framework 4, automatic decompression has been enabled on a WCF client if the server is sending a compressed response (created with an algorithm such as GZip or Deflate).</span></span> <span data-ttu-id="a0aff-117">Pokud je služba Web hostovaný v Internet Information Server (IIS), může služba IIS konfigurována na odeslání komprimované odpovědi služby.</span><span class="sxs-lookup"><span data-stu-id="a0aff-117">If the service is Web-hosted in Internet Information Server (IIS), then IIS can be configured for the service to send a compressed response.</span></span> <span data-ttu-id="a0aff-118">Tato ukázka je možné, pokud je požadavkem pro kompresi a dekompresi na klienta a služby, nebo jestli je služba v místním prostředí.</span><span class="sxs-lookup"><span data-stu-id="a0aff-118">This sample can be used if the requirement is to do compression and decompression on both the client and the service or if the service is self-hosted.</span></span>  
  
 <span data-ttu-id="a0aff-119">Vzorek ukazuje, jak sestavit a integrovat vlastní kodér zpráv do aplikace WCF.</span><span class="sxs-lookup"><span data-stu-id="a0aff-119">The sample demonstrates how to build and integrate a custom message encoder into a WCF application.</span></span> <span data-ttu-id="a0aff-120">Knihovna GZipEncoder.dll se nasazuje s klientem a službou.</span><span class="sxs-lookup"><span data-stu-id="a0aff-120">The library GZipEncoder.dll is deployed with both the client and the service.</span></span> <span data-ttu-id="a0aff-121">Tato ukázka předvádí, dopad komprese zprávy.</span><span class="sxs-lookup"><span data-stu-id="a0aff-121">This sample also demonstrates the impact of compressing messages.</span></span> <span data-ttu-id="a0aff-122">Kód v GZipEncoder.dll ukazuje následující:</span><span class="sxs-lookup"><span data-stu-id="a0aff-122">The code in GZipEncoder.dll demonstrates the following:</span></span>  
  
-   <span data-ttu-id="a0aff-123">Vytváření vlastních encoder a kodér objekt pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="a0aff-123">Building a custom encoder and encoder factory.</span></span>  
  
-   <span data-ttu-id="a0aff-124">Vývoj element vazby pro vlastní kodér.</span><span class="sxs-lookup"><span data-stu-id="a0aff-124">Developing a binding element for a custom encoder.</span></span>  
  
-   <span data-ttu-id="a0aff-125">Pomocí konfigurace vlastních vazeb pro integraci elementů vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="a0aff-125">Using the custom binding configuration for integrating custom binding elements.</span></span>  
  
-   <span data-ttu-id="a0aff-126">Vývoj vlastní obslužnou rutinu umožní konfiguraci souboru vlastní prvek vazby.</span><span class="sxs-lookup"><span data-stu-id="a0aff-126">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>  
  
 <span data-ttu-id="a0aff-127">Jak je uvedeno dříve, existuje několik vrstev, které jsou implementovány v vlastní kodér.</span><span class="sxs-lookup"><span data-stu-id="a0aff-127">As indicated previously, there are several layers that are implemented in a custom encoder.</span></span> <span data-ttu-id="a0aff-128">Abychom vám lépe předvedli vztah mezi každou z těchto úrovní, zjednodušené pořadí událostí pro spuštění služby je v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="a0aff-128">To better illustrate the relationship between each of these layers, a simplified order of events for service start-up is in the following list:</span></span>  
  
1.  <span data-ttu-id="a0aff-129">Spustí se server.</span><span class="sxs-lookup"><span data-stu-id="a0aff-129">The server starts.</span></span>  
  
2.  <span data-ttu-id="a0aff-130">Informace o konfiguraci je pro čtení.</span><span class="sxs-lookup"><span data-stu-id="a0aff-130">The configuration information is read.</span></span>  
  
    1.  <span data-ttu-id="a0aff-131">Konfigurace služby registruje rutiny vlastní konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a0aff-131">The service configuration registers the custom configuration handler.</span></span>  
  
    2.  <span data-ttu-id="a0aff-132">Hostitel služby je vytvořen a otevřít.</span><span class="sxs-lookup"><span data-stu-id="a0aff-132">The service host is created and opened.</span></span>  
  
    3.  <span data-ttu-id="a0aff-133">Vlastní konfigurace pro element vytvoří a vrátí prvek vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="a0aff-133">The custom configuration element creates and returns the custom binding element.</span></span>  
  
    4.  <span data-ttu-id="a0aff-134">Vlastní prvek vazby vytvoří a vrátí objekt pro vytváření kodéru zpráv.</span><span class="sxs-lookup"><span data-stu-id="a0aff-134">The custom binding element creates and returns a message encoder factory.</span></span>  
  
3.  <span data-ttu-id="a0aff-135">Příjmu zprávy.</span><span class="sxs-lookup"><span data-stu-id="a0aff-135">A message is received.</span></span>  
  
4.  <span data-ttu-id="a0aff-136">Objekt pro vytváření kodéru zpráv vrátí kodéru zprávy ve zprávě pro čtení a zápis odpovědi.</span><span class="sxs-lookup"><span data-stu-id="a0aff-136">The message encoder factory returns a message encoder for reading in the message and writing out the response.</span></span>  
  
5.  <span data-ttu-id="a0aff-137">Kodér vrstvy je implementovaný jako objekt pro vytváření tříd.</span><span class="sxs-lookup"><span data-stu-id="a0aff-137">The encoder layer is implemented as a class factory.</span></span> <span data-ttu-id="a0aff-138">Pouze kodéru pro vytváření tříd musí být veřejně vystavené pro vlastní kodér.</span><span class="sxs-lookup"><span data-stu-id="a0aff-138">Only the encoder class factory must be publicly exposed for the custom encoder.</span></span> <span data-ttu-id="a0aff-139">Objekt factory, který je vrácený element vazby při <xref:System.ServiceModel.ServiceHost> nebo <xref:System.ServiceModel.ChannelFactory%601> je vytvořen objekt.</span><span class="sxs-lookup"><span data-stu-id="a0aff-139">The factory object is returned by the binding element when the <xref:System.ServiceModel.ServiceHost> or <xref:System.ServiceModel.ChannelFactory%601> object is created.</span></span> <span data-ttu-id="a0aff-140">Zpráva kodérů můžou fungovat v režimu ve vyrovnávací paměti nebo datových proudů.</span><span class="sxs-lookup"><span data-stu-id="a0aff-140">Message encoders can operate in a buffered or streaming mode.</span></span> <span data-ttu-id="a0aff-141">Tato ukázka předvádí, jak ve vyrovnávací paměti režim a režim tvorby datového proudu.</span><span class="sxs-lookup"><span data-stu-id="a0aff-141">This sample demonstrates both buffered mode and streaming mode.</span></span>  
  
 <span data-ttu-id="a0aff-142">Pro oba režimy existuje je v doprovodné `ReadMessage` a `WriteMessage` metoda abstract `MessageEncoder` třídy.</span><span class="sxs-lookup"><span data-stu-id="a0aff-142">For each mode there is an accompanying `ReadMessage` and `WriteMessage` method on the abstract `MessageEncoder` class.</span></span> <span data-ttu-id="a0aff-143">Většina kódování práce probíhá v těchto metod.</span><span class="sxs-lookup"><span data-stu-id="a0aff-143">A majority of the encoding work takes place in these methods.</span></span> <span data-ttu-id="a0aff-144">Ukázka zabalí existující text a zprávy v binární kodérů.</span><span class="sxs-lookup"><span data-stu-id="a0aff-144">The sample wraps the existing text and binary message encoders.</span></span> <span data-ttu-id="a0aff-145">To umožňuje vzorku pro delegování čtení a zápis síťové vyjádření zpráv do vnitřní kodér a kompresní kodér ke kompresi a dekompresi výsledky.</span><span class="sxs-lookup"><span data-stu-id="a0aff-145">This allows the sample to delegate the reading and writing of the wire representation of messages to the inner encoder and allows the compression encoder to compress or decompress the results.</span></span> <span data-ttu-id="a0aff-146">Protože neexistuje žádný kanál pro kódování zprávy, jde o jediný model pro použití více kodérů ve službě WCF.</span><span class="sxs-lookup"><span data-stu-id="a0aff-146">Because there is no pipeline for message encoding, this is the only model for using multiple encoders in WCF.</span></span> <span data-ttu-id="a0aff-147">Jakmile byl dekomprimován zprávy, se předá výslednou zprávu zásobníku do zásobníku kanál pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="a0aff-147">Once the message has been decompressed, the resulting message is passed up the stack for the channel stack to handle.</span></span> <span data-ttu-id="a0aff-148">Během komprese je výsledný komprimované zprávy zapisují přímo do datového proudu k dispozici.</span><span class="sxs-lookup"><span data-stu-id="a0aff-148">During compression, the resulting compressed message is written directly to the stream provided.</span></span>  
  
 <span data-ttu-id="a0aff-149">Tato ukázka používá pomocné metody (`CompressBuffer` a `DecompressBuffer`) k provedení převodu z vyrovnávací paměti do datových proudů používat `GZipStream` třídy.</span><span class="sxs-lookup"><span data-stu-id="a0aff-149">This sample uses helper methods (`CompressBuffer` and `DecompressBuffer`) to perform conversion from buffers to streams to use the `GZipStream` class.</span></span>  
  
 <span data-ttu-id="a0aff-150">Ve vyrovnávací paměti `ReadMessage` a `WriteMessage` třídy Zkontrolujte použití `BufferManager` třídy.</span><span class="sxs-lookup"><span data-stu-id="a0aff-150">The buffered `ReadMessage` and `WriteMessage` classes make use of the `BufferManager` class.</span></span> <span data-ttu-id="a0aff-151">Kodér je přístupný pouze prostřednictvím kodér objekt pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="a0aff-151">The encoder is accessible only through the encoder factory.</span></span> <span data-ttu-id="a0aff-152">Abstraktní `MessageEncoderFactory` třída poskytuje vlastnost s názvem `Encoder` pro přístup k aktuální kodér a metodu s názvem `CreateSessionEncoder` pro vytvoření encoder, který podporuje relací.</span><span class="sxs-lookup"><span data-stu-id="a0aff-152">The abstract `MessageEncoderFactory` class provides a property named `Encoder` for accessing the current encoder and a method named `CreateSessionEncoder` for creating an encoder that supports sessions.</span></span> <span data-ttu-id="a0aff-153">Takové kodéru lze použít ve scénáři, kde kanál podporuje relace, je seřazený a spolehlivosti.</span><span class="sxs-lookup"><span data-stu-id="a0aff-153">Such an encoder can be used in the scenario where the channel supports sessions, is ordered and is reliable.</span></span> <span data-ttu-id="a0aff-154">Tento scénář umožňuje optimalizace v obou relacích data zapsaná do přenosu.</span><span class="sxs-lookup"><span data-stu-id="a0aff-154">This scenario allows for optimization in each session of the data written to the wire.</span></span> <span data-ttu-id="a0aff-155">Pokud to není žádoucí, by neměl přetížit základní metodu.</span><span class="sxs-lookup"><span data-stu-id="a0aff-155">If this is not desired, the base method should not be overloaded.</span></span> <span data-ttu-id="a0aff-156">`Encoder` Vlastnost poskytuje mechanismus pro přístup k relaci bez kodér a výchozí implementaci `CreateSessionEncoder` vrátí metoda hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a0aff-156">The `Encoder` property provides a mechanism for accessing the session-less encoder and the default implementation of the `CreateSessionEncoder` method returns the value of the property.</span></span> <span data-ttu-id="a0aff-157">Protože vzorku zabalí existující encoder stanovit komprese, `MessageEncoderFactory` implementace přijímá `MessageEncoderFactory` , který představuje objekt factory vnitřní kodér.</span><span class="sxs-lookup"><span data-stu-id="a0aff-157">Because the sample wraps an existing encoder to provide compression, the `MessageEncoderFactory` implementation accepts a `MessageEncoderFactory` that represents the inner encoder factory.</span></span>  
  
 <span data-ttu-id="a0aff-158">Teď, když jsou definovány encoder a kodér objekt pro vytváření, můžete použít pomocí klienta WCF a služeb.</span><span class="sxs-lookup"><span data-stu-id="a0aff-158">Now that the encoder and encoder factory are defined, they can be used with a WCF client and service.</span></span> <span data-ttu-id="a0aff-159">Tyto kodéry však musíte přidat do zásobníku kanálu.</span><span class="sxs-lookup"><span data-stu-id="a0aff-159">However, these encoders must be added to the channel stack.</span></span> <span data-ttu-id="a0aff-160">Lze odvodit z třídy <xref:System.ServiceModel.ServiceHost> a <xref:System.ServiceModel.ChannelFactory%601> třídy a přepsat `OnInitialize` metody pro tento objekt pro vytváření kodér přidat ručně.</span><span class="sxs-lookup"><span data-stu-id="a0aff-160">You can derive classes from the <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.ChannelFactory%601> classes and override the `OnInitialize` methods to add this encoder factory manually.</span></span> <span data-ttu-id="a0aff-161">Můžete také zveřejnit factory kodér prostřednictvím vlastní prvek vazby.</span><span class="sxs-lookup"><span data-stu-id="a0aff-161">You can also expose the encoder factory through a custom binding element.</span></span>  
  
 <span data-ttu-id="a0aff-162">Chcete-li vytvořit nové vlastní prvek vazby, odvoďte třídu z <xref:System.ServiceModel.Channels.BindingElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="a0aff-162">To create a new custom binding element, derive a class from the <xref:System.ServiceModel.Channels.BindingElement> class.</span></span> <span data-ttu-id="a0aff-163">Existuje však několik typů elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="a0aff-163">There are, however, several types of binding elements.</span></span> <span data-ttu-id="a0aff-164">Aby bylo zajištěno, že je vlastní prvek vazby rozpoznán jako element vazby kódování zprávy, je také nutné implementovat <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="a0aff-164">To ensure that the custom binding element is recognized as a message encoding binding element, you also must implement the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.</span></span> <span data-ttu-id="a0aff-165"><xref:System.ServiceModel.Channels.MessageEncodingBindingElement> Zpřístupní metodu pro vytvoření nového factory kodéru zpráv (`CreateMessageEncoderFactory`), které je implementováno s cílem vrátit instanci objektu pro vytváření odpovídající kodéru zpráv.</span><span class="sxs-lookup"><span data-stu-id="a0aff-165">The <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> exposes a method for creating a new message encoder factory (`CreateMessageEncoderFactory`), which is implemented to return an instance of the matching message encoder factory.</span></span> <span data-ttu-id="a0aff-166">Kromě toho <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> má vlastnost, která má označení verze adresování.</span><span class="sxs-lookup"><span data-stu-id="a0aff-166">Additionally, the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> has a property to indicate the addressing version.</span></span> <span data-ttu-id="a0aff-167">Protože tato ukázka zabalí existující kodérů, ukázková implementace také zabalí existující kodér elementů vazby a přebírá kodéru vnitřní element vazby jako parametr do konstruktoru a zpřístupní prostřednictvím vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a0aff-167">Because this sample wraps the existing encoders, the sample implementation also wraps the existing encoder binding elements and takes an inner encoder binding element as a parameter to the constructor and exposes it through a property.</span></span> <span data-ttu-id="a0aff-168">Následující ukázkový kód ukazuje implementaci `GZipMessageEncodingBindingElement` třídy.</span><span class="sxs-lookup"><span data-stu-id="a0aff-168">The following sample code shows the implementation of the `GZipMessageEncodingBindingElement` class.</span></span>  
  
```  
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
  
 <span data-ttu-id="a0aff-169">Všimněte si, že `GZipMessageEncodingBindingElement` implementuje třída `IPolicyExportExtension` rozhraní, takže tento element vazby se dá exportovat jako zásady v metadatech, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a0aff-169">Note that `GZipMessageEncodingBindingElement` class implements the `IPolicyExportExtension` interface, so that this binding element can be exported as a policy in metadata, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="a0aff-170">`GZipMessageEncodingBindingElementImporter` Implementuje třída `IPolicyImportExtension` rozhraní, tato třída Importuje zásady pro `GZipMessageEncodingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="a0aff-170">The `GZipMessageEncodingBindingElementImporter` class implements the `IPolicyImportExtension` interface, this class imports policy for `GZipMessageEncodingBindingElement`.</span></span> <span data-ttu-id="a0aff-171">Nástroje svcutil.exe lze použít pro import zásady do konfiguračního souboru, zpracování `GZipMessageEncodingBindingElement`, následující měla být přidána do Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="a0aff-171">Svcutil.exe tool can be used to import policies to the configuration file, to handle `GZipMessageEncodingBindingElement`, the following should be added to Svcutil.exe.config.</span></span>  
  
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
  
 <span data-ttu-id="a0aff-172">Teď, když je odpovídající prvek vazby pro kompresní kodér, ho můžete programově využívat do služby ani klienta vytváření nového objektu vlastní vazby a přidat vlastní prvek vazby, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="a0aff-172">Now that there is a matching binding element for the compression encoder, it can be programmatically hooked into the service or client by constructing a new custom binding object and adding the custom binding element to it, as shown in the following sample code.</span></span>  
  
```  
ICollection<BindingElement> bindingElements = new List<BindingElement>();  
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();  
GZipMessageEncodingBindingElement compBindingElement = new GZipMessageEncodingBindingElement ();  
bindingElements.Add(compBindingElement);  
bindingElements.Add(httpBindingElement);  
CustomBinding binding = new CustomBinding(bindingElements);  
binding.Name = "SampleBinding";  
binding.Namespace = "http://tempuri.org/bindings";  
```  
  
 <span data-ttu-id="a0aff-173">To může být dostatečné pro většinu scénářů uživatelů, podpora soubor konfigurace je velmi důležité, pokud má být hostované webové služby.</span><span class="sxs-lookup"><span data-stu-id="a0aff-173">While this may be sufficient for the majority of user scenarios, supporting a file configuration is critical if a service is to be Web-hosted.</span></span> <span data-ttu-id="a0aff-174">Pro podporu scénáři hostování webových, je třeba vytvořit obslužnou rutinu vlastní konfigurace na Povolit vlastní prvek vazby na umožňovat konfiguraci do souboru.</span><span class="sxs-lookup"><span data-stu-id="a0aff-174">To support the Web-hosted scenario, you must develop a custom configuration handler to allow a custom binding element to be configurable in a file.</span></span>  
  
 <span data-ttu-id="a0aff-175">Můžete vytvářet obslužné rutiny konfiguračního pro element vazby na konfigurační systém poskytované [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a0aff-175">You can build a configuration handler for the binding element on top of the configuration system provided by the [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span></span> <span data-ttu-id="a0aff-176">Obslužné rutiny konfiguračního elementu vazby musí být odvozen od <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="a0aff-176">The configuration handler for the binding element must derive from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="a0aff-177">`BindingElementType` Vlastnost se používá k informování konfigurační systém typ elementu vazby k vytvoření této části.</span><span class="sxs-lookup"><span data-stu-id="a0aff-177">The `BindingElementType` property is used to inform the configuration system of the type of binding element to create for this section.</span></span> <span data-ttu-id="a0aff-178">Všechny aspekty `BindingElement` , může být sada by měly být vystaveny jako vlastnosti <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="a0aff-178">All aspects of the `BindingElement` that can be set should be exposed as properties in the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class.</span></span> <span data-ttu-id="a0aff-179"><xref:System.Configuration.ConfigurationPropertyAttribute> Je použít jako pomůcku při mapování atributů elementu konfigurace vlastností a nastavení výchozí hodnoty, pokud jsou chybějící atributy.</span><span class="sxs-lookup"><span data-stu-id="a0aff-179">The <xref:System.Configuration.ConfigurationPropertyAttribute> is used to assist in mapping the configuration element attributes to the properties and setting default values if attributes are missing.</span></span> <span data-ttu-id="a0aff-180">Po hodnoty z konfigurace jsou načítány a použity k vlastnostem, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> metoda je volána, který převede na konkrétní instance elementu vazby vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a0aff-180">After the values from configuration are loaded and applied to the properties, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> method is called, which converts the properties into a concrete instance of a binding element.</span></span> <span data-ttu-id="a0aff-181"><xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A> Metoda se používá pro převod vlastnosti na <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> do hodnoty, které mají být nastaven pro element vazby newlycreated odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="a0aff-181">The <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A> method is used to convert the properties on the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class into the values to be set on the newlycreated binding element.</span></span>  
  
 <span data-ttu-id="a0aff-182">Následující ukázkový kód ukazuje implementaci `GZipMessageEncodingElement`.</span><span class="sxs-lookup"><span data-stu-id="a0aff-182">The following sample code shows the implementation of the `GZipMessageEncodingElement`.</span></span>  
  
```  
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
  
 <span data-ttu-id="a0aff-183">Tato obslužná rutina konfigurace mapuje následující reprezentaci v souboru App.config nebo Web.config pro službu nebo klienta.</span><span class="sxs-lookup"><span data-stu-id="a0aff-183">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>  
  
```xml  
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />  
```  
  
 <span data-ttu-id="a0aff-184">Pokud chcete použít tuto obslužnou rutinu konfigurace, je nutné jej zaregistrovat v rámci [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu, jak je znázorněno v následující ukázková konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a0aff-184">To use this configuration handler, it must be registered within the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="a0aff-185">Při spuštění serveru operace žádosti a odpovědi se zobrazí v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="a0aff-185">When you run the server, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="a0aff-186">Stisknutím klávesy ENTER v okně pro vypnutí serveru.</span><span class="sxs-lookup"><span data-stu-id="a0aff-186">Press ENTER in the window to shut down the server.</span></span>  
  
```  
Press Enter key to Exit.  
  
        Server Echo(string input) called:  
        Client message: Simple hello  
  
        Server BigEcho(string[] input) called:  
        64 client messages  
```  
  
 <span data-ttu-id="a0aff-187">Když spustíte klienta, operace žádosti a odpovědi se zobrazí v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="a0aff-187">When you run the client, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="a0aff-188">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="a0aff-188">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Calling Echo(string):  
Server responds: Simple hello Simple hello  
  
Calling BigEcho(string[]):  
Server responds: Hello 0  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a0aff-189">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="a0aff-189">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a0aff-190">Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="a0aff-190">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command:</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="a0aff-191">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a0aff-191">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="a0aff-192">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a0aff-192">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="a0aff-193">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a0aff-193">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a0aff-194">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="a0aff-194">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a0aff-195">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="a0aff-195">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a0aff-196">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="a0aff-196">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a0aff-197">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="a0aff-197">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="see-also"></a><span data-ttu-id="a0aff-198">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0aff-198">See Also</span></span>
