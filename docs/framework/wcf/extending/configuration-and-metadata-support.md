---
title: Konfigurace a podpora metadat
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: abc9177fcc7b338a365d61721b63041ddcd68ab9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59769434"
---
# <a name="configuration-and-metadata-support"></a><span data-ttu-id="68a08-102">Konfigurace a podpora metadat</span><span class="sxs-lookup"><span data-stu-id="68a08-102">Configuration and Metadata Support</span></span>
<span data-ttu-id="68a08-103">Toto téma popisuje, jak povolit podporu konfigurace a metadat pro vazby a prvky vazeb.</span><span class="sxs-lookup"><span data-stu-id="68a08-103">This topic describes how to enable configuration and metadata support for bindings and binding elements.</span></span>  
  
## <a name="overview-of-configuration-and-metadata"></a><span data-ttu-id="68a08-104">Přehled konfigurace a metadat</span><span class="sxs-lookup"><span data-stu-id="68a08-104">Overview of Configuration and Metadata</span></span>  
 <span data-ttu-id="68a08-105">Toto téma popisuje následující úkoly, které jsou volitelné položky 1, 2 a 4 v [vývoj kanálů](../../../../docs/framework/wcf/extending/developing-channels.md) seznamu úkolů.</span><span class="sxs-lookup"><span data-stu-id="68a08-105">This topic discusses the following tasks, which are optional items 1, 2, and 4 in the [Developing Channels](../../../../docs/framework/wcf/extending/developing-channels.md) task list.</span></span>  
  
-   <span data-ttu-id="68a08-106">Povolení podpory konfigurační soubor pro element vazby.</span><span class="sxs-lookup"><span data-stu-id="68a08-106">Enabling configuration file support for a binding element.</span></span>  
  
-   <span data-ttu-id="68a08-107">Povolení podpory konfigurační soubor pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="68a08-107">Enabling configuration file support for a binding.</span></span>  
  
-   <span data-ttu-id="68a08-108">Export kontrolních výrazů WSDL a zásady pro element vazby.</span><span class="sxs-lookup"><span data-stu-id="68a08-108">Exporting WSDL and policy assertions for a binding element.</span></span>  
  
-   <span data-ttu-id="68a08-109">Identifikace WSDL a zásady kontrolní výrazy pro vložení a nakonfigurujte vazby nebo element vazby.</span><span class="sxs-lookup"><span data-stu-id="68a08-109">Identifying WSDL and policy assertions to insert and configure your binding or binding element.</span></span>  
  
 <span data-ttu-id="68a08-110">Informace o vytváření uživatelem definovaných vazeb a prvky vazeb naleznete v tématu [Creating User-Defined vazby](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md) a [vytvoření BindingElement](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md)v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="68a08-110">For information about creating user-defined bindings and binding elements, see [Creating User-Defined Bindings](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md) and [Creating a BindingElement](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md), respectively.</span></span>  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="68a08-111">Přidání podpory konfigurace</span><span class="sxs-lookup"><span data-stu-id="68a08-111">Adding Configuration Support</span></span>  
 <span data-ttu-id="68a08-112">Povolení podpory konfigurační soubor pro kanál, je nutné implementovat dva oddíly konfigurace, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, která podporuje konfiguraci elementů, vazby a <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, umožňující podporu konfigurace pro vazby.</span><span class="sxs-lookup"><span data-stu-id="68a08-112">To enable configuration file support for a channel, you must implement two configuration sections, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, which enables configuration support for binding elements, and the <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> and <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, which enable configuration support for bindings.</span></span>  
  
 <span data-ttu-id="68a08-113">Snadný způsob, jak to provést, je použít [ConfigurationCodeGenerator](../../../../docs/framework/wcf/samples/configurationcodegenerator.md) ukázkový nástroj pro generování kódu konfigurace pro vazby a prvky vazeb.</span><span class="sxs-lookup"><span data-stu-id="68a08-113">An easier way to do this is to use the [ConfigurationCodeGenerator](../../../../docs/framework/wcf/samples/configurationcodegenerator.md) sample tool to generate configuration code for your bindings and binding elements.</span></span>  
  
