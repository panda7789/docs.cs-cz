---
title: Události Trasování událostí pro Windows metod
description: Viz události ETW, které shromažďují informace specifické pro metody, jako jsou události metody CLR, značka metody CLR nebo podrobná událost metody CLR a MethodJittingStarted.
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, method events (CLR)
- method events [.NET Framework]
ms.assetid: 167a4459-bb6e-476c-9046-7920880f2bb5
ms.openlocfilehash: f48867a0aef417ad0b19a15d78e0c0f01a7c30a1
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474316"
---
# <a name="method-etw-events"></a>Události Trasování událostí pro Windows metod

Tyto události shromažďují informace, které jsou specifické pro metody. Datová část těchto událostí je požadována pro rozlišení symbolu. Kromě toho tyto události poskytují užitečné informace, jako je počet volání metody.

Všechny události metody mají úroveň "informativní" (4). Všechny podrobné události metody mají úroveň verbose (5).

Všechny události metody jsou vyvolány `JITKeyword` klíčovým slovem (0x10) nebo `NGenKeyword` klíčovým slovem (0x20) pod poskytovatelem modulu runtime, nebo `JitRundownKeyword` (0x10) nebo `NGENRundownKeyword` (0x20) pod poskytovatelem doběhu.

## <a name="clr-method-events"></a>Události metody CLR

Klíčové slovo a úroveň jsou uvedeny v následující tabulce. Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|`JITKeyword`(0x10) modul runtime – poskytovatel|Informační (4)|
|`NGenKeyword`(0x20) modul runtime – poskytovatel|Informační (4)|
|`JitRundownKeyword`(0x10) doběhu poskytovatel|Informační (4)|
|`NGENRundownKeyword`(0x20) doběhu poskytovatel|Informační (4)|

Následující tabulka uvádí informace o událostech:

|Událost|ID události|Popis|
|-----------|--------------|-----------------|
|`MethodLoad_V1`|136|Vyvolá se v případě, že je metoda načtena za běhu (načtena JIT) nebo je načtena image NGEN. Dynamické a obecné metody nepoužívají tuto verzi pro načtení metody. V pomocníkech JIT se tato verze nikdy nepoužívá.|
|`MethodUnLoad_V1`|137|Je aktivována, když dojde k uvolnění modulu nebo když dojde k zničení domény aplikace. Dynamické metody nikdy nepoužívají tuto verzi pro uvolňování metod.|
|`MethodDCStart_V1`|137|Vytvoří výčet metod během doběhu spuštění.|
|`MethodDCEnd_V1`|138|Vytvoří výčet metod během koncového doběhu.|

Následující tabulka ukazuje data události:

|Název pole|Datový typ|Popis|
|----------------|---------------|-----------------|
|MethodID|Win: UInt64|Jedinečný identifikátor metody V případě pomocných metod JIT je tato metoda nastavena na počáteční adresu metody.|
|ModuleID|Win: UInt64|Identifikátor modulu, ke kterému patří tato metoda (0 pro pomocníky JIT.)|
|MethodStartAddress|Win: UInt64|Počáteční adresa metody|
|MethodSize|Win: UInt32|Velikost metody|
|MethodToken|Win: UInt32|0 pro dynamické metody a pomocníky JIT.|
|MethodFlags|Win: UInt32|0x1: dynamická metoda.<br /><br /> 0x2: obecná metoda.<br /><br /> 0x4: metoda kódu kompilovaná JIT (jinak kód nativní bitové kopie NGEN).<br /><br /> 0x8: pomocná metoda|
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|

## <a name="clr-method-marker-events"></a>Události značky metody CLR

Tyto události jsou vyvolány pouze pod poskytovatelem doběhu. Označují konec výčtu metod během počátečního nebo koncového doběhu. (To znamená, že jsou vyvolány `NGENRundownKeyword` , `JitRundownKeyword` Pokud `LoaderRundownKeyword` `AppDomainResourceManagementRundownKeyword` je povoleno klíčové slovo,, nebo.)

Klíčové slovo a úroveň jsou uvedeny v následující tabulce:

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|`AppDomainResourceManagementRundownKeyword`(0x800) doběhu poskytovatel|Informační (4)|
|`JitRundownKeyword`(0x10) doběhu poskytovatel|Informační (4)|
|`NGENRundownKeyword`(0x20) doběhu poskytovatel|Informační (4)|

Následující tabulka uvádí informace o událostech:

