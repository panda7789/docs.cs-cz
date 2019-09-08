---
title: Konfigurace a podpora metadat
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: 16c386f8479778c7d2f17fbdfdb95dee558baf52
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795835"
---
# <a name="configuration-and-metadata-support"></a><span data-ttu-id="2bd2f-102">Konfigurace a podpora metadat</span><span class="sxs-lookup"><span data-stu-id="2bd2f-102">Configuration and Metadata Support</span></span>
<span data-ttu-id="2bd2f-103">Toto téma popisuje, jak povolit podporu konfigurace a metadat pro vazby a prvky vazby.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-103">This topic describes how to enable configuration and metadata support for bindings and binding elements.</span></span>  
  
## <a name="overview-of-configuration-and-metadata"></a><span data-ttu-id="2bd2f-104">Přehled konfigurace a metadat</span><span class="sxs-lookup"><span data-stu-id="2bd2f-104">Overview of Configuration and Metadata</span></span>  
 <span data-ttu-id="2bd2f-105">Toto téma popisuje následující úkoly, což jsou volitelné položky 1, 2 a 4 v seznamu úkolů [Vývoj kanálů](developing-channels.md) .</span><span class="sxs-lookup"><span data-stu-id="2bd2f-105">This topic discusses the following tasks, which are optional items 1, 2, and 4 in the [Developing Channels](developing-channels.md) task list.</span></span>  
  
- <span data-ttu-id="2bd2f-106">Povolení podpory konfiguračního souboru pro element vazby.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-106">Enabling configuration file support for a binding element.</span></span>  
  
- <span data-ttu-id="2bd2f-107">Povolení podpory konfiguračního souboru pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-107">Enabling configuration file support for a binding.</span></span>  
  
- <span data-ttu-id="2bd2f-108">Exportování kontrolních výrazů WSDL a zásad pro element vazby.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-108">Exporting WSDL and policy assertions for a binding element.</span></span>  
  
- <span data-ttu-id="2bd2f-109">Identifikují se kontrolní výrazy WSDL a zásad pro vložení a konfiguraci vazby nebo elementu vazby.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-109">Identifying WSDL and policy assertions to insert and configure your binding or binding element.</span></span>  
  
 <span data-ttu-id="2bd2f-110">Informace o vytváření uživatelsky definovaných vazeb a elementů vazby naleznete v tématu [vytváření uživatelsky definovaných vazeb](creating-user-defined-bindings.md) a [Vytvoření BindingElement](creating-a-bindingelement.md)(v uvedeném pořadí).</span><span class="sxs-lookup"><span data-stu-id="2bd2f-110">For information about creating user-defined bindings and binding elements, see [Creating User-Defined Bindings](creating-user-defined-bindings.md) and [Creating a BindingElement](creating-a-bindingelement.md), respectively.</span></span>  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="2bd2f-111">Přidání podpory konfigurace</span><span class="sxs-lookup"><span data-stu-id="2bd2f-111">Adding Configuration Support</span></span>  
 <span data-ttu-id="2bd2f-112">Chcete-li povolit podporu konfiguračního souboru pro kanál, je nutné implementovat dva konfigurační oddíly <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>,, což umožňuje podporu konfigurace pro prvky vazby <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> a a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, které povolují podporu konfigurace pro vazeb.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-112">To enable configuration file support for a channel, you must implement two configuration sections, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, which enables configuration support for binding elements, and the <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> and <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, which enable configuration support for bindings.</span></span>  
  
 <span data-ttu-id="2bd2f-113">Jednodušší způsob, jak to provést, je použít vzorový nástroj [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) k vygenerování konfiguračního kódu pro vaše vazby a prvky vazby.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-113">An easier way to do this is to use the [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) sample tool to generate configuration code for your bindings and binding elements.</span></span>  
  
