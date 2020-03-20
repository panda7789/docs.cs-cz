---
title: Přizpůsobení buněk a sloupců v ovládacím prvku DataGridView rozšířením jejich chování a vzhledu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- columns [Windows Forms], customizing in DataGridView control
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 9b7dc7b6-5ce6-4566-9949-902f74f17a81
ms.openlocfilehash: e111f0bce812fc0851fabd1fde0fc2a6d44dd25f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182395"
---
# <a name="how-to-customize-cells-and-columns-in-the-windows-forms-datagridview-control-by-extending-their-behavior-and-appearance"></a>Postupy: Přizpůsobení buněk a sloupců v ovládacím prvku Windows Forms DataGridView rozšířením jeho chování a vzhledu
Ovládací <xref:System.Windows.Forms.DataGridView> prvek poskytuje řadu způsobů, jak přizpůsobit jeho vzhled a chování pomocí vlastností, událostí a doprovodné třídy. V některých případě můžete mít požadavky na buňky, které jdou nad rámec toho, co tyto funkce mohou poskytnout. Můžete vytvořit vlastní <xref:System.Windows.Forms.DataGridViewCell> třídu, která poskytuje rozšířené funkce.  
  
 Vlastní <xref:System.Windows.Forms.DataGridViewCell> třídu vytvoříte odvozením <xref:System.Windows.Forms.DataGridViewCell> ze základní třídy nebo jedné z jejích odvozených tříd. Přestože můžete zobrazit libovolný typ buňky v libovolném typu sloupce, obvykle také vytvoříte vlastní <xref:System.Windows.Forms.DataGridViewColumn> třídu specializovanou na zobrazení typu buňky. Třídy sloupců jsou odvozeny z <xref:System.Windows.Forms.DataGridViewColumn> nebo z jednoho z jeho odvozených typů.  
  
 V následujícím příkladu kódu vytvoříte vlastní `DataGridViewRolloverCell` třídu buněk, která zjistí, kdy myš zadá a opustí hranice buňky. Zatímco myš je v rámci hranice buňky, je nakreslena obdélník vsazení. Tento nový typ <xref:System.Windows.Forms.DataGridViewTextBoxCell> je odvozen a chová se ve všech ostatních ohledech jako jeho základní třídy. Doprovodná třída sloupce `DataGridViewRolloverColumn`se nazývá .  
  
 Chcete-li použít tyto třídy, <xref:System.Windows.Forms.DataGridView> vytvořte formulář `DataGridViewRolloverColumn` obsahující ovládací <xref:System.Windows.Forms.DataGridView.Columns%2A> prvek, přidejte jeden nebo více objektů do kolekce a naplňte ovládací prvek řádky obsahujícími hodnoty.  
  
> [!NOTE]
> Tento příklad nebude fungovat správně, pokud přidáte prázdné řádky. Prázdné řádky jsou vytvořeny, například při přidání řádků <xref:System.Windows.Forms.DataGridView.RowCount%2A> do ovládacího prvku nastavením vlastnosti. Důvodem je, že řádky přidané v tomto `DataGridViewRolloverCell` případě jsou automaticky sdíleny, což znamená, že objekty nejsou vytvářeny, dokud nekliknete na jednotlivé buňky, což způsobí, že přidružené řádky budou nesdílené.  
  
 Vzhledem k tomu, že tento typ přizpůsobení buněk vyžaduje nesdílené řádky, není vhodný pro použití s velkými datovými sadami. Další informace o sdílení řádků naleznete v [tématu Doporučené postupy pro změnu měřítka ovládacího prvku DataGridView pro formuláře systému Windows](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
> [!NOTE]
> Při odvození <xref:System.Windows.Forms.DataGridViewCell> <xref:System.Windows.Forms.DataGridViewColumn> z nebo a přidat nové vlastnosti do odvozené třídy, nezapomeňte přepsat metodu `Clone` zkopírovat nové vlastnosti během klonování operace. Měli byste také volat `Clone` metodu základní třídy tak, aby vlastnosti základní třídy byly zkopírovány do nové buňky nebo sloupce.  
  
### <a name="to-customize-cells-and-columns-in-the-datagridview-control"></a>Přizpůsobení buněk a sloupců v ovládacím prvku DataGridView  
  
1. Odvodit novou `DataGridViewRolloverCell`třídu <xref:System.Windows.Forms.DataGridViewTextBoxCell> buňky, nazývanou , z typu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#201)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#201)]  
    [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#202)]
    [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#202)]  
  
2. Přepsat metodu <xref:System.Windows.Forms.DataGridViewTextBoxCell.Paint%2A> ve `DataGridViewRolloverCell` třídě. V přepsání nejprve volání implementace základní třídy, která zpracovává funkce hostovaného textového pole. Potom pomocí metody <xref:System.Windows.Forms.Control.PointToClient%2A> ovládacího prvku transformujte pozici kurzoru <xref:System.Windows.Forms.DataGridView> (v souřadnicích obrazovky) na souřadnice klientské oblasti. Pokud souřadnice myši spadají do hranice buňky, nakreslete vsazený obdélník.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#210)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#210)]  
  
3. Přepsat <xref:System.Windows.Forms.DataGridViewCell.OnMouseEnter%2A> metody <xref:System.Windows.Forms.DataGridViewCell.OnMouseLeave%2A> a ve `DataGridViewRolloverCell` třídě vynutit buňky překreslit sami, když ukazatel myši vstoupí nebo opustí je.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#220)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#220)]  
  
4. Odvodit novou `DataGridViewRolloverCellColumn`třídu, nazvanou , z typu. <xref:System.Windows.Forms.DataGridViewColumn> V konstruktoru přiřaďte `DataGridViewRolloverCell` <xref:System.Windows.Forms.DataGridViewColumn.CellTemplate%2A> nový objekt k jeho vlastnosti.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#300)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#300)]  
  
## <a name="example"></a>Příklad  
 Kompletní příklad kódu obsahuje malý testovací formulář, který demonstruje chování vlastního typu buňky.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#000)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavy System, System.Windows.Forms a System.Drawing.  

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Přizpůsobení ovládacího prvku Windows Forms DataGridView](customizing-the-windows-forms-datagridview-control.md)
- [Architektura ovládacího prvku DataGridView](datagridview-control-architecture-windows-forms.md)
- [Typy sloupců v ovládacím prvku Windows Forms DataGridView](column-types-in-the-windows-forms-datagridview-control.md)
- [Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
