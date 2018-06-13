---
title: Operace projekce (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b8d38e6d-21cf-4619-8dbb-94476f4badc7
ms.openlocfilehash: f4d1f7531ee69ebdbfb4ccd283f9f5dcb2f000af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647641"
---
# <a name="projection-operations-visual-basic"></a>Operace projekce (Visual Basic)
Projekce odkazuje na operaci transformace objekt do nový formulář, který často se skládá jenom z těchto vlastností, které budou následně použity. Pomocí projekce můžete vytvořit nový typ, který je sestaven z každého objektu. Můžete projektu vlastnosti a na něm provádět matematické funkce. Můžete také promítnout původní objekt bez provedení změn.  
  
 Metody operátor standardní dotaz, které provádějí projekce jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka Visual Basic|Další informace|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Vyberte|Projekty hodnoty, které jsou založeny na funkce transformace.|`Select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|Označit více|Projekty pořadí hodnot, které jsou založeny na funkce transformace a pak sloučí je do jedné sekvence.|Použití více `From` – klauzule|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Příklady syntaxe výrazu dotazu  
  
### <a name="select"></a>Vyberte  
 Následující příklad používá `Select` klauzule do projektu první písmeno z každé řetězec v seznamu řetězců.  
  
```vb  
Dim words = New List(Of String) From {"an", "apple", "a", "day"}  
  
Dim query = From word In words   
            Select word.Substring(0, 1)  
  
Dim sb As New System.Text.StringBuilder()  
For Each letter As String In query  
    sb.AppendLine(letter)  
Next  
  
' Display the output.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' a  
' a  
' a  
' d  
```  
  
### <a name="selectmany"></a>Označit více  
 Následující příklad používá více `From` klauzule do projektu jednotlivých slov z každé řetězec v seznamu řetězců.  
  
```vb  
Dim phrases = New List(Of String) From {"an apple a day", "the quick brown fox"}  
  
Dim query = From phrase In phrases   
            From word In phrase.Split(" "c)   
            Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In query  
    sb.AppendLine(str)  
Next  
  
' Display the output.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' an  
' apple  
' a  
' day  
' the  
' quick  
' brown  
' fox  
```  
  
## <a name="select-versus-selectmany"></a>Vyberte a označit více  
 Pracovní i `Select()` a `SelectMany()` z hodnot zdroj je vytvořit hodnotu výsledek (nebo hodnoty). `Select()` vytvoří jednu výslednou hodnotu pro každou zdrojovou hodnotu. Kolekce, která má stejný počet elementů jako zdrojové kolekci je proto celkový výsledek. Naproti tomu `SelectMany()` vytváří jeden celkový výsledek, který obsahuje zřetězených podřízených kolekcí z každé zdrojové hodnotě. Funkce transformace, který je předán jako argument pro `SelectMany()` musí vrátit vyčíslitelná pořadí hodnot pro každou hodnotu zdroje. Tyto vyčíslitelná pořadí jsou pak zřetězených podle `SelectMany()` vytvoření jeden velký pořadí.  
  
 Následující dva obrázky ukazují koncepční rozdíl mezi tyto dvě metody akce. V každém případě předpokládá, že funkce selektor (transformace) vybere pole květy z každé zdrojové hodnoty.  
  
 Tento obrázek znázorňuje způsob `Select()` vrátí kolekce, která má stejný počet elementů jako zdrojové kolekci.  
  
 ![Koncepční obrázek akce vyberte&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")  
  
 Tento obrázek znázorňuje způsob `SelectMany()` zřetězí zprostředkující pořadí polí do jednu hodnotu konečný výsledek, který obsahuje každou hodnotu z každé zprostředkující pole.  
  
 ![Obrázek znázorňující akce označit více&#40;&#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "Označit více")  
  
### <a name="code-example"></a>Příklad kódu  
 Následující příklad porovnává chování `Select()` a `SelectMany()`. Kód vytvoří "bouquet" květy provedením první dvě položky z každé seznam názvů květina ve zdrojové kolekci. V tomto příkladu "jedna hodnota", transformační funkce <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> používá, je sám kolekci hodnot. To vyžaduje nadbytečné `For Each` smyčky, aby bylo možné vytvořit výčet každý řetězec v každé dílčí pořadí.  
  
```vb  
Class Bouquet  
    Public Flowers As List(Of String)  
End Class  
  
Sub SelectVsSelectMany()  
    Dim bouquets = New List(Of Bouquet) From {   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"sunflower", "daisy", "daffodil", "larkspur"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"tulip", "rose", "orchid"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"gladiolis", "lily", "snapdragon", "aster", "protea"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"larkspur", "lilac", "iris", "dahlia"})}}  
  
    Dim output As New System.Text.StringBuilder  
  
    ' Select()  
    Dim query1 = bouquets.Select(Function(b) b.Flowers)  
  
    output.AppendLine("Using Select():")  
    For Each flowerList In query1  
        For Each str As String In flowerList  
            output.AppendLine(str)  
        Next  
    Next  
  
    ' SelectMany()  
    Dim query2 = bouquets.SelectMany(Function(b) b.Flowers)  
  
    output.AppendLine(vbCrLf & "Using SelectMany():")  
    For Each str As String In query2  
        output.AppendLine(str)  
    Next  
  
    ' Display the output  
    MsgBox(output.ToString())  
  
    ' This code produces the following output:  
    '  
    ' Using Select():  
    ' sunflower  
    ' daisy  
    ' daffodil  
    ' larkspur  
    ' tulip  
    ' rose  
    ' orchid  
    ' gladiolis  
    ' lily  
    ' snapdragon  
    ' aster  
    ' protea  
    ' larkspur  
    ' lilac  
    ' iris  
    ' dahlia  
  
    ' Using SelectMany()  
    ' sunflower  
    ' daisy  
    ' daffodil  
    ' larkspur  
    ' tulip  
    ' rose  
    ' orchid  
    ' gladiolis  
    ' lily  
    ' snapdragon  
    ' aster  
    ' protea  
    ' larkspur  
    ' lilac  
    ' iris  
    ' dahlia  
  
End Sub  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq>  
 [Přehled standardních operátorů dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Klauzule Select](../../../../visual-basic/language-reference/queries/select-clause.md)  
 [Postupy: kombinace dat s LINQ pomocí spojení](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)  
 [Postupy: vyplňování kolekcí objektů z více zdrojů (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)  
 [Postupy: Vrácení výsledku dotazu LINQ jako specifického typu](../../../../visual-basic/programming-guide/language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md)  
 [Postupy: rozdělení souboru na mnoho souborů pomocí skupin (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
