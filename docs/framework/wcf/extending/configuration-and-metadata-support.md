---
title: Konfigurace a podpora metadat
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: 0ec8c3286037e7adbe6f5efb73e846a30b9d48d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185669"
---
# <a name="configuration-and-metadata-support"></a><span data-ttu-id="023bd-102">Konfigurace a podpora metadat</span><span class="sxs-lookup"><span data-stu-id="023bd-102">Configuration and Metadata Support</span></span>
<span data-ttu-id="023bd-103">Toto téma popisuje, jak povolit podporu konfigurace a metadat pro vazby a elementy vazby.</span><span class="sxs-lookup"><span data-stu-id="023bd-103">This topic describes how to enable configuration and metadata support for bindings and binding elements.</span></span>  
  
## <a name="overview-of-configuration-and-metadata"></a><span data-ttu-id="023bd-104">Přehled konfigurace a metadat</span><span class="sxs-lookup"><span data-stu-id="023bd-104">Overview of Configuration and Metadata</span></span>  
 <span data-ttu-id="023bd-105">Toto téma popisuje následující úkoly, které jsou volitelné položky 1, 2 a 4 v seznamu úkolů [vývoj kanálů.](developing-channels.md)</span><span class="sxs-lookup"><span data-stu-id="023bd-105">This topic discusses the following tasks, which are optional items 1, 2, and 4 in the [Developing Channels](developing-channels.md) task list.</span></span>  
  
- <span data-ttu-id="023bd-106">Povolení podpory konfiguračního souboru pro element vazby.</span><span class="sxs-lookup"><span data-stu-id="023bd-106">Enabling configuration file support for a binding element.</span></span>  
  
- <span data-ttu-id="023bd-107">Povolení podpory konfiguračního souboru pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="023bd-107">Enabling configuration file support for a binding.</span></span>  
  
- <span data-ttu-id="023bd-108">Export WSDL a kontrolní výrazy zásad pro element vazby.</span><span class="sxs-lookup"><span data-stu-id="023bd-108">Exporting WSDL and policy assertions for a binding element.</span></span>  
  
- <span data-ttu-id="023bd-109">Identifikace WSDL a kontrolní výrazy zásad pro vložení a konfiguraci elementu vazby nebo vazby.</span><span class="sxs-lookup"><span data-stu-id="023bd-109">Identifying WSDL and policy assertions to insert and configure your binding or binding element.</span></span>  
  
 <span data-ttu-id="023bd-110">Informace o vytváření uživatelem definované vazby a prvky vazby, naleznete [v tématu vytváření uživatelem definované vazby](creating-user-defined-bindings.md) a [vytvoření BindingElement](creating-a-bindingelement.md), v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="023bd-110">For information about creating user-defined bindings and binding elements, see [Creating User-Defined Bindings](creating-user-defined-bindings.md) and [Creating a BindingElement](creating-a-bindingelement.md), respectively.</span></span>  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="023bd-111">Přidání podpory konfigurace</span><span class="sxs-lookup"><span data-stu-id="023bd-111">Adding Configuration Support</span></span>  
 <span data-ttu-id="023bd-112">Chcete-li povolit podporu konfiguračního souboru pro kanál, je nutné implementovat dvě části konfigurace , <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>které umožňují podporu konfigurace prvků vazby, a <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, které umožňují podporu konfigurace vazeb.</span><span class="sxs-lookup"><span data-stu-id="023bd-112">To enable configuration file support for a channel, you must implement two configuration sections, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, which enables configuration support for binding elements, and the <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> and <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, which enable configuration support for bindings.</span></span>  
  
 <span data-ttu-id="023bd-113">Jednodušší způsob, jak to provést, je použít nástroj [ukázkový nástroj ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) ke generování konfiguračního kódu pro vaše vazby a elementy vazby.</span><span class="sxs-lookup"><span data-stu-id="023bd-113">An easier way to do this is to use the [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) sample tool to generate configuration code for your bindings and binding elements.</span></span>  
  
