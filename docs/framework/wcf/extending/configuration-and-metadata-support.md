---
title: Konfigurace a podpora metadat
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aa728f64b336cc13ae515838fb7ff5c98c742d10
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="configuration-and-metadata-support"></a><span data-ttu-id="7d992-102">Konfigurace a podpora metadat</span><span class="sxs-lookup"><span data-stu-id="7d992-102">Configuration and Metadata Support</span></span>
<span data-ttu-id="7d992-103">Toto téma popisuje, jak povolit podporu konfigurace a metadat pro vazby a prvky vazeb.</span><span class="sxs-lookup"><span data-stu-id="7d992-103">This topic describes how to enable configuration and metadata support for bindings and binding elements.</span></span>  
  
## <a name="overview-of-configuration-and-metadata"></a><span data-ttu-id="7d992-104">Přehled konfigurace a metadat</span><span class="sxs-lookup"><span data-stu-id="7d992-104">Overview of Configuration and Metadata</span></span>  
 <span data-ttu-id="7d992-105">Toto téma popisuje následující úlohy, které jsou volitelné položky 1, 2 a 4 v [rozvojových kanály](../../../../docs/framework/wcf/extending/developing-channels.md) seznamu úloh.</span><span class="sxs-lookup"><span data-stu-id="7d992-105">This topic discusses the following tasks, which are optional items 1, 2, and 4 in the [Developing Channels](../../../../docs/framework/wcf/extending/developing-channels.md) task list.</span></span>  
  
-   <span data-ttu-id="7d992-106">Povolení podpory souboru konfigurace pro prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="7d992-106">Enabling configuration file support for a binding element.</span></span>  
  
-   <span data-ttu-id="7d992-107">Povolení podpory souboru konfigurace pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="7d992-107">Enabling configuration file support for a binding.</span></span>  
  
-   <span data-ttu-id="7d992-108">Export kontrolních výrazů WSDL a zásady pro prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="7d992-108">Exporting WSDL and policy assertions for a binding element.</span></span>  
  
-   <span data-ttu-id="7d992-109">Identifikace WSDL a zásady kontrolní výrazy insert a nakonfigurovat vazby nebo prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="7d992-109">Identifying WSDL and policy assertions to insert and configure your binding or binding element.</span></span>  
  
 <span data-ttu-id="7d992-110">Informace o vytváření uživatelem definované vazby a prvky vazeb najdete v tématu [Creating User-Defined vazby](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md) a [vytvoření BindingElement](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md), v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="7d992-110">For information about creating user-defined bindings and binding elements, see [Creating User-Defined Bindings](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md) and [Creating a BindingElement](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md), respectively.</span></span>  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="7d992-111">Přidání podpory konfigurace</span><span class="sxs-lookup"><span data-stu-id="7d992-111">Adding Configuration Support</span></span>  
 <span data-ttu-id="7d992-112">Povolit podporu souboru konfigurace pro kanál, je nutné implementovat dvě konfiguračních oddílů, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, což umožňuje podporu konfigurace pro elementů, vazby a <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, která umožňují podporu konfigurace pro vazby.</span><span class="sxs-lookup"><span data-stu-id="7d992-112">To enable configuration file support for a channel, you must implement two configuration sections, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, which enables configuration support for binding elements, and the <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> and <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, which enable configuration support for bindings.</span></span>  
  
 <span data-ttu-id="7d992-113">Snadný způsob, jak to udělat, je použití [ConfigurationCodeGenerator](../../../../docs/framework/wcf/samples/configurationcodegenerator.md) ukázkový nástroj pro generování kódu konfigurace pro vazby a prvky vazeb.</span><span class="sxs-lookup"><span data-stu-id="7d992-113">An easier way to do this is to use the [ConfigurationCodeGenerator](../../../../docs/framework/wcf/samples/configurationcodegenerator.md) sample tool to generate configuration code for your bindings and binding elements.</span></span>  
  
