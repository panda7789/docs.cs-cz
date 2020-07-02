---
ms.openlocfilehash: 171b7a3a962f8259e64b88f1ae893e649b5f24bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621106"
---
### <a name="chained-popups-with-staysopenfalse"></a>Zřetězené automaticky otevírané okno s nastavením StaysOpen = false

#### <a name="details"></a>Podrobnosti

Místní nabídka s nastavením StaysOpen = false by se měla zavřít po kliknutí mimo místní nabídku. V případě zřetězení dvou nebo více překryvných oken (tj. jeden obsahuje jiný) existuje mnoho problémů, včetně:<ul><li>Otevřete dvě úrovně, klikněte na mimo P2, ale uvnitř P1.  Nic se nestane.</li><li>Otevřete dvě úrovně a klikněte mimo P1.  Obě automaticky otevíraná okna se zavřou.</li><li>Otevřete a zavřete dvě úrovně.  Pak zkuste znovu otevřít P2.  Nic se nestane.</li><li>Zkuste otevřít tři úrovně.  Nemůžete.  (Buď nic nenastane, nebo první dvě úrovně se zavřou, podle toho, kde kliknete.) Tyto případy (a jiné varianty) teď fungují podle očekávání.</li></ul>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.7.1|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|
