---
title: 'Postupy: Otestování běhového chování UserControl'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
ms.openlocfilehash: 48531ab1ef3b30b6516e3f2e7b5858a8884cbfe8
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211712"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a>Postupy: Testování běhového chování UserControl

Při vývoji <xref:System.Windows.Forms.UserControl>, je potřeba testovat jeho chování za běhu. Můžete vytvořit projekt samostatné aplikace pro systém Windows a umístit ovládací prvek na formuláři testu, ale tento postup je praktické. Jednodušší a rychlejší způsob je použít **UserControl – kontejner testů** poskytovaný sadou Visual Studio. Tento kontejner testu spustí přímo z vašeho projektu knihovny ovládacích prvků Windows.

> [!IMPORTANT]
> Pro kontejner testu se načíst vaše <xref:System.Windows.Forms.UserControl>, ovládací prvek musí mít aspoň jeden veřejný konstruktor.

> [!NOTE]
> Ovládací prvek Visual C++ nelze provést test pomocí **UserControl – kontejner testů**.

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a>Testování běhového chování UserControl

1. V sadě Visual Studio vytvořte projekt knihovny ovládacích prvků Windows volá **TestContainerExample**. Podrobnosti najdete v tématu [šablonu ovládacího prvku knihovny Windows](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).

2. V **Návrháře formulářů Windows**, přetáhněte <xref:System.Windows.Forms.Label> ovládacího prvku **nástrojů** na návrhové ploše ovládacího prvku.

3. Stisknutím klávesy **F5** chcete projekt sestavit a spustit **UserControl – kontejner testů**. Kontejner testu se zobrazí s vaší <xref:System.Windows.Forms.UserControl> v **ve verzi Preview** podokně.

4. Vyberte <xref:System.Windows.Forms.Control.BackColor%2A> zobrazená v vlastnost <xref:System.Windows.Forms.PropertyGrid> ovládací prvek vpravo od **ve verzi Preview** podokně. Změňte tuto hodnotu na `ControlDark`. Podívejte se, že ovládací prvek změní tmavší barvu. Zkuste změnit jiné hodnoty vlastností a sledujte vliv na váš ovládací prvek.

5. Klikněte na tlačítko **Ukotvit výplň uživatelský ovládací prvek** zaškrtnutím políčka níže **ve verzi Preview** podokně. Podívejte se, že ovládací prvek svou velikost tak, aby vyplnil podokna. Změna velikosti kontejneru testů a podívejte se, že ovládací prvek svou velikost podokna.

6. Zavřete kontejner testu.

7. Přidat jiný uživatelský ovládací prvek **TestContainerExample** projektu. Podrobnosti najdete v tématu [jak: Přidání existující položky do projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100)).

8. V **Návrháře formulářů Windows**, přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** na návrhové ploše ovládacího prvku.

9. Stisknutím klávesy F5 projekt sestavit a spustit kontejner testu.

10. Klikněte na tlačítko **vyberte uživatelský ovládací prvek** <xref:System.Windows.Forms.ComboBox> přepínat mezi dvěma uživatelské ovládací prvky.

## <a name="test-user-controls-from-another-project"></a>Test uživatelské ovládací prvky z jiného projektu

Uživatelské ovládací prvky z jiných projektů můžete otestovat v kontejneru testů aktuálního projektu.

1. Vytvoření projektu knihovny ovládacích prvků Windows volá **TestContainerExample2**. Podrobnosti najdete v tématu [šablonu ovládacího prvku knihovny Windows](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).

2. V **Návrháře formulářů Windows**, přetáhněte <xref:System.Windows.Forms.RadioButton> ovládacího prvku **nástrojů** na návrhové ploše ovládacího prvku.

3. Stisknutím klávesy F5 projekt sestavit a spustit kontejner testu. Kontejner testu se zobrazí s vaší <xref:System.Windows.Forms.UserControl> v **ve verzi Preview** podokně.

4. Klikněte na tlačítko **zatížení** tlačítko.

5. V **otevřít** dialogové okno, přejděte na **TestContainerExample**.dll, který jste vytvořili v předchozím postupu. Vyberte **TestContainerExample**.dll a kliknutím **otevřít** tlačítko načíst uživatelské ovládací prvky

6. Použití **vyberte uživatelský ovládací prvek** <xref:System.Windows.Forms.ComboBox> přepínat mezi dvěma uživatelské ovládací prvky z **TestContainerExample** projektu.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.UserControl>
- [Postupy: Vytváření složených ovládacích prvků](how-to-author-composite-controls.md)
- [Návod: Vytvoření složeného ovládacího prvku s jazykem Visual Basic](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [Návrhář uživatelského ovládacího prvku](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))
