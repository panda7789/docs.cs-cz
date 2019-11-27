---
title: Dim – příkaz
ms.date: 05/12/2018
f1_keywords:
- vb.Dim
- Dim
helpviewer_keywords:
- Public keyword [Visual Basic], in Dim statement
- Dim statement [Visual Basic]
- fixed-length strings [Visual Basic], declaring
- variables [Visual Basic], declaring
- WithEvents keyword [Visual Basic], Dim statement
- dynamic arrays [Visual Basic], Dim statement
- variables [Visual Basic], initializing
- '{} braces'
- fields [Visual Basic], as member variables
- declarations [Visual Basic], dynamic arrays
- member variables [Visual Basic]
- default values [Visual Basic]
- data types [Visual Basic], assigning
- braces {}
- As keyword [Visual Basic], in Dim statement
- arrays [Visual Basic], declaring
- New keyword [Visual Basic], Dim statement
- To keyword [Visual Basic], in Dim statement
- storage [Visual Basic], allocating
- local variables [Visual Basic]
- declaration statements [Visual Basic]
- Dim statement [Visual Basic], syntax
- variables [Visual Basic], member and local
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
ms.openlocfilehash: ac66ffdba622673ef42017d147c05b2a2733dede
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343759"
---
# <a name="dim-statement-visual-basic"></a>Dim – příkaz (Visual Basic)

Deklaruje a přiděluje prostor úložiště pro jednu nebo více proměnných.

## <a name="syntax"></a>Syntaxe

```vb
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]
Dim [ WithEvents ] variablelist
```

## <a name="parts"></a>Součásti

- `attributelist`

  Volitelná. Viz [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).

