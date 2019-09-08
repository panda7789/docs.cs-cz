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
# <a name="configuration-and-metadata-support"></a>Konfigurace a podpora metadat
Toto téma popisuje, jak povolit podporu konfigurace a metadat pro vazby a prvky vazby.  
  
## <a name="overview-of-configuration-and-metadata"></a>Přehled konfigurace a metadat  
 Toto téma popisuje následující úkoly, což jsou volitelné položky 1, 2 a 4 v seznamu úkolů [Vývoj kanálů](developing-channels.md) .  
  
- Povolení podpory konfiguračního souboru pro element vazby.  
  
- Povolení podpory konfiguračního souboru pro vazbu.  
  
- Exportování kontrolních výrazů WSDL a zásad pro element vazby.  
  
- Identifikují se kontrolní výrazy WSDL a zásad pro vložení a konfiguraci vazby nebo elementu vazby.  
  
 Informace o vytváření uživatelsky definovaných vazeb a elementů vazby naleznete v tématu [vytváření uživatelsky definovaných vazeb](creating-user-defined-bindings.md) a [Vytvoření BindingElement](creating-a-bindingelement.md)(v uvedeném pořadí).  
  
## <a name="adding-configuration-support"></a>Přidání podpory konfigurace  
 Chcete-li povolit podporu konfiguračního souboru pro kanál, je nutné implementovat dva konfigurační oddíly <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>,, což umožňuje podporu konfigurace pro prvky vazby <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> a a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, které povolují podporu konfigurace pro vazeb.  
  
 Jednodušší způsob, jak to provést, je použít vzorový nástroj [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) k vygenerování konfiguračního kódu pro vaše vazby a prvky vazby.  
  
### <a name="extending-bindingelementextensionelement"></a>Rozšíření BindingElementExtensionElement  
 Následující příklad kódu je pořízen z [přenosu: Ukázka](../samples/transport-udp.md) UDP Je a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> zpřístupňuje`UdpTransportBindingElement`konfiguračnímusystému. `UdpTransportElement` U několika základních přepsání ukázka definuje název konfiguračního oddílu, typ prvku vazby a postup vytvoření prvku vazby. Uživatelé pak mohou zaregistrovat oddíl rozšíření v konfiguračním souboru následujícím způsobem.  
  
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
  
 Na rozšíření se dá odkazovat z vlastních vazeb na použití UDP jako přenosu.  
  
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
 `SampleProfileUdpBinding` Oddíl `SampleProfileUdpBindingCollectionElement` ,kterýzveřejňujekonfiguračnímusystému<xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> . Hromadná implementace je delegována na `SampleProfileUdpBindingConfigurationElement`, který je odvozen z. <xref:System.ServiceModel.Configuration.StandardBindingElement> Obsahuje vlastnosti, které odpovídají vlastnostem na `SampleProfileUdpBinding`, a `ConfigurationElement` funkce, které mají být mapovány z vazby. `SampleProfileUdpBindingConfigurationElement` Nakonec je `SampleProfileUdpBinding`Metoda přepsána v, jak je znázorněno v následujícím ukázkovém kódu. `OnApplyConfiguration`  
  
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
  
 K registraci této obslužné rutiny pomocí konfiguračního systému přidejte následující oddíl do příslušného konfiguračního souboru.  
  
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
  
 Pak na něj můžete odkazovat z [ \<konfiguračního oddílu System. ServiceModel >](../../configure-apps/file-schema/wcf/system-servicemodel.md) .  
  
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
 Pro integraci kanálu do systému metadat musí podporovat import i export zásad. To umožňuje nástrojům, jako je nástroj pro dodávání [metadat ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) , generovat klienty elementu vazby.  
  
### <a name="adding-wsdl-support"></a>Přidání podpory WSDL  
 Element vazby přenosu ve vazbě zodpovídá za export a import informací o adresách v metadatech. Při použití vazby SOAP by měl element vazby přenosu také exportovat správný přenosový identifikátor URI v metadatech. Následující příklad kódu je pořízen z [přenosu: Ukázka](../samples/transport-udp.md) UDP  
  
#### <a name="wsdl-export"></a>Export WSDL  
 Chcete-li exportovat informace o `UdpTransportBindingElement` adresách <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> , implementuje rozhraní. <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> Metoda přidá správné informace o adresování do portu WSDL.  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 `UdpTransportBindingElement` Implementace<xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> metody také exportuje identifikátor URI přenosu, pokud koncový bod používá vazbu SOAP:  
  
