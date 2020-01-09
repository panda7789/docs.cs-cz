---
title: Události Trasování událostí pro Windows metod
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, method events (CLR)
- method events [.NET Framework]
ms.assetid: 167a4459-bb6e-476c-9046-7920880f2bb5
ms.openlocfilehash: 4937afe8bb23be58b72d082cd5ba200b4948ab4d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715985"
---
# <a name="method-etw-events"></a>Události Trasování událostí pro Windows metod

Tyto události shromažďují informace, které jsou specifické pro metody. Datová část těchto událostí je požadována pro rozlišení symbolu. Kromě toho tyto události poskytují užitečné informace, jako je počet volání metody.

Všechny události metody mají úroveň "informativní" (4). Všechny podrobné události metody mají úroveň verbose (5).

Všechny události metody jsou vyvolány klíčovým slovem `JITKeyword` (0x10) nebo klíčovým slovem `NGenKeyword` (0x20) pod poskytovatelem modulu runtime, nebo `JitRundownKeyword` (0x10) nebo `NGENRundownKeyword` (0x20) pod poskytovatelem doběhu.

## <a name="clr-method-events"></a>Události metody CLR

Klíčové slovo a úroveň jsou uvedeny v následující tabulce. Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|Zprostředkovatel běhového prostředí `JITKeyword` (0x10)|Informační (4)|
|Zprostředkovatel běhového prostředí `NGenKeyword` (0x20)|Informační (4)|
|poskytovatel doběhu `JitRundownKeyword` (0x10)|Informační (4)|
|poskytovatel doběhu `NGENRundownKeyword` (0x20)|Informační (4)|

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
|MethodID|win:UInt64|Jedinečný identifikátor metody V případě pomocných metod JIT je tato metoda nastavena na počáteční adresu metody.|
|ModuleID|win:UInt64|Identifikátor modulu, ke kterému patří tato metoda (0 pro pomocníky JIT.)|
|MethodStartAddress|win:UInt64|Počáteční adresa metody|
|MethodSize|Win: UInt32|Velikost metody|
|MethodToken|Win: UInt32|0 pro dynamické metody a pomocníky JIT.|
|MethodFlags|Win: UInt32|0x1: dynamická metoda.<br /><br /> 0x2: obecná metoda.<br /><br /> 0x4: metoda kódu kompilovaná JIT (jinak kód nativní bitové kopie NGEN).<br /><br /> 0x8: pomocná metoda|
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|

## <a name="clr-method-marker-events"></a>Události značky metody CLR

Tyto události jsou vyvolány pouze pod poskytovatelem doběhu. Označují konec výčtu metod během počátečního nebo koncového doběhu. (To znamená, že jsou vyvolány, pokud je povoleno klíčové slovo `NGENRundownKeyword`, `JitRundownKeyword`, `LoaderRundownKeyword`nebo `AppDomainResourceManagementRundownKeyword`.)

Klíčové slovo a úroveň jsou uvedeny v následující tabulce:

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|poskytovatel doběhu `AppDomainResourceManagementRundownKeyword` (0x800)|Informační (4)|
|poskytovatel doběhu `JitRundownKeyword` (0x10)|Informační (4)|
|poskytovatel doběhu `NGENRundownKeyword` (0x20)|Informační (4)|

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
|Zprostředkovatel běhového prostředí `JITKeyword` (0x10)|Verbose (5)|
|Zprostředkovatel běhového prostředí `NGenKeyword` (0x20)|Verbose (5)|
|poskytovatel doběhu `JitRundownKeyword` (0x10)|Verbose (5)|
|poskytovatel doběhu `NGENRundownKeyword` (0x20)|Verbose (5)|

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
|MethodID|win:UInt64|Jedinečný identifikátor metody V případě pomocných metod JIT nastavte na počáteční adresu metody.|
|ModuleID|win:UInt64|Identifikátor modulu, ke kterému patří tato metoda (0 pro pomocníky JIT.)|
|MethodStartAddress|win:UInt64|Počáteční adresa.|
|MethodSize|Win: UInt32|Délka metody.|
|MethodToken|Win: UInt32|0 pro dynamické metody a pomocníky JIT.|
|MethodFlags|Win: UInt32|0x1: dynamická metoda.<br /><br /> 0x2: obecná metoda.<br /><br /> 0x4: kompilovaná metoda JIT (jinak generovaná pomocí NGen. exe)<br /><br /> 0x8: pomocná metoda|
|MethodNameSpace|win:UnicodeString|Úplný název oboru názvů přidružený k metodě|
|MethodName|win:UnicodeString|Úplný název třídy přidružený k metodě|
|MethodSignature|win:UnicodeString|Podpis metody (čárkami oddělený seznam názvů typů)|
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|

## <a name="methodjittingstarted-event"></a>Událost MethodJittingStarted

Klíčové slovo a úroveň jsou uvedeny v následující tabulce:

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|Zprostředkovatel běhového prostředí `JITKeyword` (0x10)|Verbose (5)|
|Zprostředkovatel běhového prostředí `NGenKeyword` (0x20)|Verbose (5)|
|poskytovatel doběhu `JitRundownKeyword` (0x10)|Verbose (5)|
|poskytovatel doběhu `NGENRundownKeyword` (0x20)|Verbose (5)|

Následující tabulka uvádí informace o událostech:

|Událost|ID události|Popis|
|-----------|--------------|-----------------|
|`MethodJittingStarted`|145|Je aktivována, když je metoda kompilována JIT.|

Následující tabulka ukazuje data události:

|Název pole|Datový typ|Popis|
|----------------|---------------|-----------------|
|MethodID|win:UInt64|Jedinečný identifikátor metody|
|ModuleID|win:UInt64|Identifikátor modulu, ke kterému patří tato metoda|
|MethodToken|Win: UInt32|0 pro dynamické metody a pomocníky JIT.|
|MethodILSize|Win: UInt32|Velikost jazyka MSIL (Microsoft Intermediate Language) pro metodu, která je kompilována JIT.|
|MethodNameSpace|win:UnicodeString|Úplný název třídy přidružený k metodě|
|MethodName|win:UnicodeString|Název metody.|
|MethodSignature|win:UnicodeString|Podpis metody (čárkami oddělený seznam názvů typů)|
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|

## <a name="see-also"></a>Viz také:

- [Události Trasování událostí pro Windows v CLR](clr-etw-events.md)
