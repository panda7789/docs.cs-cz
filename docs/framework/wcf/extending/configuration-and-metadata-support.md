---
title: Konfigurace a podpora metadat
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: 4dfeeba6db220e03ad981b13e2bb093bedcd43c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486721"
---
# <a name="configuration-and-metadata-support"></a>Konfigurace a podpora metadat
Toto téma popisuje, jak povolit podporu konfigurace a metadat pro vazby a prvky vazeb.  
  
## <a name="overview-of-configuration-and-metadata"></a>Přehled konfigurace a metadat  
 Toto téma popisuje následující úlohy, které jsou volitelné položky 1, 2 a 4 v [rozvojových kanály](../../../../docs/framework/wcf/extending/developing-channels.md) seznamu úloh.  
  
-   Povolení podpory souboru konfigurace pro prvku vazby.  
  
-   Povolení podpory souboru konfigurace pro vazbu.  
  
-   Export kontrolních výrazů WSDL a zásady pro prvku vazby.  
  
-   Identifikace WSDL a zásady kontrolní výrazy insert a nakonfigurovat vazby nebo prvku vazby.  
  
 Informace o vytváření uživatelem definované vazby a prvky vazeb najdete v tématu [Creating User-Defined vazby](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md) a [vytvoření BindingElement](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md), v uvedeném pořadí.  
  
## <a name="adding-configuration-support"></a>Přidání podpory konfigurace  
 Povolit podporu souboru konfigurace pro kanál, je nutné implementovat dvě konfiguračních oddílů, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, což umožňuje podporu konfigurace pro elementů, vazby a <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, která umožňují podporu konfigurace pro vazby.  
  
 Snadný způsob, jak to udělat, je použití [ConfigurationCodeGenerator](../../../../docs/framework/wcf/samples/configurationcodegenerator.md) ukázkový nástroj pro generování kódu konfigurace pro vazby a prvky vazeb.  
  
### <a name="extending-bindingelementextensionelement"></a>Rozšíření BindingElementExtensionElement  
 Následující příklad kódu jsou převzaty z [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) ukázka. `UdpTransportElement` Je <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> která zveřejňuje `UdpTransportBindingElement` v konfiguraci systému. S několika základní přepsání ukázky definuje název konfiguračního oddílu, typ elementu vazby a postup vytvoření prvku vazby. Uživatelé můžou potom zaregistrovat části rozšíření v konfiguračním souboru následujícím způsobem.  
  
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
  
 Rozšíření můžete odkazovat z vlastních vazeb, používat UDP jako přenosu.  
  
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
  
### <a name="adding-configuration-for-a-binding"></a>Přidává se konfigurace vazby  
 V části `SampleProfileUdpBindingCollectionElement` je <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> která zveřejňuje `SampleProfileUdpBinding` v konfiguraci systému. Hromadné implementace je delegovaný jako `SampleProfileUdpBindingConfigurationElement`, která je odvozena z <xref:System.ServiceModel.Configuration.StandardBindingElement>. `SampleProfileUdpBindingConfigurationElement` Má vlastnosti, které odpovídají vlastnosti na `SampleProfileUdpBinding`a funkce pro mapování z `ConfigurationElement` vazby. Nakonec `OnApplyConfiguration` je metoda potlačena v `SampleProfileUdpBinding`, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 K registraci této obslužné rutiny konfigurace systému, přidejte do příslušných konfiguračního souboru v následující části.  
  
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
  
 Lze ji pak odkazovat z [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) konfigurační oddíl.  
  
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
  
