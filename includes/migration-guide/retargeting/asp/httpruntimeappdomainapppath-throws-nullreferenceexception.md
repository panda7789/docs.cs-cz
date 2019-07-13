---
ms.openlocfilehash: d6c658f306dd4792e3cb5dbdc9471043ca95a071
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859195"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a>HttpRuntime.AppDomainAppPath vyvolá NullReferenceException

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6.2, modul runtime vyvolá <code>T:System.NullReferenceException</code> při načítání <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> hodnotu, která obsahuje znaky s hodnotou null. V rozhraní .NET Framework 4.6.1 a starší verze, modul runtime vyvolá <code>T:System.ArgumentNullException</code>.|
|Doporučení|Můžete provést jeden z těchto kroků reagovat na tuto změnu:<ul><li>Zpracování <code>T:System.NullReferenceException</code> Pokud aplikace běží na rozhraní .NET Framework 4.6.2.</li><li>Upgrade na rozhraní .NET Framework 4.7, který obnoví předchozí chování a vyvolá <code>T:System.ArgumentNullException</code>.</li></ul>|
|Scope|Edge|
|Version|4.6.2|
|type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType></li></ul>|

