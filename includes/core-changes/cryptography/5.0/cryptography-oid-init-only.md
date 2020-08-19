---
ms.openlocfilehash: cf51d5f6b3eee7189fd9613b3d780a829d197a04
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557998"
---
### <a name="systemsecuritycryptographyoid-is-functionally-init-only"></a>System. Security. Cryptography. OID je funkčně funkční jenom pro inicializaci.

<xref:System.Security.Cryptography.Oid?displayProperty=fullName>Třída, která se používá k reprezentaci hodnot identifikátoru objektu ASN. 1 a jejich "" přívětivých "názvů, byla dříve úplně proměnlivá. Tento proměnlivost byl často přepsaný nebo byl neočekávaně. Vlastnost Setters nyní vyvolá <xref:System.PlatformNotSupportedException> při pokusu o změnu hodnoty poté, co je již přiřazena.

#### <a name="change-description"></a>Popis změny

V předchozích verzích lze metody set vlastnosti <xref:System.Security.Cryptography.Oid> použít pro změnu hodnoty <xref:System.Security.Cryptography.Oid.FriendlyName> <xref:System.Security.Cryptography.Oid.Value> vlastností a.

V rozhraní .NET 5,0 a novějších verzích lze třídy setter použít pouze k inicializaci hodnoty. Jakmile má vlastnost hodnotu, buď z konstruktoru nebo předchozího volání metody setter vlastnosti, metoda setter vlastnosti vždy vyvolá <xref:System.PlatformNotSupportedException> .

#### <a name="reason-for-change"></a>Důvod změny

Tato změna umožňuje znovu použít <xref:System.Security.Cryptography.Oid> objekty jako součást vrácených hodnot ve veřejných rozhraních API pro omezení profilů přidělení objektů. Nemusíte vytvářet dočasné kopie "obrannou linií", když <xref:System.Security.Cryptography.Oid> se hodnoty používají jako vstupy.

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 8

#### <a name="recommended-action"></a>Doporučená akce

Vyhněte se použití <xref:System.Security.Cryptography.Oid> jiných nastavení vlastností než pro inicializaci objektu. Chcete-li reprezentovat novou hodnotu, místo změny hodnoty u existujícího objektu použijte novou instanci.

#### <a name="category"></a>Kategorie

Kryptografie

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Security.Cryptography.Oid.FriendlyName?displayProperty=fullName>
- <xref:System.Security.Cryptography.Oid.Value?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Security.Cryptography.Oid.FriendlyName`
- `P:System.Security.Cryptography.Oid.Value`

-->
