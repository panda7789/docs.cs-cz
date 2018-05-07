---
title: Události Trasování událostí pro Windows běhových informací
ms.date: 03/30/2017
helpviewer_keywords:
- runtime information events [.NET Framework]
- ETW, runtime information events
ms.assetid: 68b4edbc-7f3b-45f6-ab75-4fd066d6af9a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4244196a957c67a807cdb705f6d74ee2b41869d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="runtime-information-etw-events"></a>Události Trasování událostí pro Windows běhových informací
Informace o modulu runtime, SKU, číslo verze, způsobem, ve kterém byla aktivovaná modul runtime, včetně parametrů příkazového řádku, který byl spuštěn s, identifikátor GUID (pokud existuje) a další relevantní informace protokolu tyto události trasování událostí pro Windows. Pokud jsou v rámci procesu spouštění více moduly runtime informace poskytované tyto události (ClrInstanceID) pomáhá rozlišení moduly runtime.  
  
 V následující tabulce jsou uvedeny dvě události běhových informací. Události může být vyvolána v rámci žádného – klíčové slovo či masky. (Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Událost|ID události|Zprostředkovatel|Popis|  
|-----------|--------------|--------------|-----------------|  
|`RuntimeInformationEvent`|187|CLRRuntime|Vyvolá, když je načten modulu runtime.|  
|`RuntimeInformationDCStart`|187|CLRRundown|Vytvoří výčet moduly runtime, která jsou načtena.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
|SKU|Win: UInt16|1 – plocha CLR.<br /><br /> 2 – CoreCLR.|  
|BclVersion – hlavní verze|Win: UInt16|Hlavní verze mscorlib.dll.|  
|BclVersion – podverze|Win: UInt16|Číslo podverze mscorlib.dll.|  
|BclVersion – číslo sestavení|Win: UInt16|Číslo mscorlib.dll sestavení.|  
|BclVersion – oprava QFE|Win: UInt16|Oprava hotfix číslo verze mscorlib.dll.|  
|VMVersion – hlavní verze|Win: UInt16|Verze clr.dll nebo coreclr.dll, v závislosti na SKU.|  
|VMVersion – podverze|Win: UInt16|Podverze clr.dll nebo coreclr.dll, v závislosti na SKU.|  
|VMVersion – číslo sestavení|Win: UInt16|Číslo clr.dll nebo coreclr.dll sestavení.|  
|VMVersion – oprava QFE|Win: UInt16|Oprava hotfix číslo verze clr.dll nebo coreclr.dll.|  
|StartupFlags|Win: UInt32|Spuštění příznaky definované v mscoree.h.|  
|StartupMode|Win: UInt8|0x01 – spravované spustitelný soubor.<br /><br /> 0x02 - hostované CLR.<br /><br /> 0x04 - C++ managed zprostředkovatel komunikace s objekty.<br /><br /> 0x08 - COM aktivován.<br /><br /> 0x10 - Další.|  
|příkazového řádku|Win: UnicodeString|Nesmí být nulová pouze v případě StartupMode = 0x01.|  
|ComObjectGUID|Win: GUID|Nesmí být nulová pouze v případě StartupMode = 0x08.|  
|RuntimeDLLPath|Win: UnicodeString|Cesta k souboru .dll CLR, který byl načten do procesu.|  
  
## <a name="see-also"></a>Viz také  
 [Události Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-events.md)
