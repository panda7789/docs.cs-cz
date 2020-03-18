---
ms.openlocfilehash: 9583d868ee01117d7bd6e465e7d89a734489d1a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449211"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a>Logický parametr SignedCms.ComputeSignature je respektován

V .NET Core je `silent` respektován <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> logický parametr metody. Pokud je tento parametr nastaven na `true`hodnotu , nezobrazí se výzva kódu PIN.

#### <a name="change-description"></a>Popis změny

V rozhraní .NET `silent` Framework <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> je parametr metody ignorován a výzva pin ukázne vždy, pokud to vyžaduje zprostředkovatel. V .NET Core `silent` je parametr respektován a `true`pokud je nastavena na , výzva PIN se nikdy nezobrazí, i když je vyžadována zprostředkovatelem.

Podpora zpráv CMS/PKCS #7 byla zavedena do rozhraní .NET Core ve verzi 2.1.

#### <a name="version-introduced"></a>Zavedená verze

2.1

#### <a name="recommended-action"></a>Doporučená akce

Chcete-li zajistit, aby se v <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> případě potřeby zobrazila výzva s kódem PIN, měly by aplikace klasické pracovní plochy volat a nastavit logický parametr na `false`hodnotu . Výsledné chování je stejné jako na rozhraní .NET Framework bez ohledu na to, zda je zakázán tichý kontext.

### <a name="category"></a>Kategorie

Kryptografie

### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
