---
title: Události Trasování událostí pro Windows trasování JIT
description: Porozumět událostem trasování událostí pro Windows JIT (just-in-time). Tyto události shromažďují informace týkající se úspěchu nebo neúspěchu vkládání JIT a volání funkce JIT tail.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT tracing events [.NET Framework]
- ETW, JIT tracing events (CLR)
ms.assetid: 926adde2-c123-452e-bf4f-4b977bf06ffb
ms.openlocfilehash: 568fc942cd0e2188c530d2befb6260083757ec72
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474459"
---
# <a name="jit-tracing-etw-events"></a>Události Trasování událostí pro Windows trasování JIT
Tyto události shromažďují informace týkající se úspěchu nebo neúspěchu vkládání za běhu (JIT) a volání JIT (just-in-time).

## <a name="jit-inlining-events"></a>Události vkládání JIT

### <a name="methodjitinliningfailed-event"></a>Událost MethodJitInliningFailed
 Klíčové slovo a úroveň jsou uvedeny v následující tabulce. (Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).)  
  
|Klíčové slovo pro vyvolání události|Úroveň|  
|-----------------------------------|-----------|  
|`JITTracingKeyword`0x10|Verbose (5)|  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`MethodJitInliningFailed`|186|Vkládání JIT selhalo.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|Win: UnicodeString|Obor názvů metody, která je kompilována.|  
|MethodBeingCompiledName|Win: UnicodeString|Název metody, která je kompilována.|  
|MethodBeingCompiledNameSignature|Win: UnicodeString|Podpis metody, která je kompilována.|  
|InlinerNamespace|Win: UnicodeString|Obor názvů metody, pro kterou kompilátor JIT zkouší vygenerovat kód.|  
|Inliniový|Win: UnicodeString|Název metody, pro kterou se kompilátor pokouší vytvořit kód. To nemusí být stejné jako v `MethodBeingCompiledName` případě, že se kompilátor pokouší vložit kód do `MethodBeingCompiledName` , namísto vyvolání volání `InlinerName` .|  
|InlinerNameSignature|Win: UnicodeString|Podpis pro inline.|  
|InlineeNamespace|Win: UnicodeString|Obor názvů pro inline.|  
|InlineeName|Win: UnicodeString|Metoda, kterou se kompilátor pokouší vložit (negeneruje volání do).|  
|InlineeNameSignature|Win: UnicodeString|Podpis pro inline|  
|FailAlways|výher: Boolean|Pomocný parametr kompilátoru JIT, že inlineing bude pro vložení vždy selhat.|  
|FailReason|Win: UnicodeString|INLINE_NEVER znamená, že předchozí pokus o vkládání zjistil, že vkládání nebude nikdy z jiného důvodu úspěšné; v opačném případě text volné formy.|  
|ClrInstanceID|Win: UnicodeString|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
### <a name="methodjitinliningsucceeded-event"></a>Událost MethodJitInliningSucceeded  
 Klíčové slovo a úroveň jsou uvedeny v následující tabulce.  
  
|Klíčové slovo pro vyvolání události|Úroveň|  
|-----------------------------------|-----------|  
|`JITTracingKeyword`0x10|Verbose (5)|  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`MethodJitInliningSucceeded`|185|Přeložení metody bylo úspěšné.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|Win: UnicodeString|Obor názvů metody, která je kompilována.|  
|MethodBeingCompiledName|Win: UnicodeString|Název metody, která je zkompilována.|  
|MethodBeingCompiledNameSignature|Win: UnicodeString|Signatura metody, která je kompilována.|  
|InlinerNamespace|Win: UnicodeString|Obor názvů metody, pro kterou kompilátor JIT zkouší vygenerovat kód.|  
|Inliniový|Win: UnicodeString|Název metody, pro kterou se kompilátor pokouší vytvořit kód. To nemusí být stejné jako v `MethodBeingCompiledName` případě, že se kompilátor pokouší vložit kód do `MethodBeingCompiledName` , namísto vyvolání volání `InlinerName` .|  
|InlinerNameSignature|Win: UnicodeString|Podpis pro inline.|  
|InlineeNamespace|Win: UnicodeString|Obor názvů pro inline.|  
|InlineeName|Win: UnicodeString|Metoda, kterou se kompilátor pokouší vložit (negeneruje volání do).|  
|InlineeNameSignature|Win: UnicodeString|Podpis pro inline|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  

## <a name="jit-tail-call-events"></a>Události volání funkce tail JIT  
  
### <a name="methodjittailcallfailed-event"></a>Událost MethodJITTailCallFailed  
 Klíčové slovo a úroveň jsou uvedeny v následující tabulce.  
  
|Klíčové slovo pro vyvolání události|Úroveň|  
|-----------------------------------|-----------|  
|`JITTracingKeyword`0x10|Verbose (5)|  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`MethodJitTailCallFailed`|189|Volání metody Tail se nezdařilo.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|Win: UnicodeString|Obor názvů metody, která je kompilována.|  
|MethodBeingCompiledName|Win: UnicodeString|Název metody, která je kompilována.|  
|MethodBeingCompiledNameSignature|Win: UnicodeString|Podpis metody, která je kompilována.|  
|CallerNamespace|Win: UnicodeString|Obor názvů metody, pro kterou kompilátor JIT zkouší vygenerovat kód.|  
|Volající|Win: UnicodeString|Název metody, pro kterou se kompilátor pokouší vytvořit kód.|  
|CallerNameSignature|Win: UnicodeString|Podpis volajícího.|  
|CalleeNamespace|Win: UnicodeString|Obor názvů volaného.|  
|Volaný|Win: UnicodeString|Metoda, kterou kompilátor zkouší při volání funkce tail (negeneruje volání do).|  
|CalleeNameSignature|Win: UnicodeString|Podpis volaného.|  
|TailPrefix|výher: Boolean|Předpona pro volání funkce tail|  
|FailReason|Win: UnicodeString|Důvod, proč volání funkce tail selhalo.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
### <a name="methodjittailcallsucceeded-event"></a>Událost MethodJITTailCallSucceeded  
 Klíčové slovo a úroveň jsou uvedeny v následující tabulce.  
  
|Klíčové slovo pro vyvolání události|Úroveň|  
|-----------------------------------|-----------|  
|`JITTracingKeyword`0x10|Verbose (5)|  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`MethodJitTailCallSucceeded`|188|Volání metody Tail bylo úspěšné.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|Win: UnicodeString|Obor názvů metody, která je kompilována.|  
|MethodBeingCompiledName|Win: UnicodeString|Název metody, která je kompilována.|  
|MethodBeingCompiledNameSignature|Win: UnicodeString|Podpis metody, která je kompilována.|  
|CallerNamespace|Win: UnicodeString|Obor názvů metody, pro kterou kompilátor JIT zkouší vygenerovat kód.|  
|Volající|Win: UnicodeString|Název metody, pro kterou se kompilátor pokouší vytvořit kód.|  
|CallerNameSignature|Win: UnicodeString|Podpis volajícího.|  
|CalleeNamespace|Win: UnicodeString|Obor názvů volaného.|  
|Volaný|Win: UnicodeString|Metoda, kterou kompilátor zkouší při volání funkce tail (negeneruje volání do).|  
|CalleeNameSignature|Win: UnicodeString|Podpis volaného.|  
|TailPrefix|výher: Boolean|Předpona pro volání funkce tail|  
|TailCallType|Win: UnicodeString|Typ volání funkce tail.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
## <a name="see-also"></a>Viz také

- [Události ETW CLR](clr-etw-events.md)
