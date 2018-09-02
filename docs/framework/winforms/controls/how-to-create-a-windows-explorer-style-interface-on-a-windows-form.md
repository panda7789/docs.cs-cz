---
title: 'Postupy: Vytváření rozhraní ve stylu Průzkumníku Windows ve formuláři Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: 249210d2bcb7a9ef2c5bf1aed00bcfe138193aab
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43456704"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a>Postupy: Vytváření rozhraní ve stylu Průzkumníku Windows ve formuláři Windows
Windows Explorer je běžné volbou uživatelského rozhraní pro aplikace z důvodu jeho známý připravený.  
  
 Průzkumník Windows je v podstatě <xref:System.Windows.Forms.TreeView> ovládacího prvku a <xref:System.Windows.Forms.ListView> ovládací prvek na samostatné panelů. Panely vyrábí celá rozdělovač umožňující změnu velikosti. Uspořádání ovládacích prvků je velice efektivní pro zobrazení informací o procházení.  
  
 Následující kroky ukazují, jak k uspořádání ovládacích prvků ve Windows Explorer podobě. Nezobrazovat přidání funkce procházení souborů v aplikaci Windows Explorer.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-a-windows-explorer-style-windows-form"></a>Vytvoření formuláře Windows stylem podobným Průzkumníku Windows  
  
1.  Vytvoření nového projektu aplikace Windows (**souboru** > **nový** > **projektu** > **Visual C#** nebo **jazyka Visual Basic** > **klasický desktopový** > **aplikaci Windows Forms**).  
  
2.  Z **nástrojů**:  
  
    1.  Přetáhněte <xref:System.Windows.Forms.SplitContainer> ovládacího prvku na formulář.  
  
    2.  Přetáhněte <xref:System.Windows.Forms.TreeView> ovládací prvek do **SplitterPanel1** (panelu <xref:System.Windows.Forms.SplitContainer> označený ovládací prvek **Panel1**).  
  
    3.  Přetáhněte <xref:System.Windows.Forms.ListView> ovládací prvek do **SplitterPanel2** (panelu <xref:System.Windows.Forms.SplitContainer> označený ovládací prvek **ovládací prvek Panel2**).  
  
3.  Vyberte klávesy CTRL a kliknutím zase na všechny tři ovládací prvky. Když vyberete <xref:System.Windows.Forms.SplitContainer> řídit, klikněte na tlačítko rozdělovač, nikoli panelů.  
  
    > [!NOTE]
    >  Nepoužívejte **Vybrat vše** příkaz **upravit** nabídky. Pokud tak učiníte, vlastnost, je potřeba v dalším kroku nebude zobrazovat **vlastnosti** okna.  
  
4.  V **vlastnosti** okno, nastaveno <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.  
  
5.  Stisknutím klávesy F5 spusťte aplikaci.  
  
     Formulář zobrazí dvě části uživatelského rozhraní, podobně jako u v Průzkumníku Windows.  
  
    > [!NOTE]
    >  Při přetažení příčky změnit velikost panelů sami.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.SplitContainer>  
 [Postupy: Vytváření uživatelského rozhraní s více podokny pomocí Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 [Postupy: Definování chování změny velikosti a polohování v rozděleném okně](../../../../docs/framework/winforms/controls/how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 [Postupy: Vodorovné rozdělení okna](../../../../docs/framework/winforms/controls/how-to-split-a-window-horizontally.md)  
 [Ovládací prvek SplitContainer](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
