---
title: 'Postupy: Přidávání tlačítek do ovládacího prvku ToolBar pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
ms.openlocfilehash: 4d7a49633599aabc96153e4793e50c1a4d6d092d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666220"
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a>Postupy: Přidávání tlačítek do ovládacího prvku ToolBar pomocí Návrháře

> [!NOTE]
> Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.ToolBar> <xref:System.Windows.Forms.ToolBar> ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.ToolStrip>

Nedílnou součástí <xref:System.Windows.Forms.ToolBar> ovládacího prvku jsou tlačítka, která do něj přidáte. Pomocí těchto možností lze snadno získat přístup k příkazům nabídky nebo je lze umístit do jiné oblasti uživatelského rozhraní aplikace, aby bylo možné vystavit příkazy uživatelům, kteří nejsou k dispozici ve struktuře nabídky.

Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.ToolBar> ovládací prvek. Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.

### <a name="to-add-buttons-at-design-time"></a>Přidání tlačítek v době návrhu

1. <xref:System.Windows.Forms.ToolBar> Vyberte ovládací prvek.

2. V okně **vlastnosti** klikněte <xref:System.Windows.Forms.ToolBar.Buttons%2A> na vlastnost, kterou chcete vybrat, a ![kliknutím na tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) otevřete ovládací prvky **ToolBarButton Editor kolekce**.

3. Pomocí tlačítek **Přidat** a **Odebrat** můžete přidat nebo odebrat <xref:System.Windows.Forms.ToolBar> tlačítka z ovládacího prvku.

4. Nakonfigurujte vlastnosti jednotlivých tlačítek v okně **vlastnosti** , které se zobrazí v podokně na pravé straně editoru. V následující tabulce jsou uvedeny některé důležité vlastnosti, které je třeba vzít v úvahu.

    |Vlastnost|Popis|
    |--------------|-----------------|
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|Nastaví nabídku, která se má zobrazit v rozevíracím seznamu na panelu nástrojů. <xref:System.Windows.Forms.ToolBarButton.Style%2A> Vlastnost tlačítka panelu nástrojů musí být nastavena na <xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>hodnotu. Tato vlastnost přebírá instanci <xref:System.Windows.Forms.ContextMenu> třídy jako referenci.|
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|Nastaví, zda je tlačítko panelu nástrojů přepínacího stylu částečně vloženo. <xref:System.Windows.Forms.ToolBarButton.Style%2A> Vlastnost tlačítka panelu nástrojů musí být nastavena na <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>hodnotu.|
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|Nastaví, zda je tlačítko panelu nástrojů přepínacího stylu v současné době v nabízeném stavu. <xref:System.Windows.Forms.ToolBarButton.Style%2A> Vlastnost tlačítka panelu nástrojů musí být nastavena na <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton> nebo <xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>.|
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|Nastaví styl tlačítka panelu nástrojů. Musí se jednat o jednu z hodnot ve <xref:System.Windows.Forms.ToolBarButtonStyle> výčtu.|
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|Textový řetězec zobrazený tlačítkem|
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|Text zobrazený jako popis tlačítka|

5. Kliknutím na tlačítko **OK** zavřete dialogové okno a vytvořte panely, které jste určili.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolBar>
- [Postupy: Definování ikony pro tlačítko panelu nástrojů](how-to-define-an-icon-for-a-toolbar-button.md)
- [Postupy: Aktivace událostí nabídky pro tlačítka panelu nástrojů](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [Přehled ovládacího prvku ToolBar](toolbar-control-overview-windows-forms.md)
- [Ovládací prvek ToolBar](toolbar-control-windows-forms.md)
