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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdbad4a5eb9a9d0c81ae8d29394652e9f6df136e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44214430"
---
# <a name="contextswitchdeadlock-mda"></a>contextSwitchDeadlock – pomocník spravovaného ladění (MDA)

`contextSwitchDeadlock` Pomocníka spravovaného ladění (MDA) je aktivován, když bude během na pokus o přechod kontextu COM zjištěno zablokování.

## <a name="symptoms"></a>Příznaky

Nejběžnější symptomem je, že volání nespravovaného komponenty modelu COM ze spravovaného kódu nevrací.  Dalším symptomem je využití paměti v průběhu času zvětšuje.

## <a name="cause"></a>příčina

Nejvíce nejpravděpodobnější příčinou je, že vlákno jednovláknový apartment (STA) není – čerpání zpráv. Vlákna STA je buď čekání bez čerpání zpráv nebo provádění operací zdlouhavé a nepovoluje žádná fronta zpráv čerpadla.

Využití paměti v průběhu času nezvyšuje je způsobeno pokusu o volání vlákna finalizační metody `Release` na nespravovaného COM komponenty a komponenty nevrací.  To zabrání finalizační metoda uvolní jiných objektů.

Ve výchozím nastavení modelu vláken pro hlavní vlákno konzolové aplikace jazyka Visual Basic je STA. Toto MDA aktivováno, pokud vláknem STA. používá interoperabilita modelů COM přímo nebo nepřímo prostřednictvím common language runtime nebo jiného ovládacího prvku.  Vyhněte se aktivuje toto MDA v konzolové aplikace jazyka Visual Basic, použije <xref:System.MTAThreadAttribute> atribut do metody main nebo upravit aplikaci pro pumpování zpráv.

Je možné toto MDA falešně aktivaci, pokud jsou splněny všechny následující podmínky:

-   Aplikace vytvoří komponenty modelu COM z vláken STA přímo nebo nepřímo prostřednictvím knihoven.

-   Aplikace byla zastavena v ladicím programu a uživatel pokračuje aplikace nebo provést operaci kroku.

-   Ladění nespravovaného kódu není povolená.

Pokud chcete zjistit, pokud MDA falešně aktivovaná, zakázat všechny zarážky, restartujte aplikaci a povolíte jeho spuštění bez přerušení. Pokud MDA aktivováno, je pravděpodobné, že počáteční aktivace byla hodnotu false. V takovém případě zakážete MDA, aby se zabránilo narušení relace ladění.

> [!NOTE]
> Toto MDA je ve výchozím nastavení pro sadu Visual Studio. Informace o tom, jak zakázat mda najdete v tématu [diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).

## <a name="resolution"></a>Rozlišení

Postupujte podle pravidla COM – čerpání zpráv STA.

## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime

Toto MDA nemá žádný vliv na CLR. Sestavy pouze data o COM kontextech.

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
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
