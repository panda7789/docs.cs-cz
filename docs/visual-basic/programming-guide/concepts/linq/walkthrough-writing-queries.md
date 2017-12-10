---
title: "Zápis dotazů v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
caps.latest.revision: "70"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d30ad7f0db2760427493610c630f3fff8dcfac31
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a>Návod: Zápis dotazů ve Visual Basic
Tento návod ukazuje, jak můžete použít funkce jazyka Visual Basic pro zápis [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] dotaz výrazy. Návod ukazuje, jak vytvářet dotazy na seznam objektů studenty, jak spouštět dotazy a postup je upravit. Dotazy obsahovat několik funkcí, včetně inicializátory objektů, odvození místního typu a anonymní typy.  
  
 Po dokončení tohoto průvodce, nebudete připravení přejít na ukázky a dokumentace pro konkrétní [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zprostředkovatele, které vás zajímají. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]Zprostředkovatelé zahrnují [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)], a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
## <a name="create-a-project"></a>Vytvoření projektu  
  
#### <a name="to-create-a-console-application-project"></a>Vytvoření projektu konzolové aplikace  
  
1.  Spuštění sady Visual Studio.  
  
2.  Na **soubor** nabídky, přejděte na příkaz **nový**a potom klikněte na **projektu**.  
  
3.  V **nainstalovaných šablonách** seznamu, klikněte na tlačítko **jazyka Visual Basic**.  
  
4.  V seznamu typů projektu, klikněte na **konzolové aplikace**. V **název** pole, zadejte název projektu a pak klikněte na tlačítko **OK**.  
  
     Projekt je vytvořen. Ve výchozím nastavení obsahuje odkaz na System.Core.dll. Navíc **importovat obory názvů** seznam na [stránka odkazy, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) zahrnuje <xref:System.Linq?displayProperty=nameWithType> oboru názvů.  
  
5.  Na [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), ujistěte se, že **Option infer –** je nastaven na **na**.  
  
## <a name="add-an-in-memory-data-source"></a>Přidání zdroje dat v paměti  
 Zdroj dat pro dotazy v tomto návodu je seznam `Student` objekty. Každý `Student` objekt obsahuje křestní jméno, příjmení, třída roku a academic pořadí v těle student.  
  
#### <a name="to-add-the-data-source"></a>Přidání zdroje dat  
  
-   Definování `Student` třídy a vytvoří seznam instancí třídy.  
  
    > [!IMPORTANT]
    >  Kód potřebné k definování `Student` třídy a vytvoření seznamu použít v tomto návodu je součástí příklady [postupy: vytvoření seznamu položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md). Můžete zkopírovat z ní a vložte ho do projektu. Nový kód nahradí kód, který se zobrazily při vytváření projektu.  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>Přidání nového studenta do seznamu studentů  
  
-   Postupujte podle vzoru v `getStudents` metody přidat další instanci `Student` třídy do seznamu. Přidání student vás seznámí s inicializátory objektů. Další informace najdete v tématu [inicializátory objektů: pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).  
  
## <a name="create-a-query"></a>Vytvoření dotazu  
 Po provedení dotazu přidat v této části vytvoří seznam studenty, jehož academic pořadí umístí je do prvních deset. Vzhledem k tomu, že dotaz vybere kompletní `Student` objekt pokaždé, když, typ výsledku dotazu je `IEnumerable(Of Student)`. Ale dotazu obvykle není zadaný typ v definicích dotazů. Místo toho kompilátor používá k určení typu odvození místního typu. Další informace najdete v tématu [odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md). Proměnná rozsahu dotazu, `currentStudent`, slouží jako odkaz na každou `Student` instance ve zdroji, `students`, poskytování přístupu k vlastnosti každého objektu v `students`.  
  
#### <a name="to-create-a-simple-query"></a>Vytvoření jednoduchého dotazu  
  
