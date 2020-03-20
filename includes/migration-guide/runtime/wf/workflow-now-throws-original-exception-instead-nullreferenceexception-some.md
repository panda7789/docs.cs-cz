---
ms.openlocfilehash: 470fc2ddcfbb29a677cadb6e7e1d2e55784d7ac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802557"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a>Pracovní postup nyní vyvolá původní výjimku místo NullReferenceException v některých případech

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6.2 a starších verzích při spuštění metody <code>null</code> aktivity <xref:System.Exception.Message> pracovního postupu vyvolá výjimku s <xref:System.NullReferenceException?displayProperty=name>hodnotou vlastnosti, zaběhu System.Activities Workflow vyvolá , maskování původní výjimku. V rozhraní .NET Framework 4.7 je vyvolána dříve maskovaná výjimka.|
|Návrh|Pokud váš kód závisí <xref:System.NullReferenceException?displayProperty=name>na zpracování , změňte jej zachytit výjimky, které by mohly být vyvolány z vlastníaktivity.|
|Rozsah|Vedlejší|
|Version|4.7|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|
