---
ms.openlocfilehash: 5ad9c494fd02059e05cc744aad3b06cfc9399995
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451879"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>Výchozí hodnota HttpRequestMessage.Version změněna na 1.1

Výchozí hodnota vlastnosti <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> se změnila z 2.0 na 1.1.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="change-description"></a>Popis změny

V rozhraní .NET Core 1.0 až 2.0 je výchozí hodnota vlastnosti <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 1.1. Počínaje rozhraním .NET Core 2.1 byl změněn na 2.1.

Počínaje rozhraním .NET Core 3.0 je <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> výchozí číslo verze vrácené vlastností opět 1.1.

#### <a name="recommended-action"></a>Doporučená akce

Aktualizujte kód, pokud <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> závisí na vlastnost vrácení výchozí hodnotu 2.0.

#### <a name="category"></a>Kategorie

Sítě

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-->
