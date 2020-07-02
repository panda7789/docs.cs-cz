---
ms.openlocfilehash: e9d34465970287ed94c0f0373ee4ae94d55aa1ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617181"
---
### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a>Metody MachineKey. Encode a MachineKey. dekódování jsou nyní zastaralé.

#### <a name="details"></a>Podrobnosti

Tyto metody jsou nyní zastaralé. Kompilace kódu volající tyto metody vede k upozornění překladače.

#### <a name="suggestion"></a>Návrh

Doporučené alternativy jsou <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> a <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])> . Alternativně lze upozornění sestavení potlačit, nebo je lze zabránit pomocí staršího kompilátoru. Rozhraní API jsou pořád podporovaná.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.5         |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType>
- <xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType>