### <a name="extending-bindingelementextensionelement"></a><span data-ttu-id="68a08-114">Rozšíření BindingElementExtensionElement</span><span class="sxs-lookup"><span data-stu-id="68a08-114">Extending BindingElementExtensionElement</span></span>  
 <span data-ttu-id="68a08-115">Následující vzorový kód je převzat z [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="68a08-115">The following example code is taken from the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="68a08-116">`UdpTransportElement` Je <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> , která zveřejní `UdpTransportBindingElement` k systému konfigurace.</span><span class="sxs-lookup"><span data-stu-id="68a08-116">The `UdpTransportElement` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="68a08-117">Několik základních lokálně ukázka definuje název oddílu konfigurace, typ elementu vazby a tom, jak vytvořit element vazby.</span><span class="sxs-lookup"><span data-stu-id="68a08-117">With a few basic overrides, the sample defines the configuration section name, the type of the binding element and how to create the binding element.</span></span> <span data-ttu-id="68a08-118">Uživatelé můžou potom registrovat oddílu rozšíření v konfiguračním souboru následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="68a08-118">Users can then register the extension section in a configuration file as follows.</span></span>  
  
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
  
 <span data-ttu-id="68a08-119">Rozšíření můžete odkazovat z vlastní vazby pro použití jako přenos UDP.</span><span class="sxs-lookup"><span data-stu-id="68a08-119">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
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
  
### <a name="adding-configuration-for-a-binding"></a><span data-ttu-id="68a08-120">Přidává se konfigurace pro vazbu</span><span class="sxs-lookup"><span data-stu-id="68a08-120">Adding Configuration for a Binding</span></span>  
 <span data-ttu-id="68a08-121">V části `SampleProfileUdpBindingCollectionElement` je <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> , která zveřejní `SampleProfileUdpBinding` k systému konfigurace.</span><span class="sxs-lookup"><span data-stu-id="68a08-121">The section `SampleProfileUdpBindingCollectionElement` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="68a08-122">Hromadné implementace se deleguje na `SampleProfileUdpBindingConfigurationElement`, která je odvozena z <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="68a08-122">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="68a08-123">`SampleProfileUdpBindingConfigurationElement` Má vlastnosti, které odpovídají vlastnostem v `SampleProfileUdpBinding`a funkce mapování `ConfigurationElement` vazby.</span><span class="sxs-lookup"><span data-stu-id="68a08-123">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="68a08-124">Nakonec `OnApplyConfiguration` v je přepsána metoda `SampleProfileUdpBinding`, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="68a08-124">Finally, the `OnApplyConfiguration` method is overridden in the `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="68a08-125">K registraci této obslužné rutiny konfigurace systému, přidejte následující část do souboru položky konfigurace.</span><span class="sxs-lookup"><span data-stu-id="68a08-125">To register this handler with the configuration system, add the following section to the relevant configuration file.</span></span>  
  
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
  
 <span data-ttu-id="68a08-126">Poté jej lze odkazovat z [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="68a08-126">It can then be referenced from the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) configuration section.</span></span>  
  
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
  
## <a name="adding-metadata-support-for-a-binding-element"></a><span data-ttu-id="68a08-127">Přidání podpory metadat pro Element vazby</span><span class="sxs-lookup"><span data-stu-id="68a08-127">Adding Metadata Support for a Binding Element</span></span>  
 <span data-ttu-id="68a08-128">K integraci kanál do metadat systému, musí podporovat, import a export zásad.</span><span class="sxs-lookup"><span data-stu-id="68a08-128">To integrate a channel into the metadata system, it must support both the import and export of policy.</span></span> <span data-ttu-id="68a08-129">Díky tomu nástroje, jako [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování klientů elementu vazby.</span><span class="sxs-lookup"><span data-stu-id="68a08-129">This allows tools such as [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate clients of the binding element.</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="68a08-130">Přidání podpory WSDL</span><span class="sxs-lookup"><span data-stu-id="68a08-130">Adding WSDL Support</span></span>  
 <span data-ttu-id="68a08-131">Element vazby přenosu ve vazbě je zodpovědná za export a import informací o adresách v metadatech.</span><span class="sxs-lookup"><span data-stu-id="68a08-131">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="68a08-132">Při použití vazby protokolu SOAP, element vazby přenosu by měl také exportovat správné přepravy identifikátoru URI v metadatech.</span><span class="sxs-lookup"><span data-stu-id="68a08-132">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span> <span data-ttu-id="68a08-133">Následující vzorový kód je převzat z [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="68a08-133">The following example code is taken from the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="68a08-134">WSDL Export</span><span class="sxs-lookup"><span data-stu-id="68a08-134">WSDL Export</span></span>  
 <span data-ttu-id="68a08-135">Chcete-li exportovat informace o adresách, `UdpTransportBindingElement` implementuje <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="68a08-135">To export addressing information, the `UdpTransportBindingElement` implements the <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="68a08-136"><xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> Metoda přidá správné informace o adresování na WSDL port.</span><span class="sxs-lookup"><span data-stu-id="68a08-136">The <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="68a08-137">`UdpTransportBindingElement` Provádění <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> metoda zároveň exportuje přepravy identifikátoru URI při koncový bod používá vazba SOAP:</span><span class="sxs-lookup"><span data-stu-id="68a08-137">The `UdpTransportBindingElement` implementation of the <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> method also exports a transport URI when the endpoint uses a SOAP binding:</span></span>  
  
```csharp  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="68a08-138">WSDL Import</span><span class="sxs-lookup"><span data-stu-id="68a08-138">WSDL Import</span></span>  
 <span data-ttu-id="68a08-139">Rozšíření systému importu WSDL pro zpracování importu adres, přidejte do konfiguračního souboru pro Svcutil.exe jak je znázorněno v souboru Svcutil.exe.config následující konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="68a08-139">To extend the WSDL import system to handle importing the addresses, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
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
  
 <span data-ttu-id="68a08-140">Při spuštění Svcutil.exe, existují dvě možnosti pro získání Svcutil.exe k načítání rozšíření importu WSDL:</span><span class="sxs-lookup"><span data-stu-id="68a08-140">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="68a08-141">Bod Svcutil.exe do konfiguračního souboru pomocí /SvcutilConfig:\<soubor >.</span><span class="sxs-lookup"><span data-stu-id="68a08-141">Point Svcutil.exe to the configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="68a08-142">Přidáte konfigurační oddíl pro Svcutil.exe.config ve stejném adresáři jako Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="68a08-142">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="68a08-143">`UdpBindingElementImporter` Typ implementuje <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="68a08-143">The `UdpBindingElementImporter` type implements the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="68a08-144">`ImportEndpoint` Metoda importuje adresu z portu WSDL:</span><span class="sxs-lookup"><span data-stu-id="68a08-144">The `ImportEndpoint` method imports the address from the WSDL port:</span></span>  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="68a08-145">Přidání podpory pro zásady</span><span class="sxs-lookup"><span data-stu-id="68a08-145">Adding Policy Support</span></span>  
 <span data-ttu-id="68a08-146">Vlastní prvek vazby můžete export kontrolních výrazů zásad Vazba WSDL pro koncový bod služby vyjádřit možnosti daného prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="68a08-146">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span> <span data-ttu-id="68a08-147">Následující vzorový kód je převzat z [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="68a08-147">The following example code is taken from the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="68a08-148">Export zásad</span><span class="sxs-lookup"><span data-stu-id="68a08-148">Policy Export</span></span>  
 <span data-ttu-id="68a08-149">`UdpTransportBindingElement` Typ implementuje <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> přidává funkce pro export zásad.</span><span class="sxs-lookup"><span data-stu-id="68a08-149">The `UdpTransportBindingElement` type implements <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> to add support for exporting policy.</span></span> <span data-ttu-id="68a08-150">V důsledku toho <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> zahrnuje `UdpTransportBindingElement` při generování zásad pro všechny vazby, který ji obsahuje.</span><span class="sxs-lookup"><span data-stu-id="68a08-150">As a result, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="68a08-151">V <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, přidat kontrolní výraz pro UDP a další kontrolní výraz, pokud kanál není v režimu vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="68a08-151">In <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, add an assertion for UDP and another assertion if the channel is in multicast mode.</span></span> <span data-ttu-id="68a08-152">Jak komunikačního balíku je vytvořen a proto musí být koordinovaní mezi obě strany jde vzhledem k tomu, že má vliv na režimu vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="68a08-152">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
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
  
 <span data-ttu-id="68a08-153">Protože jsou zodpovědného za obsluhu adresování elementů přenosové vlastní vazby <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementace v prostředí `UdpTransportBindingElement` musí také zpracovat export odpovídající WS-Addressing kontrolní výrazy zásad označující verzi elementu WS-Addressing používá.</span><span class="sxs-lookup"><span data-stu-id="68a08-153">Because custom transport binding elements are responsible for handling addressing, the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="68a08-154">Import zásady</span><span class="sxs-lookup"><span data-stu-id="68a08-154">Policy Import</span></span>  
 <span data-ttu-id="68a08-155">Rozšíření systému importovat zásady, přidejte následující konfiguraci do konfiguračního souboru pro Svcutil.exe jak je znázorněno v souboru Svcutil.exe.config:</span><span class="sxs-lookup"><span data-stu-id="68a08-155">To extend the policy import system, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
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
  
 <span data-ttu-id="68a08-156">Pak můžeme implementovat <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> z našich registrované třídy (`UdpBindingElementImporter`).</span><span class="sxs-lookup"><span data-stu-id="68a08-156">Then we implement <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="68a08-157">V <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, zkontrolujte kontrolní výrazy ve odpovídající obor názvů a zpracovat pro generování přenos a kontrola, zda je vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="68a08-157">In <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, examine the assertions in the appropriate namespace and process the ones for generating the transport and checking if it is multicast.</span></span> <span data-ttu-id="68a08-158">Kontrolní výrazy, které zpracovává tabulkách navíc odeberte ze seznamu vazby kontrolní výrazy.</span><span class="sxs-lookup"><span data-stu-id="68a08-158">In addition, remove the assertions that the importer handles from the list of binding assertions.</span></span> <span data-ttu-id="68a08-159">Znovu když spustíte Svcutil.exe, existují dvě možnosti pro integraci:</span><span class="sxs-lookup"><span data-stu-id="68a08-159">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="68a08-160">Bod Svcutil.exe k naší konfiguračního souboru pomocí /SvcutilConfig:\<soubor >.</span><span class="sxs-lookup"><span data-stu-id="68a08-160">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="68a08-161">Přidáte konfigurační oddíl pro Svcutil.exe.config ve stejném adresáři jako Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="68a08-161">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="68a08-162">Přidání vlastní standardní vazby programu pro import</span><span class="sxs-lookup"><span data-stu-id="68a08-162">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="68a08-163">Svcutil.exe a <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> typ, ve výchozím nastavení, rozpoznat a import vazeb poskytovaných systémem.</span><span class="sxs-lookup"><span data-stu-id="68a08-163">Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> type, by default, recognize and import system-provided bindings.</span></span> <span data-ttu-id="68a08-164">V opačném případě získá importovat, protože vazba <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance.</span><span class="sxs-lookup"><span data-stu-id="68a08-164">Otherwise, the binding gets imported as a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="68a08-165">Povolit Svcutil.exe a <xref:System.ServiceModel.Description.WsdlImporter> import `SampleProfileUdpBinding` `UdpBindingElementImporter` taky pracuje jako import standardní vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="68a08-165">To enable Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter> to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="68a08-166">Implementuje programu pro import standardní vlastní vazby `ImportEndpoint` metodu na <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> rozhraní k prozkoumání <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance naimportované z metadat zobrazíte, pokud to může být vygenerováno konkrétní standardní vazbu.</span><span class="sxs-lookup"><span data-stu-id="68a08-166">A custom standard binding importer implements the `ImportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface to examine the <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance imported from metadata to see if it could have been generated by specific standard binding.</span></span>  
  
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
  
 <span data-ttu-id="68a08-167">Obecně platí implementace programu pro import vlastních vazeb standard zahrnuje ověření vlastností elementů importované vazby k ověření, že jste změnili pouze vlastnosti, které může nastavit standardní vazbou a všechny ostatní vlastnosti se jejich výchozích hodnotách.</span><span class="sxs-lookup"><span data-stu-id="68a08-167">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="68a08-168">Základní strategií pro implementaci standardní vazbu Importér je vytvoření instance standardní vazbu, rozšíří vlastnosti z elementů vazby instanci standardní vazbu, která podporuje standardní vazbu, a porovnat vazby elementy ze standardní vazba s prvky importované vazby.</span><span class="sxs-lookup"><span data-stu-id="68a08-168">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>
