---
title: Zdroje dat podporované rozhraním Windows Forms
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
ms.openlocfilehash: aee15d8d40ddd3f928c8bc5396d8bcbff17ba533
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43562688"
---
# <a name="data-sources-supported-by-windows-forms"></a>Zdroje dat podporované rozhraním Windows Forms
Tradičně datové vazby používá v rámci aplikací využít data uložená v databázích. Pomocí Windows Forms – datová vazba, můžou k datům z databází, stejně jako data v jiných strukturách, jako jsou pole a kolekce, tak dlouho, dokud jsou splněné určité minimální požadavky.  
  
## <a name="structures-to-bind-to"></a>Struktury tak, aby vazba na  
 Ve Windows Forms, můžete vázat na širokou škálu struktury, od jednoduchého objekty (jednoduchá vazba) pro komplexní seznamů, jako jsou tabulky dat ADO.NET (komplexní vazby). Pro jednoduché vazby Windows Forms podporuje vazbu na veřejné vlastnosti u jednoduchého objektu. Vazba na základě seznamu Windows Forms obvykle vyžaduje, aby podporoval objektu <xref:System.Collections.IList> rozhraní nebo <xref:System.ComponentModel.IListSource> rozhraní. Navíc pokud vytváříte vazbu s prostřednictvím <xref:System.Windows.Forms.BindingSource> součásti, můžete vázat na objekt, který podporuje <xref:System.Collections.IEnumerable> rozhraní. Další informace o rozhraní související s datovou vazbu, naleznete v tématu [rozhraní související s datovou vazbu](../../../docs/framework/winforms/interfaces-related-to-data-binding.md).  
  
 Následující seznam obsahuje struktury že lze svázat ve Windows Forms.  
  
 <xref:System.Windows.Forms.BindingSource>  
 A <xref:System.Windows.Forms.BindingSource> je nejběžnější zdroje dat Windows Forms a funguje proxy mezi zdroji dat a ovládacích prvků Windows Forms. Obecné <xref:System.Windows.Forms.BindingSource> vzor využití je k vytvoření vazby ovládacích prvků na <xref:System.Windows.Forms.BindingSource> a vytvořit vazbu <xref:System.Windows.Forms.BindingSource> ke zdroji dat (například tabulku dat ADO.NET nebo obchodní objekt). <xref:System.Windows.Forms.BindingSource> Poskytuje služby, které umožňují a zvýšení úrovně datové vazby podpory. Například seznamu Windows Forms podle ovládací prvky, jako <xref:System.Windows.Forms.DataGridView> a <xref:System.Windows.Forms.ComboBox> přímo nepodporuje vazbu na <xref:System.Collections.IEnumerable> zdroje dat ale můžete povolit tento scénář vazbou prostřednictvím <xref:System.Windows.Forms.BindingSource>. V takovém případě <xref:System.Windows.Forms.BindingSource> převede zdroje dat <xref:System.Collections.IList>.  
  
 Jednoduché objekty  
 Windows Forms podporuje vlastnosti datové vazby ovládacího prvku na veřejné vlastnosti na instanci objektu pomocí <xref:System.Windows.Forms.Binding> typu. Windows Forms také podporuje vazba ovládacích prvků na základě seznamu, například <xref:System.Windows.Forms.ListControl> na objekt instance, kdy <xref:System.Windows.Forms.BindingSource> se používá.  
  
 pole nebo kolekce  
 Tak, aby fungoval jako zdroj dat, musí implementovat seznam <xref:System.Collections.IList> rozhraní, ale s jedním Příkladem může být pole, které je instance <xref:System.Array> třídy. Další informace o polích naleznete v tématu [postupy: vytvoření objekty z pole (Visual Basic)](https://msdn.microsoft.com/library/6b64e069-0387-400c-9081-3bdc581020c3).  
  
 Obecně byste měli použít <xref:System.ComponentModel.BindingList%601> při vytváření seznamů objektů pro vytváření datových vazeb. <xref:System.ComponentModel.BindingList%601> je obecný verze <xref:System.ComponentModel.IBindingList> rozhraní. <xref:System.ComponentModel.IBindingList> Rozhraní rozšiřuje <xref:System.Collections.IList> rozhraní přidáním vlastnosti, metody a události, které jsou nezbytné pro obousměrný datovou vazbu.  
  
 <xref:System.Collections.IEnumerable>  
 Ovládací prvky Windows Forms může být vázaný na zdroje dat, které podporují jenom <xref:System.Collections.IEnumerable> rozhraní, pokud jsou svázán prostřednictvím <xref:System.Windows.Forms.BindingSource> komponenty.  
  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] datové objekty  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] poskytuje několik datových struktur, které jsou vhodné pro vazbu. Každý se liší v její vyspělosti a složitost.  
  
