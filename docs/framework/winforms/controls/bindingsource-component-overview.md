---
title: BindingSource – přehled komponenty
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, data binding
- controls [Windows Forms], binding to data
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: be838caf-fcb0-4b68-827f-58b2c04b747f
ms.openlocfilehash: 2237ba71487afc132f9164243a664b277397ccfa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098634"
---
# <a name="bindingsource-component-overview"></a>BindingSource – přehled komponenty
<xref:System.Windows.Forms.BindingSource> Komponenta je navržené pro zjednodušení procesu vytvoření vazby ovládacích prvků do podkladového zdroje dat. <xref:System.Windows.Forms.BindingSource> Komponenty funguje jako kanál a zdroj dat pro další ovládací prvky k vytvoření vazby. Poskytuje abstrakci připojení dat formuláře při předání prostřednictvím příkazů do seznamu podkladová data. Kromě toho můžete přidat data přímo do ní, tak, aby sám komponentou funguje jako zdroj dat.  
  
## <a name="bindingsource-component-as-an-intermediary"></a>BindingSource – komponenta jako prostředník  
 <xref:System.Windows.Forms.BindingSource> Komponenty slouží jako zdroj dat pro některé nebo všechny ovládací prvky ve formuláři. V sadě Visual Studio <xref:System.Windows.Forms.BindingSource> mohou být vázány na ovládací prvek prostřednictvím `DataBindings` vlastnost, která je přístupná **vlastnosti** okna. Viz také [jak: Vytvoření vazby ovládacích prvků Windows Forms ke komponentě BindingSource pomocí návrháře](bind-wf-controls-with-the-bindingsource.md).  
  
 Můžete vytvořit vazbu <xref:System.Windows.Forms.BindingSource> komponentu obou jednoduché datové zdroje, jako je jedinou vlastností objektu nebo kolekci základní, jako je <xref:System.Collections.ArrayList>a komplexních datových zdrojů, jako jsou databázové tabulky. <xref:System.Windows.Forms.BindingSource> Komponenty slouží jako zprostředkovatel, který poskytuje služby pro správu vazeb a měny. V době návrhu nebo běhu, můžete vytvořit vazbu <xref:System.Windows.Forms.BindingSource> komponentu ke zdroji dat komplexní nastavením jeho <xref:System.Windows.Forms.BindingSource.DataSource%2A> a <xref:System.Windows.Forms.BindingSource.DataMember%2A> vlastnosti do databáze a tabulky, v uvedeném pořadí. Následující obrázek ukazuje, kde <xref:System.Windows.Forms.BindingSource> komponenty zapadá do se stávající architekturou datové vazby.  
  
 ![Vytvoření vazby zdroje a datové vazby architektura](./media/net-bindsrcdatabindarch.gif "NET_BindSrcDataBindArch")  
  
> [!NOTE]
>  V době návrhu, se některé akce, jako jsou databázové tabulce přetažení z okna data do prázdného formuláře, vytvoří <xref:System.Windows.Forms.BindingSource> komponenty, vázat na podkladový zdroj dat a přidání ovládacích prvků s ohledem na data v rámci jedné operace. Viz také [ovládací prvky vazby Windows Forms k datům v sadě Visual Studio](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio).  
  
## <a name="bindingsource-component-as-a-data-source"></a>BindingSource – komponenta jako zdroj dat  
 Pokud začnete přidávat položky, které chcete <xref:System.Windows.Forms.BindingSource> komponenty bez první zadaného seznamu vázaný na komponentu bude fungovat jako zdroj dat list-style a přijmout tyto přidali položky.  
  
 Kromě toho můžete napsat kód k zajištění vlastní funkce "Funkce operací AddNew" prostřednictvím <xref:System.Windows.Forms.BindingSource.AddingNew> událost, která je vyvolána při <xref:System.Windows.Forms.BindingSource.AddNew%2A> metoda je volána před položku přidávanou do seznamu. Další informace najdete v tématu [architektura komponenty BindingSource](bindingsource-component-architecture.md).  
  
