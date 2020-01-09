---
title: Události Trasování událostí pro Windows sledování prostředků domény aplikace (ARM)
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
ms.openlocfilehash: 0e453b2bafffd9e07a1bdddd97282c5b97f5483d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716219"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a>Události Trasování událostí pro Windows sledování prostředků domény aplikace (ARM)

Tyto události poskytují podrobné diagnostické informace o stavu domény aplikace. Tyto události můžete použít, nebo můžete použít funkci monitorování prostředků domény aplikace (ARM) a získat stejné informace.

## <a name="threadcreated-event"></a>Událost ThreadCreated –

Tato událost je vyvolána také v rámci poskytovatele doběhu jako `ThreadDC` (pod klíčovým slovem `AppDomainResourceManagementRundownKeyword`). Toto je jediná událost, která je vyvolána v rámci poskytovatele doběhu v této kategorii.

Klíčové slovo a úroveň jsou uvedeny v následující tabulce. Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|`AppDomainResourceManagementKeyword` (0x800)|Informační (4)|
|`ThreadingKeyword` (0x10000)|Informační (4)|

Následující tabulka uvádí informace o událostech:

|Událost|ID události|Vyvolá se, když|
|-----------|--------------|-----------------|
|`ThreadCreated`|85|Bylo vytvořeno vlákno pro doménu aplikace.|

Následující tabulka ukazuje data události:

|Název pole|Datový typ|Popis|
|----------------|---------------|-----------------|
|IDvlákna|win:UInt64|ID vlákna, které bylo vytvořeno.|
|AppDomainID|win:UInt64|Identifikátor domény aplikace, pro kterou je hlášena aktivita vlákna|
|Příznaky|Win: UInt32|Příznaky vytvoření vlákna.|
|ManagedThreadIndex|Win: UInt32|Spravovaný index vlákna, které bylo vytvořeno.|
|OSThreadID|Win: UInt32|ID operačního systému vytvořeného vlákna.|
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|

## <a name="appdomainmemallocated-event"></a>Událost AppDomainMemAllocated

Klíčové slovo a úroveň jsou uvedeny v následující tabulce:

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|`AppDomainResourceManagementKeyword` (0x800)|Informační (4)|

Následující tabulka uvádí informace o událostech:

|Událost|ID události|Vyvolá se, když|
|-----------|--------------|-----------------|
|`AppDomainMemAllocated`|83|V aplikační doméně je přiděleno každé 4 MB paměti (přibližně).|

Následující tabulka ukazuje data události:

|Název pole|Datový typ|Popis|
|----------------|---------------|-----------------|
|AppDomainID|win:UInt64|Identifikátor domény aplikace, pro kterou se vykazuje využití prostředků|
|Přidělování|win:UInt64|Celkový počet bajtů přidělených v této doméně aplikace od vytvoření domény aplikace (množství uvolněné paměti není odečteno).|
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|

## <a name="appdomainmemsurvived-event"></a>Událost AppDomainMemSurvived

Klíčové slovo a úroveň jsou uvedeny v následující tabulce:

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|`AppDomainResourceManagementKeyword` (0x800)|Informační (4)|

Následující tabulka uvádí informace o událostech:

|Událost|ID události|Vyvolá se, když|
|-----------|--------------|-----------------|
|`AppDomainMemSurvived`|84|Každé uvolnění paměti bylo ukončeno.|

Následující tabulka ukazuje data události:

|Název pole|Datový typ|Popis|
|----------------|---------------|-----------------|
|AppDomainID|win:UInt64|Identifikátor domény, pro kterou se vykazuje využití prostředků|
|Zachované|win:UInt64|Počet bajtů, které byly zachovány po poslední kolekci a které jsou známy pro tuto doménu aplikace. Toto číslo je přesné a úplné po úplné kolekci, ale po dočasné kolekci může být neúplné.|
|ProcessSurvived|win:UInt64|Celkový počet bajtů, které byly zachovány z poslední kolekce. Po úplné kolekci představuje toto číslo počet bajtů, které se ve spravovaných haldách uchovávají živě. Po dočasné kolekci představuje toto číslo počet bajtů uchovávaných v dočasných generacích.|
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|

## <a name="threadappdomainenter-event"></a>Událost ThreadAppDomainEnter

Klíčové slovo a úroveň jsou uvedeny v následující tabulce:

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|`AppDomainResourceManagementKeyword` (0x800)|Informační (4)|
|`ThreadingKeyword` (0x10000)|Informační (4)|

Následující tabulka uvádí informace o událostech:

|Událost|ID události|Vyvolá se, když|
|-----------|--------------|-----------------|
|`ThreadAppDomainEnter`|87|Vlákno vstoupí do domény aplikace.|

Následující tabulka ukazuje data události:

|Název pole|Datový typ|Popis|
|----------------|---------------|-----------------|
|IDvlákna|win:UInt64|Identifikátor vlákna.|
|AppDomainID|win:UInt64|Identifikátor domény aplikace|
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|

## <a name="threadterminated-event"></a>Událost ThreadTerminated

Klíčové slovo a úroveň jsou uvedeny v následující tabulce:

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|`AppDomainResourceManagementKeyword` (0x800)|Informační (4)|
|`ThreadingKeyword` (0x10000)|Informační (4)|

Následující tabulka uvádí informace o událostech:

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
