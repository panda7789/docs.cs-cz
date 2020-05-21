---
ms.openlocfilehash: b861dbaa02c97a03c015fdf4e63d25c40c90ea0a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721710"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a>Je respektován logický parametr SignedCms. ComputeSignature.

V .NET Core `silent` <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> je respektován parametr Boolean metody. Pokud je tento parametr nastaven na hodnotu, není zobrazena výzva k zadání kódu PIN `true` .

#### <a name="change-description"></a>Popis změny

V .NET Framework `silent` parametr <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> metody je ignorován a výzva k zadání kódu PIN je vždy zobrazena, pokud to vyžaduje poskytovatel. V .NET Core je `silent` parametr dodržen a pokud je nastaven na `true` , výzva k zadání kódu PIN se nikdy nezobrazuje, i když ho poskytovatel požaduje.

Podpora pro zprávy CMS/PKCS #7 byla představena do .NET Core ve verzi 2,1.

#### <a name="version-introduced"></a>Představená verze

2.1

#### <a name="recommended-action"></a>Doporučená akce

Aby se v případě potřeby zobrazila výzva k zadání kódu PIN, aplikace klasické pracovní plochy by měla zavolat <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> a nastavit parametr Boolean na `false` . Výsledné chování je stejné jako u .NET Framework bez ohledu na to, jestli je v tichém kontextu zakázaný kontext.

#### <a name="category"></a>Kategorie

Kryptografie

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
