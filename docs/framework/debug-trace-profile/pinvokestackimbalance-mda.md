---
title: pInvokeStackImbalance – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- stack depth
- platform invoke stack imbalance
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- PInvokeStackImbalance MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: 34ddc6bd-1675-4f35-86aa-de1645d5c631
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5594166081c36fbda1e5d1a62e017aaceb7a553d
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2018
ms.locfileid: "42912111"
---
# <a name="pinvokestackimbalance-mda"></a>PInvokeStackImbalance – pomocník spravovaného ladění (MDA)

`PInvokeStackImbalance` Pomocníka spravovaného ladění (MDA) se aktivuje, když modul CLR zjistí, že hloubka zásobníku po vyvolání platformy volání neodpovídá očekávané zásobníku hloubky, zadané konvence volání zadaná v <xref:System.Runtime.InteropServices.DllImportAttribute> atribut a deklarace parametrů v spravovaný podpis.

`PInvokeStackImbalance` MDA je implementované jenom pro x86 32bitové platformy.

> [!NOTE]
> `PInvokeStackImbalance` MDA je ve výchozím nastavení zakázané. V sadě Visual Studio 2017 `PInvokeStackImbalance` MDA se zobrazí v **asistentů spravovaného ladění** v seznamu **nastavení výjimek** dialogové okno (který se zobrazí po výběru **ladění**  >  **Windows** > **nastavení výjimek**). Ale zaškrtnutím nebo zrušením zaškrtnutí **přerušení při vyvolání** zaškrtněte políčko Povolit nebo zakázat MDA; pouze určuje, zda sady Visual Studio vyvolá výjimku, když MDA aktivováno.

## <a name="symptoms"></a>Příznaky

Aplikace zjistí narušením přístupu nebo paměti, volání funkce invoke poškození při vytváření nebo následující platformy.

## <a name="cause"></a>příčina

Volání funkce invoke spravovaný podpis platformy se nemusí shodovat nespravovanému podpisu volané metody.  K této neshodě může být způsobeno spravovaný podpis nedeklarováním správný počet parametrů nebo bez zadání odpovídající velikost pro parametry.  MDA lze také aktivovat, protože konvence volání, může být určeno <xref:System.Runtime.InteropServices.DllImportAttribute> atribut, se neshoduje s konvence nespravovaného volání.

## <a name="resolution"></a>Rozlišení

Kontrola spravovanou platformu vyvolání podpis a konvence volání pro potvrzení, že odpovídá podpisu a konvence volání nativní cíle.  Zkuste explicitně zadat konvence volání na spravovaných a nespravovaných stranách. Je také možné, i když ne jako pravděpodobné, že nespravovanou funkci nevyvážená zásobníku nějakého jiného důvodu, jako jsou chyby v nespravované kompilátoru.

## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime

Vynutí všechny nespravovaného volání nonoptimized cestou v CLR.

## <a name="output"></a>Výstup

Zpráva MDA poskytuje název platformy vyvolat volání metody, která je příčinou nevyváženosti zásobníku. Ukázková zpráva platformy vyvolání volání metody `SampleMethod` je:

**Zásobník má nevyvážená volání funkce PInvoke "SampleMethod". To je pravděpodobné, protože spravovaný podpis PInvoke neodpovídá nespravovanému cílovému podpisu. Zkontrolujte, jestli se konvence volání a parametry podpisu PInvoke odpovídají cílovému nespravovanému podpisu.**

## <a name="configuration"></a>Konfigurace

```xml
<mdaConfig>
  <assistants>
    <pInvokeStackImbalance />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
