---
title: 'Postupy: Zobrazení značky vložení v ovládacím prvku Windows Forms ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ListView control [Windows Forms], drag operations
- graphics [Windows Forms], insertion marks
- drop and drag [Windows Forms], insertion marks
- insertion marks
ms.assetid: 88d0a15b-25fd-4dc3-a685-297351311940
ms.openlocfilehash: 6c87a4cb68baa15b5f670a23fb4e8ef7ce16cf6f
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710053"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a>Postupy: Zobrazení značky vložení v ovládacím prvku Windows Forms ListView
Značky vložení v <xref:System.Windows.Forms.ListView> ovládací prvek zobrazuje uživatele, kteří bodu vloženy Přetahované položky. Když uživatel přetáhne položku do bodu mezi dvě další položky, značky vložení ukazuje očekávané nové umístění položky.  
  
> [!NOTE]
>  Označit funkce vložení dostupná pouze na [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] když vaše aplikace volá <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody. Ve starších operačních systémech jakýkoli kód týkající se značky vložení nemá žádný vliv a značky vložení nezobrazí. Další informace naleznete v tématu <xref:System.Windows.Forms.ListViewInsertionMark>.  
  
 Následující obrázek ukazuje značky vložení:  
  
 ![Značky vložení ListView](./media/listviewinsertion.gif "ListViewInsertion")  
  
 Následující příklad kódu ukazuje, jak tuto funkci používat.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému a System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewInsertionMark>
- [Ovládací prvek ListView](listview-control-windows-forms.md)
- [Přehled ovládacího prvku ListView](listview-control-overview-windows-forms.md)
- [Návod: Operace a přetažení ve Windows Forms](../advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
