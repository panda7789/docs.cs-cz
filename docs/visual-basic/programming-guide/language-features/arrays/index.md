---
title: Pole
ms.date: 12/06/2017
f1_keywords:
- vb.Array
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
ms.openlocfilehash: 5093f28f05c5b72294dce9a4e69723acafb31a9f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413089"
---
# <a name="arrays-in-visual-basic"></a>Pole v jazyce Visual Basic

Pole je sada hodnot, které jsou *výrazy, které*jsou logicky vzájemně propojené. Pole může například sestávat z počtu studentů v každé třídě v gramatické škole; Každý prvek pole je počet studentů v jedné třídě. Podobně může pole sestávat ze tříd studenta pro třídu; Každý prvek pole je jednou ze stupňů.

Je možné, že jednotlivé proměnné budou ukládat jednotlivé datové položky. Například pokud naše aplikace analyzuje třídy studenta, můžeme použít samostatnou proměnnou pro každou třídu studenta, jako `englishGrade1` je například, `englishGrade2` atd. Tento přístup má tři hlavní omezení:

- V době návrhu musíme přesně zjistit, kolik stupňů potřebujeme zpracovat.
- Rychlé zpracování velkého počtu druhů se nepraktický. Tím dojde k tomu, že aplikace bude mnohem pravděpodobnější, že bude mít vážné chyby.
- Údržbu je obtížné. Každou novou třídu, kterou přidáváme, vyžaduje, aby se aplikace upravila, znovu zkompiluje a znovu nasadila.

Pomocí pole můžete odkazovat na tyto související hodnoty se stejným názvem a použít číslo, které se nazývá *index* nebo *dolní index* k identifikaci jednotlivého prvku na základě jeho pozice v poli. Indexy rozsahu pole od 0 do jednoho menšího než celkový počet prvků v poli. Použijete-li syntaxi Visual Basic k definování velikosti pole, určíte jeho nejvyšší index, nikoli celkový počet prvků v poli. S polem můžete pracovat jako s jednotkou a možnost iterovat své prvky je nepotřebné k tomu, abyste přesně věděli, kolik prvků obsahuje v době návrhu.

Některé rychlé příklady před vysvětlením:

