---
title: Implementace iEnumerable
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: 4151a680050f234d450d8de5e67a767c54e8df68
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266908"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>Návod: Implementace IEnumerable(Of T) v jazyce Visual Basic
Rozhraní <xref:System.Collections.Generic.IEnumerable%601> je implementováno třídami, které mohou vracet posloupnost hodnot po jedné položce. Výhodou vrácení dat po jedné položce je, že není nutné načítat úplnou sadu dat do paměti, abyste s ní mohli pracovat. Stačí použít dostatek paměti k načtení jedné položky z dat. Třídy, `IEnumerable(T)` které implementují `For Each` rozhraní lze použít s smyčky nebo LINQ dotazy.  
  
 Zvažte například aplikaci, která musí číst velký textový soubor a vrátit každý řádek ze souboru, který odpovídá konkrétním kritériím hledání. Aplikace používá dotaz LINQ k vrácení řádků ze souboru, které odpovídají zadaným kritériím. Chcete-li dotaz na obsah souboru pomocí dotazu LINQ, aplikace může načíst obsah souboru do pole nebo kolekce. Načítání celého souboru do pole nebo kolekce by však spotřebovávat mnohem více paměti, než je požadováno. Dotaz LINQ by mohl místo toho dotaz ovat obsah souboru pomocí enumerovatelné třídy a vrátit pouze hodnoty, které odpovídají kritériím hledání. Dotazy, které vrátí pouze několik odpovídajících hodnot, by spotřebovávaly mnohem méně paměti.  
  
 Můžete vytvořit třídu, která <xref:System.Collections.Generic.IEnumerable%601> implementuje rozhraní vystavit zdrojová data jako výčet dat. Vaše třída, která `IEnumerable(T)` implementuje rozhraní bude <xref:System.Collections.Generic.IEnumerator%601> vyžadovat jinou třídu, která implementuje rozhraní iterát prostřednictvím zdrojových dat. Tyto dvě třídy umožňují vrátit položky dat postupně jako určitý typ.  
  
 V tomto návodu vytvoříte třídu, `IEnumerable(Of String)` která implementuje rozhraní `IEnumerator(Of String)` a třídu, která implementuje rozhraní pro čtení textového souboru po jednom řádku.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>Vytvoření třídy výčtu  
  
**Vytvoření projektu výčtu třídy**

1. V jazyce Visual Basic v nabídce **Soubor** přejděte na **Nový** a potom klepněte na **položku Project**.

1. V dialogovém okně **Nový projekt** zkontrolujte v podokně **Typy projektů,** zda je vybrán **systém Windows.** V podokně **Šablony** vyberte **Knihovna tříd.** Do pole **Název** `StreamReaderEnumerable`zadejte a klepněte na tlačítko **OK**. Zobrazí se nový projekt.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na soubor Class1.vb a klepněte na příkaz **Přejmenovat**. Přejmenujte soubor `StreamReaderEnumerable.vb` na klávesu ENTER a stiskněte klávesu ENTER. Přejmenování souboru bude také přejmenovat třídu na `StreamReaderEnumerable`. Tato třída bude `IEnumerable(Of String)` implementovat rozhraní.

1. Klepněte pravým tlačítkem myši na projekt StreamReaderEnumerable, přejděte na **Přidat**a potom klepněte na příkaz **Nová položka**. Vyberte šablonu **třídy.** Do pole **Název** `StreamReaderEnumerator.vb` zadejte a klepněte na **tlačítko OK**.

 První třída v tomto projektu je výčet třídy a bude implementovat `IEnumerable(Of String)` rozhraní. Toto obecné rozhraní <xref:System.Collections.IEnumerable> implementuje rozhraní a zaručuje, že spotřebitelé `String`této třídy mohou přistupovat k hodnotám zadaným jako .  
  
**Přidejte kód k implementaci iEnumerable**

1. Otevřete soubor StreamReaderEnumerable.vb.

2. Na řádku `Public Class StreamReaderEnumerable`za , zadejte následující a stiskněte klávesu ENTER.

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   Visual Basic automaticky naplní třídu členy, `IEnumerable(Of String)` které jsou vyžadovány rozhraním.
  
3. Tato třída s početitelnými bude číst řádky z textového souboru po jednom řádku. Přidejte následující kód do třídy vystavit veřejný konstruktor, který bere cestu k souboru jako vstupní parametr.

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. Implementace <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metody `IEnumerable(Of String)` rozhraní vrátí novou instanci třídy. `StreamReaderEnumerator` Implementace `GetEnumerator` metody `IEnumerable` rozhraní může být provedena `Private`, protože je třeba vystavit `IEnumerable(Of String)` pouze členy rozhraní. Nahraďte kód, který jazyk `GetEnumerator` Visual Basic vygeneroval pro metody následujícím kódem.

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
**Přidejte kód k implementaci nástroje IEnumerator**

1. Otevřete soubor StreamReaderEnumerator.vb.

2. Na řádku `Public Class StreamReaderEnumerator`za , zadejte následující a stiskněte klávesu ENTER.

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   Visual Basic automaticky naplní třídu členy, `IEnumerator(Of String)` které jsou vyžadovány rozhraním.

3. Třída čítače otevře textový soubor a provede vstupně-va souboru pro čtení řádků ze souboru. Přidejte následující kód do třídy vystavit veřejný konstruktor, který trvá cestu k souboru jako vstupní parametr a otevřete textový soubor pro čtení.

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. Vlastnosti `Current` rozhraní `IEnumerator(Of String)` a `IEnumerator` rozhraní vrátí aktuální položku z `String`textového souboru jako . Implementace `Current` vlastnostrozhraní `IEnumerator` lze provést `Private`, protože je třeba vystavit pouze `IEnumerator(Of String)` členy rozhraní. Nahraďte kód, který jazyk `Current` Visual Basic vygeneroval pro vlastnosti následujícím kódem.

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. Metoda `MoveNext` `IEnumerator` rozhraní přejde na další položku v textovém souboru a `Current` aktualizuje hodnotu, která je vrácena vlastností. Pokud nejsou žádné další položky `MoveNext` ke `False`čtení, metoda vrátí ; jinak `MoveNext` metoda `True`vrátí . Do metody `MoveNext` přidejte následující kód.

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. Metoda `Reset` `IEnumerator` rozhraní přesměruje iterátor tak, aby ukazoval na začátek textového souboru a vymaže aktuální hodnotu položky. Do metody `Reset` přidejte následující kód.

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. Metoda `Dispose` `IEnumerator` rozhraní zaručuje, že všechny nespravované prostředky jsou uvolněny před zničením iterátoru. Popisovač souboru, který `StreamReader` je používán objektem je nespravovaný prostředek a musí být uzavřen před zničením instance iterátoru. Nahraďte kód, který pro `Dispose` metodu vygeneroval jazyk Visual Basic, následujícím kódem.

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)]
  
## <a name="using-the-sample-iterator"></a>Použití ukázkového iterátoru

 Můžete použít znakovou třídu v kódu spolu s řídicí struktury, `IEnumerable`které vyžadují `For Next` objekt, který implementuje , jako je například smyčka nebo linq dotaz. Následující příklad ukazuje `StreamReaderEnumerable` v linq dotazu.  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a>Viz také

- [Představení technologie LINQ v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Tok řízení](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Struktury smyčky](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Příkaz For Each...Next](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