## <a name="navigation"></a>Navigace  
 Pro uživatele, kteří potřebují data ve formuláři, přejděte <xref:System.Windows.Forms.BindingNavigator> komponenty umožňuje navigaci a manipulaci s daty ve spolupráci s <xref:System.Windows.Forms.BindingSource> komponenty. Další informace najdete v tématu [BindingNavigator – ovládací prvek](bindingnavigator-control-windows-forms.md).  
  
## <a name="data-manipulation"></a>Manipulace s daty  
 Na: <xref:System.Windows.Forms.BindingSource> funguje jako <xref:System.Windows.Forms.CurrencyManager> pro všemi jeho vazby a může proto poskytnout přístup k měn a pozice informace týkající se zdroji dat. Následující tabulka uvádí členy, které <xref:System.Windows.Forms.BindingSource> součást poskytuje přístup k a manipulaci s podkladová data.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Current%2A> property|Získá aktuální položku datového zdroje.|  
|<xref:System.Windows.Forms.BindingSource.Position%2A> property|Získá nebo nastaví aktuální pozici v nadřízeném seznamu.|  
|<xref:System.Windows.Forms.BindingSource.List%2A> property|Získá seznam, který je po vyhodnocení <xref:System.Windows.Forms.BindingSource.DataSource%2A> a <xref:System.Windows.Forms.BindingSource.DataMember%2A> hodnocení. Pokud <xref:System.Windows.Forms.BindingSource.DataMember%2A> není nastavena, vrací seznam určené <xref:System.Windows.Forms.BindingSource.DataSource%2A>.|  
|<xref:System.Windows.Forms.BindingSource.Insert%2A> – metoda|Vloží položku v seznamu na zadaném indexu.|  
|<xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> – metoda|Odebere aktuální položky ze seznamu.|  
|<xref:System.Windows.Forms.BindingSource.EndEdit%2A> – metoda|Podkladový zdroj dat se týká čekající změny.|  
|<xref:System.Windows.Forms.BindingSource.CancelEdit%2A> – metoda|Zruší aktuální operaci úprav.|  
|<xref:System.Windows.Forms.BindingSource.AddNew%2A> – metoda|Přidá novou položku do seznamu základní. Pokud zdroj dat implementuje <xref:System.ComponentModel.IBindingList> a vrátí položku ze <xref:System.Windows.Forms.BindingSource.AddingNew> události, přidá tuto položku. V opačném případě požadavek je předán do seznamu <xref:System.ComponentModel.IBindingList.AddNew%2A> metody. Pokud je podkladový seznam <xref:System.ComponentModel.IBindingList>, položka je automaticky vytvořená prostřednictvím jeho veřejný výchozí konstruktor.|  
  
## <a name="sorting-and-filtering"></a>Řazení a filtrování  
 Obvykle byste měli spolupracovat s zobrazení zdroje dat o seřazený a filtrovaný. Následující tabulka uvádí členy, které <xref:System.Windows.Forms.BindingSource> poskytuje zdroj dat součástí.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Sort%2A> property|Pokud je zdroj dat <xref:System.ComponentModel.IBindingList>, získá nebo nastaví název sloupce pro řazení a informace o pořadí řazení. Pokud je zdroj dat <xref:System.ComponentModel.IBindingListView> a podporuje rozšířené řazení, získá více názvů sloupců použité pro řazení a informace o pořadí řazení|  
|<xref:System.Windows.Forms.BindingSource.Filter%2A> property|Pokud je zdroj dat <xref:System.ComponentModel.IBindingListView>, získá nebo nastaví výraz určený k filtrování, které řádky jsou zobrazeny.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [Architektura součásti BindingSource](bindingsource-component-architecture.md)
- [BindingSource – komponenta](bindingsource-component.md)
- [Ovládací prvek BindingNavigator](bindingnavigator-control-windows-forms.md)
- [Windows Forms – datová vazba](../windows-forms-data-binding.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
