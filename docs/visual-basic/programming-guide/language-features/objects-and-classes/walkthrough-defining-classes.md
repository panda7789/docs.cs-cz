---
title: "Definice tříd (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- execution [Visual Basic], ending
- objects [Visual Basic], initializing
- Initialize event [Visual Basic]
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- objects [Visual Basic], creating
- program termination
- classes [Visual Basic], walkthroughs
- class modules, walkthroughs
- Terminate event [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ec002e1709fa5fe31dfe7744fb91a230c32337a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-defining-classes-visual-basic"></a>Návod: Definování tříd (Visual Basic)
Tento návod ukazuje, jak definovat třídy, které pak můžete použít k vytváření objektů. Také ukazuje, jak přidat vlastnosti a metody pro novou třídu a ukazuje, jak k chybě při inicializaci objektu.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-define-a-class"></a>Chcete-li definovat třídu  
  
1.  Vytvoření projektu kliknutím **nový projekt** na **souboru** nabídky. **Nový projekt** zobrazí se dialogové okno.  
  
2.  Vyberte ze seznamu aplikací systému Windows [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] šablony zobrazíte nový projekt projektu.  
  
3.  Přidejte novou třídu do projektu kliknutím **přidat třídu** na **projektu** nabídky. **Přidat novou položku** zobrazí se dialogové okno.  
  
4.  Vyberte **třída** šablony.  
  
5.  Pojmenujte novou třídu `UserNameInfo.vb`a potom klikněte na **přidat** k zobrazení kódu nové třídy.  
  
     [!code-vb[VbVbalrOOP#5](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_1.vb)]  
  
    > [!NOTE]
    >  Můžete použít [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] **Editor kódu** přidat třídu do svého formuláře spuštění zadáním `Class` – klíčové slovo a název nové třídy. **Editor kódu** poskytuje odpovídající `End Class` příkaz za vás.  
  
6.  Definování soukromé pole pro třídu přidáním následujícího kódu mezi `Class` a `End Class` příkazy:  
  
     [!code-vb[VbVbalrOOP#7](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_2.vb)]  
  
     Deklarace pole jako `Private` znamená ho lze použít pouze v rámci třídy. Můžete zpřístupnit pole z mimo třídu pomocí modifikátory přístupu, jako `Public` , poskytovat další přístup. Další informace najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
7.  Definujte vlastnosti pro třídu přidáním následující kód:  
  
     [!code-vb[VbVbalrOOP#8](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_3.vb)]  
  
8.  Definujte metody pro třídu přidáním následující kód:  
  
     [!code-vb[VbVbalrOOP#9](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_4.vb)]  
  
9. Definice parametrizované konstruktoru pro novou třídu přidáním proceduru s názvem `Sub New`:  
  
     [!code-vb[VbVbalrOOP#10](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_5.vb)]  
  
     `Sub New` Konstruktor je automaticky volána, když je vytvořen objekt na základě této třídy. Tento konstruktor nastaví hodnotu pole, která obsahuje uživatelské jméno.  
  
### <a name="to-create-a-button-to-test-the-class"></a>Chcete-li vytvořit tlačítko můžete otestovat třídy  
  
1.  Změnit formulář spuštění do režimu návrhu kliknutím pravým tlačítkem na jeho název v **Průzkumníku řešení** a pak levým na **Návrhář zobrazení**. Ve výchozím nastavení je spouštěcí formulář pro projekty Windows aplikací s názvem Form1.vb. Hlavní formulář se potom zobrazí.  
  
2.  Přidání tlačítka do hlavní formulář a poklikejte na něj zobrazíte kód pro `Button1_Click` obslužné rutiny události. Přidejte následující kód k volání procedury testu:  
  
     [!code-vb[VbVbalrOOP#12](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_6.vb)]  
  
### <a name="to-run-your-application"></a>Spusťte aplikaci  
  
1.  Spusťte aplikaci stisknutím klávesy F5. Klikněte na tlačítko ve formuláři voláním procedury testu. Zobrazí zprávu, že původní `UserName` je "STOKLASY, Jana", protože procedura volána `Capitalize` metodu objektu.  
  
2.  Klikněte na tlačítko **OK** se zavřít okno se zprávou. `Button1 Click` Postup změní hodnotu `UserName` vlastnost a zobrazí zprávu, že nová hodnota `UserName` je "Worden, Jan".  
  
## <a name="see-also"></a>Viz také  
 [Objektově orientované programování](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)  
 [Objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