1.  Najít na místo, `Main` metoda projekt, který je označen následujícím způsobem:  
  
     [!code-vb[VbLINQWalkthrough#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_1.vb)]  
  
     Zkopírujte následující kód a vložte jej do.  
  
     [!code-vb[VbLINQWalkthrough#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_2.vb)]  
  
2.  Umístěte ukazatel myši nad `studentQuery` ve vašem kódu k ověření, že typ přiřazené kompilátoru je `IEnumerable(Of Student)`.  
  
## <a name="run-the-query"></a>Spuštění dotazu  
 Proměnná `studentQuery` obsahuje definici dotazu, není výsledky spuštění dotazu. Je typické mechanismus pro spuštění dotazu `For Each` smyčky. Každý prvek v pořadí vrácených přistupuje prostřednictvím proměnné iterace smyčky. Další informace o provádění dotazů najdete v tématu [zápis vaše první dotaz LINQ](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
#### <a name="to-run-the-query"></a>Spuštění dotazu  
  
1.  Přidejte následující `For Each` smyčky níže dotazu ve vašem projektu.  
  
     [!code-vb[VbLINQWalkthrough#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_3.vb)]  
  
2.  Umístěte ukazatel myši nad řídicí proměnná smyčky `studentRecord` zobrazíte jeho datového typu. Typ `studentRecord` je odvodit být `Student`, protože `studentQuery` vrátí kolekci `Student` instance.  
  
3.  Sestavte a spusťte aplikaci stisknutím kombinace kláves CTRL + F5. Poznamenejte si výsledky v okně konzoly.  
  
## <a name="modify-the-query"></a>Úprava dotazu  
 Je snazší Kontrola výsledků dotazu, pokud jsou v zadaném pořadí. Můžete řadit vrácený pořadí podle každé pole, k dispozici.  
  
#### <a name="to-order-the-results"></a>Řazení výsledků  
  
1.  Přidejte následující `Order By` klauzule mezi `Where` příkaz a `Select` příkaz dotazu. `Order By` Klauzule bude řazení výsledků abecedně z A až Z, podle poslední název každé student.  
  
    ```  
    Order By currentStudent.Last Ascending   
    ```  
  
2.  Chcete-li řadit podle příjmení a potom křestní jméno, chcete do dotazu přidáte obě pole:  
  
    ```  
    Order By currentStudent.Last Ascending, currentStudent.First Ascending   
    ```  
  
     Můžete také zadat `Descending` k seřazení od Z do A.  
  
3.  Sestavte a spusťte aplikaci stisknutím kombinace kláves CTRL + F5. Poznamenejte si výsledky v okně konzoly.  
  
#### <a name="to-introduce-a-local-identifier"></a>Zavedení lokálního identifikátoru  
  
1.  Přidejte kód v této části zavádět místní identifikátor ve výrazu dotazu. Identifikátor místní bude obsahovat mezilehlých výsledků. V následujícím příkladu `name` je identifikátor, který obsahuje zřetězení student první a příjmení. Identifikátor místní lze použít ke zvýšení pohodlí, nebo ji můžete zvýšit výkon uložením výsledky výraz, který by jinak vypočítat vícekrát.  
  
     [!code-vb[VbLINQWalkthrough#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_4.vb)]  
  
2.  Sestavte a spusťte aplikaci stisknutím kombinace kláves CTRL + F5. Poznamenejte si výsledky v okně konzoly.  
  
#### <a name="to-project-one-field-in-the-select-clause"></a>Projekce jednoho pole v klauzuli Select  
  
1.  Přidání dotazu a `For Each` smyčky z této části můžete vytvořit dotaz, který produkuje pořadí, jehož elementy se liší od elementů ve zdrojovém. V následujícím příkladu, zdroj je kolekce `Student` objekty, ale pouze jednoho člena každého objektu se vrátí: křestní jméno studenty, jejichž příjmení je Garcia. Protože `currentStudent.First` je řetězec, datový typ vrácený pořadí `studentQuery3` je `IEnumerable(Of String)`, posloupnosti řetězců. Jako v předchozích příkladech přiřazení datový typ pro `studentQuery3` je ponechán pro kompilátor určit pomocí odvození místního typu.  
  
     [!code-vb[VbLINQWalkthrough#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_5.vb)]  
  
2.  Umístěte ukazatel myši nad `studentQuery3` ve vašem kódu k ověření, že přiřazené typ je `IEnumerable(Of String)`.  
  
3.  Sestavte a spusťte aplikaci stisknutím kombinace kláves CTRL + F5. Poznamenejte si výsledky v okně konzoly.  
  
#### <a name="to-create-an-anonymous-type-in-the-select-clause"></a>Vytvoření anonymního typu v klauzuli Select  
  
1.  Přidejte kód z této části najdete v části Jak anonymní typy se používají v dotazech. Je používat v dotazech. Pokud chcete vrátit několik polí ze zdroje dat místo kompletní záznamy (`currentStudent` záznamy v předchozích příkladech) nebo jedna pole (`First` v předchozí části). Místo definice nový typ s názvem, který obsahuje pole, které chcete zahrnout do výsledku, zadejte na pole v `Select` klauzule a kompilátor vytvoří anonymní typ s těmito poli jako jeho vlastnosti. Další informace najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     Následující příklad vytvoří dotaz, který vrátí název a pořadí seniors jehož academic pořadí je mezi 1 a 10 v academic pořadí. V tomto příkladu typ `studentQuery4` musí odvodit, protože `Select` klauzule vrací instanci anonymního typu a anonymní typ nemá žádný použitelný název.  
  
     [!code-vb[VbLINQWalkthrough#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_6.vb)]  
  
2.  Sestavte a spusťte aplikaci stisknutím kombinace kláves CTRL + F5. Poznamenejte si výsledky v okně konzoly.  
  
## <a name="additional-examples"></a>Další příklady  
 Teď, když porozumíte základům, tady je seznam Další příklady pro ilustraci flexibilitu a výkonu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy. Každý příklad předchází stručný popis co dělá. Umístěte ukazatel myši nad proměnnou výsledek dotazu pro každý dotaz na najdete v odvozeném typu. Použití `For Each` opakování ve smyčce bude mít výsledky.  
  
 [!code-vb[VbLINQWalkthrough#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_7.vb)]  
  
## <a name="additional-information"></a>Další informace  
 Jakmile se seznámíte se základními koncepcemi pracovat s dotazy, jste připravení číst dokumentace a ukázky pro konkrétní typ [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zprostředkovatele, které vás zajímají:  
  
 [LINQ na objekty](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9)  
  
 [Technologie LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
  
 [Technologie LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)  
  
 [LINQ na DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
## <a name="see-also"></a>Viz také  
 [Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 [Začínáme s dotazy LINQ v jazyku Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Inicializátory objektů: Pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Úvod do LINQ v jazyku Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Dotazy](../../../../visual-basic/language-reference/queries/queries.md)
