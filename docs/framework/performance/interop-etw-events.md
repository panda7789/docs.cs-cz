---
title: "Události Trasování událostí pro Windows interoperability"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5670eb910406626096f776d3b4192e2d58d7ce1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="interop-etw-events"></a>Události Trasování událostí pro Windows interoperability
<a name="top"></a>Události interoperability zaznamenat informace o Microsoft (MSIL intermediate language) se zakázaným inzerováním generování a ukládání do mezipaměti.  
  
 Tato kategorie se skládá z následujících událostí:  
  
-   [ILStubGenerated událostí](#ilstubgenerated_event)  
  
-   [ILStubCacheHit událostí](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a>ILStubGenerated událostí  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň. (Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`InteropKeyword`(0x2000)|Informational(4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|88|MSIL stub byla vygenerována.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ID modulu|Win: UInt16|Identifikátor modulu.|  
|StubMethodID|Win: UInt64|Identifikátor se zakázaným inzerováním metoda.|  
|StubFlags|Win: UInt64|Příznaky pro testovací kód:<br /><br /> 0x1 - zpětné zprostředkovatel komunikace s objekty.<br /><br /> 0x2 - zprostředkovatel komunikace s objekty COM.<br /><br /> 0x4 - stub generované NGen.exe.<br /><br /> 0x8 - delegáta.<br /><br /> 0x10 - proměnné arrgument.<br /><br /> 0x20 – nespravované volaný.|  
|ManagedInteropMethodToken|Win: UInt32|Token pro metodu spravovaného zprostředkovatele komunikace s objekty.|  
|ManagedInteropMethodNameSpace|Win: UnicodeString|Obor názvů metodu spravovaného zprostředkovatele komunikace s objekty.|  
|ManagedInteropMethodName|Win: UnicodeString|Název spravovaného zprostředkovatele komunikace s objekty metody.|  
|ManagedInteropMethodSignature|Win: UnicodeString|Podpis spravované spolupráce metody.|  
|NativeMethodSignature|Win: UnicodeString|Nativní metoda podpis.|  
|StubMethodSignature|Win: UnicodeString|Podpis metody se zakázaným inzerováním.|  
|StubMethodILCode|Win: UnicodeString|MSIL kód pro metodu se zakázaným inzerováním.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a>ILStubCacheHit událostí  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`InteropKeyword`(0x2000)|Informational(4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|89|Přistupoval MSIL mezipaměti.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ID modulu|Win: UInt16|Identifikátor modulu.|  
|StubMethodID|Win: UInt64|Identifikátor se zakázaným inzerováním metoda.|  
|ManagedInteropMethodToken|Win: UInt32|Token pro metodu spravovaného zprostředkovatele komunikace s objekty.|  
|ManagedInteropMethodNameSpace|Win: UnicodeString|Obor názvů metodu spravovaného zprostředkovatele komunikace s objekty.|  
|ManagedInteropMethodName|Win: UnicodeString|Název spravovaného zprostředkovatele komunikace s objekty metody.|  
|ManagedInteropMethodSignature|Win: UnicodeString|Podpis spravované spolupráce metody.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
## <a name="see-also"></a>Viz také  
 [Události Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-events.md)