## <a name="adding-metadata-support-for-a-binding-element"></a>Přidání podpory Metadata pro Element vazby  
 Kanál, který se integruje do systém metadat, musí podporovat, import a export zásad. To umožňuje nástroje, jako [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování klienti prvku vazby.  
  
### <a name="adding-wsdl-support"></a>Přidání podpory WSDL  
 Element vazby přenosu ve vazbě zodpovídá pro export a import informací o adresách v metadatech. Při použití vazby protokolu SOAP, element vazby přenosu by také exportovat správné přenosu URI v metadatech. Následující příklad kódu jsou převzaty z [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) ukázka.  
  
#### <a name="wsdl-export"></a>WSDL Export  
 Chcete-li exportovat informace o přidělování `UdpTransportBindingElement` implementuje <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> rozhraní. <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> Metoda přidá správné informace o přidělování do portu WSDL.  
  
```  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 `UdpTransportBindingElement` Implementace <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> metoda zároveň exportuje přenos identifikátor URI, pokud koncový bod používá vazbu protokolu SOAP:  
  
```  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>Import schématu WSDL  
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
  
 Když spustíte Svcutil.exe, existují dvě možnosti pro získání Svcutil.exe načíst import rozšíření schématu WSDL:  
  
1.  Bod Svcutil.exe do konfiguračního souboru pomocí /SvcutilConfig:\<souboru >.  
  
2.  Přidejte konfigurační oddíl k Svcutil.exe.config ve stejném adresáři jako Svcutil.exe.  
  
 `UdpBindingElementImporter` Zadejte implementuje <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> rozhraní. `ImportEndpoint` Metoda importuje adresu z portu WSDL:  
  
```  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Přidání zásady podpory  
 Vlastní vazby element můžete exportovat zásady kontrolní výrazy ve vazbě WSDL pro koncový bod služby do express možnosti tohoto prvku vazby. Následující příklad kódu jsou převzaty z [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) ukázka.  
  
#### <a name="policy-export"></a>Export zásad  
 `UdpTransportBindingElement` Zadejte implementuje ''<xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> přidání podpory pro export zásad. V důsledku toho <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> zahrnuje `UdpTransportBindingElement` při generování zásad u všech vazby, která ji obsahuje.  
  
 V <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, přidejte kontrolní výrazy pro UDP a jiné assertion, pokud je kanál v režimu vícesměrového vysílání. Toto je vzhledem k tomu, že má vliv na režimu vícesměrového vysílání jak komunikačního balíku je vytvořený a proto musí být koordinované mezi na obou stranách.  
  
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
  
 Protože elementů přenosové vlastní vazby je zodpovědná za zpracování adresy, <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementace na `UdpTransportBindingElement` musí také zpracovat export příslušné WS-Addressing kontrolních výrazů zásad označující verzi adresování WS používá.  
  
```  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>Import zásady  
 Rozšíření systému import zásady, přidejte následující konfigurace do konfiguračního souboru pro Svcutil.exe jak je znázorněno v souboru Svcutil.exe.config:  
  
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
  
 Pak můžeme implementovat <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> z našich registrované třídy (`UdpBindingElementImporter`). V <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, zkontrolujte kontrolní výrazy v příslušné oboru názvů a zpracovat těm, které jsou pro generování přenosu a kontrola, zda je vícesměrového vysílání. Kontrolní výrazy, které zpracovává program pro import můžete také odeberte ze seznamu vazby kontrolní výrazy. Znovu když spustíte Svcutil.exe, existují dvě možnosti pro integraci:  
  
1.  Bod Svcutil.exe pro naše konfiguračního souboru pomocí /SvcutilConfig:\<souboru >.  
  
2.  Přidejte konfigurační oddíl k Svcutil.exe.config ve stejném adresáři jako Svcutil.exe.  
  
### <a name="adding-a-custom-standard-binding-importer"></a>Přidání vlastních standardní vazby – Importér  
 Svcutil.exe a <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> typu, standardně rozpoznat a importovat vazby poskytované systémem. Jinak získává importovat, protože vazba <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance. Chcete-li povolit Svcutil.exe a <xref:System.ServiceModel.Description.WsdlImporter> k importu `SampleProfileUdpBinding` `UdpBindingElementImporter` taky funguje jako – Importér vlastní standardní vazby.  
  
 Implementuje – Importér vlastní standardní vazby `ImportEndpoint` metodu <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> rozhraní prozkoumat <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance importovat z metadat, které chcete zobrazit, pokud ho může být vygenerovaná konkrétní standardní vazby.  
  
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
  
 Obecně platí implementace – Importér vlastní standardní vazby zahrnuje kontrolu vlastnosti prvky importované vazby pro ověření, že pouze vlastnosti, které by mohly být nastaveny standardní vazbou změnily a všechny ostatní vlastnosti jsou jejich výchozí hodnoty. Základní strategii pro implementaci – Importér standardní vazba je vytvoření instance standardní vazby, rozšířit vlastnosti z elementů vazby standardní vazby instanci, která podporuje standardní vazby a porovnání vazby elementy ze standardní vazba s prvky importované vazby.
