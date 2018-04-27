---
title: Implementace IEnumerable v jazyce Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4645153f9c830bc96b7ec55367f46f09098eb78d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>Návod: Implementace IEnumerable(Of T) v jazyce Visual Basic
<xref:System.Collections.Generic.IEnumerable%601> Rozhraní je implementováno modulem třídy, které můžete při návratu posloupnost hodnoty jednu položku. Výhodou vrací data, která je jednu položku najednou, není nutné načíst kompletní sadu dat do paměti pro práci s ním. Potřebujete dostatek paměti pro načtení jednu položku z dat použijte. Třídy implementující `IEnumerable(T)` rozhraní lze použít s `For Each` smyčky nebo dotazů LINQ.  
  
 Představte si třeba aplikaci, která musí čtení velké textového souboru a vrátí každý řádek ze souboru, který odpovídá konkrétní vyhledávací kritéria. Aplikace používá k vrácení řádky ze souboru, které odpovídají zadaným kritériím dotazu LINQ. K dotazu na obsah souboru pomocí dotazu LINQ, může aplikace načíst obsah souboru do pole nebo kolekce. Načítání celého souboru do pole nebo kolekce by využívat podstatně více paměti, než je vyžadováno. Dotaz LINQ místo dotazovat obsah souboru s použitím vyčíslitelná třídy, vrací pouze hodnoty, které by odpovídaly kritériím hledání. Dotazy, které vracejí pouze několik odpovídající hodnoty by využívat mnohem méně paměti.  
  
 Můžete vytvořit třídu, která implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní k zobrazení zdroje dat jako vyčíslitelná data. Vaše třídu, která implementuje `IEnumerable(T)` rozhraní bude vyžadovat jiné třídy, která implementuje <xref:System.Collections.Generic.IEnumerator%601> rozhraní k iteraci v rámci zdrojová data. Tyto dvě třídy umožňují postupně jako specifického typu vrátit datové položky.  
  
 V tomto návodu vytvoříte třídu, která implementuje `IEnumerable(Of String)` rozhraní a třídy, která implementuje `IEnumerator(Of String)` rozhraní pro čtení textového souboru řádcích najednou.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>Vytváření vyčíslitelná – třída  
  
|Vytvoření projektu vyčíslitelná – třída|  
|---|  
|1.  V jazyce Visual Basic na **soubor** nabídky, přejděte na příkaz **nový** a pak klikněte na **projektu**.<br />2.  V **nový projekt** dialogovém **typy projektů** podokně, ujistěte se, že **Windows** je vybrána. Vyberte **knihovny tříd** v **šablony** podokně. V **název** zadejte `StreamReaderEnumerable`a potom klikněte na **OK**. Zobrazí se nový projekt.<br />3.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na soubor Class1.vb a klikněte na **přejmenovat**. Přejmenujte soubor `StreamReaderEnumerable.vb` a stiskněte klávesu ENTER. Přejmenování souboru také přejmenuje třídy pro `StreamReaderEnumerable`. Tato třída se implementovat `IEnumerable(Of String)` rozhraní.<br />4.  Klikněte pravým tlačítkem na projekt StreamReaderEnumerable, přejděte na **přidat**a potom klikněte na **novou položku**. Vyberte **třída** šablony. V **název** zadejte `StreamReaderEnumerator.vb` a klikněte na tlačítko **OK**.|  
  
 První třídy v tomto projektu je vyčíslitelná třída a implementovat `IEnumerable(Of String)` rozhraní. Tato obecná rozhraní implementuje <xref:System.Collections.IEnumerable> rozhraní a záruky, aby měli přístup k příjemce této třídy hodnoty zadané jako `String`.  
  
