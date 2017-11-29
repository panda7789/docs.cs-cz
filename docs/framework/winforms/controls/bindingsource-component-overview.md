---
title: "BindingSource – přehled komponenty"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, data binding
- controls [Windows Forms], binding to data
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: be838caf-fcb0-4b68-827f-58b2c04b747f
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cf46a3d5207f3414bc8abd5fd7bdb904e91f07d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="bindingsource-component-overview"></a>BindingSource – přehled komponenty
<xref:System.Windows.Forms.BindingSource> Součásti je určen ke zjednodušení procesu vytvoření vazby ovládacích prvků pro příslušný zdroj dat. <xref:System.Windows.Forms.BindingSource> Součást funguje jako kanál a zdroj dat pro další ovládací prvky pro vazbu. Poskytuje abstrakci svého formuláře datové připojení při předávání pomocí příkazů do seznamu základní data. Kromě toho můžete data přidat do něj tak, aby sám komponentou funguje jako zdroj dat.  
  
## <a name="bindingsource-component-as-an-intermediary"></a>BindingSource – komponenta jako prostředník  
 <xref:System.Windows.Forms.BindingSource> Součást funguje jako zdroj dat pro některé nebo všechny ovládací prvky na formuláři. V sadě Visual Studio <xref:System.Windows.Forms.BindingSource> může být svázán s ovládacím prostřednictvím `DataBindings` vlastnosti, která je přístupná ze **vlastnosti** okno. Viz také [postupy: vytvoření vazby ovládacích prvků Windows Forms s BindingSource součást pomocí návrháře](../../../../docs/framework/winforms/controls/bind-wf-controls-with-the-bindingsource.md).  
  
 Můžete vázat <xref:System.Windows.Forms.BindingSource> součásti na obou jednoduché datové zdroje, jako jedinou vlastnost objektu nebo kolekci základní jako <xref:System.Collections.ArrayList>a složitých datových zdrojů, například databázové tabulky. <xref:System.Windows.Forms.BindingSource> Součást slouží jako prostředník, který poskytuje služby správy vazbu a měny. V době návrhu nebo dobu spuštění, můžete vázat <xref:System.Windows.Forms.BindingSource> součásti ke zdroji dat komplexní nastavením jeho <xref:System.Windows.Forms.BindingSource.DataSource%2A> a <xref:System.Windows.Forms.BindingSource.DataMember%2A> vlastností databáze a tabulky, v uvedeném pořadí. Následující obrázek ukazuje, kde <xref:System.Windows.Forms.BindingSource> součást zapadá do stávající architektura datové vazby.  
  
 ![Vytvoření vazby zdroje a architektura datové vazby](../../../../docs/framework/winforms/controls/media/net-bindsrcdatabindarch.gif "NET_BindSrcDataBindArch")  
  
> [!NOTE]
>  V době návrhu jsou některé akce, například databázové tabulky přetažení z okna data do prázdného formuláře, vytvoří <xref:System.Windows.Forms.BindingSource> součást navázat jej na podkladový zdroj dat a přidejte data ovládacích prvcích všechny v rámci jedné operace. Viz také [vazby Windows Forms – ovládací prvky k datům v sadě Visual Studio](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio).  
  
## <a name="bindingsource-component-as-a-data-source"></a>BindingSource – komponenta jako zdroj dat  
 Pokud spustíte přidávání položek do <xref:System.Windows.Forms.BindingSource> součást bez první zadat seznam bylo vázané na komponentu bude fungovat stejně jako zdroj dat styl seznamu a přijmout tyto přidat položky.  
  
 Kromě toho můžete napsat kód pro poskytují vlastní funkce "AddNew" prostřednictvím <xref:System.Windows.Forms.BindingSource.AddingNew> událost, která se vyvolá, když <xref:System.Windows.Forms.BindingSource.AddNew%2A> metoda je volána před položku přidávanou do seznamu. Další informace najdete v tématu [architektura součásti BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component-architecture.md).  
  
