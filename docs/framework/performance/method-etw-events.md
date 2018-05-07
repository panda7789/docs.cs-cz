---
title: Události Trasování událostí pro Windows metod
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, method events (CLR)
- method events [.NET Framework]
ms.assetid: 167a4459-bb6e-476c-9046-7920880f2bb5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 578aed02d5d44ae94763b6a254420a4976320f13
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="method-etw-events"></a>Události Trasování událostí pro Windows metod
<a name="top"></a> Tyto události shromažďovat informace, které jsou specifické pro metody. Datová část tyto události je vyžadována pro symbol řešení. Kromě toho tyto události poskytují užitečné informace, jako je počet pokusů, že byla volána metoda.  
  
 Všechny události metoda mají úroveň "Informační (4)". Všechny události podrobné metoda mít úrovní "Verbose (5)".  
  
 Všechny události metod jsou vydané `JITKeyword` – klíčové slovo (0x10) nebo `NGenKeyword` – klíčové slovo (0x20) v rámci zprostředkovatele runtime, nebo `JitRundownKeyword` (0x10) nebo `NGENRundownKeyword` (0x20) v rámci sekvence daneho zprostředkovatele.  
  
 Události metod CLR dále dělí na následující:  
  
-   [Události metod CLR](#clr_method_events)  
  
-   [CLR – metoda značky události](#clr_method_marker_events)  
  
-   [Podrobné události CLR – metoda](#clr_method_verbose_events)  
  
-   [MethodJittingStarted událostí](#methodjittingstarted_event)  
  
<a name="clr_method_events"></a>   
## <a name="clr-method-events"></a>Události metod CLR  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň. (Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`JITKeyword` Poskytovatel modulu runtime (0x10)|Informativní (4)|  
|`NGenKeyword` Poskytovatel modulu runtime (0x20)|Informativní (4)|  
|`JitRundownKeyword` sekvence daneho zprostředkovatele (0x10)|Informativní (4)|  
|`NGENRundownKeyword` sekvence daneho zprostředkovatele (0x20)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`MethodLoad_V1`|136|Vyvolá, když metoda je v běhu načíst (JIT načíst) nebo bitovou kopii NGEN je načtena. Dynamické a obecné metody pro zatížení metoda nepoužívejte tuto verzi. Pomocníci JIT nikdy nepoužívejte tuto verzi.|  
|`MethodUnLoad_V1`|137|Vyvolá, když modul je odpojen nebo zničena domény aplikace. Dynamické metody pro metoda uvolní nikdy nepoužívejte tuto verzi.|  
|`MethodDCStart_V1`|137|Vytvoří výčet metody během spuštění rundown.|  
|`MethodDCEnd_V1`|138|Vytvoří výčet metod během rundown end.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|MethodID|Win: UInt64|Jedinečný identifikátor metody. Pro JIT pomocné metody je nastavena na adresu spuštění metody.|  
|ID modulu|Win: UInt64|Identifikátor modulu, do které patří tato metoda (0 = Pomocníci JIT).|  
|MethodStartAddress|Win: UInt64|Počáteční adresa metody.|  
|MethodSize|Win: UInt32|Velikost metody.|  
|MethodToken|Win: UInt32|0 pro dynamických metod a JIT pomocné rutiny.|  
|MethodFlags|Win: UInt32|0x1: dynamické metoda.<br /><br /> 0x2: Obecné metody.<br /><br /> 0x4: kompilována code – metoda (jinak NGEN nativních bitových kopií kód).<br /><br /> 0x8: Pomocná metoda.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="clr_method_marker_events"></a>   
## <a name="clr-method-marker-events"></a>CLR – metoda značky události  
 Tyto události jsou vyvolány pouze v rámci sekvence daneho zprostředkovatele. Jsou označují konec metoda výčtu při spuštění nebo ukončení rundown. (To znamená, že jsou vyvolány při `NGENRundownKeyword`, `JitRundownKeyword`, `LoaderRundownKeyword`, nebo `AppDomainResourceManagementRundownKeyword` – klíčové slovo je povolená.)  
  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementRundownKeyword` sekvence daneho zprostředkovatele (0x800)|Informativní (4)|  
|`JitRundownKeyword` sekvence daneho zprostředkovatele (0x10)|Informativní (4)|  
|`NGENRundownKeyword` sekvence daneho zprostředkovatele (0x20)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|----------------|  
|`DCStartInit_V1`|147|Odesílat před začátek výčtu během spuštění rundown.|  
|`DCStartComplete_V1`|145|Odeslat na konci výčtu během spuštění rundown.|  
|`DCEndInit_V1`|148|Odesílat před začátek výčtu během rundown end.|  
|`DCEndComplete_V1`|146|Odeslat na konci výčtu během rundown end.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="clr_method_verbose_events"></a>   
## <a name="clr-method-verbose-events"></a>Podrobné události CLR – metoda  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`JITKeyword` Poskytovatel modulu runtime (0x10)|Verbose (5)|  
|`NGenKeyword` Poskytovatel modulu runtime (0x20)|Verbose (5)|  
|`JitRundownKeyword` sekvence daneho zprostředkovatele (0x10)|Verbose (5)|  
|`NGENRundownKeyword` sekvence daneho zprostředkovatele (0x20)|Verbose (5)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`MethodLoadVerbose_V1`|143|Vyvolá, když je metoda JIT načíst nebo bitovou kopii NGEN je načtena. Dynamické a obecné metody vždy v této verzi metoda zatížení. Pomocníci JIT vždy používají tuto verzi.|  
|`MethodUnLoadVerbose_V1`|144|Vyvolá, když je zničen dynamické metody, modul je odpojen nebo zničena domény aplikace. Dynamické metody vždy v této verzi metoda uvolní.|  
|`MethodDCStartVerbose_V1`|141|Vytvoří výčet metody během spuštění rundown.|  
|`MethodDCEndVerbose_V1`|142|Vytvoří výčet metod během rundown end.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|MethodID|Win: UInt64|Jedinečný identifikátor metody. U metody helper JIT nastavte počáteční adresa metody.|  
|ID modulu|Win: UInt64|Identifikátor modulu, do které patří tato metoda (0 = Pomocníci JIT).|  
|MethodStartAddress|Win: UInt64|Počáteční adresa.|  
|MethodSize|Win: UInt32|Metoda délka.|  
|MethodToken|Win: UInt32|0 pro dynamických metod a JIT pomocné rutiny.|  
|MethodFlags|Win: UInt32|0x1: dynamické metoda.<br /><br /> 0x2: Obecné metody.<br /><br /> 0x4: metoda kompilována (jinak, generovaný nástrojem NGen.exe)<br /><br /> 0x8: Pomocná metoda.|  
|MethodNameSpace|Win: UnicodeString|Název úplné oboru názvů přidružené k metodě.|  
|MethodName|Win: UnicodeString|Název úplné třídy přidružené k metodě.|  
|MethodSignature|Win: UnicodeString|Podpis metody (čárkami oddělený seznam názvů typu).|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="methodjittingstarted_event"></a>   
## <a name="methodjittingstarted-event"></a>MethodJittingStarted událostí  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`JITKeyword` Poskytovatel modulu runtime (0x10)|Verbose (5)|  
|`NGenKeyword` Poskytovatel modulu runtime (0x20)|Verbose (5)|  
|`JitRundownKeyword` sekvence daneho zprostředkovatele (0x10)|Verbose (5)|  
|`NGENRundownKeyword` sekvence daneho zprostředkovatele (0x20)|Verbose (5)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`MethodJittingStarted`|145|Vyvolá, když metoda, která má být kompilována.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|MethodID|Win: UInt64|Jedinečný identifikátor metody.|  
|ID modulu|Win: UInt64|Identifikátor modulu, do které patří tato metoda.|  
|MethodToken|Win: UInt32|0 pro dynamických metod a JIT pomocné rutiny.|  
|MethodILSize|Win: UInt32|Velikost Microsoft (MSIL intermediate language) pro metodu, která se kompilována.|  
|MethodNameSpace|Win: UnicodeString|Název úplné třídy přidružené k metodě.|  
|MethodName|Win: UnicodeString|Název metody.|  
|MethodSignature|Win: UnicodeString|Podpis metody (čárkami oddělený seznam názvů typu).|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
## <a name="see-also"></a>Viz také  
 [Události Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-events.md)
