---
ms.openlocfilehash: e7154919d6a09a04e650d5546feb2ae6c6cc912f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859195"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a>HttpRuntime.AppDomainAppPath vyvolá výjimku NullReferenceException

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6.2 za <code>T:System.NullReferenceException</code> běhu vyvolá <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> při načítání hodnoty, která obsahuje znaky null. V rozhraní .NET Framework 4.6.1 a starších verzích za běhu vyvolá . <code>T:System.ArgumentNullException</code>|
|Návrh|Můžete provést některou z následujících reagovat na tuto změnu:<ul><li><code>T:System.NullReferenceException</code> Zpracování, pokud je aplikace spuštěna v rozhraní .NET Framework 4.6.2.</li><li>Upgrade na rozhraní .NET Framework 4.7, který obnoví <code>T:System.ArgumentNullException</code>předchozí chování a vyvolá .</li></ul>|
|Rozsah|Edge|
|Version|4.6.2|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType></li></ul>|
