---
ms.openlocfilehash: ae0c7322b7415157838278b5568e6e49936e9a93
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621100"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a>Pracovní postup teď vygeneruje původní výjimku místo NullReferenceException v některých případech.

#### <a name="details"></a>Podrobnosti

V .NET Framework 4.6.2 a starších verzích, když metoda Execute aktivity pracovního postupu vyvolá výjimku s <code>null</code> hodnotou <xref:System.Exception.Message> vlastnosti, modul runtime pracovního postupu System. Activities vyvolá a <xref:System.NullReferenceException?displayProperty=fullName> maskuje původní výjimku. V .NET Framework 4,7 je vyvolána dříve maskovaná výjimka.

#### <a name="suggestion"></a>Návrh

Pokud váš kód spoléhá na zpracování <xref:System.NullReferenceException?displayProperty=fullName> , změňte ho na zachytit výjimky, které by mohly být vyvolány z vašich vlastních aktivit.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4,7|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|
