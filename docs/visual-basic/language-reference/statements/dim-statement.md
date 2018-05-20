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
ms.openlocfilehash: b3384b771748a1f2c9e841407042f81ce6ebe76d
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
---
# <a name="dim-statement-visual-basic"></a>Dim – příkaz (Visual Basic)
Deklaruje a přidělí prostor úložiště pro jeden nebo více proměnných.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]   
Dim [ WithEvents ] variablelist  
```  
  
## <a name="parts"></a>Součásti  
  
-   `attributelist`  
  
     Volitelné. V tématu [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
-   `accessmodifier`  
  
     Volitelné. Může být jedna z následujících akcí:  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   [Chráněné Friend](../../language-reference/modifiers/protected-friend.md)
    
    - [Privátní chráněný](../../language-reference/modifiers/private-protected.md)

     V tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
-   `Shared`  
  
     Volitelné. V tématu [sdílené](../../../visual-basic/language-reference/modifiers/shared.md).  
  
-   `Shadows`  
  
     Volitelné. V tématu [stínů](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
-   `Static`  
  
     Volitelné. V tématu [statické](../../../visual-basic/language-reference/modifiers/static.md).  
  
-   `ReadOnly`  
  
     Volitelné. V tématu [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
-   `WithEvents`  
  
     Volitelné. Určuje, že jsou objektové proměnné, které odkazují na instancí třídy, který může vyvolat události. V tématu [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).  
  
-   `variablelist`  
  
     Požadováno. Seznam proměnných se deklarovaných v tomto příkazu.  
  
     `variable [ , variable ... ]`  
  
     Každý `variable` má následující syntaxe a částí:  
  
     `variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`  
  
    |Část|Popis|  
    |---|---|  
    |`variablename`|Požadováno. Název proměnné. V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
    |`boundslist`|Volitelné. Seznam mezí Každá dimenze proměnná typu pole.|  
    |`New`|Volitelné. Vytvoří novou instanci třídy, když `Dim` příkaz spustí.|  
    |`datatype`|Volitelné. Datový typ proměnné.|  
    |`With`|Volitelné. Představuje seznam inicializátoru objektu.|  
    |`propertyname`|Volitelné. Název vlastnosti ve třídě provádíte instanci.|  
    |`propinitializer`|Požadované po `propertyname` =. Výraz, který se vyhodnotí a přiřadí název vlastnosti.|  
    |`initializer`|Nepovinný, pokud `New` není zadán. Výraz, který se vyhodnotí a přiřadí do proměnné při jeho vytvoření.|  
  
## <a name="remarks"></a>Poznámky  
 Visual Basic – kompilátor používá `Dim` příkaz k určení typu dat proměnné a další informace, například jaké kódu mají přístup k proměnné. Následující příklad deklaruje proměnnou pro uložení `Integer` hodnotu.  
  
```vb  
Dim numberOfStudents As Integer  
```  
  
 Můžete zadat jakýkoli datový typ nebo název výčtu, struktura, třídy nebo rozhraní.  
  
```vb  
Dim finished As Boolean  
Dim monitorBox As System.Windows.Forms.Form  
```  
  
 Pro odkaz na typ, můžete použít `New` – klíčové slovo vytvořit novou instanci třídy nebo struktury, která je zadána datového typu. Pokud používáte `New`, nepoužívejte inicializátoru výrazu. Místo toho zadáte argumenty, pokud jsou požadována konstruktoru třídy, ze kterého jsou vytváření proměnné.  
  
```vb  
Dim bottomLabel As New System.Windows.Forms.Label  
```  
  
 Je možné deklarovat proměnnou v postupu, blok, třída, struktura nebo modul. Nelze deklarovat proměnnou v zdrojový soubor, obor názvů nebo rozhraní. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Proměnné, která je deklarovaná na úrovni modulu mimo libovolná procedura je *členské proměnné* nebo *pole*. Členské proměnné jsou v oboru v rámci své třídy, struktury nebo modul. Proměnné, která je deklarovaná na úrovni postup je *místní proměnné*. Jsou místní proměnné v oboru pouze v rámci postupu nebo bloku.  
  
 Následující modifikátory přístupu slouží k deklarujte proměnné mimo proceduru: `Public`, `Protected`, `Friend`, `Protected Friend`, a `Private`. Další informace najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Dim` – Klíčové slovo je volitelný a obvykle vynechána, pokud je zadána některá z následujících modifikátory: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, nebo `WithEvents`.  
  
