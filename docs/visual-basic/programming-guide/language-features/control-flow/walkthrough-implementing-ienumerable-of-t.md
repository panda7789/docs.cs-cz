---
title: Implementace rozhraní IEnumerable
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: 582957c91eac63cf7f72dd2f6c0cf40e627be686
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402028"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>Návod: Implementace IEnumerable(Of T) v jazyce Visual Basic
<xref:System.Collections.Generic.IEnumerable%601>Rozhraní je implementováno třídami, které mohou vracet sekvenci hodnot po jednotlivých položkách najednou. Výhodou vrácení dat jedné položky v čase je, že není nutné načíst úplnou sadu dat do paměti, abyste s ní mohli pracovat. K načtení jedné položky z dat stačí použít dostatek paměti. Třídy, které implementují `IEnumerable(T)` rozhraní, lze použít s `For Each` cykly nebo dotazy LINQ.  
  
 Představte si například aplikaci, která musí číst velký textový soubor a vrátí každý řádek ze souboru, který odpovídá konkrétním kritériím hledání. Aplikace používá dotaz LINQ k vrácení řádků ze souboru, které odpovídají zadaným kritériím. K dotazování obsahu souboru pomocí dotazu LINQ může aplikace načíst obsah souboru do pole nebo kolekce. Načtení celého souboru do pole nebo kolekce by však využívalo mnohem více paměti, než je vyžadováno. Dotaz LINQ může místo toho zadat dotaz na obsah souboru pomocí vyčíslitelné třídy a vracet pouze hodnoty, které odpovídají kritériím vyhledávání. Dotazy, které vracejí pouze pár hodnot, by využívaly mnohem méně paměti.  
  
 Můžete vytvořit třídu, která implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní k vystavení zdrojových dat jako vyčíslitelného data. Vaše třída, která implementuje `IEnumerable(T)` rozhraní, bude vyžadovat další třídu, která implementuje <xref:System.Collections.Generic.IEnumerator%601> rozhraní pro iteraci skrze zdrojová data. Tyto dvě třídy umožňují vracet položky dat sekvenčně jako konkrétní typ.  
  
 V tomto návodu vytvoříte třídu, která implementuje `IEnumerable(Of String)` rozhraní a třídu, která implementuje `IEnumerator(Of String)` rozhraní pro čtení textového souboru v jednom řádku.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>Vytváření vyčíslitelné třídy  
  
**Vytvoření vyčíslitelného projektu třídy**

1. V Visual Basic v nabídce **soubor** přejděte na příkaz **Nový** a potom klikněte na **projekt**.

1. V dialogovém okně **Nový projekt** v podokně **typy projektů** se ujistěte, že je vybrána možnost **Windows** . V podokně **šablony** vyberte **Knihovna tříd** . Do pole **název** zadejte `StreamReaderEnumerable` a pak klikněte na **OK**. Zobrazí se nový projekt.

1. V **Průzkumník řešení**klikněte pravým tlačítkem na soubor Class1. vb a klikněte na **Přejmenovat**. Přejmenujte soubor na `StreamReaderEnumerable.vb` a stiskněte klávesu ENTER. Přejmenováním souboru dojde také k přejmenování třídy na `StreamReaderEnumerable` . Tato třída implementuje `IEnumerable(Of String)` rozhraní.

1. Klikněte pravým tlačítkem na projekt StreamReaderEnumerable, přejděte na **Přidat**a klikněte na **Nová položka**. Vyberte šablonu **třídy** . Do pole **název** zadejte `StreamReaderEnumerator.vb` a klikněte na **OK**.

 První třída v tomto projektu je vyčíslitelné třída a implementuje `IEnumerable(Of String)` rozhraní. Toto obecné rozhraní implementuje <xref:System.Collections.IEnumerable> rozhraní a zaručuje, že příjemci této třídy mají přístup k hodnotám, které jsou zadány jako `String` .  
  
