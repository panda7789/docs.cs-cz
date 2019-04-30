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
ms.openlocfilehash: 6b0773b4c41b77fe43a5b7fba994778ae18c16c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941593"
---
# <a name="how-to-customize-cells-and-columns-in-the-windows-forms-datagridview-control-by-extending-their-behavior-and-appearance"></a>Postupy: Přizpůsobení buněk a sloupců v ovládacím prvku Windows Forms DataGridView rozšířením jejich chování a vzhledu
<xref:System.Windows.Forms.DataGridView> Ovládacího prvku poskytuje několik způsobů, jak přizpůsobit její vzhled a chování pomocí vlastnosti, události a doprovodné třídy. V některých případech můžete mít požadavky pro vaše buňky, která přesahují co může poskytnout tyto funkce. Můžete vytvořit vlastní <xref:System.Windows.Forms.DataGridViewCell> třídy k zajištění rozšířené funkce.  
  
 Vytvoření vlastní <xref:System.Windows.Forms.DataGridViewCell> třídy odvozené z <xref:System.Windows.Forms.DataGridViewCell> základní třídy nebo některé z odvozených tříd. I když můžete zobrazit libovolného typu buňky v jakýkoli typ sloupce, obvykle vytvoříte vlastní <xref:System.Windows.Forms.DataGridViewColumn> třídy specializované pro zobrazení typu buňky. Sloupec třídy odvozovat z <xref:System.Windows.Forms.DataGridViewColumn> nebo jeden z jeho odvozených typů.  
  
 V následujícím příkladu kódu se vytvoří vlastní třídu s názvem `DataGridViewRolloverCell` , který zjistí, že ukazatel myši přejde a dostanou buňky. Kdy je myš v rámci hranice na buňku, inset obdélník vykreslením. Tento nový typ je odvozen od <xref:System.Windows.Forms.DataGridViewTextBoxCell> a ve všech ohledech se chová jako její základní třídě. Třídě doprovodných prvků sloupce se nazývá `DataGridViewRolloverColumn`.  
  
 K použití těchto tříd, vytvořit formulář, který obsahuje <xref:System.Windows.Forms.DataGridView> řídit, přidejte jeden nebo více `DataGridViewRolloverColumn` objektů <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekce a naplnit řádky obsahující hodnoty ovládacího prvku.  
  
> [!NOTE]
>  V tomto příkladu nebude fungovat správně, pokud chcete přidat prázdné řádky. Prázdné řádky se vytvoří, například při přidání řádků do ovládacího prvku tak, že nastavíte <xref:System.Windows.Forms.DataGridView.RowCount%2A> vlastnost. Důvodem je, že řádky přidané v tomto případě se automaticky sdílet, což znamená, že `DataGridViewRolloverCell` objekty nejsou vytvořena instance, dokud nekliknete na jednotlivé buňky a způsobuje související řádky, které mají být nejdříve zrušeno sdílení.  
  
 Vzhledem k tomu, že tento typ buňky přizpůsobení vyžaduje nesdílený řádky, není vhodné pro použití s velkými datovými sadami. Další informace o sdílení řádků, naleznete v tématu [osvědčené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
> [!NOTE]
>  Pokud odvozujete od <xref:System.Windows.Forms.DataGridViewCell> nebo <xref:System.Windows.Forms.DataGridViewColumn> a přidání nových vlastností do odvozené třídy, je nutné přepsat `Clone` metoda kopírování nové vlastnosti během operace klonování. Měli byste také zavolat základní třídu `Clone` metodu tak, aby vlastností základní třídy jsou zkopírovány do nové buňky nebo sloupec.  
  
### <a name="to-customize-cells-and-columns-in-the-datagridview-control"></a>Přizpůsobení buněk a sloupců v ovládacím prvku DataGridView  
  
1. Odvodit novou třídu buňky, s názvem `DataGridViewRolloverCell`, z <xref:System.Windows.Forms.DataGridViewTextBoxCell> typu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#201)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#201)]  
    [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#202)]
    [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#202)]  
  
2. Přepsat <xref:System.Windows.Forms.DataGridViewTextBoxCell.Paint%2A> metodu `DataGridViewRolloverCell` třídy. V přepsání nejprve volejte implementaci základní třídy, která zpracovává pole funkcí hostované text. Pak pomocí ovládacího prvku <xref:System.Windows.Forms.Control.PointToClient%2A> metody pro transformaci do pozice kurzoru (v souřadnicovém systému obrazovky) <xref:System.Windows.Forms.DataGridView> souřadnice klientské oblasti. Pokud souřadnice myši spadat do hranice buňky, kreslení obdélníku vložené.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#210)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#210)]  
  
3. Přepsat <xref:System.Windows.Forms.DataGridViewCell.OnMouseEnter%2A> a <xref:System.Windows.Forms.DataGridViewCell.OnMouseLeave%2A> metody v `DataGridViewRolloverCell` třídy přinutit buňky, které chcete repaint sami, pokud ukazatel myši přejde do nebo je opustí.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#220)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#220)]  
  
4. Odvozovat nové třídy, nazvané `DataGridViewRolloverCellColumn`, z <xref:System.Windows.Forms.DataGridViewColumn> typu. V konstruktoru, přiřaďte nový `DataGridViewRolloverCell` objektu na jeho <xref:System.Windows.Forms.DataGridViewColumn.CellTemplate%2A> vlastnost.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#300)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#300)]  
  
## <a name="example"></a>Příklad  
 Příklad úplného kódu obsahuje formulář malý test, který ukazuje chování typu vlastní.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#000)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení systému, System.Windows.Forms a System.Drawing.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Přizpůsobení ovládacího prvku Windows Forms DataGridView](customizing-the-windows-forms-datagridview-control.md)
- [Architektura ovládacího prvku DataGridView](datagridview-control-architecture-windows-forms.md)
- [Typy sloupců v ovládacím prvku Windows Forms DataGridView](column-types-in-the-windows-forms-datagridview-control.md)
- [Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
