---
title: Definování třídy (Visual Basic)
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
ms.openlocfilehash: 3129824f6e4047420c422503cc366a1c8d28b7e7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326213"
---
# <a name="walkthrough-defining-classes-visual-basic"></a>Návod: Definování třídy (Visual Basic)

Tento návod ukazuje, jak definovat třídy, které pak můžete použít k vytváření objektů. Také ukazuje, jak přidat vlastnosti a metody do nové třídy a ukazuje, jak inicializovat objekt.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a>Definování třídy
  
1. Vytvořte projekt kliknutím **nový projekt** na **souboru** nabídky. Zobrazí se dialogové okno **Nový projekt**.  
  
2. Vyberte ze seznamu šablon projektů jazyka Visual Basic k zobrazení nového projektu aplikace Windows.  
  
3. Přidejte novou třídu do projektu kliknutím **přidat třídu** na **projektu** nabídky. Zobrazí se dialogové okno **Přidat novou položku**.  
  
4. Vyberte **třídy** šablony.  
  
5. Pojmenujte novou třídu `UserNameInfo.vb`a potom klikněte na tlačítko **přidat** zobrazíte kód pro novou třídu.  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    >  Můžete použít Visual Basic **Editor kódu** přidání třídy do svého formuláře po spuštění zadáním `Class` – klíčové slovo, za nímž následuje název nové třídy. **Editor kódu** poskytuje odpovídající `End Class` příkaz za vás.  
  
6. Definovat privátní pole pro třídu přidáním následujícího kódu mezi `Class` a `End Class` příkazy:  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     Deklarace pole jako `Private` znamená, že je možné pouze v rámci třídy. Můžete zpřístupnit pole z mimo třídu pomocí modifikátorů přístupu, jako `Public` , které poskytují další přístup. Další informace najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
7. Definujte vlastnost třídy přidáním následujícího kódu:  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8. Definování metody pro třídu přidáním následujícího kódu:  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. Definování konstruktoru s parametry pro novou třídu přidáním postup s názvem `Sub New`:  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     `Sub New` Konstruktor je automaticky volána, když je vytvořen objekt na základě této třídy. Tento konstruktor nastaví hodnotu pole, která obsahuje uživatelské jméno.  
  
## <a name="to-create-a-button-to-test-the-class"></a>Chcete-li vytvořit tlačítko pro testovací třídu
  
1. Změna formuláře úvodního formuláře do režimu návrhu kliknutím pravým tlačítkem myši jejího názvu do **Průzkumníka řešení** a pak levým na **Návrhář zobrazení**. Ve výchozím nastavení je formulář spuštění pro projekty aplikací pro Windows s názvem Form1.vb. Hlavní formulář se potom zobrazí.  
  
2. Přidání tlačítka pro hlavní formulář a dvojím kliknutím ho zobrazte kód `Button1_Click` obslužné rutiny události. Přidejte následující kód do volání procedury testu:  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a>Ke spuštění aplikace
  
1. Stisknutím klávesy F5 spusťte aplikaci. Klikněte na tlačítko na formulář pro volání procedury testu. Zobrazí se zpráva oznamující, že původní `UserName` je "MOORE, Jana", protože procedura volána `Capitalize` metodu objektu.  
  
2. Klikněte na tlačítko **OK** zavřete okno se zprávou. `Button1 Click` Postupu změní hodnotu `UserName` vlastnost a zobrazí zprávu oznamující, že nová hodnota `UserName` je "Worden Joe".  
  
## <a name="see-also"></a>Viz také:

- [Objektově orientované programování (Visual Basic)](../../concepts/object-oriented-programming.md)
- [Objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
