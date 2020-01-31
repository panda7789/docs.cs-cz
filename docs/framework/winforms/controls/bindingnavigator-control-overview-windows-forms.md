---
title: Přehled ovládacího prvku BindingNavigator
ms.date: 03/30/2017
f1_keywords:
- DataNavigator
helpviewer_keywords:
- BindingNavigator control [Windows Forms], about BindingNavigator control
- records [Windows Forms], navigating on a form
- data [Windows Forms], navigating
- data navigation
ms.assetid: 4423eede-f8d1-4d02-822f-5bf8432680d0
ms.openlocfilehash: c2747a6801d4aa9cfde4227ffd5c29ca1de78d48
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744098"
---
# <a name="bindingnavigator-control-overview-windows-forms"></a>BindingNavigator – přehled ovládacího prvku (Windows Forms)
Pomocí ovládacího prvku <xref:System.Windows.Forms.BindingNavigator> můžete vytvořit standardizované prostředky pro uživatele, kteří budou vyhledávat a měnit data ve formuláři Windows. <xref:System.Windows.Forms.BindingNavigator> s komponentou <xref:System.Windows.Forms.BindingSource> často používáte k tomu, aby uživatelé mohli přesouvat záznamy dat na formuláři a interagovat se záznamy.  
  
## <a name="how-the-bindingnavigator-works"></a>Jak funguje BindingNavigator  

 <xref:System.Windows.Forms.BindingNavigator> ovládací prvek se skládá z <xref:System.Windows.Forms.ToolStrip> s řadou <xref:System.Windows.Forms.ToolStripItem> objektů pro většinu běžných akcí souvisejících s daty: přidávání dat, odstraňování dat a procházení dat. Ve výchozím nastavení obsahuje ovládací prvek <xref:System.Windows.Forms.BindingNavigator> Tato standardní tlačítka. Na následujícím snímku obrazovky je zobrazen ovládací prvek <xref:System.Windows.Forms.BindingNavigator> na formuláři:
  
 ![Snímek obrazovky znázorňující ovládací prvek BindingNavigator](./media/bindingnavigator-control-overview-windows-forms/bindingnavigator-control-form.gif)  
  
 Následující tabulka uvádí ovládací prvky a popisuje jejich funkce.  
  
|Control|Funkce|  
|-------------|--------------|  
|<xref:System.Windows.Forms.BindingNavigator.AddNewItem%2A> – tlačítko|Vloží nový řádek do podkladového zdroje dat.|  
|<xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> – tlačítko|Odstraní aktuální řádek z podkladového zdroje dat.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> – tlačítko|Přesune se na první položku v podkladovém zdroji dat.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveLastItem%2A> – tlačítko|Přesune se na poslední položku v podkladovém zdroji dat.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveNextItem%2A> – tlačítko|Přesune se na další položku v podkladovém zdroji dat.|  
|<xref:System.Windows.Forms.BindingNavigator.MovePreviousItem%2A> – tlačítko|Přesune se na předchozí položku v podkladovém zdroji dat.|  
|<xref:System.Windows.Forms.BindingNavigator.PositionItem%2A> textové pole|Vrátí aktuální pozici v podkladovém zdroji dat.|  
|<xref:System.Windows.Forms.BindingNavigator.CountItem%2A> textové pole|Vrátí celkový počet položek v podkladovém zdroji dat.|  
  
 Pro každý ovládací prvek v této kolekci je k dispozici odpovídající člen <xref:System.Windows.Forms.BindingSource> komponenty, který programově poskytuje stejné funkce. Například tlačítko <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> odpovídá metodě <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> <xref:System.Windows.Forms.BindingSource> komponenty, <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> tlačítko, které odpovídá metodě <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A>, a tak dále.  
  
 Pokud výchozí tlačítka nejsou vhodná pro vaši aplikaci nebo pokud požadujete další tlačítka pro podporu jiných typů funkcí, můžete vlastní <xref:System.Windows.Forms.ToolStrip> tlačítka. Viz také [Postupy: Přidání tlačítek Load, Save a Cancel do ovládacího prvku BindingNavigator model Windows Forms](load-save-and-cancel-bindingnavigator.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- [Ovládací prvek BindingNavigator](bindingnavigator-control-windows-forms.md)
