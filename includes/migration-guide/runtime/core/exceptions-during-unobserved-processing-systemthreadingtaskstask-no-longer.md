---
ms.openlocfilehash: 5ba2ddb76ab946339449246840667ba4a48e9c66
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619978"
---
### <a name="exceptions-during-unobserved-processing-in-systemthreadingtaskstask-no-longer-propagate-on-finalizer-thread"></a>Výjimky během nepozorovaného zpracování v System. Threading. Tasks. Task již nešíří v finalizačním vlákně

#### <a name="details"></a>Podrobnosti

Vzhledem k tomu <xref:System.Threading.Tasks.Task?displayProperty=fullName> , že třída představuje asynchronní operaci, zachycuje všechny nezávažné výjimky, ke kterým dojde během asynchronního zpracování. Pokud je v .NET Framework 4,5 výjimka nedodržena a váš kód nikdy nečeká na úlohu, výjimka již nebude rozšířena na finalizační vlákno a při uvolňování paměti během procesu uvolňování paměti dojde k chybě. Tato změna zvyšuje spolehlivost aplikací, které používají třídu Task k provádění nepozorovaného asynchronního zpracování.

#### <a name="suggestion"></a>Návrh

Pokud aplikace závisí na nepozorovaných asynchronních výjimkách, které se šíří do finalizační metody, předchozí chování lze obnovit poskytnutím vhodné obslužné rutiny pro <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> událost nebo nastavením [elementu konfigurace modulu runtime](~/docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md).

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Action,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Start?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Start(System.Threading.Tasks.TaskScheduler)?displayProperty=nameWithType></li></ul>|
