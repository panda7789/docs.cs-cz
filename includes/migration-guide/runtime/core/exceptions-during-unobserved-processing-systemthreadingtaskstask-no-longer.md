---
ms.openlocfilehash: b0e6d6f228647148083d3df64e65f817dc3455d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379583"
---
### <a name="exceptions-during-unobserved-processing-in-systemthreadingtaskstask-no-longer-propagate-on-finalizer-thread"></a>Výjimky během asynchronního nepozorovaného zpracování v System.Threading.Tasks.Task již nebude šířit na finalizační podproces

|   |   |
|---|---|
|Podrobnosti|Vzhledem k tomu, <xref:System.Threading.Tasks.Task?displayProperty=name> třída reprezentuje asynchronní operaci, zachycuje všechny nezávažné výjimky, ke kterým dojde během asynchronního zpracování. V rozhraní .NET Framework 4.5 Pokud není dodržena výjimka a váš kód nikdy nečeká v úloze, výjimka se již nebude šířit na finalizační podproces a shazovat proces při uvolňování paměti. Tato změna zvyšuje spolehlivost aplikací, které používají třídy úloh k provádění asynchronního nepozorovaného zpracování.|
|Doporučení|Aplikací závislých na asynchronního nepozorovaného asynchronní výjimky šíření vlákna finalizační metody, poskytnutím odpovídajícího popisovače lze obnovit předchozí chování <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> události, nebo nastavením [element konfigurace modulu runtime ](~/docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md).|
|Scope|Edge|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Action,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Start?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Start(System.Threading.Tasks.TaskScheduler)?displayProperty=nameWithType></li></ul>|
