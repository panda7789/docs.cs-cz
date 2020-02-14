---
title: contextSwitchDeadlock – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- deadlocks [.NET Framework]
- pumping messages
- STA message pumping
- single-threaded COM components
- MDAs (managed debugging assistants), context switching deadlocks
- managed debugging assistants (MDAs), context switching deadlocks
- ContextSwitchDeadlock MDA
- message pumping
- context switching deadlocks
ms.assetid: 26dfaa15-9ddb-4b0a-b6da-999bba664fa6
ms.openlocfilehash: e3fc4a2cb35cdcc713ba0ef362071083af08a27b
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217557"
---
# <a name="contextswitchdeadlock-mda"></a>contextSwitchDeadlock – pomocník spravovaného ladění (MDA)

Pokud se během přechodu kontextu modelu COM zjistí zablokování, aktivuje se Pomocník s `contextSwitchDeadlock` Managed Debugging Assistant (MDA).

## <a name="symptoms"></a>Příznaky

Nejběžnějším příznakem je, že volání na nespravované součásti modelu COM ze spravovaného kódu nevrátí.  Dalším příznakem je využití paměti při nárůstu času.

## <a name="cause"></a>Příčina

Nejpravděpodobnější příčinou je, že vlákno s jedním vláknem (STA) neprovádí pumpu zpráv. Vlákno STA buď čeká bez pumpování zpráv, nebo provádí zdlouhavé operace a neumožňuje frontě zpráv pumpovat.

Zvýšení využití paměti v průběhu času je způsobeno tím, že se podproces finalizačního vlákna snaží volat `Release` na nespravované součásti modelu COM a tato součást nevrací.  To brání finalizačnímu objektu v uvolnění jiných objektů.

Ve výchozím nastavení je model vláken pro hlavní vlákno Visual Basic konzolových aplikací STA. Tato aplikace MDA je aktivována, pokud vlákno STA používá interoperabilitu modelu COM přímo nebo nepřímo prostřednictvím modulu CLR (Common Language Runtime) nebo ovládacího prvku třetí strany.  Chcete-li se vyhnout aktivaci tohoto MDA ve Visual Basic konzolové aplikaci, použijte atribut <xref:System.MTAThreadAttribute> na metodu Main nebo upravte aplikaci na zprávy pumpy.

Je možné, že se tento MDA při splnění všech následujících podmínek aktivuje jako nepravdivá:

- Aplikace vytváří komponenty modelu COM z vláken STA buď přímo, nebo nepřímo prostřednictvím knihoven.

- Aplikace byla zastavena v ladicím programu a uživatel buď pokračoval v aplikaci, nebo provedení operace kroku.

- Nespravované ladění není povoleno.

Chcete-li zjistit, zda je MDA nepravdivě aktivován, zakažte všechny zarážky, restartujte aplikaci a umožněte její spuštění bez zastavení. Pokud není modul MDA aktivován, je pravděpodobnější, že počáteční aktivace byla nepravdivá. V takovém případě zakažte režim MDA, aby se zabránilo interferenci s relací ladění.

> [!NOTE]
> Tento MDA je ve výchozí sadě pro Visual Studio. Informace o tom, jak zakázat MDA, najdete v tématu [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).

## <a name="resolution"></a>Řešení

Sledujte pravidla modelu COM týkající se čerpacích zpráv STA.

## <a name="effect-on-the-runtime"></a>Vliv na modul runtime

Tento MDA nemá žádný vliv na CLR. Pouze hlásí data o kontextech COM.

## <a name="output"></a>Výstup

Zpráva popisující aktuální kontext a cílový kontext.

## <a name="configuration"></a>Konfigurace

```xml
<mdaConfig>
  <assistants>
    <contextSwitchDeadlock />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
