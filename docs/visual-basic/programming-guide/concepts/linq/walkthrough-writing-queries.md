---
title: Zápis dotazů v Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
ms.openlocfilehash: 256075ad5de5b88595dd4be7f199a74b5912c082
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046551"
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a>Návod: Zápis dotazů v Visual Basic

Tento návod ukazuje, jak lze pomocí funkcí jazyka Visual Basic zapsat [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] výrazy dotazu. Návod ukazuje, jak vytvořit dotazy na seznam objektů studenta, jak spustit dotazy a jak je upravit. Dotazy obsahují několik funkcí, včetně inicializátorů objektů, místního typu odvození a anonymních typů.

Po dokončení tohoto Názorného postupu budete připraveni přejít k ukázkám a dokumentaci pro konkrétního [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] poskytovatele, kterého vás zajímá. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]poskytovatelé [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]zahrnují, LINQ to DataSet a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].

## <a name="create-a-project"></a>Vytvořit projekt

### <a name="to-create-a-console-application-project"></a>Vytvoření projektu konzolové aplikace

1. Spusťte Visual Studio.

2. V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.

3. V seznamu **Nainstalované šablony** klikněte na **Visual Basic**.

4. V seznamu typů projektů klikněte na konzolová **aplikace**. Do pole **název** zadejte název projektu a klikněte na tlačítko **OK**.

    Vytvoří se projekt. Ve výchozím nastavení obsahuje odkaz na System. Core. dll. Také seznam **importovaných oborů názvů** na [stránce s odkazy, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) obsahuje <xref:System.Linq?displayProperty=nameWithType> obor názvů.

5. Na [stránce kompilovat Návrháře projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)zajistěte, aby byla **možnost** odvoditelné na hodnotu **zapnuto**.

## <a name="add-an-in-memory-data-source"></a>Přidání zdroje dat v paměti

Zdroj dat pro dotazy v tomto návodu je seznam `Student` objektů. Každý `Student` objekt obsahuje křestní jméno, příjmení, rok třídy a akademickou hodnost v těle studenta.

### <a name="to-add-the-data-source"></a>Přidání zdroje dat

- `Student` Definujte třídu a vytvořte seznam instancí třídy.

  > [!IMPORTANT]
  > Kód potřebný k definování `Student` třídy a vytvoření seznamu, který se používá v příkladech návodu, je uveden v [tématu How to: Vytvoří seznam položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md). Můžete z něj zkopírovat a vložit ho do projektu. Nový kód nahradí kód, který se zobrazil při vytváření projektu.

### <a name="to-add-a-new-student-to-the-students-list"></a>Přidání nového studenta do seznamu studentů

- Postupujte podle vzoru v `getStudents` metodě pro přidání další instance `Student` třídy do seznamu. Přidáním studenta se seznámíte s Inicializátory objektů. Další informace najdete v tématu [Inicializátory objektů: Pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).

## <a name="create-a-query"></a>Vytvoření dotazu

Po spuštění se dotaz přidaný v této části vytvoří seznam studentů, jejichž školní řazení je v prvních deseti. Vzhledem k tomu, že dotaz `Student` vybírá úplný objekt pokaždé, typ výsledku dotazu je `IEnumerable(Of Student)`. Nicméně typ dotazu obvykle není zadán v definicích dotazů. Místo toho kompilátor používá odvození místního typu k určení typu. Další informace naleznete v tématu [odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md). Proměnná `currentStudent`rozsahu dotazu slouží jako odkaz na každou `Student` `students`instanci ve zdroji, a poskytuje přístup k vlastnostem každého objektu v `students`.

### <a name="to-create-a-simple-query"></a>Vytvoření jednoduchého dotazu

