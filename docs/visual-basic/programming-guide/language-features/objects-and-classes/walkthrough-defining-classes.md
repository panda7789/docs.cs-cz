---
title: Definování tříd
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
ms.openlocfilehash: bd3f6e5cff41551240d9904ab93af8758eb104d2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346078"
---
# <a name="walkthrough-defining-classes-visual-basic"></a>Návod: Definování tříd (Visual Basic)

Tento návod ukazuje, jak definovat třídy, které pak můžete použít k vytvoření objektů. Také ukazuje, jak přidat vlastnosti a metody do nové třídy a ukazuje, jak inicializovat objekt.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a>Definování třídy
  
1. Vytvořte projekt kliknutím na **Nový projekt** v nabídce **soubor** . Zobrazí se dialogové okno **Nový projekt** .  
  
2. Vyberte možnost aplikace systému Windows ze seznamu Visual Basic šablony projektu, chcete-li zobrazit nový projekt.  
  
3. Kliknutím na **Přidat třídu** v nabídce **projekt** přidejte do projektu novou třídu. Zobrazí se dialogové okno **Přidat novou položku** .  
  
4. Vyberte šablonu **třídy** .  
  
5. Pojmenujte novou třídu `UserNameInfo.vb`a potom kliknutím na tlačítko **Přidat** zobrazte kód pro novou třídu.  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    > Pomocí **editoru kódu** Visual Basic můžete přidat třídu do formuláře po spuštění zadáním klíčového slova `Class` následovaného názvem nové třídy. **Editor kódu** poskytuje odpovídající příkaz `End Class` za vás.  
  
6. Definujte soukromé pole pro třídu přidáním následujícího kódu mezi příkazy `Class` a `End Class`:  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     Deklarace pole jako `Private` znamená, že může být použita pouze v rámci třídy. Pole, která jsou k dispozici vně třídy, můžete zpřístupnit pomocí modifikátorů přístupu, jako je `Public`, které poskytují další přístup. Další informace najdete v tématu [úrovně přístupu v Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
7. Definujte vlastnost pro třídu přidáním následujícího kódu:  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8. Definujte metodu pro třídu přidáním následujícího kódu:  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. Definujte parametrizovaný konstruktor pro novou třídu přidáním procedury s názvem `Sub New`:  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     Konstruktor `Sub New` se nazývá automaticky při vytvoření objektu založeného na této třídě. Tento konstruktor nastaví hodnotu pole, které obsahuje uživatelské jméno.  
  
## <a name="to-create-a-button-to-test-the-class"></a>Chcete-li vytvořit tlačítko pro otestování třídy
  
1. Změňte spouštěcí formulář na režim návrhu kliknutím pravým tlačítkem myši na jeho název v **Průzkumník řešení** a následným kliknutím na položku **Návrhář zobrazení**. Ve výchozím nastavení je úvodní formulář pro projekty aplikací pro Windows pojmenovaný Form1. vb. Pak se zobrazí hlavní formulář.  
  
2. Přidejte do hlavního formuláře tlačítko a dvojím kliknutím na něj zobrazte kód pro obslužnou rutinu události `Button1_Click`. Přidejte následující kód pro volání testovací procedury:  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a>Spuštění aplikace
  
1. Spusťte aplikaci stisknutím klávesy F5. Klikněte na tlačítko ve formuláři pro volání testovací procedury. Zobrazí se zpráva s oznámením, že původní `UserName` jsou "MOORE, BOBBY", protože procedura volala metodu `Capitalize` objektu.  
  
2. Kliknutím na tlačítko **OK** zavřete okno se zprávou. Procedura `Button1 Click` změní hodnotu vlastnosti `UserName` a zobrazí zprávu s oznámením, že nová hodnota `UserName` je "Worden, Jana".  
  
## <a name="see-also"></a>Viz také:

- [Objektově orientované programování (Visual Basic)](../../concepts/object-oriented-programming.md)
- [Objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
