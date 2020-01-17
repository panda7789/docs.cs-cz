---
ms.openlocfilehash: 9aff20e35469f9e786f0f790fda4ffaa04e76e64
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116414"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>Výchozí hodnota zprávy HttpRequestMessage. Version se změnila na 1,1.

Výchozí hodnota vlastnosti <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> se změnila z 2,0 na 1,1.

#### <a name="version-introduced"></a>Představená verze

.NET Core 3.0

#### <a name="change-description"></a>Popis změny

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

-->
