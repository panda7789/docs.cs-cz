---
title: Zápis dotazů v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
ms.openlocfilehash: 8e3d893a21b36868f59d132bd8ba9a6f634cac62
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296066"
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a>Návod: Zápis dotazů v jazyce Visual Basic
Tento návod ukazuje, jak můžete funkce jazyka Visual Basic pro zápis [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] výrazech dotazů. Návod ukazuje, jak vytvořit dotazy v seznamu objektů Student, jak spouštět dotazy a způsobech jejich změny. Dotazy obsahovat několik funkcí, včetně anonymních typů, inicializátory objektů a odvození místního typu.  
  
 Po dokončení tohoto návodu budete připraveni přejít ukázky a dokumentaci pro konkrétní [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zprostředkovatele, které vás zajímají. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] poskytovatelé zahrnují [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)], a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
## <a name="create-a-project"></a>Vytvoření projektu  
  
#### <a name="to-create-a-console-application-project"></a>Vytvoření projektu konzolové aplikace  
  
1. Spusťte Visual Studio.  
  
2. Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.  
  
3. V **nainstalované šablony** klikněte na možnost **jazyka Visual Basic**.  
  
4. V seznamu typů projektů klepněte **konzolovou aplikaci**. V **název** pole, zadejte název projektu a pak klikněte na tlačítko **OK**.  
  
     Projekt je vytvořen. Ve výchozím nastavení obsahuje odkaz na System.Core.dll. Navíc **importovat obory názvů** seznamu [odkazy na stránky, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) zahrnuje <xref:System.Linq?displayProperty=nameWithType> oboru názvů.  
  
5. Na [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), ujistěte se, že **Option infer** je nastavena na **na**.  
  
## <a name="add-an-in-memory-data-source"></a>Přidání zdroje dat v paměti  
 Zdroj dat pro dotazy v tomto návodu je seznam `Student` objekty. Každý `Student` objekt obsahuje křestní jméno, příjmení, rok třídy a akademické pořadí v těle studentů.  
  
#### <a name="to-add-the-data-source"></a>Přidání zdroje dat  
  
-   Definování `Student` třídy a vytvoří seznam instancí třídy.  
  
    > [!IMPORTANT]
    >  Kód potřebný k definování `Student` třídy a vytvořit seznam použitý v tomto návodu je součástí příklady [jak: Vytvoření seznamu položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md). Můžete zkopírovat z něj a vložte ho do projektu. Nový kód nahradí kódu, které se zobrazovalo při vytváření projektu.  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>Přidání nového studenta do seznamu studentů  
  
-   Podle tohoto vzoru vytvořené v `getStudents` způsob, jak přidat další instanci `Student` třídy do seznamu. Přidání studenta vás seznámí s inicializátory objektů. Další informace najdete v tématu [inicializátory objektů: Pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).  
  
## <a name="create-a-query"></a>Vytvořit dotaz  
 Při spuštění dotaz přidaný v této části vytváří seznam studentů, jehož academic pořadí umístí je do prvních deset. Vzhledem k tomu, že dotaz vybere kompletní `Student` objekt pokaždé, když, typ výsledku dotazu je `IEnumerable(Of Student)`. Nicméně dotazu obvykle není zadaný typ v definicích dotazů. Místo toho používá kompilátor odvození místního typu k určení typu. Další informace najdete v tématu [odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md). Proměnná rozsahu v dotazu, `currentStudent`, slouží jako odkaz na každé `Student` instance ve zdroji, `students`, díky přístupu k vlastnosti jednotlivých objektů v `students`.  
  
#### <a name="to-create-a-simple-query"></a>Vytvoření jednoduchého dotazu  
  
