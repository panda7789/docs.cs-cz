---
title: Operátory porovnání
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
ms.openlocfilehash: ea7604626ede66da818e4bc22fe4922bc752dc2c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336088"
---
# <a name="comparison-operators-visual-basic"></a>Operátory porovnání (Visual Basic)
Níže jsou uvedeny operátory porovnání definované v Visual Basic.

 operátor `<`

 operátor `<=`

 operátor `>`

 operátor `>=`

 operátor `=`

 operátor `<>`

 [Operátor Is](../../../visual-basic/language-reference/operators/is-operator.md)

 [Operátor IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)

 [Operátor Like](../../../visual-basic/language-reference/operators/like-operator.md)

 Tyto operátory porovnávají dva výrazy a určí, zda jsou nebo nejsou rovny, a pokud ne, jak se liší. `Is`, `IsNot`a `Like` jsou podrobněji popsány na samostatných stránkách s usnadněním. Relační operátory porovnání jsou podrobněji popsány na této stránce.

## <a name="syntax"></a>Syntaxe
  
```vb
result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a>Součásti
 `result`  
 Požadováno. Hodnota `Boolean` představující výsledek porovnání.

 `expression1``expression2`  
 Požadováno. Libovolný výraz.

 `comparisonoperator`  
 Požadováno. Jakýkoli relační operátor porovnání.

 `object1``object2`  
 Požadováno. Názvy referenčních objektů.

 `string`  
 Požadováno. Libovolný výraz `String`.

 `pattern`  
 Požadováno. Libovolný výraz `String` nebo rozsah znaků.

## <a name="remarks"></a>Poznámky
 Následující tabulka obsahuje seznam relačních operátorů porovnání a podmínky, které určují, zda je `result` `True` nebo `False`.

|Operátor|`True` if|`False` if|
|--------------|---------------|----------------|
|`<` (méně než)|`expression1` < `expression2`|`expression1` >= `expression2`|
|`<=` (je menší než nebo rovno)|`expression1` <= `expression2`|`expression1` > `expression2`|
|`>` (je větší než)|`expression1` > `expression2`|`expression1` <= `expression2`|
|`>=` (je větší než nebo rovno)|`expression1` >= `expression2`|`expression1` < `expression2`|
|`=` (je rovno)|`expression1` = `expression2`|`expression1` <> `expression2`|
|`<>` (není rovno)|`expression1` <> `expression2`|`expression1` = `expression2`|

> [!NOTE]
> [Operátor =](../../../visual-basic/language-reference/operators/assignment-operator.md) se používá také jako operátor přiřazení.

 Operátor `Is`, operátor `IsNot` a operátor `Like` mají konkrétní funkce porovnání, které se liší od operátorů v předchozí tabulce.

## <a name="comparing-numbers"></a>Porovnávání čísel
 Když porovnáte výraz typu `Single` k jednomu typu `Double`, je výraz `Single` převeden na `Double`. Toto chování je opakem chování zjištěného v Visual Basic 6.

 Podobně když porovnáte výraz typu `Decimal` k výrazu typu `Single` nebo `Double`, je výraz `Decimal` převeden na `Single` nebo `Double`. Pro `Decimal` výrazy může dojít ke ztrátě všech zlomkových hodnot menší než 1E – 28. Tato ztráta zlomkové hodnoty může způsobit porovnání dvou hodnot, které jsou stejné, pokud nejsou. Z tohoto důvodu byste měli být opatrní při použití rovnosti (`=`) k porovnání dvou proměnných s plovoucí desetinnou čárkou. Je bezpečnější testovat, zda absolutní hodnota rozdílu mezi dvěma čísly je menší než malá přijatelná tolerance.

### <a name="floating-point-imprecision"></a>Nepřesnost plovoucí desetinné čárky
 Když pracujete s čísly s plovoucí desetinnou čárkou, mějte na paměti, že nemají vždy přesnou reprezentaci v paměti. To může vést k neočekávaným výsledkům z určitých operací, jako je porovnání hodnot a [operátor mod](../../../visual-basic/language-reference/operators/mod-operator.md). Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).

## <a name="comparing-strings"></a>Porovnávání řetězců
 Při porovnávání řetězců jsou řetězcové výrazy vyhodnocovány na základě pořadí řazení podle abecedy, které závisí na nastavení `Option Compare`.

 `Option Compare Binary` porovnávání řetězců základů v pořadí řazení odvozeném z interní binární reprezentace znaků. Pořadí řazení je určeno znakovou stránkou. Následující příklad ukazuje typické binární pořadí řazení.

 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

 `Option Compare Text` porovnávání řetězců nerozlišuje malá a velká písmena, textové pořadí řazení určené národním prostředím vaší aplikace. Když nastavíte `Option Compare Text` a seřadíte znaky v předchozím příkladu, použije se následující řazení textu:

 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`

