---
ms.openlocfilehash: cef8096c971da8ae245ff974697022f350cb9195
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616041"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a>VB.NET už nepodporuje částečnou kvalifikaci oboru názvů pro System. rozhraní API systému Windows.

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4.5.2 nemohou projekty VB.NET určovat rozhraní API System. Windows s částečně kvalifikovanými obory názvů. Například odkaz na se `Windows.Forms.DialogResult` nezdaří. Místo toho musí kód odkazovat na plně kvalifikovaný název ( <xref:System.Windows.Forms.DialogResult> ) nebo importovat konkrétní obor názvů a odkazovat pouze na <xref:System.Windows.Forms.DialogResult?displayProperty=fullName> .

#### <a name="suggestion"></a>Návrh

Kód by měl být aktualizován, aby odkazoval na `System.Windows` rozhraní API buď pomocí jednoduchých názvů (a importu příslušného oboru názvů), nebo s plně kvalifikovanými názvy.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.5.2       |
| Typ    | Změna cílení |
