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
ms.openlocfilehash: ae1e8273c39122e094817e28379e52c19c573a3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="bindingnavigator-control-overview-windows-forms"></a>BindingNavigator – přehled ovládacího prvku (Windows Forms)
Můžete použít <xref:System.Windows.Forms.BindingNavigator> řízení k vytvoření standardizovaným způsobem uživatelům vyhledávat a měnit data na formuláři Windows. Často používáte <xref:System.Windows.Forms.BindingNavigator> s <xref:System.Windows.Forms.BindingSource> komponenty, aby uživatelům pohyb záznamů dat ve formuláři a interakci s záznamy.  
  
## <a name="how-the-bindingnavigator-works"></a>Jak funguje BindingNavigator  
 <xref:System.Windows.Forms.BindingNavigator> Řízení se skládá z <xref:System.Windows.Forms.ToolStrip> s řadou <xref:System.Windows.Forms.ToolStripItem> objekty pro většinu běžné akce souvisejících s daty: přidání dat, odstranění dat a procházení data. Ve výchozím nastavení <xref:System.Windows.Forms.BindingNavigator> ovládací prvek obsahuje tyto standardní tlačítka. Zobrazuje snímek následující obrazovky <xref:System.Windows.Forms.BindingNavigator> prvek na formuláři.  
  
 ![BindingNavigator – ovládací prvek](../../../../docs/framework/winforms/controls/media/cpdatacontainerctrl.gif "cpDataContainerCtrl")  
  
 V následující tabulce jsou uvedeny ovládací prvky a popisuje jejich funkce.  
  
|Ovládací prvek|Funkce|  
|-------------|--------------|  
|<xref:System.Windows.Forms.BindingNavigator.AddNewItem%2A> Tlačítko|Vloží nový řádek do základního datového zdroje.|  
|<xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> Tlačítko|Odstraní z podkladové zdroje dat na aktuálním řádku.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> Tlačítko|Přesun na první položku v podkladovém zdroji dat|  
|<xref:System.Windows.Forms.BindingNavigator.MoveLastItem%2A> Tlačítko|Přejde na poslední položky v podkladovém zdroji dat.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveNextItem%2A> Tlačítko|Přesun na další položku v podkladovém zdroji dat|  
|<xref:System.Windows.Forms.BindingNavigator.MovePreviousItem%2A> Tlačítko|Přesune na předchozí položky v podkladovém zdroji dat.|  
|<xref:System.Windows.Forms.BindingNavigator.PositionItem%2A> Textové pole|Vrátí aktuální pozici v podkladovém zdroji dat.|  
|<xref:System.Windows.Forms.BindingNavigator.CountItem%2A> Textové pole|Vrátí celkový počet položek v podkladovém zdroji dat.|  
  
 Pro každý ovládací prvek v této kolekci, je členem příslušné skupiny <xref:System.Windows.Forms.BindingSource> komponenty, která prostřednictvím kódu programu poskytuje stejné funkce. Například <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> tlačítko odpovídá <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> metodu <xref:System.Windows.Forms.BindingSource> součásti, <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> tlačítko odpovídá <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> metoda a tak dále.  
  
 Pokud výchozí tlačítka nejsou vhodné pro vaše aplikace, nebo pokud budete potřebovat další tlačítka pro podporu dalších typů funkce, můžete zadat vlastní <xref:System.Windows.Forms.ToolStrip> tlačítka. Viz také [postupy: Přidání načíst, uložit, a tlačítka Storno do ovládacího prvku Windows Forms BindingNavigator](../../../../docs/framework/winforms/controls/load-save-and-cancel-bindingnavigator.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.BindingSource>  
 [Ovládací prvek BindingNavigator](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)
