---
title: "Postupy: Otestování běhového chování UserControl"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2ce4f821a7b964b3ed2e03c795346b47bb88d618
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a>Postupy: Otestování běhového chování UserControl
Když budete vyvíjet <xref:System.Windows.Forms.UserControl>, je potřeba provést testování její chování. Můžete vytvořit projekt samostatné aplikace systému Windows a umístěte ovládací prvek na formuláři testu, ale tento postup je nepohodlná. Je rychlejší a jednodušší způsob použití **UserControl – kontejner testů** poskytované sadě Visual Studio. Tento kontejner testů spustí přímo z projektu knihovny ovládacího prvku systému Windows.  
  
> [!IMPORTANT]
>  Pro kontejner testů načíst vaše <xref:System.Windows.Forms.UserControl>, ovládacího prvku musí mít alespoň jeden veřejný konstruktor.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
> [!NOTE]
>  Visual C++ ovládacího prvku nelze testovat pomocí **UserControl – kontejner testů**.  
  
### <a name="to-test-the-run-time-behavior-of-a-usercontrol"></a>K otestování běhového chování UserControl  
  
1.  Vytvoření projektu knihovny ovládacího prvku Windows názvem **TestContainerExample**. Podrobnosti najdete v tématu [šablona knihovny ovládacího prvku Windows](http://msdn.microsoft.com/en-us/722f4e2d-1310-4ed5-8f33-593337ab66b4).  
  
2.  V **Návrhář formulářů Windows**, přetáhněte <xref:System.Windows.Forms.Label> řídit z **sada nástrojů** na návrhovou plochu ovládacího prvku.  
  
3.  Stiskněte klávesu F5, aby se projekt sestavil a spustit **UserControl – kontejner testů**. Kontejner testů se zobrazí s vaší <xref:System.Windows.Forms.UserControl> v **Preview** podokně.  
  
4.  Vyberte <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost zobrazena v <xref:System.Windows.Forms.PropertyGrid> řízení napravo **Preview** podokně. Změnit jeho hodnotu na `ControlDark`. Zkontrolujte, že ovládací prvek změny tmavší barva. Zkuste změnit dalších hodnot vlastností a sledovat účinek na vlastní ovládací prvek.  
  
5.  Klikněte **ukotvení vyplnění uživatelský ovládací prvek** zaškrtnutí políčka dole **Preview** podokně. Sledujte, změně velikosti ovládacího prvku k vyplnění podokně. Resize – kontejner testů a sledovat změně velikosti ovládacího prvku s podokně.  
  
6.  Zavřete testovací kontejneru.  
  
7.  Přidat další uživatelský ovládací prvek na **TestContainerExample** projektu. Podrobnosti najdete v tématu [NIB: postupy: Přidání existujících položek do projektu](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).  
  
8.  V **Návrhář formulářů Windows**, přetáhněte <xref:System.Windows.Forms.Button> řídit z **sada nástrojů** na návrhovou plochu ovládacího prvku.  
  
9. Stisknutím klávesy F5 sestavte projekt a spusťte kontejner testů.  
  
10. Klikněte **vyberte uživatelský ovládací prvek** <xref:System.Windows.Forms.ComboBox> přepínat mezi dvěma uživatelské ovládací prvky.  
  
## <a name="testing-user-controls-from-another-project"></a>Testování uživatelských ovládacích prvků z jiného projektu  
 Uživatelské ovládací prvky z jiných projektů můžete otestovat v aktuálním projektu – kontejner testů.  
  
#### <a name="to-test-user-controls-from-another-project"></a>K testování uživatelských ovládacích prvků z jiného projektu  
  
1.  Vytvoření projektu knihovny ovládacího prvku Windows názvem **TestContainerExample2**. Podrobnosti najdete v tématu [šablona knihovny ovládacího prvku Windows](http://msdn.microsoft.com/en-us/722f4e2d-1310-4ed5-8f33-593337ab66b4).  
  
2.  V **Návrhář formulářů Windows**, přetáhněte <xref:System.Windows.Forms.RadioButton> řídit z **sada nástrojů** na návrhovou plochu ovládacího prvku.  
  
3.  Stisknutím klávesy F5 sestavte projekt a spusťte kontejner testů. Kontejner testů se zobrazí s vaší <xref:System.Windows.Forms.UserControl> v **Preview** podokně.  
  
4.  Klikněte **zatížení** tlačítko.  
  
5.  V **otevřete** dialogové okno pole, přejděte na **TestContainerExample**.dll, který jste vytvořili v předchozím postupu. Vyberte **TestContainerExample**.dll a kliknutím **otevřete** tlačítko načíst uživatelské ovládací prvky  
  
6.  Použití **vyberte uživatelský ovládací prvek** <xref:System.Windows.Forms.ComboBox> přepínat mezi dvěma uživatelské ovládací prvky z **TestContainerExample** projektu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.UserControl>  
 [Postupy: vytváření složených ovládacích prvků](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 [Návod: Vytvoření složeného ovládacího prvku pomocí Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 [Uživatel Designer ovládacího prvku](http://msdn.microsoft.com/en-us/2abb9eec-ba32-45cb-b73d-8b52a8bd6bf1)
