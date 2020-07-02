---
ms.openlocfilehash: 80e61d4dd5b8d4754a39e95e37475fefff57fcbd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617170"
---
### <a name="new-ambiguous-dispatcherinvoke-overloads-could-result-in-different-behavior"></a>New (dvojznačný) Dispatcher. Invoke přetížení může mít za následek odlišné chování.

#### <a name="details"></a>Podrobnosti

.NET Framework 4,5 přidává nová přetížení <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> , která obsahují parametr typu <xref:System.Action> . Pokud je existující kód znovu zkompilován, kompilátory mohou vyřešit volání metody Dispatcher. Invoke metod, které mají <xref:System.Delegate> parametr jako volání metody Dispatcher. Invoke metod s <xref:System.Action> parametrem. Pokud volání metody Dispatcher. Invoke přetížení s <xref:System.Delegate> parametrem je přeloženo jako volání metody Dispatcher. Invoke přetížení s <xref:System.Action> parametrem, mohou nastat následující rozdíly v chování:

- Pokud dojde k výjimce, <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter> <xref:System.Windows.Threading.Dispatcher.UnhandledException> události a nejsou vyvolány. Místo toho jsou výjimky zpracovávány <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=fullName> událostí.
- Volání některých členů, například <xref:System.Windows.Threading.DispatcherOperation.Result> , zablokuje, dokud se operace nedokončí.

#### <a name="suggestion"></a>Návrh

Aby nedocházelo k nejednoznačnosti (a potenciálním rozdílům v chování zpracování výjimek nebo blokování), kód volajícího metody Dispatcher. Invoke může předat prázdný objekt [] jako druhý parametr volání metody Invoke, aby bylo zajištěno překládání na přetížení metody .NET Framework 4,0.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.5         |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType>
