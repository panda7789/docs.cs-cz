---
title: Události Trasování událostí pro Windows trasování JIT
ms.date: 03/30/2017
helpviewer_keywords:
- JIT tracing events [.NET Framework]
- ETW, JIT tracing events (CLR)
ms.assetid: 926adde2-c123-452e-bf4f-4b977bf06ffb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7261e5ce06a4ac20b1e7c816ababf8c8ba129b29
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949276"
---
# <a name="jit-tracing-etw-events"></a>Události Trasování událostí pro Windows trasování JIT
<a name="top"></a> Tyto události shromažďování informací týkajících se úspěchu nebo neúspěchu just-in-time (JIT) vkládání a volání funkce tail JIT.  
  
 JIT – události trasování se skládají z těchto dvou kategorií:  
  
- [JIT vkládání události](#jit_inlining_events)  
  
- [JIT – události volání funkce Tail](#jit_tail_call_events)  
  
<a name="jit_inlining_events"></a>   
## <a name="jit-inlining-events"></a>JIT vkládání události  
  
### <a name="methodjitinliningfailed-event"></a>MethodJitInliningFailed události  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň. (Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`JITTracingKeyword` (0x10)|Verbose (5)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`MethodJitInliningFailed`|186|Vkládání JIT se nezdařilo.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|win:UnicodeString|Namespace metody, která je kompilován.|  
|MethodBeingCompiledName|win:UnicodeString|Název metody, která je kompilován.|  
|MethodBeingCompiledNameSignature|win:UnicodeString|Podpis metody, která je kompilován.|  
|InlinerNamespace|win:UnicodeString|Obor názvů metody kompilátor JIT je pokusu o generování kódu pro.|  
|InlinerName|win:UnicodeString|Název metody, kompilátor se pokouší o generování kódu pro. To nemusí být stejný jako `MethodBeingCompiledName` Pokud kompilátor se pokouší vloženého kódu do `MethodBeingCompiledName` místo aby generovala volání `InlinerName`.|  
|InlinerNameSignature|win:UnicodeString|Podpis pro inliner.|  
|InlineeNamespace|win:UnicodeString|Obor názvů inlinee.|  
|InlineeName|win:UnicodeString|Kompilátor se pokouší vložené metody (ne generovat volání).|  
|InlineeNameSignature|win:UnicodeString|Podpis pro inlinee.|  
|FailAlways|Windows: datový typ Boolean|Nápovědu pro vkládání, který kompilátor JIT vždy se nezdaří inlinee.|  
|FailReason|win:UnicodeString|INLINE_NEVER znamená, že předchozí pokus o vkládání určit se vkládání bude z nějakého důvodu; nikdy úspěšné text, v opačném případě volného tvaru.|  
|ClrInstanceID|win:UnicodeString|Jedinečné ID instance CLR nebo CoreCLR.|  
  
### <a name="methodjitinliningsucceeded-event"></a>MethodJitInliningSucceeded události  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`JITTracingKeyword` (0x10)|Verbose (5)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`MethodJitInliningSucceeded`|185|Metoda vkládání byla úspěšná.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|win:UnicodeString|Obor názvů metody, která je kompilován.|  
|MethodBeingCompiledName|win:UnicodeString|Název metody, které se je zkompilován.|  
|MethodBeingCompiledNameSignature|win:UnicodeString|Podpis metody, která je kompilován.|  
|InlinerNamespace|win:UnicodeString|Obor názvů metody kompilátor JIT se pokouší o generování kódu pro.|  
|InlinerName|win:UnicodeString|Název metody, kompilátor se pokouší o generování kódu pro. To nemusí být stejný jako `MethodBeingCompiledName` Pokud kompilátor se pokouší vloženého kódu do `MethodBeingCompiledName` místo aby generovala volání `InlinerName`.|  
|InlinerNameSignature|win:UnicodeString|Podpis pro inliner.|  
|InlineeNamespace|win:UnicodeString|Obor názvů inlinee.|  
|InlineeName|win:UnicodeString|Kompilátor se pokouší vložené metody (ne generovat volání).|  
|InlineeNameSignature|win:UnicodeString|Podpis pro inlinee.|  
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="jit_tail_call_events"></a>   
## <a name="jit-tail-call-events"></a>JIT – události volání funkce Tail  
  
### <a name="methodjittailcallfailed-event"></a>MethodJITTailCallFailed události  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`JITTracingKeyword` (0x10)|Verbose (5)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`MethodJitTailCallFailed`|189|Volání funkce tail metody se nezdařilo.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|win:UnicodeString|Namespace metody, která je kompilován.|  
|MethodBeingCompiledName|win:UnicodeString|Název metody, která je kompilován.|  
|MethodBeingCompiledNameSignature|win:UnicodeString|Podpis metody, která je kompilován.|  
|CallerNamespace|win:UnicodeString|Obor názvů metody kompilátor JIT se pokouší o generování kódu pro.|  
|CallerName|win:UnicodeString|Název metody, kompilátor se pokouší o generování kódu pro.|  
|CallerNameSignature|win:UnicodeString|Podpis pro volajícího.|  
|CalleeNamespace|win:UnicodeString|Obor názvů volaný.|  
|CalleeName|win:UnicodeString|Metoda kompilátor se pokouší o volání tail (ne generovat volání).|  
|CalleeNameSignature|win:UnicodeString|Podpis pro volaný.|  
|TailPrefix|Windows: datový typ Boolean|Předpona pro volání funkce tail|  
|FailReason|win:UnicodeString|Volání funkce tail důvod se nezdařilo.|  
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
### <a name="methodjittailcallsucceeded-event"></a>MethodJITTailCallSucceeded události  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`JITTracingKeyword` (0x10)|Verbose (5)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`MethodJitTailCallSucceeded`|188|Volání funkce tail metoda byla úspěšná.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|win:UnicodeString|Namespace metody, která je kompilován.|  
|MethodBeingCompiledName|win:UnicodeString|Název metody, která je kompilován.|  
|MethodBeingCompiledNameSignature|win:UnicodeString|Podpis metody, která je kompilován.|  
|CallerNamespace|win:UnicodeString|Obor názvů metody kompilátor JIT se pokouší o generování kódu pro.|  
|CallerName|win:UnicodeString|Název metody, kompilátor se pokouší o generování kódu pro.|  
|CallerNameSignature|win:UnicodeString|Podpis pro volajícího.|  
|CalleeNamespace|win:UnicodeString|Obor názvů volaný.|  
|CalleeName|win:UnicodeString|Metoda kompilátor se pokouší o volání tail (ne generovat volání).|  
|CalleeNameSignature|win:UnicodeString|Podpis pro volaný.|  
|TailPrefix|Windows: datový typ Boolean|Předpona pro volání funkce tail.|  
|TailCallType|win:UnicodeString|Druh volání funkce tail.|  
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
## <a name="see-also"></a>Viz také:

- [Události Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-events.md)
