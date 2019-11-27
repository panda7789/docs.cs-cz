---
title: Implementace rozhraní IEnumerable
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: f40fcf7e0724addc478b261dcd36d09e1d8a751a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333689"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>Návod: Implementace IEnumerable(Of T) v jazyce Visual Basic
Rozhraní <xref:System.Collections.Generic.IEnumerable%601> je implementováno třídami, které mohou vracet sekvenci hodnot po jednotlivých položkách najednou. Výhodou vrácení dat jedné položky v čase je, že není nutné načíst úplnou sadu dat do paměti, abyste s ní mohli pracovat. K načtení jedné položky z dat stačí použít dostatek paměti. Třídy, které implementují rozhraní `IEnumerable(T)`, lze použít s `For Each` cykly nebo dotazy LINQ.  
  
 Představte si například aplikaci, která musí číst velký textový soubor a vrátí každý řádek ze souboru, který odpovídá konkrétním kritériím hledání. Aplikace používá dotaz LINQ k vrácení řádků ze souboru, které odpovídají zadaným kritériím. K dotazování obsahu souboru pomocí dotazu LINQ může aplikace načíst obsah souboru do pole nebo kolekce. Načtení celého souboru do pole nebo kolekce by však využívalo mnohem více paměti, než je vyžadováno. Dotaz LINQ může místo toho zadat dotaz na obsah souboru pomocí vyčíslitelné třídy a vracet pouze hodnoty, které odpovídají kritériím vyhledávání. Dotazy, které vracejí pouze pár hodnot, by využívaly mnohem méně paměti.  
  
 Můžete vytvořit třídu, která implementuje rozhraní <xref:System.Collections.Generic.IEnumerable%601> k vystavení zdrojových dat jako vyčíslitelného data. Vaše třída, která implementuje rozhraní `IEnumerable(T)`, bude vyžadovat další třídu, která implementuje rozhraní <xref:System.Collections.Generic.IEnumerator%601> pro iteraci skrze zdrojová data. Tyto dvě třídy umožňují vracet položky dat sekvenčně jako konkrétní typ.  
  
 V tomto návodu vytvoříte třídu, která implementuje rozhraní `IEnumerable(Of String)` a třídu, která implementuje rozhraní `IEnumerator(Of String)` pro čtení textového souboru v jednom řádku.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>Vytváření vyčíslitelné třídy  
  
**Vytvoření vyčíslitelného projektu třídy**

1. V Visual Basic v nabídce **soubor** přejděte na příkaz **Nový** a potom klikněte na **projekt**.

1. V dialogovém okně **Nový projekt** v podokně **typy projektů** se ujistěte, že je vybrána možnost **Windows** . V podokně **šablony** vyberte **Knihovna tříd** . Do pole **název** zadejte `StreamReaderEnumerable`a pak klikněte na **OK**. Zobrazí se nový projekt.

1. V **Průzkumník řešení**klikněte pravým tlačítkem na soubor Class1. vb a klikněte na **Přejmenovat**. Přejmenujte soubor na `StreamReaderEnumerable.vb` a stiskněte klávesu ENTER. Přejmenováním souboru dojde také k přejmenování třídy na `StreamReaderEnumerable`. Tato třída bude implementovat rozhraní `IEnumerable(Of String)`.

1. Klikněte pravým tlačítkem na projekt StreamReaderEnumerable, přejděte na **Přidat**a klikněte na **Nová položka**. Vyberte šablonu **třídy** . Do pole **název** zadejte `StreamReaderEnumerator.vb` a klikněte na **OK**.

 První třída v tomto projektu je vyčíslitelné třída a implementuje rozhraní `IEnumerable(Of String)`. Toto obecné rozhraní implementuje rozhraní <xref:System.Collections.IEnumerable> a zaručuje, že příjemci této třídy mohou přistupovat k hodnotám, které jsou zadány jako `String`.  
  
**Přidejte kód pro implementaci rozhraní IEnumerable**

1. Otevřete soubor StreamReaderEnumerable. vb.

2. Na řádku po `Public Class StreamReaderEnumerable`zadejte následující příkaz a stiskněte klávesu ENTER.

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   Visual Basic automaticky naplní třídu členy, které jsou vyžadovány rozhraním `IEnumerable(Of String)`.
  
3. Tato Výčtová třída načte řádky z textového souboru po jednom řádku. Přidejte následující kód do třídy k vystavení veřejného konstruktoru, který jako vstupní parametr převezme cestu k souboru.

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. Vaše implementace metody <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> rozhraní `IEnumerable(Of String)` vrátí novou instanci třídy `StreamReaderEnumerator`. Implementaci metody `GetEnumerator` rozhraní `IEnumerable` lze vytvořit `Private`, protože je nutné vystavit pouze členy `IEnumerable(Of String)` rozhraní. Nahraďte kód, který Visual Basic generovaný pro `GetEnumerator` metody, pomocí následujícího kódu.

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
**Přidání kódu pro implementaci rozhraní IEnumerator**

1. Otevřete soubor StreamReaderEnumerator. vb.

2. Na řádku po `Public Class StreamReaderEnumerator`zadejte následující příkaz a stiskněte klávesu ENTER.

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   Visual Basic automaticky naplní třídu členy, které jsou vyžadovány rozhraním `IEnumerator(Of String)`.

3. Třída enumerator otevře textový soubor a provede vstupně-výstupní operace souboru pro čtení řádků ze souboru. Přidejte následující kód do třídy k vystavení veřejného konstruktoru, který jako vstupní parametr převezme cestu k souboru, a otevřete textový soubor pro čtení.

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. Vlastnosti `Current` pro rozhraní `IEnumerator(Of String)` a `IEnumerator` vrátí aktuální položku z textového souboru jako `String`. Implementaci vlastnosti `Current` rozhraní `IEnumerator` lze vytvořit `Private`, protože je nutné vystavit pouze členy `IEnumerator(Of String)` rozhraní. Nahraďte kód, který Visual Basic generovaný pro `Current` vlastností, pomocí následujícího kódu.

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. Metoda `MoveNext` rozhraní `IEnumerator` naviguje na další položku v textovém souboru a aktualizuje hodnotu vrácenou vlastností `Current`. Pokud nejsou k dispozici žádné další položky ke čtení, metoda `MoveNext` vrátí `False`; v opačném případě metoda `MoveNext` vrátí `True`. Do metody `MoveNext` přidejte následující kód.

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. Metoda `Reset` rozhraní `IEnumerator` přesměruje iterátor, aby odkazoval na začátek textového souboru a vymaže hodnotu aktuální položky. Do metody `Reset` přidejte následující kód.

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. Metoda `Dispose` rozhraní `IEnumerator` garantuje, že všechny nespravované prostředky byly vydány před zničením iterátoru. Popisovač souboru, který je používán objektem `StreamReader`, je nespravovaný prostředek a je třeba jej zavřít před zničením instance iterátoru. Nahraďte kód, který Visual Basic generovaný pro metodu `Dispose`, pomocí následujícího kódu.

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)] 
  
## <a name="using-the-sample-iterator"></a>Použití ukázkového iterátoru

 Můžete použít vyčíslitelné třídy v kódu společně s řídicími strukturami, které vyžadují objekt, který implementuje `IEnumerable`, jako je například smyčka `For Next` nebo dotaz LINQ. Následující příklad ukazuje `StreamReaderEnumerable` v dotazu LINQ.  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a>Viz také:

- [Úvod do jazyka LINQ v Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Tok řízení](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Struktury smyčky](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Příkaz For Each...Next](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
