---
title: Vytvoření komplexní mřížky
description: Příklad, jak používat ovládací prvek mřížky vytvořit rozložení, který vypadá jako měsíční kalendář.
ms.date: 03/30/2017
helpviewer_keywords:
- calendar [WPF], creating
- monthly calendar [WPF], creating
- Grid control [WPF], creating [WPF], complex grid
ms.assetid: 4ce3040a-a156-4364-9596-98ca1eca5550
ms.openlocfilehash: ab5490d608b21fe8b29a078dc1f0147f038c27a3
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645676"
---
# <a name="how-to-create-a-complex-grid"></a>Vytvoření komplexní mřížky

Tento příklad ukazuje způsob použití <xref:System.Windows.Controls.Grid> ovládacího prvku k vytvoření rozložení, který vypadá jako měsíční kalendář.

## <a name="example"></a>Příklad

Následující příklad definuje osm řádků a sloupců osm pomocí <xref:System.Windows.Controls.RowDefinition> a <xref:System.Windows.Controls.ColumnDefinition> třídy. Používá <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> a <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> připojených vlastností, spolu s <xref:System.Windows.Shapes.Rectangle> elementy, které vyplnit pozadí různých sloupců a řádků. Tento návrh je možné, protože v každá buňka může existovat více než jeden prvek <xref:System.Windows.Controls.Grid>, hlavní rozdíl mezi <xref:System.Windows.Controls.Grid> a <xref:System.Windows.Documents.Table>.

V příkladu je použit svislá přechody do <xref:System.Windows.Shapes.Shape.Fill%2A> sloupců a řádků ke zlepšení čitelnosti kalendáře a vizuální prezentace. Styl <xref:System.Windows.Controls.TextBlock> elementy reprezentují data a dny v týdnu. <xref:System.Windows.Controls.TextBlock> prvky jsou absolutně umístěné v rámci jejich buňky pomocí <xref:System.Windows.FrameworkElement.Margin%2A> vlastnosti a vlastnosti zarovnání, které jsou definované ve stylu pro aplikaci.

[!code-xaml[GridComplex#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]

Následující obrázek ukazuje výsledný ovládací prvek, přizpůsobitelné kalendáře:

![Snímek obrazovky výsledný ovládací prvek](././media/how-to-create-a-complex-grid/wpf-manual-calendar.png)

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.Grid?displayProperty=nameWithType>
- <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType>
- [Přehled malování plnými barvami a přechody](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [Přehled panelu](panels-overview.md)
- [Přehled tabulky](../advanced/table-overview.md)
