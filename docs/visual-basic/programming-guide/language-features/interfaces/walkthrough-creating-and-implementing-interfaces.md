---
title: Vytvoření a implementace rozhraní
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: 89e8f91a04b25b84bc783d5c4f4b91cf12426f72
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405064"
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
  
4. Zadejte rozhraní `TestInterface` , které je pojmenované v rámci `Module1` , zadáním `Interface TestInterface` mezi `Module` `End Module` příkazy a a stisknutím klávesy ENTER. **Editor kódu** odsadí `Interface` klíčové slovo a přidá `End Interface` příkaz pro vytvoření bloku kódu.  
  
5. Určete vlastnost, metodu a událost pro rozhraní umístěním následujícího kódu mezi `Interface` `End Interface` příkazy a:  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a>Implementace

 Můžete si všimnout, že syntaxe použitá pro deklaraci členů rozhraní se liší od syntaxe použité k deklaraci členů třídy. Tento rozdíl odráží skutečnost, že rozhraní nemohou obsahovat implementační kód.  
  
### <a name="to-implement-the-interface"></a>Implementace rozhraní
  
1. Přidejte třídu s názvem `ImplementationClass` přidáním následujícího příkazu do `Module1` , po `End Interface` příkazu, ale před `End Module` příkazem, a stisknutím klávesy ENTER:  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     Pokud pracujete v integrovaném vývojovém prostředí, **Editor kódu** `End Class` při stisknutí klávesy ENTER dodá odpovídajícího příkazu.  
  
2. Přidejte následující `Implements` příkaz do `ImplementationClass` , který pojmenuje rozhraní, které třída implementuje:  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     Pokud je uvedeno odděleně od jiných položek v horní části třídy nebo struktury, `Implements` příkaz označuje, že třída nebo struktura implementuje rozhraní.  
  
     Pokud pracujete v integrovaném vývojovém prostředí, **Editor kódu** implementuje členy třídy vyžadované `TestInterface` při stisknutí klávesy ENTER a můžete přeskočit další krok.  
  
3. Pokud nepracujete v integrovaném vývojovém prostředí, je nutné implementovat všechny členy rozhraní `MyInterface` . Přidejte následující kód k `ImplementationClass` implementaci `Event1` , `Method1` a `Prop1` :  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     `Implements`Příkaz zajmenovává rozhraní a člen rozhraní, které je implementováno.  
  
4. Dokončete definici `Prop1` přidáním soukromého pole do třídy, která ukládá hodnotu vlastnosti:  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     Vrátí hodnotu `pval` z přístupového objektu Get vlastnosti.  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     Nastavte hodnotu `pval` v přístupovém objektu sady vlastností.  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5. Dokončete definici `Method1` přidáním následujícího kódu.  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a>Testování implementace rozhraní
  
1. Klikněte pravým tlačítkem myši na spouštěcí formulář v **Průzkumník řešení**a klikněte na **Zobrazit kód**. Editor zobrazuje třídu pro úvodní formulář. Ve výchozím nastavení se volá formulář pro spuštění `Form1` .  
  
2. `testInstance`Do třídy přidejte následující pole `Form1` :  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     Deklarováním `testInstance` jako `WithEvents` `Form1` může třída zpracovávat své události.  
  
3. Přidejte následující obslužnou rutinu události do `Form1` třídy pro zpracování událostí vyvolaných `testInstance` :  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4. Přidejte podprogram s názvem `Test` do `Form1` třídy pro otestování třídy implementace:  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     `Test`Procedura vytvoří instanci třídy, která implementuje `MyInterface` , přiřadí tuto instanci k `testInstance` poli, nastaví vlastnost a spustí metodu prostřednictvím rozhraní.  
  
5. Přidejte kód pro volání `Test` procedury z `Form1 Load` procedury spouštěcího formuláře:  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6. Spusťte `Test` proceduru stisknutím klávesy F5. Zobrazí se zpráva "Prop1 byl nastaven na 9". Po kliknutí na tlačítko OK se zobrazí zpráva "parametr X pro – Metoda1 je 5". Klikněte na tlačítko OK a zobrazí se zpráva "obslužná rutina události byla zachycena událost".  
  
## <a name="see-also"></a>Viz také

- [Implements – Příkaz](../../../language-reference/statements/implements-statement.md)
- [Rozhraní](index.md)
- [Interface – příkaz](../../../language-reference/statements/interface-statement.md)
- [Event – příkaz](../../../language-reference/statements/event-statement.md)
