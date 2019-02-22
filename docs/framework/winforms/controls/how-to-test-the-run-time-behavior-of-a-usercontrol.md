---
title: 'Postupy: Testování běhového chování UserControl'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
ms.openlocfilehash: 06f2320648bd8fee3465ea1672be886293667879
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/22/2019
ms.locfileid: "56664416"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a>Postupy: Testování běhového chování UserControl
Při vývoji <xref:System.Windows.Forms.UserControl>, je potřeba testovat jeho chování za běhu. Můžete vytvořit projekt samostatné aplikace pro systém Windows a umístit ovládací prvek na formuláři testu, ale tento postup je praktické. Jednodušší a rychlejší způsob je použít **UserControl – kontejner testů** poskytovaný sadou Visual Studio. Tento kontejner testu spustí přímo z vašeho projektu knihovny ovládacích prvků Windows.  
  
> [!IMPORTANT]
>  Pro kontejner testu se načíst vaše <xref:System.Windows.Forms.UserControl>, ovládací prvek musí mít aspoň jeden veřejný konstruktor.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
> [!NOTE]
>  Ovládací prvek Visual C++ nelze provést test pomocí **UserControl – kontejner testů**.  
  
### <a name="to-test-the-run-time-behavior-of-a-usercontrol"></a>K otestování běhového chování UserControl  
  
1.  Vytvoření projektu knihovny ovládacích prvků Windows volá **TestContainerExample**. Podrobnosti najdete v tématu [šablonu ovládacího prvku knihovny Windows](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).  
  
2.  V **Návrháře formulářů Windows**, přetáhněte <xref:System.Windows.Forms.Label> ovládacího prvku **nástrojů** na návrhové ploše ovládacího prvku.  
  
3.  Stisknutím klávesy F5 projekt sestavit a spustit **UserControl – kontejner testů**. Kontejner testu se zobrazí s vaší <xref:System.Windows.Forms.UserControl> v **ve verzi Preview** podokně.  
  
4.  Vyberte <xref:System.Windows.Forms.Control.BackColor%2A> zobrazená v vlastnost <xref:System.Windows.Forms.PropertyGrid> ovládací prvek vpravo od **ve verzi Preview** podokně. Změňte tuto hodnotu na `ControlDark`. Podívejte se, že ovládací prvek změní tmavší barvu. Zkuste změnit jiné hodnoty vlastností a sledujte vliv na váš ovládací prvek.  
  
5.  Klikněte na tlačítko **Ukotvit výplň uživatelský ovládací prvek** zaškrtnutím políčka níže **ve verzi Preview** podokně. Podívejte se, že ovládací prvek svou velikost tak, aby vyplnil podokna. Změna velikosti kontejneru testů a podívejte se, že ovládací prvek svou velikost podokna.  
  
6.  Zavřete kontejner testu.  
  
7.  Přidat jiný uživatelský ovládací prvek **TestContainerExample** projektu. Podrobnosti najdete v tématu [jak: Přidání existující položky do projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100)).  
  
8.  V **Návrháře formulářů Windows**, přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** na návrhové ploše ovládacího prvku.  
  
9. Stisknutím klávesy F5 projekt sestavit a spustit kontejner testu.  
  
10. Klikněte na tlačítko **vyberte uživatelský ovládací prvek** <xref:System.Windows.Forms.ComboBox> přepínat mezi dvěma uživatelské ovládací prvky.  
  
## <a name="testing-user-controls-from-another-project"></a>Testování uživatelských ovládacích prvků z jiného projektu  
 Uživatelské ovládací prvky z jiných projektů můžete otestovat v kontejneru testů aktuálního projektu.  
  
#### <a name="to-test-user-controls-from-another-project"></a>K testování uživatelských ovládacích prvků z jiného projektu  
  
1.  Vytvoření projektu knihovny ovládacích prvků Windows volá **TestContainerExample2**. Podrobnosti najdete v tématu [šablonu ovládacího prvku knihovny Windows](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).  
  
2.  V **Návrháře formulářů Windows**, přetáhněte <xref:System.Windows.Forms.RadioButton> ovládacího prvku **nástrojů** na návrhové ploše ovládacího prvku.  
  
3.  Stisknutím klávesy F5 projekt sestavit a spustit kontejner testu. Kontejner testu se zobrazí s vaší <xref:System.Windows.Forms.UserControl> v **ve verzi Preview** podokně.  
  
4.  Klikněte na tlačítko **zatížení** tlačítko.  
  
5.  V **otevřít** dialogové okno, přejděte na **TestContainerExample**.dll, který jste vytvořili v předchozím postupu. Vyberte **TestContainerExample**.dll a kliknutím **otevřít** tlačítko načíst uživatelské ovládací prvky  
  
6.  Použití **vyberte uživatelský ovládací prvek** <xref:System.Windows.Forms.ComboBox> přepínat mezi dvěma uživatelské ovládací prvky z **TestContainerExample** projektu.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.UserControl>
- [Postupy: Vytváření složených ovládacích prvků](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)
- [Návod: Vytvoření složeného ovládacího prvku s jazykem Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [Návrhář uživatelského ovládacího prvku](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))
