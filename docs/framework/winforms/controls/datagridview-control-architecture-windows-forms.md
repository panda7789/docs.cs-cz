---
title: Architektura ovládacího prvku DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: 2e1884383cca87f8d4ff84f486e2b29761a0c55d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742525"
---
# <a name="datagridview-control-architecture-windows-forms"></a>Architektura ovládacího prvku DataGridView (Windows Forms)
Ovládací prvek <xref:System.Windows.Forms.DataGridView> a jeho související třídy jsou navržené tak, aby byly flexibilní a rozšiřitelný systém pro zobrazení a úpravy tabulkových dat. Tyto třídy jsou obsaženy v oboru názvů <xref:System.Windows.Forms?displayProperty=nameWithType> a jsou všechny pojmenovány s předponou "DataGridView".  
  
## <a name="architecture-elements"></a>Prvky architektury  
 Primární <xref:System.Windows.Forms.DataGridView> doprovodné třídy jsou odvozeny z <xref:System.Windows.Forms.DataGridViewElement>. Následující objektový model znázorňuje <xref:System.Windows.Forms.DataGridViewElement> hierarchii dědičnosti.  
  
 ![Diagram, který zobrazuje hierarchii objektového modelu DataGridViewElement.](./media/datagridview-control-architecture-windows-forms/datagridviewelement-object-model.gif)  
  
 Třída <xref:System.Windows.Forms.DataGridViewElement> poskytuje odkaz na nadřazený ovládací prvek <xref:System.Windows.Forms.DataGridView> a má vlastnost <xref:System.Windows.Forms.DataGridViewElement.State%2A>, která obsahuje hodnotu, která představuje kombinaci hodnot z výčtu <xref:System.Windows.Forms.DataGridViewElementStates>.  
  
 Následující části popisují <xref:System.Windows.Forms.DataGridView> doprovodné třídy podrobněji.  
  
### <a name="datagridviewelementstates"></a>DataGridViewElementStates  
 Výčet <xref:System.Windows.Forms.DataGridViewElementStates> obsahuje následující hodnoty:  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 Hodnoty tohoto výčtu lze kombinovat s bitovými logickými operátory, takže vlastnost <xref:System.Windows.Forms.DataGridViewElement.State%2A> může vyjádřit více než jeden stav najednou. <xref:System.Windows.Forms.DataGridViewElement> může být například současně <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>a <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.  
  
### <a name="cells-and-bands"></a>Buňky a pruhy  
 Ovládací prvek <xref:System.Windows.Forms.DataGridView> obsahuje dva základní druhy objektů: buňky a pásma. Všechny buňky jsou odvozeny od <xref:System.Windows.Forms.DataGridViewCell> základní třídy. Dva druhy pásem, <xref:System.Windows.Forms.DataGridViewColumn> a <xref:System.Windows.Forms.DataGridViewRow>, jsou odvozeny ze <xref:System.Windows.Forms.DataGridViewBand> základní třídy.  
  
 Ovládací prvek <xref:System.Windows.Forms.DataGridView> spolupracuje s několika třídami, ale nejčastěji zjištěné jsou <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>a <xref:System.Windows.Forms.DataGridViewRow>.  
  
### <a name="datagridviewcell"></a>DataGridViewCell  
 Buňka je základní jednotkou interakce pro <xref:System.Windows.Forms.DataGridView>. Zobrazení se zacentruje na buňky a zadání dat se často provádí v buňkách. K buňkám můžete přistupovat pomocí <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> kolekce <xref:System.Windows.Forms.DataGridViewRow> třídy a k vybraným buňkám můžete přistupovat pomocí kolekce <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Následující objektový model znázorňuje toto použití a ukazuje hierarchii dědičnosti <xref:System.Windows.Forms.DataGridViewCell>.  
  
 ![Diagram, který zobrazuje hierarchii objektového modelu DataGridViewCell.](./media/datagridview-control-architecture-windows-forms/datagridviewcell-object-model.gif)  
  
 Typ <xref:System.Windows.Forms.DataGridViewCell> je abstraktní základní třída, ze které jsou odvozeny všechny typy buněk. <xref:System.Windows.Forms.DataGridViewCell> a jeho odvozené typy nejsou model Windows Forms ovládací prvky, ale některé ovládací prvky model Windows Forms hostitele. Všechny funkce úprav, které buňka podporuje, je obvykle zpracovávána hostovaným ovládacím prvkem.  
  
 <xref:System.Windows.Forms.DataGridViewCell> objekty neovládají vlastní funkce vzhledu a malování stejným způsobem jako model Windows Forms ovládací prvky. Místo toho je <xref:System.Windows.Forms.DataGridView> zodpovědná za vzhled jeho <xref:System.Windows.Forms.DataGridViewCell>ch objektů. Při interakci s vlastnostmi a událostmi ovládacího prvku <xref:System.Windows.Forms.DataGridView> můžete významně ovlivnit vzhled a chování buněk. Pokud máte zvláštní požadavky pro přizpůsobení, které jsou nad rámec možností ovládacího prvku <xref:System.Windows.Forms.DataGridView>, můžete implementovat vlastní třídu, která je odvozena z <xref:System.Windows.Forms.DataGridViewCell> nebo některé z jejích podřízených tříd.  
  
 Následující seznam obsahuje třídy odvozené od <xref:System.Windows.Forms.DataGridViewCell>:  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
