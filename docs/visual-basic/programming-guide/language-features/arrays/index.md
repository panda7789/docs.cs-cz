---
title: Pole v jazyce Visual Basic
ms.date: 12/06/2017
f1_keywords:
  - vb.Array
helpviewer_keywords:
  - 'arrays [Visual Basic]'
  - 'Visual Basic, arrays'
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
---

# <a name="arrays-in-visual-basic"></a>Pole v jazyce Visual Basic

Pole je sada hodnot, které jsou označovány jako *prvky*, která jsou logicky vzájemně souvisí. Například pole může obsahovat počet studentů v každé třídě gymnázia; Každý prvek pole je počet studentů v jedné na podnikové úrovni. Podobně může obsahovat pole student získal známek pro třídy; Každý prvek pole je jeden na podnikové úrovni.

Je možné jednotlivé proměnné pro uložení všech našich datových položek. Například pokud aplikace analyzuje známek studentů, můžeme použít samostatná proměnná pro každého studenta, jako například `englishGrade1`, `englishGrade2`atd. Tento přístup má tři hlavní omezení:

- Máme vědět v době návrhu přesně kolik známek máme ke zpracování.
- Zpracování velkého počtu tříd rychle nepraktický. Díky tomu aplikace mnohem větší pravděpodobností mít závažné chyby.
- Je obtížné udržovat. Každý nový na podnikové úrovni, které přidáme vyžaduje, že aplikace se změnil, znovu zkompilovat a znovu nasadit.

Pomocí pole můžete odkazovat na tyto související hodnoty se stejným názvem a použít číslo, která je volána *index* nebo *dolní index* k identifikaci jednotlivý element podle jeho pozice v poli. Indexy pole rozsahu od 0 do jednoho nižší než celkový počet prvků v poli. Při použití syntaxe jazyka Visual Basic pro definování velikosti pole zadáte její nejvyšší index není celkový počet prvků v poli. Můžete pracovat s pole jako celek, a možnost iterovat jeho prvky díky které nepotřebuje vědět přesně počet prvků, obsahuje v době návrhu.

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

## <a name="array-elements-in-a-simple-array"></a>Prvky pole v jednoduchém poli

Pojďme vytvořit pole s názvem `students` k ukládání počtu studentů z každého stupně ve škole gramatiky. Indexy prvků v rozsahu od 0 do 6. Pomocí tohoto pole je jednodušší než deklarování sedmi proměnných.

Je vidět na následujícím obrázku `students` pole. Pro každý prvek pole:

- Index prvku představuje stupeň (index 0 představuje mateřské školy).

- Hodnota, která je obsažena v elementu představuje počet studentů v této platové třídě.

![Diagram znázorňující, bude pole čísel studentů](./media/index/students-array-elements.gif)

Následující příklad obsahuje kód jazyka Visual Basic, které vytváří a používá pole:

[!code-vb[simple-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/simple-array.vb)]

V příkladu dělá tři věci:

- Deklaruje `students` pole sedm prvků. Číslo `6` v poli prohlášení znamená poslední index v poli; jeden je menší než počet prvků v poli.
- Přiřadí hodnoty ke každému prvku v poli. Prvky pole jsou přístupné pomocí názvu pole a včetně index jednotlivý element v závorkách.
- Uvádí každou hodnotu pole. V příkladu se používá [ `For` ](../../../language-reference/statements/for-next-statement.md) příkaz pro přístup k každý prvek pole pomocí čísla indexu.

`students` Pole v předchozím příkladu je jednorozměrné pole, protože používá jeden index. Pole, která používá více než jeden index nebo dolní index, se nazývá *multidimenzionální*. Další informace najdete v tématu zbývající část tohoto článku a [rozměry pole v jazyce Visual Basic](../../language-features/arrays/array-dimensions.md).

## <a name="creating-an-array"></a>Vytvoření pole

Můžete definovat velikost pole několika způsoby:

- Při deklaraci pole můžete zadat velikost:

  [!code-vb[creating1](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#1)]

- Můžete použít `New` klauzule k zadání velikosti pole při jeho vytváření:

  [!code-vb[creating2](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#2)]

Pokud máte existující pole, můžete změnit jeho velikost pomocí [ `ReDim` ](../../../language-reference/statements/redim-statement.md) příkazu. Můžete určit, že `ReDim` příkaz zachovat hodnoty, které jsou v poli, nebo můžete určit, že vytvoří prázdné pole. Následující příklad ukazuje různá použití `ReDim` příkaz pro úpravu velikosti existujícího pole.

[!code-vb[redimensioning](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#3)]

Další informace najdete v tématu [ReDim – příkaz](../../../language-reference/statements/redim-statement.md).

## <a name="storing-values-in-an-array"></a>Ukládání hodnot v poli

Každé umístění v poli můžete přistupovat pomocí indexu typu `Integer`. Můžete ukládat a načítat hodnoty v matici odkazováním na umístění jednotlivých polí pomocí indexu uvedeného v závorkách. Indexy pro vícerozměrná pole jsou odděleny čárkami (,). Budete potřebovat jeden index pro každou dimenzi pole.

Následující příklad ukazuje některé příkazy, které ukládat a načítat hodnoty v polích.

[!code-vb[store-and-retrieve](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/store-and-retrieve.vb)]

## <a name="populating-an-array-with-array-literals"></a>Vyplnění pole pomocí literálů pole

Pomocí literálového pole, která můžete naplnit pole s počáteční sadu hodnot ve stejnou dobu, kterou vytvoříte. Literál pole obsahuje seznam hodnot oddělených čárkami, které jsou uzavřeny ve složených závorkách (`{}`).

Při vytváření pole pomocí literálu pole můžete zadat typ pole nebo typ pole můžete určit pomocí odvození typu proměnné. Následující příklad ukazuje obě možnosti.

[!code-vb[create-with-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#4)]

Při použití odvození typu proměnné typu pole závisí *dominantní typ* v seznamu hodnot literálů. Dominantní typ je typ, ke kterému lze rozšířit všechny ostatní typy jako pole. Pokud nelze určit tento jedinečný typ, dominantní typ je jedinečný typ, do kterého můžete zúžit všechny typy v poli. Pokud ani jeden z těchto jedinečných typů nelze určit, dominantní typ je `Object`. Například, pokud seznam hodnot, který je zadaný pro literál pole obsahuje hodnoty typu `Integer`, `Long`, a `Double`, výsledné pole je typu `Double`. Protože `Integer` a `Long` rozšiřují pouze na `Double`, `Double` dominantní typ je. Další informace najdete v tématu [Widening a zúžení převodů](../../language-features/data-types/widening-and-narrowing-conversions.md).

> [!NOTE]
> Odvození typu můžete použít pouze pro pole, které jsou definovány jako lokální proměnné v člena typu. Pokud chybí definice explicitního typu, pole definované pomocí literály pole na úrovni třídy jsou typu `Object[]`. Další informace najdete v tématu [odvození místního typu](../variables/local-type-inference.md).

Všimněte si, že v předchozím příkladu je definována `values` jako pole typu `Double` i když jsou všechny literály pole typu `Integer`. Toto pole můžete vytvořit, protože můžou hodnoty v poli literálu rozšířit na `Double` hodnoty.

Můžete také vytvořit a naplnit vícedimenzionální pole pomocí *vnořené literály pole*. Literály vnořeného pole musí mít počet rozměrů, která je kompatibilní s výsledným polem. Následující příklad vytvoří dvourozměrné pole celých čísel pomocí literál vnořeného pole.

[!code-vb[nested-array-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#5)]

Když vytvořit a naplnit pole pomocí literál vnořeného pole, dojde k chybě, pokud počet prvků v literálech vnořeného pole, které se neshodují. Pokud explicitně deklarujete proměnnou pole mají různý počet rozměrů než literály pole také dojde k chybě.

Stejně jako pro jednorozměrné pole, můžete se spolehnout na odvození typu při vytváření vícedimenzionálního pole pomocí literál vnořeného pole. Je odvozený typ dominantní typ pro všechny hodnoty ve všech literálech pole pro všechny úrovně vnoření. Následující příklad vytvoří dvourozměrné pole typu `Double[,]` z hodnot, které jsou typu `Integer` a `Double`.

[!code-vb[nested-type-inference](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#6)]

Další příklady najdete v tématu [jak: Inicializace proměnné pole v jazyce Visual Basic](../../language-features/arrays/how-to-initialize-an-array-variable.md).

## <a name="iterating-through-an-array"></a>Procházení skrze pole

Při iteraci pole máte přístup každý prvek v poli od nejnižšího indexu k nejvyšší nebo z nejvyšší k nejnižší. Obvykle, použijte buď [pro... Další příkaz](../../../language-reference/statements/for-next-statement.md) nebo [For Each... Další příkaz](../../../language-reference/statements/for-each-next-statement.md) k iteraci v rámci prvků pole. Pokud si nejste jisti horní mez pole, můžete volat <xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType> metodu k získání nejvyšší hodnotě indexu. I když nejnižší hodnota indexu je téměř vždy 0, můžete volat <xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType> metodu k získání nejnižší hodnota indexu.

Následující příklad provede iteraci jednorozměrového pole použitím [ `For...Next` ](../../../language-reference/statements/for-next-statement.md) příkazu.

[!code-vb[iterate-one-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate1d.vb)]

Následující příklad provede iteraci multidimenzionálního pole použitím [ `For...Next` ](../../../language-reference/statements/for-next-statement.md) příkazu. <xref:System.Array.GetUpperBound%2A> Metoda má parametr, který určuje dimenzi. `GetUpperBound(0)` Vrátí nejvyšší index prvního rozměru a `GetUpperBound(1)` vrátí nejvyšší index druhého rozměru.

[!code-vb[iterate-two-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate2d.vb)]

Následující příklad používá [For Each... Další příkaz](../../../language-reference/statements/for-each-next-statement.md)pro iteraci jednorozměrového pole a dvourozměrné pole.

[!code-vb[iterate-for-each-next](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate-for-each-next.vb)]

## <a name="array-size"></a>Velikost pole

Velikost pole je produktem délek všech jeho rozměrů. Představuje celkový počet prvků, které jsou aktuálně obsaženy v poli.  Například následující příklad deklaruje 2rozměrné pole čtyřech prvcích v každém rozměru. Jak výstup z příkladu ukazuje, velikost tohoto pole je 16 (nebo (3 + 1) * (3 + 1).

[!code-vb[array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size.vb)]

> [!NOTE]
> Tato diskuse o velikosti pole se nevztahují na Vícenásobná pole. Informace o Vícenásobná pole a určování velikosti vícenásobného pole, najdete v článku [Vícenásobná pole](#jagged-arrays) oddílu.

Velikost pole můžete najít pomocí <xref:System.Array.Length%2A?displayProperty=nameWithType> vlastnost. Délka každé dimenze vícerozměrného pole můžete najít pomocí <xref:System.Array.GetLength%2A?displayProperty=nameWithType> metody.

Pomocí přiřazení nového objektu pole do něj nebo můžete změnit velikost proměnné pole [ `ReDim` příkaz](../../../language-reference/statements/redim-statement.md) příkazu. V následujícím příkladu `ReDim` příkaz Změnit 100 elementu pole na pole 51 elementu.

[!code-vb[resize-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size2.vb)]

Mějte na paměti při zpracování komplexnějších velikost pole několika způsoby.

|||
|---|---|
|Délka dimenze|Index každé dimenze je založen na 0, což znamená, že má že rozsah od 0 do horní mez. Délka dané dimenze je proto jeden stupeň větší než deklarovaná horní mez dané dimenzi.|
|Omezení délky|Délka každé dimenze pole je omezená na maximální hodnotu `Integer` datového typu, který je <xref:System.Int32.MaxValue?displayProperty=nameWithType> nebo (2 ^ 31) + 1. Celková velikost pole je také omezena pamětí, které jsou k dispozici ve vašem systému. Při pokusu o inicializaci pole, který překračuje množství dostupné paměti, modul runtime vyvolá výjimku <xref:System.OutOfMemoryException>.|
|Velikost a velikost elementu|Velikost tohoto pole je nezávislé na typu dat jeho elementů. Velikost vždy představuje celkový počet prvků, nikoli počet bajtů, které spotřebovávají v paměti.|
|Využití paměti|Není bezpečné nevyvozujte předpoklady o tom, jak je pole uloženo v paměti. Skladování závisí na platformách s různou šířkou dat, takže stejné pole může spotřebovávat více paměti na 64bitovou verzi systému než v 32bitové verzi systému. V závislosti na konfiguraci systému při inicializaci pole, modul CLR (CLR) může přiřadit úložiště zabalil elementy co co nejblíže k sobě nebo je zarovnal na hranice fyzických hardwarových vazeb. Také pole vyžaduje režii úložiště pro informace o jeho ovládacího prvku a tato režie se zvyšuje s každou přidanou dimenzi.|

## <a name="the-array-type"></a>Typ pole

Každé pole má datový typ, který se liší od typu dat jeho elementů. Neexistuje žádný jednotlivý typ dat pro všechna pole. Místo toho je určen datový typ pole podle počtu rozměrů, nebo *pořadí*, pole a datový typ prvků v poli. Dvě proměnné pole se stejný datový typ, pouze pokud mají stejné pořadí a jejich elementy mají stejný datový typ. Délky dimenzí v poli neovlivňují datový typ pole.

Každé pole dědí z <xref:System.Array?displayProperty=nameWithType> třídy a můžete deklarovat proměnnou typu `Array`, ale nemůžete vytvořit pole typu `Array`. Například i když následující kód deklaruje `arr` proměnnou typu `Array` a volá <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metoda pro vytvoření instance pole, typ pole ukáže Object [].

[!code-vb[array-class](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-class.vb)]

Také [ReDim – příkaz](../../../language-reference/statements/redim-statement.md) nejde použít pro proměnné deklarované jako typ `Array`. Z těchto důvodů a pro bezpečnost typů je vhodné deklarovat každé pole jako specifického typu.

Můžete zjistit datový typ pole nebo jeho prvky několika způsoby.

- Můžete volat <xref:System.Object.GetType%2A> metoda v proměnné k získání <xref:System.Type> objekt, který reprezentuje za běhu typ proměnné. <xref:System.Type> Objekt obsahuje rozsáhlé informace ve vlastnostech a metodách.
- Můžete předat proměnnou <xref:Microsoft.VisualBasic.Information.TypeName%2A> funkce získáte `String` s názvem typu za běhu.

Následující příklad volá obě `GetType` metoda a `TypeName` funkce určit typ pole. Typ pole je `Byte(,)`. Všimněte si, že <xref:System.Type.BaseType%2A?displayProperty=nameWithType> vlastnost také určuje, že je základní typ pole bajtů <xref:System.Array> třídy.

[!code-vb[array-type](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-type.vb)]

## <a name="arrays-as-return-values-and-parameters"></a>Pole jako návratové hodnoty a parametry

Chcete-li vrátit pole z `Function` postupu, zadejte datový typ pole a počet dimenzí jako návratový typ [Function – příkaz](../../../language-reference/statements/function-statement.md). V rámci této funkce deklarujte místní proměnnou pole se stejným datovým typem a počtem dimenzí. V [příkaz Return](../../../language-reference/statements/return-statement.md), zahrnují proměnnou místního pole bez závorek.

Chcete-li určit pole jako parametr `Sub` nebo `Function` postupu, definujte parametr jako pole se zadaným datovým polem a počtem dimenzí. Ve volání do procedury předejte proměnnou pole se stejný datový typ a počet rozměrů.

V následujícím příkladu `GetNumbers` vrací funkce `Integer()`, jednorozměrné pole typu `Integer`. `ShowNumbers` Procedury přijímá `Integer()` argument.

[!code-vb[return-value-and-params](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params.vb)]

V následujícím příkladu `GetNumbersMultiDim` vrací funkce `Integer(,)`, dvourozměrné pole typu `Integer`.  `ShowNumbersMultiDim` Procedury přijímá `Integer(,)` argument.

[!code-vb[multidimensional-return-value](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params-2d.vb)]

## <a name="jagged-arrays"></a>Vícenásobná pole

Struktura dat v aplikaci je někdy dvourozměrná, ale nemá tvar obdélníku. Například můžete použít pole k ukládání dat o nejvyšší teplota každý den v měsíci. První rozměr pole představuje měsíc, ale druhého rozměru představuje počet dní, a počet dní v měsíci není jednotné. A *vícenásobného pole*, což se označuje taky jako *pole polí*, je určen pro takové scénáře. Vícenásobné pole je pole, jehož prvky jsou také pole. Vícenásobné pole a každý prvek ve vícenásobném poli může mít jednu nebo více dimenzí.

Následující příklad používá celou řadu měsíců, jejichž každým prvkem je pole dnů. V příkladu používá vícenásobné pole, vzhledem k tomu, že různé měsíce mají různý počet dnů.  Tento příklad ukazuje, jak vytvořit vícenásobného pole, přiřadit hodnoty, načíst a zobrazit jeho hodnoty.

[!code-vb[jagged-arrays](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged.vb)]

Předchozí příklad přiřazuje hodnoty vícenásobného pole na základě prvek po prvku pomocí `For...Next` smyčky. Můžete také přiřadit hodnoty prvků vícenásobného pole pomocí literál vnořeného pole. Ale pokusem o použití vnořené literály pole (například `Dim valuesjagged = {{1, 2}, {2, 3, 4}}`) vygeneruje Chyba kompilátoru [BC30568](../../../,,/../misc/bc30568.md). Chcete-li opravit chybu, uzavřete literál vnitřní pole do závorek. Závorky vynutí vyhodnocení literálního výrazu pole a výsledné hodnoty se používají u vnějšího literálu, pole, jak ukazuje následující příklad.

[!code-vb[jagged-array-initialization](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-assign.vb)]

Vícenásobné pole je jednorozměrné pole, jehož prvky obsahovat pole. Proto <xref:System.Array.Length%2A?displayProperty=nameWithType> vlastnost a `Array.GetLength(0)` metoda vrátí počet prvků v jednorozměrné pole, a `Array.GetLength(1)` vyvolá <xref:System.IndexOutOfRangeException> protože vícenásobného pole není multidimenzionální. Určení počtu prvků v každé podpole načtením hodnoty jednotlivých podpole <xref:System.Array.Length%2A?displayProperty=nameWithType> vlastnost. Následující příklad ukazuje, jak určit počet prvků ve vícenásobném poli.

[!code-vb[jagged-array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-length.vb)]

## <a name="zero-length-arrays"></a>Pole nulové délky

Visual Basic rozlišuje mezi neinicializované pole (pole, jehož hodnota je `Nothing`) a *pole nulové délky* nebo prázdné pole (pole, které neobsahuje žádné prvky.) Neinicializované pole je ten, který nebyl byla dimenzovanými nebo k němu přidělili žádné hodnoty. Příklad:

```vb
Dim arr() As String
```

Pole s nulovou délkou je deklarována s rozměrem-1. Příklad:

```vb
Dim arrZ(-1) As String
```

Můžete potřebovat vytvořit pole nulové délky za následujících okolností:

- Bez riskování <xref:System.NullReferenceException> výjimky, váš kód musí přístup ke členům <xref:System.Array> třídy, jako například <xref:System.Array.Length%2A> nebo <xref:System.Array.Rank%2A>, nebo zavolat funkci jazyka Visual Basic jako <xref:Microsoft.VisualBasic.Information.UBound%2A>.

- Chcete pro zjednodušení kódu tím, že ke kontrole `Nothing` jako speciální případ.

- Kód spolupracuje s programovací rozhraním aplikace (API), vyžaduje předání pole nulové délky do jednoho nebo více postupů nebo vrátí pole nulové délky z jednoho nebo více postupů.

## <a name="splitting-an-array"></a>Rozdělení pole

V některých případech můžete rozdělit do několika polí jedno pole. To zahrnuje identifikaci bodu nebo bodů, na kterých je možné rozdělit pole a potom plivání pole do dvou nebo více samostatných polích.

> [!NOTE]
> Tato část neobsahuje informace o rozdělení jeden řetězec do pole řetězců na základě některých oddělovače. Informace o řetězec, najdete v článku <xref:System.String.Split%2A?displayProperty=nameWithType> metody.

Nejběžnější kritéria pro rozdělení pole jsou:

- Počet prvků v poli. Můžete například chtít rozdělit pole větší než zadaný počet prvků na počet přibližně stejné části. K tomuto účelu můžete použít hodnotu vrácenou příkazem buď <xref:System.Array.Length%2A?displayProperty=nameWithType> nebo <xref:System.Array.GetLength%2A?displayProperty=nameWithType> metody.

- Hodnota elementu, který slouží jako oddělovač, který označuje, kde by měl rozdělit pole. Můžete vyhledat určitou hodnotu při volání <xref:System.Array.FindIndex%2A?displayProperty=nameWithType> a <xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType> metody.

Jakmile potvrdíte, index nebo indexů, na kterých je rozdělit pole, potom můžete vytvořit jednotlivé pole voláním <xref:System.Array.Copy%2A?displayProperty=nameWithType> metody.

V následujícím příkladu se rozdělí pole do dvou polí přibližně stejnou velikost. (Pokud celkový počet prvků pole je liché, první pole má jeden prvek více než druhý.)

[!code-vb[splitting-an-array-by-length](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split1.vb)]

Následující příklad rozdělí dvě pole, podle přítomnosti element, jehož hodnota je "zzz", která slouží jako oddělovač pole řetězců. Nové pole nezahrnují elementu, který obsahuje oddělovač.

[!code-vb[splitting-an-array-by-delimiter](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split2.vb)]

## <a name="joining-arrays"></a>Připojení k poli

Můžete také kombinovat několik polí do jediného větší pole. K tomuto účelu můžete také použít <xref:System.Array.Copy%2A?displayProperty=nameWithType> metody.

> [!NOTE]
> Tato část neobsahuje informace o spojování pole řetězců do jednoho řetězce. Informace o spojování pole řetězců, najdete v článku <xref:System.String.Join%2A?displayProperty=nameWithType> metody.

Před kopírováním prvky jednotlivá pole do nového pole, je nutné nejdříve zkontrolovat, že jste inicializovali pole tak, aby je dostatečně velký, aby vyhovoval nové pole. Toto lze provést jedním ze dvou způsobů:

- Použití [ `ReDim Preserve` ](../../../language-reference/statements/redim-statement.md) příkaz dynamicky rozbalte pole před přidáním nových elementů do něj. Toto je nejjednodušší postup, ale může způsobit snížení výkonu a využití využívala příliš mnoho paměti při kopírování velké pole.
- Vypočítá celkový počet prvků, které jsou potřebné pro nové velké pole a potom k němu přidat prvky pole každý zdroj.

Druhý přístup k přidání čtyř polí s deset prvky jedno pole v následujícím příkladu.

[!code-vb[joining-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join.vb)]

Protože zdrojové pole v tomto případě jsou všechny malé, jsme také dynamicky rozbalte pole, protože budeme přidávat prvky každé nové pole do něj. Následující příklad činí.

[!code-vb[joining-an-array-dynamically](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join2.vb)]

## <a name="collections-as-an-alternative-to-arrays"></a>Kolekce jako alternativa k polím

Pole jsou zvláště užitečná pro vytváření a práci s pevným počtem silně typované objekty. Kolekce poskytují pružnější způsob práce se skupinami objektů. Na rozdíl od pole, které vyžadují explicitně změnit velikost pole [ `ReDim` příkaz](../../../language-reference/statements/redim-statement.md), kolekce zvětšení a zmenšení dynamicky podle potřeb aplikace mění.

Při použití `ReDim` redimension pole, Visual Basic vytvoří nové pole a uvolní předchozí. Zabírá to čas spuštění. Proto pokud počet položek, které pracujete často mění, nebo nelze předvídat maximální počet položek, které potřebujete, budete obvykle získáte lepší výkon pomocí kolekce.

Pro některé kolekce můžete přiřadit klíč na libovolný objekt, který vložíte do kolekce, takže můžete snadno obnovit objekt pomocí klíče.

Pokud kolekce obsahuje prvky pouze jednoho datového typu, můžete použít jednu z tříd v <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů. Obecná kolekce vynucuje bezpečnost typů tak, aby žádný jiný typ dat můžete do ní přidá.

Další informace o kolekcích najdete v tématu [kolekce](../../concepts/collections.md).

## <a name="related-topics"></a>Související témata

|Termín|Definice|
|----------|----------------|
|[Rozměry pole v jazyce Visual Basic](../../language-features/arrays/array-dimensions.md)|Popisuje pořadí a rozměry v polích.|
|[Postupy: Inicializace proměnné pole v jazyce Visual Basic](../../language-features/arrays/how-to-initialize-an-array-variable.md)|Popisuje, jak naplnit pole počátečními hodnotami.|
|[Postupy: Řazení pole v jazyce Visual Basic](../../language-features/arrays/how-to-sort-an-array.md)|Ukazuje, jak prvky pole seřadit podle abecedy.|
|[Postupy: Přiřazení jednoho pole ke druhému](../../language-features/arrays/how-to-assign-one-array-to-another-array.md)|Popisuje pravidla a postup pro přiřazení pole do jiné proměnné pole.|
|[Řešení potíží s poli](../../language-features/arrays/troubleshooting-arrays.md)|Tento článek popisuje některé běžné problémy, které vznikají při práci s poli.|

## <a name="see-also"></a>Viz také:

- <xref:System.Array?displayProperty=nameWithType>
- [Příkaz Dim](../../../language-reference/statements/dim-statement.md)
- [Příkaz ReDim](../../../language-reference/statements/redim-statement.md)
