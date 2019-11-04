---
title: Konfigurace a podpora metadat
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: 3f6d506d719cbb1b2ecc8bae223dfe73e7e2d1a9
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425136"
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
 Chcete-li povolit podporu konfiguračního souboru pro kanál, je nutné implementovat dva konfigurační oddíly, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, což umožňuje podporu konfigurace pro prvky vazby a <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, které povolují podporu konfigurace pro vazby.  
  
 Jednodušší způsob, jak to provést, je použít vzorový nástroj [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) k vygenerování konfiguračního kódu pro vaše vazby a prvky vazby.  
  
### <a name="extending-bindingelementextensionelement"></a>Rozšíření BindingElementExtensionElement  
 Následující příklad kódu je pořízen z ukázky [Transport: UDP](../samples/transport-udp.md) . `UdpTransportElement` je <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>, který zpřístupňuje `UdpTransportBindingElement` konfiguračnímu systému. U několika základních přepsání ukázka definuje název konfiguračního oddílu, typ prvku vazby a postup vytvoření prvku vazby. Uživatelé pak mohou zaregistrovat oddíl rozšíření v konfiguračním souboru následujícím způsobem.  
  
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
 Oddíl `SampleProfileUdpBindingCollectionElement` je <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602>, který zpřístupňuje `SampleProfileUdpBinding` konfiguračnímu systému. Hromadná implementace je delegována na `SampleProfileUdpBindingConfigurationElement`, která je odvozena z <xref:System.ServiceModel.Configuration.StandardBindingElement>. `SampleProfileUdpBindingConfigurationElement` obsahuje vlastnosti, které odpovídají vlastnostem `SampleProfileUdpBinding`a funkce, které mají být mapovány z vazby `ConfigurationElement`. Nakonec je metoda `OnApplyConfiguration` v `SampleProfileUdpBinding`přepsána, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Lze na něj potom odkazovat z konfiguračního oddílu [\<System. serviceModel >](../../configure-apps/file-schema/wcf/system-servicemodel.md) .  
  
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
 Element vazby přenosu ve vazbě zodpovídá za export a import informací o adresách v metadatech. Při použití vazby SOAP by měl element vazby přenosu také exportovat správný přenosový identifikátor URI v metadatech. Následující příklad kódu je pořízen z ukázky [Transport: UDP](../samples/transport-udp.md) .  
  
#### <a name="wsdl-export"></a>Export WSDL  
 Chcete-li exportovat informace o adresách, `UdpTransportBindingElement` implementuje rozhraní <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType>. Metoda <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> přidá do portu WSDL správné informace o adresách.  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 `UdpTransportBindingElement` implementace metody <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> také exportuje identifikátor URI přenosu, pokud koncový bod používá vazbu SOAP:  
  
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
  
1. Najeďte Svcutil. exe na konfigurační soubor pomocí > souboru/SvcutilConfig:\<.  
  
2. Přidejte konfigurační oddíl do souboru Svcutil. exe. config ve stejném adresáři jako soubor Svcutil. exe.  
  
 Typ `UdpBindingElementImporter` implementuje rozhraní <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType>. Metoda `ImportEndpoint` importuje adresu z portu WSDL:  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Přidání podpory zásad  
 Vlastní element vazby může exportovat kontrolní výrazy zásad ve vazbě WSDL pro koncový bod služby, aby bylo možné vyjádřit možnosti tohoto prvku vazby. Následující příklad kódu je pořízen z ukázky [Transport: UDP](../samples/transport-udp.md) .  
  
#### <a name="policy-export"></a>Export zásad  
 Typ `UdpTransportBindingElement` implementuje <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> k přidání podpory pro export zásad. V důsledku toho <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> zahrnuje `UdpTransportBindingElement` při generování zásad pro všechny vazby, které ji obsahují.  
  
 V <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>přidejte kontrolní výraz pro protokol UDP a jiný kontrolní výraz, pokud je kanál v režimu vícesměrového vysílání. Je to proto, že režim vícesměrového vysílání ovlivňuje způsob, jakým je vytvořen komunikační zásobník, a proto musí být koordinován mezi oběma stranami.  
  
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
  
 Vzhledem k tomu, že vlastní prvky vazby přenosu jsou zodpovědné za zpracování adresování, <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementace v `UdpTransportBindingElement` musí také zpracovat export příslušných kontrolních výrazů WS-Addressing, aby označovaly používané verze WS-Addressing.  
  
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
  
 Pak implementujeme <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> z naší registrované třídy (`UdpBindingElementImporter`). V <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>Projděte kontrolní výrazy v příslušném oboru názvů a zpracujte je pro generování přenosu a kontrolu, jestli se jedná o vícesměrové vysílání. Kromě toho odeberte kontrolní výrazy, které dovozce zpracovává ze seznamu kontrolních výrazů vazby. Při spuštění Svcutil. exe existují dvě možnosti integrace:  
  
1. Najeďte Svcutil. exe na náš konfigurační soubor pomocí > souboru/SvcutilConfig:\<.  
  
2. Přidejte konfigurační oddíl do souboru Svcutil. exe. config ve stejném adresáři jako soubor Svcutil. exe.  
  
### <a name="adding-a-custom-standard-binding-importer"></a>Přidání vlastního programu pro import standardních vazeb  
 Svcutil. exe a typ <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> ve výchozím nastavení rozpoznávají a naimportují vazby poskytnuté systémem. V opačném případě se vazba importuje jako instance <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>. Chcete-li povolit Svcutil. exe a <xref:System.ServiceModel.Description.WsdlImporter> importovat `SampleProfileUdpBinding` `UdpBindingElementImporter` také funguje jako vlastní import standardních vazeb.  
  
 Vlastní nástroj pro importování standardních vazeb implementuje metodu `ImportEndpoint` v rozhraní <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType>, aby kontrolovala instanci <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> importovanou z metadat, aby zjistila, jestli by mohla být vygenerovaná konkrétní standardní vazbou.  
  
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