1. Vyhledejte místo v `Main` metodě projektu, který je označen následujícím způsobem:

    [!code-vb[VbLINQWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#1)]

    Zkopírujte následující kód a vložte ho do.

    [!code-vb[VbLINQWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#2)]

2. Umístěte ukazatel myši nad `studentQuery` v kódu a ověřte, zda je `IEnumerable(Of Student)`typ přiřazený kompilátorem.

## <a name="run-the-query"></a>Spuštění dotazu

Proměnná `studentQuery` obsahuje definici dotazu, nikoli výsledky spuštění dotazu. Typickým mechanismem pro spuštění dotazu je `For Each` smyčka. Každý prvek v vrácené sekvenci je k dispozici prostřednictvím proměnné iterace smyčky. Další informace o provádění dotazů naleznete v tématu [zápis prvního dotazu LINQ](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).

### <a name="to-run-the-query"></a>Spuštění dotazu

1. Přidejte následující `For Each` smyčku pod dotaz v projektu.

    [!code-vb[VbLINQWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#3)]

2. Umístěte ukazatel myši na proměnnou `studentRecord` ovládacího prvku smyčky, aby se zobrazil jeho datový typ. Typ `studentRecord` je odvozený `Student` `studentQuery` ,`Student` protože vrací kolekci instancí.

3. Sestavte a spusťte aplikaci stisknutím kombinace kláves CTRL + F5. Všimněte si výsledků v okně konzoly.

## <a name="modify-the-query"></a>Úprava dotazu

Vyhledávání výsledků dotazu je snazší, pokud jsou v zadaném pořadí. Vrácenou sekvenci můžete seřadit na základě libovolného dostupného pole.

### <a name="to-order-the-results"></a>Řazení výsledků

1. Přidejte následující `Order By` klauzuli `Where` mezi příkaz a `Select` příkaz dotazu. `Order By` Klauzule seřadí výsledky abecedně od a do Z v závislosti na posledním jménu každého studenta.

    ```
    Order By currentStudent.Last Ascending
    ```

2. Chcete-li seřadit podle příjmení a pak jako křestní jméno, přidejte do dotazu obě pole:

    ```
    Order By currentStudent.Last Ascending, currentStudent.First Ascending
    ```

    Můžete také určit `Descending` , že se má seřadit z z do a.

3. Sestavte a spusťte aplikaci stisknutím kombinace kláves CTRL + F5. Všimněte si výsledků v okně konzoly.

### <a name="to-introduce-a-local-identifier"></a>Zavedení lokálního identifikátoru

1. Přidejte kód v této části, chcete-li do výrazu dotazu zavést místní identifikátor. Místní identifikátor bude obsahovat mezilehlé výsledky. V následujícím příkladu `name` je identifikátor, který obsahuje zřetězení křestní jméno a příjmení studenta. Místní identifikátor lze použít pro pohodlí nebo může zvýšit výkon tím, že ukládá výsledky výrazu, který by jinak vypočítal vícekrát.

    [!code-vb[VbLINQWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#4)]

2. Sestavte a spusťte aplikaci stisknutím kombinace kláves CTRL + F5. Všimněte si výsledků v okně konzoly.

### <a name="to-project-one-field-in-the-select-clause"></a>Projekce jednoho pole v klauzuli Select

1. Přidejte dotaz a `For Each` smyčku z této části, chcete-li vytvořit dotaz, který vytvoří sekvenci, jejíž prvky se liší od prvků ve zdroji. V následujícím příkladu je zdrojem kolekce `Student` objektů, ale je vrácen pouze jeden člen každého objektu: křestní jméno studentů, jejichž příjmení je Garcia. Vzhledem `currentStudent.First` k tomu, že je řetězec, datový typ sekvence, kterou `studentQuery3` vrátí `IEnumerable(Of String)`, je sekvence řetězců. Jak je uvedeno v předchozích příkladech, přiřazení datového typu pro `studentQuery3` je ponecháno pro kompilátor pro určení pomocí odvození místního typu.

    [!code-vb[VbLINQWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#5)]

2. Umístěte ukazatel myši nad `studentQuery3` v kódu a ověřte, zda je `IEnumerable(Of String)`přiřazený typ.

3. Sestavte a spusťte aplikaci stisknutím kombinace kláves CTRL + F5. Všimněte si výsledků v okně konzoly.

### <a name="to-create-an-anonymous-type-in-the-select-clause"></a>Vytvoření anonymního typu v klauzuli Select

1. Přidejte kód z této části, abyste viděli, jak se v dotazech používají anonymní typy. Je možné je použít v dotazech, pokud chcete vrátit několik polí ze zdroje dat namísto úplných záznamů (`currentStudent` záznamy v předchozích příkladech) nebo v jednom`First` poli (v předchozí části). Namísto definování nového pojmenovaného typu, který obsahuje pole, která chcete zahrnout do výsledku, zadáte pole v `Select` klauzuli a kompilátor vytvoří anonymní typ s těmito poli jako jeho vlastnosti. Další informace najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).

    Následující příklad vytvoří dotaz, který vrátí název a pořadí vyšších, jejichž školní řazení je v pořadí podle akademického řádu v rozmezí od 1 do 10. V tomto příkladu `studentQuery4` musí být typ odvozen, `Select` protože klauzule vrací instanci anonymního typu a anonymní typ nemá použitelný název.

    [!code-vb[VbLINQWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#6)]

2. Sestavte a spusťte aplikaci stisknutím kombinace kláves CTRL + F5. Všimněte si výsledků v okně konzoly.

## <a name="additional-examples"></a>Další příklady

Teď, když rozumíte základům, následuje seznam dalších příkladů, které znázorňují flexibilitu a sílu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazů. Každý příklad předchází stručný popis toho, co dělá. Umístěte ukazatel myši na výslednou proměnnou dotazu pro každý dotaz, aby se zobrazil odvozený typ. K vytvoření výsledků použijte smyčku.`For Each`

[!code-vb[VbLINQWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#7)]

## <a name="additional-information"></a>Další informace

Jakmile se seznámíte se základními koncepty práce s dotazy, můžete si přečíst dokumentaci a ukázky pro konkrétní typ [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] poskytovatele, kterého vás zajímá:

- [LINQ to Objects](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)

- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)

- [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)

- [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)

## <a name="see-also"></a>Viz také:

- [LINQ (Language-Integrated Query) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [Začínáme pomocí LINQ v Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Inicializátory objektů: Pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Úvod do jazyka LINQ v Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Dotazy](../../../../visual-basic/language-reference/queries/index.md)
