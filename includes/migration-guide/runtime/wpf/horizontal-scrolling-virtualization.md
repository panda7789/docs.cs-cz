---
ms.openlocfilehash: ac7a56dc654ef4fd966077dd25012f0c50b0fc8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857562"
---
### <a name="horizontal-scrolling-and-virtualization"></a>Vodorovné posouvání a virtualizace

|   |   |
|---|---|
|Podrobnosti|Tato změna se <xref:System.Windows.Controls.ItemsControl?displayProperty=name> vztahuje na který provádí vlastní virtualizaci ve směru ortogonální hlavní směr <xref:System.Windows.Controls.DataGrid?displayProperty=name> posouvání (hlavní&quot;&quot;příklad je s EnableColumnVirtualization = True ).  Výsledek některých operací vodorovného posouvání byl změněn tak, aby přinesl výsledky, které jsou intuitivnější a anatypičtější s výsledky srovnatelných vertikálních operací.<p/>Operace zahrnují &quot;Scroll&quot; &quot;Here&quot;a Right Edge , chcete-li použít názvy z nabídky získané klepnutím pravým tlačítkem myši na vodorovný posuvník.  Oba tyto vypočítat kandidáta <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)>posun a volání .<p/>Po posouvání na nový posun &quot;se&quot; &quot;pojem zde nebo pravý okraj&quot; mohl změnit, <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name>protože nově devirtualizovaný obsah změnil hodnotu aplikace .<p/>Před rozhraním .NET Framework 4.6.2 operace posouvání jednoduše používá odsazení kandidáta, i když &quot;nemusí být zde&quot; nebo na &quot;pravém okraji&quot; žádné další.  To má za &quot;následek&quot; efekty, jako je poskakování rolovací palec, nejlépe ilustruje příklad. Předpokládejme, <xref:System.Windows.Controls.DataGrid?displayProperty=name> že má ExtentWidth=1000 a Width=200.  Posun na &quot;pravý&quot; okraj používá odsazení kandidáta 1000 - 200 = 800.  Při posouvání na tento posun jsou nové sloupce devirtualizovány; Předpokládejme, že jsou velmi široké, <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name> takže změny na 2000.  Posun končí HorizontalOffset = 800 a &quot;palec&quot; se odrazí zpět do blízkosti středu posuvníku - přesně na 800/2000 = 40%.<p/>Změna je přepočítat nový kandidát posun, když nastane tato situace a zkuste to znovu. (Takto již funguje svislé posouvání.) <p/>Změna vytváří předvídatelnější a intuitivní prostředí pro koncového uživatele, ale může také ovlivnit všechny <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=name> aplikace, která závisí na přesnou hodnotu po <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)>vodorovném svitku, ať už vyvolána koncovým uživatelem nebo explicitní volání .|
|Návrh|Aplikace, která používá předpovídanou hodnotu pro <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=name> by měla být <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name>změněna načíst skutečnou hodnotu (a hodnotu) po jakékoli vodorovné posouvání, které by se mohlo změnit <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name> z důvodu de-virtualizace.|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.Primitives.IScrollInfo?displayProperty=nameWithType></li></ul>|