### <a name="extending-bindingelementextensionelement"></a><span data-ttu-id="023bd-114">Rozšíření elementu BindingElementExtensionElement</span><span class="sxs-lookup"><span data-stu-id="023bd-114">Extending BindingElementExtensionElement</span></span>  
 <span data-ttu-id="023bd-115">Následující ukázkový kód je převzat z [transportu: udp](../samples/transport-udp.md) ukázky.</span><span class="sxs-lookup"><span data-stu-id="023bd-115">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span> <span data-ttu-id="023bd-116">Je, `UdpTransportElement` který zpřístupňuje `UdpTransportBindingElement` konfiguračnísystém. <xref:System.ServiceModel.Configuration.BindingElementExtensionElement></span><span class="sxs-lookup"><span data-stu-id="023bd-116">The `UdpTransportElement` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="023bd-117">S několika základními přepsáními ukázka definuje název konfiguračního oddílu, typ elementu vazby a způsob vytvoření elementu vazby.</span><span class="sxs-lookup"><span data-stu-id="023bd-117">With a few basic overrides, the sample defines the configuration section name, the type of the binding element and how to create the binding element.</span></span> <span data-ttu-id="023bd-118">Uživatelé pak mohou zaregistrovat oddíl rozšíření v konfiguračním souboru následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="023bd-118">Users can then register the extension section in a configuration file as follows.</span></span>  
  
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
  
 <span data-ttu-id="023bd-119">Rozšíření lze odkazovat z vlastní vazby použít UDP jako přenos.</span><span class="sxs-lookup"><span data-stu-id="023bd-119">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
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
  
