---
ms.openlocfilehash: 470fc2ddcfbb29a677cadb6e7e1d2e55784d7ac2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803646"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a>Pracovní postup vyvolá nyní původní výjimku namísto NullReferenceException v některých případech

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6.2 a předchozími verzemi, pokud metodu Execute aktivita pracovního postupu vyvolá výjimku <code>null</code> hodnota <xref:System.Exception.Message> vlastnost, modul runtime pracovního postupu System.Activities vyvolá výjimku <xref:System.NullReferenceException?displayProperty=name>, maskování původní výjimka. V rozhraní .NET Framework 4.7 je vyvolána výjimka dříve maskované.|
|Doporučení|Pokud váš kód závisí na zpracování <xref:System.NullReferenceException?displayProperty=name>, změňte ho na zachytit výjimky, které mohou být vyvolány z vlastních aktivit.|
|Rozsah|Vedlejší|
|Version|4.7|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|
