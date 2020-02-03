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
ms.openlocfilehash: be01e085d4fa74c0c49f0a0494183482875c6a09
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744070"
---
# <a name="how-to-customize-cells-and-columns-in-the-windows-forms-datagridview-control-by-extending-their-behavior-and-appearance"></a>Postupy: Přizpůsobení buněk a sloupců v ovládacím prvku Windows Forms DataGridView rozšířením jeho chování a vzhledu
Ovládací prvek <xref:System.Windows.Forms.DataGridView> poskytuje několik způsobů přizpůsobení jeho vzhledu a chování pomocí vlastností, událostí a doprovodných tříd. V některých případech je možné, že budete mít požadavky na buňky, které přesahují rámec toho, co tyto funkce poskytují. Můžete vytvořit vlastní třídu <xref:System.Windows.Forms.DataGridViewCell> pro poskytování rozšířených funkcí.  
  
 Můžete vytvořit vlastní třídu <xref:System.Windows.Forms.DataGridViewCell> Odvozením ze <xref:System.Windows.Forms.DataGridViewCell> základní třídy nebo jedné z jeho odvozených tříd. I když můžete zobrazit libovolný typ buňky v jakémkoli typu sloupce, obvykle vytvoříte také vlastní třídu <xref:System.Windows.Forms.DataGridViewColumn> specializované pro zobrazení typu buňky. Třídy sloupců jsou odvozeny z <xref:System.Windows.Forms.DataGridViewColumn> nebo jednoho z jeho odvozených typů.  
  
 V následujícím příkladu kódu vytvoříte třídu vlastní buňky s názvem `DataGridViewRolloverCell`, která se detekuje, když ukazatel myši přejde a opustí hranice buňky. I když je ukazatel myši v rámci hranice buňky, vykreslí se vsazený obdélník. Tento nový typ je odvozen z <xref:System.Windows.Forms.DataGridViewTextBoxCell> a chová se ve všech ostatních ohledech jako jeho základní třída. Třída doprovodného sloupce se nazývá `DataGridViewRolloverColumn`.  
  
 Chcete-li použít tyto třídy, vytvořte formulář obsahující ovládací prvek <xref:System.Windows.Forms.DataGridView>, do kolekce <xref:System.Windows.Forms.DataGridView.Columns%2A> přidejte jeden nebo více objektů `DataGridViewRolloverColumn` a naplňte ovládací prvek řádky obsahující hodnoty.  
  
> [!NOTE]
> Pokud přidáte prázdné řádky, tento příklad nebude fungovat správně. Jsou vytvořeny prázdné řádky, například při přidávání řádků do ovládacího prvku nastavením vlastnosti <xref:System.Windows.Forms.DataGridView.RowCount%2A>. Důvodem je to, že řádky přidané v tomto případě jsou automaticky sdíleny, což znamená, že `DataGridViewRolloverCell` objektů nebudou vytvořeny instance, dokud nekliknete na jednotlivé buňky, což způsobí, že přidružené řádky budou nesdíleny.  
  
 Vzhledem k tomu, že tento typ přizpůsobení buňky vyžaduje nesdílené řádky, není vhodné používat s velkými datovými sadami. Další informace o sdílení řádků naleznete v tématu [osvědčené postupy pro škálování ovládacího prvku DataGridView model Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
> [!NOTE]
> Při odvozování z <xref:System.Windows.Forms.DataGridViewCell> nebo <xref:System.Windows.Forms.DataGridViewColumn> a přidání nových vlastností do odvozené třídy nezapomeňte přepsat metodu `Clone` pro kopírování nových vlastností během operací klonování. Měli byste také zavolat metodu `Clone` základní třídy tak, aby byly vlastnosti základní třídy zkopírovány do nové buňky nebo sloupce.  
  
### <a name="to-customize-cells-and-columns-in-the-datagridview-control"></a>Přizpůsobení buněk a sloupců v ovládacím prvku DataGridView  
  
1. Z <xref:System.Windows.Forms.DataGridViewTextBoxCell> typu odvodit novou třídu buněk nazvanou `DataGridViewRolloverCell`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#201)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#201)]  
    [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#202)]
    [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#202)]  
  
2. Přepište metodu <xref:System.Windows.Forms.DataGridViewTextBoxCell.Paint%2A> ve třídě `DataGridViewRolloverCell`. V přepsání nejprve zavolejte implementaci základní třídy, která zpracovává funkce hostovaného textového pole. Pak použijte metodu <xref:System.Windows.Forms.Control.PointToClient%2A> ovládacího prvku pro transformaci pozice kurzoru (v souřadnicích obrazovky) na souřadnice <xref:System.Windows.Forms.DataGridView> oblasti klienta. Pokud souřadnice myši spadají do hranice buňky, nakreslete vsazený obdélník.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#210)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#210)]  
  
3. Přepsat <xref:System.Windows.Forms.DataGridViewCell.OnMouseEnter%2A> a <xref:System.Windows.Forms.DataGridViewCell.OnMouseLeave%2A> metody ve třídě `DataGridViewRolloverCell` pro vynucení překreslení buněk, když na ně ukazatel myši vstoupí nebo opustí.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#220)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#220)]  
  
4. Z typu <xref:System.Windows.Forms.DataGridViewColumn> odvodit novou třídu nazvanou `DataGridViewRolloverCellColumn`. V konstruktoru přiřaďte k vlastnosti <xref:System.Windows.Forms.DataGridViewColumn.CellTemplate%2A> nový objekt `DataGridViewRolloverCell`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#300)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#300)]  
  
## <a name="example"></a>Příklad  
 Příklad kompletního kódu obsahuje malý testovací formulář, který demonstruje chování vlastního typu buňky.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#000)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. Windows. Forms a System. Drawing.  
 
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Přizpůsobení ovládacího prvku Windows Forms DataGridView](customizing-the-windows-forms-datagridview-control.md)
- [Architektura ovládacího prvku DataGridView](datagridview-control-architecture-windows-forms.md)
- [Typy sloupců v ovládacím prvku Windows Forms DataGridView](column-types-in-the-windows-forms-datagridview-control.md)
- [Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
