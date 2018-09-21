---
title: Implementace IEnumerable v jazyce Visual Basic
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: be2eefdc52d38df3071d457b7a71dbac6eaa2657
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46490501"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>Návod: Implementace IEnumerable(Of T) v jazyce Visual Basic
<xref:System.Collections.Generic.IEnumerable%601> Rozhraní je implementováno třídy, které může vrátit posloupnost hodnot položek najednou. Výhodou vracející data, která je jedna položka v čase, že nemáte k načtení úplná sada dat do paměti pro práci s ní. Stačí načtení jednu položku z dat pomocí dostatek paměti. Třídy, které implementují `IEnumerable(T)` rozhraní jde použít s `For Each` smyčky nebo dotazů LINQ.  
  
 Zvažte například aplikaci, která musí číst velkého textového souboru a vracet každý řádek ze souboru, který by odpovídal kritériím hledání konkrétní. Aplikace používá k vrácení řádky ze souboru, které odpovídají zadaným kritériím dotazu LINQ. K dotazu na obsah souboru pomocí dotazu LINQ, může aplikace načítat obsah souboru do pole nebo kolekce. Načítání celého souboru do pole nebo kolekce by využívat mnohem větší paměť, než je povinný. Dotaz LINQ může místo toho dotazu na obsah souboru pomocí vyčíslitelné třídy, vrací pouze hodnoty, které odpovídají kritériím hledání. Dotazy, které vracejí jen několik porovnání hodnot by využívat mnohem méně paměti.  
  
 Můžete vytvořit třídu, která implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní ke zveřejňování zdroje dat jako vyčíslitelné data. Vaše třída, která implementuje `IEnumerable(T)` rozhraní se vyžaduje jinou třídu, která implementuje <xref:System.Collections.Generic.IEnumerator%601> rozhraní k iteraci v rámci zdrojová data. Tyto dvě třídy umožňují snadno vrátit položky dat postupně jako specifického typu.  
  
 V tomto návodu vytvoříte třídu, která implementuje `IEnumerable(Of String)` rozhraní a třídy, která implementuje `IEnumerator(Of String)` rozhraní ke čtení souboru jeden řádek textu v čase.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>Vytvoření výčtu třídy  
  
**Vytvořte projekt vyčíslitelné tříd**

1.  V jazyce Visual Basic na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.

1.  V **nový projekt** v dialogu **typy projektů** podokno, ujistěte se, že **Windows** zaškrtnuto. Vyberte **knihovny tříd** v **šablony** podokně. V **název** zadejte `StreamReaderEnumerable`a potom klikněte na tlačítko **OK**. Zobrazí se nový projekt.

1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na soubor Class1.vb a klikněte na tlačítko **přejmenovat**. Přejmenujte soubor na `StreamReaderEnumerable.vb` a stiskněte klávesu ENTER. Přejmenování souboru se také přejmenujte třídu na `StreamReaderEnumerable`. Tato třída implementuje `IEnumerable(Of String)` rozhraní.

1.  Klikněte pravým tlačítkem na projekt StreamReaderEnumerable, přejděte na **přidat**a potom klikněte na tlačítko **nová položka**. Vyberte **třídy** šablony. V **název** zadejte `StreamReaderEnumerator.vb` a klikněte na tlačítko **OK**.

 První třídy v tomto projektu je vyčíslitelná třídy a implementuje `IEnumerable(Of String)` rozhraní. Tato obecná rozhraní implementuje <xref:System.Collections.IEnumerable> rozhraní a zaručuje, že příjemci této třídy můžete přístup k hodnoty zadané jako `String`.  
  
**Přidejte kód k implementaci IEnumerable**

1. Otevřete soubor StreamReaderEnumerable.vb.

