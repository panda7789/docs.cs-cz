---
title: ToolBar – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ToolBar
helpviewer_keywords:
- toolbars [Windows Forms], about toolbars
- ToolBar control [Windows Forms], about ToolBar controls
ms.assetid: d426b203-0216-4dbe-b834-1641e50a9c29
ms.openlocfilehash: 42c3d9c681da9ca87125a274fa12af623269bd70
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745245"
---
# <a name="toolbar-control-overview-windows-forms"></a>ToolBar – přehled ovládacího prvku (Windows Forms)
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.ToolBar> řízení; však <xref:System.Windows.Forms.ToolBar> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.  
  
 Windows Forms <xref:System.Windows.Forms.ToolBar> ovládací prvek se používá ve formulářích jako ovládací panel, který zobrazuje řádek z rozevírací nabídky a tlačítek s rastrovými obrázky, které aktivovat příkazy. Kliknutím na tlačítko panelu nástrojů proto může být ekvivalent k příkazu nabídky. Tlačítka lze nastavit na a chovají se jako tlačítek, rozevíracích nabídek nebo oddělovače. Obvykle obsahuje panel nástrojů tlačítka a nabídky, které odpovídají položky nabídky struktury aplikace poskytuje rychlý přístup k aplikačním nejčastěji používané funkce a příkazy.  
  
## <a name="working-with-the-toolbar-control"></a>Práce s ovládacím prvkem panel nástrojů  
 A <xref:System.Windows.Forms.ToolBar> ovládací prvek je obvykle "ukotven" podél horního okraje nezašle nadřazenému oknu, ale taky ho lze ukotvit na žádné straně okna. Panel nástrojů můžete zobrazit popisy tlačítek, když uživatel ukazuje ukazatel myši na tlačítko panelu nástrojů. Popisek je malého vyskakovacího okna, která stručně popisuje účel nabídky nebo tlačítka. Zobrazit popisy tlačítek, <xref:System.Windows.Forms.ToolBar.ShowToolTips%2A> musí být vlastnost nastavena na `true`.  
  
> [!NOTE]
>  Některé aplikace funkcí ovládacích prvků velmi podobný panelu nástrojů, které se budou moct "float" nad oknem aplikace a změnit umístění. Ovládacím prvkem Windows Forms panel nástrojů není schopen provést tyto akce.  
  
 Když <xref:System.Windows.Forms.ToolBar.Appearance%2A> je nastavena na <xref:System.Windows.Forms.ToolBarAppearance>, tlačítka panelu nástrojů zobrazí trojrozměrného a nevyskytla se. Můžete nastavit <xref:System.Windows.Forms.ToolBar.Appearance%2A> vlastnost panelu nástrojů <xref:System.Windows.Forms.ToolBarAppearance> poskytnout jeho tlačítka panelu nástrojů a plochý vzhled. Při umístění ukazatele myši nad plochý tlačítkem, vzhled na tlačítko se změní na trojrozměrné. Tlačítka panelu nástrojů je možné rozdělit do logických skupin pomocí oddělovače. Oddělovač je pomocí tlačítka panelu nástrojů <xref:System.Windows.Forms.ToolBarButton.Style%2A> nastavenou na <xref:System.Windows.Forms.ToolBarButtonStyle>. Zobrazí se jako prázdné znaky na panelu nástrojů. Plochý vzhled po panelu nástrojů tlačítko oddělovače zobrazí jako řádky, nikoli mezery mezi tlačítka.  
  
 <xref:System.Windows.Forms.ToolBar> Ovládací prvek umožňuje vytvářet panely nástrojů tak, že přidáte <xref:System.Windows.Forms.Button> objektů do <xref:System.Windows.Forms.ToolBar.Buttons%2A> kolekce. Editor kolekce slouží k přidání tlačítek <xref:System.Windows.Forms.ToolBar> ovládacího prvku; každý <xref:System.Windows.Forms.Button> objekt musí mít text nebo obrázek přiřazen, i když můžete přiřadit oba. Zadaná image podle přidružené [ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) komponenty. V době běhu, můžete přidat nebo odebrat tlačítka z <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection> pomocí <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Add%2A> a <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Remove%2A> metody. Programování tlačítek <xref:System.Windows.Forms.ToolBar>, přidejte kód, který <xref:System.Windows.Forms.ToolBar.ButtonClick> události <xref:System.Windows.Forms.ToolBar>, pomocí <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> vlastnost <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> třídu k určení, které tlačítko došlo ke kliknutí na.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.ToolBar>
- [Ovládací prvek ToolBar](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)
- [Postupy: Přidání tlačítek do ovládacího prvku ToolBar](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)
- [Postupy: Definování ikony pro tlačítko ToolBar](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)
- [Postupy: Aktivační události nabídky pro tlačítka panelu nástrojů](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)
