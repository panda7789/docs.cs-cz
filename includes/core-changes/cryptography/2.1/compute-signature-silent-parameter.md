---
ms.openlocfilehash: 9583d868ee01117d7bd6e465e7d89a734489d1a8
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449211"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a>Je respektován logický parametr SignedCms. ComputeSignature.

V rozhraní .NET Core je respektován logický `silent` parametr <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> metody. Pokud je tento parametr nastaven na `true`, nezobrazuje se výzva k zadání kódu PIN.

#### <a name="change-description"></a>Změnit popis

V .NET Framework se parametr `silent` <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> metody ignoruje a výzva k zadání kódu PIN je vždy zobrazená, pokud to vyžaduje poskytovatel. V rozhraní .NET Core je dodržen parametr `silent` a pokud je nastavená `true`, výzva k zadání kódu PIN se nikdy nezobrazuje, i když ho poskytovatel požaduje.

Podpora pro zprávy CMS/PKCS #7 byla představena do .NET Core ve verzi 2,1.

#### <a name="version-introduced"></a>Představená verze

2.1

#### <a name="recommended-action"></a>Doporučená akce

Aby se v případě potřeby zobrazila výzva k zadání kódu PIN, aplikace klasické pracovní plochy by měly volat <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> a nastavit parametr Boolean na `false`. Výsledné chování je stejné jako u .NET Framework bez ohledu na to, jestli je v tichém kontextu zakázaný kontext.

### <a name="category"></a>Kategorie

Kryptografie

### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