2. Na řádku po `Public Class StreamReaderEnumerable`, zadejte následující příkaz a stiskněte klávesu ENTER.

   [!code-vb[VbVbalrIteratorWalkthrough#1](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_1.vb)]

   Visual Basic automaticky naplní třídu s členy, které jsou vyžadované `IEnumerable(Of String)` rozhraní.
  
3. Tato třída vyčíslitelné bude číst řádky z jeden řádek textu souboru najednou. Přidejte následující kód do třídy vystavit veřejný konstruktor, který přijímá jako vstupní parametr cestu k souboru.

   [!code-vb[VbVbalrIteratorWalkthrough#2](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_2.vb)]

4. Implementace <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metodu `IEnumerable(Of String)` rozhraní vrátí novou instanci třídy `StreamReaderEnumerator` třídy. Provádění `GetEnumerator` metodu `IEnumerable` rozhraní nelze realizovat `Private`, protože je nutné vystavit pouze členové `IEnumerable(Of String)` rozhraní. Nahraďte kód generovaný pro Visual Basic `GetEnumerator` metody s následujícím kódem.

   [!code-vb[VbVbalrIteratorWalkthrough#3](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_3.vb)]  
  
**Přidejte kód, který implementují IEnumerator**

1. Otevřete soubor StreamReaderEnumerator.vb.

2. Na řádku po `Public Class StreamReaderEnumerator`, zadejte následující příkaz a stiskněte klávesu ENTER.

   [!code-vb[VbVbalrIteratorWalkthrough#4](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_4.vb)]

   Visual Basic automaticky naplní třídu s členy, které jsou vyžadované `IEnumerator(Of String)` rozhraní.

3. Třída výčtu otevře textový soubor a provádí souboru vstupně-výstupních operací čtení řádků ze souboru. Přidejte následující kód do třídy vystavit veřejný konstruktor, který přijímá jako vstupní parametr cestu k souboru a otevřete textový soubor pro čtení.

   [!code-vb[VbVbalrIteratorWalkthrough#5](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_5.vb)]

4. `Current` Vlastnosti pro obě `IEnumerator(Of String)` a `IEnumerator` rozhraní vrátit aktuální položky z textového souboru jako `String`. Provádění `Current` vlastnost `IEnumerator` rozhraní nelze realizovat `Private`, protože je nutné vystavit pouze členové `IEnumerator(Of String)` rozhraní. Nahraďte kód generovaný pro Visual Basic `Current` vlastnosti s následujícím kódem.

   [!code-vb[VbVbalrIteratorWalkthrough#6](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_6.vb)]

5. `MoveNext` Metodu `IEnumerator` rozhraní přejde na další položku v textovém souboru a aktualizuje hodnotu, která je vrácena `Current` vlastnost. Pokud neexistují žádné další položky ke čtení, `MoveNext` vrátí metoda `False`; jinak vrátí hodnotu `MoveNext` vrátí metoda `True`. Přidejte následující kód, který `MoveNext` metody.

   [!code-vb[VbVbalrIteratorWalkthrough#7](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_7.vb)]

6. `Reset` Metodu `IEnumerator` rozhraní přesměruje iterátor, který má odkazovat na začátku textový soubor a vymaže aktuální hodnotu položky. Přidejte následující kód, který `Reset` metody.

   [!code-vb[VbVbalrIteratorWalkthrough#8](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_8.vb)]

7. `Dispose` Metodu `IEnumerator` rozhraní zaručuje, že jsou všechny nespravované prostředky uvolněny zničen iterátor. Popisovač souboru, který je používán `StreamReader` objektu je nespravovaný prostředek a musí být uzavřen zničen instance iterátoru. Nahraďte kód generovaný pro Visual Basic `Dispose` metodu s následujícím kódem.

   [!code-vb[VbVbalrIteratorWalkthrough#9](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_9.vb)] 
  
## <a name="using-the-sample-iterator"></a>Pomocí iterátoru vzorku

 Vyčíslitelná třídu lze použít ve vašem kódu společně s řídicí struktury, které vyžadují objekt, který implementuje `IEnumerable`, například `For Next` smyčky nebo dotazu LINQ. Následující příklad ukazuje `StreamReaderEnumerable` v dotazu LINQ.  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_10.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Úvod do LINQ v JAZYKU Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Tok řízení](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Struktury smyčky](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Příkaz For Each...Next](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
