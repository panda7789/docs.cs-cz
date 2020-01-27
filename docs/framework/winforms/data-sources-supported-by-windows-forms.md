---
title: Podporované zdroje dat
ms.date: 03/30/2017
helpviewer_keywords:
- collections [Windows Forms], binding to
- OLE DB providers [Windows Forms], Windows Forms
- DataTable class [Windows Forms], binding and Windows Forms
- Windows Forms, data binding
- DataView class [Windows Forms], binding and Windows Forms
- DataViewManager class [Windows Forms], binding and Windows Forms
- Windows Forms, source data
- arrays [Windows Forms]
- data sources [Windows Forms]
- data providers [Windows Forms]
- DataSet class [Windows Forms], binding and Windows Forms
- data [Windows Forms], data providers
ms.assetid: 3d2c43f6-462b-4d35-9c86-13e9afe012e1
ms.openlocfilehash: 83ce4bb0d6f0bf81bcad4e38af212dccc3483ca5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742309"
---
# <a name="data-sources-supported-by-windows-forms"></a>Zdroje dat podporované rozhraním Windows Forms
V rámci aplikací se tradičně používaly datové vazby, které využívají data uložená v databázích. Pomocí model Windows Forms datové vazby můžete získat přístup k datům z databází i k datům v jiných strukturách, jako jsou například pole a kolekce, tak dlouho, jak byly splněny určité minimální požadavky.  
  
## <a name="structures-to-bind-to"></a>Struktury, na které se má vytvořit vazba  
 V model Windows Forms můžete vytvořit vazbu na širokou škálu struktur, od jednoduchých objektů (jednoduchá vazba) až po komplexní seznamy, jako jsou tabulky dat ADO.NET (komplexní vazby). Pro jednoduchou vazbu model Windows Forms podporuje vazbu na veřejné vlastnosti jednoduchého objektu. Model Windows Forms vazba na základě seznamu obvykle vyžaduje, aby objekt podporoval rozhraní <xref:System.Collections.IList> nebo rozhraní <xref:System.ComponentModel.IListSource>. Kromě toho, pokud vytváříte vazbu pomocí <xref:System.Windows.Forms.BindingSource> komponenty, můžete vytvořit vazbu na objekt, který podporuje rozhraní <xref:System.Collections.IEnumerable>. Další informace o rozhraních souvisejících s datovou vazbou najdete v tématu [rozhraní související s datovou vazbou](interfaces-related-to-data-binding.md).  
  
 Následující seznam obsahuje struktury, se kterými můžete vytvořit vazby v model Windows Forms.  
  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingSource> je nejběžnější model Windows Forms zdroj dat a funguje proxy mezi zdrojem dat a ovládacími prvky model Windows Forms. Obecný <xref:System.Windows.Forms.BindingSource> vzor použití je Svázání ovládacích prvků s <xref:System.Windows.Forms.BindingSource> a svázání <xref:System.Windows.Forms.BindingSource> se zdrojem dat (například tabulka dat ADO.NET nebo obchodní objekt). <xref:System.Windows.Forms.BindingSource> poskytuje služby, které umožňují a zlepšují úroveň podpory datových vazeb. Například model Windows Forms ovládací prvky založené na seznamu jako <xref:System.Windows.Forms.DataGridView> a <xref:System.Windows.Forms.ComboBox> nepodporují přímo vazby na <xref:System.Collections.IEnumerable> zdroje dat, ale můžete tento scénář povolit vazbou prostřednictvím <xref:System.Windows.Forms.BindingSource>. V takovém případě <xref:System.Windows.Forms.BindingSource> převede zdroj dat na <xref:System.Collections.IList>.  
  
 Jednoduché objekty  
 Model Windows Forms podporuje vlastnosti ovládacího prvku datové vazby na veřejné vlastnosti instance objektu pomocí <xref:System.Windows.Forms.Binding>ho typu. Model Windows Forms podporuje i ovládací prvky založené na seznamu, jako je například <xref:System.Windows.Forms.ListControl> instance objektu při použití <xref:System.Windows.Forms.BindingSource>.  
  
 pole nebo kolekce  
 Aby fungoval jako zdroj dat, musí seznam implementovat rozhraní <xref:System.Collections.IList>; jedním z příkladů může být pole, které je instancí třídy <xref:System.Array>. Další informace o polích naleznete v tématu [How to: Create a Array of Objects (Visual Basic)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/487y7874(v=vs.100)).  
  
 Obecně platí, že při vytváření seznamů objektů pro datovou vazbu byste měli použít <xref:System.ComponentModel.BindingList%601>. <xref:System.ComponentModel.BindingList%601> je obecná verze <xref:System.ComponentModel.IBindingList> rozhraní. Rozhraní <xref:System.ComponentModel.IBindingList> rozšiřuje rozhraní <xref:System.Collections.IList> přidáním vlastností, metod a událostí nezbytných pro obousměrnou datovou vazbu.  
  
 <xref:System.Collections.IEnumerable>  
 Ovládací prvky model Windows Forms mohou být vázány na zdroje dat, které podporují pouze rozhraní <xref:System.Collections.IEnumerable>, jsou-li svázány prostřednictvím součásti <xref:System.Windows.Forms.BindingSource>.  
  
 Datové objekty ADO.NET  
 ADO.NET poskytuje řadu datových struktur vhodných pro vytvoření vazby. Jednotlivé sofistikovanější a složitost se liší.  
  
