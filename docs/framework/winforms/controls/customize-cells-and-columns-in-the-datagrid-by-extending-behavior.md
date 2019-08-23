---
title: 'Postupy: Přizpůsobení buněk a sloupců v ovládacím prvku Windows Forms DataGridView rozšířením jejich chování a vzhledu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- columns [Windows Forms], customizing in DataGridView control
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 9b7dc7b6-5ce6-4566-9949-902f74f17a81
ms.openlocfilehash: 0976a0e07aead1bbaf951c6db8266c5de1a31cd8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929704"
---
# <a name="how-to-customize-cells-and-columns-in-the-windows-forms-datagridview-control-by-extending-their-behavior-and-appearance"></a>Postupy: Přizpůsobení buněk a sloupců v ovládacím prvku Windows Forms DataGridView rozšířením jejich chování a vzhledu
<xref:System.Windows.Forms.DataGridView> Ovládací prvek poskytuje několik způsobů, jak přizpůsobit jeho vzhled a chování pomocí vlastností, událostí a doprovodných tříd. V některých případech je možné, že budete mít požadavky na buňky, které přesahují rámec toho, co tyto funkce poskytují. Můžete vytvořit <xref:System.Windows.Forms.DataGridViewCell> vlastní třídu pro poskytování rozšířených funkcí.  
  
 Vlastní <xref:System.Windows.Forms.DataGridViewCell> třídu lze vytvořit odvozením <xref:System.Windows.Forms.DataGridViewCell> ze základní třídy nebo jedné z jeho odvozených tříd. I když můžete zobrazit libovolný typ buňky v jakémkoli typu sloupce, obvykle vytvoříte také vlastní <xref:System.Windows.Forms.DataGridViewColumn> třídu specializované pro zobrazení typu buňky. Třídy sloupců jsou odvozeny z <xref:System.Windows.Forms.DataGridViewColumn> nebo jednoho z jeho odvozených typů.  
  
 V následujícím příkladu kódu vytvoříte třídu vlastní buňky s názvem `DataGridViewRolloverCell` , která se detekuje, když ukazatel myši přejde a opustí hranice buňky. I když je ukazatel myši v rámci hranice buňky, vykreslí se vsazený obdélník. Tento nový typ je odvozen z <xref:System.Windows.Forms.DataGridViewTextBoxCell> a se chová ve všech ostatních ohledech jako na svou základní třídu. Je volána `DataGridViewRolloverColumn`třída doprovodného sloupce.  
  
 Chcete-li použít tyto třídy, vytvořte formulář, <xref:System.Windows.Forms.DataGridView> který obsahuje ovládací prvek, přidejte `DataGridViewRolloverColumn` jeden nebo více <xref:System.Windows.Forms.DataGridView.Columns%2A> objektů do kolekce a naplňte ovládací prvek řádky obsahující hodnoty.  
  
> [!NOTE]
> Pokud přidáte prázdné řádky, tento příklad nebude fungovat správně. Jsou vytvořeny prázdné řádky, například při přidávání řádků do ovládacího prvku nastavením <xref:System.Windows.Forms.DataGridView.RowCount%2A> vlastnosti. Důvodem je to, že řádky přidané v tomto případě jsou automaticky sdíleny, což `DataGridViewRolloverCell` znamená, že objekty nebudou vytvořeny, dokud nekliknete na jednotlivé buňky, což způsobí, že přidružené řádky budou Nesdílet.  
  
 Vzhledem k tomu, že tento typ přizpůsobení buňky vyžaduje nesdílené řádky, není vhodné používat s velkými datovými sadami. Další informace o sdílení řádků naleznete v tématu [osvědčené postupy pro škálování ovládacího prvku DataGridView model Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
> [!NOTE]
> Při odvozování z <xref:System.Windows.Forms.DataGridViewCell> nebo <xref:System.Windows.Forms.DataGridViewColumn> a přidání nových vlastností na odvozenou třídu nezapomeňte přepsat `Clone` metodu pro kopírování nových vlastností během operací klonování. Měli byste také zavolat `Clone` metodu základní třídy tak, aby byly vlastnosti základní třídy zkopírovány do nové buňky nebo sloupce.  
  
### <a name="to-customize-cells-and-columns-in-the-datagridview-control"></a>Přizpůsobení buněk a sloupců v ovládacím prvku DataGridView  
  
1. Odvodit třídu nové buňky, která `DataGridViewRolloverCell`je volána <xref:System.Windows.Forms.DataGridViewTextBoxCell> z typu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#201)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#201)]  
    [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#202)]
    [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#202)]  
  
2. <xref:System.Windows.Forms.DataGridViewTextBoxCell.Paint%2A> Přepsat metodu`DataGridViewRolloverCell` ve třídě. V přepsání nejprve zavolejte implementaci základní třídy, která zpracovává funkce hostovaného textového pole. Pak použijte <xref:System.Windows.Forms.Control.PointToClient%2A> metodu ovládacího prvku pro transformaci pozice kurzoru (v souřadnicích obrazovky) <xref:System.Windows.Forms.DataGridView> na souřadnice klientské oblasti. Pokud souřadnice myši spadají do hranice buňky, nakreslete vsazený obdélník.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#210)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#210)]  
  
3. Přepište metody <xref:System.Windows.Forms.DataGridViewCell.OnMouseLeave%2A> `DataGridViewRolloverCell` a ve třídě, aby buňky vynutily překreslení, když ukazatel myši zadá nebo opustí. <xref:System.Windows.Forms.DataGridViewCell.OnMouseEnter%2A>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#220)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#220)]  
  
4. `DataGridViewRolloverCellColumn` Odvodit<xref:System.Windows.Forms.DataGridViewColumn> z typu novou třídu s názvem. V konstruktoru přiřaďte <xref:System.Windows.Forms.DataGridViewColumn.CellTemplate%2A> k vlastnosti nový `DataGridViewRolloverCell` objekt.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#300)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#300)]  
  
## <a name="example"></a>Příklad  
 Příklad kompletního kódu obsahuje malý testovací formulář, který demonstruje chování vlastního typu buňky.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#000)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. Windows. Forms a System. Drawing.  
 
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Přizpůsobení ovládacího prvku Windows Forms DataGridView](customizing-the-windows-forms-datagridview-control.md)
- [Architektura ovládacího prvku DataGridView](datagridview-control-architecture-windows-forms.md)
- [Typy sloupců v ovládacím prvku Windows Forms DataGridView](column-types-in-the-windows-forms-datagridview-control.md)
- [Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
