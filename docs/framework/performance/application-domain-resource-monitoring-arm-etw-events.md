---
title: Události Trasování událostí pro Windows sledování prostředků domény aplikace (ARM)
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2bb2b0dd95877fc6492f6d23a19c14688cd78f7c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133819"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a>Události Trasování událostí pro Windows sledování prostředků domény aplikace (ARM)
<a name="top"></a> Tyto události poskytují podrobné diagnostické informace o stavu domény aplikace. Můžete použít tyto události nebo použití prostředků domény aplikace (ARM) funkci monitorování získávat stejné informace.  
  
 Tato kategorie se skládá z následujících událostí:  
  
-   [ThreadCreated události](#threadcreated_event)  
  
-   [AppDomainMemAllocated události](#appdomainmemallocated_event)  
  
-   [AppDomainMemSurvived Event](#appdomainmemsurvived_event)  
  
-   [ThreadAppDomainEnter události](#threadappdomainenter_event)  
  
-   [ThreadTerminated události](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a>ThreadCreated události  
 Tato událost se vyvolá také jako skrze zprostředkovatele doběhu `ThreadDC` (v části `AppDomainResourceManagementRundownKeyword` – klíčové slovo). Toto je jediná událost, která je vyvolána v této kategorii skrze zprostředkovatele doběhu.  
  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň. (Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informational(4)|  
|`ThreadingKeyword` (0x10000)|Informational(4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|85|Vlákno bylo vytvořeno pro doménu aplikace.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Idvlákna|win:UInt64|ID vlákna, který byl vytvořen.|  
|AppDomainID|win:UInt64|Identifikátor domény aplikace, pro které vlákno je hlášena aktivity.|  
|Příznaky|win:UInt32|Příznaky vytváření vlákna.|  
|ManagedThreadIndex|win:UInt32|Spravovat indexu vlákna, který byl vytvořen.|  
|OSThreadID|win:UInt32|Operační systém ID vlákna, který byl vytvořen.|  
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a>AppDomainMemAllocated události  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informational(4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|83|Každé 4 MB paměti (přibližně) je přidělena v doméně aplikace.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|AppDomainID|win:UInt64|Identifikátor domény aplikace, pro který prostředek se hlásí využití.|  
|přidělené|win:UInt64|Celkový počet bajtů alokovaných v této doméně aplikace, od vytvoření domény aplikace (množství uvolněné paměti není odečtena).|  
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a>AppDomainMemSurvived Event  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informational(4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|84|Každá kolekce uvolnění paměti bylo již ukončeno.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|AppDomainID|win:UInt64|Identifikátor domény, pro který prostředek se hlásí využití.|  
|Zůstat naživu při|win:UInt64|Počet bajtů, které zůstat naživu po poslední a, které jsou známé uchovávat podle této domény aplikace. Toto číslo je přesné a úplné po celé kolekce, ale mohou být neúplné po dočasné kolekce.|  
|ProcessSurvived|win:UInt64|Celkový počet bajtů, které zůstat naživu z posledního kolekce. Po celé kolekce toto číslo představuje počet bajtů se konají za provozu ve spravované haldy. Po dočasné kolekce toto číslo představuje počet bajtů uložených za provozu v dočasných generací.|  
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a>ThreadAppDomainEnter Event  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informational(4)|  
|`ThreadingKeyword` (0x10000)|Informational(4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|87|Vlákno přejde do domény aplikace.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Idvlákna|win:UInt64|Identifikátor vlákna.|  
|AppDomainID|win:UInt64|Identifikátor domény aplikace.|  
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a>ThreadTerminated události  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informational(4)|  
|`ThreadingKeyword` (0x10000)|Informational(4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|86|Vlákno ukončí.|  
  
 V následující tabulce jsou uvedeny data události:  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Idvlákna|win:UInt64|Identifikátor vlákna.|  
|AppDomainID|win:UInt64|Identifikátor domény aplikace.|  
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
## <a name="see-also"></a>Viz také:

- [Události Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-events.md)
