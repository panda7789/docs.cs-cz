---
title: "Zdroje dat podporované rozhraním Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d2c1c021759c7032257e95eb2cad202a461dc05
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="data-sources-supported-by-windows-forms"></a>Zdroje dat podporované rozhraním Windows Forms
Datová vazba tradičně, už je použité v aplikacích využít dat uložených v databázích. S Windows Forms – datová vazba, můžete přístup k datům z databáze a také data v jiných struktur, jako je například pole a kolekcí, tak dlouho, dokud byly splněny určité minimální požadavky.  
  
## <a name="structures-to-bind-to"></a>Struktury pro vazbu na  
 V systému Windows Forms, můžete vázat na širokou škálu struktury, od jednoduchého objekty (jednoduchá vazba) pro komplexní seznamy například tabulky dat ADO.NET (komplexní vazba). Windows Forms pro jednoduchá vazba podporuje vazbu na veřejné vlastnosti na jednoduchého objektu. Vazba na základě seznamu Windows Forms obvykle vyžaduje, aby podporoval objektu <xref:System.Collections.IList> rozhraní nebo <xref:System.ComponentModel.IListSource> rozhraní. Kromě toho pokud vytváříte vazbu s prostřednictvím <xref:System.Windows.Forms.BindingSource> součásti, můžete vázat na objekt, který podporuje <xref:System.Collections.IEnumerable> rozhraní. Další informace o rozhraní související s datovou vazbu najdete v tématu [rozhraní související s datovou vazbu](../../../docs/framework/winforms/interfaces-related-to-data-binding.md).  
  
 Následující seznam obsahuje struktury že můžete vázat na ve Windows Forms.  
  
 <xref:System.Windows.Forms.BindingSource>  
 A <xref:System.Windows.Forms.BindingSource> je nejběžnější zdroj dat Windows Forms a funguje proxy server mezi zdrojem dat a ovládací prvky Windows Forms. Obecné <xref:System.Windows.Forms.BindingSource> vzor používání je pro vaše ovládací prvky pro vazbu <xref:System.Windows.Forms.BindingSource> a vytvořte vazbu <xref:System.Windows.Forms.BindingSource> ke zdroji dat (například ADO.NET data tabulky nebo objekt firmy). <xref:System.Windows.Forms.BindingSource> Poskytuje služby, které umožňují a zvýšit úroveň datové vazby podpory. Například seznamu Windows Forms na základě ovládací prvky, jako <xref:System.Windows.Forms.DataGridView> a <xref:System.Windows.Forms.ComboBox> přímo nepodporují vazbu k <xref:System.Collections.IEnumerable> zdroje dat ale můžete povolit tento scénář v vazbě prostřednictvím <xref:System.Windows.Forms.BindingSource>. V takovém případě <xref:System.Windows.Forms.BindingSource> převede zdroje dat pro <xref:System.Collections.IList>.  
  
 Jednoduché objekty  
 Windows Forms podporuje ovládací prvek vlastnosti datové vazby k veřejné vlastnosti na instanci objektu pomocí <xref:System.Windows.Forms.Binding> typu. Windows Forms také podporuje vazba ovládacích prvků na základě seznamu, například <xref:System.Windows.Forms.ListControl> k objektu instance, kdy <xref:System.Windows.Forms.BindingSource> se používá.  
  
 pole nebo kolekce  
 Tak, aby fungoval jako zdroj dat, musí implementovat seznam <xref:System.Collections.IList> rozhraní; jeden Příkladem může být pole, které je instance <xref:System.Array> třídy. Další informace o pole najdete v tématu [postupy: vytvoření objekty z pole (Visual Basic)](http://msdn.microsoft.com/en-us/6b64e069-0387-400c-9081-3bdc581020c3).  
  
 Obecně platí, měli byste použít <xref:System.ComponentModel.BindingList%601> při vytváření seznamů objektů pro datovou vazbu. <xref:System.ComponentModel.BindingList%601>je obecná verze <xref:System.ComponentModel.IBindingList> rozhraní. <xref:System.ComponentModel.IBindingList> Rozšiřuje rozhraní <xref:System.Collections.IList> rozhraní přidáním vlastnosti, metod a události, které jsou nezbytné pro dvoucestné datovou vazbu.  
  
 <xref:System.Collections.IEnumerable>  
 Ovládací prvky Windows Forms mohou být vázány na zdroje dat, které podporují pouze <xref:System.Collections.IEnumerable> rozhraní, pokud je vázána prostřednictvím <xref:System.Windows.Forms.BindingSource> součásti.  
  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]datové objekty  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]poskytuje řadu datové struktury vhodný vazba. Každý se liší v její vyspělosti a složitost.  
  
