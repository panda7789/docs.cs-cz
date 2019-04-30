---
title: Události Trasování událostí pro Windows metod
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, method events (CLR)
- method events [.NET Framework]
ms.assetid: 167a4459-bb6e-476c-9046-7920880f2bb5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c7969c0a3f5f828f1a1c0d4f33b82881130c6e15
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949250"
---
# <a name="method-etw-events"></a>Události Trasování událostí pro Windows metod

<a name="top"></a> Tyto události shromažďovat informace, které jsou specifické pro metody. Datová část tyto události se vyžaduje pro rozlišení symbolů. Kromě toho tyto události poskytují užitečné informace, jako je například počet, kolikrát, že byla volána metoda.

Všechny události metod úroveň "Informační (4)". Všechny události podrobné metoda úroveň "Verbose (5)".

Všechny metody události jsou vyvolány `JITKeyword` – klíčové slovo (0x10) nebo `NGenKeyword` – klíčové slovo (0x20) v části zprostředkovatel běhového prostředí, nebo `JitRundownKeyword` (0x10) nebo `NGENRundownKeyword` (0x20) skrze zprostředkovatele doběhu.

Události metod modulu CLR je dále rozdělená na následující:

- [Události CLR – metoda](#clr_method_events)

- [CLR – metoda značky události](#clr_method_marker_events)

- [Podrobné události CLR – metoda](#clr_method_verbose_events)

- [MethodJittingStarted události](#methodjittingstarted_event)

<a name="clr_method_events"></a>

## <a name="clr-method-events"></a>Události CLR – metoda

V následující tabulce jsou uvedeny klíčové slovo a úroveň. (Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)

|Klíčové slovo pro vyvolání události|úroveň|
|-----------------------------------|-----------|
|`JITKeyword` Zprostředkovatel běhového prostředí (0x10)|Informativní (4)|
|`NGenKeyword` Zprostředkovatel běhového prostředí (0x20)|Informativní (4)|
|`JitRundownKeyword` Zprostředkovatel doběhu (0x10)|Informativní (4)|
|`NGENRundownKeyword` Zprostředkovatel doběhu (0x20)|Informativní (4)|

V následující tabulce jsou uvedeny informace o události.

|Událost|ID události|Popis|
|-----------|--------------|-----------------|
|`MethodLoad_V1`|136|Vyvolá, když metoda je just-in-time načíst (za běhu načíst) nebo načíst NGEN image. Dynamické a obecné metody nepoužívejte tuto verzi metoda zatížení. Pomocné rutiny JIT nikdy nepoužívejte tuto verzi.|
|`MethodUnLoad_V1`|137|Vyvoláno, když modul je odpojen nebo je zničen domény aplikace. Tuto verzi dynamické metody nikdy použít pro metodu uvolní.|
|`MethodDCStart_V1`|137|Podává výčet metod během začátek doběhu.|
|`MethodDCEnd_V1`|138|Podává výčet metod během konec doběhu.|

Následující tabulka zobrazuje data událostí.

|Název pole|Datový typ|Popis|
|----------------|---------------|-----------------|
|MethodID|win:UInt64|Jedinečný identifikátor metody. Pro metody helper JIT je nastavena na počáteční adresu metody.|
|ID modulu|win:UInt64|Identifikátor modulu, ke kterému patří tato metoda (0 pro pomocné rutiny JIT).|
|MethodStartAddress|win:UInt64|Počáteční adresa metody.|
|MethodSize|win:UInt32|Velikost metody.|
|MethodToken|win:UInt32|0 pro dynamických metod a JIT pomocné rutiny.|
|MethodFlags|win:UInt32|0x1: Dynamická metoda.<br /><br /> 0x2: Obecné metody.<br /><br /> 0x4: Metoda kód zkompilovaný kompilátorem JIT (jinak NGEN nativních bitových kopií kód).<br /><br /> 0x8: Pomocná metoda.|
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|

[Zpět na začátek](#top)

<a name="clr_method_marker_events"></a>

## <a name="clr-method-marker-events"></a>CLR – metoda značky události

Tyto události jsou vyvolány pouze skrze zprostředkovatele doběhu. Jsou místo na konec metody výčet při spuštění nebo ukončení doběhu. (To znamená, že jsou generovány při `NGENRundownKeyword`, `JitRundownKeyword`, `LoaderRundownKeyword`, nebo `AppDomainResourceManagementRundownKeyword` – klíčové slovo je povolená.)

V následující tabulce jsou uvedeny klíčové slovo a úroveň.

|Klíčové slovo pro vyvolání události|úroveň|
|-----------------------------------|-----------|
|`AppDomainResourceManagementRundownKeyword` Zprostředkovatel doběhu (0x800)|Informativní (4)|
|`JitRundownKeyword` Zprostředkovatel doběhu (0x10)|Informativní (4)|
|`NGENRundownKeyword` Zprostředkovatel doběhu (0x20)|Informativní (4)|

V následující tabulce jsou uvedeny informace o události.

|Událost|ID události|Popis|
|-----------|--------------|----------------|
|`DCStartInit_V1`|147|Před zahájením výčtu během začátek doběhu odeslány.|
|`DCStartComplete_V1`|145|Odeslání na konci výčtu během začátek doběhu.|
|`DCEndInit_V1`|148|Před zahájením výčtu během konec doběhu odeslány.|
|`DCEndComplete_V1`|146|Odeslání na konci výčtu během konec doběhu.|

Následující tabulka zobrazuje data událostí.

|Název pole|Datový typ|Popis|
|----------------|---------------|-----------------|
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|

[Zpět na začátek](#top)

<a name="clr_method_verbose_events"></a>

## <a name="clr-method-verbose-events"></a>Podrobné události CLR – metoda

V následující tabulce jsou uvedeny klíčové slovo a úroveň.

|Klíčové slovo pro vyvolání události|úroveň|
|-----------------------------------|-----------|
|`JITKeyword` Zprostředkovatel běhového prostředí (0x10)|Verbose (5)|
|`NGenKeyword` Zprostředkovatel běhového prostředí (0x20)|Verbose (5)|
|`JitRundownKeyword` Zprostředkovatel doběhu (0x10)|Verbose (5)|
|`NGENRundownKeyword` Zprostředkovatel doběhu (0x20)|Verbose (5)|

V následující tabulce jsou uvedeny informace o události.

|Událost|ID události|Popis|
|-----------|--------------|-----------------|
|`MethodLoadVerbose_V1`|143|Vyvoláno, když je metoda JIT načíst nebo načíst NGEN image. Tuto verzi dynamické a obecné metody vždy použít pro metodu načtení. Pomocné rutiny JIT vždy pomocí této verze.|
|`MethodUnLoadVerbose_V1`|144|Vyvolána, když je zničen dynamickou metodu, modul je odpojen nebo je zničen domény aplikace. Tuto verzi dynamické metody vždy použít pro metodu uvolní.|
|`MethodDCStartVerbose_V1`|141|Podává výčet metod během začátek doběhu.|
|`MethodDCEndVerbose_V1`|142|Podává výčet metod během konec doběhu.|

Následující tabulka zobrazuje data událostí.

|Název pole|Datový typ|Popis|
|----------------|---------------|-----------------|
|MethodID|win:UInt64|Jedinečný identifikátor metody. Pro metody helper JIT nastavte počáteční adresa metody.|
|ID modulu|win:UInt64|Identifikátor modulu, ke kterému patří tato metoda (0 pro pomocné rutiny JIT).|
|MethodStartAddress|win:UInt64|Počáteční adresa.|
|MethodSize|win:UInt32|Metoda délku.|
|MethodToken|win:UInt32|0 pro dynamických metod a JIT pomocné rutiny.|
|MethodFlags|win:UInt32|0x1: Dynamická metoda.<br /><br /> 0x2: Obecné metody.<br /><br /> 0x4: Metody zkompilované JIT (jinak, vygenerované pomocí NGen.exe)<br /><br /> 0x8: Pomocná metoda.|
|MethodNameSpace|win:UnicodeString|Obor názvů úplný název přidružený k metodu.|
|methodName|win:UnicodeString|Úplný název třídy přidružené k metodě.|
|MethodSignature|win:UnicodeString|Podpis metody (čárkou oddělený seznam názvů typů).|
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|

[Zpět na začátek](#top)

<a name="methodjittingstarted_event"></a>

## <a name="methodjittingstarted-event"></a>MethodJittingStarted události

V následující tabulce jsou uvedeny klíčové slovo a úroveň.

|Klíčové slovo pro vyvolání události|úroveň|
|-----------------------------------|-----------|
|`JITKeyword` Zprostředkovatel běhového prostředí (0x10)|Verbose (5)|
|`NGenKeyword` Zprostředkovatel běhového prostředí (0x20)|Verbose (5)|
|`JitRundownKeyword` Zprostředkovatel doběhu (0x10)|Verbose (5)|
|`NGENRundownKeyword` Zprostředkovatel doběhu (0x20)|Verbose (5)|

V následující tabulce jsou uvedeny informace o události.

|Událost|ID události|Popis|
|-----------|--------------|-----------------|
|`MethodJittingStarted`|145|Vyvoláno, když metoda, která má být zkompilovaný kompilátorem JIT.|

Následující tabulka zobrazuje data událostí.

|Název pole|Datový typ|Popis|
|----------------|---------------|-----------------|
|MethodID|win:UInt64|Jedinečný identifikátor metody.|
|ID modulu|win:UInt64|Identifikátor modulu, ke kterému patří tato metoda.|
|MethodToken|win:UInt32|0 pro dynamických metod a JIT pomocné rutiny.|
|MethodILSize|win:UInt32|Velikost Microsoft intermediate language (MSIL) pro metodu, která je právě zkompilovaný kompilátorem JIT.|
|MethodNameSpace|win:UnicodeString|Úplný název třídy přidružené k metodě.|
|methodName|win:UnicodeString|Název metody.|
|MethodSignature|win:UnicodeString|Podpis metody (čárkou oddělený seznam názvů typů).|
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|

## <a name="see-also"></a>Viz také:

- [Události Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-events.md)