|Chcete-li přidat kód pro implementaci rozhraní IEnumerable|  
|---|  
|1.  Otevřete soubor StreamReaderEnumerable.vb.<br />2.  Na řádku po `Public Class StreamReaderEnumerable`, zadejte následující příkaz a stiskněte klávesu ENTER.<br />     [!code-vb[VbVbalrIteratorWalkthrough#1](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_1.vb)]<br />     Visual Basic automaticky naplní třídu se členy, které jsou vyžadované `IEnumerable(Of String)` rozhraní.<br />3.  Tato třída vyčíslitelná bude číst řádky z textu, řádek souboru najednou. Přidejte následující kód do třídy vystavit veřejný konstruktor, který přebírá cestu k souboru jako vstupní parametr.<br />     [!code-vb[VbVbalrIteratorWalkthrough#2](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_2.vb)]<br />4.  Vaši implementaci <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metodu `IEnumerable(Of String)` rozhraní vrátí novou instanci třídy `StreamReaderEnumerator` třídy. Implementace `GetEnumerator` metodu `IEnumerable` rozhraní můžete provést `Private`, protože je nutné vystavit pouze členové `IEnumerable(Of String)` rozhraní. Nahraďte kód jazyka Visual Basic vygenerované `GetEnumerator` metody s následujícím kódem.<br />     [!code-vb[VbVbalrIteratorWalkthrough#3](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_3.vb)]|  
  
|Chcete-li přidat kód pro implementaci IEnumerator|  
|---|  
|1.  Otevřete soubor StreamReaderEnumerator.vb.<br />2.  Na řádku po `Public Class StreamReaderEnumerator`, zadejte následující příkaz a stiskněte klávesu ENTER.<br />     [!code-vb[VbVbalrIteratorWalkthrough#4](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_4.vb)]<br />     Visual Basic automaticky naplní třídu se členy, které jsou vyžadované `IEnumerator(Of String)` rozhraní.<br />3.  Třída enumerátor otevře textový soubor a provede soubor vstupně-výstupních operací čtení řádky ze souboru. Přidejte následující kód do třídy vystavení veřejný konstruktor, který přebírá cestu k souboru jako vstupní parametr a otevřete textový soubor pro čtení.<br />     [!code-vb[VbVbalrIteratorWalkthrough#5](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_5.vb)]<br />4.  `Current` Vlastnosti pro oba `IEnumerator(Of String)` a `IEnumerator` rozhraní vrátí aktuální položky z textového souboru jako `String`. Implementace `Current` vlastnost `IEnumerator` rozhraní můžete provést `Private`, protože je nutné vystavit pouze členové `IEnumerator(Of String)` rozhraní. Nahraďte kód jazyka Visual Basic vygenerované `Current` vlastnosti následujícím kódem.<br />     [!code-vb[VbVbalrIteratorWalkthrough#6](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_6.vb)]<br />5.  `MoveNext` Metodu `IEnumerator` rozhraní přejde na další položku v textovém souboru a aktualizuje hodnotu, která je vrácený `Current` vlastnost. Pokud neexistují žádné další položky najdete `MoveNext` metoda vrátí `False`; v opačném případě `MoveNext` metoda vrátí `True`. Přidejte následující kód, který `MoveNext` metoda.<br />     [!code-vb[VbVbalrIteratorWalkthrough#7](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_7.vb)]<br />6.  `Reset` Metodu `IEnumerator` rozhraní přesměruje iterator tak, aby odkazoval na začátek textového souboru a vymaže aktuální hodnotu položky. Přidejte následující kód, který `Reset` metoda.<br />     [!code-vb[VbVbalrIteratorWalkthrough#8](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_8.vb)]<br />7.  `Dispose` Metodu `IEnumerator` rozhraní zaručuje, že všechny nespravované prostředky jsou uvolněny zničen iteraci. Popisovač souboru, který je používán `StreamReader` objekt nespravovaný prostředek a musí být uzavřeny zničen iterator instance. Nahraďte kód jazyka Visual Basic vygenerované `Dispose` metoda následujícím kódem.<br />     [!code-vb[VbVbalrIteratorWalkthrough#9](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_9.vb)]|  
  
## <a name="using-the-sample-iterator"></a>Pomocí iterátorů vzorku  
 Vyčíslitelná třídu můžete použít ve vašem kódu společně s řídicí struktury, které vyžadují objekt, který implementuje `IEnumerable`, například `For Next` smyčky nebo dotaz LINQ. Následující příklad ukazuje `StreamReaderEnumerable` v dotazu LINQ.  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_10.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Úvod do LINQ v jazyku Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Tok řízení](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Struktury smyčky](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Příkaz For Each...Next](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
