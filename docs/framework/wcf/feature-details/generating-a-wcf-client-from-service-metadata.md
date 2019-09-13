---
title: Generování klienta WCF z metadat služby
ms.date: 03/30/2017
ms.assetid: 27f8f545-cc44-412a-b104-617e0781b803
ms.openlocfilehash: 938b1363be3b168fce74d80b47c9ae463d018669
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70892751"
---
# <a name="generating-a-wcf-client-from-service-metadata"></a>Generování klienta WCF z metadat služby
Toto téma popisuje, jak pomocí různých přepínačů v nástroji Svcutil. exe generovat klienty z dokumentů metadat.  
  
 Dokumenty metadat můžou být na trvalém úložišti nebo je možné je načíst online. Online načítání následuje buď prostřednictvím protokolu WS-MetadataExchange, nebo protokolu Microsoft Discovery (DISCe). Svcutil. exe při načítání metadat současně vydává následující požadavky na metadata:  
  
- Požadavek WS-MetadataExchange (MEX) na zadanou adresu.  
  
- Požadavek MEX na zadanou adresu se `/mex` připojil.  
  
- Požadavek na DISCích (pomocí [DiscoveryClientProtocol](https://go.microsoft.com/fwlink/?LinkId=94777) z webových služeb ASP.NET) na zadanou adresu.  
  
 Svcutil. exe vygeneruje klienta založeného na jazyce WSDL (Web Services Description Language) nebo souboru zásad přijatém ze služby. Hlavní název uživatele (UPN) je vygenerován zřetězením uživatelského jména s "\@" a následným přidáním plně kvalifikovaného názvu domény (FQDN). Pro uživatele, kteří jsou zaregistrovaní ve službě Active Directory, není tento formát platný a hlavní název uživatele, který Nástroj generuje, způsobuje selhání při ověřování pomocí protokolu Kerberos s následující chybovou zprávou: **Pokus o přihlášení se nezdařil.** Chcete-li tento problém vyřešit, opravte ručně soubor klienta, který nástroj vygeneroval.  
  
```console
svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>  
```  
  
## <a name="referencing-and-sharing-types"></a>Odkazování a sdílení typů  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/Reference:\<> Cesta k souboru**|Odkazuje na typy v zadaném sestavení. Při generování klientů pomocí této možnosti zadejte sestavení, která mohou obsahovat typy představující importovaná metadata.<br /><br /> Krátký tvar:`/r`|  
|**/excludeType:\<typ >**|Určuje plně kvalifikovaný název nebo kvalifikovaný název sestavení, který bude vyloučen z odkazovaných typů kontraktů.<br /><br /> Krátký tvar:`/et`|  
  
## <a name="choosing-a-serializer"></a>Výběr serializátoru  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/Serializer: auto**|Automaticky vybere serializátor. Používá `DataContract` serializátor. Pokud se to nepovede `XmlSerializer` , použije se.<br /><br /> Krátký tvar:`/ser:Auto`|  
|**/serializer:DataContractSerializer**|Generuje datové typy, které používají `DataContract` serializátor pro serializaci a deserializaci.<br /><br /> Krátký tvar:`/ser:DataContractSerializer`|  
|**/serializer:XmlSerializer**|Generuje datové typy, které používají `XmlSerializer` pro serializaci a deserializaci.<br /><br /> Krátký tvar:`/ser:XmlSerializer`|  
|**/importXmlTypes**|Nakonfiguruje`DataContract` `IXmlSerializable` serializátor pro importování typů, které nejsou typy. `DataContract`<br /><br /> Krátký tvar:`/ixt`|  
|**/dataContractOnly**|Generuje kód pouze `DataContract` pro typy. `ServiceContract`generují se typy.<br /><br /> Pro tuto možnost byste měli zadat jenom místní soubory metadat.<br /><br /> Krátký tvar:`/dconly`|  
  
## <a name="choosing-a-language-for-the-client"></a>Volba jazyka pro klienta  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/Language:\<> jazyka**|Určuje programovací jazyk, který se má použít pro generování kódu. Zadejte buď název jazyka zaregistrovaný v souboru Machine. config, nebo plně kvalifikovaný název třídy, která dědí z <xref:System.CodeDom.Compiler.CodeDomProvider>.<br /><br /> Hodnoty: c#, cs, CSharp, VB, VBS, VisualBasic, VBScript, JavaScript, c++, MC, cpp<br /><br /> Výchozí: CSharp<br /><br /> Krátký tvar:`/l`<br /><br /> Další informace naleznete v tématu [Třída CodeDomProvider](https://go.microsoft.com/fwlink/?LinkId=94778).|  
  
## <a name="choosing-a-namespace-for-the-client"></a>Výběr oboru názvů pro klienta  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/Namespace:\<String, > řetězců**|Určuje mapování ze schématu `targetNamespace` WSDL nebo XML na obor názvů Common Language Runtime (CLR). Použití zástupného znaku (*) pro `targetNamespace` všechny `targetNamespaces` mapy bez explicitního mapování na tento obor názvů CLR.<br /><br /> Aby se zajistilo, že název kontraktu zprávy nekoliduje s názvem operace, zařaďte odkaz na typ pomocí dvojitých dvojtečk (`::`) nebo se ujistěte, že jsou názvy jedinečné.<br /><br /> Výchozí Odvozeno z cílového oboru názvů dokumentu schématu pro `DataContracts`. Výchozí obor názvů se používá pro všechny ostatní generované typy.<br /><br /> Krátký tvar:`/n`|  
  
## <a name="choosing-a-data-binding"></a>Výběr datové vazby  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/enableDataBinding**|Implementuje rozhraní pro všechny `DataContract` typy, aby bylo možné datovou vazbu povolit. <xref:System.ComponentModel.INotifyPropertyChanged><br /><br /> Krátký tvar:`/edb`|  
  
## <a name="generating-configuration"></a>Generování konfigurace  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/config:\<configFile>**|Určuje název souboru generovaného konfiguračního souboru.<br /><br /> Výchozí: Output. config|  
|**/mergeConfig**|Sloučí vygenerovanou konfiguraci do existujícího souboru namísto přepsání stávajícího souboru.|  
|**/noConfig**|Negenerovat konfigurační soubory.|  
  
## <a name="see-also"></a>Viz také:

- [Používání metadat](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [Přehled architektury metadat](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
