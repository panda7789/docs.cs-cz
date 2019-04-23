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
# <a name="configuration-and-metadata-support"></a>Konfigurace a podpora metadat
Toto téma popisuje, jak povolit podporu konfigurace a metadat pro vazby a prvky vazeb.  
  
## <a name="overview-of-configuration-and-metadata"></a>Přehled konfigurace a metadat  
 Toto téma popisuje následující úkoly, které jsou volitelné položky 1, 2 a 4 v [vývoj kanálů](../../../../docs/framework/wcf/extending/developing-channels.md) seznamu úkolů.  
  
-   Povolení podpory konfigurační soubor pro element vazby.  
  
-   Povolení podpory konfigurační soubor pro vazbu.  
  
-   Export kontrolních výrazů WSDL a zásady pro element vazby.  
  
-   Identifikace WSDL a zásady kontrolní výrazy pro vložení a nakonfigurujte vazby nebo element vazby.  
  
 Informace o vytváření uživatelem definovaných vazeb a prvky vazeb naleznete v tématu [Creating User-Defined vazby](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md) a [vytvoření BindingElement](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md)v uvedeném pořadí.  
  
## <a name="adding-configuration-support"></a>Přidání podpory konfigurace  
 Povolení podpory konfigurační soubor pro kanál, je nutné implementovat dva oddíly konfigurace, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, která podporuje konfiguraci elementů, vazby a <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, umožňující podporu konfigurace pro vazby.  
  
 Snadný způsob, jak to provést, je použít [ConfigurationCodeGenerator](../../../../docs/framework/wcf/samples/configurationcodegenerator.md) ukázkový nástroj pro generování kódu konfigurace pro vazby a prvky vazeb.  
  
### <a name="extending-bindingelementextensionelement"></a>Rozšíření BindingElementExtensionElement  
 Následující vzorový kód je převzat z [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) vzorku. `UdpTransportElement` Je <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> , která zveřejní `UdpTransportBindingElement` k systému konfigurace. Několik základních lokálně ukázka definuje název oddílu konfigurace, typ elementu vazby a tom, jak vytvořit element vazby. Uživatelé můžou potom registrovat oddílu rozšíření v konfiguračním souboru následujícím způsobem.  
  
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
  
 Rozšíření můžete odkazovat z vlastní vazby pro použití jako přenos UDP.  
  
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
  
### <a name="adding-configuration-for-a-binding"></a>Přidává se konfigurace pro vazbu  
 V části `SampleProfileUdpBindingCollectionElement` je <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> , která zveřejní `SampleProfileUdpBinding` k systému konfigurace. Hromadné implementace se deleguje na `SampleProfileUdpBindingConfigurationElement`, která je odvozena z <xref:System.ServiceModel.Configuration.StandardBindingElement>. `SampleProfileUdpBindingConfigurationElement` Má vlastnosti, které odpovídají vlastnostem v `SampleProfileUdpBinding`a funkce mapování `ConfigurationElement` vazby. Nakonec `OnApplyConfiguration` v je přepsána metoda `SampleProfileUdpBinding`, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 K registraci této obslužné rutiny konfigurace systému, přidejte následující část do souboru položky konfigurace.  
  
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
  
 Poté jej lze odkazovat z [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) konfigurační oddíl.  
  
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
  
