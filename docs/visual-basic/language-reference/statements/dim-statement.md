---
title: Dim – příkaz (Visual Basic)
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
ms.openlocfilehash: 5a16060efc45cc0642aa6612d02644e252cd53d9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751792"
---
# <a name="dim-statement-visual-basic"></a>Dim – příkaz (Visual Basic)

Deklaruje a přiděluje místo pro jednu nebo více proměnných.

## <a name="syntax"></a>Syntaxe

```
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]
Dim [ WithEvents ] variablelist
```

## <a name="parts"></a>Součásti

- `attributelist`

  Volitelné. Zobrazit [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).

- `accessmodifier`

  Volitelné. Může být jedna z následujících akcí:

  - [Public](../../../visual-basic/language-reference/modifiers/public.md)

  - [Protected](../../../visual-basic/language-reference/modifiers/protected.md)

  - [Friend](../../../visual-basic/language-reference/modifiers/friend.md)

  - [Private](../../../visual-basic/language-reference/modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

  Zobrazit [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

- `Shared`

  Volitelné. Zobrazit [sdílené](../../../visual-basic/language-reference/modifiers/shared.md).

- `Shadows`

  Volitelné. Zobrazit [stíny](../../../visual-basic/language-reference/modifiers/shadows.md).

- `Static`

  Volitelné. Zobrazit [statické](../../../visual-basic/language-reference/modifiers/static.md).

- `ReadOnly`

  Volitelné. Zobrazit [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).

- `WithEvents`

Volitelné. Určuje, že jde o objektových proměnných, které odkazují na instance třídy, která může vyvolat události. Zobrazit [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).

- `variablelist`

  Povinný parametr. Seznam proměnných, které jsou deklarované v tomto prohlášení.

  `variable [ , variable ... ]`

  Každý `variable` má následující syntaxi a části:

  `variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`

  |Část|Popis|
  |---|---|
  |`variablename`|Povinný parametr. Název proměnné. Zobrazit [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|
  |`boundslist`|Volitelné. Seznam mezí jednotlivých rozměrů proměnné pole.|
  |`New`|Volitelné. Vytvoří novou instanci třídy, když `Dim` spuštění příkazu.|
  |`datatype`|Volitelné. Datový typ proměnné.|
  |`With`|Volitelné. Představuje seznam inicializátorů objektů.|
  |`propertyname`|Volitelné. Název vlastnosti ve třídě provádíte instance.|
  |`propinitializer`|Opakovaným načtením vyžadovaným po `propertyname` =. Výraz, který je vyhodnocen a přiřazen název vlastnosti.|
  |`initializer`|Nepovinné, pokud `New` není zadán. Výraz, který je vyhodnocen a přiřazen do proměnné při jeho vytvoření.|

## <a name="remarks"></a>Poznámky

Kompilátor jazyka Visual Basic používá `Dim` příkaz k určení proměnné datový typ a další informace, jako je například jaké kód může přistupovat k proměnné. Následující příklad deklaruje proměnnou pro uchování `Integer` hodnotu.

```vb
Dim numberOfStudents As Integer
```

Můžete zadat libovolný datový typ nebo název výčtu, strukturu, třídu nebo rozhraní.

```vb
Dim finished As Boolean
Dim monitorBox As System.Windows.Forms.Form
```

Pro typ odkazu, je použít `New` – klíčové slovo chcete vytvořit novou instanci třídy nebo struktury, která je určená datového typu. Pokud používáte `New`, je velmi riskantní používat inicializační výraz. Místo toho zadáte argumenty, pokud jsou požadována pro konstruktor třídy, ve kterém vytvoříte proměnnou.

```vb
Dim bottomLabel As New System.Windows.Forms.Label
```

Můžete deklarovat proměnnou v postupu, blok, třídy, struktury nebo modulu. Nelze deklarovat proměnnou ve zdrojovém souboru, obor názvů nebo rozhraní. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

Proměnná, která je deklarována na úrovni modulu mimo všechny procedury, je *členskou proměnnou* nebo *pole*. Členské proměnné jsou v oboru v celém jejich třídy, struktury nebo modulu. Proměnná, která je deklarována v úroveň procedury je *lokální proměnná*. Lokální proměnné jsou v rozsahu pouze v rámci jejich proceduru nebo blok.

Následující modifikátory přístupu slouží k deklaraci proměnné mimo proceduru: `Public`, `Protected`, `Friend`, `Protected Friend`, a `Private`. Další informace najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

`Dim` – Klíčové slovo je volitelný a obvykle vynechána, pokud je zadána některá z následujících parametrů: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, nebo `WithEvents`.

```vb
Public maximumAllowed As Double
Protected Friend currentUserName As String
Private salary As Decimal
Static runningTotal As Integer
```

Pokud `Option Explicit` je zapnuto (výchozí), kompilátor vyžaduje deklaraci pro každou proměnnou můžete použít. Další informace najdete v tématu [Option Explicit – příkaz](../../../visual-basic/language-reference/statements/option-explicit-statement.md).

## <a name="specifying-an-initial-value"></a>Určení počáteční hodnoty

Přiřadit hodnotu k proměnné při jeho vytvoření. Pro typ hodnoty, použijete *inicializátor* zadat výraz přiřazovaný proměnné. Výraz se musí vyhodnotit na konstantu, která lze vypočítat v době kompilace.

```vb
Dim quantity As Integer = 10
Dim message As String = "Just started"
```

Pokud je zadán inicializátor a není zadaný datový typ v `As` klauzule *odvození typu* je použít k odvození typu dat z inicializátoru. V následujícím příkladu obě `num1` a `num2` jsou silného typu jako celá čísla. V deklaraci druhý odvození typu odvodí typ z hodnotu 3.

```vb
' Use explicit typing.
Dim num1 As Integer = 3

' Use local type inference.
Dim num2 = 3
```

Odvození typu proměnné se vztahuje na úrovni postup. Nevztahuje se mimo proceduru v třída, struktura, modul nebo rozhraní. Další informace o odvození typu, najdete v části [Option Infer – příkaz](../../../visual-basic/language-reference/statements/option-infer-statement.md) a [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).

Informace o tom, co se stane, když není zadaný datový typ nebo inicializační procedury, naleznete v tématu [výchozí datové typy a hodnoty](../../../visual-basic/language-reference/statements/dim-statement.md#default) dále v tomto tématu.

Můžete použít *objektu inicializátoru* deklarovat výskyty pojmenované a anonymní typy. Následující kód vytvoří instanci `Student` třídy a pomocí inicializátoru objektu inicializovat vlastnosti.

```vb
Dim student1 As New Student With {.First = "Michael",
                                  .Last = "Tucker"}
```

Další informace o inicializátory objektů najdete v tématu [jak: Deklarace objektu pomocí inicializátoru objektu](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [inicializátorech objektu: Pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), a [anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).

## <a name="declaring-multiple-variables"></a>Deklarování více proměnných

Je možné deklarovat několik proměnných v příkazu jednu deklaraci, zadáte název proměnné pro každé z nich a po každé pole názvu v závorkách. Více proměnných jsou odděleny čárkami.

```vb
Dim lastTime, nextTime, allTimes() As Date
```

Je-li deklarována více než jednu proměnnou na jednu `As` klauzule, nelze zadat inicializátor pro tuto skupinu proměnných.

Různé datové typy pro různé proměnné můžete určit pomocí samostatné `As` klauzuli pro každou proměnnou můžete deklarovat. Každá proměnná má datový typ zadaný v prvním `As` klauzule došlo po jeho `variablename` část.

```vb
Dim a, b, c As Single, x, y As Double, i As Integer
' a, b, and c are all Single; x and y are both Double
```

## <a name="arrays"></a>Pole

Můžete deklarovat proměnnou pro uchování *pole*, který může obsahovat více hodnot. Chcete-li určit, že proměnná obsahuje pole, postupujte podle jeho `variablename` okamžitě se závorkami. Další informace o polích naleznete v tématu [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).

Můžete zadat dolní a horní mez každé dimenze matice. Chcete-li to provést, patří `boundslist` v závorkách. Pro každou dimenzi `boundslist` Určuje horní mez a volitelně dolní mez. Dolní mez, je vždy nula, a zda ho zadáte nebo ne. Každý index se může lišit od nuly prostřednictvím její hodnotu horní mez.

Následující dva příkazy jsou ekvivalentní. Každý příkaz deklaruje pole 21 `Integer` elementy. Při přístupu k poli, index se může lišit od 0 do 20.

```vb
Dim totals(20) As Integer
Dim totals(0 To 20) As Integer
```

Následující příkaz deklaruje dvourozměrné pole typu `Double`. Pole má 6 sloupců (5 + 1) každé 4 řádky (3 + 1). Všimněte si, že horní mez představuje nejvyšší možnou hodnotu pro index, nikoli velikost rozměru. Délka druhého rozměru je horní mez plus jedna.

```vb
Dim matrix2(3, 5) As Double
```

Pole může mít 1 až 32 rozměrů.

Můžete ponechat všechny hranice v deklaraci pole prázdné. Pokud to uděláte, pole má počet dimenzí, které zadáte, ale není inicializován. Má hodnotu `Nothing` dokud inicializovat alespoň některé z jeho prvků. `Dim` Příkaz musí určovat hranice pro všechny dimenze nebo žádné dimenze.

```vb
' Declare an array with blank array bounds.
Dim messages() As String
' Initialize the array.
ReDim messages(4)
```

Pokud pole má více než jednou dimenzí, je nutné zahrnout čárek mezi závorky k označení počet rozměrů.

```vb
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte
```

Je možné deklarovat *pole nulové délky* deklarováním jeden z rozměrů pole jako hodnotu-1. Proměnná, která obsahuje pole s nulovou délkou nemá hodnotu `Nothing`. Některé běžné funkce modulu runtime jazyka vyžaduje pole nulové délky. Pokud se pokusíte o přístup k takové pole, dojde k výjimce modulu runtime. Další informace najdete v tématu [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).

Inicializovat hodnoty pole pomocí literálu pole. K tomuto účelu před a za inicializace hodnoty se závorkami (`{}`).

```vb
Dim longArray() As Long = {0, 1, 2, 3}
```

Pro vícerozměrná pole je inicializace pro každou samostatnou dimenzi uzavřeny ve složených závorkách v vnější dimenzi. Prvky jsou uvedeny v pořadí preferujícím řádek.

```vb
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}
```

Další informace o literály pole, naleznete v tématu [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).

## <a name="default"></a> Výchozí datové typy a hodnoty

Následující tabulka popisuje výsledky různých kombinací určující typ dat a obsahuje inicializační proceduru `Dim` příkazu.

|Zadaný datový typ?|Inicializátor zadaný?|Příklad|Výsledek|
|---|---|---|---|
|Ne|Ne|`Dim qty`|Pokud [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) je vypnuto (výchozí), je proměnná nastavena `Nothing`.<br /><br /> Pokud `Option Strict` zapnutý, dojde k chybě kompilace.|
|Ne|Ano|`Dim qty = 5`|Pokud [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) je zapnuto (výchozí), zadejte proměnné přijímá data z inicializátoru. Zobrazit [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Pokud `Option Infer` je vypnuté a `Option Strict` je vypnuté, nabývá datový typ `Object`.<br /><br /> Pokud `Option Infer` je vypnuté a `Option Strict` zapnutý, dojde k chybě kompilace.|
|Ano|Ne|`Dim qty As Integer`|Proměnná je inicializována na výchozí hodnotu pro typ dat. V tabulce dále v tomto oddílu.|
|Ano|Ano|`Dim qty  As Integer = 5`|Pokud datový typ inicializátor není lze převést na zadaný datový typ, dojde k chybě kompilace.|

Pokud zadáte datový typ, ale nezadávejte inicializátor, Visual Basic inicializuje proměnnou na výchozí hodnotu pro jeho datového typu. V následující tabulce jsou uvedeny výchozí inicializace hodnoty.

|Datový typ|Výchozí hodnota|
|---|---|
|Všechny číselné typy (včetně `Byte` a `SByte`)|0|
|`Char`|Binární 0|
|Všechny typy odkazů (včetně `Object`, `String`a všechna pole)|`Nothing`|
|`Boolean`|`False`|
|`Date`|12:00:00 1. ledna roku 1 (01, 01/0001 12:00:00 AM)|

Každý prvek struktury je inicializována, jako by šlo samostatná proměnná. Pokud deklarujete délku pole, ale jeho elementy neinicializujte, každý element je inicializována, jako by šlo samostatná proměnná.

## <a name="static-local-variable-lifetime"></a>Statické místní proměnné dobu platnosti

A `Static` lokální proměnná má delší dobu platnosti než u postupu, ve kterém je deklarována. Hranice životnost proměnné závisí na ve kterém je deklarována jako postup a určuje, zda je `Shared`.

|Deklarace procedury|Proměnná inicializována|Proměnná přestane existující|
|---|---|---|
|V modulu|Při prvním volání procedury|Když váš program zastaví provádění|
|Ve třídě nebo struktuře postup je `Shared`|Při prvním volání procedury na konkrétní instanci nebo na dané třídy nebo struktury samotné|Když váš program zastaví provádění|
|Ve třídě nebo struktuře není postup `Shared`|Při prvním volání procedury na konkrétní instanci|Uvolnění instance pro uvolňování paměti (GC)|

## <a name="attributes-and-modifiers"></a>Atributy a modifikátory

Můžete použít atributy pouze na členské proměnné, nikoli na lokální proměnné. Atribut přispívá informace metadat sestavení, která není smysl pro dočasné úložiště, jako jsou místní proměnné.

Na úrovni modulu nelze použít `Static` Modifikátor pro deklaraci členské proměnné. Na úrovni postupu nelze použít `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, nebo žádný přístup k modifikátory při deklarování lokálních proměnných.

Můžete určit, jaký kód může přistupovat k proměnné zadáním `accessmodifier`. Třídy a modul členské proměnné (mimo všechny procedury) výchozí privátní přístup a struktura členské proměnné výchozí veřejný přístup. Můžete nastavit jejich úrovně přístupu modifikátory přístupu. Na lokální proměnné (uvnitř procedury) nejde použít modifikátory přístupu.

Můžete zadat `WithEvents` pouze na členské proměnné, nikoli na lokálních proměnných uvnitř procedury. Pokud zadáte `WithEvents`, datový typ proměnné musí určitý typ třídy, ne `Object`. Nelze deklarovat pole `WithEvents`. Další informace o událostech najdete v tématu [události](../../../visual-basic/programming-guide/language-features/events/index.md).

> [!NOTE]
> Kód mimo třídu, strukturu nebo modul musí kvalifikovat název členské proměnné s názvem této třídy, struktury nebo modulu. Kód mimo území proceduru nebo blok nemůžou odkazovat na žádné místní proměnné v rámci tohoto postupu nebo blok.

## <a name="releasing-managed-resources"></a>Spravované prostředky

Uvolňování paměti rozhraní .NET Framework uvolní spravované prostředky bez dodatečné kódování z vaší strany. Ale můžete vynutit uvolnění spravovaného prostředku, místo abyste čekali, systému uvolňování paměti.

Pokud třída obsahuje do zejména cenných a omezených prostředků (jako je například připojení nebo soubor popisovač databáze), nebudete chtít počkat do dalšího uvolnění pro vyčištění instance třídy, která se už používá. Třída může implementovat <xref:System.IDisposable> rozhraní poskytují způsob k uvolnění prostředků než uvolnění paměti. Poskytuje třídu, která implementuje rozhraní `Dispose` metoda, kterou lze volat pro vynucení cenné prostředky okamžitě uvolní.

`Using` Příkaz automatizuje proces získání prostředku, provedení sady příkazů a pak uvolnění prostředku. Však musí implementovat prostředek <xref:System.IDisposable> rozhraní. Další informace najdete v tématu [příkazu Using](../../../visual-basic/language-reference/statements/using-statement.md).

## <a name="example"></a>Příklad

Následující příklad proměnné deklarovány s použitím `Dim` příkaz různé možnosti.

[!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]

## <a name="example"></a>Příklad

Následující příklad vypíše prvočísel od 1 do 30. Obor lokální proměnné jsou popsány v komentářích ke kódu.

[!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]

## <a name="example"></a>Příklad

V následujícím příkladu `speedValue` proměnná je deklarovaná na úrovni třídy. `Private` – Klíčové slovo se používá k deklaraci proměnné. Proměnná je možný přes všechny procedury v `Car` třídy.

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
- [Inicializátory objektů: Pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Inicializátory objektů: Pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Postupy: Deklarace objektu pomocí inicializátoru objektů](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
