---
title: Architektura ovládacího prvku DataGridView (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: 81ac17c9f78baa71d005883c9dd928e398b10a33
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842340"
---
# <a name="datagridview-control-architecture-windows-forms"></a>Architektura ovládacího prvku DataGridView (Windows Forms)
<xref:System.Windows.Forms.DataGridView> Ovládacího prvku a jeho souvisejícími třídami jsou navržené tak flexibilní a rozšiřitelný systém pro zobrazení a úpravy tabulková data. Tyto třídy jsou obsaženy v <xref:System.Windows.Forms?displayProperty=nameWithType> obor názvů a že jsou všechny pojmenované s předponou "DataGridView".  
  
## <a name="architecture-elements"></a>Prvky architektury  
 Primární <xref:System.Windows.Forms.DataGridView> doprovodné třídy odvozovat z <xref:System.Windows.Forms.DataGridViewElement>. Následující objektový model ukazuje <xref:System.Windows.Forms.DataGridViewElement> hierarchii dědičnosti.  
  
 ![Diagram znázorňující hierarchii DataGridViewElement – objektový Model.](./media/datagridview-control-architecture-windows-forms/datagridviewelement-object-model.gif)  
  
 <xref:System.Windows.Forms.DataGridViewElement> Třída poskytuje odkaz na nadřazený <xref:System.Windows.Forms.DataGridView> ovládací prvek a má <xref:System.Windows.Forms.DataGridViewElement.State%2A> vlastnost, která obsahuje hodnotu, která představuje kombinaci hodnot z <xref:System.Windows.Forms.DataGridViewElementStates> výčtu.  
  
 V následujících částech <xref:System.Windows.Forms.DataGridView> doprovodné třídy podrobněji.  
  
### <a name="datagridviewelementstates"></a>DataGridViewElementStates  
 <xref:System.Windows.Forms.DataGridViewElementStates> Výčet obsahuje následující hodnoty:  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 Hodnoty tento výčet je možné kombinovat s bitové logické operátory, takže <xref:System.Windows.Forms.DataGridViewElement.State%2A> vlastnost můžete vyjádřit najednou více než jeden stav. Například <xref:System.Windows.Forms.DataGridViewElement> může být současně <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, a <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.  
  
### <a name="cells-and-bands"></a>Buňky a pruhy  
 <xref:System.Windows.Forms.DataGridView> Ovládací prvek obsahuje dva základní druhy objektů: buňky a pruhy. Všechny buňky odvozovat <xref:System.Windows.Forms.DataGridViewCell> základní třídy. Dva druhy pruhy, <xref:System.Windows.Forms.DataGridViewColumn> a <xref:System.Windows.Forms.DataGridViewRow>, obě jsou odvozeny z <xref:System.Windows.Forms.DataGridViewBand> základní třídy.  
  
 <xref:System.Windows.Forms.DataGridView> Ovládací prvek spolupracuje s více třídami, ale jsou nejčastěji vyskytují <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, a <xref:System.Windows.Forms.DataGridViewRow>.  
  
### <a name="datagridviewcell"></a>DataGridViewCell  
 Je základní jednotkou interakce pro buňku <xref:System.Windows.Forms.DataGridView>. U buněk zarovnaný na střed zobrazení a zadávání dat často probíhá prostřednictvím buňky. Přistupujete buňky pomocí <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> kolekce <xref:System.Windows.Forms.DataGridViewRow> třídy kde můžete přistupovat pomocí vybrané buňky <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> kolekce <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Následující objektový model ukazuje toto využití a ukazuje, <xref:System.Windows.Forms.DataGridViewCell> hierarchii dědičnosti.  
  
 ![Diagram znázorňující hierarchii modelu objektu DataGridViewCell.](./media/datagridview-control-architecture-windows-forms/datagridviewcell-object-model.gif)  
  
 <xref:System.Windows.Forms.DataGridViewCell> Typ je abstraktní základní třída, ze které jsou odvozeny všechny typy buňky. <xref:System.Windows.Forms.DataGridViewCell> a jeho odvozených typů nejsou ovládacích prvků Windows Forms, ale některé hostitelské ovládací prvky Windows Forms. Žádné funkce pro úpravy podporovaných buňky je obvykle zpracovávána hostovaného ovládacího prvku.  
  
 <xref:System.Windows.Forms.DataGridViewCell> objekty nejsou v ovládacím prvku vlastní vzhled a funkce Malování stejným způsobem jako ovládací prvky Windows Forms. Místo toho <xref:System.Windows.Forms.DataGridView> zodpovídá za vzhled jeho <xref:System.Windows.Forms.DataGridViewCell> objekty. To interakcí se může významně ovlivnit vzhled a chování buněk <xref:System.Windows.Forms.DataGridView> vlastnosti a události ovládacího prvku. Pokud máte zvláštní požadavky na přizpůsobení, které jsou nad rámec možností <xref:System.Windows.Forms.DataGridView> ovládací prvek, můžete implementovat vlastní třídu odvozenou od <xref:System.Windows.Forms.DataGridViewCell> nebo jeden z jejích podřízených tříd.  
  
 V následující seznamu jsou uvedeny třídy odvozené od <xref:System.Windows.Forms.DataGridViewCell>:  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewImageCell>  
  
-   <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
-   Vaše vlastní typy  
  
### <a name="datagridviewcolumn"></a>DataGridViewColumn  
 Schéma <xref:System.Windows.Forms.DataGridView> ovládacího prvku připojené datové úložiště je vyjádřen v <xref:System.Windows.Forms.DataGridView> sloupce ovládacího prvku. Můžete přistupovat <xref:System.Windows.Forms.DataGridView> sloupce ovládacího prvku s použitím <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekce. Dostanete z vybraných sloupců pomocí <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> kolekce. Následující objektový model ukazuje toto využití a ukazuje, <xref:System.Windows.Forms.DataGridViewColumn> hierarchii dědičnosti.  
  
 ![Diagram znázorňující hierarchii modelu objektu DataGridViewColumn.](./media/datagridview-control-architecture-windows-forms/datagridviewcolumn-object-model.gif)  
  
 Některé typy klíčů buněk mají odpovídající typy sloupců. Tyto jsou odvozeny z <xref:System.Windows.Forms.DataGridViewColumn> základní třídy.  
  
 V následující seznamu jsou uvedeny třídy odvozené od <xref:System.Windows.Forms.DataGridViewColumn>:  
  
-   <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
-   Vaše typy vlastní sloupec  
  
### <a name="datagridview-editing-controls"></a>Úpravy ovládacích prvků DataGridView  
 Buňky, které podporují pokročilé funkce pro úpravy obvykle používají hostovaného ovládacího prvku, který je odvozen z ovládacího prvku Windows Forms. Tyto ovládací prvky implementovat taky <xref:System.Windows.Forms.IDataGridViewEditingControl> rozhraní. Následující objektový model ukazuje využití těchto ovládacích prvků.  
  
 ![Diagram znázorňující hierarchii Model objektu úpravy ovládacího prvku DataGridView.](./media/datagridview-control-architecture-windows-forms/datagridviewediting-object-model.gif)  
  
 Následující ovládací prvky pro úpravy jsou součástí <xref:System.Windows.Forms.DataGridView> ovládacího prvku:  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 Informace o vytváření vlastních úprav ovládacích prvků naleznete v tématu [jak: Hostování ovládacích prvků ve Windows Forms DataGridView buňky](how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
 Následující tabulka znázorňuje vztah mezi typy buněk, typy sloupců a ovládací prvky pro úpravy.  
  
|Typ buňky|Hostovaného ovládacího prvku|Typ sloupce|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|není k dispozici|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|není k dispozici|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|není k dispozici|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|není k dispozici|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a>DataGridViewRow  
 <xref:System.Windows.Forms.DataGridViewRow> Třídy zobrazí pole záznamu dat z data ukládat do kterého <xref:System.Windows.Forms.DataGridView> ovládací prvek připojen. Můžete přistupovat <xref:System.Windows.Forms.DataGridView> řádků ovládacího prvku s použitím <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekce. Vybrané řádky přístupné prostřednictvím <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> kolekce. Následující objektový model ukazuje toto využití a ukazuje, <xref:System.Windows.Forms.DataGridViewRow> hierarchii dědičnosti.  
  
 ![Diagram znázorňující hierarchii DataGridViewRow objektový Model.](./media/datagridview-control-architecture-windows-forms/datagridviewrow-object-model.gif)
  
 Můžete odvozovat vlastní typy z <xref:System.Windows.Forms.DataGridViewRow> třídy, i když to není obvykle nutné. <xref:System.Windows.Forms.DataGridView> Ovládací prvek má několik řádků související události a vlastnosti pro přizpůsobení chování jeho <xref:System.Windows.Forms.DataGridViewRow> objekty.  
  
 Pokud povolíte <xref:System.Windows.Forms.DataGridView> ovládacího prvku <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> , zvláštní řádek pro přidání nových řádků se zobrazí jako poslední řádek. Tento řádek je součástí <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekce, ale má speciální funkce, které můžou vyžadovat vaši pozornost. Další informace najdete v tématu [použití řádku pro nové záznamy v ovládacím prvku Windows Forms DataGridView](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také:
- [Přehled ovládacího prvku DataGridView](datagridview-control-overview-windows-forms.md)
- [Přizpůsobení ovládacího prvku Windows Forms DataGridView](customizing-the-windows-forms-datagridview-control.md)
- [Použití řádku pro nové záznamy v ovládacím prvku Windows Forms DataGridView](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