-   <xref:System.Data.DataColumn>. A <xref:System.Data.DataColumn> je základní stavební blok <xref:System.Data.DataTable>, v tom, že zahrnují počet sloupců tabulky. Každý <xref:System.Data.DataColumn> má <xref:System.Data.DataColumn.DataType%2A> vlastnost, která určuje, jaká data obsahuje sloupec (například zkontrolujte automobilu v tabulce s popisem auta). Vám může jednoduché vytvořit vazbu ovládacího prvku (například <xref:System.Windows.Forms.TextBox> ovládacího prvku <xref:System.Windows.Forms.Control.Text%2A> vlastnost) na sloupec v tabulce dat.  
  
-   <xref:System.Data.DataTable>. A <xref:System.Data.DataTable> je reprezentace tabulku s řádky a sloupce v [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]. Tabulka dat obsahuje dvě kolekce: <xref:System.Data.DataColumn>, představující sloupce dat v dané tabulce (což nakonec určit druh dat, který lze zadat do tabulky), a <xref:System.Data.DataRow>, představující řádky dat z dané tabulky. Vám může komplexní Vazba ovládacího prvku na informace obsažené v tabulce dat (jako je například vazby <xref:System.Windows.Forms.DataGridView> ovládací prvek tabulka dat). Nicméně pokud svážete <xref:System.Data.DataTable>, jsou ve skutečnosti vazby do výchozího zobrazení tabulky.  
  
-   <xref:System.Data.DataView>. A <xref:System.Data.DataView> je přizpůsobené zobrazení jedné tabulky datového, která mohou filtrovat a řadit. Zobrazení dat jsou data "snímku" používané ovládací prvky vázané na komplexní. Můžete vazby jednoduché nebo komplexní vazby k datům v rámci zobrazení dat, ale mějte na paměti, že jsou vytvoření vazby na pevnou "obrázek" data spíše než zdroj čisté, aktualizace dat.  
  
-   <xref:System.Data.DataSet>. A <xref:System.Data.DataSet> je kolekce tabulky, relace a omezení dat v databázi. Můžete vazby jednoduché nebo komplexní vazby k datům v datové sadě, ale mějte na paměti, že jsou vazby na výchozí hodnotu <xref:System.Data.DataViewManager> pro <xref:System.Data.DataSet> (viz následující odrážka).  
  
-   <xref:System.Data.DataViewManager>. A <xref:System.Data.DataViewManager> je přizpůsobené zobrazení celého <xref:System.Data.DataSet>, obdobná <xref:System.Data.DataView>, ale s vztahy zahrnuté. S <xref:System.Data.DataViewManager.DataViewSettings%2A> kolekci, můžete nastavit výchozí filtry a možnosti řazení pro všechna zobrazení, která <xref:System.Data.DataViewManager> má pro danou tabulku.  
  
## <a name="see-also"></a>Viz také  
 [Oznámení změn v datové vazbě Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [Datové vazby a Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Windows Forms – datová vazba](../../../docs/framework/winforms/windows-forms-data-binding.md)