- `accessmodifier`

  Volitelná. Může být jedna z následujících akcí:

  - [Public](../../../visual-basic/language-reference/modifiers/public.md)

  - [Protected](../../../visual-basic/language-reference/modifiers/protected.md)

  - [Friend](../../../visual-basic/language-reference/modifiers/friend.md)

  - [Private](../../../visual-basic/language-reference/modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

  Podívejte [se na úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

- `Shared`

  Volitelná. Viz [Shared](../../../visual-basic/language-reference/modifiers/shared.md).

- `Shadows`

  Volitelná. Viz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).

- `Static`

  Volitelná. Viz [static](../../../visual-basic/language-reference/modifiers/static.md).

- `ReadOnly`

  Volitelná. Zobrazit [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).

- `WithEvents`

Volitelná. Určuje, že se jedná o objektové proměnné, které odkazují na instance třídy, které mohou vyvolat události. Viz [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).

- `variablelist`

  Požadováno. Seznam proměnných, které jsou deklarovány v tomto příkazu.

  `variable [ , variable ... ]`

  Každý `variable` má následující syntaxi a části:

  `variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`

  |Částí|Popis|
  |---|---|
  |`variablename`|Požadováno. Název proměnné Viz [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|
  |`boundslist`|Volitelná. Seznam mezí jednotlivých dimenzí proměnné pole|
  |`New`|Volitelná. Vytvoří novou instanci třídy při spuštění příkazu `Dim`.|
  |`datatype`|Volitelná. Datový typ proměnné|
  |`With`|Volitelná. Zavádí seznam inicializátorů objektů.|
  |`propertyname`|Volitelná. Název vlastnosti ve třídě, pro kterou vytváříte instanci.|
  |`propinitializer`|Vyžadováno po `propertyname` =. Výraz, který je vyhodnocen a přiřazen k názvu vlastnosti.|
  |`initializer`|Volitelné, pokud není zadán `New`. Výraz, který je vyhodnocen a přiřazen k proměnné při jejím vytvoření.|

## <a name="remarks"></a>Poznámky

Kompilátor Visual Basic používá příkaz `Dim` k určení datového typu proměnné a dalších informací, jako je například jaký kód má přístup k proměnné. Následující příklad deklaruje proměnnou pro uchování `Integer` hodnoty.

```vb
Dim numberOfStudents As Integer
```

Můžete zadat libovolný datový typ nebo název výčtu, struktury, třídy nebo rozhraní.

```vb
Dim finished As Boolean
Dim monitorBox As System.Windows.Forms.Form
```

Pro typ odkazu použijete klíčové slovo `New` k vytvoření nové instance třídy nebo struktury, která je určena datovým typem. Použijete-li `New`, nepoužijete výraz inicializátoru. Místo toho zadáte argumenty, pokud jsou požadovány, do konstruktoru třídy, ze které vytváříte proměnnou.

```vb
Dim bottomLabel As New System.Windows.Forms.Label
```

Proměnnou lze deklarovat v proceduře, bloku, třídě, struktuře nebo modulu. Nelze deklarovat proměnnou ve zdrojovém souboru, oboru názvů nebo rozhraní. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

Proměnná deklarovaná na úrovni modulu, mimo jakoukoli proceduru, je *členskou proměnnou* nebo *polem*. Členské proměnné jsou v oboru v rámci své třídy, struktury nebo modulu. Proměnná, která je deklarována na úrovni procedury, je *místní proměnná*. Lokální proměnné jsou v oboru pouze v rámci jejich procedury nebo bloku.

Následující modifikátory přístupu se používají k deklarování proměnných mimo proceduru: `Public`, `Protected`, `Friend`, `Protected Friend`a `Private`. Další informace najdete v tématu [úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

Klíčové slovo `Dim` je nepovinné a obvykle se vynechává, pokud zadáte některý z následujících modifikátorů: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`nebo `WithEvents`.

```vb
Public maximumAllowed As Double
Protected Friend currentUserName As String
Private salary As Decimal
Static runningTotal As Integer
```

Pokud je `Option Explicit` zapnuto (výchozí), kompilátor vyžaduje deklaraci pro každou proměnnou, kterou používáte. Další informace naleznete v tématu [Option Explicit – příkaz](../../../visual-basic/language-reference/statements/option-explicit-statement.md).

## <a name="specifying-an-initial-value"></a>Určení počáteční hodnoty

Můžete přiřadit hodnotu proměnné při jejím vytvoření. Pro typ hodnoty použijete *inicializátor* k zadání výrazu, který má být přiřazen proměnné. Výraz se musí vyhodnotit na konstantu, kterou lze vypočítat v době kompilace.

```vb
Dim quantity As Integer = 10
Dim message As String = "Just started"
```

Pokud je určen inicializátor a datový typ není zadán v klauzuli `As`, je použita *odvození typu* pro odvození datového typu z inicializátoru. V následujícím příkladu jsou `num1` i `num2` silně typované jako celá čísla. Ve druhé deklaraci typu odvození typu odvodí typ z hodnoty 3.

```vb
' Use explicit typing.
Dim num1 As Integer = 3

' Use local type inference.
Dim num2 = 3
```

Odvození typu se vztahuje na úroveň procedury. Nevztahuje se mimo proceduru ve třídě, struktuře, modulu nebo rozhraní. Další informace o odvození typu naleznete v tématu [Option include Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) a [místní typ odvození](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).

Informace o tom, co se stane, když není zadán datový typ nebo inicializátor, naleznete v části [výchozí datové typy a hodnoty](../../../visual-basic/language-reference/statements/dim-statement.md#default) dále v tomto tématu.

Můžete použít *inicializátor objektu* pro deklaraci instancí pojmenovaného a anonymního typu. Následující kód vytvoří instanci třídy `Student` a k inicializaci vlastností používá inicializátor objektu.

```vb
Dim student1 As New Student With {.First = "Michael",
                                  .Last = "Tucker"}
```

Další informace o inicializátorech objektů naleznete v tématu [How to: Declare a Object Using](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)a inicializátor Object, [Inicializátory objektů: pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)a [anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).

## <a name="declaring-multiple-variables"></a>Deklarace více proměnných

Můžete deklarovat několik proměnných v jednom příkazu deklarace, zadat název proměnné pro každý z nich a za každým názvem pole pomocí závorek. Více proměnných je odděleno čárkami.

```vb
Dim lastTime, nextTime, allTimes() As Date
```

Pokud deklarujete více než jednu proměnnou s jednou `As` klauzulí, nemůžete pro tuto skupinu proměnných dodat inicializátor.

Pro každou proměnnou, kterou deklarujete, můžete určit různé typy dat pro různé proměnné pomocí samostatné klauzule `As`. Každá proměnná přebírá datový typ zadaný v první klauzuli `As`, který se objevil po jeho `variablename` část.

```vb
Dim a, b, c As Single, x, y As Double, i As Integer
' a, b, and c are all Single; x and y are both Double
```

## <a name="arrays"></a>Pole

Můžete deklarovat proměnnou pro uchování *pole*, které může obsahovat více hodnot. Chcete-li určit, že proměnná obsahuje pole, postupujte podle `variablename` hned pomocí závorek. Další informace o polích naleznete v tématu [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).

Můžete zadat dolní a horní mez každého rozměru pole. Chcete-li to provést, zahrňte `boundslist` do závorek. Pro každou dimenzi `boundslist` určuje horní mez a volitelně i dolní mez. Dolní mez je vždycky nulová, ať už ji zadáte, nebo ne. Každý index se může od nuly pohybovat od hodnoty horní meze.

Následující dva příkazy jsou ekvivalentní. Každý příkaz deklaruje pole 21 `Integer` prvků. Když přistupujete k poli, index se může lišit od 0 do 20.

```vb
Dim totals(20) As Integer
Dim totals(0 To 20) As Integer
```

Následující příkaz deklaruje dvojrozměrné pole typu `Double`. Pole má 4 řádky (3 + 1) z 6 sloupců (5 + 1). Všimněte si, že horní mez představuje nejvyšší možnou hodnotu indexu, nikoli délku dimenze. Délka dimenze je horní mez plus jedna.

```vb
Dim matrix2(3, 5) As Double
```

Pole může mít 1 až 32 dimenzí.

V deklaraci pole můžete ponechat všechny meze prázdné. Pokud to uděláte, pole má počet dimenzí, které zadáte, ale není inicializovaný. Má hodnotu `Nothing`, dokud neinicializujete alespoň některé z jeho prvků. Příkaz `Dim` musí určovat meze buď pro všechny dimenze, nebo pro žádné dimenze.

```vb
' Declare an array with blank array bounds.
Dim messages() As String
' Initialize the array.
ReDim messages(4)
```

Pokud má pole více než jednu dimenzi, je nutné zahrnout čárky mezi závorky, které označují počet rozměrů.

```vb
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte
```

*Pole s nulovou délkou* můžete deklarovat deklarováním jednoho z dimenzí pole, které je-1. Proměnná, která obsahuje pole s nulovou délkou, nemá hodnotu `Nothing`. Pole s nulovou délkou jsou vyžadovány některými funkcemi modulu CLR (Common Language Runtime). Pokud se pokusíte o přístup k takovému poli, dojde k výjimce modulu runtime. Další informace naleznete v tématu [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).

Hodnoty pole lze inicializovat pomocí literálu pole. Provedete to tak, že tyto inicializační hodnoty uzavřete do složených závorek (`{}`).

```vb
Dim longArray() As Long = {0, 1, 2, 3}
```

Pro multidimenzionální pole je inicializace pro každou samostatnou dimenzi uzavřena do složených závorek ve vnější dimenzi. Prvky jsou uvedeny v pořadí podle hlavní řady.

```vb
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}
```

Další informace o literálech pole naleznete v tématu [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).

## <a name="default"></a>Výchozí datové typy a hodnoty

Následující tabulka popisuje výsledky různých kombinací určení datového typu a inicializátoru v příkazu `Dim`.

|Byl zadán datový typ?|Byl určen inicializátor?|Příklad|Výsledek|
|---|---|---|---|
|Ne|Ne|`Dim qty`|Pokud je [možnost Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) vypnutá (výchozí nastavení), proměnná je nastavená na `Nothing`.<br /><br /> Pokud je `Option Strict` zapnutý, dojde k chybě při kompilaci.|
|Ne|Ano|`Dim qty = 5`|Pokud je nastavená [možnost odvodit](../../../visual-basic/language-reference/statements/option-infer-statement.md) (výchozí), proměnná vezme datový typ inicializátoru. Viz [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Pokud je `Option Infer` vypnuto a `Option Strict` je vypnutý, proměnná převezme datový typ `Object`.<br /><br /> Pokud je `Option Infer` vypnuto a `Option Strict` je zapnutá, dojde k chybě při kompilaci.|
|Ano|Ne|`Dim qty As Integer`|Proměnná je inicializována na výchozí hodnotu pro datový typ. Další informace najdete v tabulce dále v této části.|
|Ano|Ano|`Dim qty  As Integer = 5`|Pokud datový typ inicializátoru nelze převést na zadaný datový typ, dojde k chybě při kompilaci.|

Zadáte-li datový typ, ale nezadáte inicializátor, Visual Basic inicializuje proměnnou na výchozí hodnotu pro svůj datový typ. V následující tabulce jsou uvedeny výchozí inicializační hodnoty.

|Typ dat|Výchozí hodnota|
|---|---|
|Všechny číselné typy (včetně `Byte` a `SByte`)|0|
|`Char`|Binární hodnota 0|
|Všechny typy odkazů (včetně `Object`, `String`a všech polí)|`Nothing`|
|`Boolean`|`False`|
|`Date`|12:00 z 1. ledna v roce 1 (01/01/0001 12:00:00 dop.)|

Každý prvek struktury je inicializován, jako by šlo o samostatnou proměnnou. Pokud deklarujete délku pole, ale neinicializujete jeho prvky, každý prvek je inicializován, jako by šlo o samostatnou proměnnou.

## <a name="static-local-variable-lifetime"></a>Životnost statické lokální proměnné

`Static` místní proměnná má delší dobu života, než je procedura, ve které je deklarována. Hranice životnosti proměnné závisí na tom, kde je procedura deklarována a zda je `Shared`.

|Deklarace procedury|Proměnná inicializovaná|Proměnná zastaví existující.|
|---|---|---|
|V modulu|Při prvním volání procedury|Když váš program zastaví provádění|
|V rámci třídy nebo struktury je procedura `Shared`|Při prvním volání procedury buď na konkrétní instanci, nebo v samotné třídě nebo struktuře|Když váš program zastaví provádění|
|V třídě nebo struktuře není procedura `Shared`|Při prvním volání procedury na konkrétní instanci|Při uvolnění instance pro uvolňování paměti (GC)|

## <a name="attributes-and-modifiers"></a>Atributy a modifikátory

Můžete použít atributy pouze na členské proměnné, nikoli na lokální proměnné. Atribut přispívá k metadatům sestavení, která nejsou smysluplná pro dočasné úložiště, jako jsou místní proměnné.

Na úrovni modulu nemůžete použít modifikátor `Static` k deklaraci proměnných členů. Na úrovni procedury nelze použít `Shared`, `Shadows`, `ReadOnly`, `WithEvents`nebo žádné modifikátory přístupu k deklaraci místních proměnných.

Můžete určit, který kód má přístup k proměnné, zadáním `accessmodifier`. Proměnné členů třídy a modulu (mimo všechny procedury) výchozí pro privátní přístup a proměnné členů struktury jako výchozí pro veřejný přístup. Můžete upravit jejich úrovně přístupu modifikátory přístupu. Modifikátory přístupu nemůžete použít u místních proměnných (uvnitř procedury).

`WithEvents` lze zadat pouze pro členské proměnné, nikoli pro lokální proměnné v rámci procedury. Pokud zadáte `WithEvents`, datový typ proměnné musí být konkrétní typ třídy, ne `Object`. Pole nelze deklarovat pomocí `WithEvents`. Další informace o událostech najdete v tématu [události](../../../visual-basic/programming-guide/language-features/events/index.md).

> [!NOTE]
> Kód mimo třídu, strukturu nebo modul musí kvalifikovat název členské proměnné s názvem této třídy, struktury nebo modulu. Kód mimo proceduru nebo blok nemůže odkazovat na žádné místní proměnné v rámci tohoto postupu nebo bloku.

## <a name="releasing-managed-resources"></a>Uvolňování spravovaných prostředků

Systém uvolňování paměti .NET Framework uvolní spravované prostředky bez jakéhokoli dalšího kódování na vaší straně. Místo toho, abyste čekali na uvolňování paměti, ale můžete vynutit vyřazení spravovaného prostředku.

Pokud třída obsahuje obzvláště cenný a omezených prostředek (například připojení k databázi nebo popisovač souboru), nebudete chtít počkat do dalšího uvolňování paměti, aby se vyčistila instance třídy, která se už nepoužívá. Třída může implementovat rozhraní <xref:System.IDisposable>, aby poskytovala způsob, jak uvolnit prostředky před uvolňováním paměti. Třída, která implementuje toto rozhraní, zpřístupňuje `Dispose` metodu, která může být volána, aby vynutila okamžité vydání cenných prostředků.

Příkaz `Using` automatizuje proces získání prostředku, spuštění sady příkazů a následné likvidaci prostředku. Prostředek však musí implementovat rozhraní <xref:System.IDisposable>. Další informace naleznete v tématu [using – příkaz](../../../visual-basic/language-reference/statements/using-statement.md).

## <a name="example"></a>Příklad

Následující příklad deklaruje proměnné pomocí příkazu `Dim` s různými možnostmi.

[!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]

## <a name="example"></a>Příklad

Následující příklad uvádí hlavní čísla mezi 1 a 30. Rozsah místních proměnných je popsán v komentářích ke kódu.

[!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]

## <a name="example"></a>Příklad

V následujícím příkladu je proměnná `speedValue` deklarována na úrovni třídy. Klíčové slovo `Private` slouží k deklaraci proměnné. K proměnné lze přistupovat jakýmkoli postupem ve třídě `Car`.

[!code-vb[VbVbalrStatements#144](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#144)]

[!code-vb[VbVbalrStatements#145](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#145)]

## <a name="see-also"></a>Viz také:

- [Příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md)
- [Příkaz ReDim](../../../visual-basic/language-reference/statements/redim-statement.md)
- [Příkaz Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Příkaz Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Stránka Kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [Deklarace proměnné](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Pole](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Inicializátory objektů: pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Inicializátory objektů: pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Postupy: Deklarace objektu pomocí inicializátoru objektu](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
