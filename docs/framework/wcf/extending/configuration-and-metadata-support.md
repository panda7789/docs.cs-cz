---
title: Konfigurace a podpora metadat
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: fb4e1cc51b827f083e580362f57df27ced770179
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345286"
---
# <a name="configuration-and-metadata-support"></a>Konfigurace a podpora metadat
Toto téma popisuje, jak povolit podporu konfigurace a metadat pro vazby a elementy vazby.  
  
## <a name="overview-of-configuration-and-metadata"></a>Přehled konfigurace a metadat  
 Toto téma popisuje následující úkoly, které jsou volitelné položky 1, 2 a 4 v seznamu úkolů [vývoj kanálů.](developing-channels.md)  
  
- Povolení podpory konfiguračního souboru pro element vazby.  
  
- Povolení podpory konfiguračního souboru pro vazbu.  
  
- Export WSDL a kontrolní výrazy zásad pro element vazby.  
  
- Identifikace WSDL a kontrolní výrazy zásad pro vložení a konfiguraci elementu vazby nebo vazby.  
  
 Informace o vytváření uživatelem definované vazby a prvky vazby, naleznete [v tématu vytváření uživatelem definované vazby](creating-user-defined-bindings.md) a [vytvoření BindingElement](creating-a-bindingelement.md), v uvedeném pořadí.  
  
## <a name="adding-configuration-support"></a>Přidání podpory konfigurace  
 Chcete-li povolit podporu konfiguračního souboru pro kanál, je nutné implementovat dvě části konfigurace , <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>které umožňují podporu konfigurace prvků vazby, a <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, které umožňují podporu konfigurace vazeb.  
  
 Jednodušší způsob, jak to provést, je použít nástroj [ukázkový nástroj ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) ke generování konfiguračního kódu pro vaše vazby a elementy vazby.  
  
### <a name="extending-bindingelementextensionelement"></a>Rozšíření elementu BindingElementExtensionElement  
 Následující ukázkový kód je převzat z [transportu: udp](../samples/transport-udp.md) ukázky. Je, `UdpTransportElement` který zpřístupňuje `UdpTransportBindingElement` konfiguračnísystém. <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> S několika základními přepsáními ukázka definuje název konfiguračního oddílu, typ elementu vazby a způsob vytvoření elementu vazby. Uživatelé pak mohou zaregistrovat oddíl rozšíření v konfiguračním souboru následujícím způsobem.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
      <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport" />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 Rozšíření lze odkazovat z vlastní vazby použít UDP jako přenos.  
  
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
  
### <a name="adding-configuration-for-a-binding"></a>Přidání konfigurace pro vazbu  
 Sekce `SampleProfileUdpBindingCollectionElement` <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> je, která `SampleProfileUdpBinding` zpřístupňuje konfiguračnísystém. Převážná část implementace je delegována `SampleProfileUdpBindingConfigurationElement`na <xref:System.ServiceModel.Configuration.StandardBindingElement>, který je odvozen z . Má `SampleProfileUdpBindingConfigurationElement` vlastnosti, které odpovídají `SampleProfileUdpBinding`vlastnosti na , `ConfigurationElement` a funkce mapovat z vazby. Nakonec je `OnApplyConfiguration` metoda přepsána `SampleProfileUdpBinding`v , jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Chcete-li zaregistrovat tuto obslužnou rutinu v konfiguračním systému, přidejte do příslušného konfiguračního souboru následující část.  
  
```xml  
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
         <sectionGroup name="bindings">  
                 <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
         </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 Potom může být odkazováno z [ \<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) konfigurační části.  
  
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
  
## <a name="adding-metadata-support-for-a-binding-element"></a>Přidání podpory metadat pro element vazby  
 Chcete-li integrovat kanál do systému metadat, musí podporovat import i export zásad. To umožňuje nástroje, jako je [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) generovat klienty elementu vazby.  
  
### <a name="adding-wsdl-support"></a>Přidání podpory WSDL  
 Prvek vazby přenosu ve vazbě je zodpovědný za export a import adresování informací v metadatech. Při použití soap vazby, prvek vazby přenosu by měl také exportovat správný identifikátor URI přenosu v metadatech. Následující ukázkový kód je převzat z [transportu: udp](../samples/transport-udp.md) ukázky.  
  
#### <a name="wsdl-export"></a>WSDL Export  
 Chcete-li exportovat `UdpTransportBindingElement` adresování <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> informace, implementuje rozhraní. Metoda <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> přidá správné informace o adresování wsdl port.  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 Implementace `UdpTransportBindingElement` <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> metody také exportuje identifikátor URI přenosu, pokud koncový bod používá vazbu SOAP:  
  
```csharp  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>WSDL Import  
 Chcete-li rozšířit systém importu WSDL na zpracování importu adres, přidejte do konfiguračního souboru svcutil.exe následující konfiguraci, jak je znázorněno v souboru Svcutil.exe.config:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </wsdlImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 Při spuštění svcutil.exe, existují dvě možnosti pro získání Svcutil.exe načíst rozšíření importu WSDL:  
  
