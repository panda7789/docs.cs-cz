---
ms.openlocfilehash: 4529d8040fc08b5290ac46abd1ef752086ea3aeb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62088477"
---
### <a name="new-ambiguous-dispatcherinvoke-overloads-could-result-in-different-behavior"></a>Nová přetížení (nejednoznačný) Dispatcher.Invoke by mohlo způsobit různé chování

|   |   |
|---|---|
|Podrobnosti|Rozhraní .NET Framework 4.5 přidá nová přetížení <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> , které zahrnují parametr typu <xref:System.Action>. Při nové kompilaci stávajícího kódu mohou kompilátory vyřešit volání metod Dispatcher.Invoke, které mají <xref:System.Delegate> parametr jako volání metod Dispatcher.Invoke s <xref:System.Action> parametru. Pokud je volání přetížení Dispatcher.Invoke s <xref:System.Delegate> parametrem je vyřešeno jako volání přetížení Dispatcher.Invoke s <xref:System.Action> parametr, mohou nastat následující rozdíly v chování:<ul><li>Pokud dojde k výjimce <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter> a <xref:System.Windows.Threading.Dispatcher.UnhandledException> události nejsou započteny. Místo toho jsou výjimky zpracovávány <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=name> událostí.</li><li>Volání některých členů jako <xref:System.Windows.Threading.DispatcherOperation.Result>, zablokována až do dokončení operace.</li></ul>|
|Doporučení|Vyhněte se nejednoznačnosti (a potenciální rozdíly v výjimek zpracování nebo blokování chování), code volání Dispatcher.Invoke lze předat prázdný object [] jako druhý parametr je vyvolat volání opravdu řešení přetížení metody rozhraní .NET Framework 4.0.|
|Rozsah|Vedlejší|
|Version|4.5|
|Type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType></li></ul>|
