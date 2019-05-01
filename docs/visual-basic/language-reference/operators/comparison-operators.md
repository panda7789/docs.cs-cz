---
title: Operátory porovnání (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<>
- vb.>=
- vb.<=
- vb.>
- vb.<
helpviewer_keywords:
- greater than or equal to operator [Visual Basic]
- '>= operator [Visual Basic]'
- = operator [Visual Basic]
- < operator [Visual Basic]
- less than operator [Visual Basic]
- relational operators [Visual Basic], syntax
- Like operator [Visual Basic]
- <> operator [Visual Basic]
- '> operator [Visual Basic]'
- equal operator [Visual Basic]
- less than or equal to operator [Visual Basic]
- symbols, operators
- greater than operator [Visual Basic]
- comparing values [Visual Basic]
- operators [Visual Basic], relational
- string comparison [Visual Basic]
- not equal to comparison operator [Visual Basic]
- <= operator [Visual Basic]
- operators [Visual Basic], comparison
- Is operator [Visual Basic]
- comparison operators [Visual Basic], Visual Basic
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
ms.openlocfilehash: 9014cac5e2f3933b27411dfe5681fc16f4cdde30
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013579"
---
# <a name="comparison-operators-visual-basic"></a>Operátory porovnání (Visual Basic)
Níže jsou operátory porovnání, které jsou definovány v jazyce Visual Basic.  
  
 `<` – Operátor  
  
 `<=` – Operátor  
  
 `>` – Operátor  
  
 `>=` – Operátor  
  
 `=` – Operátor  
  
 `<>` – Operátor  
  
 [Operátor Is](../../../visual-basic/language-reference/operators/is-operator.md)  
  
 [Operátor IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)  
  
 [Operátor Like](../../../visual-basic/language-reference/operators/like-operator.md)  
  
 Tyto operátory porovnávají dva výrazy k určení, zda jsou stejné, a pokud ne, jak se liší. `Is`, `IsNot`, a `Like` jsou podrobně popsány v na samostatných stránkách nápovědy. Relační porovnávací operátory jsou podrobně popsány v na této stránce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
      result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinný parametr. A `Boolean` hodnotu představující výsledek porovnání.  
  
 `expression`  
 Povinný parametr. Libovolný výraz.  
  
 `comparisonoperator`  
 Povinný parametr. Libovolný relační operátor porovnání.  
  
 `object1`, `object2`  
 Povinný parametr. Všechny odkazy názvy objektů.  
  
 `string`  
 Povinný parametr. Žádné `String` výrazu.  
  
 `pattern`  
 Povinný parametr. Žádné `String` výraz nebo rozsahu znaků.  
  
## <a name="remarks"></a>Poznámky  
 Následující tabulka obsahuje seznam relační relační operátory a podmínky, které určují, jestli `result` je `True` nebo `False`.  
  
|Operátor|`True` If|`False` If|  
|--------------|---------------|----------------|  
|`<` (Méně než)|`expression1` < `expression2`|`expression1` >= `expression2`|  
|`<=` (Menší než nebo rovno)|`expression1` <= `expression2`|`expression1` > `expression2`|  
|`>` (Větší než)|`expression1` > `expression2`|`expression1` <= `expression2`|  
|`>=` (Větší než nebo rovno)|`expression1` >= `expression2`|`expression1` < `expression2`|  
|`=` (Rovná se)|`expression1` = `expression2`|`expression1` <> `expression2`|  
|`<>` (Není rovno)|`expression1` <> `expression2`|`expression1` = `expression2`|  
  
> [!NOTE]
>  [= – Operátor](../../../visual-basic/language-reference/operators/assignment-operator.md) slouží také jako operátor přiřazení.  
  
 `Is` Operátoru `IsNot` operátor a `Like` operátor mít konkrétní porovnání funkcí, které se liší od operátorů v předchozí tabulce.  
  
## <a name="comparing-numbers"></a>Porovnání čísel  
 Při porovnávání výraz typu `Single` do jednoho typu `Double`, `Single` výrazu je převedena na `Double`. Toto chování je než tomuto chování dochází v jazyce Visual Basic 6.  
  
 Podobně při porovnávání výraz typu `Decimal` ve výrazu typu `Single` nebo `Double`, `Decimal` výrazu je převedena na `Single` nebo `Double`. Pro `Decimal` výrazy, všechny desetinná hodnota menší než 1E-28 může být ztracené. Takové ztrátě desetinná hodnota může způsobit, že dvě hodnoty a vyhodnoceny jako shodné, když se nepoužívají. Z tohoto důvodu, které byste měli věnovat pozornost při použití rovnosti (`=`) Chcete-li porovnat dvě proměnné s plovoucí desetinnou čárkou. Je bezpečnější k ověření, zda absolutní hodnota rozdílu daných dvou čísel je menší než malé přípustné.  
  
### <a name="floating-point-imprecision"></a>S plovoucí desetinnou čárkou nepřesnost  
 Při práci s čísly s plovoucí desetinnou čárkou, mějte na paměti, že vždy nemají přesnou reprezentací v paměti. To může vést k neočekávaným výsledkům z určité operace, jako je například porovnání hodnoty a [Mod operátor](../../../visual-basic/language-reference/operators/mod-operator.md). Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="comparing-strings"></a>Porovnávání řetězců  
 Při porovnávání řetězců řetězcové výrazy jsou vyhodnocovány v pořadí jejich abecední řazení, která závisí na `Option Compare` nastavení.  
  
 `Option Compare Binary` na pořadí řazení odvozený z vnitřní binární reprezentace znaků při porovnávání řetězců základních tříd. Pořadí řazení se určuje podle kódové stránky. Následující příklad ukazuje typické binární řazení.  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 `Option Compare Text` Při porovnávání na určené národní prostředí vaší aplikace velkých a malých písmen, textové řazení řetězců základních tříd. Pokud nastavíte `Option Compare Text` a řazení znaků v předchozím příkladu, použije textové řazení:  
  
 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`  
  
### <a name="locale-dependence"></a>Závislost na národním prostředí  
 Pokud nastavíte `Option Compare Text`, výsledku porovnání řetězců může záviset na národním prostředí, ve kterém je aplikace spuštěna. Stejné jedno prostředí, ale není v druhém může porovnat dva znaky. Pokud používáte porovnání řetězců učinění důležitých rozhodnutí, jako je například, jestli se má přijmout pokus o přihlášení, musí být výstraha citlivosti národní prostředí. Vezměte v úvahu buď nastavení `Option Compare Binary` nebo volání <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, který bere v úvahu národní prostředí.  
  
## <a name="typeless-programming-with-relational-comparison-operators"></a>Programování bez psaní s relačními relační operátory  
 Použití operátorů relační porovnání s `Object` výrazů není povolen v kontextu `Option Strict On`. Když `Option Strict` je `Off`a buď `expression1` nebo `expression2` je `Object` výrazu, typy za běhu zjistit, jak jsou porovnány. V následující tabulce najdete porovnání výrazy a výsledkem porovnání, v závislosti na typu runtime z operandů.  
  
|Pokud jsou operandy|Porovnání|  
|---------------------|-------------------|  
|Obojí `String`|Seřadit podle vlastnosti řazení řetězců porovnání.|  
|Číselné|Objekty převedeny na `Double`, číselné porovnání.|  
|Jedna číslice a jeden `String`|`String` Je převedena na `Double` a číselné porovnání je provedeno. Pokud `String` nelze převést na `Double`, <xref:System.InvalidCastException> je vyvolána výjimka.|  
|Jeden nebo oba jsou odkazové typy jiné než `String`|<xref:System.InvalidCastException> Je vyvolána výjimka.|  
  
 Číselné porovnání považovat `Nothing` jako 0. Porovnávání řetězců považovat `Nothing` jako `""` (prázdný řetězec).  
  
## <a name="overloading"></a>Přetížení  
 Relační porovnávací operátory (`<`. `<=``>`, `>=`, `=`, `<>`) může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jejich chování při operand má typ této třídě nebo struktuře. Pokud váš kód používá některou z těchto operátorů na takové třídy nebo struktury, ujistěte se, že rozumíte Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
 Všimněte si, [= – operátor](../../../visual-basic/language-reference/operators/assignment-operator.md) může být přetížená pouze jako operátor porovnání relační, nikoli jako operátor přiřazení.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje různé možnosti použití relační porovnávací operátory, které můžete použít k porovnání výrazy. Vrátí relační relační operátory `Boolean` výsledek, který představuje zda uvedená výraz je vyhodnocen jako `True`. Pokud použijete `>` a `<` operátory na řetězce, je provedeno porovnání použitím normální abecedním pořadí řazení řetězců. Toto pořadí může být závislé na nastavení národního prostředí. Určuje, zda je řazení malá a velká písmena nebo není závislá [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) nastavení.  
  
 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]  
  
 V předchozím příkladu vrátí první porovnání `False` a vrátit zbývající porovnání `True`.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.InvalidCastException>
- [= – operátor](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Operátory porovnání v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
