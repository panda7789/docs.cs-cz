---
ms.openlocfilehash: 9c3c0bf7fbd8d45eba84eaa8634fd2d834195702
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617209"
---
### <a name="systemuri-parsing-adheres-to-rfc-3987"></a>Analýza System. URI dodržuje specifikaci RFC 3987.

#### <a name="details"></a>Podrobnosti

Analýza identifikátoru URI se změnila několika způsoby v .NET Framework 4,5. Všimněte si ale, že tyto změny ovlivní jenom cílení kódu .NET Framework 4,5. Pokud jsou v binárním cíli .NET Framework 4,0, bude zjištěno staré chování. Změny analýzy identifikátorů URI v .NET Framework 4,5 zahrnují:

- Analýza identifikátoru URI provede normalizaci a kontrolu znaku podle nejnovějších pravidel IRI v dokumentu RFC 3987.
- Normalizovaná forma kódu Unicode C bude provedena pouze v části hostitele identifikátoru URI.
- Neplatné mailto: identifikátory URI teď způsobí výjimku.
- Koncové tečky na konci segmentu cesty jsou nyní zachované.
- `file://`Identifikátory URI neřídí `?` znak.
- Řídicí znaky Unicode `U+0080` prostřednictvím `U+009F` se nepodporují.
- Čárky `,` nebo nejsou `%2c` automaticky bez řídicích znaků.

#### <a name="suggestion"></a>Návrh

Pokud jsou nezbytné sémantiky analýzy identifikátorů URI .NET Framework 4,0 (často nejsou), mohou být použity při cílení na .NET Framework 4,0. To lze provést pomocí nástroje <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> na sestavení nebo prostřednictvím uživatelského rozhraní systému projektu sady Visual Studio na stránce vlastností projektu.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Hlavní       |
| Verze | 4.5         |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Uri.%23ctor(System.String)>
- <xref:System.Uri.%23ctor(System.String,System.Boolean)>
- <xref:System.Uri.%23ctor(System.String,System.UriKind)>
- <xref:System.Uri.%23ctor(System.Uri,System.String)>
- <xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType>
