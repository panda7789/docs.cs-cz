---
title: Operace projekce (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b8d38e6d-21cf-4619-8dbb-94476f4badc7
ms.openlocfilehash: 4d92405d9f3da69df4fa3964468599d6549480cb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740957"
---
# <a name="projection-operations-visual-basic"></a>Operace projekce (Visual Basic)
Projekce odkazuje na operace transformace objektu na nový formulář, který často se skládá pouze z těchto vlastností, které se následně použijí. S použitím projekce, můžete vytvořit nový typ, který je sestaven z každého objektu. Můžete vlastnosti projektu a provádění matematických funkcí na něj. Můžete také promítnout na původní objekt bez provedení změn.  
  
 V následující části jsou uvedeny standardní metody operátoru dotazu, které provádějí projekce.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka Visual Basic|Další informace|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Vyberte|Projekty hodnoty, které jsou založeny na funkce transformace.|`Select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|SelectMany|Projekty pořadí hodnot, které jsou založeny na funkce transformace a sloučí je do jedné sekvence.|Použití více `From` klauzule|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Příklady syntaxe výrazů dotazů  
  
### <a name="select"></a>Vyberte  
 V následujícím příkladu `Select` klauzuli do projektu první písmeno každého řetězce v seznamu řetězců.  
  
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
  
### <a name="selectmany"></a>SelectMany  
 Následující příklad používá více `From` klauzule do projektu všechna slova ze každý řetězec v seznamu řetězců.  
  
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
  
## <a name="select-versus-selectmany"></a>Vyberte a operátor SelectMany  
 Práce z obou `Select()` a `SelectMany()` je výsledná hodnota (nebo hodnoty) ze zdrojové hodnoty. `Select()` vytvoří jednu výslednou hodnotu pro každou zdrojovou hodnotu. Celkový výsledek je proto kolekci, která má stejný počet prvků jako zdrojové kolekce. Naproti tomu `SelectMany()` jeden celkový výsledek, který obsahuje zřetězených podřízené kolekce od všech hodnot zdroje. Funkce transformace, která je předána jako argument `SelectMany()` musí vracet vyčíslitelné posloupnost hodnot pro každou zdrojovou hodnotu. Tyto vyčíslitelné sekvence jsou pak zřetězeny podle `SelectMany()` vytvořte jedno velké pořadí.  
  
 Následující dva obrázky ukazují konceptuální rozdíl mezi akcemi z těchto dvou metod. V obou případech se předpokládá, že funkce selektor (transformace) vybere z každé zdrojové hodnoty pole květin.  
  
 Tento obrázek znázorňuje, jak `Select()` vrátí kolekci, která má stejný počet prvků jako zdrojové kolekce.  
  
 ![Ilustrace akci vyberte&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")  
  
 Tento obrázek znázorňuje, jak `SelectMany()` zřetězí zprostředkující pořadí polí do jedné hodnoty konečný výsledek, který obsahuje každou hodnotu z každé zprostředkující pole.  
  
 ![Obrázek znázorňující akce operátor SelectMany&#40;&#41;. ](../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "Operátor SelectMany")  
  
### <a name="code-example"></a>Příklad kódu  
 Následující příklad porovnává chování `Select()` a `SelectMany()`. Kód vytvoří "kytice" květin díky první dvě položky z každého seznam názvů květinu ve zdrojové kolekce. V tomto příkladu "jedna hodnota", který funkce transformace <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> používá, je samotný kolekci hodnot. To vyžaduje, aby nadbytečné `For Each` smyčky, aby bylo možné vytvořit výčet každého řetězce v každé dílčí sekvenci.  
  
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
  
## <a name="see-also"></a>Viz také:
- <xref:System.Linq>
- [Přehled standardních operátorů dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Klauzule Select](../../../../visual-basic/language-reference/queries/select-clause.md)
- [Postupy: Kombinace dat s LINQ pomocí spojení](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)
- [Postupy: Vyplňování kolekcí objektů z více zdrojů (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
- [Postupy: Vrácení výsledku dotazu LINQ jako specifického typu](../../../../visual-basic/programming-guide/language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md)
- [Postupy: Rozdělení souboru na více souborů pomocí skupin (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