- <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewImageCell>  
  
- <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
- Vlastní typy buněk  
  
### <a name="datagridviewcolumn"></a>DataGridViewColumn  
 Schéma připojeného úložiště dat ovládacího prvku <xref:System.Windows.Forms.DataGridView> je vyjádřeno ve sloupcích <xref:System.Windows.Forms.DataGridView>ho ovládacího prvku. Ke sloupcům ovládacího prvku <xref:System.Windows.Forms.DataGridView> můžete přistupovat pomocí kolekce <xref:System.Windows.Forms.DataGridView.Columns%2A>. K vybraným sloupcům můžete přistupovat pomocí kolekce <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>. Následující objektový model znázorňuje toto použití a ukazuje hierarchii dědičnosti <xref:System.Windows.Forms.DataGridViewColumn>.  
  
 ![Diagram, který znázorňuje hierarchii objektového modelu DataGridViewColumn.](./media/datagridview-control-architecture-windows-forms/datagridviewcolumn-object-model.gif)  
  
 Některé typy klíčových buněk mají odpovídající typy sloupců. Tyto jsou odvozeny od <xref:System.Windows.Forms.DataGridViewColumn> základní třídy.  
  
 Následující seznam obsahuje třídy odvozené od <xref:System.Windows.Forms.DataGridViewColumn>:  
  
- <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
- Vlastní typy sloupců  
  
### <a name="datagridview-editing-controls"></a>Ovládací prvky DataGridView pro úpravy  
 Buňky, které podporují pokročilé funkce úprav, obvykle používají hostovaný ovládací prvek, který je odvozen od ovládacího prvku model Windows Forms. Tyto ovládací prvky také implementují rozhraní <xref:System.Windows.Forms.IDataGridViewEditingControl>. Následující objektový model znázorňuje použití těchto ovládacích prvků.  
  
 ![Diagram znázorňující hierarchii modelu objektu ovládacího prvku pro úpravu DataGridView](./media/datagridview-control-architecture-windows-forms/datagridviewediting-object-model.gif)  
  
 S ovládacím prvkem <xref:System.Windows.Forms.DataGridView> jsou k dispozici následující ovládací prvky pro úpravy:  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 Informace o vytváření vlastních ovládacích prvků pro úpravy naleznete v tématu [How to: Host Controls in model Windows Forms DataGridView Cells](how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
 Následující tabulka znázorňuje vztah mezi typy buněk, typy sloupců a ovládacími prvky pro úpravy.  
  
|Typ buňky|Hostovaný ovládací prvek|Typ sloupce|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|neuvedeno|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|neuvedeno|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|neuvedeno|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|neuvedeno|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a>DataGridViewRow  
 Třída <xref:System.Windows.Forms.DataGridViewRow> zobrazuje datová pole záznamu z úložiště dat, ke kterému je připojen ovládací prvek <xref:System.Windows.Forms.DataGridView>. K řádkům ovládacího prvku <xref:System.Windows.Forms.DataGridView> můžete přistupovat pomocí kolekce <xref:System.Windows.Forms.DataGridView.Rows%2A>. K vybraným řádkům můžete přistupovat pomocí kolekce <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>. Následující objektový model znázorňuje toto použití a ukazuje hierarchii dědičnosti <xref:System.Windows.Forms.DataGridViewRow>.  
  
 ![Diagram, který zobrazuje hierarchii objektového modelu DataGridViewRow.](./media/datagridview-control-architecture-windows-forms/datagridviewrow-object-model.gif)
  
 Z třídy <xref:System.Windows.Forms.DataGridViewRow> můžete odvodit vlastní typy, i když to obvykle nebude nutné. Ovládací prvek <xref:System.Windows.Forms.DataGridView> má několik událostí souvisejících s řádky a vlastnosti pro přizpůsobení chování jeho objektů <xref:System.Windows.Forms.DataGridViewRow>.  
  
 Pokud povolíte vlastnost <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> ovládacího prvku <xref:System.Windows.Forms.DataGridView>, zobrazí se speciální řádek pro přidání nových řádků jako poslední řádek. Tento řádek je součástí kolekce <xref:System.Windows.Forms.DataGridView.Rows%2A>, ale má speciální funkce, které mohou vyžadovat vaši pozornost. Další informace najdete v tématu [použití řádku pro nové záznamy v ovládacím prvku DataGridView model Windows Forms](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také

- [Přehled ovládacího prvku DataGridView](datagridview-control-overview-windows-forms.md)
- [Přizpůsobení ovládacího prvku Windows Forms DataGridView](customizing-the-windows-forms-datagridview-control.md)
- [Použití řádku pro nové záznamy v ovládacím prvku Windows Forms DataGridView](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
