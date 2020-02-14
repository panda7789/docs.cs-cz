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
ms.openlocfilehash: c789e8cb409bd4c59c91d6b646efe428afe7c86d
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217244"
---
# <a name="pinvokestackimbalance-mda"></a>PInvokeStackImbalance – pomocník spravovaného ladění (MDA)

Pokud CLR zjistí, že Hloubka zásobníku po volání metody Invoke se neshoduje s očekávanou hloubkou zásobníku, na základě konvence volání zadané v atributu <xref:System.Runtime.InteropServices.DllImportAttribute> a deklaraci parametrů ve spravovaném podpisu, je aktivována aplikace `PInvokeStackImbalance` Managed Debugging Assistant (MDA).

`PInvokeStackImbalance` MDA se implementuje jenom pro 32 platformy x86.

> [!NOTE]
> Služba `PInvokeStackImbalance` MDA je ve výchozím nastavení zakázána. V aplikaci Visual Studio 2017 a novějších verzích se `PInvokeStackImbalance` MDA zobrazí v seznamu **asistenti spravovaného ladění** v dialogovém okně **nastavení výjimky** (které se zobrazí, když vyberete **ladění** > **Windows** > **Nastavení výjimek**). Zaškrtnutím nebo zrušením zaškrtnutí políčka **přerušit, pokud je vyvolána** , nepovolíte nebo zakážete MDA; Určuje, zda aplikace Visual Studio vyvolá výjimku při aktivaci MDA.

## <a name="symptoms"></a>Příznaky

V aplikaci dojde k narušení přístupu nebo poškození paměti při volání vyvolání nebo po volání platformy.

## <a name="cause"></a>Příčina

Spravovaný podpis volání vyvolání platformy nemusí odpovídat nespravovanému podpisu volané metody.  Tato neshoda může být způsobena spravovaným podpisem, který nedeklaruje správný počet parametrů, nebo nespecifikuje odpovídající velikost pro parametry.  Služba MDA může být také aktivována, protože konvence volání, která je pravděpodobně určena atributem <xref:System.Runtime.InteropServices.DllImportAttribute>, neodpovídá nespravované konvenci volání.

## <a name="resolution"></a>Řešení

Zkontrolujte spravovanou platformu vyvolání signatury a konvence volání, abyste ověřili shodu s signaturou a konvencí volání nativního cíle.  Zkuste explicitně specifikovat konvenci volání na spravovaných i nespravovaných stranách. Je také možné, i když to není pravděpodobné, že nespravované funkce z nějakého důvodu vyrovnaly zásobník z nějakého jiného důvodu, jako je například Chyba v nespravovaném kompilátoru.

## <a name="effect-on-the-runtime"></a>Vliv na modul runtime

Vynutí, aby volání všech platforem převzala neoptimalizovanou cestu v modulu CLR.

## <a name="output"></a>Výstup

Zpráva MDA poskytuje název volání metody vyvolání platformy, která způsobuje nerovnováhu zásobníku. Ukázková zpráva volání metody Invoke na metodě `SampleMethod` je:

**Volání funkce PInvoke ' SampleMethod ' vyrovnalo vyvážení zásobníku. To je pravděpodobně způsobeno tím, že spravovaný podpis PInvoke neodpovídá nespravovanému cílovému podpisu. Ověřte, že konvence volání a parametry signatury PInvoke odpovídají cílovému nespravovanému podpisu.**

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
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
