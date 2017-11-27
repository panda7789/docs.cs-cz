---
title: "Události Trasování událostí pro Windows trasování JIT"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JIT tracing events [.NET Framework]
- ETW, JIT tracing events (CLR)
ms.assetid: 926adde2-c123-452e-bf4f-4b977bf06ffb
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b33a86eb235524ed9cbe5e07dd6625fedf884411
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="jit-tracing-etw-events"></a>Události Trasování událostí pro Windows trasování JIT
<a name="top"></a>Tyto události shromažďovat údaje o úspěch nebo Chyba v běhu (JIT) vložené a volání tail JIT.  
  
 JIT – události trasování se skládají z následujících dvou kategorií:  
  
-   [JIT vložené události](#jit_inlining_events)  
  
-   [JIT – události volání Tail](#jit_tail_call_events)  
  
<a name="jit_inlining_events"></a>   
## <a name="jit-inlining-events"></a>JIT vložené události  
  
### <a name="methodjitinliningfailed-event"></a>MethodJitInliningFailed událostí  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň. (Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`JITTracingKeyword`(0x10)|Verbose (5)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`MethodJitInliningFailed`|186|Vložené JIT se nezdařilo.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|Win: UnicodeString|Namespace metody, která se bude kompilovat.|  
|MethodBeingCompiledName|Win: UnicodeString|Název metody, která se bude kompilovat.|  
|MethodBeingCompiledNameSignature|Win: UnicodeString|Podpis metody, která se bude kompilovat.|  
|InlinerNamespace|Win: UnicodeString|Obor názvů metody kompilátoru za běhu je pokusu o generování kódu pro.|  
|InlinerName|Win: UnicodeString|Název metody kompilátor se pokouší o generování kódu pro. Toto nemusí být stejný jako `MethodBeingCompiledName` Pokud kompilátor se pokouší vloženého kódu do `MethodBeingCompiledName` místo aby generovala volání `InlinerName`.|  
|InlinerNameSignature|Win: UnicodeString|Podpis pro inliner.|  
|InlineeNamespace|Win: UnicodeString|Obor názvů inlinee.|  
|InlineeName|Win: UnicodeString|Metoda kompilátor pokouší vložené (ne generovat volání).|  
|InlineeNameSignature|Win: UnicodeString|Podpis pro inlinee.|  
|FailAlways|Win: logická hodnota|Nápovědu pro to vložené JIT kompilátoru se vždy nepodaří inlinee.|  
|FailReason|Win: UnicodeString|INLINE_NEVER znamená předchozí pokus o vložené určit, že vložené se nikdy úspěšné z jiného důvodu; v opačném případě vlastní text.|  
|ClrInstanceID|Win: UnicodeString|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
### <a name="methodjitinliningsucceeded-event"></a>MethodJitInliningSucceeded událostí  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`JITTracingKeyword`(0x10)|Verbose (5)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`MethodJitInliningSucceeded`|185|Vložené metoda byla úspěšná.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|Win: UnicodeString|Obor názvů metody, která se bude kompilovat.|  
|MethodBeingCompiledName|Win: UnicodeString|Název metody, které se je zkompilovat.|  
|MethodBeingCompiledNameSignature|Win: UnicodeString|Podpis metody, která se bude kompilovat.|  
|InlinerNamespace|Win: UnicodeString|Obor názvů metody do kompilátoru JIT se pokouší o generování kódu pro.|  
|InlinerName|Win: UnicodeString|Název metody kompilátor se pokouší o generování kódu pro. Toto nemusí být stejný jako `MethodBeingCompiledName` Pokud kompilátor se pokouší vloženého kódu do `MethodBeingCompiledName` místo aby generovala volání `InlinerName`.|  
|InlinerNameSignature|Win: UnicodeString|Podpis pro inliner.|  
|InlineeNamespace|Win: UnicodeString|Obor názvů inlinee.|  
|InlineeName|Win: UnicodeString|Metoda kompilátor pokouší vložené (ne generovat volání).|  
|InlineeNameSignature|Win: UnicodeString|Podpis pro inlinee.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="jit_tail_call_events"></a>   
## <a name="jit-tail-call-events"></a>JIT – události volání Tail  
  
### <a name="methodjittailcallfailed-event"></a>MethodJITTailCallFailed událostí  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`JITTracingKeyword`(0x10)|Verbose (5)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`MethodJitTailCallFailed`|189|Volání metody, které poškozené databáze se nezdařilo.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|Win: UnicodeString|Namespace metody, která se bude kompilovat.|  
|MethodBeingCompiledName|Win: UnicodeString|Název metody, která se bude kompilovat.|  
|MethodBeingCompiledNameSignature|Win: UnicodeString|Podpis metody, která se bude kompilovat.|  
|CallerNamespace|Win: UnicodeString|Obor názvů metody do kompilátoru JIT se pokouší o generování kódu pro.|  
|CallerName|Win: UnicodeString|Název metody kompilátor se pokouší o generování kódu pro.|  
|CallerNameSignature|Win: UnicodeString|Podpis pro volajícího.|  
|CalleeNamespace|Win: UnicodeString|Obor názvů volaného.|  
|CalleeName|Win: UnicodeString|Metoda kompilátor se pokouší o volání tail (ne generovat volání).|  
|CalleeNameSignature|Win: UnicodeString|Podpis pro volaného.|  
|TailPrefix|Win: logická hodnota|Předpona pro volání funkce tail|  
|FailReason|Win: UnicodeString|Důvod volání funkce tail se nezdařilo.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
### <a name="methodjittailcallsucceeded-event"></a>MethodJITTailCallSucceeded událostí  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`JITTracingKeyword`(0x10)|Verbose (5)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`MethodJitTailCallSucceeded`|188|Volání funkce tail metoda byla úspěšná.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|Win: UnicodeString|Namespace metody, která se bude kompilovat.|  
|MethodBeingCompiledName|Win: UnicodeString|Název metody, která se bude kompilovat.|  
|MethodBeingCompiledNameSignature|Win: UnicodeString|Podpis metody, která se bude kompilovat.|  
|CallerNamespace|Win: UnicodeString|Obor názvů metody do kompilátoru JIT se pokouší o generování kódu pro.|  
|CallerName|Win: UnicodeString|Název metody kompilátor se pokouší o generování kódu pro.|  
|CallerNameSignature|Win: UnicodeString|Podpis pro volajícího.|  
|CalleeNamespace|Win: UnicodeString|Obor názvů volaného.|  
|CalleeName|Win: UnicodeString|Metoda kompilátor se pokouší o volání tail (ne generovat volání).|  
|CalleeNameSignature|Win: UnicodeString|Podpis pro volaného.|  
|TailPrefix|Win: logická hodnota|Předpona pro volání funkce tail.|  
|TailCallType|Win: UnicodeString|Druh volání funkce tail.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
## <a name="see-also"></a>Viz také  
 [CLR ETW – události](../../../docs/framework/performance/clr-etw-events.md)
