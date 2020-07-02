---
ms.openlocfilehash: c996dafcf65b1fd428be908be346de603ead6e0b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615678"
---
### <a name="certificate-eku-oid-validation"></a>Ověřování IDENTIFIKÁTORu klíče EKU certifikátu

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4,6 <xref:System.Net.Security.SslStream> <xref:System.Net.ServicePointManager> třídy nebo provádějí ověřování identifikátoru objektu (OID) pomocí rozšířeného použití klíče (EKU). Rozšíření rozšířené použití klíče (EKU) je kolekce identifikátorů objektů (OID), které označují aplikace, které klíč používají. Ověřování OID rozšířeného použití klíče používá zpětná volání vzdáleného certifikátu, aby se zajistilo, že vzdálený certifikát má správné identifikátory OID pro zamýšlený účel.

#### <a name="suggestion"></a>Návrh

Pokud je tato změna nežádoucí, můžete ověření IDENTIFIKÁTORu klíče rozšířeného použití certifikátu zakázat přidáním následujícího přepínače do [\<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) [`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontCheckCertificateEKUs=true" />
</runtime>
```

> [!IMPORTANT]
> Toto nastavení je k dispozici pouze pro zpětnou kompatibilitu. Jeho použití není jinak doporučeno.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.6         |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.ServicePointManager?displayProperty=nameWithType>
- <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
