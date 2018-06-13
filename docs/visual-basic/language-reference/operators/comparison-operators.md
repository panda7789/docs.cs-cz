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
- comparison operators [Visual Basic], Visual Basicl
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
ms.openlocfilehash: 4e37f55b4c873c3dbea22a8edf0e5e2b58824720
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604923"
---
# <a name="comparison-operators-visual-basic"></a>Operátory porovnání (Visual Basic)
Níže jsou uvedeny operátory porovnání definované v jazyce Visual Basic.  
  
 `<` Operátor  
  
 `<=` Operátor  
  
 `>` Operátor  
  
 `>=` Operátor  
  
 `=` Operátor  
  
 `<>` Operátor  
  
 [Operátor Is](../../../visual-basic/language-reference/operators/is-operator.md)  
  
 [Operátor IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)  
  
 [Operátor Like](../../../visual-basic/language-reference/operators/like-operator.md)  
  
 Tyto operátory porovnání dvou výrazů k určení, zda jsou stejné, a pokud ne, jak se liší. `Is`, `IsNot`, a `Like` jsou podrobně popsané na samostatné stránky nápovědy. Relační relační operátory jsou podrobně popsané na této stránce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
      result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Požadováno. A `Boolean` hodnotu představující výsledku porovnání.  
  
 `expression`  
 Požadováno. Jakýkoli výraz.  
  
 `comparisonoperator`  
 Požadováno. Libovolný relační operátor porovnání.  
  
 `object1`, `object2`  
 Požadováno. Všechny názvy objektů odkaz.  
  
 `string`  
 Požadováno. Všechny `String` výraz.  
  
 `pattern`  
 Požadováno. Všechny `String` výraz nebo rozsah znaků.  
  
## <a name="remarks"></a>Poznámky  
 Následující tabulka obsahuje seznam relační relační operátory a podmínky určující, zda `result` je `True` nebo `False`.  
  
|Operátor|`True` Pokud|`False` Pokud|  
|--------------|---------------|----------------|  
|`<` (Méně než)|`expression1` < `expression2`|`expression1` >= `expression2`|  
|`<=` (Je menší než nebo rovno)|`expression1` <= `expression2`|`expression1` > `expression2`|  
|`>` (Větší než)|`expression1` > `expression2`|`expression1` <= `expression2`|  
|`>=` (Je větší než nebo rovno)|`expression1` >= `expression2`|`expression1` < `expression2`|  
|`=` (Rovno)|`expression1` = `expression2`|`expression1` <> `expression2`|  
|`<>` (Není rovno)|`expression1` <> `expression2`|`expression1` = `expression2`|  
  
> [!NOTE]
>  [= – Operátor](../../../visual-basic/language-reference/operators/assignment-operator.md) se používá jako operátor přiřazení.  
  
 `Is` Operátor, `IsNot` operátor a `Like` operátor mají konkrétní porovnání funkcí, které se liší od operátory v předchozí tabulce.  
  
## <a name="comparing-numbers"></a>Porovnání čísla  
 Při porovnání výrazu typu `Single` na jednu z typu `Double`, `Single` výrazu je převést na `Double`. Toto chování je opačné tomuto chování dochází v jazyce Visual Basic 6.  
  
 Podobně když porovnání výrazu typu `Decimal` do výrazu typu `Single` nebo `Double`, `Decimal` výrazu je převést na `Single` nebo `Double`. Pro `Decimal` výrazy, všechny desetinnou hodnotu menší než 1E-28 mohou být ztraceny. Takové ztrátě desetinnou hodnotu, může způsobit dvě hodnoty k porovnání jako s rovnocennými, když se nepoužívají. Z tohoto důvodu můžete dbát na při použití rovnosti (`=`) k porovnání dvou proměnné s plovoucí desetinnou čárkou. Je bezpečnější a otestovat, jestli absolutní hodnotu rozdíl mezi dvěma čísly je menší než malé přípustné tolerance.  
  
