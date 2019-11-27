---
title: Vytvoření a implementace rozhraní
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: 47176d2e7a512d8e8c27a90ac04d2a2a2af274b5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345044"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a>Návod: Vytvoření a implementace rozhraní (Visual Basic)

Rozhraní popisují charakteristiky vlastností, metod a událostí, ale ponechají podrobnosti o implementaci až do struktur nebo tříd.  
  
 Tento návod ukazuje, jak deklarovat a implementovat rozhraní.  
  
> [!NOTE]
> Tento návod neposkytuje informace o tom, jak vytvořit uživatelské rozhraní.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a>Definování rozhraní
  
1. Otevřete nový Visual Basic projekt aplikace systému Windows.  
  
2. Přidejte do projektu nový modul kliknutím na **Přidat modul** v nabídce **projekt** .  
  
3. Pojmenujte nový modul `Module1.vb` a klikněte na **Přidat**. Zobrazí se kód nového modulu.  
  
4. V `Module1` definujte rozhraní s názvem `TestInterface` zadáním `Interface TestInterface` mezi příkazy `Module` a `End Module` a potom stiskněte klávesu ENTER. **Editor kódu** odsadí klíčové slovo `Interface` a přidá příkaz `End Interface` pro vytvoření bloku kódu.  
  
5. Určete vlastnost, metodu a událost pro rozhraní umístěním následujícího kódu mezi příkazy `Interface` a `End Interface`:  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a>Implementace

 Můžete si všimnout, že syntaxe použitá pro deklaraci členů rozhraní se liší od syntaxe použité k deklaraci členů třídy. Tento rozdíl odráží skutečnost, že rozhraní nemohou obsahovat implementační kód.  
  
### <a name="to-implement-the-interface"></a>Implementace rozhraní
  
1. Přidejte třídu s názvem `ImplementationClass` přidáním následujícího příkazu do `Module1`, po příkazu `End Interface`, ale před příkazem `End Module` a stisknutím klávesy ENTER:  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     Pokud pracujete v integrovaném vývojovém prostředí, **Editor kódu** při stisknutí klávesy ENTER poskytne při stisknutí odpovídajícího příkazu `End Class`.  
  
2. Přidejte následující příkaz `Implements` do `ImplementationClass`, který název rozhraní implementuje třídou:  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     Pokud je uvedeno odděleně od jiných položek v horní části třídy nebo struktury, příkaz `Implements` označuje, že třída nebo struktura implementuje rozhraní.  
  
     Pokud pracujete v integrovaném vývojovém prostředí, **Editor kódu** implementuje členy třídy vyžadované `TestInterface` po stisknutí klávesy ENTER a můžete přeskočit další krok.  
  
3. Pokud nepracujete v integrovaném vývojovém prostředí, je nutné implementovat všechny členy rozhraní `MyInterface`. Přidejte následující kód, který `ImplementationClass` k implementaci `Event1`, `Method1`a `Prop1`:  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     Příkaz `Implements` zajmenovává rozhraní a člen rozhraní, které je implementováno.  
  
4. Dokončete definici `Prop1` přidáním soukromého pole do třídy, která ukládá hodnotu vlastnosti:  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     Vrátí hodnotu `pval` z vlastnosti get objektu.  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     V přistupujícím objektu sady vlastností nastavte hodnotu `pval`.  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5. Dokončete definici `Method1` přidáním následujícího kódu.  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a>Testování implementace rozhraní
  
1. Klikněte pravým tlačítkem myši na spouštěcí formulář v **Průzkumník řešení**a klikněte na **Zobrazit kód**. Editor zobrazuje třídu pro úvodní formulář. Ve výchozím nastavení se pro úvodní formulář používá `Form1`.  
  
2. Do `Form1` třídy přidejte následující `testInstance` pole:  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     Deklarováním `testInstance` jako `WithEvents`může třída `Form1` zpracovávat své události.  
  
3. Přidejte následující obslužnou rutinu události do třídy `Form1` pro zpracování událostí vyvolaných `testInstance`:  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4. Přidejte podprogram s názvem `Test` do třídy `Form1` k otestování třídy implementace:  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     Procedura `Test` vytvoří instanci třídy, která implementuje `MyInterface`, přiřadí tuto instanci k poli `testInstance`, nastaví vlastnost a spustí metodu prostřednictvím rozhraní.  
  
5. Přidejte kód pro volání `Test` procedury z `Form1 Load` postupu ve spouštěcím formuláři:  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6. Spusťte `Test` proceduru stisknutím klávesy F5. Zobrazí se zpráva "Prop1 byl nastaven na 9". Po kliknutí na tlačítko OK se zobrazí zpráva "parametr X pro – Metoda1 je 5". Klikněte na tlačítko OK a zobrazí se zpráva "obslužná rutina události byla zachycena událost".  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Implements](../../../../visual-basic/language-reference/statements/implements-statement.md)
- [Rozhraní](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Příkaz Interface](../../../../visual-basic/language-reference/statements/interface-statement.md)
- [Příkaz Event](../../../../visual-basic/language-reference/statements/event-statement.md)
