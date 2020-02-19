---
ms.openlocfilehash: 5ad9c494fd02059e05cc744aad3b06cfc9399995
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451879"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>Výchozí hodnota zprávy HttpRequestMessage. Version se změnila na 1,1.

Výchozí hodnota vlastnosti <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> se změnila z 2,0 na 1,1.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="change-description"></a>Změnit popis

V .NET Core 1,0 až 2,0 je výchozí hodnota vlastnosti <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 1,1. Počínaje .NET Core 2,1 se změnilo na 2,1.

Počínaje rozhraním .NET Core 3,0 je výchozí číslo verze vrácené vlastností <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> znovu 1,1.

#### <a name="recommended-action"></a>Doporučená akce

Aktualizujte kód, pokud závisí na vlastnosti <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> vracející výchozí hodnotu 2,0.

#### <a name="category"></a>Kategorie

Sítě

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-->