|Událost|ID události|Popis|
|-----------|--------------|----------------|
|`DCStartInit_V1`|147|Odesílá se před začátek výčtu během počáteční doběhuy.|
|`DCStartComplete_V1`|145|Odesílá se na konci výčtu během spouštěcího doběhuu.|
|`DCEndInit_V1`|148|Odesílá se před zahájením výčtu během koncového doběhu.|
|`DCEndComplete_V1`|146|Odesílá se na konci výčtu během koncového doběhu.|

Následující tabulka ukazuje data události:

|Název pole|Datový typ|Popis|
|----------------|---------------|-----------------|
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|

## <a name="clr-method-verbose-events"></a>Podrobná událost metody CLR

Klíčové slovo a úroveň jsou uvedeny v následující tabulce:

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|`JITKeyword`(0x10) modul runtime – poskytovatel|Verbose (5)|
|`NGenKeyword`(0x20) modul runtime – poskytovatel|Verbose (5)|
|`JitRundownKeyword`(0x10) doběhu poskytovatel|Verbose (5)|
|`NGENRundownKeyword`(0x20) doběhu poskytovatel|Verbose (5)|

Následující tabulka uvádí informace o událostech:

|Událost|ID události|Popis|
|-----------|--------------|-----------------|
|`MethodLoadVerbose_V1`|143|Je aktivována, když je metoda načtena JIT nebo je načtena image NGEN. Dynamické a obecné metody vždy používají tuto verzi pro načtení metody. Tato verze vždy používá pomocníky JIT.|
|`MethodUnLoadVerbose_V1`|144|Je aktivována, když je zničena dynamická metoda, modul je uvolněn nebo je odstraněna doména aplikace. Dynamické metody vždy používají tuto verzi pro uvolňování metod.|
|`MethodDCStartVerbose_V1`|141|Vytvoří výčet metod během doběhu spuštění.|
|`MethodDCEndVerbose_V1`|142|Vytvoří výčet metod během koncového doběhu.|

Následující tabulka ukazuje data události:

|Název pole|Datový typ|Popis|
|----------------|---------------|-----------------|
|MethodID|Win: UInt64|Jedinečný identifikátor metody V případě pomocných metod JIT nastavte na počáteční adresu metody.|
|ModuleID|Win: UInt64|Identifikátor modulu, ke kterému patří tato metoda (0 pro pomocníky JIT.)|
|MethodStartAddress|Win: UInt64|Počáteční adresa.|
|MethodSize|Win: UInt32|Délka metody.|
|MethodToken|Win: UInt32|0 pro dynamické metody a pomocníky JIT.|
|MethodFlags|Win: UInt32|0x1: dynamická metoda.<br /><br /> 0x2: obecná metoda.<br /><br /> 0x4: kompilovaná metoda JIT (jinak generovaná NGen.exe)<br /><br /> 0x8: pomocná metoda|
|MethodNameSpace|Win: UnicodeString|Úplný název oboru názvů přidružený k metodě|
|MethodName|Win: UnicodeString|Úplný název třídy přidružený k metodě|
|MethodSignature|Win: UnicodeString|Podpis metody (čárkami oddělený seznam názvů typů)|
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|

## <a name="methodjittingstarted-event"></a>Událost MethodJittingStarted

Klíčové slovo a úroveň jsou uvedeny v následující tabulce:

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|`JITKeyword`(0x10) modul runtime – poskytovatel|Verbose (5)|
|`NGenKeyword`(0x20) modul runtime – poskytovatel|Verbose (5)|
|`JitRundownKeyword`(0x10) doběhu poskytovatel|Verbose (5)|
|`NGENRundownKeyword`(0x20) doběhu poskytovatel|Verbose (5)|

Následující tabulka uvádí informace o událostech:

|Událost|ID události|Popis|
|-----------|--------------|-----------------|
|`MethodJittingStarted`|145|Je aktivována, když je metoda kompilována JIT.|

Následující tabulka ukazuje data události:

|Název pole|Datový typ|Popis|
|----------------|---------------|-----------------|
|MethodID|Win: UInt64|Jedinečný identifikátor metody|
|ModuleID|Win: UInt64|Identifikátor modulu, ke kterému patří tato metoda|
|MethodToken|Win: UInt32|0 pro dynamické metody a pomocníky JIT.|
|MethodILSize|Win: UInt32|Velikost jazyka MSIL (Microsoft Intermediate Language) pro metodu, která je kompilována JIT.|
|MethodNameSpace|Win: UnicodeString|Úplný název třídy přidružený k metodě|
|MethodName|Win: UnicodeString|Název metody|
|MethodSignature|Win: UnicodeString|Podpis metody (čárkami oddělený seznam názvů typů)|
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|

## <a name="see-also"></a>Viz také

- [Události ETW CLR](clr-etw-events.md)
