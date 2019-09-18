---
title: Události Trasování událostí pro Windows sledování prostředků domény aplikace (ARM)
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0e4002ae248022a9e4380c79174109494b5e4ca
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046773"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a>Události Trasování událostí pro Windows sledování prostředků domény aplikace (ARM)
<a name="top"></a>Tyto události poskytují podrobné diagnostické informace o stavu domény aplikace. Tyto události můžete použít, nebo můžete použít funkci monitorování prostředků domény aplikace (ARM) a získat stejné informace.  
  
 Tato kategorie se skládá z následujících událostí:  
  
- [Událost ThreadCreated –](#threadcreated_event)  
  
- [Událost AppDomainMemAllocated](#appdomainmemallocated_event)  
  
- [AppDomainMemSurvived Event](#appdomainmemsurvived_event)  
  
- [Událost ThreadAppDomainEnter](#threadappdomainenter_event)  
  
- [Událost ThreadTerminated](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a>Událost ThreadCreated –  
 Tato událost se taky vyvolala pod poskytovatelem `ThreadDC` doběhu jako ( `AppDomainResourceManagementRundownKeyword` pod klíčovým slovem). Toto je jediná událost, která je vyvolána v rámci poskytovatele doběhu v této kategorii.  
  
 Klíčové slovo a úroveň jsou uvedeny v následující tabulce. (Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).)  
  
|Klíčové slovo pro vyvolání události|Level|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informační (4)|  
|`ThreadingKeyword` (0x10000)|Informační (4)|  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|85|Bylo vytvořeno vlákno pro doménu aplikace.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|IDvlákna|win:UInt64|ID vlákna, které bylo vytvořeno.|  
|AppDomainID|win:UInt64|Identifikátor domény aplikace, pro kterou je hlášena aktivita vlákna|  
|Příznaky|Win: UInt32|Příznaky vytvoření vlákna.|  
|ManagedThreadIndex|Win: UInt32|Spravovaný index vlákna, které bylo vytvořeno.|  
|OSThreadID|Win: UInt32|ID operačního systému vytvořeného vlákna.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a>Událost AppDomainMemAllocated  
 Klíčové slovo a úroveň jsou uvedeny v následující tabulce.  
  
|Klíčové slovo pro vyvolání události|Level|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informační (4)|  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|83|V aplikační doméně je přiděleno každé 4 MB paměti (přibližně).|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|AppDomainID|win:UInt64|Identifikátor domény aplikace, pro kterou se vykazuje využití prostředků|  
|Přidělování|win:UInt64|Celkový počet bajtů přidělených v této doméně aplikace od vytvoření domény aplikace (množství uvolněné paměti není odečteno).|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a>Událost AppDomainMemSurvived  
 Klíčové slovo a úroveň jsou uvedeny v následující tabulce.  
  
|Klíčové slovo pro vyvolání události|Level|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informační (4)|  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|84|Každé uvolnění paměti bylo ukončeno.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|AppDomainID|win:UInt64|Identifikátor domény, pro kterou se vykazuje využití prostředků|  
|Zachované|win:UInt64|Počet bajtů, které byly zachovány po poslední kolekci a které jsou známy pro tuto doménu aplikace. Toto číslo je přesné a úplné po úplné kolekci, ale po dočasné kolekci může být neúplné.|  
|ProcessSurvived|win:UInt64|Celkový počet bajtů, které byly zachovány z poslední kolekce. Po úplné kolekci představuje toto číslo počet bajtů, které se ve spravovaných haldách uchovávají živě. Po dočasné kolekci představuje toto číslo počet bajtů uchovávaných v dočasných generacích.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a>Událost ThreadAppDomainEnter  
 Klíčové slovo a úroveň jsou uvedeny v následující tabulce.  
  
|Klíčové slovo pro vyvolání události|Level|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informační (4)|  
|`ThreadingKeyword` (0x10000)|Informační (4)|  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|87|Vlákno vstoupí do domény aplikace.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|IDvlákna|win:UInt64|Identifikátor vlákna.|  
|AppDomainID|win:UInt64|Identifikátor domény aplikace|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a>Událost ThreadTerminated  
 Klíčové slovo a úroveň jsou uvedeny v následující tabulce.  
  
|Klíčové slovo pro vyvolání události|Level|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informační (4)|  
|`ThreadingKeyword` (0x10000)|Informační (4)|  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|86|Vlákno se ukončí.|  
  
 Následující tabulka ukazuje data události:  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|IDvlákna|win:UInt64|Identifikátor vlákna.|  
|AppDomainID|win:UInt64|Identifikátor domény aplikace|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
## <a name="see-also"></a>Viz také:

- [Události Trasování událostí pro Windows v CLR](clr-etw-events.md)
