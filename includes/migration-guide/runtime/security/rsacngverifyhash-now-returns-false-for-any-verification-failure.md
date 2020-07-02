---
ms.openlocfilehash: fa5cf2280cdd9535962568a6272d047d261eeba5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621082"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a>Algoritmem RSACng. VerifyHash teď pro jakékoli selhání ověřování vrátí hodnotu false.

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4.6.2 vrátí tato metoda **hodnotu false** , pokud samotný podpis není správně naformátován. Nyní vrátí hodnotu false pro jakékoli selhání ověřování. V .NET Framework 4,6 a 4.6.1 metoda vyvolá výjimku, <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> Pokud samotný podpis není správně naformátován.

#### <a name="suggestion"></a>Návrh

Jakýkoli kód, jehož provádění závisí na zpracování, je <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> třeba provést, pokud se ověření nepovede a metoda vrátí **hodnotu false**.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.6.2|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
