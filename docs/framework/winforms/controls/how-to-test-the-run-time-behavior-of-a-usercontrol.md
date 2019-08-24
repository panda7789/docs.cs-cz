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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1be79d52be3b5b84938d8548a8f101e965fa9dbb
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015768"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a>Postupy: Testování chování prvku UserControl v době běhu

Při vývoji <xref:System.Windows.Forms.UserControl>nástroje je nutné otestovat jeho chování za běhu. Můžete vytvořit samostatný projekt aplikace pro systém Windows a umístit ovládací prvek do formuláře testu, ale tato procedura je nepraktická. Rychlejší a snazší způsob použití **kontejneru testu UserControl** , který poskytuje Visual Studio. Tento kontejner testů začíná přímo z projektu knihovny ovládacích prvků systému Windows.

> [!IMPORTANT]
> Aby mohl kontejner testu načíst svůj <xref:System.Windows.Forms.UserControl>ovládací prvek, musí mít alespoň jeden veřejný konstruktor.

> [!NOTE]
> Vizuální C++ ovládací prvek nelze testovat pomocí **kontejneru testu UserControl**.

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a>Testování chování prvku UserControl v době běhu

1. V aplikaci Visual Studio vytvořte projekt knihovny ovládacích prvků systému Windows a pojmenujte jej **TestContainerExample**.

2. V **Návrhář formulářů**přetáhněte <xref:System.Windows.Forms.Label> ovládací prvek z **panelu nástrojů** na návrhovou plochu ovládacího prvku.

3. Stisknutím klávesy **F5** Sestavte projekt a spusťte **kontejner testu UserControl**. Kontejner testu se zobrazí <xref:System.Windows.Forms.UserControl> v podokně **náhledu** .

4. Vyberte vlastnost zobrazenou <xref:System.Windows.Forms.PropertyGrid> v ovládacím prvku napravo od podokna **náhledu.** <xref:System.Windows.Forms.Control.BackColor%2A> Změňte její hodnotu na **ControlDark**. Pozor, aby se ovládací prvek změnil na tmavší barvu. Zkuste změnit další hodnoty vlastností a sledujte efekt ovládacího prvku.

5. V podokně **náhledu** klikněte na zaškrtávací políčko **ukotvit výplň uživatelského ovládacího prvku** . Všimněte si, že se změní velikost ovládacího prvku, aby bylo možné vyplnit podokno. Změňte velikost kontejneru testu a sledujte, že se změní velikost ovládacího prvku v podokně.

6. Zavřete kontejner testu.

7. Přidejte do projektu **TestContainerExample** další uživatelský ovládací prvek.

8. V **Návrhář formulářů**přetáhněte <xref:System.Windows.Forms.Button> ovládací prvek z **panelu nástrojů** na návrhovou plochu ovládacího prvku.

9. Stisknutím klávesy **F5** Sestavte projekt a spusťte kontejner testu.

10. Klikněte na **ovládací prvek** <xref:System.Windows.Forms.ComboBox> pro výběr uživatele, který chcete přepínat mezi dvěma uživatelskými ovládacími prvky.

## <a name="test-user-controls-from-another-project"></a>Testování uživatelských ovládacích prvků z jiného projektu

Uživatelské ovládací prvky můžete testovat z jiných projektů v aktuálním kontejneru testů projektu.

1. V aplikaci Visual Studio vytvořte projekt knihovny ovládacích prvků systému Windows a pojmenujte jej **TestContainerExample2**.

2. V **Návrhář formulářů**přetáhněte <xref:System.Windows.Forms.RadioButton> ovládací prvek z **panelu nástrojů** na návrhovou plochu ovládacího prvku.

3. Stisknutím klávesy **F5** Sestavte projekt a spusťte kontejner testu. Kontejner testu se zobrazí <xref:System.Windows.Forms.UserControl> v podokně **náhledu** .

4. Klikněte na tlačítko **načíst** .

5. V dialogovém okně **otevřít** přejděte na **TestContainerExample**. dll, které jste vytvořili v předchozím postupu. Vyberte **TestContainerExample**. dll a kliknutím na tlačítko **otevřít** načtěte uživatelské ovládací prvky.

6. Pomocí **ovládacího prvku vybrat uživatelský ovládací prvek** <xref:System.Windows.Forms.ComboBox> můžete přepínat mezi dvěma uživatelskými ovládacími prvky z projektu **TestContainerExample** .

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.UserControl>
- [Postupy: Vytváření složených ovládacích prvků](how-to-author-composite-controls.md)
- [Návod: Vytváření složeného ovládacího prvku](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [Návrhář uživatelského ovládacího prvku](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))
