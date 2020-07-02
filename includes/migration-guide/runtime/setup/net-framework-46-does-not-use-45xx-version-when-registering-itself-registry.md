---
ms.openlocfilehash: 09fb7a54fccd5cf37800483c64e2fa6a54681f11
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621142"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a>.NET Framework 4,6 nepoužívá při registraci sebe v registru verzi 4.5. x. x.

#### <a name="details"></a>Podrobnosti

Jak to může očekávat, klíč verze nastavený v registru (on <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code> ) pro .NET Framework 4,6 začíná na ' 4,6 ', nikoli ' 4,5 '. Aplikace, které jsou na těchto klíčích registru závislé na tom, aby věděli, které .NET Framework verze jsou nainstalované na počítači, by měly být aktualizované, aby zjistili, že 4,6 je nová možná verze a ta, která je kompatibilní s předchozími verzemi 4.5. x.

#### <a name="suggestion"></a>Návrh

Aktualizujte aplikace zjišťováním pro instalaci .NET Framework 4,5, a to tak, že vyhledáte 4,5 klíče registru, abyste mohli taky přijmout 4,6.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.6|
|Typ|Modul runtime|
