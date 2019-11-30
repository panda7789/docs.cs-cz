---
ms.openlocfilehash: ff156afb3da4b921517fd841c5de2295265a8d7b
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567757"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>Výchozí hodnota zprávy HttpRequestMessage. Version se změnila na 1,1.

Výchozí hodnota vlastnosti <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> se změnila z 2,0 na 1,1.

#### <a name="version-introduced"></a>Představená verze

.NET Core 3.0

#### <a name="change-description"></a>Změnit popis

V .NET Core 1,0 až 2,0 je výchozí hodnota vlastnosti <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 1,1. Počínaje .NET Core 2,1 se změnilo na 2,1.

Počínaje rozhraním .NET Core 3,0 je výchozí číslo verze vrácené vlastností <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> znovu 1,1.

#### <a name="recommended-action"></a>Doporučená akce

Aktualizujte kód, pokud závisí na vlastnosti <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> vracející výchozí hodnotu 2,0.

#### <a name="category"></a>Kategorie

Síťové služby

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--
a def
### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-- >

