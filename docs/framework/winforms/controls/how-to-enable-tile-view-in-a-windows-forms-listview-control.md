---
title: 'Postupy: Povolení zobrazení Vedle sebe v ovládacím prvku Windows Forms ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tile view feature
- tiling
- Windows Forms, controls
- ListView control [Windows Forms], tile view
ms.assetid: c20e67a3-2d94-413d-9fcf-ecbd0fe251da
ms.openlocfilehash: 44d34ddb00005a0fb86b2d06c4c14e2a5b949819
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966680"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a>Postupy: Povolení zobrazení Vedle sebe v ovládacím prvku Windows Forms ListView
Pomocí funkce <xref:System.Windows.Forms.ListView> zobrazení dlaždic v ovládacím prvku můžete zadat vizuální vyvážení mezi grafickými a textovými informacemi. Textové informace zobrazené pro položku v zobrazení dlaždic jsou stejné jako informace o sloupci definované pro zobrazení podrobností. Zobrazení dlaždic funguje v kombinaci s funkcemi seskupení nebo vložení v <xref:System.Windows.Forms.ListView> ovládacím prvku.  
  
 V zobrazení dlaždice se používá ikona 32 x 32 pixelů a několik řádků textu, jak je znázorněno na následujících obrázcích.  
  
 ![Zobrazení dlaždic v ovládacím prvku ListView](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Ikony a text dlaždicového zobrazení")  
 
 Chcete-li povolit zobrazení dlaždic, <xref:System.Windows.Forms.ListView.View%2A> nastavte vlastnost <xref:System.Windows.Forms.View.Tile>na hodnotu. Velikost dlaždic můžete upravit nastavením <xref:System.Windows.Forms.ListView.TileSize%2A> vlastnosti a počtu řádků textu zobrazených v dlaždici <xref:System.Windows.Forms.ListView.Columns%2A> úpravou kolekce.  
  
> [!NOTE]
> Zobrazení dlaždice je k dispozici pouze [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] v případě, <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> že vaše aplikace volá metodu. V předchozích operačních systémech nemá žádný vliv žádný kód související s zobrazením dlaždice a <xref:System.Windows.Forms.ListView> ovládací prvek se zobrazí v zobrazení velkých ikon. Další informace naleznete v tématu <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.  
  
### <a name="to-set-tile-view-programmatically"></a>Postup při nastavování zobrazení dlaždic prostřednictvím kódu programu  
  
1. <xref:System.Windows.Forms.View> Použijte výčet <xref:System.Windows.Forms.ListView> ovládacího prvku.  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a>Příklad  
 Následující kompletní příklad kódu ukazuje zobrazení dlaždic s upravenými dlaždicemi pro zobrazení tří řádků textu. Velikost dlaždice byla upravena, aby se zabránilo zalamování řádků.  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System a System. Windows. Forms.  
  
- Soubor ikony s názvem book. ico ve stejném adresáři jako spustitelný soubor.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [Ovládací prvek ListView](listview-control-windows-forms.md)
- [Přehled ovládacího prvku ListView](listview-control-overview-windows-forms.md)