1. Najít na místo `Main` metoda projektu, který je označen následujícím způsobem:  
  
     [!code-vb[VbLINQWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#1)]  
  
     Zkopírujte následující kód a vložte ji.  
  
     [!code-vb[VbLINQWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#2)]  
  
2. Umístěte ukazatel myši nad `studentQuery` ve vašem kódu, chcete-li ověřit, jestli je typ přiřazené kompilátoru `IEnumerable(Of Student)`.  
  
## <a name="run-the-query"></a>Spuštění dotazu  
 Proměnná `studentQuery` obsahuje definici dotazu nejsou výsledky ze spuštěného dotazu. Je typické mechanismus pro spuštění dotazu `For Each` smyčky. Každý prvek ve vrácené posloupnosti je přístupné prostřednictvím proměnné iterace smyčky. Další informace o provádění dotazů, najdete v části [zápis svůj první dotaz LINQ](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
#### <a name="to-run-the-query"></a>Spuštění dotazu  
  
1. Přidejte následující `For Each` smyčky pod dotaz ve vašem projektu.  
  
     [!code-vb[VbLINQWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#3)]  
  
2. Umístěte ukazatel myši nad řídicí proměnná smyčky for `studentRecord` zobrazíte jeho datového typu. Typ `studentRecord` odvozena jako `Student`, protože `studentQuery` vrátí kolekci `Student` instancí.  
  
3. Sestavte a spusťte aplikaci stisknutím kombinace kláves CTRL + F5. Poznamenejte si výsledky v okně konzoly.  
  
## <a name="modify-the-query"></a>Úprava dotazu  
 Je snazší dotazu výsledky kontroly, když jsou v uvedeném pořadí. Můžete řadit podle všechna dostupná pole vrácené posloupnosti.  
  
#### <a name="to-order-the-results"></a>Řazení výsledků  
  
1. Přidejte následující `Order By` klauzule mezi `Where` příkazu a `Select` příkaz dotazu. `Order By` Klauzule bude řazení výsledků podle abecedy od A až Z, podle poslední název každého studenta.  
  
    ```  
    Order By currentStudent.Last Ascending   
    ```  
  
2. Chcete-li řadit podle příjmení a pak křestní jméno, přidáte do dotazu obě pole:  
  
    ```  
    Order By currentStudent.Last Ascending, currentStudent.First Ascending   
    ```  
  
     Můžete také určit `Descending` na pořadí od Z do A.  
  
3. Sestavte a spusťte aplikaci stisknutím kombinace kláves CTRL + F5. Poznamenejte si výsledky v okně konzoly.  
  
#### <a name="to-introduce-a-local-identifier"></a>Zavedení lokálního identifikátoru  
  
1. Přidejte kód v této části k zavedení lokálního identifikátoru ve výrazu dotazu. Identifikátor místní, bude obsahovat přechodný výsledek. V následujícím příkladu `name` je identifikátor, který obsahuje zřetězení student jméno a příjmení. Místní identifikátor lze použít ke zvýšení pohodlí, nebo ho můžete zvýšit výkon díky ukládání výsledků výrazu, který by jinak vypočítá více než jednou.  
  
     [!code-vb[VbLINQWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#4)]  
  
2. Sestavte a spusťte aplikaci stisknutím kombinace kláves CTRL + F5. Poznamenejte si výsledky v okně konzoly.  
  
#### <a name="to-project-one-field-in-the-select-clause"></a>Projekce jednoho pole v klauzuli Select  
  
1. Přidat dotaz a `For Each` smyčky v této části, chcete-li vytvořit dotaz, který vytvoří posloupnost, jehož prvky se liší od prvků ve zdroji. V následujícím příkladu, zdroj je kolekce `Student` objekty, ale pouze jednoho člena každý objekt je vrácen: křestní jméno, jejichž příjmení je Garcia studentů. Protože `currentStudent.First` není řetězcový datový typ vrácený pořadí `studentQuery3` je `IEnumerable(Of String)`, posloupnost řetězců. Jako v předchozích příkladech přiřazení datový typ pro `studentQuery3` zbývá kompilátor určit pomocí odvození místního typu.  
  
     [!code-vb[VbLINQWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#5)]  
  
2. Umístěte ukazatel myši nad `studentQuery3` ve vašem kódu, chcete-li ověřit, jestli je typ přiřazené `IEnumerable(Of String)`.  
  
3. Sestavte a spusťte aplikaci stisknutím kombinace kláves CTRL + F5. Poznamenejte si výsledky v okně konzoly.  
  
#### <a name="to-create-an-anonymous-type-in-the-select-clause"></a>Vytvoření anonymního typu v klauzuli Select  
  
1. Přidejte kód z tohoto oddílu zobrazíte jak anonymní typy se používají v dotazech. Můžete je používat v dotazech Pokud chcete vrátit několik polí ze zdroje dat místo úplné záznamy (`currentStudent` záznamy v předchozích příkladech) neboli jednotlivých polí (`First` v předchozí části). Místo definování nový typ s názvem, který obsahuje pole, které chcete zahrnout do výsledku, určíte pole, v `Select` klauzule a kompilátor vytvoří anonymního typu s těmito poli jako její vlastnosti. Další informace najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     Následující příklad vytvoří dotaz, který vrátí název a pořadí seniors jehož academic pořadí je mezi 1 a 10 v akademické pořadí. V tomto příkladu typu `studentQuery4` musí být odvozen, protože `Select` klauzule vrátí instanci anonymního typu a nemá žádný použitelný název anonymního typu.  
  
     [!code-vb[VbLINQWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#6)]  
  
2. Sestavte a spusťte aplikaci stisknutím kombinace kláves CTRL + F5. Poznamenejte si výsledky v okně konzoly.  
  
## <a name="additional-examples"></a>Další příklady  
 Teď, když jste se seznámili se základy, tady je seznam Další příklady ilustrují flexibilitu a výkon [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy. Každý příklad předchází stručný popis toho, co dělá. Umístěte ukazatel myši nad proměnnou výsledek dotazu pro každý dotaz zobrazíte odvozený typ. Použití `For Each` smyčky výsledky.  
  
 [!code-vb[VbLINQWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#7)]  
  
## <a name="additional-information"></a>Další informace  
 Jakmile se seznámíte se základními koncepcemi práce s dotazy, budete chtít přečíst dokumentaci a ukázky pro konkrétní typ [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zprostředkovatele, které vás zajímají:  
  
 [LINQ to Objects](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
## <a name="see-also"></a>Viz také:

- [Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [Začínáme s dotazy LINQ v jazyce Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Inicializátory objektů: Pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Úvod do LINQ v JAZYKU Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Dotazy](../../../../visual-basic/language-reference/queries/index.md)
