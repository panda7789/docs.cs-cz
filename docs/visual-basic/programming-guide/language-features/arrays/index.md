---
title: Pole v jazyce Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Array
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
caps.latest.revision: "47"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 04deeccd19fd4edb3f2c88310d660eedf5c707d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="arrays-in-visual-basic"></a>Pole v jazyce Visual Basic
Pole je sada hodnot, které jsou logicky vzájemně souvisí, jako je počet studentů v každé úrovni ve škole gramatika.  Pokud hledáte pomoc na pole v jazyce Visual Basic for Applications (VBA), přečtěte si téma [referenční příručka jazyka](https://msdn.microsoft.com/library/office/gg264383\(v=office.14\).aspx).  
  
 Pomocí pole můžete odkazovat na tyto hodnoty související se stejným názvem a použijte číslo, které se má volat index nebo dolní index, aby věděli, od sebe. Jednotlivé hodnoty se nazývají elementy pole. Jsou souvislý z indexu 0 prostřednictvím nejvyšší hodnotu indexu.  
  
 Na rozdíl od pole, je názvem proměnné, která obsahují jednu hodnotu *skalární* proměnné.  
  
 Rychlé příklady před vysvětlení:  
  
```vb  
'Declare a single-dimension array of 5 values  
Dim numbers(4) As Integer   
  
'Declare a single-dimension array and set array element values  
Dim numbers = New Integer() {1, 2, 4, 8}  
  
'Redefine the size of an existing array retaining the current values  
ReDim Preserve numbers(15)  
  
'Redefine the size of an existing array, resetting the values  
ReDim numbers(15)  
  
'Declare a multi-dimensional array  
Dim matrix(5, 5) As Double  
  
'Declare a multi-dimensional array and set array element values  
Dim matrix = New Integer(4, 4) {{1, 2}, {3, 4}, {5, 6}, {7, 8}}  
  
'Declare a jagged array  
Dim sales()() As Double = New Double(11)() {}  
```  
  
 **V tomto tématu**  
  
-   [Elementy pole v jednoduchých polí](#BKMK_ArrayElements)  
  
-   [Vytváření pole](#BKMK_CreatingAnArray)  
  
-   [Ukládání hodnot v matici](#BKMK_StoringValues)  
  
-   [Vyplní pole s počáteční hodnoty](#BKMK_Populating)  
  
    -   [Vnořená pole literály](#BKMK_NestedArrayLiterals)  
  
-   [Iterace v rámci pole](#BKMK_Iterating)  
  
-   [Pole jako parametry a návratové hodnoty](#BKMK_ReturnValues)  
  
-   [Vícenásobná pole](#BKMK_JaggedArrays)  
  
-   [Pole s nulovou délkou](#BKMK_ZeroLength)  
  
-   [Velikost pole](#BKMK_ArraySize)  
  
-   [Typy polí a dalších typů](#BKMK_ArrayTypes)  
  
-   [Kolekce jako alternativu k polím](#BKMK_Collections)  
  
##  <a name="BKMK_ArrayElements"></a>Elementy pole v jednoduchých polí  
 Následující příklad deklaruje proměnné pole pro uložení počet studentů v každé úrovni ve škole gramatika.  
  
 [!code-vb[VbVbalrArrays#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#2)]  
  
 Pole `students` v předchozím příkladu obsahuje sedm elementy. Indexy elementů rozsahu od 0 do 6. Toto pole je jednodušší než deklarování sedm proměnných.  
  
 Následující obrázek znázorňuje pole `students`. Pro každý element pole:  
  
-   Index elementu představuje úrovni (index 0 představuje mateřské školy).  
  
-   Hodnota, která je obsažena v elementu představuje počet studentů v této úrovni.  
  
 ![Obrázek znázorňující počet studentů pole](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexampleschool.gif "ArrayExampleSchool")  
Prvky pole "studenty"  
  
 Následující příklad ukazuje, jak odkazovat na první, druhý a posledním elementem pole `students`.  
  
 [!code-vb[VbVbalrArrays#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#3)]  
  
 Pole najdete jako celek s použitím právě názvu proměnné pole bez indexy.  
  
 Pole `students` v předchozím příkladu používá jeden index a je označen jako jednorozměrné. Pole, které používá více než jeden index nebo dolní index se nazývá multidimenzionální. Další informace najdete v tématu zbývající část tohoto tématu a [rozměry pole v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
##  <a name="BKMK_CreatingAnArray"></a>Vytváření pole  
 Můžete definovat velikosti pole několika způsoby. Když toto pole je deklarován jako následující příklad ukazuje, můžete zadat velikost.  
  
 [!code-vb[VbVbalrArrays#12](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#12)]  
  
 Můžete použít také `New` klauzule zadat velikost pole, když je vytvořen, jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrArrays#11](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#11)]  
  
 Pokud máte existující pole, můžete změnit její velikost pomocí `Redim` příkaz. Můžete určit, že `Redim` příkaz měli mít hodnoty, které jsou v poli, nebo můžete zadat, že ho vytvořit prázdné pole. Následující příklad ukazuje použití různých `Redim` příkaz mohli provádět úpravu velikosti pole existujících.  
  
 [!code-vb[VbVbalrArrays#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#13)]  
  
 Další informace najdete v tématu [ReDim – příkaz](../../../../visual-basic/language-reference/statements/redim-statement.md).  
  
##  <a name="BKMK_StoringValues"></a>Ukládání hodnot v matici  
 Mají přístup ke každé umístění v matici pomocí indexu typu `Integer`. Můžete ukládat a načíst hodnoty v pole pod položkou každé pole umístění pomocí jeho index uzavřený v závorkách. Indexů pro multidimenzionální pole se oddělují čárkami (,). Pro každé pole dimenze potřebovat jeden index. Následující příklad ukazuje některé příkazy, které ukládají hodnoty v polích.  
  
 [!code-vb[VbVbalrArrays#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#5)]  
  
 Následující příklad ukazuje některé příkazy, které získávají hodnoty z pole.  
  
 [!code-vb[VbVbalrArrays#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#6)]  
  
##  <a name="BKMK_Populating"></a>Vyplní pole s počáteční hodnoty  
 Pomocí pole literálu, můžete vytvořit pole, které obsahuje počáteční sadu hodnot. Literál pole sestává ze seznamu hodnot oddělených čárkami, které jsou uzavřené do složených závorek (`{}`).  
  
 Když vytvoříte pole pomocí pole literálu, můžete zadat typ pole nebo použít odvození typu určit typ pole. Následující kód ukazuje obě možnosti.  
  
 [!code-vb[VbVbalrCollectionInitializers#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#3)]  
  
 Při použití odvození typu typ pole je určen podle dominantní typu v seznamu hodnot pro pole literál poskytnutý. Dominantní typ je jedinečný typ, do které všechny ostatní typy v poli můžete rozšířit literál. Pokud tento typ jedinečného nelze určit, dominantní typ je typ jedinečného, do kterého můžete zúžit všechny ostatní typy v poli. Pokud žádná z těchto jedinečný se dá určit, že dominantní typ je `Object`. Například, pokud je seznam hodnot, do pole literál poskytnutý obsahuje hodnoty typu `Integer`, `Long`, a `Double`, výsledné pole je typu `Double`. Obě `Integer` a `Long` rozšířit pouze `Double`. Proto `Double` dominantní typu. Další informace najdete v tématu [Widening a zužující převody](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). Tato odvozená pravidla platí pro typy, které jsou odvozené pro pole, které jsou místní proměnné, které jsou definovány v člena třídy. I když literály pole můžete použít při vytváření proměnné na úrovni, nelze použít odvození typu proměnné na úrovni třídy. V důsledku toho literály pole, které jsou zadány na úrovni třídy odvození hodnoty, které jsou zadaná pro pole literálu jako typ `Object`.  
  
 Typ elementů můžete explicitně zadáte v pole, které je vytvořená pomocí pole literálu. V takovém případě musí rozšířit hodnoty v poli literálu typu elementy pole. Následující příklad kódu vytvoří pole typu `Double` ze seznamu celých čísel.  
  
 [!code-vb[VbVbalrCollectionInitializers#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#4)]  
  
###  <a name="BKMK_NestedArrayLiterals"></a>Vnořená pole literály  
 Multidimenzionální pole můžete vytvořit pomocí literály vnořená pole. Literály vnořená pole musí mít dimenze, počet nebo rank, který je v souladu s výsledné pole. Následující příklad kódu vytvoří dvourozměrná pole celých čísel pomocí pole literálu.  
  
 [!code-vb[VbVbalrCollectionInitializers#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#7)]  
  
 V předchozím příkladu by dojít k chybě, pokud počet elementů v literálech vnořená pole se neshodovaly. Pokud explicitně deklarovat proměnnou pole být jiné než dvourozměrná by také dojít k chybě.  
  
> [!NOTE]
>  Když zadáte vnořená pole literály různých dimenzí uzavřením literály vnitřní pole do závorek se můžete vyhnout k chybě. Vynutit závorek literálu výraz pole k vyhodnocení a výsledné hodnoty se používají s poli vnější literálu, jak ukazuje následující kód.  
  
 [!code-vb[VbVbalrCollectionInitializers#11](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#11)]  
  
 Když vytvoříte multidimenzionálního pole pomocí literály vnořená pole, můžete použít odvození typu. Při použití odvození typu odvozené typ je typ dominantní pro všechny hodnoty ve všech literály pole pro úroveň vnoření. Následující příklad kódu vytvoří dvourozměrná pole typu `Double` z hodnoty, které jsou typu `Integer` a `Double`.  
  
 [!code-vb[VbVbalrCollectionInitializers#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#8)]  
  
 Další příklady najdete v tématu [postupy: Inicializace proměnné pole v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md).  
  
##  <a name="BKMK_Iterating"></a>Iterace v rámci pole  
 Při iteraci pole přístup k nejvyšší index každý prvek v poli od nejnižší indexu.  
  
 V následujícím příkladu prochází jednorozměrné pole s použitím [pro... Další příkaz](../../../../visual-basic/language-reference/statements/for-next-statement.md). <xref:System.Array.GetUpperBound%2A> Metoda vrátí nejvyšší hodnotu, která může mít index. Nejnižší hodnotu indexu je vždy 0.  
  
 [!code-vb[VbVbalrArrays#41](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#41)]  
  
 V následujícím příkladu prochází multidimenzionálního pole pomocí `For...Next` příkaz. <xref:System.Array.GetUpperBound%2A> Metoda má parametr, který určuje dimenzi. `GetUpperBound(0)`Vrátí hodnotu vysoké index pro první dimenze a `GetUpperBound(1)` vrací hodnotu vysoké index pro druhý dimenze.  
  
 [!code-vb[VbVbalrArrays#42](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#42)]  
  
 V následujícím příkladu prochází jednorozměrné pole pomocí [For Each... Další příkaz](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 [!code-vb[VbVbalrArrays#43](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#43)]  
  
 V následujícím příkladu prochází multidimenzionálního pole pomocí `For Each...Next` příkaz. Ale máte větší kontrolu nad prvky multidimenzionální pole Pokud používáte vnořený `For…Next` příkaz, jak ukazuje předchozí příklad, místo `For Each…Next` příkaz.  
  
 [!code-vb[VbVbalrArrays#44](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#44)]  
  
##  <a name="BKMK_ReturnValues"></a>Pole jako parametry a návratové hodnoty  
 Pro vrácení pole z `Function` postupu zadejte pole datový typ a počet dimenzí jako návratový typ [funkce příkaz](../../../../visual-basic/language-reference/statements/function-statement.md). V rámci funkce deklarujte proměnnou místní pole stejným datový typ a počet dimenzí. V [příkaz Return](../../../../visual-basic/language-reference/statements/return-statement.md), zahrnout proměnnou místní pole bez závorek.  
  
 Chcete určit pole jako parametr, který se `Sub` nebo `Function` postupu, definujte parametr jako pole s zadaný datový typ a počet dimenzí. Ve volání postup odeslání proměnné pole s stejný datový typ a počet dimenzí.  
  
 V následujícím příkladu `GetNumbers` funkce vrátí `Integer()`. Tento typ pole je typu jednorozměrné pole `Integer`. `ShowNumbers` Přijímá postup `Integer()` argument.  
  
 [!code-vb[VbVbalrArrays#51](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#51)]  
  
 V následujícím příkladu `GetNumbersMultiDim` funkce vrátí `Integer(,)`. Tento typ pole je dva dimenzí pole typu `Integer`.  `ShowNumbersMultiDim` Přijímá postup `Integer(,)` argument.  
  
 [!code-vb[VbVbalrArrays#52](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#52)]  
  
##  <a name="BKMK_JaggedArrays"></a>Vícenásobná pole  
 Pole, které obsahuje další pole jako elementy se označuje jako pole polí nebo Vícenásobná pole. Vícenásobná pole a každý prvek v Vícenásobná pole může mít jeden nebo více dimenzí. Struktura dat v aplikaci je někdy dvourozměrná, ale není obdélníkový.  
  
 V následujícím příkladu má pole měsíců, je každý element pole dní. Protože různé měsíce mají různý počet dní, nemáte elementy formuláři obdélníková dvourozměrná pole. Vícenásobná pole se tedy používá místo multidimenzionálního pole.  
  
 [!code-vb[VbVbalrArrays#21](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#21)]  
  
##  <a name="BKMK_ZeroLength"></a>Pole s nulovou délkou  
 Pole, které neobsahuje žádné elementy, je také označován pole nulové délky. Proměnné, která obsahuje pole nulovou délkou nemá hodnotu `Nothing`. Pokud chcete vytvořit pole, které nemá žádné elementy, deklarujte jeden z tohoto pole dimenze mít hodnotu -1, jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrArrays#14](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#14)]  
  
 Můžete potřebovat pro vytvoření nulová délka pole v následujících případech:  
  
-   Bez rizika <xref:System.NullReferenceException> výjimky, kódu musí přístup ke členům v <xref:System.Array> třídy, jako například <xref:System.Array.Length%2A> nebo <xref:System.Array.Rank%2A>, nebo volejte [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] funkce, jako <xref:Microsoft.VisualBasic.Information.UBound%2A>.  
  
-   Chcete zachovat jednodušší náročné kód tak, že není zkontrolujte `Nothing` zvláštním způsobem.  
  
-   Váš kód komunikuje s programovací rozhraní aplikace (API), který vyžaduje, abyste předat nulová délka pole jednoho nebo více procedur nebo vrátí pole nulovou délkou z jednoho nebo více procedur.  
  
##  <a name="BKMK_ArraySize"></a>Velikost pole  
 Velikost pole je produkt délek všechny jeho dimenze. Představuje celkový počet elementů aktuálně obsažených v poli.  
  
 Následující příklad deklaruje trojrozměrné.  
  
```vb
Dim prices(3, 4, 5) As Long  
```  
  
 Celkovou velikost pole v proměnné `prices` (3 + 1) x (4 + 1) x (5 + 1) = 120.  
  
 Velikost pole můžete najít pomocí <xref:System.Array.Length%2A> vlastnost. Délka Každá dimenze vícerozměrné můžete najít pomocí <xref:System.Array.GetLength%2A> metoda.  
  
 Velikost proměnné pole můžete změnit přiřazením nový objekt pole k němu nebo pomocí `ReDim` příkaz.  
  
 Je třeba vzít v úvahu při plánování práce s velikost pole několik věcí.  
  
|||  
|---|---|  
|Délka dimenze|Index Každá dimenze je založené na 0, což znamená, že ho rozsahu od 0 do jeho horní mez. Délka dané dimenze je proto o 1 větší deklarované horní mez pro daná dimenze.|  
|Omezení délky|Délka všech dimenzí pole je omezená na maximální hodnota, která `Integer` datového typu, který je (2 ^ 31) - 1. Ale celková velikost pole je také omezena paměti k dispozici v systému. Pokud pokus o inicializaci pole, přesahuje množství dostupné paměti RAM, vyvolá modul common language runtime <xref:System.OutOfMemoryException> výjimka.|  
|Velikost a velikost – Element|Velikost tohoto pole je nezávislé na datový typ jejích elementů. Velikost vždy představuje celkový počet elementů, nikoli počet bajtů, které budou využívat v úložišti.|  
|Paměťové nároky|Není bezpečné, aby všechny předpoklady týkající se uložení pole v paměti. Úložiště se liší na platformy různých datových šířek, takže stejného pole můžete spotřebuje další paměť na 64bitovém systému než v 32bitové verzi systému. V závislosti na konfiguraci systému při inicializaci pole, modul CLR (CLR) můžete přiřadit úložiště jako zavřete společně, nejdříve pack elementy nebo přizpůsobit je všechny na hranicích přirozené hardwaru. Také pole úložiště režie vyžaduje pro své informace o řízení a režijní náklady na tato hodnota se zvyšuje s každá přidané dimenze.|  
  
##  <a name="BKMK_ArrayTypes"></a>Typy polí a dalších typů  
 Každé pole má datový typ, ale liší se od datového typu jejích elementů. Neexistuje žádný single – datový typ pro všechna pole. Místo toho je datový typ pole určuje počet dimenzí, nebo *pořadí*, pole a datový typ elementů v poli. Dvě proměnné pole, které jsou považovány za mít stejný datový typ, pouze pokud mají stejné pořadí a jejich elementů mít stejný datový typ. Dimenze v pole délek neovlivňují datový typ pole.  
  
 Každé pole dědí z <xref:System.Array?displayProperty=nameWithType> třídy a můžou deklarovat proměnnou být typu `Array`, ale nelze vytvořit pole typu `Array`. Navíc [ReDim – příkaz](../../../../visual-basic/language-reference/statements/redim-statement.md) nemůže pracovat na proměnnou deklarován jako typ `Array`. Z těchto důvodů a pro bezpečnost typů, je třeba deklarovat každé pole jako specifického typu, například `Integer` v předchozím příkladu.  
  
 Můžete zjistit datový typ pole nebo jeho prvky několika způsoby.  
  
-   Můžete volat <xref:System.Object.GetType%2A?displayProperty=nameWithType> metoda na proměnnou pro příjem <xref:System.Type> objektu pro typ spuštění proměnné. <xref:System.Type> Objektu obsahuje velké množství informací v její vlastnosti a metody.  
  
-   Můžete předat proměnnou <xref:Microsoft.VisualBasic.Information.TypeName%2A> funkce pro příjem `String` obsahující název typu běhu.  
  
-   Můžete předat proměnnou <xref:Microsoft.VisualBasic.Information.VarType%2A> funkce pro příjem `VariantType` hodnotu představující klasifikace typ proměnné.  
  
 Následující příklad volání `TypeName` funkce k určení typu pole a typ elementů v poli. Typ pole je `Integer(,)` a prvků v poli typu `Integer`.  
  
 [!code-vb[VbVbalrArrays#15](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#15)]  
  
##  <a name="BKMK_Collections"></a>Kolekce jako alternativu k polím  
 Pole jsou velmi užitečné pro vytváření a práci s pevný počet objektů se silným typem. Kolekce poskytují flexibilnější způsob, jak pracovat s skupiny objektů. Na rozdíl od pole skupinu objektů, které pracují se můžete zvýšit nebo snížit dynamicky potřebám změna aplikace.  
  
 Pokud potřebujete změnit velikost pole, je nutné použít [ReDim – příkaz](../../../../visual-basic/language-reference/statements/redim-statement.md). Při tomto, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] vytvoří nové pole a uvolní předchozí pole pro uvolnění. Tato akce trvá dobu provádění. Proto pokud počet položek, které pracují se často mění, nebo nelze předpovědět maximální počet položek, které potřebujete, může získat lepší výkon pomocí kolekce.  
  
 Pro některé kolekce můžete přiřadit klíč pro libovolný objekt, který vložíte do kolekce, takže můžete rychle načíst objekt pomocí klíče.  
  
 Pokud kolekce obsahuje prvky pouze jeden datový typ, můžete použít jednu z tříd ve <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů. Obecné kolekce vynucuje bezpečnost typů tak, aby žádný datový typ lze přidat do ní. Při načítání element z obecnou kolekci, není nutné určit její datový typ nebo je převeďte.  
  
 Další informace o kolekcích najdete v tématu [kolekce](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b).  
  
### <a name="example"></a>Příklad  
 Následující příklad používá [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] – obecná třída <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> k vytvoření kolekce seznamu `Customer` objekty.  
  
 [!code-vb[VbVbalrArrays#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#1)]  
  
 Prohlášení o `CustomerFile` kolekce Určuje, že může obsahovat pouze elementy typu `Customer`. Umožňuje také počáteční kapacita 200 elementů. Postup `AddNewCustomer` kontroluje nového elementu pro platnosti a poté jej přidá do kolekce. Postup `PrintCustomers` používá `For Each` smyčky k procházení kolekce a zobrazení jejích elementů.  
  
## <a name="related-topics"></a>Související témata  
  
|Termín|Definice|  
|----------|----------------|  
|[Rozměry pole v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)|Popisuje pořadí a dimenzí v polích.|  
|[Postupy: Inicializace proměnné pole v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)|Popisuje, jak k vyplnění polí se počáteční hodnoty.|  
|[Postupy: řazení pole v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-sort-an-array.md)|Ukazuje, jak abecedně seřaďte prvků pole.|  
|[Postupy: přiřazení jednoho pole ke druhému](../../../../visual-basic/programming-guide/language-features/arrays/how-to-assign-one-array-to-another-array.md)|Popisuje pravidla a kroky pro přiřazení k jiné proměnné pole pole.|  
|[Řešení potíží s poli](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)|Popisuje některé běžné problémy, které vznikají při práci s poli.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Array>  
 [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [ReDim – příkaz](../../../../visual-basic/language-reference/statements/redim-statement.md)
