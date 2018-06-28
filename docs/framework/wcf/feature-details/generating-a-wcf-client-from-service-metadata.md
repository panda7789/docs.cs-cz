---
title: Generování klienta WCF z metadat služby
ms.date: 03/30/2017
ms.assetid: 27f8f545-cc44-412a-b104-617e0781b803
ms.openlocfilehash: 55034868b465b63dca3ca28238d81b348d9d6893
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027925"
---
# <a name="generating-a-wcf-client-from-service-metadata"></a>Generování klienta WCF z metadat služby
Toto téma popisuje, jak používat různé přepínače v Svcutil.exe generovat klienty z dokumentů metadat.  
  
 Dokumenty metadat na odolná úložiště může být nebo získat online. Načítání online následuje protokol WS-MetadataExchange nebo protokol Microsoft zjišťování (DISCO). Svcutil.exe vystaví následující požadavků na metadata současně pro načtení metadat:  
  
-   WS-MetadataExchange (MEX) požadavek na zadaná adresa.  
  
-   MEX žádost o zadaná adresa s `/mex` připojí.  
  
-   DISCO požadavku (pomocí [DiscoveryClientProtocol](http://go.microsoft.com/fwlink/?LinkId=94777) z webových služeb ASP.NET) pro zadaná adresa.  
  
 Svcutil.exe generuje klienta na základě webové služby popis Language (WSDL) nebo zásady souboru přijal od služby. Hlavní název uživatele (UPN) je generována zřetězením uživatelské jméno s "\@" a následným přidáním plně kvalifikovaný název domény (FQDN). Ale pro uživatele, kteří si zaregistrovali na službě Active Directory, tento formát není platný a názvu UPN, které nástroj generuje způsobí selhání v ověřování protokolem Kerberos se následující chybová zpráva: **pokus o přihlášení se nezdařilo.** Chcete-li vyřešit tento problém, opravte ručně, nástroj vygeneruje soubor klienta.  
  
```  
svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>  
```  
  
## <a name="referencing-and-sharing-types"></a>Sdílení typy a odkazování na  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/ reference:\<cesta k souboru >**|Typy odkazů v zadaném sestavení. Generování klienty, když pomocí této možnosti zadejte sestavení, která může obsahovat typy, které představují metadata importována.<br /><br /> Krátkých úseků: `/r`|  
|**/excludeType:\<typ >**|Určuje název plně kvalifikovaný nebo sestavení kvalifikovaný typ mají být vyloučeny z typů odkazované kontrakt.<br /><br /> Krátkých úseků: `/et`|  
  
## <a name="choosing-a-serializer"></a>Výběr označuje, že serializátor  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/serializer:Auto**|Automaticky vybere serializátor. Se používá `DataContract` serializátor. Pokud se to nezdaří, `XmlSerializer` se používá.<br /><br /> Krátkých úseků: `/ser:Auto`|  
|**/serializer:dataContractSerializer**|Generuje datové typy, které používají `DataContract` serializátor k serializaci a deserializaci.<br /><br /> Krátkých úseků: `/ser:DataContractSerializer`|  
|**/serializer:XmlSerializer**|Generuje datové typy, které používají `XmlSerializer` k serializaci a deserializaci.<br /><br /> Krátkých úseků: `/ser:XmlSerializer`|  
|**/importXmlTypes**|Nakonfiguruje `DataContract` serializátor import jinou hodnotu než`DataContract` typy jako `IXmlSerializable` typy.<br /><br /> Krátkých úseků: `/ixt`|  
|**/dataContractOnly**|Generuje kód pro `DataContract` pouze typy. `ServiceContract` typy jsou generovány.<br /><br /> Musíte zadat pouze místních metadat soubory pro tuto možnost.<br /><br /> Krátkých úseků: `/dconly`|  
  
## <a name="choosing-a-language-for-the-client"></a>Výběr jazyka klienta  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/Language:\<jazyka >**|Určuje programovací jazyk, který chcete použít pro generování kódu. Zadejte název jazyka zaregistrovat v souboru Machine.config nebo plně kvalifikovaný název třídy, která dědí z <xref:System.CodeDom.Compiler.CodeDomProvider>.<br /><br /> Hodnoty: c#, cs, csharp, vb, vbs, visualbasic, vbscript, javascript, c ++, mc, cpp<br /><br /> Výchozí: csharp<br /><br /> Krátkých úseků: `/l`<br /><br /> Další informace najdete v tématu [CodeDomProvider třída](http://go.microsoft.com/fwlink/?LinkId=94778).|  
  
## <a name="choosing-a-namespace-for-the-client"></a>Výběr Namespace pro klienta  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/ NAMESPACE:\<řetězec, řetězec >**|Určuje mapování z WSDL nebo schématu XML `targetNamespace` do běžné oboru názvů language runtime (CLR). Pomocí zástupného znaku (*) pro `targetNamespace` mapuje všechny `targetNamespaces` bez explicitní mapování do daného oboru názvů CLR.<br /><br /> Abyste měli jistotu, že název kontraktu zpráv nejsou v konfliktu s názvem operace, buď kvalifikaci odkaz na typ dvojitý dvojtečky (`::`) nebo zkontrolujte, zda jsou jedinečné názvy.<br /><br /> Výchozí hodnota: Odvozené z dokumentu schéma pro cílový obor názvů `DataContracts`. Výchozí obor názvů se používá pro všechny ostatní typy vygenerovaný.<br /><br /> Krátkých úseků: `/n`|  
  
## <a name="choosing-a-data-binding"></a>Výběr datová vazba  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/enableDataBinding**|Implementuje <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní na všech `DataContract` typy povolit datové vazby.<br /><br /> Krátkých úseků: `/edb`|  
  
## <a name="generating-configuration"></a>Generování konfigurace  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/ config:\<configFile >**|Určuje název souboru pro generovaný konfiguračního souboru.<br /><br /> Výchozí: output.config|  
|**/mergeConfig**|Vygenerovaný konfigurace sloučí existující soubor, místo přepsal existující soubor.|  
|**/ noconfig**|Nevydávají konfigurační soubory.|  
  
## <a name="see-also"></a>Viz také  
 [Používání metadat](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [Přehled architektury metadat](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
