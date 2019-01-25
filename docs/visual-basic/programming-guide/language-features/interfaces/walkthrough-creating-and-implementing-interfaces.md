---
title: Vytvoření a implementace rozhraní (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: 7a5694826e0fff82aceb8ad18f75f96f308e724c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680384"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a>Průvodce: Vytvoření a implementace rozhraní (Visual Basic)

Rozhraní popisují vlastnosti vlastnosti, metody a události, ale nechat podrobnosti implementace až struktur nebo tříd.  
  
 Tento návod ukazuje, jak deklarovat a implementovat rozhraní.  
  
> [!NOTE]
>  Tento průvodce neposkytuje informace o tom, jak vytvořit uživatelské rozhraní.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a>Chcete-li definovat rozhraní
  
1.  Otevřete nový projekt aplikace Windows jazyka Visual Basic.  
  
2.  Přidat nový modul do projektu kliknutím **přidat modul** na **projektu** nabídky.  
  
3.  Název nového modulu `Module1.vb` a klikněte na tlačítko **přidat**. Zobrazí se kód pro nový modul.  
  
4.  Definujte rozhraní s názvem `TestInterface` v rámci `Module1` zadáním `Interface TestInterface` mezi `Module` a `End Module` příkazy a stiskněte klávesu ENTER. **Editor kódu** odsazení `Interface` – klíčové slovo a přidá `End Interface` příkaz k vytvoření bloku kódu.  
  
5.  Definovat vlastnosti, metody a události pro rozhraní tak, že následující kód mezi `Interface` a `End Interface` příkazy:  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a>Implementace

 Můžete si všimnout, že syntaxe slouží k deklaraci členy rozhraní se liší od syntaxe používané pro deklaraci členů třídy. Tento rozdíl odráží fakt, že rozhraní nemůžou obsahovat implementační kód.  
  
### <a name="to-implement-the-interface"></a>Implementace rozhraní
  
1.  Přidejte třídu pojmenovanou `ImplementationClass` přidáním následujícího příkazu `Module1`, poté, co `End Interface` příkaz ale předtím, než `End Module` příkaz a stiskněte klávesu ENTER:  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     Pokud pracujete v rámci integrovaného vývojového prostředí **Editor kódu** dodává odpovídající `End Class` při stisknutí klávesy ENTER.  
  
2.  Přidejte následující `Implements` příkazu `ImplementationClass`, která pojmenuje rozhraní třídy implementuje:  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     Když se uvádějí odděleně od jiných položek v horní části třídy nebo struktury, `Implements` příkaz označuje, že třída nebo struktura implementuje rozhraní.  
  
     Pokud pracujete v rámci integrovaného vývojového prostředí **Editor kódu** implementuje členy třídy, které jsou vyžadované `TestInterface` při stisknutí klávesy ENTER a můžete přeskočit na další krok.  
  
3.  Pokud nepracujete v rámci integrovaného vývojového prostředí, musí implementovat členy rozhraní `MyInterface`. Přidejte následující kód, který `ImplementationClass` k implementaci `Event1`, `Method1`, a `Prop1`:  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     `Implements` Příkaz názvy rozhraní a se implementuje člena rozhraní.  
  
4.  Dokončení definice `Prop1` přidáním soukromé pole do třídy, která je uložená hodnota vlastnosti:  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     Vrátí hodnotu `pval` z vlastnosti načtení přístupového objektu.  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     Nastavte hodnotu `pval` ve vlastnosti nastavení přístupového objektu.  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5.  Dokončení definice `Method1` přidáním následujícího kódu.  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a>K otestování implementace rozhraní
  
1.  Klikněte pravým tlačítkem na formuláři po spuštění pro váš projekt v **Průzkumníka řešení**a klikněte na tlačítko **zobrazit kód**. Editor zobrazí třídu pro daný formulář spuštění. Ve výchozím nastavení, se nazývá změna formuláře úvodního formuláře `Form1`.  
  
2.  Přidejte následující `testInstance` pole `Form1` třídy:  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     Deklarováním `testInstance` jako `WithEvents`, `Form1` třídy můžete zpracovávat jeho události.  
  
3.  Přidejte následující obslužnou rutinu události pro `Form1` třídy zpracovávají události vyvolané `testInstance`:  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4.  Přidat podprogram s názvem `Test` k `Form1` se třídou k testování implementace třídy:  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     `Test` Procedura vytvoří instanci třídy, která implementuje `MyInterface`, přiřadí tuto instanci k `testInstance` pole, nastaví vlastnost a spustí metodu rozhraní.  
  
5.  Přidejte kód pro volání `Test` procedury ze `Form1 Load` postup formuláře po spuštění:  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6.  Spustit `Test` postup stisknutím klávesy F5. Zobrazí se zpráva "vlastnost1 byl nastaven na 9". Zobrazí se po kliknutí na OK, zpráva "X parametr – metoda1 je 5". Klikněte na tlačítko OK a zobrazí se zpráva "Obslužná rutina události byla zachycena událost".  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Implements](../../../../visual-basic/language-reference/statements/implements-statement.md)
- [Rozhraní](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Příkaz Interface](../../../../visual-basic/language-reference/statements/interface-statement.md)
- [Příkaz Event](../../../../visual-basic/language-reference/statements/event-statement.md)
