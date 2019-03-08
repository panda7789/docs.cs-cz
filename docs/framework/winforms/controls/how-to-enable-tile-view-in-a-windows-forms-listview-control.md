---
title: 'Postupy: Povolení zobrazení Tile v ovládacím prvku Windows Forms ListView'
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
ms.openlocfilehash: 4bc5a9dfc17acc453030c6213b9c76572d21c474
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675807"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a>Postupy: Povolení zobrazení Tile v ovládacím prvku Windows Forms ListView
S funkcí zobrazení dlaždice <xref:System.Windows.Forms.ListView> ovládacího prvku, můžete zadat vizuální rovnováhu mezi textové a grafické informace. Textové informace zobrazené položky v zobrazení tile je stejný jako sloupec informace definované pro zobrazení podrobností. Zobrazení Tile funguje v kombinaci s funkcemi označit seskupení nebo vložení ve <xref:System.Windows.Forms.ListView> ovládacího prvku.  
  
 Zobrazení tile používá ikony 32 x 32 pixelů a několik řádků textu, jak je znázorněno na následujících obrázcích.  
  
 ![Dlaždice zobrazení v ovládacím prvku ListView](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "dlaždici zobrazení ikon a textu")  
  
  
 Chcete-li povolit zobrazení tile, nastavte <xref:System.Windows.Forms.ListView.View%2A> vlastnost <xref:System.Windows.Forms.View.Tile>. Můžete nastavit velikost dlaždic tak, že nastavíte <xref:System.Windows.Forms.ListView.TileSize%2A> vlastnost a počet řádků textu se zobrazí na dlaždici úpravou <xref:System.Windows.Forms.ListView.Columns%2A> kolekce.  
  
> [!NOTE]
>  Je k dispozici pouze v zobrazení tile [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] když vaše aplikace volá <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody. Ve starších operačních systémech, jakýkoli kód související s zobrazení tile nemá žádný účinek a <xref:System.Windows.Forms.ListView> ovládací prvek zobrazí v zobrazení LargeIcon. Další informace naleznete v tématu <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.  
  
### <a name="to-set-tile-view-programmatically"></a>Chcete-li nastavit zobrazení tile prostřednictvím kódu programu  
  
1.  Použití <xref:System.Windows.Forms.View> výčet <xref:System.Windows.Forms.ListView> ovládacího prvku.  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a>Příklad  
 Následující příklad kompletní kód ukazuje zobrazení Tile s dlaždicemi, které upravit tak, aby zobrazit tři řádky textu. Aby se zabránilo zalomení řádku bylo změněno velikosti dlaždice.  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému a System.Windows.Forms.  
  
-   Soubor ikony s názvem book.ico ve stejném adresáři jako spustitelný soubor.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [Ovládací prvek ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
- [Přehled ovládacího prvku ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
