---
title: Definice tříd (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: aac30a8b0272ae6c141138a91585953237ab8098
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-defining-classes-visual-basic"></a>Návod: Definování tříd (Visual Basic)

Tento návod ukazuje, jak definovat třídy, které pak můžete použít k vytváření objektů. Také ukazuje, jak přidat vlastnosti a metody pro novou třídu a ukazuje, jak k chybě při inicializaci objektu.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a>Chcete-li definovat třídu
  
1.  Vytvoření projektu kliknutím **nový projekt** na **souboru** nabídky. **Nový projekt** zobrazí se dialogové okno.  
  
2.  Aplikace systému Windows vyberte ze seznamu šablon projektu jazyka Visual Basic pro zobrazení nového projektu.  
  
3.  Přidejte novou třídu do projektu kliknutím **přidat třídu** na **projektu** nabídky. **Přidat novou položku** zobrazí se dialogové okno.  
  
4.  Vyberte **třída** šablony.  
  
5.  Pojmenujte novou třídu `UserNameInfo.vb`a potom klikněte na **přidat** k zobrazení kódu nové třídy.  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    >  Můžete použít Visual Basicu **Editor kódu** přidat třídu do svého formuláře spuštění zadáním `Class` – klíčové slovo a název nové třídy. **Editor kódu** poskytuje odpovídající `End Class` příkaz za vás.  
  
6.  Definování soukromé pole pro třídu přidáním následujícího kódu mezi `Class` a `End Class` příkazy:  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     Deklarace pole jako `Private` znamená ho lze použít pouze v rámci třídy. Můžete zpřístupnit pole z mimo třídu pomocí modifikátory přístupu, jako `Public` , poskytovat další přístup. Další informace najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
7.  Definujte vlastnosti pro třídu přidáním následující kód:  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8.  Definujte metody pro třídu přidáním následující kód:  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. Definice parametrizované konstruktoru pro novou třídu přidáním proceduru s názvem `Sub New`:  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     `Sub New` Konstruktor je automaticky volána, když je vytvořen objekt na základě této třídy. Tento konstruktor nastaví hodnotu pole, která obsahuje uživatelské jméno.  
  
## <a name="to-create-a-button-to-test-the-class"></a>Chcete-li vytvořit tlačítko můžete otestovat třídy
  
1.  Změnit formulář spuštění do režimu návrhu kliknutím pravým tlačítkem na jeho název v **Průzkumníku řešení** a pak levým na **Návrhář zobrazení**. Ve výchozím nastavení je spouštěcí formulář pro projekty Windows aplikací s názvem Form1.vb. Hlavní formulář se potom zobrazí.  
  
2.  Přidání tlačítka do hlavní formulář a poklikejte na něj zobrazíte kód pro `Button1_Click` obslužné rutiny události. Přidejte následující kód k volání procedury testu:  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a>Spusťte aplikaci
  
1.  Spusťte aplikaci stisknutím klávesy F5. Klikněte na tlačítko ve formuláři voláním procedury testu. Zobrazí zprávu, že původní `UserName` je "STOKLASY, Jana", protože procedura volána `Capitalize` metodu objektu.  
  
2.  Klikněte na tlačítko **OK** se zavřít okno se zprávou. `Button1 Click` Postup změní hodnotu `UserName` vlastnost a zobrazí zprávu, že nová hodnota `UserName` je "Worden, Jan".  
  
## <a name="see-also"></a>Viz také

[Objektově orientované programování (Visual Basic)](../../concepts/object-oriented-programming.md)  
[Objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)