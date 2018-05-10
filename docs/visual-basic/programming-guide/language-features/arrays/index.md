---
title: Pole v jazyce Visual Basic
ms.date: 12/06/2017
f1_keywords:
- vb.Array
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b6c1db0131f2a150dc1b00dd5e6dafc3a418f05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="arrays-in-visual-basic"></a>Pole v jazyce Visual Basic
Pole je sada hodnot, které jsou označovány jako *elementy*, které logicky se vztahují k sobě navzájem. Například může obsahovat pole počet studentů v každé úrovni ve škole gramatika; Každý element pole je počet studentů v jedné úrovni. Podobně pole může obsahovat Studentova tříd pro třídu; Každý element pole je jedné úrovni.    

Je možné jednotlivé proměnné, které chcete uložit všechny naše datové položky. Například pokud aplikace analyzuje známek studentů, jsme můžete používat samostatná proměnná pro každý Studentova úrovni, jako třeba `englishGrade1`, `englishGrade2`atd. Tento přístup má tři hlavní omezení:
- Máme vědět v době návrhu přesně kolik známek máme pro zpracování.
- Zpracování velkého počtu tříd rychle stane nepraktické. Díky tomu pak mnohem pravděpodobnější závažné chyby aplikace.
- Je obtížné. Každé nové třídy, které přidáme vyžaduje, že aplikace se změnil, překompilovat a znovu nasazena.  
 
 Pomocí pole můžete odkazovat na tyto hodnoty související se stejným názvem a použití čísla, která je volána *index* nebo *dolní index* k identifikaci jednotlivých element na pozici v poli základě. Indexy pole rozsahu od 0 do jedné menší než celkový počet prvků v poli. Při definování velikost pole pomocí syntaxe jazyka Visual Basic, zadejte jeho nejvyšší index, nebyl celkový počet prvků v poli. Můžete pracovat s polem jako jednotku, a možnost k iteraci v jeho elementy není znáte přesně kolik elementy obsahuje v době návrhu.
  
 Rychlé příklady před vysvětlení:  
  
```vb  
' Declare a single-dimension array of 5 numbers.  
Dim numbers(4) As Integer   
  
'Declare a single-dimension array and set its 4 values.  
Dim numbers = New Integer() {1, 2, 4, 8}  
  
' Change the size of an existing array to 16 elements and retain the current values.
ReDim Preserve numbers(15)
  
' Redefine the size of an existing array and reset the values.
ReDim numbers(15)  
  
' Declare a 6 x 6 multidimensional array.
Dim matrix(5, 5) As Double  
  
' Declare a 4 x 3 multidimensional array and set array element values.  
Dim matrix = New Integer(3, 2) {{1, 2, 3}, {2, 3, 4}, {3, 4, 5}, {4, 5, 6}}  
  
' Declare a jagged array  
Dim sales()() As Double = New Double(11)() {}  
```  
  
 ## <a name="in-this-article"></a>V tomto článku
  
