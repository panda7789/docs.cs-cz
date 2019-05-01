---
ms.openlocfilehash: 77e04333ed2b9a5ca8b900c1355fb5b12957772d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62088475"
---
### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a>MachineKey.Encode a MachineKey.Decode metody jsou nyní zastaralé

|   |   |
|---|---|
|Podrobnosti|Tyto metody jsou nyní zastaralé. Kompilace kódu volající tyto metody vede k upozornění překladače.|
|Doporučení|Doporučené alternativy jsou <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> a <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>. Alternativně lze potlačit upozornění sestavení nebo lze se vyhnout pomocí staršího kompilátoru. Rozhraní API jsou stále podporovány.|
|Rozsah|Vedlejší|
|Version|4.5|
|Type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li><li><xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li></ul>|