### <a name="extending-bindingelementextensionelement"></a><span data-ttu-id="2bd2f-114">Rozšíření BindingElementExtensionElement</span><span class="sxs-lookup"><span data-stu-id="2bd2f-114">Extending BindingElementExtensionElement</span></span>  
 <span data-ttu-id="2bd2f-115">Následující příklad kódu je pořízen z [přenosu: Ukázka](../samples/transport-udp.md) UDP</span><span class="sxs-lookup"><span data-stu-id="2bd2f-115">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span> <span data-ttu-id="2bd2f-116">Je a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> zpřístupňuje`UdpTransportBindingElement`konfiguračnímusystému. `UdpTransportElement`</span><span class="sxs-lookup"><span data-stu-id="2bd2f-116">The `UdpTransportElement` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="2bd2f-117">U několika základních přepsání ukázka definuje název konfiguračního oddílu, typ prvku vazby a postup vytvoření prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-117">With a few basic overrides, the sample defines the configuration section name, the type of the binding element and how to create the binding element.</span></span> <span data-ttu-id="2bd2f-118">Uživatelé pak mohou zaregistrovat oddíl rozšíření v konfiguračním souboru následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-118">Users can then register the extension section in a configuration file as follows.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
      <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="2bd2f-119">Na rozšíření se dá odkazovat z vlastních vazeb na použití UDP jako přenosu.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-119">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="adding-configuration-for-a-binding"></a><span data-ttu-id="2bd2f-120">Přidání konfigurace pro vazbu</span><span class="sxs-lookup"><span data-stu-id="2bd2f-120">Adding Configuration for a Binding</span></span>  
 <span data-ttu-id="2bd2f-121">`SampleProfileUdpBinding` Oddíl `SampleProfileUdpBindingCollectionElement` ,kterýzveřejňujekonfiguračnímusystému<xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> .</span><span class="sxs-lookup"><span data-stu-id="2bd2f-121">The section `SampleProfileUdpBindingCollectionElement` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="2bd2f-122">Hromadná implementace je delegována na `SampleProfileUdpBindingConfigurationElement`, který je odvozen z. <xref:System.ServiceModel.Configuration.StandardBindingElement></span><span class="sxs-lookup"><span data-stu-id="2bd2f-122">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="2bd2f-123">Obsahuje vlastnosti, které odpovídají vlastnostem na `SampleProfileUdpBinding`, a `ConfigurationElement` funkce, které mají být mapovány z vazby. `SampleProfileUdpBindingConfigurationElement`</span><span class="sxs-lookup"><span data-stu-id="2bd2f-123">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="2bd2f-124">Nakonec je `SampleProfileUdpBinding`Metoda přepsána v, jak je znázorněno v následujícím ukázkovém kódu. `OnApplyConfiguration`</span><span class="sxs-lookup"><span data-stu-id="2bd2f-124">Finally, the `OnApplyConfiguration` method is overridden in the `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
```csharp 
protected override void OnApplyConfiguration(string configurationName)  
{  
            if (binding == null)  
                throw new ArgumentNullException("binding");  
  
            if (binding.GetType() != typeof(SampleProfileUdpBinding))  
            {  
                throw new ArgumentException(string.Format(CultureInfo.CurrentCulture,  
                    "Invalid type for binding. Expected type: {0}. Type passed in: {1}.",  
                    typeof(SampleProfileUdpBinding).AssemblyQualifiedName,  
                    binding.GetType().AssemblyQualifiedName));  
            }  
            SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;  
  
            udpBinding.OrderedSession = this.OrderedSession;  
            udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;  
            udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;  
            if (this.ClientBaseAddress != null)  
                   udpBinding.ClientBaseAddress = ClientBaseAddress;  
}  
```  
  
 <span data-ttu-id="2bd2f-125">K registraci této obslužné rutiny pomocí konfiguračního systému přidejte následující oddíl do příslušného konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-125">To register this handler with the configuration system, add the following section to the relevant configuration file.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
         <sectionGroup name="bindings">  
                 <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport />  
         </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 <span data-ttu-id="2bd2f-126">Pak na něj můžete odkazovat z [ \<konfiguračního oddílu System. ServiceModel >](../../configure-apps/file-schema/wcf/system-servicemodel.md) .</span><span class="sxs-lookup"><span data-stu-id="2bd2f-126">It can then be referenced from the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) configuration section.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"   
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"   
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="adding-metadata-support-for-a-binding-element"></a><span data-ttu-id="2bd2f-127">Přidání podpory metadat pro element vazby</span><span class="sxs-lookup"><span data-stu-id="2bd2f-127">Adding Metadata Support for a Binding Element</span></span>  
 <span data-ttu-id="2bd2f-128">Pro integraci kanálu do systému metadat musí podporovat import i export zásad.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-128">To integrate a channel into the metadata system, it must support both the import and export of policy.</span></span> <span data-ttu-id="2bd2f-129">To umožňuje nástrojům, jako je nástroj pro dodávání [metadat ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) , generovat klienty elementu vazby.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-129">This allows tools such as [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate clients of the binding element.</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="2bd2f-130">Přidání podpory WSDL</span><span class="sxs-lookup"><span data-stu-id="2bd2f-130">Adding WSDL Support</span></span>  
 <span data-ttu-id="2bd2f-131">Element vazby přenosu ve vazbě zodpovídá za export a import informací o adresách v metadatech.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-131">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="2bd2f-132">Při použití vazby SOAP by měl element vazby přenosu také exportovat správný přenosový identifikátor URI v metadatech.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-132">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span> <span data-ttu-id="2bd2f-133">Následující příklad kódu je pořízen z [přenosu: Ukázka](../samples/transport-udp.md) UDP</span><span class="sxs-lookup"><span data-stu-id="2bd2f-133">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="2bd2f-134">Export WSDL</span><span class="sxs-lookup"><span data-stu-id="2bd2f-134">WSDL Export</span></span>  
 <span data-ttu-id="2bd2f-135">Chcete-li exportovat informace o `UdpTransportBindingElement` adresách <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> , implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-135">To export addressing information, the `UdpTransportBindingElement` implements the <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="2bd2f-136"><xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> Metoda přidá správné informace o adresování do portu WSDL.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-136">The <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="2bd2f-137">`UdpTransportBindingElement` Implementace<xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> metody také exportuje identifikátor URI přenosu, pokud koncový bod používá vazbu SOAP:</span><span class="sxs-lookup"><span data-stu-id="2bd2f-137">The `UdpTransportBindingElement` implementation of the <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> method also exports a transport URI when the endpoint uses a SOAP binding:</span></span>  
  
```csharp  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="2bd2f-138">Import WSDL</span><span class="sxs-lookup"><span data-stu-id="2bd2f-138">WSDL Import</span></span>  
 <span data-ttu-id="2bd2f-139">Chcete-li roztáhnout systém importu WSDL pro zpracování importu adres, přidejte následující konfiguraci do konfiguračního souboru pro Svcutil. exe, jak je znázorněno v souboru Svcutil. exe. config:</span><span class="sxs-lookup"><span data-stu-id="2bd2f-139">To extend the WSDL import system to handle importing the addresses, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="2bd2f-140">Při spuštění Svcutil. exe jsou k dispozici dvě možnosti, jak Svcutil. exe načíst rozšíření importu WSDL:</span><span class="sxs-lookup"><span data-stu-id="2bd2f-140">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="2bd2f-141">Najeďte Svcutil. exe na konfigurační soubor pomocí souboru/SvcutilConfig:\<>.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-141">Point Svcutil.exe to the configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="2bd2f-142">Přidejte konfigurační oddíl do souboru Svcutil. exe. config ve stejném adresáři jako soubor Svcutil. exe.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-142">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="2bd2f-143">`UdpBindingElementImporter` Typ<xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-143">The `UdpBindingElementImporter` type implements the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="2bd2f-144">`ImportEndpoint` Metoda importuje adresu z portu WSDL:</span><span class="sxs-lookup"><span data-stu-id="2bd2f-144">The `ImportEndpoint` method imports the address from the WSDL port:</span></span>  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="2bd2f-145">Přidání podpory zásad</span><span class="sxs-lookup"><span data-stu-id="2bd2f-145">Adding Policy Support</span></span>  
 <span data-ttu-id="2bd2f-146">Vlastní element vazby může exportovat kontrolní výrazy zásad ve vazbě WSDL pro koncový bod služby, aby bylo možné vyjádřit možnosti tohoto prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-146">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span> <span data-ttu-id="2bd2f-147">Následující příklad kódu je pořízen z [přenosu: Ukázka](../samples/transport-udp.md) UDP</span><span class="sxs-lookup"><span data-stu-id="2bd2f-147">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="2bd2f-148">Export zásad</span><span class="sxs-lookup"><span data-stu-id="2bd2f-148">Policy Export</span></span>  
 <span data-ttu-id="2bd2f-149">`UdpTransportBindingElement` Typ implementuje<xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> k přidání podpory pro export zásad.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-149">The `UdpTransportBindingElement` type implements <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> to add support for exporting policy.</span></span> <span data-ttu-id="2bd2f-150">Výsledkem je, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> že zahrnuje `UdpTransportBindingElement` generování zásad pro všechny vazby, které ji obsahují.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-150">As a result, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="2bd2f-151">V <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>přidejte kontrolní výraz pro UDP a jiný kontrolní výraz, pokud je kanál v režimu vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-151">In <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, add an assertion for UDP and another assertion if the channel is in multicast mode.</span></span> <span data-ttu-id="2bd2f-152">Je to proto, že režim vícesměrového vysílání ovlivňuje způsob, jakým je vytvořen komunikační zásobník, a proto musí být koordinován mezi oběma stranami.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-152">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