1. Bod Svcutil.exe do konfiguračního souboru pomocí\</SvcutilConfig: soubor>.  
  
2. Přidejte oddíl konfigurace do svcutil.exe.config ve stejném adresáři jako Svcutil.exe.  
  
 Typ `UdpBindingElementImporter` implementuje <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> rozhraní. Metoda `ImportEndpoint` importuje adresu z portu WSDL:  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Přidání podpory zásad  
 Vlastní element vazby můžete exportovat kontrolní výrazy zásad ve vazbě WSDL pro koncový bod služby vyjádřit možnosti tohoto prvku vazby. Následující ukázkový kód je převzat z [transportu: udp](../samples/transport-udp.md) ukázky.  
  
#### <a name="policy-export"></a>Export zásad  
 Typ `UdpTransportBindingElement` implementuje <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> přidat podporu pro zásady exportu. V důsledku <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> toho `UdpTransportBindingElement` zahrnuje v generování zásad pro všechny vazby, která ji zahrnuje.  
  
 V <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>aplikaci přidejte kontrolní výraz pro UDP a další kontrolní výraz, pokud je kanál v režimu vícesměrového vysílání. Důvodem je, že režim vícesměrového vysílání ovlivňuje způsob vytvoření zásobníku komunikace, a proto musí být koordinován mezi oběma stranami.  
  
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
  
 Vzhledem k tomu, že vlastní <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> prvky `UdpTransportBindingElement` vazby přenosu jsou zodpovědné za zpracování adresování, implementace na musí také zpracovat export příslušných výrazů zásad WS-Addressing k označení verze ws adresování se používá.  
  
```csharp  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>Import zásad  
 Chcete-li rozšířit systém importu zásad, přidejte do konfiguračního souboru pro soubor Svcutil.exe následující konfiguraci, jak je znázorněno v souboru Svcutil.exe.config:  
  
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
  
 Pak implementujeme <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> z`UdpBindingElementImporter`naší registrované třídy ( ). V <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, zkontrolujte kontrolní výrazy v příslušném oboru názvů a zpracujte ty, které generují přenos a kontrolují, zda je vícesměrové vysílání. Kromě toho odeberte tvrzení, že dovozce zpracovává ze seznamu tvrzení vazby. Opět platí, že při spuštění Svcutil.exe existují dvě možnosti integrace:  
  
1. Bod Svcutil.exe do našeho konfiguračního souboru pomocí /SvcutilConfig:\<soubor>.  
  
2. Přidejte oddíl konfigurace do svcutil.exe.config ve stejném adresáři jako Svcutil.exe.  
  
### <a name="adding-a-custom-standard-binding-importer"></a>Přidání vlastního standardního importu vazeb  
 Svcutil.exe a <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> typ, ve výchozím nastavení rozpoznat a importovat systémem poskytované vazby. V opačném případě vazba <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> získá importován jako instance. Chcete-li povolit Svcutil.exe `SampleProfileUdpBinding` `UdpBindingElementImporter` a <xref:System.ServiceModel.Description.WsdlImporter> importovat také působí jako vlastní standardní vázací dovozce.  
  
 Vlastní standardní importér `ImportEndpoint` vazby <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> implementuje <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> metodu na rozhraní prozkoumat instanci importované z metadat a zjistit, zda mohla být generována konkrétní standardní vazby.  
  
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
  
 Obecně platí, že implementace vlastní standardní vazby import zahrnuje kontrolu vlastností importované elementy vazby k ověření, že pouze vlastnosti, které mohly být nastaveny standardní vazby byly změněny a všechny ostatní vlastnosti jsou jejich výchozí hodnoty. Základní strategií pro implementaci standardního importu vazby je vytvoření instance standardní vazby, šíření vlastností z elementů vazby na standardní instanci vazby, kterou podporuje standardní vazba, a porovnání vazby prvky ze standardní vazby s importovanými prvky vazby.