- [Elementy pole v jednoduchých polí](#array-elements-in-a-simple-array)  
  
- [Vytváření pole](#creating-an-array)  
  
- [Ukládání hodnot v matici](#storing-values-in-an-array)  
  
- [Vyplní pole s literály pole](#populating-an-array-with-array-literals)  
  
- [Iterace v rámci pole](#iterating-through-an-array)  
  
- [Velikost pole](#BKMK_ArraySize)  

- [Typ pole](#the-array-type)  
  
- [Pole jako parametry a návratové hodnoty](#arrays-as-return-values-and-parameters)  
- [Vícenásobná pole](#jagged-arrays)  
  
- [Pole s nulovou délkou](#zero-length-arrays)  

- [Rozdělení pole](#splitting-an-array)
  
- [Kolekce jako alternativu k polím](#collections-as-an-alternative-to-arrays)  
  
##  <a name="array-elements-in-a-simple-array"></a>Elementy pole v jednoduchých polí  

Umožňuje vytvořit pole s názvem `students` k uložení počet studentů v každé úrovni ve škole gramatika. Indexy elementů rozsahu od 0 do 6. Pomocí tohoto pole je jednodušší než deklarování sedm proměnných.

Následující obrázek ukazuje `students` pole. Pro každý element pole:  
  
-   Index elementu představuje úrovni (index 0 představuje mateřské školy).
  
-   Hodnota, která je obsažena v elementu představuje počet studentů v této úrovni.
  
 ![Obrázek znázorňující počet studentů pole](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexampleschool.gif "ArrayExampleSchool")  
Prvky pole "studenty"  
 
Následující příklad obsahuje kód jazyka Visual Basic, které vytváří a používá pole:

 [!code-vb[simple-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/simple-array.vb)]  

V příkladu provádí tři věci:

- Deklaruje `students` pole sedm prvků. Číslo `6` v poli deklarace vyplývá poslední index v poli, že je menší než počet elementů v poli.
- Přiřadí hodnoty do každý prvek v poli. Elementy pole přistupují pomocí názvu pole a včetně index jednotlivý prvek v závorkách.
- Zobrazí se seznam každou hodnotu pole. V příkladu se používá [ `For` ](../../../language-reference/statements/for-next-statement.md) příkaz, který má přístup každý elementu pole pomocí čísla indexu.
  
 `students` Pole v předchozím příkladu je jednorozměrné pole, protože používá jeden index. Pole, které používá více než jeden index nebo dolní index nazývá *multidimenzionální*. Další informace najdete v tématu zbývající části tohoto článku a [rozměry pole v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
##  <a name="creating-an-array"></a>Vytváření pole  
 
Velikost pole můžete definovat několika způsoby: 

- Můžete zadat velikost, když je deklarovaná pole:
  
    [!code-vb[creating1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#1)]  
  
 - Můžete použít `New` klauzule zadat velikost pole, když je vytvořeno:  
  
    [!code-vb[creating2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#2)]  
  
 Pokud máte existující pole, můžete změnit její velikost pomocí [ `Redim` ](../../../../visual-basic/language-reference/statements/redim-statement.md) příkaz. Můžete určit, že `Redim` příkaz zachovat hodnoty, které jsou v poli, nebo můžete zadat, že ho vytvořit prázdné pole. Následující příklad ukazuje použití různých `Redim` příkaz mohli provádět úpravu velikosti pole existujících.  
  
 [!code-vb[redimensioning](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#3)]  
  
 Další informace najdete v tématu [ReDim – příkaz](../../../../visual-basic/language-reference/statements/redim-statement.md).  
  
##  <a name="storing-values-in-an-array"></a>Ukládání hodnot v matici
 
 Mají přístup ke každé umístění v matici pomocí indexu typu `Integer`. Můžete ukládat a načíst hodnoty v pole pod položkou každé pole umístění pomocí jeho index uzavřený v závorkách. Indexů pro vícerozměrná pole se oddělují čárkami (,). Pro každé pole dimenze potřebovat jeden index. 

Následující příklad ukazuje některé příkazy, které ukládají a načítají hodnoty v polích.
  
 [!code-vb[store-and-retrieve](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/store-and-retrieve.vb)]  
  
## <a name="populating-an-array-with-array-literals"></a>Vyplní pole s literály pole
 Pomocí pole literálu může vyplnit pole s počáteční sadu hodnot v době, kdy musíte ji vytvořit. Literál pole sestává ze seznamu hodnot oddělených čárkami, které jsou uzavřené do složených závorek (`{}`).  
  
 Když vytvoříte pole pomocí pole literálu, můžete zadat typ pole nebo použít odvození typu určit typ pole. Následující příklad ukazuje obě možnosti.  
  
 [!code-vb[create-with-literals](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#4)]  
  
 Pokud používáte odvození typu, je dáno typ pole *dominantní typ* v seznamu hodnot literálu. Dominantní typ je typ, do kterého můžete rozšířit všechny ostatní typy v poli. Pokud tento typ jedinečného nelze určit, dominantní typ je typ jedinečného, do kterého můžete zúžit všechny ostatní typy v poli. Pokud žádná z těchto jedinečný se dá určit, že dominantní typ je `Object`. Například, pokud je seznam hodnot, do pole literál poskytnutý obsahuje hodnoty typu `Integer`, `Long`, a `Double`, výsledné pole je typu `Double`. Protože `Integer` a `Long` rozšířit pouze `Double`, `Double` dominantní typu. Další informace najdete v tématu [Widening a zužující převody](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). 
 
> [!NOTE] 
> Odvození typu můžete použít pouze pro pole, které jsou definovány jako místní proměnné v člena typu. Chybí-li definici explicitní typu, pole definované s literály pole na úrovni třídy jsou typu `Object[]`. Další informace najdete v tématu [odvození místního typu](../variables/local-type-inference.md). 

Všimněte si, že předchozí příklad definuje `values` jako pole typu `Double` to i v případě, že jsou všechna pole literály typu `Integer`. Toto pole můžete vytvořit, protože hodnoty v poli literálu můžete rozšířit do `Double` hodnoty. 
  
 Můžete také vytvořit a naplnit multidimenzionálního pole pomocí *vnořená pole literály*. Literály vnořená pole musí mít číslo dimenzí, které je v souladu s výsledné pole. Následující příklad vytvoří dvourozměrná pole celých čísel pomocí literály vnořená pole.  
  
 [!code-vb[nested-array-literals](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#5)]  
  
Pokud používáte literály vnořená pole vytvořit a naplnit pole, dojde k chybě, pokud počet elementů v literálech vnořená pole se neshodují. Pokud je explicitně deklarovat proměnnou pole do mají jiný počet dimenzí než literály pole také dojde k chybě. 
  
Stejně jako lze pro jednorozměrné pole, můžete spolehnout na odvození typu při vytváření multidimenzionálního pole s literály vnořená pole. Odvozené typ je typ dominantní pro všechny hodnoty ve všech literály pole pro všechny úroveň vnoření. Následující příklad vytvoří dvourozměrná pole typu `Double[,]` z hodnoty, které jsou typu `Integer` a `Double`.  
  
 [!code-vb[nested-type-inference](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#6)]  
  
 Další příklady najdete v tématu [postupy: Inicializace proměnné pole v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md).  
  
##  <a name="iterating-through-an-array"></a>Iterace v rámci pole  
 Když jste iteraci v rámci pole, je přístup každý prvek v poli od nejnižší indexu na ty nejvyšší, nebo od nejvyšší nejnižší. Obvykle používají použijte buď [pro... Další příkaz](../../../../visual-basic/language-reference/statements/for-next-statement.md) nebo [pro každou... Další příkaz](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) k iteraci v rámci prvků pole. Pokud si nejste jisti horní hranice pole, můžete volat <xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType> metodu k získání nejvyšší hodnoty indexu. I když nejnižší hodnotu indexu je téměř vždy 0, můžete zavolat <xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType> metodu k získání nejnižší hodnoty indexu.   
  
 V následujícím příkladu prochází jednorozměrné pole s použitím [ `For...Next` ](../../../../visual-basic/language-reference/statements/for-next-statement.md) příkaz. 
  
 [!code-vb[iterate-one-dimensional-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate1d.vb)]  
  
 V následujícím příkladu prochází multidimenzionálního pole pomocí [ `For...Next` ](../../../../visual-basic/language-reference/statements/for-next-statement.md) příkaz. <xref:System.Array.GetUpperBound%2A> Metoda má parametr, který určuje dimenzi. `GetUpperBound(0)` Vrátí nejvyšší index první dimenze a `GetUpperBound(1)` vrátí nejvyšší index druhý dimenze.
  
 [!code-vb[iterate-two-dimensional-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate2d.vb)]  
  
 Následující příklad používá [For Each... Další příkaz](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)k iteraci v rámci jednorozměrné pole a dvourozměrná pole.  
  
 [!code-vb[iterate-for-each-next](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate-for-each-next.vb)]  
  
## <a name="array-size"></a>Velikost pole  

 Velikost pole je produkt délek všechny jeho dimenze. Představuje celkový počet elementů aktuálně obsažených v poli.  Například v následujícím příkladu deklaruje 2 dimenzí pole se čtyřmi prvky v Každá dimenze. Jak ukazuje výstup z příkladu, velikost tohoto pole je 16 (nebo (3 + 1) * (3 + 1).

 [!code-vb[array-size](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size.vb)]  

> [!NOTE] 
> Tato diskuse o velikosti pole se nevztahuje na Vícenásobná pole. Informace o Vícenásobná pole a určení velikosti Vícenásobná pole, najdete v článku [Vícenásobná pole](#jagged-arrays) části.
  
  Velikost pole můžete najít pomocí <xref:System.Array.Length%2A?displayProperty=nameWithType> vlastnost. Délka Každá dimenze multidimenzionálního pole můžete najít pomocí <xref:System.Array.GetLength%2A?displayProperty=nameWithType> metoda.  
  
 Velikost proměnné pole můžete změnit přiřazením nový objekt pole k němu nebo pomocí [ `ReDim` příkaz](../../../../visual-basic/language-reference/statements/redim-statement.md) příkaz. Následující příklad používá `ReDim` příkaz Změnit 100 element pole k poli 51 elementu.

 [!code-vb[resize-an-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size2.vb)]  
  
 Je třeba vzít v úvahu při plánování práce s velikost pole několik věcí.  
  
|||  
|---|---|  
|Délka dimenze|Index Každá dimenze je založené na 0, což znamená, že se pohybuje od 0 do jeho horní mez. Délka dané dimenze je proto jeden znak větší než deklarované horní hranice této dimenze.|  
|Omezení délky|Délka všech dimenzí pole je omezená na maximální hodnota, která `Integer` datového typu, který je <xref:System.Int32.MaxValue?displayProperty=nameWithType> nebo (2 ^ 31) - 1. Ale celková velikost pole je také omezena paměti k dispozici v systému. Pokud pokus o inicializaci pole, který překračuje množství dostupné paměti, modul runtime vyvolá <xref:System.OutOfMemoryException>.|  
|Velikost a velikost – Element|Velikost tohoto pole je nezávislé na datový typ jejích elementů. Velikost vždy představuje celkový počet elementů, nikoli počet bajtů, které budou využívat v paměti.|  
|Paměťové nároky|Není bezpečné, aby všechny předpoklady týkající se uložení pole v paměti. Úložiště se liší na platformy různých datových šířek, takže stejného pole můžete spotřebuje další paměť na 64bitovém systému než v 32bitové verzi systému. V závislosti na konfiguraci systému při inicializaci pole, modul CLR (CLR) můžete přiřadit úložiště jako zavřete společně, nejdříve pack elementy nebo přizpůsobit je všechny na hranicích přirozené hardwaru. Také pole úložiště režie vyžaduje pro své informace o řízení a režijní náklady na tato hodnota se zvyšuje s každá přidané dimenze.|  

## <a name="the-array-type"></a>Typ pole 
 Každé pole má datový typ, který se liší od datového typu jejích elementů. Neexistuje žádný single – datový typ pro všechna pole. Místo toho je datový typ pole určuje počet dimenzí, nebo *pořadí*, pole a datový typ elementů v poli. Dvě proměnné pole jsou stejných dat, zadejte pouze, pokud mají stejné pořadí a jejich prvky mít stejný datový typ. Rozměry pole délek neovlivňují datový typ pole.  
  
 Každé pole dědí z <xref:System.Array?displayProperty=nameWithType> třídy a můžou deklarovat proměnnou být typu `Array`, ale nelze vytvořit pole typu `Array`. Například i když následující kód deklaruje `arr` proměnná být typu `Array` a volání <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metoda pro vytvoření instance pole, pole typu prokáže, že se objekt [].

 [!code-vb[array-class](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-class.vb)] 

Navíc [ReDim – příkaz](../../../../visual-basic/language-reference/statements/redim-statement.md) nemůže pracovat na proměnnou deklarován jako typ `Array`. Z těchto důvodů a pro bezpečnost typů je třeba deklarovat každé pole jako specifického typu.  
  
 Můžete zjistit datový typ pole nebo jeho prvky několika způsoby. 
  
-   Můžete volat <xref:System.Object.GetType%2A> metoda na proměnnou, a získat <xref:System.Type> objekt, který představuje typ spuštění proměnné. <xref:System.Type> Objektu obsahuje velké množství informací v její vlastnosti a metody.  
  
-   Můžete předat proměnnou <xref:Microsoft.VisualBasic.Information.TypeName%2A> funkce pro zjištění `String` s názvem typu v době spuštění.  
  
 V následujícím příkladu volání obou `GetType` metoda a `TypeName` funkce určit typ pole. Typ pole je `Byte(,)`. Všimněte si, že <xref:System.Type.BaseType%2A?displayProperty=nameWithType> vlastnost také označuje, že je základní typ pole bajtů <xref:System.Array> třídy.  
  
 [!code-vb[array-type](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-type.vb)]  
  
##  <a name="arrays-as-return-values-and-parameters"></a>Pole jako parametry a návratové hodnoty  
 Pro vrácení pole z `Function` postupu zadejte pole datový typ a počet dimenzí jako návratový typ [funkce příkaz](../../../../visual-basic/language-reference/statements/function-statement.md). V rámci funkce deklarujte proměnnou místní pole stejným datový typ a počet dimenzí. V [příkaz Return](../../../../visual-basic/language-reference/statements/return-statement.md), zahrnout proměnnou místní pole bez závorek.  
  
 Chcete určit pole jako parametr, který se `Sub` nebo `Function` postupu, definujte parametr jako pole s zadaný datový typ a počet dimenzí. Ve volání postup předejte proměnné pole s stejný datový typ a počet dimenzí.  
  
 V následujícím příkladu `GetNumbers` funkce vrátí `Integer()`, jednorozměrné pole typu `Integer`. `ShowNumbers` Přijímá postup `Integer()` argument. 
  
 [!code-vb[return-value-and-params](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params.vb)]  
  
 V následujícím příkladu `GetNumbersMultiDim` funkce vrátí `Integer(,)`, dvourozměrná pole typu `Integer`.  `ShowNumbersMultiDim` Přijímá postup `Integer(,)` argument.  
  
 [!code-vb[multidimensional-return-value](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params-2d.vb)]  
  
## <a name="jagged-arrays"></a>Vícenásobná pole  
 
Struktura dat v aplikaci je někdy dvourozměrná, ale není obdélníkový. Pole může například použít k ukládání dat o vysoké teplota každý den v měsíci. První dimenze pole představuje v měsíci, ale druhá dimenze představuje počet dní, a počet dní v měsíci není uniform. A *Vícenásobná pole*, což se označuje taky jako *pole polí*, je určen pro takové scénáře. Vícenásobná pole je pole, jehož elementy jsou také pole. Vícenásobná pole a každý prvek v Vícenásobná pole může mít jeden nebo více dimenzí.  
  
 Následující příklad používá pole měsíců, je každý element pole dní. Tento příklad používá Vícenásobná pole, protože jiný měsíce mají různý počet dnů.  Tento příklad ukazuje, jak vytvořit Vícenásobná pole, přiřadit hodnoty a načíst a zobrazit jeho hodnoty.
  
 [!code-vb[jagged-arrays](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged.vb)]  

Předchozí příklad přiřazuje hodnoty Vícenásobná pole na základě elementu pomocí elementu pomocí `For...Next` smyčky. Můžete také přiřadit hodnoty prvky Vícenásobná pole pomocí literály vnořená pole. Ale vnořené pokusu o použití pole literály (například ```Dim valuesjagged = {{1, 2}, {2, 3, 4}}```) vygeneruje Chyba kompilátoru [BC30568](../../../,,/../misc/bc30568.md). Opravte chybu, uzavřete literály vnitřní pole v závorkách. Vynutit závorek literálu výraz pole k vyhodnocení a výsledné hodnoty se používají s poli vnější literálu, jak ukazuje následující příklad.  
  
 [!code-vb[jagged-array-initialization](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-assign.vb)] 

Vícenásobná pole je jednorozměrné pole, jehož elementy obsahovat pole. Proto <xref:System.Array.Length%2A?displayProperty=nameWithType> vlastnost a `Array.GetLength(0)` metoda vrátí počet prvků v jednorozměrné pole, a `Array.GetLength(1)` vyvolá <xref:System.IndexOutOfRangeException> protože Vícenásobná pole není multidimenzionální. Určit počet elementů v každé subarray načtením hodnoty jednotlivých subarray <xref:System.Array.Length%2A?displayProperty=nameWithType> vlastnost. Následující příklad ukazuje, jak můžete určit počet elementů v Vícenásobná pole.

[!code-vb[jagged-array-size](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-length.vb)] 

## <a name="zero-length-arrays"></a>Pole s nulovou délkou  
Visual Basic rozlišuje Neinicializovaný pole (pole, jehož hodnota je `Nothing`) a *nulová délka pole* nebo prázdné pole (pole, které nemá žádné elementy.) Neinicializovaný pole je ten, který nebyl byla dimenzovány nebo k němu přidělili žádné hodnoty. Příklad:

```vb
Dim arr() As String
```
Pole nulovou délkou je deklarovaný s dimenzí-1. Příklad:

```vb
Dim arrZ(-1) As String
```
Můžete potřebovat pro vytvoření nulová délka pole v následujících případech:  
  
-   Bez rizika <xref:System.NullReferenceException> výjimky, kódu musí přístup ke členům v <xref:System.Array> třídy, jako například <xref:System.Array.Length%2A> nebo <xref:System.Array.Rank%2A>, nebo volejte funkci jazyka Visual Basic, jako <xref:Microsoft.VisualBasic.Information.UBound%2A>.  
  
-   Chcete zachovat kódu jednoduchý, protože není nutné kontrolovat `Nothing` zvláštním způsobem.  
  
-   Váš kód komunikuje s programovací rozhraní aplikace (API), který vyžaduje, abyste předat nulová délka pole jednoho nebo více procedur nebo vrátí pole nulovou délkou z jednoho nebo více procedur.

## <a name="splitting-an-array"></a>Rozdělení pole

V některých případech můžete rozdělit do jednoho pole na více polí. To zahrnuje identifikace bodů nebo bodů, na kterých je možné rozdělit pole a pak plivání pole do dvou nebo více samostatných pole. 

> [!NOTE] 
> Tato část nezaměřuje rozdělení jednoho řetězce na pole na základě některé oddělovače. Informace o rozdělení řetězec, najdete v článku <xref:System.String.Split%2A?displayProperty=nameWithType> metoda.

Nejběžnější kritéria pro rozdělení pole jsou:

- Počet prvků v poli. Můžete například chtít rozdělit pole více než zadaný počet elementů na číslo přibližně stejné části. Pro tento účel můžete použít hodnoty vrácené buď <xref:System.Array.Length%2A?displayProperty=nameWithType> nebo <xref:System.Array.GetLength%2A?displayProperty=nameWithType> metoda.

- Hodnota elementu, který slouží jako oddělovač, který označuje, kde by měl rozdělit pole. Můžete vyhledat konkrétní hodnotu voláním <xref:System.Array.FindIndex%2A?displayProperty=nameWithType> a <xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType> metody.
 
Jakmile jste zjistili, index nebo indexy, na kterých je rozdělit pole, potom můžete vytvořit jednotlivé pole voláním <xref:System.Array.Copy%2A?displayProperty=nameWithType> metoda. 

Následující příklad rozdělí na dvě pole přibližně stejné velikosti pole. (Pokud je celkový počet elementů pole liché, první pole má jeden prvek více než druhá.) 

[!code-vb[splitting-an-array-by-length](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/split1.vb)] 

Následující příklad rozdělí na dvě pole na základě přítomnosti elementu, jehož hodnota je "zzz", který slouží jako oddělovač pole pole řetězců. Nové pole nezahrnují elementu, který obsahuje oddělovač.

[!code-vb[splitting-an-array-by-delimiter](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/split2.vb)] 

## <a name="joining-arrays"></a>Propojení polí

Můžete také kombinovat několik polí do jednoho pole větší. K tomuto účelu můžete také použít <xref:System.Array.Copy%2A?displayProperty=nameWithType> metoda. 

> [!NOTE] 
> Tato část nezaměřuje připojení pole řetězců do jednoho řetězce. Informace o připojení pole řetězců najdete v tématu <xref:System.String.Join%2A?displayProperty=nameWithType> metoda.

Před kopírováním do pole nové prvky každé pole, je třeba nejprve zajistit, že jste inicializovali pole, aby bylo dostatečně velký pro accompodate nové pole. Toto lze provést jedním ze dvou způsobů:

- Použití [ `ReDim Preserve` ](../../../../visual-basic/language-reference/statements/redim-statement.md) příkaz dynamicky rozšiřovat pole před přidáním nových elementů do ní. Toto je nejjednodušší techniku, ale to může způsobit snížení výkonu a využití příliš mnoho paměti při kopírování velké pole.
- Vypočítat celkový počet elementů potřebné pro nové velké pole a pak přidejte do ní prvků každé zdrojové pole.

Následující příklad používá druhý přístup k přidání čtyři pole deset elementy do jednoho pole.  

[!code-vb[joining-an-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/join.vb)] 

Vzhledem k tomu, že v tomto případě jsou všechny malé pole zdroj, jsme také dynamicky rozbalte pole jako přidáme prvky každé nové pole do ní. Následující příklad nemá který.

[!code-vb[joining-an-array-dynamically](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/join2.vb)] 

##  <a name="collections-as-an-alternative-to-arrays"></a>Kolekce jako alternativu k polím  
 Pole jsou velmi užitečné pro vytváření a práci s pevný počet objektů se silným typem. Kolekce poskytují flexibilnější způsob, jak pracovat s skupiny objektů. Na rozdíl od pole, které vyžadují explicitně změnit velikost pole s [ `ReDim` příkaz](../../../../visual-basic/language-reference/statements/redim-statement.md), kolekce zvýšit nebo snížit dynamicky potřebám o změnu aplikace.  
  
 Při použití `ReDim` k redimension pole, Visual Basic vytvoří nové pole a předchozí verze. Tato akce trvá dobu provádění. Proto pokud počet položek, které pracují se často mění, nebo nelze předpovědět maximální počet položek, které potřebujete, budete je obvykle získat lepší výkon pomocí kolekce.  
  
 Pro některé kolekce můžete přiřadit klíč pro libovolný objekt, který vložíte do kolekce, takže můžete rychle načíst objekt pomocí klíče.  
  
 Pokud kolekce obsahuje prvky pouze jeden datový typ, můžete použít jednu z tříd ve <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů. Obecné kolekce vynucuje bezpečnost typů tak, aby žádný datový typ lze přidat do ní.  
  
 Další informace o kolekcích najdete v tématu [kolekce](../../concepts/collections.md).
  
## <a name="related-topics"></a>Související témata  
  
|Termín|Definice|  
|----------|----------------|  
|[Rozměry pole v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)|Popisuje pořadí a dimenzí v polích.|  
|[Postupy: Inicializace proměnné pole v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)|Popisuje, jak k vyplnění polí se počáteční hodnoty.|  
|[Postupy: řazení pole v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-sort-an-array.md)|Ukazuje, jak abecedně seřaďte prvků pole.|  
|[Postupy: Přiřazení jednoho pole k druhému](../../../../visual-basic/programming-guide/language-features/arrays/how-to-assign-one-array-to-another-array.md)|Popisuje pravidla a kroky pro přiřazení k jiné proměnné pole pole.|  
|[Řešení potíží s poli](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)|Popisuje některé běžné problémy, které vznikají při práci s poli.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Array?displayProperty=nameWithType>  
 [Příkaz Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Příkaz ReDim](../../../../visual-basic/language-reference/statements/redim-statement.md)