## <a name="navigation"></a>Navigace  
 Pro uživatele, kteří potřebují data ve formuláři, přejděte <xref:System.Windows.Forms.BindingNavigator> součást umožňuje přejděte a pracovat s daty v koordinaci s <xref:System.Windows.Forms.BindingSource> součásti. Další informace najdete v tématu [BindingNavigator – ovládací prvek](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md).  
  
## <a name="data-manipulation"></a>Manipulace s daty  
 Na: <xref:System.Windows.Forms.BindingSource> funguje jako <xref:System.Windows.Forms.CurrencyManager> pro všechny jeho vazby a můžete je tedy poskytnout přístup k měny a pozice informace o zdroji dat. Následující tabulka uvádí členy, který <xref:System.Windows.Forms.BindingSource> součást poskytuje pro přístup k informacím a manipulace s základní data.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Current%2A>Vlastnost|Získá aktuální položku datového zdroje.|  
|<xref:System.Windows.Forms.BindingSource.Position%2A>Vlastnost|Získá nebo nastaví aktuální pozici v podkladový seznam.|  
|<xref:System.Windows.Forms.BindingSource.List%2A>Vlastnost|Získá seznam, který je vyhodnocení <xref:System.Windows.Forms.BindingSource.DataSource%2A> a <xref:System.Windows.Forms.BindingSource.DataMember%2A> vyhodnocení. Pokud <xref:System.Windows.Forms.BindingSource.DataMember%2A> není nastavený, vrátí seznam určeného <xref:System.Windows.Forms.BindingSource.DataSource%2A>.|  
|<xref:System.Windows.Forms.BindingSource.Insert%2A>– Metoda|Vloží položku v seznamu v zadaném indexu.|  
|<xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A>– Metoda|Odebere aktuální položku ze seznamu.|  
|<xref:System.Windows.Forms.BindingSource.EndEdit%2A>– Metoda|Platí pro daný zdroj dat. změny čekající na zpracování.|  
|<xref:System.Windows.Forms.BindingSource.CancelEdit%2A>– Metoda|Zruší aktuální operace upravit.|  
|<xref:System.Windows.Forms.BindingSource.AddNew%2A>– Metoda|Přidá novou položku do podkladový seznam. Pokud zdroj dat implementuje <xref:System.ComponentModel.IBindingList> a vrátí položku z <xref:System.Windows.Forms.BindingSource.AddingNew> událostí, přidá tato položka. V opačném požadavek je předán do seznamu <xref:System.ComponentModel.IBindingList.AddNew%2A> metoda. Pokud není podkladový seznam <xref:System.ComponentModel.IBindingList>, položky se automaticky vytvoří přes jeho veřejné výchozí konstruktor.|  
  
## <a name="sorting-and-filtering"></a>Řazení a filtrování  
 By měl obvykle, pracovat seřazené nebo filtrované zobrazení zdroje dat. Následující tabulka uvádí členy, který <xref:System.Windows.Forms.BindingSource> poskytuje zdroj dat součástí.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Sort%2A>Vlastnost|Pokud je zdroj dat <xref:System.ComponentModel.IBindingList>, získá nebo nastaví název sloupce sloužící k řazení a informace o pořadí řazení. Pokud je zdroj dat <xref:System.ComponentModel.IBindingListView> a podporuje rozšířené, řazení, získá více názvů sloupců použít pro řazení a informace o pořadí řazení|  
|<xref:System.Windows.Forms.BindingSource.Filter%2A>Vlastnost|Pokud je zdroj dat <xref:System.ComponentModel.IBindingListView>, získá nebo nastaví výraz použitý pro filtrování, jsou-li zobrazit řádky.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [Architektura součásti BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component-architecture.md)  
 [BindingSource – komponenta](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [BindingNavigator – ovládací prvek](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [Windows Forms – datová vazba](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Ovládací prvky používané ve formulářích Windows](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
