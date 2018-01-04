---
title: "Události Trasování událostí pro Windows sledování prostředků domény aplikace (ARM)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6384700c7039cb705f2db759ebd3d733bf8954ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a>Události Trasování událostí pro Windows sledování prostředků domény aplikace (ARM)
<a name="top"></a>Tyto události poskytují podrobné diagnostické informace týkající se stavu služby domény aplikace. Můžete použít tyto události nebo pomocí prostředků domény aplikace (ARM) funkci monitorování získat stejné informace.  
  
 Tato kategorie se skládá z následujících událostí:  
  
-   [Threadcreated – událost](#threadcreated_event)  
  
-   [AppDomainMemAllocated událostí](#appdomainmemallocated_event)  
  
-   [AppDomainMemSurvived událostí](#appdomainmemsurvived_event)  
  
-   [ThreadAppDomainEnter událostí](#threadappdomainenter_event)  
  
-   [ThreadTerminated událostí](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a>Threadcreated – událost  
 Tato událost je aktivována také v rámci sekvence daneho zprostředkovatele jako `ThreadDC` (v části `AppDomainResourceManagementRundownKeyword` – klíčové slovo). Toto je pouze událost, která se vyvolá v rámci sekvence daneho zprostředkovatele v této kategorii.  
  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň. (Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword`(0x800)|Informational(4)|  
|`ThreadingKeyword`(0x10000)|Informational(4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|85|Vlákno byl vytvořen pro doménu aplikace.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ID podprocesu|Win: UInt64|ID vlákna, která byla vytvořena.|  
|AppDomainID|Win: UInt64|Identifikátor doménu aplikace, pro které vlákno je hlášena aktivity.|  
|Příznaky|Win: UInt32|Vytvoření příznaky přístup z více vláken.|  
|ManagedThreadIndex|Win: UInt32|Spravované index vláken, která byla vytvořena.|  
|OSThreadID|Win: UInt32|Operační systém ID vlákna, která byla vytvořena.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a>AppDomainMemAllocated událostí  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword`(0x800)|Informational(4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|83|Každý 4 MB paměti (přibližně) je přidělen v doméně aplikace.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|AppDomainID|Win: UInt64|Identifikátor doménu aplikace, pro který prostředek je hlášena využití.|  
|Přidělené|Win: UInt64|Celkový počet bajtů přidělených v této doméně aplikace od vytvoření domény aplikace (množství uvolněné paměti není odečítat).|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a>AppDomainMemSurvived událostí  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword`(0x800)|Informational(4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|84|Uvolňování paměti jednotlivých byl ukončen.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|AppDomainID|Win: UInt64|Identifikátor domény, pro který prostředek je hlášena využití.|  
|Zůstal naživu|Win: UInt64|Počet bajtů, který zůstal naživu po poslední kolekce a které jsou známé uchovávat tato doména aplikace. Toto číslo je přesné a úplné po úplné kolekce, ale mohou být neúplné po dočasné kolekce.|  
|ProcessSurvived|Win: UInt64|Celkový počet bajtů, které zůstal naživu z poslední kolekce. Po kompletní sadu toto číslo představuje počet bajtů, se uchovávat za provozu ve spravovaných haldách. Po dočasné kolekce toto číslo představuje počet bajtů uchovávat v dočasných generace za provozu.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a>ThreadAppDomainEnter událostí  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword`(0x800)|Informational(4)|  
|`ThreadingKeyword`(0x10000)|Informational(4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|87|Vlákno vstupuje do domény aplikace.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ID podprocesu|Win: UInt64|Identifikátor přístup z více vláken.|  
|AppDomainID|Win: UInt64|Identifikátor domény aplikace.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a>ThreadTerminated událostí  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword`(0x800)|Informational(4)|  
|`ThreadingKeyword`(0x10000)|Informational(4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|86|Vlákno ukončí.|  
  
 Následující tabulka zobrazuje data událostí:  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ID podprocesu|Win: UInt64|Identifikátor přístup z více vláken.|  
|AppDomainID|Win: UInt64|Identifikátor domény aplikace.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
## <a name="see-also"></a>Viz také  
 [Události Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-events.md)
