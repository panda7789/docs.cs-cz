---
ms.openlocfilehash: ac7a56dc654ef4fd966077dd25012f0c50b0fc8d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981886"
---
### <a name="horizontal-scrolling-and-virtualization"></a>Vodorovné posouvání a virtualizace

|   |   |
|---|---|
|Podrobnosti|Tato změna se vztahuje na <xref:System.Windows.Controls.ItemsControl?displayProperty=name> , který provede vlastní virtualizace ve směru kolmě směru hlavní posouvání (první příklad je <xref:System.Windows.Controls.DataGrid?displayProperty=name> s EnableColumnVirtualization =&quot;True&quot;).  Výsledek určité operace vodorovného posouvání se změnil na výsledky, které jsou mnohem intuitivnější a více obdobná výsledků srovnatelné svislé operací.<p/>Operace zahrnují &quot;přejděte sem&quot; a &quot;pravý okraj&quot;, používat názvy z nabídky získali kliknutím pravým tlačítkem myši vodorovný posuvník.  Obě tyto výpočty posun Release candidate a volání <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)>.<p/>Po posouvání nové posun pojem &quot;tady&quot; nebo &quot;pravého&quot; možná změnily, protože nově zrušit virtualizované obsahu došlo ke změně hodnoty <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name>.<p/>Před rozhraní .NET Framework 4.6.2, operace posuvníku jednoduše používá Release candidate posun, i když nemusí být &quot;tady&quot; nebo &quot;pravého&quot; víc.  Výsledkem je efekty, jako jsou &quot;skákání&quot; posuvníku jezdce, nejlepší znázorněno v příkladu. Předpokládejme, že <xref:System.Windows.Controls.DataGrid?displayProperty=name> má ExtentWidth = 1 000 a šířku = 200.  Přejděte do &quot;pravý okraj&quot; Release candidate používá posun 1000 200 = 800.  Nové sloupce jsou při posouvání na tento posun, de-virtualizované; Předpokládejme, že jsou velmi široké, tak, aby <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name> změní na 2000.  Posuvníku končí HorizontalOffset = 800 a jezdce &quot;nedoručitelných zpráv&quot; zpět do středu posuvník - přesně v 800/2000 = 40 %.<p/>Změna je přepočtu nového kandidáta posun, když dojde k této situaci a zkuste to znovu. (To je jak svislé posouvání funguje již.) <p/>Změna vytvoří zajišťuje předvídatelný a intuitivní prostředí pro koncové uživatele, ale může také ovlivnit jakékoli aplikaci, která závisí na přesná hodnota <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=name> po vodorovného posouvání, zda vyvolat koncovým uživatelem nebo explicitní volání konstruktoru <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)>.|
|Doporučení|Aplikaci, která využívá předpovězené hodnoty pro <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=name> by měla být změněna načíst skutečnou hodnotu (a hodnota <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name>) po vodorovné rolovací, který by mohl změnit <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name> kvůli uvolnění virtualizace.|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.Primitives.IScrollInfo?displayProperty=nameWithType></li></ul>|
