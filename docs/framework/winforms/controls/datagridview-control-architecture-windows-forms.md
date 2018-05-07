---
title: Architektura ovládacího prvku DataGridView (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: a9fc1707b1691266d1844c411a08e7e8f35514ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="datagridview-control-architecture-windows-forms"></a>Architektura ovládacího prvku DataGridView (Windows Forms)
<xref:System.Windows.Forms.DataGridView> Ovládací prvek a jeho souvisejících tříd jsou navržené jako flexibilní a rozšiřitelný systém pro zobrazení a úpravy tabulková data. Tyto třídy jsou obsaženy v <xref:System.Windows.Forms?displayProperty=nameWithType> oboru názvů a že jsou všechny pojmenované s předponou "DataGridView".  
  
## <a name="architecture-elements"></a>Architektura elementy  
 Primární <xref:System.Windows.Forms.DataGridView> doprovodné třídy jsou odvozeny od <xref:System.Windows.Forms.DataGridViewElement>. Znázorňuje následující objektový model <xref:System.Windows.Forms.DataGridViewElement> hierarchie dědičnosti.  
  
 ![DataGridViewElement – objektový Model](../../../../docs/framework/winforms/controls/media/datagridviewelement.gif "DataGridViewElement –")  
DataGridViewElement – objektový model  
  
 <xref:System.Windows.Forms.DataGridViewElement> Třída poskytuje odkaz na nadřazený <xref:System.Windows.Forms.DataGridView> řízení a má <xref:System.Windows.Forms.DataGridViewElement.State%2A> vlastnosti, která obsahuje hodnotu, která představuje kombinace hodnot z <xref:System.Windows.Forms.DataGridViewElementStates> výčtu.  
  
 Následující části popisují <xref:System.Windows.Forms.DataGridView> doprovodné třídy podrobněji.  
  
### <a name="datagridviewelementstates"></a>DataGridViewElementStates  
 <xref:System.Windows.Forms.DataGridViewElementStates> Výčet obsahuje následující hodnoty:  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 Hodnoty tento výčet je možné kombinovat s bitové logické operátory, proto <xref:System.Windows.Forms.DataGridViewElement.State%2A> vlastnost express víc než jeden stav najednou. Například <xref:System.Windows.Forms.DataGridViewElement> může být současně <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, a <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.  
  
### <a name="cells-and-bands"></a>Buňky a pruhy  
 <xref:System.Windows.Forms.DataGridView> Ovládací prvek obsahuje dva základní typy objektů: buněk a pruhy. Všechny buňky odvozena od <xref:System.Windows.Forms.DataGridViewCell> základní třídy. Dva druhy pruhy, <xref:System.Windows.Forms.DataGridViewColumn> a <xref:System.Windows.Forms.DataGridViewRow>, obě jsou odvozeny od <xref:System.Windows.Forms.DataGridViewBand> základní třídy.  
  
 <xref:System.Windows.Forms.DataGridView> Řízení spolupracuje s několik tříd, ale jsou nejčastěji došlo k <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, a <xref:System.Windows.Forms.DataGridViewRow>.  
  
### <a name="datagridviewcell"></a>DataGridViewCell  
 Buňky je základní jednotkou interakce pro <xref:System.Windows.Forms.DataGridView>. Zobrazení se jedná o buněk a vkládání dat se často provádí prostřednictvím buněk. Máte přístup k buněk pomocí <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> kolekce <xref:System.Windows.Forms.DataGridViewRow> třídy a můžete přistupovat pomocí vybrané buňky <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> kolekce <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Následující objektový model ukazuje toto využití a zobrazuje <xref:System.Windows.Forms.DataGridViewCell> hierarchie dědičnosti.  
  
 ![DataGridViewCell – objektový Model](../../../../docs/framework/winforms/controls/media/datagridviewcell.gif "DataGridViewCell")  
DataGridViewCell objektový model  
  
 <xref:System.Windows.Forms.DataGridViewCell> Typ je abstraktní základní třídu, ze které jsou odvozeny všechny typy buňky. <xref:System.Windows.Forms.DataGridViewCell> a jeho odvozených typů nejsou ovládací prvky Windows Forms, ale některé ovládací prvky Windows Forms hostitele. Žádné úpravy funkce nepodporuje buňku je obvykle zpracovávány hostované ovládacího prvku.  
  
 <xref:System.Windows.Forms.DataGridViewCell> objekty neurčují vlastní vzhled a funkce Malování stejným způsobem, jak Windows Forms – ovládací prvky. Místo toho <xref:System.Windows.Forms.DataGridView> zodpovídá za vzhled jeho <xref:System.Windows.Forms.DataGridViewCell> objekty. Vzhled a chování buněk může výrazně ovlivnit interakcí s <xref:System.Windows.Forms.DataGridView> vlastnosti a události ovládacího prvku. Pokud máte speciální požadavky pro úpravy, které jsou nad rámec možností <xref:System.Windows.Forms.DataGridView> ovládací prvek, můžete implementovat vlastní třídu odvozenou od <xref:System.Windows.Forms.DataGridViewCell> nebo jedna z jejích podřízených tříd.  
  
 V následujícím seznamu jsou uvedeny třídy odvozené z <xref:System.Windows.Forms.DataGridViewCell>:  
  
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
  
-   Vaše vlastní buňky typy  
  
### <a name="datagridviewcolumn"></a>DataGridViewColumn  
 Schéma <xref:System.Windows.Forms.DataGridView> úložiště připojená data ovládacího prvku je vyjádřena v <xref:System.Windows.Forms.DataGridView> sloupce ovládacího prvku. Dostanete <xref:System.Windows.Forms.DataGridView> sloupce ovládacího prvku pomocí <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekce. Máte přístup k vybrané sloupce pomocí <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> kolekce. Následující objektový model ukazuje toto využití a zobrazuje <xref:System.Windows.Forms.DataGridViewColumn> hierarchie dědičnosti.  
  
 ![DataGridViewColumn – objektový Model](../../../../docs/framework/winforms/controls/media/datagridviewcolumn.gif "DataGridViewColumn")  
DataGridViewColumn objektový model  
  
 Některé typy klíčů buňky mají odpovídající typy sloupců. Tyto jsou odvozeny od <xref:System.Windows.Forms.DataGridViewColumn> základní třídy.  
  
 V následujícím seznamu jsou uvedeny třídy odvozené z <xref:System.Windows.Forms.DataGridViewColumn>:  
  
-   <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
-   Vaše vlastní sloupec typy  
  
### <a name="datagridview-editing-controls"></a>Ovládací prvky úprav DataGridView  
 Buněk, které obvykle podporu pokročilých funkcí úpravy pomocí hostované ovládací prvek, který je odvozený z ovládacího prvku Windows Forms. Tyto ovládací prvky taky implementovat <xref:System.Windows.Forms.IDataGridViewEditingControl> rozhraní. Následující objektový model ukazuje použití těchto ovládacích prvků.  
  
 ![Úpravy objektový Model ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/media/datagridviewediting.gif "DataGridViewEditing")  
Objektový model úpravy ovládacího prvku DataGridView  
  
 Jsou k dispozici následující ovládací prvky pro úpravy s <xref:System.Windows.Forms.DataGridView> ovládacího prvku:  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 Informace o vytváření vlastních úprav ovládacích prvků najdete v tématu [postup: hostitelské ovládací prvky v systému Windows Forms DataGridView buněk](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
 Následující tabulka ukazuje vztah mezi buňky typy, typy sloupců a ovládací prvky pro úpravy.  
  
|Typ buňky|Hostované ovládací prvek|Typ sloupce|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|není k dispozici|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|není k dispozici|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|není k dispozici|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|není k dispozici|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a>DataGridViewRow  
 <xref:System.Windows.Forms.DataGridViewRow> Třída zobrazí pole záznam dat z data ukládat do kterého <xref:System.Windows.Forms.DataGridView> ovládací prvek připojen. Dostanete <xref:System.Windows.Forms.DataGridView> řádek ovládacího prvku pomocí <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekce. Máte přístup k vybrané řádky pomocí <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> kolekce. Následující objektový model ukazuje toto využití a zobrazuje <xref:System.Windows.Forms.DataGridViewRow> hierarchie dědičnosti.  
  
 ![Model objektu DataGridViewRow](../../../../docs/framework/winforms/controls/media/datagridviewrow.gif "DataGridViewRow")  
DataGridViewRow objektový model  
  
 Odvozujete vlastních typů z <xref:System.Windows.Forms.DataGridViewRow> třídy, i když to není obvykle nutné. <xref:System.Windows.Forms.DataGridView> Ovládací prvek má několik řádků související události a vlastnosti pro přizpůsobení chování jeho <xref:System.Windows.Forms.DataGridViewRow> objekty.  
  
 Pokud povolíte <xref:System.Windows.Forms.DataGridView> ovládacího prvku <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> vlastnost, zvláštní řádek pro přidání nové řádky se zobrazí jako poslední řádek. Tento řádek je součástí <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekce, ale má zvláštní funkce, které můžou vyžadovat vaši pozornost. Další informace najdete v tématu [použití řádku pro nové záznamy v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 [Přizpůsobení ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [Použití řádku pro nové záznamy v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
