---
title: 'Postupy: Vytváření rozhraní ve stylu Průzkumníka Windows ve formuláři Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: db2c5431dfb0156c1508a18ef13d2af80eb4981b
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039537"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a>Postupy: Vytváření rozhraní ve stylu Průzkumníka Windows ve formuláři Windows Forms
Průzkumník Windows je běžná volba uživatelského rozhraní pro aplikace z důvodu své připravenosti.

 Průzkumník Windows je v podstatě <xref:System.Windows.Forms.TreeView> ovládací prvek <xref:System.Windows.Forms.ListView> a ovládací prvek na samostatných panelech. Panely mají změnu velikosti příčkou. Toto uspořádání ovládacích prvků je velmi efektivní pro zobrazení a informace o procházení.

 Následující kroky ukazují, jak uspořádat ovládací prvky ve formuláři podobném prohlížeči Windows Explorer. Neukazují, jak přidat funkce pro procházení souborů v aplikaci Průzkumník Windows.

## <a name="to-create-a-windows-explorer-style-windows-form"></a>Vytvoření formuláře Windows ve stylu Průzkumníka Windows

1. Vytvoření nového projektu aplikace pro Windows (**soubor** > **nového** > **projektu** > **Visual C#**  nebo**klasický Desktop** **Visual Basic** >  >  **Model Windows Forms aplikace**).

2. Ze **sady nástrojů**:

    1. <xref:System.Windows.Forms.SplitContainer> Přetáhněte ovládací prvek do formuláře.

    2. Přetáhněte ovládací prvek do **SplitterPanel1** (panel <xref:System.Windows.Forms.SplitContainer> ovládacího prvku označený ovládacího Panel1 (). <xref:System.Windows.Forms.TreeView>

    3. Přetáhněte ovládací prvek do **SplitterPanel2** (panel <xref:System.Windows.Forms.SplitContainer> ovládacího prvku označený Panel2). <xref:System.Windows.Forms.ListView>

3. Vyberte všechny tři ovládací prvky tak, že stisknete klávesu CTRL a pak je kliknete zase. Když vyberete <xref:System.Windows.Forms.SplitContainer> ovládací prvek, klikněte na rozdělovač, nikoli na panely.

    > [!NOTE]
    >  V nabídce **Úpravy** nepoužívejte příkaz **Select All** . Pokud tak učiníte, vlastnost potřebná v dalším kroku se nezobrazí v okně **vlastnosti** .

4. V okně **vlastnosti** nastavte <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost na <xref:System.Windows.Forms.DockStyle.Fill>hodnotu.

5. Stisknutím klávesy F5 spusťte aplikaci.

     Ve formuláři se zobrazí uživatelské rozhraní se dvěma částmi, podobně jako v Průzkumníkovi Windows.

    > [!NOTE]
    >  Při přetahování rozdělovače se panely změní samy na sebe.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.SplitContainer>
- [Postupy: Vytvoření uživatelského rozhraní s více podokny pomocí model Windows Forms](how-to-create-a-multipane-user-interface-with-windows-forms.md)
- [Postupy: Definování chování změny velikosti a umístění v rozděleném okně](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)
- [Postupy: Vodorovné rozdělení okna](how-to-split-a-window-horizontally.md)
- [Ovládací prvek SplitContainer](splitcontainer-control-windows-forms.md)