-   <xref:System.Data.DataColumn>. A <xref:System.Data.DataColumn> je základní stavební blok <xref:System.Data.DataTable>, v tom, že počet sloupců tvoří tabulku. Každý <xref:System.Data.DataColumn> má <xref:System.Data.DataColumn.DataType%2A> vlastnost, která určuje, jaké dat sloupce blokování (například značku automobilu v tabulce popisující aut). Vám může jednoduchý vytvořit vazbu ovládacího prvku (například <xref:System.Windows.Forms.TextBox> ovládacího prvku <xref:System.Windows.Forms.Control.Text%2A> vlastnost) na sloupec v tabulce data.  
  
-   <xref:System.Data.DataTable>. A <xref:System.Data.DataTable> je reprezentace tabulku s řádky a sloupce, v [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]. Datová tabulka obsahuje dvě kolekce: <xref:System.Data.DataColumn>, představující sloupce dat v dané tabulce (který nakonec určení typů dat, kterou lze zadat do této tabulky), a <xref:System.Data.DataRow>, představující řádky dat v dané tabulce. Vám může komplexní vazbu ovládacího prvku na informace obsažené v tabulce dat. (jako je například vazba <xref:System.Windows.Forms.DataGridView> ovládacího prvku do tabulky data). Ale když můžete vytvořit vazbu <xref:System.Data.DataTable>, jsou skutečně vazbu pro výchozí zobrazení v tabulce.  
  
-   <xref:System.Data.DataView>. A <xref:System.Data.DataView> je vlastní pohled na jednu datovou tabulku, která může filtrovat a řadit. Zobrazení dat jsou data "snímek" používané ovládací prvky vázané na komplexní. Můžete vazby jednoduché nebo komplexní vazby na data v rámci zobrazení dat, ale uvědomte si, že vytváříte vazbu s pevnou "obrázek" data místo zdroj dat čistá, aktualizace.  
  
-   <xref:System.Data.DataSet>. A <xref:System.Data.DataSet> je kolekce tabulek, vztahy a omezení dat v databázi. Můžete vazby jednoduché nebo komplexní vazby na data v rámci datové sady, ale mějte na paměti, že vytváříte vazbu na výchozí hodnoty <xref:System.Data.DataViewManager> pro <xref:System.Data.DataSet> (viz další odrážka bodu).  
  
-   <xref:System.Data.DataViewManager>. A <xref:System.Data.DataViewManager> je přizpůsobené zobrazení na celou <xref:System.Data.DataSet>, podobá <xref:System.Data.DataView>, ale s vztahy, které jsou zahrnuty. S <xref:System.Data.DataViewManager.DataViewSettings%2A> kolekce, můžete nastavit výchozí filtrů a řazení možnosti pro všechna zobrazení, <xref:System.Data.DataViewManager> má pro danou tabulku.  
  
## <a name="see-also"></a>Viz také  
 [Oznámení změn v datové vazbě Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [Datové vazby a Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Windows Forms – datová vazba](../../../docs/framework/winforms/windows-forms-data-binding.md)