### <a name="floating-point-imprecision"></a>S plovoucí desetinnou čárkou nepřesnosti  
 Při práci s plovoucí desetinnou čárkou, mějte na paměti, že vždy nemají znázornění přesné v paměti. To může vést k neočekávaným výsledkům z určité operace, jako je například porovnání hodnoty a [Mod operátor](../../../visual-basic/language-reference/operators/mod-operator.md). Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="comparing-strings"></a>Porovnávání řetězců  
 Při porovnávání řetězců se vyhodnotí výrazy řetězec na jejich abecedním pořadí, což závisí na základě `Option Compare` nastavení.  
  
 `Option Compare Binary` základů řetězec porovnání na pořadí řazení odvozené z interní binární reprezentace znaky. Pořadí řazení je určen podle znakové stránky. Následující příklad ukazuje typické binární řazení.  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 `Option Compare Text` základů řetězec porovnání na pořadí řazení velká a malá písmena, textovou dáno národního prostředí vaší aplikace. Když nastavíte `Option Compare Text` a seřadit znaky v předchozím příkladu, platí následující pořadí řazení text:  
  
 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`  
  
### <a name="locale-dependence"></a>Závislost na národním prostředí  
 Když nastavíte `Option Compare Text`, výsledku porovnání řetězců, může záviset na národním prostředí, ve kterém je aplikace spuštěna. Dva znaky může porovnat jako rovná jeden národního prostředí, ale ne v jiném. Pokud používáte porovnání řetězců učinění důležitých rozhodnutí, jako je například, jestli se má přijmout pokus o přihlášení, musí být výstraha národního prostředí velkých a malých písmen. Vezměte v úvahu buď nastavení `Option Compare Binary` nebo volání <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, který bere v úvahu národní prostředí.  
  
## <a name="typeless-programming-with-relational-comparison-operators"></a>Programování bez psaní s porovnání relační operátory  
 Použití operátorů relační porovnání s `Object` výrazy není povolen v kontextu `Option Strict On`. Když `Option Strict` je `Off`a buď `expression1` nebo `expression2` je `Object` výrazu typy spuštění určují, jak jsou porovnávány. V následující tabulce jsou uvedeny porovnání výrazy a výsledek z porovnání, v závislosti na typu runtime operandy.  
  
|Pokud jsou operandy|Porovnání se|  
|---------------------|-------------------|  
|Obě `String`|Seřadí porovnání založené na řetězci řazení charakteristiky.|  
|Jedná se o číselné|Objekty převést na `Double`, číselné porovnání.|  
|Jedna číslice a jeden `String`|`String` Jsou převedeny na `Double` a je provedeno číselné porovnání. Pokud `String` nelze převést na `Double`, <xref:System.InvalidCastException> je vyvolána výjimka.|  
|Odkazové typy jiné než je buď nebo obě `String`|<xref:System.InvalidCastException> Je vyvolána výjimka.|  
  
 Číselné porovnání považovat `Nothing` jako 0. Porovnání řetězců považovat `Nothing` jako `""` (prázdný řetězec).  
  
## <a name="overloading"></a>Přetížení  
 Porovnání relační operátory (`<`. `<=``>`, `>=`, `=`, `<>`) může být *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat jejich chování při operand má typ třídy nebo struktura. Pokud váš kód používá některé z těchto operátorů na takové třídu nebo strukturu, ujistěte se, že rozumíte Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
 Všimněte si, že [= – operátor](../../../visual-basic/language-reference/operators/assignment-operator.md) může být přetížené pouze jako operátor porovnání relační, ne jako operátor přiřazení.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje různé používá relační relační operátory, které můžete použít k porovnání výrazy. Vrátí porovnání relační operátory `Boolean` výsledek, který představuje zda stanovené výraz vyhodnocen jako `True`. Pokud použijete `>` a `<` operátorům řetězce, porovnání se provádí pomocí normální abecedním pořadí řazení řetězců. Toto pořadí může být závislá na vaše nastavení národního prostředí. Řazení není jestli malá a velká písmena, nebo není závislá [možnost porovnat](../../../visual-basic/language-reference/statements/option-compare-statement.md) nastavení.  
  
 [!code-vb[VbVbalrOperators#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 V předchozím příkladu, vrátí první porovnání `False` a vrátit zbývající porovnání `True`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.InvalidCastException>  
 [= – operátor](../../../visual-basic/language-reference/operators/assignment-operator.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Operátory porovnání v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