```csharp  
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.MulticastAssertion,     UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 <span data-ttu-id="2bd2f-153">Vzhledem k tomu, že vlastní prvky vazby přenosu jsou zodpovědné za <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> zpracování adresování `UdpTransportBindingElement` , implementace na musí také zpracovávat příslušné kontrolní výrazy WS-Addressing, aby označovaly verzi elementu WS-Addressing. používá se.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-153">Because custom transport binding elements are responsible for handling addressing, the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="2bd2f-154">Import zásad</span><span class="sxs-lookup"><span data-stu-id="2bd2f-154">Policy Import</span></span>  
 <span data-ttu-id="2bd2f-155">Chcete-li přidat systém pro import zásad, přidejte následující konfiguraci do konfiguračního souboru pro Svcutil. exe, jak je znázorněno v souboru Svcutil. exe. config:</span><span class="sxs-lookup"><span data-stu-id="2bd2f-155">To extend the policy import system, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="2bd2f-156">Pak implementujeme <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> z naší registrované třídy (`UdpBindingElementImporter`).</span><span class="sxs-lookup"><span data-stu-id="2bd2f-156">Then we implement <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="2bd2f-157">V <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, Prověřte kontrolní výrazy v příslušném oboru názvů a zpracujte je pro generování přenosu a kontrolu, jestli se jedná o vícesměrové vysílání.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-157">In <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, examine the assertions in the appropriate namespace and process the ones for generating the transport and checking if it is multicast.</span></span> <span data-ttu-id="2bd2f-158">Kromě toho odeberte kontrolní výrazy, které dovozce zpracovává ze seznamu kontrolních výrazů vazby.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-158">In addition, remove the assertions that the importer handles from the list of binding assertions.</span></span> <span data-ttu-id="2bd2f-159">Při spuštění Svcutil. exe existují dvě možnosti integrace:</span><span class="sxs-lookup"><span data-stu-id="2bd2f-159">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="2bd2f-160">Najeďte Svcutil. exe na náš konfigurační soubor pomocí souboru/svcutilConfig\<: >.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-160">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="2bd2f-161">Přidejte konfigurační oddíl do souboru Svcutil. exe. config ve stejném adresáři jako soubor Svcutil. exe.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-161">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="2bd2f-162">Přidání vlastního programu pro import standardních vazeb</span><span class="sxs-lookup"><span data-stu-id="2bd2f-162">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="2bd2f-163">Svcutil. exe a <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> typ, ve výchozím nastavení rozpoznávají a naimportují vazby poskytnuté systémem.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-163">Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> type, by default, recognize and import system-provided bindings.</span></span> <span data-ttu-id="2bd2f-164">V opačném případě se vazba naimportuje jako <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-164">Otherwise, the binding gets imported as a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="2bd2f-165">Chcete-li povolit Svcutil. exe <xref:System.ServiceModel.Description.WsdlImporter> a `SampleProfileUdpBinding` importovat `UdpBindingElementImporter` také jako vlastní import standardních vazeb.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-165">To enable Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter> to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="2bd2f-166">Vlastní nástroj `ImportEndpoint` <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> pro import standardních vazeb implementuje metodu na rozhraníprokontroluinstanceimportovanézmetadat,abybylomožnézjistit,zdabymohlabýtvygenerovánakonkrétnístandardnívazbou.<xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="2bd2f-166">A custom standard binding importer implements the `ImportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface to examine the <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance imported from metadata to see if it could have been generated by specific standard binding.</span></span>  
  
```csharp  
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="2bd2f-167">Obecně implementace vlastního programu pro importování standardní vazby zahrnuje kontrolu vlastností importovaných prvků vazby, aby bylo možné ověřit, zda byly změněny pouze vlastnosti, které by mohly být nastaveny standardní vazbou, a všechny ostatní vlastnosti jsou jejich výchozími hodnotami.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-167">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="2bd2f-168">Základní strategií pro implementaci programu pro import standardních vazeb je vytvoření instance standardní vazby, šíření vlastností z prvků vazby na standardní instanci vazby, kterou podporuje standardní vazba, a porovnáním vazby prvky ze standardní vazby s importovanými prvky vazby.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-168">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>