- <xref:System.Data.DataColumn>. <xref:System.Data.DataColumn> je základním stavebním blokem <xref:System.Data.DataTable>v tom, že řada sloupců sestává z tabulky. Každé <xref:System.Data.DataColumn> má vlastnost <xref:System.Data.DataColumn.DataType%2A>, která určuje druh dat, které sloupec obsahuje (například značka auto v tabulce popisující automobily). Můžete vytvořit jednoduchou datovou kopii ovládacího prvku (například vlastnost <xref:System.Windows.Forms.Control.Text%2A> ovládacího prvku <xref:System.Windows.Forms.TextBox>) do sloupce v tabulce dat.  
  
- <xref:System.Data.DataTable>. <xref:System.Data.DataTable> je reprezentace tabulky s řádky a sloupci v ADO.NET. Tabulka dat obsahuje dvě kolekce: <xref:System.Data.DataColumn>reprezentující sloupce dat v dané tabulce (které nakonec určují typy dat, které lze do této tabulky zadat) a <xref:System.Data.DataRow>představují řádky dat v dané tabulce. Můžete složitě svázat ovládací prvek s informacemi obsaženými v tabulce dat (například svázat ovládací prvek <xref:System.Windows.Forms.DataGridView> s datovou tabulkou). Pokud však vytvoříte vazbu na <xref:System.Data.DataTable>, jste skutečně vázáni na výchozí zobrazení tabulky.  
  
- <xref:System.Data.DataView>. <xref:System.Data.DataView> je vlastní pohled na jednu tabulku dat, která se může filtrovat nebo řadit. Zobrazení dat je datový "snímek", který používají ovládací prvky se složitými vazbami. Data v zobrazení dat můžete jednoduše svázat nebo složitě svázat, ale uvědomte si, že vytváříte místo čistého a aktualizovaného zdroje dat vazbu na pevný obrázek dat.  
  
- <xref:System.Data.DataSet>. <xref:System.Data.DataSet> je kolekce tabulek, relací a omezení dat v databázi. Data v datové sadě můžete jednoduše svázat nebo složitě svázat, ale nezapomeňte, že vytváříte vazbu na výchozí <xref:System.Data.DataViewManager> pro <xref:System.Data.DataSet> (viz další odrážka).  
  
- <xref:System.Data.DataViewManager>. <xref:System.Data.DataViewManager> je přizpůsobené zobrazení celého <xref:System.Data.DataSet>, které je podobné <xref:System.Data.DataView>, ale včetně zahrnutých vztahů. Pomocí kolekce <xref:System.Data.DataViewManager.DataViewSettings%2A> můžete nastavit výchozí filtry a možnosti řazení pro všechna zobrazení, která má <xref:System.Data.DataViewManager> pro danou tabulku.  
  
## <a name="see-also"></a>Viz také:

- [Oznámení změn v datové vazbě Windows Forms](change-notification-in-windows-forms-data-binding.md)
- [Datové vazby a Windows Forms](data-binding-and-windows-forms.md)
- [Windows Forms – datová vazba](windows-forms-data-binding.md)
