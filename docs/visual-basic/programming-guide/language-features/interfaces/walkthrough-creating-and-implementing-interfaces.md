---
title: "Vytvoření a implementace rozhraní (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 08bf6dc7344d4f83c8ab1908fdeb29eb4a53e142
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a>Návod: Vytvoření a implementace rozhraní (Visual Basic)
Rozhraní popisují charakteristiky vlastností, metod a událostí, ale nechte podrobnosti implementace až struktury nebo třídy.  
  
 Tento návod ukazuje, jak deklarace a implementovat rozhraní.  
  
> [!NOTE]
>  Tento návod neposkytuje informace o tom, jak vytvořit uživatelské rozhraní.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-define-an-interface"></a>Chcete-li definovat rozhraní  
  
1.  Otevřete nový [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projekt aplikace Windows.  
  
2.  Přidejte nový modul do projektu kliknutím **přidat modul** na **projektu** nabídky.  
  
3.  Název nového modulu `Module1.vb` a klikněte na tlačítko **přidat**. Kód pro nový modul se zobrazí.  
  
4.  Definování rozhraní s názvem `TestInterface` v rámci `Module1` zadáním `Interface TestInterface` mezi `Module` a `End Module` příkazy a stiskněte ENTER. **Editor kódu** odsazení `Interface` – klíčové slovo a přidá `End Interface` příkaz k vytvoření bloku kódu.  
  
5.  Definuje vlastnosti, metodu a událostí pro rozhraní následující kód mezi umístěním `Interface` a `End Interface` příkazy:  
  
     [!code-vb[VbVbalrOOP#98](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_1.vb)]  
  
## <a name="implementation"></a>Implementace  
 Můžete si všimnout, že syntaxe používá k deklaraci členové rozhraní se liší od syntaxe používá k deklaraci členy třídy. Tento rozdíl odráží fakt, že rozhraní nemůže obsahovat implementaci kódu.  
  
#### <a name="to-implement-the-interface"></a>Implementace rozhraní  
  
1.  Přidejte třídu s názvem `ImplementationClass` přidáním následující příkaz a `Module1`, po `End Interface` příkaz ale předtím, než `End Module` příkaz a stiskněte ENTER:  
  
     [!code-vb[VbVbalrOOP#99](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_2.vb)]  
  
     Pokud pracujete v integrovaném vývojovém prostředí, **Editor kódu** poskytuje odpovídající `End Class` příkaz po stisknutí klávesy ENTER.  
  
2.  Přidejte následující `Implements` příkaz, který má `ImplementationClass`, které názvy rozhraní třída implementuje:  
  
     [!code-vb[VbVbalrOOP#100](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_3.vb)]  
  
     Když uvedené odděleně od jiných položek v horní části třídu nebo strukturu, `Implements` příkaz označuje, že třídu nebo strukturu implementuje rozhraní.  
  
     Pokud pracujete v integrovaném vývojovém prostředí, **Editor kódu** implementuje členy třídy vyžadovanou `TestInterface` při stisknutí klávesy ENTER, a můžete přejít na další krok.  
  
3.  Pokud nepracujete v integrovaném vývojovém prostředí, je nutné implementovat všechny členy rozhraní `MyInterface`. Přidejte následující kód, který `ImplementationClass` implementovat `Event1`, `Method1`, a `Prop1`:  
  
     [!code-vb[VbVbalrOOP#101](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_4.vb)]  
  
     `Implements` Příkaz názvy rozhraní a člena rozhraní se implementuje.  
  
4.  Dokončit definici `Prop1` přidáním soukromé pole na třídu, která uložená hodnota vlastnosti:  
  
     [!code-vb[VbVbalrOOP#102](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_5.vb)]  
  
     Vrátí hodnotu `pval` z vlastnosti načtení přístupového objektu.  
  
     [!code-vb[VbVbalrOOP#103](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_6.vb)]  
  
     Nastavte hodnotu `pval` ve vlastnosti nastavení přístupového objektu.  
  
     [!code-vb[VbVbalrOOP#104](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_7.vb)]  
  
5.  Dokončit definici `Method1` přidáním následující kód.  
  
     [!code-vb[VbVbalrOOP#105](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_8.vb)]  
  
#### <a name="to-test-the-implementation-of-the-interface"></a>Pro testování implementace rozhraní  
  
1.  Klikněte pravým tlačítkem na spouštěcí formulář pro projekt v **Průzkumníku řešení**a klikněte na tlačítko **kód zobrazení**. Editor zobrazí třídu pro formulář spuštění. Ve výchozím nastavení, je volána spouštěcí formulář `Form1`.  
  
2.  Přidejte následující `testInstance` pole na `Form1` třídy:  
  
     [!code-vb[VbVbalrOOP#120](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_9.vb)]  
  
     Deklarováním `testInstance` jako `WithEvents`, `Form1` třída může zpracovávat události.  
  
3.  Přidejte následující obslužné rutiny události pro `Form1` třídy pro zpracování události vyvolané službou `testInstance`:  
  
     [!code-vb[VbVbalrOOP#106](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_10.vb)]  
  
4.  Přidat podprogramu s názvem `Test` k `Form1` třída k testování třída implementace:  
  
     [!code-vb[VbVbalrOOP#107](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_11.vb)]  
  
     `Test` Postup vytvoří instanci třídy, který implementuje `MyInterface`, přiřadí tuto instanci k `testInstance` pole, nastaví vlastnost a spustí metodu přes rozhraní.  
  
5.  Přidejte kód volání `Test` procedury `Form1 Load` postup spuštění formuláře:  
  
     [!code-vb[VbVbalrOOP#108](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_12.vb)]  
  
6.  Spustit `Test` postup stisknutím klávesy F5. Zobrazí se zpráva "vlastnost1 byla nastavena na 9". Zobrazí se po kliknutí na tlačítko OK, zpráva "parametr X pro Method1 je 5". Klikněte na tlačítko OK a zobrazí se zpráva "obslužné rutiny události zachycena událost".  
  
## <a name="see-also"></a>Viz také  
 [Implements – příkaz](../../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Rozhraní](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
 [Interface – příkaz](../../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Event – příkaz](../../../../visual-basic/language-reference/statements/event-statement.md)
