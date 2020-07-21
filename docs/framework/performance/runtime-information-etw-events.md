---
title: Události Trasování událostí pro Windows běhových informací
description: Viz události trasování událostí pro Windows za běhu, které zaznamenávají SKLADOVOU položku, číslo verze, způsob aktivace modulu runtime (včetně parametrů příkazového řádku), identifikátor GUID a další.
ms.date: 03/30/2017
helpviewer_keywords:
- runtime information events [.NET Framework]
- ETW, runtime information events
ms.assetid: 68b4edbc-7f3b-45f6-ab75-4fd066d6af9a
ms.openlocfilehash: 385519229bdb76841cdf592d95e96d2288ec5e1a
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474225"
---
# <a name="runtime-information-etw-events"></a>Události Trasování událostí pro Windows běhových informací
Tyto události ETW protokolují informace o modulu runtime, včetně SKU, čísla verze, způsobu, jakým byl aktivován modul runtime, parametry příkazového řádku, s nimiž byl spuštěn, identifikátor GUID (Pokud je k dispozici) a další relevantní informace. Pokud je v rámci procesu spuštěno více modulů runtime, pomáhají informace poskytované těmito událostmi (ClrInstanceID) k odstranění nejednoznačnosti modulu runtime.  
  
 Následující tabulka uvádí dvě běhové informační události. Události lze vyvolat v jakémkoli klíčovém slově nebo masce. (Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).)  
  
|Událost|ID události|Poskytovatel|Popis|  
|-----------|--------------|--------------|-----------------|  
|`RuntimeInformationEvent`|187|CLRRuntime|Vyvolá se při načtení modulu runtime.|  
|`RuntimeInformationDCStart`|187|CLRRundown|Vytvoří výčet načtených modulů runtime.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
|Skladová jednotka (SKU)|Win: UInt16|1 – CLR pro stolní počítače.<br /><br /> 2 – CoreCLR.|  
|BclVersion – hlavní verze|Win: UInt16|Hlavní verze mscorlib.dll.|  
|BclVersion – dílčí verze|Win: UInt16|Číslo dílčí verze mscorlib.dll.|  
|BclVersion – číslo buildu|Win: UInt16|Číslo buildu mscorlib.dll.|  
|BclVersion – QFE|Win: UInt16|Číslo verze opravy hotfix mscorlib.dll.|  
|VMVersion – hlavní verze|Win: UInt16|Verze clr.dll nebo coreclr.dll v závislosti na SKU.|  
|VMVersion – dílčí verze|Win: UInt16|Dílčí verze clr.dll nebo coreclr.dll v závislosti na SKU|  
|VMVersion – číslo buildu|Win: UInt16|Číslo buildu clr.dll nebo coreclr.dll.|  
|VMVersion – QFE|Win: UInt16|Číslo verze opravy hotfix clr.dll nebo coreclr.dll.|  
|StartupFlags|Win: UInt32|Příznaky spouštění definované v knihovně Mscoree. h.|  
|StartupMode|Win: UInt8|spustitelný soubor spravovaný za 0x01<br /><br /> 0x02 – hostovaný modul CLR.<br /><br /> spravované spolupráci 0x04-C++.<br /><br /> 0x08-COM-aktivované.<br /><br /> 0x10 – jiné.|  
|CommandLine|Win: UnicodeString|Hodnota jinou než null, pouze pokud StartupMode = 0x01.|  
|ComObjectGUID|Win: GUID|Hodnota jinou než null, pouze pokud StartupMode = 0x08.|  
|RuntimeDLLPath|Win: UnicodeString|Cesta k souboru CLR. dll, který byl načten do procesu.|  
  
## <a name="see-also"></a>Viz také

- [Události ETW CLR](clr-etw-events.md)