**Přidejte kód pro implementaci rozhraní IEnumerable**

1. Otevřete soubor StreamReaderEnumerable. vb.

2. Na řádku `Public Class StreamReaderEnumerable` Zadejte následující příkaz a stiskněte klávesu ENTER.

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   Visual Basic automaticky naplní třídu členy, které jsou vyžadovány `IEnumerable(Of String)` rozhraním.
  
3. Tato Výčtová třída načte řádky z textového souboru po jednom řádku. Přidejte následující kód do třídy k vystavení veřejného konstruktoru, který jako vstupní parametr převezme cestu k souboru.

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. Vaše implementace <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metody `IEnumerable(Of String)` rozhraní vrátí novou instanci `StreamReaderEnumerator` třídy. Implementaci `GetEnumerator` metody `IEnumerable` rozhraní lze vytvořit `Private` , protože je nutné vystavit pouze členy `IEnumerable(Of String)` rozhraní. Nahraďte kód, který Visual Basic vygeneroval pro `GetEnumerator` metody, pomocí následujícího kódu.

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
**Přidání kódu pro implementaci rozhraní IEnumerator**

1. Otevřete soubor StreamReaderEnumerator. vb.

2. Na řádku `Public Class StreamReaderEnumerator` Zadejte následující příkaz a stiskněte klávesu ENTER.

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   Visual Basic automaticky naplní třídu členy, které jsou vyžadovány `IEnumerator(Of String)` rozhraním.

3. Třída enumerator otevře textový soubor a provede vstupně-výstupní operace souboru pro čtení řádků ze souboru. Přidejte následující kód do třídy k vystavení veřejného konstruktoru, který jako vstupní parametr převezme cestu k souboru, a otevřete textový soubor pro čtení.

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. `Current`Vlastnosti `IEnumerator(Of String)` `IEnumerator` rozhraní a vracejí aktuální položku z textového souboru jako `String` . Implementaci `Current` vlastnosti `IEnumerator` rozhraní lze vytvořit `Private` , protože je nutné vystavit pouze členy `IEnumerator(Of String)` rozhraní. Nahraďte kód, který Visual Basic vygeneroval pro `Current` vlastnosti, pomocí následujícího kódu.

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. `MoveNext`Metoda `IEnumerator` rozhraní přejde na další položku v textovém souboru a aktualizuje hodnotu vrácenou `Current` vlastností. Pokud nejsou k dispozici žádné další položky ke čtení, `MoveNext` Metoda vrátí hodnotu `False` ; v opačném případě se `MoveNext` Metoda vrátí `True` . Do metody `MoveNext` přidejte následující kód.

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. `Reset`Metoda `IEnumerator` rozhraní přesměruje iterátor, aby odkazoval na začátek textového souboru a vymaže hodnotu aktuální položky. Do metody `Reset` přidejte následující kód.

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. `Dispose`Metoda `IEnumerator` rozhraní zaručuje, že všechny nespravované prostředky jsou uvolněny před zničením iterátoru. Popisovač souboru, který je používán `StreamReader` objektem, je nespravovaný prostředek a je třeba jej zavřít před zničením instance iterátoru. Nahraďte kód, který Visual Basic vygeneroval pro `Dispose` metodu, pomocí následujícího kódu.

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)]
  
## <a name="using-the-sample-iterator"></a>Použití ukázkového iterátoru

 V kódu můžete použít vyčíslitelné třídy společně s řídicími strukturami, které vyžadují objekt, který implementuje `IEnumerable` , jako je například `For Next` smyčka nebo dotaz LINQ. Následující příklad ukazuje `StreamReaderEnumerable` v dotazu LINQ.  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a>Viz také

- [Představení technologie LINQ v jazyce Visual Basic](../linq/introduction-to-linq.md)
- [Tok řízení](index.md)
- [Struktury smyčky](loop-structures.md)
- [For Each...Next – příkaz](../../../language-reference/statements/for-each-next-statement.md)