### <a name="adding-configuration-for-a-binding"></a><span data-ttu-id="023bd-120">Přidání konfigurace pro vazbu</span><span class="sxs-lookup"><span data-stu-id="023bd-120">Adding Configuration for a Binding</span></span>  
 <span data-ttu-id="023bd-121">Sekce `SampleProfileUdpBindingCollectionElement` <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> je, která `SampleProfileUdpBinding` zpřístupňuje konfiguračnísystém.</span><span class="sxs-lookup"><span data-stu-id="023bd-121">The section `SampleProfileUdpBindingCollectionElement` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="023bd-122">Převážná část implementace je delegována `SampleProfileUdpBindingConfigurationElement`na <xref:System.ServiceModel.Configuration.StandardBindingElement>, který je odvozen z .</span><span class="sxs-lookup"><span data-stu-id="023bd-122">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="023bd-123">Má `SampleProfileUdpBindingConfigurationElement` vlastnosti, které odpovídají `SampleProfileUdpBinding`vlastnosti na , `ConfigurationElement` a funkce mapovat z vazby.</span><span class="sxs-lookup"><span data-stu-id="023bd-123">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="023bd-124">Nakonec je `OnApplyConfiguration` metoda přepsána `SampleProfileUdpBinding`v , jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="023bd-124">Finally, the `OnApplyConfiguration` method is overridden in the `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
```csharp
protected override void OnApplyConfiguration(string configurationName)  
{  
            if (binding == null)  
                throw new ArgumentNullException("binding");  
  
            if (binding.GetType() != typeof(SampleProfileUdpBinding))  
            {  
                var expectedType = typeof(SampleProfileUdpBinding).AssemblyQualifiedName;
                var typePassedIn = binding.GetType().AssemblyQualifiedName;
                throw new ArgumentException($"Invalid type for binding. Expected type: {expectedType}. Type passed in: {typePassedIn}.");  
            }  
            SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;  
  
            udpBinding.OrderedSession = this.OrderedSession;  
            udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;  
            udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;  
            if (this.ClientBaseAddress != null)  
                   udpBinding.ClientBaseAddress = ClientBaseAddress;  
}  
```  
  
 <span data-ttu-id="023bd-125">Chcete-li zaregistrovat tuto obslužnou rutinu v konfiguračním systému, přidejte do příslušného konfiguračního souboru následující část.</span><span class="sxs-lookup"><span data-stu-id="023bd-125">To register this handler with the configuration system, add the following section to the relevant configuration file.</span></span>  
  
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
  
 <span data-ttu-id="023bd-126">Potom může být odkazováno z [ \<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) konfigurační části.</span><span class="sxs-lookup"><span data-stu-id="023bd-126">It can then be referenced from the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) configuration section.</span></span>  
  
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
  
## <a name="adding-metadata-support-for-a-binding-element"></a><span data-ttu-id="023bd-127">Přidání podpory metadat pro element vazby</span><span class="sxs-lookup"><span data-stu-id="023bd-127">Adding Metadata Support for a Binding Element</span></span>  
 <span data-ttu-id="023bd-128">Chcete-li integrovat kanál do systému metadat, musí podporovat import i export zásad.</span><span class="sxs-lookup"><span data-stu-id="023bd-128">To integrate a channel into the metadata system, it must support both the import and export of policy.</span></span> <span data-ttu-id="023bd-129">To umožňuje nástroje, jako je [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) generovat klienty elementu vazby.</span><span class="sxs-lookup"><span data-stu-id="023bd-129">This allows tools such as [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate clients of the binding element.</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="023bd-130">Přidání podpory WSDL</span><span class="sxs-lookup"><span data-stu-id="023bd-130">Adding WSDL Support</span></span>  
 <span data-ttu-id="023bd-131">Prvek vazby přenosu ve vazbě je zodpovědný za export a import adresování informací v metadatech.</span><span class="sxs-lookup"><span data-stu-id="023bd-131">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="023bd-132">Při použití soap vazby, prvek vazby přenosu by měl také exportovat správný identifikátor URI přenosu v metadatech.</span><span class="sxs-lookup"><span data-stu-id="023bd-132">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span> <span data-ttu-id="023bd-133">Následující ukázkový kód je převzat z [transportu: udp](../samples/transport-udp.md) ukázky.</span><span class="sxs-lookup"><span data-stu-id="023bd-133">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="023bd-134">WSDL Export</span><span class="sxs-lookup"><span data-stu-id="023bd-134">WSDL Export</span></span>  
 <span data-ttu-id="023bd-135">Chcete-li exportovat `UdpTransportBindingElement` adresování <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> informace, implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="023bd-135">To export addressing information, the `UdpTransportBindingElement` implements the <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="023bd-136">Metoda <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> přidá správné informace o adresování wsdl port.</span><span class="sxs-lookup"><span data-stu-id="023bd-136">The <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="023bd-137">Implementace `UdpTransportBindingElement` <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> metody také exportuje identifikátor URI přenosu, pokud koncový bod používá vazbu SOAP:</span><span class="sxs-lookup"><span data-stu-id="023bd-137">The `UdpTransportBindingElement` implementation of the <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> method also exports a transport URI when the endpoint uses a SOAP binding:</span></span>  
  
```csharp  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="023bd-138">WSDL Import</span><span class="sxs-lookup"><span data-stu-id="023bd-138">WSDL Import</span></span>  
 <span data-ttu-id="023bd-139">Chcete-li rozšířit systém importu WSDL na zpracování importu adres, přidejte do konfiguračního souboru svcutil.exe následující konfiguraci, jak je znázorněno v souboru Svcutil.exe.config:</span><span class="sxs-lookup"><span data-stu-id="023bd-139">To extend the WSDL import system to handle importing the addresses, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
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
  
 <span data-ttu-id="023bd-140">Při spuštění svcutil.exe, existují dvě možnosti pro získání Svcutil.exe načíst rozšíření importu WSDL:</span><span class="sxs-lookup"><span data-stu-id="023bd-140">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="023bd-141">Bod Svcutil.exe do konfiguračního souboru pomocí\</SvcutilConfig: soubor>.</span><span class="sxs-lookup"><span data-stu-id="023bd-141">Point Svcutil.exe to the configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="023bd-142">Přidejte oddíl konfigurace do svcutil.exe.config ve stejném adresáři jako Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="023bd-142">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="023bd-143">Typ `UdpBindingElementImporter` implementuje <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="023bd-143">The `UdpBindingElementImporter` type implements the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="023bd-144">Metoda `ImportEndpoint` importuje adresu z portu WSDL:</span><span class="sxs-lookup"><span data-stu-id="023bd-144">The `ImportEndpoint` method imports the address from the WSDL port:</span></span>  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="023bd-145">Přidání podpory zásad</span><span class="sxs-lookup"><span data-stu-id="023bd-145">Adding Policy Support</span></span>  
 <span data-ttu-id="023bd-146">Vlastní element vazby můžete exportovat kontrolní výrazy zásad ve vazbě WSDL pro koncový bod služby vyjádřit možnosti tohoto prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="023bd-146">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span> <span data-ttu-id="023bd-147">Následující ukázkový kód je převzat z [transportu: udp](../samples/transport-udp.md) ukázky.</span><span class="sxs-lookup"><span data-stu-id="023bd-147">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="023bd-148">Export zásad</span><span class="sxs-lookup"><span data-stu-id="023bd-148">Policy Export</span></span>  
 <span data-ttu-id="023bd-149">Typ `UdpTransportBindingElement` implementuje <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> přidat podporu pro zásady exportu.</span><span class="sxs-lookup"><span data-stu-id="023bd-149">The `UdpTransportBindingElement` type implements <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> to add support for exporting policy.</span></span> <span data-ttu-id="023bd-150">V důsledku <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> toho `UdpTransportBindingElement` zahrnuje v generování zásad pro všechny vazby, která ji zahrnuje.</span><span class="sxs-lookup"><span data-stu-id="023bd-150">As a result, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="023bd-151">V <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>aplikaci přidejte kontrolní výraz pro UDP a další kontrolní výraz, pokud je kanál v režimu vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="023bd-151">In <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, add an assertion for UDP and another assertion if the channel is in multicast mode.</span></span> <span data-ttu-id="023bd-152">Důvodem je, že režim vícesměrového vysílání ovlivňuje způsob vytvoření zásobníku komunikace, a proto musí být koordinován mezi oběma stranami.</span><span class="sxs-lookup"><span data-stu-id="023bd-152">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
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
  
 <span data-ttu-id="023bd-153">Vzhledem k tomu, že vlastní <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> prvky `UdpTransportBindingElement` vazby přenosu jsou zodpovědné za zpracování adresování, implementace na musí také zpracovat export příslušných výrazů zásad WS-Addressing k označení verze ws adresování se používá.</span><span class="sxs-lookup"><span data-stu-id="023bd-153">Because custom transport binding elements are responsible for handling addressing, the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="023bd-154">Import zásad</span><span class="sxs-lookup"><span data-stu-id="023bd-154">Policy Import</span></span>  
 <span data-ttu-id="023bd-155">Chcete-li rozšířit systém importu zásad, přidejte do konfiguračního souboru pro soubor Svcutil.exe následující konfiguraci, jak je znázorněno v souboru Svcutil.exe.config:</span><span class="sxs-lookup"><span data-stu-id="023bd-155">To extend the policy import system, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
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
  
 <span data-ttu-id="023bd-156">Pak implementujeme <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> z`UdpBindingElementImporter`naší registrované třídy ( ).</span><span class="sxs-lookup"><span data-stu-id="023bd-156">Then we implement <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="023bd-157">V <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, zkontrolujte kontrolní výrazy v příslušném oboru názvů a zpracujte ty, které generují přenos a kontrolují, zda je vícesměrové vysílání.</span><span class="sxs-lookup"><span data-stu-id="023bd-157">In <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, examine the assertions in the appropriate namespace and process the ones for generating the transport and checking if it is multicast.</span></span> <span data-ttu-id="023bd-158">Kromě toho odeberte tvrzení, že dovozce zpracovává ze seznamu tvrzení vazby.</span><span class="sxs-lookup"><span data-stu-id="023bd-158">In addition, remove the assertions that the importer handles from the list of binding assertions.</span></span> <span data-ttu-id="023bd-159">Opět platí, že při spuštění Svcutil.exe existují dvě možnosti integrace:</span><span class="sxs-lookup"><span data-stu-id="023bd-159">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="023bd-160">Bod Svcutil.exe do našeho konfiguračního souboru pomocí /SvcutilConfig:\<soubor>.</span><span class="sxs-lookup"><span data-stu-id="023bd-160">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="023bd-161">Přidejte oddíl konfigurace do svcutil.exe.config ve stejném adresáři jako Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="023bd-161">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="023bd-162">Přidání vlastního standardního importu vazeb</span><span class="sxs-lookup"><span data-stu-id="023bd-162">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="023bd-163">Svcutil.exe a <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> typ, ve výchozím nastavení rozpoznat a importovat systémem poskytované vazby.</span><span class="sxs-lookup"><span data-stu-id="023bd-163">Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> type, by default, recognize and import system-provided bindings.</span></span> <span data-ttu-id="023bd-164">V opačném případě vazba <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> získá importován jako instance.</span><span class="sxs-lookup"><span data-stu-id="023bd-164">Otherwise, the binding gets imported as a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="023bd-165">Chcete-li povolit Svcutil.exe `SampleProfileUdpBinding` `UdpBindingElementImporter` a <xref:System.ServiceModel.Description.WsdlImporter> importovat také působí jako vlastní standardní vázací dovozce.</span><span class="sxs-lookup"><span data-stu-id="023bd-165">To enable Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter> to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="023bd-166">Vlastní standardní importér `ImportEndpoint` vazby <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> implementuje <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> metodu na rozhraní prozkoumat instanci importované z metadat a zjistit, zda mohla být generována konkrétní standardní vazby.</span><span class="sxs-lookup"><span data-stu-id="023bd-166">A custom standard binding importer implements the `ImportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface to examine the <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance imported from metadata to see if it could have been generated by specific standard binding.</span></span>  
  
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
  
 <span data-ttu-id="023bd-167">Obecně platí, že implementace vlastní standardní vazby import zahrnuje kontrolu vlastností importované elementy vazby k ověření, že pouze vlastnosti, které mohly být nastaveny standardní vazby byly změněny a všechny ostatní vlastnosti jsou jejich výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="023bd-167">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="023bd-168">Základní strategií pro implementaci standardního importu vazby je vytvoření instance standardní vazby, šíření vlastností z elementů vazby na standardní instanci vazby, kterou podporuje standardní vazba, a porovnání vazby prvky ze standardní vazby s importovanými prvky vazby.</span><span class="sxs-lookup"><span data-stu-id="023bd-168">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>
