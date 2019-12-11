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
ms.openlocfilehash: 489b9a9d0341391c756175acb19d962d642eb7b2
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960446"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a>Postupy: Povolení zobrazení Vedle sebe v ovládacím prvku Windows Forms ListView
Pomocí funkce zobrazení dlaždice ovládacího prvku <xref:System.Windows.Forms.ListView> můžete zadat vizuální vyvážení mezi grafickými a textovými informacemi. Textové informace zobrazené pro položku v zobrazení dlaždic jsou stejné jako informace o sloupci definované pro zobrazení podrobností. Zobrazení dlaždic funguje v kombinaci s funkcemi seskupení nebo vložení pomocí značek v ovládacím prvku <xref:System.Windows.Forms.ListView>.  
  
 V zobrazení dlaždice se používá ikona 32 x 32 pixelů a několik řádků textu, jak je znázorněno na následujících obrázcích.  
  
 ![Zobrazení dlaždic v ovládacím prvku ListView](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Ikony a text dlaždicového zobrazení")  
 
 Chcete-li povolit zobrazení dlaždic, nastavte vlastnost <xref:System.Windows.Forms.ListView.View%2A> na hodnotu <xref:System.Windows.Forms.View.Tile>. Velikost dlaždic můžete upravit nastavením vlastnosti <xref:System.Windows.Forms.ListView.TileSize%2A> a počtu řádků textu zobrazených na dlaždici úpravou kolekce <xref:System.Windows.Forms.ListView.Columns%2A>.  
  
### <a name="to-set-tile-view-programmatically"></a>Postup při nastavování zobrazení dlaždic prostřednictvím kódu programu  
  
1. Použijte <xref:System.Windows.Forms.View> výčtu ovládacího prvku <xref:System.Windows.Forms.ListView>.  
  
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