### <a name="locale-dependence"></a>Závislost národního prostředí
 Při nastavení `Option Compare Text`může výsledek porovnání řetězců záviset na národním prostředí, ve kterém je aplikace spuštěná. Dva znaky se můžou porovnat stejně jako v jednom národním prostředí, ale ne v jiném. Pokud používáte porovnání řetězců k rozhodování o důležitých rozhodnutích, například o tom, jestli se má přijmout pokus o přihlášení, měli byste být upozorňováni na citlivost národního prostředí. Zvažte buď nastavení `Option Compare Binary` nebo volání <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, která převezme národní prostředí v úvahu.

## <a name="typeless-programming-with-relational-comparison-operators"></a>Programování bez beztypových relačních operátorů porovnání
 Použití relačních operátorů porovnání s `Object` výrazy není povoleno v `Option Strict On`. Pokud je `Option Strict` `Off`a `expression1` nebo `expression2` je výraz `Object`, určují typy za běhu jejich porovnání. Následující tabulka ukazuje, jak jsou porovnány výrazy a výsledek porovnání v závislosti na typu modulu runtime operandů.

|Pokud jsou operandy|Porovnání je|
|---------------------|-------------------|
|Jak `String`|Porovnání řazení založené na charakteristikách řazení řetězců.|
|Oba číslice|Objekty převedené na `Double`, číselné porovnání.|
|Jedna číselná a jedna `String`|`String` je převedena na `Double` a číselné porovnání je provedeno. Pokud `String` nelze převést na `Double`, je vyvolána <xref:System.InvalidCastException>.|
|Oba typy odkazují na jiné než `String`.|Je vyvolána <xref:System.InvalidCastException>.|

 Číselná porovnání považovat `Nothing` za 0. Porovnávání řetězců považuje `Nothing` jako `""` (prázdný řetězec).

## <a name="overloading"></a>Přetížení
 Relační operátory porovnání (`<`. `<=`, `>`, `>=`, `=`, `<>`) mohou být *přetíženy*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury. Pokud váš kód používá některý z těchto operátorů v takové třídě nebo struktuře, ujistěte se, že rozumíte předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).

 Všimněte si, že [operátor =](../../../visual-basic/language-reference/operators/assignment-operator.md) může být přetížen pouze jako relační operátor porovnání, nikoli jako operátor přiřazení.

## <a name="example"></a>Příklad
 Následující příklad ukazuje různé způsoby použití relačních relačních operátorů, které slouží k porovnání výrazů. Relační operátory porovnání vracejí `Boolean` výsledek, který představuje, zda je nebo není stanovený výraz vyhodnocen jako `True`. Když použijete operátory `>` a `<` na řetězce, bude porovnání provedeno pomocí normálního pořadí řazení řetězců v abecedním pořadí. Tato objednávka může být závislá na nastavení národního prostředí. Bez ohledu na to, zda řazení rozlišuje velká a malá písmena, závisí na nastavení [Možnosti porovnat](../../../visual-basic/language-reference/statements/option-compare-statement.md) .

 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]

 V předchozím příkladu vrátí první porovnávání `False` a zbývající porovnávání vrátí `True`.

## <a name="see-also"></a>Viz také:

- <xref:System.InvalidCastException>
- [= – operátor](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Operátory porovnávání v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
