---
title: ToolBar – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ToolBar
helpviewer_keywords:
- toolbars [Windows Forms], about toolbars
- ToolBar control [Windows Forms], about ToolBar controls
ms.assetid: d426b203-0216-4dbe-b834-1641e50a9c29
ms.openlocfilehash: c7c19783963bb315a0356979797c6f4d4e3b9e08
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929596"
---
# <a name="toolbar-control-overview-windows-forms"></a>ToolBar – přehled ovládacího prvku (Windows Forms)
> [!NOTE]
> Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.ToolBar> <xref:System.Windows.Forms.ToolBar> ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.ToolStrip>  
  
 Model Windows Forms <xref:System.Windows.Forms.ToolBar> ovládací prvek se používá ve formulářích jako ovládací panel, který zobrazuje řádek rozevíracích nabídek a tlačítek s rastrovými obrázky, které aktivují příkazy. Proto kliknutí na tlačítko panelu nástrojů může být ekvivalentem pro výběr příkazu nabídky. Tlačítka se dají nakonfigurovat tak, aby se zobrazovala jako pushbuttons, rozevírací nabídky nebo oddělovače. Panel nástrojů obvykle obsahuje tlačítka a nabídky, které odpovídají položkám v rámci struktury nabídky aplikace, a poskytuje tak rychlý přístup k nejčastěji používaným funkcím a příkazům aplikace.  
  
## <a name="working-with-the-toolbar-control"></a>Práce s ovládacím prvkem panel nástrojů  
 <xref:System.Windows.Forms.ToolBar> Ovládací prvek je obvykle "ukotven" podél horního okraje jeho nadřazeného okna, ale lze jej ukotvit i na kteroukoli stranu okna. Panel nástrojů může zobrazit popisy tlačítek, když uživatel přejde ukazatelem myši na tlačítko na panelu nástrojů. Popis tlačítka je malé automaticky otevírané okno, které stručně popisuje účel tlačítka nebo nabídky. Chcete-li zobrazit popisy tlačítek <xref:System.Windows.Forms.ToolBar.ShowToolTips%2A> , musí být vlastnost nastavena `true`na hodnotu.  
  
> [!NOTE]
> Některé aplikace řídí funkci velmi podobné panelu nástrojů, který má možnost "float" nad oknem aplikace a přemístění. Ovládací prvek panelu nástrojů model Windows Forms nemůže provádět tyto akce.  
  
 <xref:System.Windows.Forms.ToolBarAppearance>Když je <xref:System.Windows.Forms.ToolBar.Appearance%2A> vlastnost nastavena na, tlačítka panelu nástrojů se zobrazí jako vystouplá a trojrozměrná. <xref:System.Windows.Forms.ToolBar.Appearance%2A> Vlastnost panelu nástrojů lze nastavit tak <xref:System.Windows.Forms.ToolBarAppearance> , aby měl panel nástrojů a jeho tlačítka plochý vzhled. Když se ukazatel myši pohybuje nad plochým tlačítkem, vzhled tlačítka se změní na trojrozměrné. Tlačítka panelu nástrojů lze rozdělit do logických skupin pomocí oddělovačů. Oddělovač je tlačítko panelu nástrojů s <xref:System.Windows.Forms.ToolBarButton.Style%2A> vlastností nastavenou na. <xref:System.Windows.Forms.ToolBarButtonStyle> Zobrazuje se jako prázdné místo na panelu nástrojů. Pokud má panel nástrojů plochý vzhled, oddělovače tlačítek se zobrazí jako řádky, nikoli mezery mezi tlačítky.  
  
 Ovládací prvek umožňuje vytvořit panely nástrojů přidáním <xref:System.Windows.Forms.Button> objektů do <xref:System.Windows.Forms.ToolBar.Buttons%2A> kolekce. <xref:System.Windows.Forms.ToolBar> Editor kolekce lze použít k přidání tlačítek k <xref:System.Windows.Forms.ToolBar> ovládacímu prvku. Každý <xref:System.Windows.Forms.Button> objekt by měl mít přiřazený text nebo obrázek, i když můžete oba přiřadit obojí. Obrázek je dodán přidruženou komponentou [ImageList](imagelist-component-windows-forms.md) . V době běhu můžete přidat nebo odebrat tlačítka z <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection> <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Add%2A> pomocí metody a <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Remove%2A> . Chcete-li programovat tlačítka <xref:System.Windows.Forms.ToolBar>rozhraní, přidejte kód <xref:System.Windows.Forms.ToolBar.ButtonClick> do událostí <xref:System.Windows.Forms.ToolBar>, pomocí <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> vlastnosti <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> třídy určete, na které tlačítko bylo kliknuto.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolBar>
- [Ovládací prvek ToolBar](toolbar-control-windows-forms.md)
- [Postupy: Přidání tlačítek do ovládacího prvku ToolBar](how-to-add-buttons-to-a-toolbar-control.md)
- [Postupy: Definování ikony pro tlačítko panelu nástrojů](how-to-define-an-icon-for-a-toolbar-button.md)
- [Postupy: Aktivace událostí nabídky pro tlačítka panelu nástrojů](how-to-trigger-menu-events-for-toolbar-buttons.md)