### <a name="extending-bindingelementextensionelement"></a><span data-ttu-id="7d992-114">Rozšíření BindingElementExtensionElement</span><span class="sxs-lookup"><span data-stu-id="7d992-114">Extending BindingElementExtensionElement</span></span>  
 <span data-ttu-id="7d992-115">Následující příklad kódu jsou převzaty z [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="7d992-115">The following example code is taken from the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="7d992-116">`UdpTransportElement` Je <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> která zveřejňuje `UdpTransportBindingElement` v konfiguraci systému.</span><span class="sxs-lookup"><span data-stu-id="7d992-116">The `UdpTransportElement` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="7d992-117">S několika základní přepsání ukázky definuje název konfiguračního oddílu, typ elementu vazby a postup vytvoření prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="7d992-117">With a few basic overrides, the sample defines the configuration section name, the type of the binding element and how to create the binding element.</span></span> <span data-ttu-id="7d992-118">Uživatelé můžou potom zaregistrovat části rozšíření v konfiguračním souboru následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="7d992-118">Users can then register the extension section in a configuration file as follows.</span></span>  
  
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
  
 <span data-ttu-id="7d992-119">Rozšíření můžete odkazovat z vlastních vazeb, používat UDP jako přenosu.</span><span class="sxs-lookup"><span data-stu-id="7d992-119">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
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
  
### <a name="adding-configuration-for-a-binding"></a><span data-ttu-id="7d992-120">Přidává se konfigurace vazby</span><span class="sxs-lookup"><span data-stu-id="7d992-120">Adding Configuration for a Binding</span></span>  
 <span data-ttu-id="7d992-121">V části `SampleProfileUdpBindingCollectionElement` je <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> která zveřejňuje `SampleProfileUdpBinding` v konfiguraci systému.</span><span class="sxs-lookup"><span data-stu-id="7d992-121">The section `SampleProfileUdpBindingCollectionElement` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="7d992-122">Hromadné implementace je delegovaný jako `SampleProfileUdpBindingConfigurationElement`, která je odvozena z <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="7d992-122">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="7d992-123">`SampleProfileUdpBindingConfigurationElement` Má vlastnosti, které odpovídají vlastnosti na `SampleProfileUdpBinding`a funkce pro mapování z `ConfigurationElement` vazby.</span><span class="sxs-lookup"><span data-stu-id="7d992-123">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="7d992-124">Nakonec `OnApplyConfiguration` je metoda potlačena v `SampleProfileUdpBinding`, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="7d992-124">Finally, the `OnApplyConfiguration` method is overridden in the `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="7d992-125">K registraci této obslužné rutiny konfigurace systému, přidejte do příslušných konfiguračního souboru v následující části.</span><span class="sxs-lookup"><span data-stu-id="7d992-125">To register this handler with the configuration system, add the following section to the relevant configuration file.</span></span>  
  
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
  
 <span data-ttu-id="7d992-126">Lze ji pak odkazovat z [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="7d992-126">It can then be referenced from the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) configuration section.</span></span>  
  
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
  
## <a name="adding-metadata-support-for-a-binding-element"></a><span data-ttu-id="7d992-127">Přidání podpory Metadata pro Element vazby</span><span class="sxs-lookup"><span data-stu-id="7d992-127">Adding Metadata Support for a Binding Element</span></span>  
 <span data-ttu-id="7d992-128">Kanál, který se integruje do systém metadat, musí podporovat, import a export zásad.</span><span class="sxs-lookup"><span data-stu-id="7d992-128">To integrate a channel into the metadata system, it must support both the import and export of policy.</span></span> <span data-ttu-id="7d992-129">To umožňuje nástroje, jako [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování klienti prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="7d992-129">This allows tools such as [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate clients of the binding element.</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="7d992-130">Přidání podpory WSDL</span><span class="sxs-lookup"><span data-stu-id="7d992-130">Adding WSDL Support</span></span>  
 <span data-ttu-id="7d992-131">Element vazby přenosu ve vazbě zodpovídá pro export a import informací o adresách v metadatech.</span><span class="sxs-lookup"><span data-stu-id="7d992-131">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="7d992-132">Při použití vazby protokolu SOAP, element vazby přenosu by také exportovat správné přenosu URI v metadatech.</span><span class="sxs-lookup"><span data-stu-id="7d992-132">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span> <span data-ttu-id="7d992-133">Následující příklad kódu jsou převzaty z [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="7d992-133">The following example code is taken from the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="7d992-134">WSDL Export</span><span class="sxs-lookup"><span data-stu-id="7d992-134">WSDL Export</span></span>  
 <span data-ttu-id="7d992-135">Chcete-li exportovat informace o přidělování `UdpTransportBindingElement` implementuje <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7d992-135">To export addressing information, the `UdpTransportBindingElement` implements the <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="7d992-136"><xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> Metoda přidá správné informace o přidělování do portu WSDL.</span><span class="sxs-lookup"><span data-stu-id="7d992-136">The <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> method adds the correct addressing information to the WSDL port.</span></span>  
  
```  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="7d992-137">`UdpTransportBindingElement` Implementace <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> metoda zároveň exportuje přenos identifikátor URI, pokud koncový bod používá vazbu protokolu SOAP:</span><span class="sxs-lookup"><span data-stu-id="7d992-137">The `UdpTransportBindingElement` implementation of the <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> method also exports a transport URI when the endpoint uses a SOAP binding:</span></span>  
  
```  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="7d992-138">Import schématu WSDL</span><span class="sxs-lookup"><span data-stu-id="7d992-138">WSDL Import</span></span>  
 <span data-ttu-id="7d992-139">Rozšíření systému importu WSDL pro zpracování importu adres, přidejte do konfiguračního souboru pro Svcutil.exe jak je znázorněno v souboru Svcutil.exe.config následující konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="7d992-139">To extend the WSDL import system to handle importing the addresses, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
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
  
 <span data-ttu-id="7d992-140">Když spustíte Svcutil.exe, existují dvě možnosti pro získání Svcutil.exe načíst import rozšíření schématu WSDL:</span><span class="sxs-lookup"><span data-stu-id="7d992-140">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1.  <span data-ttu-id="7d992-141">Bod Svcutil.exe do konfiguračního souboru pomocí /SvcutilConfig:\<souboru >.</span><span class="sxs-lookup"><span data-stu-id="7d992-141">Point Svcutil.exe to the configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2.  <span data-ttu-id="7d992-142">Přidejte konfigurační oddíl k Svcutil.exe.config ve stejném adresáři jako Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="7d992-142">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="7d992-143">`UdpBindingElementImporter` Zadejte implementuje <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7d992-143">The `UdpBindingElementImporter` type implements the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="7d992-144">`ImportEndpoint` Metoda importuje adresu z portu WSDL:</span><span class="sxs-lookup"><span data-stu-id="7d992-144">The `ImportEndpoint` method imports the address from the WSDL port:</span></span>  
  
```  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="7d992-145">Přidání zásady podpory</span><span class="sxs-lookup"><span data-stu-id="7d992-145">Adding Policy Support</span></span>  
 <span data-ttu-id="7d992-146">Vlastní vazby element můžete exportovat zásady kontrolní výrazy ve vazbě WSDL pro koncový bod služby do express možnosti tohoto prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="7d992-146">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span> <span data-ttu-id="7d992-147">Následující příklad kódu jsou převzaty z [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="7d992-147">The following example code is taken from the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="7d992-148">Export zásad</span><span class="sxs-lookup"><span data-stu-id="7d992-148">Policy Export</span></span>  
 <span data-ttu-id="7d992-149">`UdpTransportBindingElement` Zadejte implementuje ''<xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> přidání podpory pro export zásad.</span><span class="sxs-lookup"><span data-stu-id="7d992-149">The `UdpTransportBindingElement` type implements``<xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> to add support for exporting policy.</span></span> <span data-ttu-id="7d992-150">V důsledku toho <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> zahrnuje `UdpTransportBindingElement` při generování zásad u všech vazby, která ji obsahuje.</span><span class="sxs-lookup"><span data-stu-id="7d992-150">As a result, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="7d992-151">V <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, přidejte kontrolní výrazy pro UDP a jiné assertion, pokud je kanál v režimu vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="7d992-151">In <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, add an assertion for UDP and another assertion if the channel is in multicast mode.</span></span> <span data-ttu-id="7d992-152">Toto je vzhledem k tomu, že má vliv na režimu vícesměrového vysílání jak komunikačního balíku je vytvořený a proto musí být koordinované mezi na obou stranách.</span><span class="sxs-lookup"><span data-stu-id="7d992-152">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
```  
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
  
 <span data-ttu-id="7d992-153">Protože elementů přenosové vlastní vazby je zodpovědná za zpracování adresy, <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementace na `UdpTransportBindingElement` musí také zpracovat export příslušné WS-Addressing kontrolních výrazů zásad označující verzi adresování WS používá.</span><span class="sxs-lookup"><span data-stu-id="7d992-153">Because custom transport binding elements are responsible for handling addressing, the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="7d992-154">Import zásady</span><span class="sxs-lookup"><span data-stu-id="7d992-154">Policy Import</span></span>  
 <span data-ttu-id="7d992-155">Rozšíření systému import zásady, přidejte následující konfigurace do konfiguračního souboru pro Svcutil.exe jak je znázorněno v souboru Svcutil.exe.config:</span><span class="sxs-lookup"><span data-stu-id="7d992-155">To extend the policy import system, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
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
  
 <span data-ttu-id="7d992-156">Pak můžeme implementovat <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> z našich registrované třídy (`UdpBindingElementImporter`).</span><span class="sxs-lookup"><span data-stu-id="7d992-156">Then we implement <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="7d992-157">V <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, zkontrolujte kontrolní výrazy v příslušné oboru názvů a zpracovat těm, které jsou pro generování přenosu a kontrola, zda je vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="7d992-157">In <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, examine the assertions in the appropriate namespace and process the ones for generating the transport and checking if it is multicast.</span></span> <span data-ttu-id="7d992-158">Kontrolní výrazy, které zpracovává program pro import můžete také odeberte ze seznamu vazby kontrolní výrazy.</span><span class="sxs-lookup"><span data-stu-id="7d992-158">In addition, remove the assertions that the importer handles from the list of binding assertions.</span></span> <span data-ttu-id="7d992-159">Znovu když spustíte Svcutil.exe, existují dvě možnosti pro integraci:</span><span class="sxs-lookup"><span data-stu-id="7d992-159">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1.  <span data-ttu-id="7d992-160">Bod Svcutil.exe pro naše konfiguračního souboru pomocí /SvcutilConfig:\<souboru >.</span><span class="sxs-lookup"><span data-stu-id="7d992-160">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2.  <span data-ttu-id="7d992-161">Přidejte konfigurační oddíl k Svcutil.exe.config ve stejném adresáři jako Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="7d992-161">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="7d992-162">Přidání vlastních standardní vazby – Importér</span><span class="sxs-lookup"><span data-stu-id="7d992-162">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="7d992-163">Svcutil.exe a <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> typu, standardně rozpoznat a importovat vazby poskytované systémem.</span><span class="sxs-lookup"><span data-stu-id="7d992-163">Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> type, by default, recognize and import system-provided bindings.</span></span> <span data-ttu-id="7d992-164">Jinak získává importovat, protože vazba <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance.</span><span class="sxs-lookup"><span data-stu-id="7d992-164">Otherwise, the binding gets imported as a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="7d992-165">Chcete-li povolit Svcutil.exe a <xref:System.ServiceModel.Description.WsdlImporter> k importu `SampleProfileUdpBinding` `UdpBindingElementImporter` taky funguje jako – Importér vlastní standardní vazby.</span><span class="sxs-lookup"><span data-stu-id="7d992-165">To enable Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter> to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="7d992-166">Implementuje – Importér vlastní standardní vazby `ImportEndpoint` metodu <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> rozhraní prozkoumat <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance importovat z metadat, které chcete zobrazit, pokud ho může být vygenerovaná konkrétní standardní vazby.</span><span class="sxs-lookup"><span data-stu-id="7d992-166">A custom standard binding importer implements the `ImportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface to examine the <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance imported from metadata to see if it could have been generated by specific standard binding.</span></span>  
  
```  
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
  
 <span data-ttu-id="7d992-167">Obecně platí implementace – Importér vlastní standardní vazby zahrnuje kontrolu vlastnosti prvky importované vazby pro ověření, že pouze vlastnosti, které by mohly být nastaveny standardní vazbou změnily a všechny ostatní vlastnosti jsou jejich výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7d992-167">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="7d992-168">Základní strategii pro implementaci – Importér standardní vazba je vytvoření instance standardní vazby, rozšířit vlastnosti z elementů vazby standardní vazby instanci, která podporuje standardní vazby a porovnání vazby elementy ze standardní vazba s prvky importované vazby.</span><span class="sxs-lookup"><span data-stu-id="7d992-168">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>
