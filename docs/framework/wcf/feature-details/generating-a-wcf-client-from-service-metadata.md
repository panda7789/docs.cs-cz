---
title: Generování klienta WCF z metadat služby
ms.date: 03/30/2017
ms.assetid: 27f8f545-cc44-412a-b104-617e0781b803
ms.openlocfilehash: 3bdb283e461076ffd5c1e77963933de0e5b4bb02
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54570954"
---
# <a name="generating-a-wcf-client-from-service-metadata"></a>Generování klienta WCF z metadat služby
Toto téma popisuje, jak používat různé přepínače v Svcutil.exe ke generování klientů z dokumentů metadat.  
  
 Dokumenty metadat mohou být odolné úložiště nebo načítá online. Načítání online následuje protokol WS-MetadataExchange nebo protokolu Microsoft zjišťování (ROZ). Svcutil.exe vystaví následující žádostí o metadata současně k načtení metadat:  
  
-   Požadavek WS-MetadataExchange (MEX) na zadané adresy.  
  
-   MEX požadavek na zadané adresy s `/mex` připojí.  
  
-   DISCO požadavku (pomocí [DiscoveryClientProtocol](https://go.microsoft.com/fwlink/?LinkId=94777) z webových služeb ASP.NET s) na zadané adresy.  
  
 Svcutil.exe generuje klienta na základě webové služby WSDL (Description Language) nebo zásad souboru přijatých ze služby. Hlavní název uživatele (UPN) je generována zřetězením uživatelské jméno s "\@" a následným přidáním plně kvalifikovaný název domény (FQDN). Pro uživatele, kteří si zaregistrovali ve službě Active Directory, ale tento formát není platný a hlavní název uživatele, který generuje nástroj způsobí, že k chybě v ověřování protokolem Kerberos se následující chybová zpráva: **Pokus o přihlášení se nezdařilo.** Chcete-li vyřešit potíže, vyřešit ručně instalační soubor klienta, nástroj vygeneruje.  
  
```  
svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>  
```  
  
## <a name="referencing-and-sharing-types"></a>Odkazování na a sdílení typů  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/ reference:\<cesta k souboru >**|Typy odkazů v zadaném sestavení. Při generování klientů, pokud pomocí této možnosti zadejte sestavení, která může obsahovat typy představující importovaná metadata.<br /><br /> Krátký tvar: `/r`|  
|**/excludeType:\<typ >**|Určuje název plně kvalifikovaný nebo sestavením kvalifikovaný typ mají být vyloučeny z smlouvy odkazované typy.<br /><br /> Krátký tvar: `/et`|  
  
## <a name="choosing-a-serializer"></a>Výběr serializátor  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/serializer:Auto**|Automaticky vybere serializátor. Tady se používá `DataContract` serializátor. Když se to nepovede, `XmlSerializer` se používá.<br /><br /> Krátký tvar: `/ser:Auto`|  
|**/serializer:DataContractSerializer**|Generuje datové typy, které používají `DataContract` serializátor pro serializaci a deserializaci.<br /><br /> Krátký tvar: `/ser:DataContractSerializer`|  
|**/serializer:XmlSerializer**|Generuje datové typy, které používají `XmlSerializer` k serializaci a deserializaci.<br /><br /> Krátký tvar: `/ser:XmlSerializer`|  
|**/importXmlTypes**|Konfiguruje `DataContract` serializátor pro import jinou hodnotu než`DataContract` typy jako `IXmlSerializable` typy.<br /><br /> Krátký tvar: `/ixt`|  
|**/dataContractOnly**|Generuje kód pro `DataContract` pouze typy. `ServiceContract` typy jsou generovány.<br /><br /> Měli byste určit pouze místních metadat souborů pro tuto možnost.<br /><br /> Krátký tvar: `/dconly`|  
  
## <a name="choosing-a-language-for-the-client"></a>Výběr jazyka klienta  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/Language:\<jazyk >**|Určuje programovací jazyk, který má použít pro generování kódu. Zadejte buď název jazyka zaregistrovaný v souboru Machine.config nebo plně kvalifikovaný název třídy, která dědí z <xref:System.CodeDom.Compiler.CodeDomProvider>.<br /><br /> Hodnoty: c#, cs, csharp, vb, vbs, visualbasic, vbscript, javascript, c ++, mc, cpp<br /><br /> Výchozí: csharp<br /><br /> Krátký tvar: `/l`<br /><br /> Další informace najdete v tématu [CodeDomProvider třídy](https://go.microsoft.com/fwlink/?LinkId=94778).|  
  
## <a name="choosing-a-namespace-for-the-client"></a>Výběr Namespace pro klienta  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/ NAMESPACE:\<string, string >**|Určuje mapování z WSDL nebo XML schématu `targetNamespace` k oboru názvů common language runtime (CLR). Použití zástupného znaku (*) pro `targetNamespace` mapuje všechny `targetNamespaces` bez explicitního mapování na tento obor názvů CLR.<br /><br /> Pokud chcete mít jistotu, že název kontraktu zprávy nejsou v konfliktu s názvem operace, buď kvalifikovat odkaz na typ double dvojtečky (`::`) nebo se ujistěte, názvy musí být jedinečné.<br /><br /> Výchozí hodnota: Odvozeno z cílového oboru názvů dokumentu schématu pro `DataContracts`. Výchozí obor názvů je používán pro všechny ostatní generované typy.<br /><br /> Krátký tvar: `/n`|  
  
## <a name="choosing-a-data-binding"></a>Výběr datové vazby  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/enableDataBinding**|Implementuje <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní na všech `DataContract` typů, který chcete vytvořit datovou vazbu.<br /><br /> Krátký tvar: `/edb`|  
  
## <a name="generating-configuration"></a>Generování konfigurace  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/config:\<configFile>**|Určuje název souboru pro vygenerovaný konfigurační soubor.<br /><br /> Výchozí: output.config|  
|**/mergeConfig**|Sloučí existující soubor, místo abyste přepsali tu stávající soubor vygenerovanou konfiguraci.|  
|**/noConfig**|Konfigurační soubory nejsou generovány.|  
  
## <a name="see-also"></a>Viz také:
- [Používání metadat](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [Přehled architektury metadat](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
