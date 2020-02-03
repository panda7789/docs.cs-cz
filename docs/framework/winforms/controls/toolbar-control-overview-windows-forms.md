---
title: Přehled ovládacího prvku ToolBar
ms.date: 03/30/2017
f1_keywords:
- ToolBar
helpviewer_keywords:
- toolbars [Windows Forms], about toolbars
- ToolBar control [Windows Forms], about ToolBar controls
ms.assetid: d426b203-0216-4dbe-b834-1641e50a9c29
ms.openlocfilehash: f364e052258703331496f8103b48953a90aa3a9b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735481"
---
# <a name="toolbar-control-overview-windows-forms"></a>ToolBar – přehled ovládacího prvku (Windows Forms)
> [!NOTE]
> Ovládací prvek <xref:System.Windows.Forms.ToolStrip> nahrazuje a přidává funkce do ovládacího prvku <xref:System.Windows.Forms.ToolBar>; Nicméně ovládací prvek <xref:System.Windows.Forms.ToolBar> se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.  
  
 Ovládací prvek model Windows Forms <xref:System.Windows.Forms.ToolBar> se ve formulářích používá jako ovládací panel, který zobrazuje řádek rozevíracích nabídek a tlačítek s rastrovými obrázky, které aktivují příkazy. Proto kliknutí na tlačítko panelu nástrojů může být ekvivalentem pro výběr příkazu nabídky. Tlačítka se dají nakonfigurovat tak, aby se zobrazovala jako pushbuttons, rozevírací nabídky nebo oddělovače. Panel nástrojů obvykle obsahuje tlačítka a nabídky, které odpovídají položkám v rámci struktury nabídky aplikace, a poskytuje tak rychlý přístup k nejčastěji používaným funkcím a příkazům aplikace.  
  
## <a name="working-with-the-toolbar-control"></a>Práce s ovládacím prvkem panel nástrojů  
 <xref:System.Windows.Forms.ToolBar> ovládací prvek je obvykle "ukotven" podél horní části svého nadřazeného okna, ale může být také ukotven na libovolné straně okna. Panel nástrojů může zobrazit popisy tlačítek, když uživatel přejde ukazatelem myši na tlačítko na panelu nástrojů. Popis tlačítka je malé automaticky otevírané okno, které stručně popisuje účel tlačítka nebo nabídky. Chcete-li zobrazit popisy tlačítek, vlastnost <xref:System.Windows.Forms.ToolBar.ShowToolTips%2A> musí být nastavena na hodnotu `true`.  
  
> [!NOTE]
> Některé aplikace řídí funkci velmi podobné panelu nástrojů, který má možnost "float" nad oknem aplikace a přemístění. Ovládací prvek panelu nástrojů model Windows Forms nemůže provádět tyto akce.  
  
 Pokud je vlastnost <xref:System.Windows.Forms.ToolBar.Appearance%2A> nastavena na hodnotu <xref:System.Windows.Forms.ToolBarAppearance>, tlačítka panelu nástrojů se zobrazí jako vystouplá a trojrozměrná. Vlastnost <xref:System.Windows.Forms.ToolBar.Appearance%2A> panelu nástrojů můžete nastavit tak, aby <xref:System.Windows.Forms.ToolBarAppearance>, aby měl panel nástrojů a jeho tlačítka plochý vzhled. Když se ukazatel myši pohybuje nad plochým tlačítkem, vzhled tlačítka se změní na trojrozměrné. Tlačítka panelu nástrojů lze rozdělit do logických skupin pomocí oddělovačů. Oddělovač je tlačítko panelu nástrojů s vlastností <xref:System.Windows.Forms.ToolBarButton.Style%2A> nastavenou na hodnotu <xref:System.Windows.Forms.ToolBarButtonStyle>. Zobrazuje se jako prázdné místo na panelu nástrojů. Pokud má panel nástrojů plochý vzhled, oddělovače tlačítek se zobrazí jako řádky, nikoli mezery mezi tlačítky.  
  
 Ovládací prvek <xref:System.Windows.Forms.ToolBar> umožňuje vytvořit panely nástrojů přidáním objektů <xref:System.Windows.Forms.Button> do kolekce <xref:System.Windows.Forms.ToolBar.Buttons%2A>. Editor kolekce lze použít k přidání tlačítek do ovládacího prvku <xref:System.Windows.Forms.ToolBar>; Každý objekt <xref:System.Windows.Forms.Button> by měl mít přiřazený text nebo obrázek, i když můžete oba přiřadit obojí. Obrázek je dodán přidruženou komponentou [ImageList](imagelist-component-windows-forms.md) . V době běhu můžete přidat nebo odebrat tlačítka z <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection> pomocí metod <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Add%2A> a <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Remove%2A>. Chcete-li programovat tlačítka <xref:System.Windows.Forms.ToolBar>, přidejte kód do události <xref:System.Windows.Forms.ToolBar.ButtonClick> <xref:System.Windows.Forms.ToolBar>pomocí vlastnosti <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> třídy <xref:System.Windows.Forms.ToolBarButtonClickEventArgs>, abyste určili, na které tlačítko bylo kliknuto.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ToolBar>
- [Ovládací prvek ToolBar](toolbar-control-windows-forms.md)
- [Postupy: Přidání tlačítek do ovládacího prvku ToolBar](how-to-add-buttons-to-a-toolbar-control.md)
- [Postupy: Definování ikony pro tlačítko ToolBar](how-to-define-an-icon-for-a-toolbar-button.md)
- [Postupy: Spouštění událostí nabídky pro tlačítka panelu nástrojů](how-to-trigger-menu-events-for-toolbar-buttons.md)