```vb  
Public maximumAllowed As Double  
Protected Friend currentUserName As String  
Private salary As Decimal  
Static runningTotal As Integer  
```  
  
 Pokud `Option Explicit` je na (výchozí), vyžaduje kompilátor deklaraci pro každou proměnnou můžete použít. Další informace najdete v tématu [Option Explicit – příkaz](../../../visual-basic/language-reference/statements/option-explicit-statement.md).  
  
## <a name="specifying-an-initial-value"></a>Pokud zadáte počáteční hodnotu  
 Při vytvoření, můžete přiřadit hodnotu proměnné. Pro typ hodnoty, můžete použít *inicializátoru* k poskytování výraz pro přiřazení k proměnné. Výsledkem výrazu musí být konstanta, která lze vypočítat v době kompilace.  
  
```vb  
Dim quantity As Integer = 10  
Dim message As String = "Just started"  
```  
  
 Pokud je zadán inicializátoru a datový typ není zadán `As` klauzuli *odvození typu* se používá k odvození typu dat z inicializátoru. V následujícím příkladu obě `num1` a `num2` jsou silného typu jako celá čísla. V druhé deklaraci odvození typu odvodí typ z hodnotu 3.  
  
```vb  
' Use explicit typing.  
Dim num1 As Integer = 3  
  
' Use local type inference.  
Dim num2 = 3  
```  
  
 Odvození typu se vztahuje na úrovni postupu. Nevztahuje se mimo proceduru v třída, struktura, modulu nebo rozhraní. Další informace o odvození typu najdete v tématu [Option Infer – příkaz](../../../visual-basic/language-reference/statements/option-infer-statement.md) a [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
 Informace o tom co se stane, když není zadaný datový typ nebo inicializátoru najdete v tématu [výchozí datových typů a hodnot](../../../visual-basic/language-reference/statements/dim-statement.md#default) dál v tomto tématu.  
  
 Můžete použít *inicializátoru objektu* deklarovat instance pojmenované a anonymní typy. Následující kód vytvoří instanci `Student` třídy a inicializace vlastností pomocí inicializátoru objektu.  
  
```vb  
Dim student1 As New Student With {.First = "Michael",   
                                  .Last = "Tucker"}  
```  
  
 Další informace o inicializátory objektů najdete v tématu [postupy: Deklarace objektu pomocí inicializátoru objektu](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [inicializátory objektů: pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), a [anonymní typy ](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="declaring-multiple-variables"></a>Deklarování více proměnných  
 Je možné deklarovat několik proměnné v rámci jedné deklarace příkazu zadání názvu proměnné pro každé z nich a název každého pole v závorkách. Více proměnných jsou oddělené čárkami.  
  
```vb  
Dim lastTime, nextTime, allTimes() As Date  
```  
  
 Pokud je deklarovat více než jednu proměnnou na jednu `As` klauzule, nelze zadat inicializátoru pro tuto skupinu proměnných.  
  
 Můžete zadat různé datové typy pro jiné proměnné pomocí samostatné `As` klauzule pro každou proměnnou můžete deklarovat. Každá proměnná má datový typ zadaný v prvním `As` klauzule došlo po jeho `variablename` část.  
  
```vb  
Dim a, b, c As Single, x, y As Double, i As Integer  
' a, b, and c are all Single; x and y are both Double  
```  
  
## <a name="arrays"></a>Pole  
 Je možné deklarovat proměnnou pro uložení *pole*, která může pojmout více hodnot. Chcete-li určit, že proměnné obsahuje pole, postupujte podle jeho `variablename` okamžitě v závorkách. Další informace o polích najdete v tématu [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
 Můžete zadat dolní a horní mez Každá dimenze pole. Chcete-li to provést, zahrňte `boundslist` v závorkách. Pro každou dimenzi `boundslist` Určuje horní mez a volitelně dolní hranice. Dolní hranice, je vždy nula, a jestli ho zadáte nebo ne. Každý index se může lišit od nuly pomocí jeho horní mez hodnoty.  
  
 Následující dva příkazy jsou ekvivalentní. Každý příkaz deklaruje pole 21 `Integer` elementy. Pokud získáváte přístup k poli, index se může lišit od 0 do 20.  
  
```vb  
Dim totals(20) As Integer  
Dim totals(0 To 20) As Integer  
```  
  
 Následující příkaz deklaruje dvourozměrná pole typu `Double`. Pole má 6 sloupců (5 + 1) každé 4 řádky (3 + 1). Všimněte si, že horní mez představuje nejvyšší možná hodnota pro index, nebyl délka dimenze. Délka dimenze je horní mez plus jedna.  
  
```vb  
Dim matrix2(3, 5) As Double  
```  
  
 Pole může mít od 1 do 32 dimenzí.  
  
 Všechny hranice můžete nechat prázdné v deklarace pole. Pokud to uděláte, pole má počet dimenzí, které zadáte, ale není inicializován. Má hodnotu `Nothing` dokud alespoň inicializaci některé z jejích elementů. `Dim` Příkaz musíte zadat rozsah pro všechny dimenze nebo žádné dimenze.  
  
```vb  
' Declare an array with blank array bounds.  
Dim messages() As String  
' Initialize the array.  
ReDim messages(4)  
```  
  
 Pokud pole má více než jednou dimenzí, je nutné zahrnout čárkami k označení počet dimenzí v závorkách.  
  
```vb  
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte  
```  
  
 Je možné deklarovat *nulová délka pole* deklarováním jeden z tohoto pole dimenze mít hodnotu -1. Proměnné, která obsahuje pole nulovou délkou nemá hodnotu `Nothing`. Pole s nulovou délkou vyžadují některé běžné funkce runtime jazyka. Pokud se pokusíte přístup k takové pole, došlo k výjimce modulu runtime. Další informace najdete v tématu [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
 Hodnoty pole lze inicializovat pomocí pole literálu. Chcete-li to provést, uzavřete inicializace hodnoty se složené závorky (`{}`).  
  
```vb  
Dim longArray() As Long = {0, 1, 2, 3}  
```  
  
 Pro vícerozměrná pole je inicializace pro každý samostatný dimenzi uzavřené do složených závorek v vnější dimenzi. Elementy jsou určené v řádku hlavní pořadí.  
  
```vb  
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}  
```  
  
 Další informace o literálech pole najdete v tématu [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
##  <a name="default"></a> Typy a hodnoty výchozí Data  
 Následující tabulka popisuje výsledky datový typ a inicializátoru v různých kombinacích `Dim` příkaz.  
  
|Datový typ zadaný?|Zadaný inicializační?|Příklad|Výsledek|  
|---|---|---|---|  
|Ne|Ne|`Dim qty`|Pokud [možnost striktní](../../../visual-basic/language-reference/statements/option-strict-statement.md) je vypnuto (výchozí), proměnná je nastavená na `Nothing`.<br /><br /> Pokud `Option Strict` zapnutý, dojde k chybě kompilace.|  
|Ne|Ano|`Dim qty = 5`|Pokud [Option Infer –](../../../visual-basic/language-reference/statements/option-infer-statement.md) je na (výchozí), typ inicializátoru proměnné přijímá data. V tématu [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Pokud `Option Infer` vypnuté a `Option Strict` je vypnutý, nabývá datový typ `Object`.<br /><br /> Pokud `Option Infer` vypnuté a `Option Strict` zapnutý, dojde k chybě kompilace.|  
|Ano|Ne|`Dim qty As Integer`|Výchozí hodnota pro typ dat je inicializováno proměnnou. Najdete v tabulce dál v této části.|  
|Ano|Ano|`Dim qty  As Integer = 5`|Pokud datový typ inicializátoru není převést na zadaný datový typ, dojde k chybě kompilace.|  
  
 Pokud zadáte datový typ, ale nezadávejte žádné inicializátoru, Visual Basic inicializuje proměnnou na výchozí hodnotu pro jeho datového typu. Následující tabulka uvádí výchozí hodnoty inicializace.  
  
|Datový typ|Výchozí hodnota|  
|---|---|  
|Všechny číselnými typy (včetně `Byte` a `SByte`)|0|  
|`Char`|Binární 0|  
|Všechny odkazové typy (včetně `Object`, `String`a všechna pole)|`Nothing`|  
|`Boolean`|`False`|  
|`Date`|12:00:00 1. ledna roku 1 (01/01/0001 12:00:00 AM)|  
  
 Každý prvek strukturou je inicializován, jako by šlo samostatná proměnná. Pokud deklarovat délka pole, ale není inicializovat jeho prvky, každý prvek je inicializován, jako by šlo samostatná proměnná.  
  
## <a name="static-local-variable-lifetime"></a>Statické místní proměnné doba platnosti  
 A `Static` místní proměnné má delší doba platnosti než procesu, ve kterém je deklarovaná. Hranice životního cyklu proměnné závisí na kterém je deklarovaná postupu a zda je `Shared`.  
  
|Deklarace procedur|Proměnná inicializována|Proměnná zastaví existující|  
|---|---|---|  
|V modulu|Při prvním volání procedury|Pokud váš program zastaví provádění|  
|Ve třídě nebo struktuře postup je `Shared`|První postup se nazývá na konkrétní instanci nebo na třídu nebo strukturu, sám sebe|Pokud váš program zastaví provádění|  
|Ve třídě nebo struktuře není postup `Shared`|První postup se nazývá na konkrétní instanci|Uvolnění instance pro uvolňování paměti (GC)|  
  
## <a name="attributes-and-modifiers"></a>Atributy a modifikátory  
 Atributy lze použít pouze k členské proměnné, nikoli k lokální proměnné. Atribut přispívá informace metadat sestavení, která není smysl pro dočasné úložiště, jako je například místní proměnné.  
  
 Na úrovni modulu, nemůžete použít `Static` modifikátor deklarovat členské proměnné. Na úrovni postup, nemůžete použít `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, nebo žádný přístup modifikátory deklarovat lokální proměnné.  
  
 Můžete určit, jaký kód můžete přístup k proměnné zadáním `accessmodifier`. Třídy a modul výchozí proměnné (mimo libovolná procedura) člena privátní přístup a struktura členské proměnné výchozí nastavení veřejný přístup. Můžete nastavit jejich úrovně přístupu s modifikátory přístupu. Modifikátory přístupu nelze použít na lokální proměnné (uvnitř procedury).  
  
 Můžete zadat `WithEvents` pouze na členské proměnné, nikoli na lokální proměnné uvnitř procedury. Pokud zadáte `WithEvents`, datový typ proměnné, musí typu určité třídy, ne `Object`. Nelze deklarovat pole s `WithEvents`. Další informace o událostech najdete v tématu [události](../../../visual-basic/programming-guide/language-features/events/index.md).  
  
> [!NOTE]
>  Kód mimo třída, struktura, modul nebo kvalifikaci název členské proměnné s názvem třídy, struktury nebo modul. Mimo území procedura nebo bloku nemůže odkazovat na žádné místní proměnné v rámci tohoto postupu nebo bloku kódu.  
  
## <a name="releasing-managed-resources"></a>Uvolnění spravované prostředky  
 Uvolňování paměti rozhraní .NET Framework uvolní spravované prostředky bez další kódování z vaší strany. Ale můžete vynutit vyřazení spravovaných prostředků, místo abyste čekali, bude systém uvolňování.  
  
 Pokud do zvlášť cenné a omezených prostředků (například databáze připojení nebo soubor popisovač) obsahuje třídu, nechcete čekat na další uvolňování paměti pro vyčištění instance třídy, která je již používána. Třída může implementovat <xref:System.IDisposable> rozhraní a poskytují způsob k uvolnění prostředků než uvolnění paměti. Poskytuje třídu, která implementuje rozhraní `Dispose` metoda, kterou lze volat vynutit cenné prostředky k uvolnění okamžitě.  
  
 `Using` Příkaz automatizuje proces získávání prostředku, provádění sadu příkazů a pak uvolnění prostředku. Však musí implementovat prostředku <xref:System.IDisposable> rozhraní. Další informace najdete v tématu [pomocí příkazu](../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje proměnné pomocí `Dim` příkaz s různé možnosti.  
  
 [!code-vb[VbVbalrStatements#141](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad uvádí prvočísel od 1 do 30. Rozsah místních proměnných je popsaná v komentáře kódu.  
  
 [!code-vb[VbVbalrStatements#142](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_2.vb)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `speedValue` proměnné je deklarovaná na úrovni třídy. `Private` – Klíčové slovo se používá k deklaraci proměnnou. Proměnná je přístupná procedurou v `Car` třídy.  
  
 [!code-vb[VbVbalrStatements#144](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements#145](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_4.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Příkaz ReDim](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [Příkaz Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Příkaz Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Stránka Kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [Deklarace proměnné](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Pole](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Inicializátory objektů: pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Inicializátory objektů: pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Postupy: Deklarace objektu pomocí inicializátoru objektu](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)  
 [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
