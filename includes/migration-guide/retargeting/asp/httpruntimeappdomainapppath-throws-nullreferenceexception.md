---
ms.openlocfilehash: 986b647047aaa4a185c1403e96e499ae587bea98
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617526"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a>HttpRuntime. AppDomainAppPath vyvolá NullReferenceException

#### <a name="details"></a>Podrobnosti

V .NET Framework 4.6.2 vyvolá modul runtime `T:System.NullReferenceException` při načítání `P:System.Web.HttpRuntime.AppDomainAppPath` hodnoty, která obsahuje znaky null. V .NET Framework 4.6.1 a dřívějších verzích vyvolá modul runtime `T:System.ArgumentNullException` .

#### <a name="suggestion"></a>Návrh

Na tuto změnu můžete reagovat jedním z těchto kroků:

- Zpracujte, `T:System.NullReferenceException` Pokud je aplikace spuštěná na .NET Framework 4.6.2.
- Upgradujte na .NET Framework 4,7, který obnoví předchozí chování a vyvolá `T:System.ArgumentNullException` .

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.6.2       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType>
