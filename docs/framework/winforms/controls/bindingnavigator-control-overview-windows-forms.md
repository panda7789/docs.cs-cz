---
title: BindingNavigator – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- DataNavigator
helpviewer_keywords:
- BindingNavigator control [Windows Forms], about BindingNavigator control
- records [Windows Forms], navigating on a form
- data [Windows Forms], navigating
- data navigation
ms.assetid: 4423eede-f8d1-4d02-822f-5bf8432680d0
ms.openlocfilehash: ad63f622aae55cb4175eddc93ab5e086965a8fe8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59109106"
---
# <a name="bindingnavigator-control-overview-windows-forms"></a>BindingNavigator – přehled ovládacího prvku (Windows Forms)
Můžete použít <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku k vytvoření standardizovaný způsob pro uživatele k vyhledání a měnit data na formuláři Windows. Často používáte <xref:System.Windows.Forms.BindingNavigator> s <xref:System.Windows.Forms.BindingSource> komponenty, aby uživatelům procházení datových záznamů ve formuláři a interakci se záznamy.  
  
## <a name="how-the-bindingnavigator-works"></a>Jak funguje BindingNavigator  

 <xref:System.Windows.Forms.BindingNavigator> Ovládací prvek se skládá z <xref:System.Windows.Forms.ToolStrip> s řadou <xref:System.Windows.Forms.ToolStripItem> objekty pro většinu běžné akce související s daty: přidání dat, odstranění dat a procházet data. Ve výchozím nastavení <xref:System.Windows.Forms.BindingNavigator> ovládací prvek obsahuje tyto standardní tlačítka. Následující snímek obrazovky ukazuje <xref:System.Windows.Forms.BindingNavigator> ovládací prvek na formuláři:
  
 ![Snímek obrazovky zobrazující BindingNavigator – ovládací prvek.](./media/bindingnavigator-control-overview-windows-forms/bindingnavigator-control-form.gif)  
  
 V následující tabulce jsou uvedeny ovládací prvky a popisuje jejich funkce.  
  
|Control|Funkce|  
|-------------|--------------|  
|<xref:System.Windows.Forms.BindingNavigator.AddNewItem%2A> Tlačítko|Vloží nový řádek do podkladového zdroje dat.|  
|<xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> Tlačítko|Odstraní z podkladového zdroje dat na aktuálním řádku.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> Tlačítko|Přesune na první položku v podkladovém zdroji dat|  
|<xref:System.Windows.Forms.BindingNavigator.MoveLastItem%2A> Tlačítko|Přejde na poslední položku v podkladovém zdroji dat.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveNextItem%2A> Tlačítko|Přejde na další položku v podkladovém zdroji dat.|  
|<xref:System.Windows.Forms.BindingNavigator.MovePreviousItem%2A> Tlačítko|Přesune k předešlé položce v podkladovém zdroji dat|  
|<xref:System.Windows.Forms.BindingNavigator.PositionItem%2A> textové pole|Vrátí aktuální pozici v podkladovém zdroji dat.|  
|<xref:System.Windows.Forms.BindingNavigator.CountItem%2A> textové pole|Vrátí celkový počet položek v podkladovém zdroji dat.|  
  
 Pro každý ovládací prvek v této kolekci neexistuje odpovídající člen <xref:System.Windows.Forms.BindingSource> součást, která programově poskytuje stejné funkce. Například <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> tlačítko odpovídá <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> metodu <xref:System.Windows.Forms.BindingSource> komponenty, <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> tlačítko odpovídá <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> metody a tak dále.  
  
 Pokud výchozí tlačítka nejsou vhodné pro vaši aplikaci, nebo pokud budete potřebovat další tlačítka pro podporu dalších typů funkce, můžete zadat vlastní <xref:System.Windows.Forms.ToolStrip> tlačítka. Viz také [jak: Přidat načíst, uložit, a tlačítka Storno pro Windows Forms BindingNavigator – ovládací prvek](load-save-and-cancel-bindingnavigator.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- [Ovládací prvek BindingNavigator](bindingnavigator-control-windows-forms.md)