## <a name="adding-metadata-support-for-a-binding-element"></a>Přidání podpory metadat pro Element vazby  
 K integraci kanál do metadat systému, musí podporovat, import a export zásad. Díky tomu nástroje, jako [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování klientů elementu vazby.  
  
### <a name="adding-wsdl-support"></a>Přidání podpory WSDL  
 Element vazby přenosu ve vazbě je zodpovědná za export a import informací o adresách v metadatech. Při použití vazby protokolu SOAP, element vazby přenosu by měl také exportovat správné přepravy identifikátoru URI v metadatech. Následující vzorový kód je převzat z [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) vzorku.  
  
#### <a name="wsdl-export"></a>WSDL Export  
 Chcete-li exportovat informace o adresách, `UdpTransportBindingElement` implementuje <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> rozhraní. <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> Metoda přidá správné informace o adresování na WSDL port.  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 `UdpTransportBindingElement` Provádění <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> metoda zároveň exportuje přepravy identifikátoru URI při koncový bod používá vazba SOAP:  
  
```csharp  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>WSDL Import  
 Rozšíření systému importu WSDL pro zpracování importu adres, přidejte do konfiguračního souboru pro Svcutil.exe jak je znázorněno v souboru Svcutil.exe.config následující konfiguraci:  
  
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
  
 Při spuštění Svcutil.exe, existují dvě možnosti pro získání Svcutil.exe k načítání rozšíření importu WSDL:  
  
1. Bod Svcutil.exe do konfiguračního souboru pomocí /SvcutilConfig:\<soubor >.  
  
2. Přidáte konfigurační oddíl pro Svcutil.exe.config ve stejném adresáři jako Svcutil.exe.  
  
 `UdpBindingElementImporter` Typ implementuje <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> rozhraní. `ImportEndpoint` Metoda importuje adresu z portu WSDL:  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Přidání podpory pro zásady  
 Vlastní prvek vazby můžete export kontrolních výrazů zásad Vazba WSDL pro koncový bod služby vyjádřit možnosti daného prvku vazby. Následující vzorový kód je převzat z [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) vzorku.  
  
#### <a name="policy-export"></a>Export zásad  
 `UdpTransportBindingElement` Typ implementuje <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> přidává funkce pro export zásad. V důsledku toho <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> zahrnuje `UdpTransportBindingElement` při generování zásad pro všechny vazby, který ji obsahuje.  
  
 V <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, přidat kontrolní výraz pro UDP a další kontrolní výraz, pokud kanál není v režimu vícesměrového vysílání. Jak komunikačního balíku je vytvořen a proto musí být koordinovaní mezi obě strany jde vzhledem k tomu, že má vliv na režimu vícesměrového vysílání.  
  
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
  
 Protože jsou zodpovědného za obsluhu adresování elementů přenosové vlastní vazby <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementace v prostředí `UdpTransportBindingElement` musí také zpracovat export odpovídající WS-Addressing kontrolní výrazy zásad označující verzi elementu WS-Addressing používá.  
  
```csharp  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>Import zásady  
 Rozšíření systému importovat zásady, přidejte následující konfiguraci do konfiguračního souboru pro Svcutil.exe jak je znázorněno v souboru Svcutil.exe.config:  
  
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
  
 Pak můžeme implementovat <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> z našich registrované třídy (`UdpBindingElementImporter`). V <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, zkontrolujte kontrolní výrazy ve odpovídající obor názvů a zpracovat pro generování přenos a kontrola, zda je vícesměrového vysílání. Kontrolní výrazy, které zpracovává tabulkách navíc odeberte ze seznamu vazby kontrolní výrazy. Znovu když spustíte Svcutil.exe, existují dvě možnosti pro integraci:  
  
1. Bod Svcutil.exe k naší konfiguračního souboru pomocí /SvcutilConfig:\<soubor >.  
  
2. Přidáte konfigurační oddíl pro Svcutil.exe.config ve stejném adresáři jako Svcutil.exe.  
  
### <a name="adding-a-custom-standard-binding-importer"></a>Přidání vlastní standardní vazby programu pro import  
 Svcutil.exe a <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> typ, ve výchozím nastavení, rozpoznat a import vazeb poskytovaných systémem. V opačném případě získá importovat, protože vazba <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance. Povolit Svcutil.exe a <xref:System.ServiceModel.Description.WsdlImporter> import `SampleProfileUdpBinding` `UdpBindingElementImporter` taky pracuje jako import standardní vlastní vazby.  
  
 Implementuje programu pro import standardní vlastní vazby `ImportEndpoint` metodu na <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> rozhraní k prozkoumání <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance naimportované z metadat zobrazíte, pokud to může být vygenerováno konkrétní standardní vazbu.  
  
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
  
 Obecně platí implementace programu pro import vlastních vazeb standard zahrnuje ověření vlastností elementů importované vazby k ověření, že jste změnili pouze vlastnosti, které může nastavit standardní vazbou a všechny ostatní vlastnosti se jejich výchozích hodnotách. Základní strategií pro implementaci standardní vazbu Importér je vytvoření instance standardní vazbu, rozšíří vlastnosti z elementů vazby instanci standardní vazbu, která podporuje standardní vazbu, a porovnat vazby elementy ze standardní vazba s prvky importované vazby.
