---
ms.openlocfilehash: e92cbb7decb5e530bbf611cec26ce03a05e06eb3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622235"
---
### <a name="rsacng-and-dsacng-are-once-again-usable-in-partial-trust-scenarios"></a>Algoritmem RSACng a algoritmem dsacng jsou znovu použitelné ve scénářích s částečnou důvěryhodností.

#### <a name="details"></a>Podrobnosti

CngLightup (používá se v několika šifrovacích rozhraních API vyšší úrovně, například <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> ) a <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> v některých případech závisí na úplném vztahu důvěryhodnosti. Patří mezi ně volání nespravovaného kódu bez uplatnění <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> oprávnění a cesty kódu, kde <xref:System.Security.Cryptography.CngKey?displayProperty=nameWithType> má oprávnění požadavky <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> . Počínaje .NET Framework 4.6.2 se CngLightup použil k přepínání tam, kde je <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> to možné. V důsledku toho částečně důvěryhodné aplikace, které úspěšně používaly začátek <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> k selhání a vyvolávají <xref:System.Security.SecurityException> výjimky. Tato změna přidá požadované výrazy, aby všechny funkce využívající CngLightup měly požadovaná oprávnění.

#### <a name="suggestion"></a>Návrh

Pokud tato změna .NET Framework 4.6.2 negativně ovlivnila vaše aplikace s částečným vztahem důvěryhodnosti, upgradujte na .NET Framework 4.7.1.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.6.2|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Security.Cryptography.DSACng.%23ctor(System.Security.Cryptography.CngKey)></li><li><xref:System.Security.Cryptography.DSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.LegalKeySizes?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.CreateSignature(System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.VerifySignature(System.Byte[],System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.%23ctor(System.Security.Cryptography.CngKey)></li><li><xref:System.Security.Cryptography.RSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.Decrypt(System.Byte[],System.Security.Cryptography.RSAEncryptionPadding)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.SignHash(System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