```csharp  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>Import WSDL  
 Chcete-li roztáhnout systém importu WSDL pro zpracování importu adres, přidejte následující konfiguraci do konfiguračního souboru pro Svcutil. exe, jak je znázorněno v souboru Svcutil. exe. config:  
  
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
  
 Při spuštění Svcutil. exe jsou k dispozici dvě možnosti, jak Svcutil. exe načíst rozšíření importu WSDL:  
  
1. Najeďte Svcutil. exe na konfigurační soubor pomocí souboru/SvcutilConfig:\<>.  
  
2. Přidejte konfigurační oddíl do souboru Svcutil. exe. config ve stejném adresáři jako soubor Svcutil. exe.  
  
 `UdpBindingElementImporter` Typ<xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> implementuje rozhraní. `ImportEndpoint` Metoda importuje adresu z portu WSDL:  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Přidání podpory zásad  
 Vlastní element vazby může exportovat kontrolní výrazy zásad ve vazbě WSDL pro koncový bod služby, aby bylo možné vyjádřit možnosti tohoto prvku vazby. Následující příklad kódu je pořízen z [přenosu: Ukázka](../samples/transport-udp.md) UDP  
  
#### <a name="policy-export"></a>Export zásad  
 `UdpTransportBindingElement` Typ implementuje<xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> k přidání podpory pro export zásad. Výsledkem je, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> že zahrnuje `UdpTransportBindingElement` generování zásad pro všechny vazby, které ji obsahují.  
  
 V <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>přidejte kontrolní výraz pro UDP a jiný kontrolní výraz, pokud je kanál v režimu vícesměrového vysílání. Je to proto, že režim vícesměrového vysílání ovlivňuje způsob, jakým je vytvořen komunikační zásobník, a proto musí být koordinován mezi oběma stranami.  
  
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
  
 Vzhledem k tomu, že vlastní prvky vazby přenosu jsou zodpovědné za <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> zpracování adresování `UdpTransportBindingElement` , implementace na musí také zpracovávat příslušné kontrolní výrazy WS-Addressing, aby označovaly verzi elementu WS-Addressing. používá se.  
  
```csharp  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>Import zásad  
 Chcete-li přidat systém pro import zásad, přidejte následující konfiguraci do konfiguračního souboru pro Svcutil. exe, jak je znázorněno v souboru Svcutil. exe. config:  
  
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
  
 Pak implementujeme <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> z naší registrované třídy (`UdpBindingElementImporter`). V <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, Prověřte kontrolní výrazy v příslušném oboru názvů a zpracujte je pro generování přenosu a kontrolu, jestli se jedná o vícesměrové vysílání. Kromě toho odeberte kontrolní výrazy, které dovozce zpracovává ze seznamu kontrolních výrazů vazby. Při spuštění Svcutil. exe existují dvě možnosti integrace:  
  
1. Najeďte Svcutil. exe na náš konfigurační soubor pomocí souboru/svcutilConfig\<: >.  
  
2. Přidejte konfigurační oddíl do souboru Svcutil. exe. config ve stejném adresáři jako soubor Svcutil. exe.  
  
### <a name="adding-a-custom-standard-binding-importer"></a>Přidání vlastního programu pro import standardních vazeb  
 Svcutil. exe a <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> typ, ve výchozím nastavení rozpoznávají a naimportují vazby poskytnuté systémem. V opačném případě se vazba naimportuje jako <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance. Chcete-li povolit Svcutil. exe <xref:System.ServiceModel.Description.WsdlImporter> a `SampleProfileUdpBinding` importovat `UdpBindingElementImporter` také jako vlastní import standardních vazeb.  
  
 Vlastní nástroj `ImportEndpoint` <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> pro import standardních vazeb implementuje metodu na rozhraníprokontroluinstanceimportovanézmetadat,abybylomožnézjistit,zdabymohlabýtvygenerovánakonkrétnístandardnívazbou.<xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType>  
  
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
  
 Obecně implementace vlastního programu pro importování standardní vazby zahrnuje kontrolu vlastností importovaných prvků vazby, aby bylo možné ověřit, zda byly změněny pouze vlastnosti, které by mohly být nastaveny standardní vazbou, a všechny ostatní vlastnosti jsou jejich výchozími hodnotami. Základní strategií pro implementaci programu pro import standardních vazeb je vytvoření instance standardní vazby, šíření vlastností z prvků vazby na standardní instanci vazby, kterou podporuje standardní vazba, a porovnáním vazby prvky ze standardní vazby s importovanými prvky vazby.
