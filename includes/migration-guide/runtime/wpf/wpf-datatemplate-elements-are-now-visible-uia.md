---
ms.openlocfilehash: 06c699281c8890ac65be1d282b72b54774acc280
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620101"
---
### <a name="wpf-datatemplate-elements-are-now-visible-to-uia"></a>Prvky WPF DataTemplate jsou teď viditelné pro UIA

#### <a name="details"></a>Podrobnosti

Dříve <xref:System.Windows.DataTemplate?displayProperty=fullName> byly elementy pro automatizaci uživatelského rozhraní neviditelné. Počínaje 4,5 bude automatizace uživatelského rozhraní detekovat tyto prvky. To je užitečné v mnoha případech, ale může přerušit testy závislé na UIA stromech, které neobsahují <xref:System.Windows.DataTemplate?displayProperty=fullName> prvky.

#### <a name="suggestion"></a>Návrh

Testy pro automatizaci uživatelského rozhraní pro tuto aplikaci se možná budou muset aktualizovat na účet UIA stromu hned včetně dříve neviditelných <xref:System.Windows.DataTemplate?displayProperty=fullName> prvků. Například testy, které očekávají, že některé prvky jsou vedle sebe, mohou nyní potřebovat očekávat dříve neviditelné prvky UIA v mezi. Nebo testy, které spoléhají na určité počty nebo indexy pro prvky UIA, mohou vyžadovat aktualizaci novými hodnotami.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Windows.DataTemplate.%23ctor></li><li><xref:System.Windows.DataTemplate.%23ctor(System.Object)></li></ul>|
