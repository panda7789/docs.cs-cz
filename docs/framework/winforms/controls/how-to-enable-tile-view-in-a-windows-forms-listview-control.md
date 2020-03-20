---
title: Povolení zobrazení dlaždic v ovládacím prvku ListView
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
ms.openlocfilehash: 1478ba5e4f175cd7d9ec7ab5c3c4bc9050ce02fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182156"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a>Postupy: Povolení zobrazení Vedle sebe v ovládacím prvku Windows Forms ListView
Pomocí funkce zobrazení dlaždic <xref:System.Windows.Forms.ListView> ovládacího prvku můžete zajistit vizuální rovnováhu mezi grafickými a textovými informacemi. Textové informace zobrazené pro položku v zobrazení dlaždic jsou stejné jako informace o sloupci definované pro zobrazení podrobností. Zobrazení dlaždic funguje v kombinaci s prvky seskupení <xref:System.Windows.Forms.ListView> nebo značky vložení v ovládacím prvku.  
  
 Zobrazení dlaždic používá ikonu 32 x 32 pixelů a několik řádků textu, jak je znázorněno na následujících obrázcích.  
  
 ![Zobrazení dlaždic v ovládacím prvku ListView](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Ikony a text zobrazení dlaždic")  

 Chcete-li povolit <xref:System.Windows.Forms.ListView.View%2A> zobrazení <xref:System.Windows.Forms.View.Tile>dlaždic, nastavte vlastnost na . Velikost dlaždic můžete upravit nastavením <xref:System.Windows.Forms.ListView.TileSize%2A> vlastnosti a počtu řádků textu zobrazených na dlaždici úpravou <xref:System.Windows.Forms.ListView.Columns%2A> kolekce.  
  
### <a name="to-set-tile-view-programmatically"></a>Nastavení zobrazení dlaždic programově  
  
1. Použijte <xref:System.Windows.Forms.View> výčet ovládacího <xref:System.Windows.Forms.ListView> prvku.  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a>Příklad  
 Následující příklad úplného kódu ukazuje zobrazení dlaždic s dlaždicemi upravenými tak, aby zobrazovaly tři řádky textu. Velikost dlaždice byla upravena tak, aby se zabránilo zalamování řádků.  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení Systém u systému a systému.Windows.Forms.  
  
- Soubor ikon s názvem book.ico ve stejném adresáři jako spustitelný soubor.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [ListView – ovládací prvek](listview-control-windows-forms.md)
- [ListView – přehled ovládacího prvku](listview-control-overview-windows-forms.md)