```vb
' Declare a single-dimension array of 5 numbers.
Dim numbers(4) As Integer

' Declare a single-dimension array and set its 4 values.
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

## <a name="array-elements-in-a-simple-array"></a>Prvky pole v jednoduchém poli

Pojďme vytvořit pole s názvem `students` pro uložení počtu studentů v každé třídě v gramatické škole. Indexy prvků jsou v rozsahu od 0 do 6. Použití tohoto pole je jednodušší než deklarace sedmi proměnných.

Následující ilustrace znázorňuje `students` pole. Pro každý prvek pole:

- Index elementu reprezentuje třídu (index 0 představuje kindergarten).

- Hodnota, která je obsažena v elementu, představuje počet studentů v této třídě.

![Diagram znázorňující pole čísel studentů](./media/index/students-array-elements.gif)

Následující příklad obsahuje kód Visual Basic, který vytváří a používá pole:

[!code-vb[simple-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/simple-array.vb)]

Příklad provádí tři věci:

- Deklaruje `students` pole s sedmi prvky. Číslo `6` v deklaraci pole označuje poslední index v poli, je menší než počet prvků v poli.
- Přiřadí hodnoty každému prvku v poli. K prvkům pole se dostanete pomocí názvu pole a zahrnutím indexu jednotlivého prvku do závorek.
- Obsahuje seznam všech hodnot pole. V příkladu se používá [`For`](../../../language-reference/statements/for-next-statement.md) příkaz pro přístup k jednotlivým prvkům pole podle jeho čísla indexu.

`students`Pole v předchozím příkladu je jednorozměrné pole, protože používá jeden index. Pole, které používá více než jeden index nebo dolní index, je označováno jako *multidimenzionální*. Další informace najdete v tématu zbývající část tohoto článku a [rozměry pole v Visual Basic](array-dimensions.md).

## <a name="creating-an-array"></a>Vytvoření pole

Velikost pole můžete definovat několika způsoby:

- Můžete určit velikost při deklaraci pole:

  [!code-vb[creating1](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#1)]

- Můžete použít `New` klauzuli k poskytnutí velikosti pole při jeho vytvoření:

  [!code-vb[creating2](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#2)]

Máte-li existující pole, lze jeho velikost změnit pomocí [`ReDim`](../../../language-reference/statements/redim-statement.md) příkazu. Můžete určit, že `ReDim` příkaz zachová hodnoty, které jsou v poli, nebo můžete určit, že vytvoří prázdné pole. Následující příklad ukazuje různá použití `ReDim` příkazu pro úpravu velikosti existujícího pole.

[!code-vb[redimensioning](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#3)]

Další informace naleznete v [příkazu ReDim](../../../language-reference/statements/redim-statement.md).

## <a name="storing-values-in-an-array"></a>Ukládání hodnot do pole

Ke každému umístění v poli můžete přistupovat pomocí indexu typu `Integer` . Můžete uložit a načíst hodnoty v poli odkazem na každé umístění pole pomocí jeho indexu uzavřeného v závorkách. Indexy multidimenzionálních polí jsou odděleny čárkami (,). Pro každou dimenzi pole potřebujete jeden index.

Následující příklad ukazuje některé příkazy, které ukládají a načítají hodnoty v polích.

[!code-vb[store-and-retrieve](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/store-and-retrieve.vb)]

## <a name="populating-an-array-with-array-literals"></a>Naplnění pole pomocí literálů pole

Pomocí literálu pole lze naplnit pole počáteční sadou hodnot ve stejnou dobu, kterou vytvoříte. Literál pole se skládá ze seznamu hodnot oddělených čárkami, které jsou uzavřeny ve složených závorkách ( `{}` ).

Při vytváření pole pomocí literálu pole můžete buď zadat typ pole nebo použít odvození typu k určení typu pole. Následující příklad ukazuje obě možnosti.

[!code-vb[create-with-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#4)]

Při použití odvození typu je typ pole určen *dominantním typem* v seznamu hodnot literálů. Dominantní typ je typ, na který lze rozšířit všechny ostatní typy v poli. Pokud tento jedinečný typ nelze určit, dominantní typ je jedinečný typ, na který mohou být zúženy všechny ostatní typy v poli. Pokud ani jeden z těchto jedinečných typů nelze určit, dominantní typ je `Object` . Například pokud seznam hodnot, které jsou zadány do literálu pole, obsahuje hodnoty typu `Integer` , `Long` , a `Double` výsledné pole je typu `Double` . Protože `Integer` a `Long` rozšíření pouze na `Double` , `Double` je dominantní typ. Další informace najdete v tématu [rozšiřování a zúžení převodů](../data-types/widening-and-narrowing-conversions.md).

> [!NOTE]
> Odvození typu lze použít pouze pro pole, která jsou definována jako lokální proměnné v rámci člena typu. Pokud není k dispozici definice explicitního typu, pole definovaná s literály pole na úrovni třídy jsou typu `Object[]` . Další informace naleznete v tématu [odvození místního typu](../variables/local-type-inference.md).

Všimněte si, že předchozí příklad definuje `values` jako pole typu, `Double` i když všechny literály pole jsou typu `Integer` . Toto pole lze vytvořit, protože hodnoty v literálu pole lze rozšířit na `Double` hodnoty.

Můžete také vytvořit a naplnit multidimenzionální pole pomocí *literálů vnořeného pole*. Literály vnořeného pole musí obsahovat řadu dimenzí, které jsou konzistentní s výsledným polem. Následující příklad vytvoří dvojrozměrné pole celých čísel pomocí literálů vnořeného pole.

[!code-vb[nested-array-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#5)]

Při použití literálů vnořeného pole k vytvoření a naplnění pole dojde k chybě, pokud se počet prvků v literálech vnořeného pole neshoduje. K chybě dojde také v případě, že explicitně deklarujete proměnnou pole tak, aby měla jiný počet rozměrů než literály pole.

Stejně jako u jednorozměrného pole lze při vytváření multidimenzionálního pole s literály vnořeného pole spoléhat na odvození typu. Odvozený typ je dominantní typ pro všechny hodnoty ve všech literálech pole pro všechny úrovně vnoření. Následující příklad vytvoří dvourozměrné pole typu `Double[,]` z hodnot, které jsou typu `Integer` a `Double` .

[!code-vb[nested-type-inference](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#6)]

Další příklady naleznete v tématu [How to: Initialize a Array Variable in Visual Basic](how-to-initialize-an-array-variable.md).

## <a name="iterating-through-an-array"></a>Iterace prostřednictvím pole

Při iteraci přes pole přistupujete ke každému prvku v poli z nejnižší index na nejvyšší nebo od nejvyšších po nejnižší. Obvykle použijte buď [pro... Další příkaz](../../../language-reference/statements/for-next-statement.md) nebo [pro každý... Další příkaz](../../../language-reference/statements/for-each-next-statement.md) pro iteraci prvky pole. Pokud neznáte horní meze pole, můžete zavolat <xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType> metodu pro získání nejvyšší hodnoty indexu. I když nejnižší hodnota indexu je skoro vždycky 0, můžete zavolat <xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType> metodu, abyste získali nejnižší hodnotu indexu.

Následující příklad projde jednorozměrné pole pomocí [`For...Next`](../../../language-reference/statements/for-next-statement.md) příkazu.

[!code-vb[iterate-one-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate1d.vb)]

Následující příklad provede iteraci multidimenzionálního pole pomocí [`For...Next`](../../../language-reference/statements/for-next-statement.md) příkazu. <xref:System.Array.GetUpperBound%2A>Metoda má parametr, který určuje dimenzi. `GetUpperBound(0)`Vrátí nejvyšší index prvního rozměru a `GetUpperBound(1)` vrátí nejvyšší index druhé dimenze.

[!code-vb[iterate-two-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate2d.vb)]

Následující příklad používá [pro každý... Další příkaz](../../../language-reference/statements/for-each-next-statement.md)pro iterování pomocí jednorozměrného pole a dvojrozměrného pole.

[!code-vb[iterate-for-each-next](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate-for-each-next.vb)]

## <a name="array-size"></a>Velikost pole

Velikost pole je součinem délek všech jeho rozměrů. Představuje celkový počet prvků, které jsou aktuálně obsaženy v poli.  Například následující příklad deklaruje dvojrozměrné pole se čtyřmi prvky v každé dimenzi. Jak ukazuje výstup z příkladu, je velikost pole 16 (nebo (3 + 1) * (3 + 1).

[!code-vb[array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size.vb)]

> [!NOTE]
> Tato diskuze o velikosti pole se nevztahuje na vícenásobná pole. Informace o vícenásobných polích a určení velikosti vícenásobného pole naleznete v části [vícenásobná pole](#jagged-arrays) .

Velikost pole můžete najít pomocí <xref:System.Array.Length%2A?displayProperty=nameWithType> Vlastnosti. Délku každé dimenze multidimenzionálního pole lze najít pomocí <xref:System.Array.GetLength%2A?displayProperty=nameWithType> metody.

Můžete změnit velikost proměnné pole přiřazením nového objektu Array k poli nebo pomocí příkazu [ `ReDim` příkazu](../../../language-reference/statements/redim-statement.md) . Následující příklad používá `ReDim` příkaz ke změně pole 100 elementu na pole 51-element.

[!code-vb[resize-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size2.vb)]

Při práci s velikostí pole je potřeba mít na paměti několik věcí.

|||
|---|---|
|Délka dimenze|Index každé dimenze je založen na 0, což znamená, že je rozsah od 0 do horní meze. Proto je délka dané dimenze jedna větší než deklarovaná horní mez této dimenze.|
|Omezení délky|Délka každé dimenze pole je omezená na maximální hodnotu `Integer` datového typu, což je <xref:System.Int32.MaxValue?displayProperty=nameWithType> nebo (2 ^ 31)-1. Celková velikost pole je ale také omezená pamětí, která je k dispozici ve vašem systému. Pokud se pokusíte inicializovat pole, které překračuje množství dostupné paměti, modul runtime vyvolá <xref:System.OutOfMemoryException> .|
|Velikost a velikost elementu|Velikost pole je nezávislá na datovém typu jeho prvků. Velikost vždy představuje celkový počet prvků, nikoli počet bajtů, které spotřebovávají v paměti.|
|Memory Consumption|Není bezpečné dělat žádné předpoklady týkající se toho, jak je pole Uloženo v paměti. Úložiště se liší na platformách různých šířek dat, takže stejné pole může spotřebovat víc paměti v 64 systému, než na 32 systému. V závislosti na konfiguraci systému při inicializaci pole může modul CLR (Common Language Runtime) přiřadit úložiště buď k zabalení prvků co nejblíže, nebo pro jejich zarovnání na hranice přirozeného hardwaru. Pole také vyžaduje režijní náklady na úložiště pro informace o ovládacím prvku a tato režie se zvyšuje s každou přidanou dimenzí.|

## <a name="the-array-type"></a>Typ pole

Každé pole má datový typ, který se liší od datového typu jeho prvků. Pro všechna pole není k dispozici žádný jediný datový typ. Místo toho se datový typ pole určuje podle počtu rozměrů nebo *pořadí*, pole a datového typu prvků v poli. Dvě proměnné pole jsou stejného datového typu pouze v případě, že mají stejný rozsah a jejich prvky mají stejný datový typ. Délky rozměrů pole neovlivňují datový typ pole.

Každé pole dědí z <xref:System.Array?displayProperty=nameWithType> třídy a můžete deklarovat proměnnou, která má být typu `Array` , ale nelze vytvořit pole typu `Array` . Například Přestože následující kód deklaruje `arr` proměnnou jako typ `Array` a volá <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metodu pro vytvoření instance pole, typ pole se projeví jako objekt [].

[!code-vb[array-class](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-class.vb)]

[Příkaz ReDim](../../../language-reference/statements/redim-statement.md) nelze také použít pro proměnnou deklarovanou jako typ `Array` . Z těchto důvodů a pro bezpečnost typů je vhodné deklarovat každé pole jako konkrétní typ.

Datový typ pole nebo jeho prvků můžete zjistit několika způsoby.

- Můžete zavolat <xref:System.Object.GetType%2A> metodu na proměnnou a získat tak <xref:System.Type> objekt, který představuje běhový typ proměnné. <xref:System.Type>Objekt obsahuje rozsáhlé informace o vlastnostech a metodách.
- Proměnnou můžete předat do <xref:Microsoft.VisualBasic.Information.TypeName%2A> funkce a získat tak `String` název typu za běhu.

Následující příklad volá jak `GetType` metodu, tak `TypeName` funkci pro určení typu pole. Typ pole je `Byte(,)` . Všimněte si, že <xref:System.Type.BaseType%2A?displayProperty=nameWithType> vlastnost také označuje, že základní typ bajtového pole je <xref:System.Array> Třída.

[!code-vb[array-type](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-type.vb)]

## <a name="arrays-as-return-values-and-parameters"></a>Pole jako návratové hodnoty a parametry

Chcete-li vrátit pole z `Function` procedury, zadejte datový typ Array a počet dimenzí jako návratový typ [příkazu funkce](../../../language-reference/statements/function-statement.md). V rámci funkce deklarujte místní proměnnou pole se stejným datovým typem a počtem rozměrů. V [příkazu return](../../../language-reference/statements/return-statement.md)zahrňte proměnnou místního pole bez závorek.

Chcete-li určit pole jako parametr pro `Sub` `Function` proceduru nebo, definujte parametr jako pole se zadaným datovým typem a počtem dimenzí. V volání procedury předejte proměnnou pole se stejným datovým typem a počtem dimenzí.

V následujícím příkladu `GetNumbers` funkce vrací jednorozměrné `Integer()` pole typu `Integer` . `ShowNumbers`Procedura přijímá `Integer()` argument.

[!code-vb[return-value-and-params](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params.vb)]

V následujícím příkladu `GetNumbersMultiDim` funkce vrací dvojrozměrné `Integer(,)` pole typu `Integer` .  `ShowNumbersMultiDim`Procedura přijímá `Integer(,)` argument.

[!code-vb[multidimensional-return-value](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params-2d.vb)]

## <a name="jagged-arrays"></a>Vícenásobná pole

V některých případech je struktura dat ve vaší aplikaci dvourozměrná, ale ne pravoúhlá. Například můžete použít pole k ukládání dat o vysoké teplotě každého dne v měsíci. První rozměr pole představuje měsíc, ale druhá dimenze představuje počet dní a počet dní v měsíci není stejnorodý. *Vícenásobné pole*, které se označuje také jako *pole polí*, je navrženo pro tyto scénáře. Vícenásobné pole je pole, jehož prvky jsou také pole. Vícenásobné pole a každý prvek ve vícenásobném poli může mít jednu nebo více dimenzí.

Následující příklad používá pole měsíců, přičemž každý prvek je pole dnů. V příkladu se používá vícenásobné pole, protože různé měsíce mají různý počet dnů.  Tento příklad ukazuje, jak vytvořit vícenásobné pole, přiřadit k němu hodnoty a načíst a zobrazit jeho hodnoty.

[!code-vb[jagged-arrays](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged.vb)]

Předchozí příklad přiřadí hodnoty vícenásobnému poli na základě prvku pomocí `For...Next` smyčky. Můžete také přiřadit hodnoty prvkům vícenásobného pole pomocí literálů vnořeného pole. Pokus o použití literálů vnořeného pole (například `Dim valuesjagged = {{1, 2}, {2, 3, 4}}` ) vygeneruje chybu kompilátoru [BC30568](../../../misc/bc30568.md). Chcete-li chybu opravit, vložte literály vnitřních polí do závorek. Závorky přinutí vyhodnotit výraz literálu pole a výsledné hodnoty jsou použity s vnějším literálem pole, jak ukazuje následující příklad.

[!code-vb[jagged-array-initialization](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-assign.vb)]

Vícenásobné pole je jednorozměrné pole, jehož prvky obsahují pole. Proto <xref:System.Array.Length%2A?displayProperty=nameWithType> vlastnost a `Array.GetLength(0)` Metoda vrátí počet prvků v jednorozměrném poli a `Array.GetLength(1)` vyvolá výjimku, <xref:System.IndexOutOfRangeException> protože vícenásobné pole není vícerozměrné. Určíte počet prvků v každém podpoli načtením hodnoty vlastnosti každého podpole <xref:System.Array.Length%2A?displayProperty=nameWithType> . Následující příklad ukazuje, jak určit počet prvků ve vícenásobném poli.

[!code-vb[jagged-array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-length.vb)]

## <a name="zero-length-arrays"></a>Pole s nulovou délkou

Visual Basic rozlišuje mezi neinicializovaným polem (polem, jehož hodnota je `Nothing` ) a *polem s nulovou délkou* nebo prázdným polem (pole, které neobsahuje žádné prvky.) Neinicializovaný objekt Array je ten, který nemá vytvořenou dimenzi nebo k němu byly přiřazeny nějaké hodnoty. Příklad:

```vb
Dim arr() As String
```

Pole s nulovou délkou je deklarováno s rozměrem-1. Příklad:

```vb
Dim arrZ(-1) As String
```

Pole s nulovou délkou možná budete muset vytvořit za následujících okolností:

- Aniž by došlo k <xref:System.NullReferenceException> výjimce, váš kód musí mít přístup ke členům třídy, jako je například <xref:System.Array> <xref:System.Array.Length%2A> nebo <xref:System.Array.Rank%2A> , nebo volat funkci Visual Basic, jako je například <xref:Microsoft.VisualBasic.Information.UBound%2A> .

- Chcete, aby byl kód jednoduchý, nemusíte ho kontrolovat `Nothing` jako zvláštní případ.

- Váš kód komunikuje s rozhraním API (Application Programming Interface), které vyžaduje, abyste předávali pole nulové délky k jednomu nebo více procedurám nebo v jednom nebo více postupech vrátili pole s nulovou délkou.

## <a name="splitting-an-array"></a>Rozdělení pole

V některých případech může být nutné rozdělit jedno pole do více polí. To zahrnuje identifikaci bodu nebo bodů, ve kterých má být pole rozděleno, a pak Spitting pole do dvou nebo více samostatných polí.

> [!NOTE]
> Tato část nepopisuje rozdělení jednoho řetězce do pole řetězců na základě některého oddělovače. Informace o rozdělení řetězce naleznete v <xref:System.String.Split%2A?displayProperty=nameWithType> metodě.

Nejběžnější kritéria pro rozdělení pole jsou:

- Počet prvků v poli. Například můžete chtít rozdělit pole více než zadaný počet prvků na číslo přibližně stejné části. Pro účely tohoto účelu můžete použít hodnotu vrácenou <xref:System.Array.Length%2A?displayProperty=nameWithType> <xref:System.Array.GetLength%2A?displayProperty=nameWithType> metodou nebo.

- Hodnota prvku, který slouží jako oddělovač, který označuje, kde má být pole rozděleno. Konkrétní hodnotu můžete vyhledat voláním <xref:System.Array.FindIndex%2A?displayProperty=nameWithType> <xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType> metod a.

Jakmile určíte index nebo indexy, u kterých má být pole rozděleno, můžete vytvořit jednotlivá pole voláním <xref:System.Array.Copy%2A?displayProperty=nameWithType> metody.

Následující příklad rozdělí pole do dvou polí přibližně stejné velikosti. (Pokud celkový počet elementů pole je lichý, první pole má jeden další prvek než druhý.)

[!code-vb[splitting-an-array-by-length](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split1.vb)]

Následující příklad rozdělí pole řetězců do dvou polí na základě přítomnosti elementu, jehož hodnota je "ZZZ", která slouží jako oddělovač pole. Nová pole neobsahují element, který obsahuje oddělovač.

[!code-vb[splitting-an-array-by-delimiter](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split2.vb)]

## <a name="joining-arrays"></a>Spojování polí

V jednom větším poli můžete také zkombinovat několik polí. K tomu můžete použít také <xref:System.Array.Copy%2A?displayProperty=nameWithType> metodu.

> [!NOTE]
> Tato část se nezabývá připojením pole řetězců k jednomu řetězci. Informace o spojování pole řetězců naleznete v <xref:System.String.Join%2A?displayProperty=nameWithType> metodě.

Před zkopírováním prvků každého pole do nového pole je nutné nejprve zajistit, aby bylo pole inicializováno tak, aby bylo dostatečně velké, aby bylo možné přizpůsobit novému poli. Toto lze provést jedním ze dvou způsobů:

- Použijte [`ReDim Preserve`](../../../language-reference/statements/redim-statement.md) příkaz k dynamickému rozbalení pole před přidáním nových prvků do něj. Toto je nejjednodušší postup, ale může způsobit snížení výkonu a nadměrné využití paměti při kopírování velkých polí.
- Vypočítá celkový počet prvků potřebných pro nové velké pole a potom do něj přidejte prvky každého zdrojového pole.

Následující příklad používá druhý přístup pro přidání čtyř polí s deseti prvky každý do jednoho pole.

[!code-vb[joining-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join.vb)]

Vzhledem k tomu, že v tomto případě jsou zdrojová pole malá, můžeme také dynamicky rozšířit pole, protože do něj přidáte prvky každého nového pole. V následujícím příkladu je to.

[!code-vb[joining-an-array-dynamically](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join2.vb)]

## <a name="collections-as-an-alternative-to-arrays"></a>Kolekce jako alternativa k polím

Pole jsou užitečná pro vytváření a práci s pevným počtem silně typových objektů. Kolekce poskytují pružnější způsob práce se skupinami objektů. Na rozdíl od polí, která vyžadují, abyste explicitně změnili velikost pole [ `ReDim` příkazem](../../../language-reference/statements/redim-statement.md), kolekce se dynamicky zvětšují a zmenšují podle potřeb změny aplikace.

Když použijete `ReDim` k redimenzi pole, Visual Basic vytvoří nové pole a uvolní předchozí. Tím se provede doba provádění. Proto pokud počet položek, se kterými pracujete, často mění nebo nemůžete odhadnout maximální počet položek, které potřebujete, obvykle získáte lepší výkon pomocí kolekce.

U některých kolekcí můžete přiřadit klíč k libovolnému objektu, který vložíte do kolekce, abyste mohli rychle načíst objekt pomocí klíče.

Pokud kolekce obsahuje prvky pouze jednoho typu dat, můžete použít jednu ze tříd v <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů. Obecná kolekce vynutila bezpečnost typů, takže do ní nelze přidat žádný jiný datový typ.

Další informace o kolekcích najdete v tématu [kolekce](../../concepts/collections.md).

## <a name="related-topics"></a>Související témata

|Pojem|Definice|
|----------|----------------|
|[Rozměry pole v jazyce Visual Basic](array-dimensions.md)|Vysvětluje pořadí a dimenze v polích.|
|[Postupy: Inicializace proměnné pole v jazyce Visual Basic](how-to-initialize-an-array-variable.md)|Popisuje, jak naplnit pole počátečními hodnotami.|
|[Postupy: Řazení pole v jazyce Visual Basic](how-to-sort-an-array.md)|Ukazuje, jak seřadit prvky pole abecedně.|
|[Postupy: Přiřazení jednoho pole ke druhému](how-to-assign-one-array-to-another-array.md)|Popisuje pravidla a kroky pro přiřazení pole k jiné proměnné pole.|
|[Řešení potíží s poli](troubleshooting-arrays.md)|Popisuje některé běžné problémy, které vznikají při práci s poli.|

## <a name="see-also"></a>Viz také

- <xref:System.Array?displayProperty=nameWithType>
- [Dim – příkaz](../../../language-reference/statements/dim-statement.md)
- [ReDim – příkaz](../../../language-reference/statements/redim-statement.md)
