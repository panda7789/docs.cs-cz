---
ms.openlocfilehash: 51208762cea2a5688c5d43e5d444d4e014e5f0b4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621139"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>X509Certificate2. ToString (Boolean) nevrátí hodnotu Now, pokud rozhraní .NET nemůže zpracovat certifikát.

#### <a name="details"></a>Podrobnosti

V .NET Framework 4.5.2 a starších verzích vyvolala Tato metoda, pokud <code>true</code> byla předána parametru verbose, a nainstalují se certifikáty, které nepodporovala .NET Framework. Nyní bude metoda úspěšná a vrátí platný řetězec, který vynechá nepřístupné části certifikátu.

#### <a name="suggestion"></a>Návrh

Jakýkoli kód, který závisí na <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> tom, by měl být aktualizován, aby bylo možné očekávat, že vrácený řetězec může vyloučit některá data certifikátu (například veřejný klíč, privátní klíč a rozšíření) v některých případech, kdy by předtím bylo vyvoláno rozhraní API.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.6|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|
