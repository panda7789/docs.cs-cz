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
ms.openlocfilehash: bcd51d70c5c7bd08991c7433e244316a82daa9da
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371788"
---
# <a name="comparison-operators-visual-basic"></a>Operátory porovnání (Visual Basic)
Níže jsou uvedeny operátory porovnání definované v Visual Basic.

 `<`podnikatel

 `<=`podnikatel

 `>`podnikatel

 `>=`podnikatel

 `=`podnikatel

 `<>`podnikatel

 [Is – operátor](is-operator.md)

 [IsNot – operátor](isnot-operator.md)

 [Like – operátor](like-operator.md)

 Tyto operátory porovnávají dva výrazy a určí, zda jsou nebo nejsou rovny, a pokud ne, jak se liší. `Is`, `IsNot` a `Like` jsou podrobněji popsány na samostatných stránkách s usnadněním. Relační operátory porovnání jsou podrobněji popsány na této stránce.

## <a name="syntax"></a>Syntaxe
  
```vb
result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a>Součásti
 `result`  
 Povinná hodnota. `Boolean`Hodnota představující výsledek porovnání.

 `expression1`, `expression2`  
 Povinná hodnota. Libovolný výraz

 `comparisonoperator`  
 Povinná hodnota. Jakýkoli relační operátor porovnání.

 `object1`, `object2`  
 Povinná hodnota. Názvy referenčních objektů.

 `string`  
 Povinná hodnota. Libovolný `String` výraz.

 `pattern`  
 Povinná hodnota. Libovolný `String` výraz nebo rozsah znaků.

## <a name="remarks"></a>Poznámky
 Následující tabulka obsahuje seznam relačních operátorů porovnání a podmínky, které určují, zda `result` jsou `True` nebo `False` .

|Operátor|`True`Přestože|`False`Přestože|
|--------------|---------------|----------------|
|`<`(Menší než)|`expression1` < `expression2`|`expression1` >= `expression2`|
|`<=`(Je menší než nebo rovno)|`expression1` <= `expression2`|`expression1` > `expression2`|
|`>`(Je větší než)|`expression1` > `expression2`|`expression1` <= `expression2`|
|`>=`(Je větší než nebo rovno)|`expression1` >= `expression2`|`expression1` < `expression2`|
|`=`(Je rovno)|`expression1` = `expression2`|`expression1` <> `expression2`|
|`<>`(Není rovno)|`expression1` <> `expression2`|`expression1` = `expression2`|

> [!NOTE]
> [Operátor =](assignment-operator.md) se používá také jako operátor přiřazení.

 `Is`Operátor, `IsNot` operátor a `Like` operátor mají specifické funkce porovnání, které se liší od operátorů v předchozí tabulce.

## <a name="comparing-numbers"></a>Porovnávání čísel
 Když porovnáte výraz typu `Single` k jednomu typu `Double` , `Single` je výraz převeden na `Double` . Toto chování je opakem chování zjištěného v Visual Basic 6.

 Podobně při porovnání výrazu typu `Decimal` s výrazem typu `Single` nebo `Double` `Decimal` je výraz převeden na `Single` nebo `Double` . U `Decimal` výrazů může dojít ke ztrátě jakékoli desetinné hodnoty menší než 1e-28. Tato ztráta zlomkové hodnoty může způsobit porovnání dvou hodnot, které jsou stejné, pokud nejsou. Z tohoto důvodu byste měli být opatrní při použití rovnosti ( `=` ) pro porovnání dvou proměnných s plovoucí desetinnou čárkou. Je bezpečnější testovat, zda absolutní hodnota rozdílu mezi dvěma čísly je menší než malá přijatelná tolerance.

### <a name="floating-point-imprecision"></a>Nepřesnost plovoucí desetinné čárky
 Když pracujete s čísly s plovoucí desetinnou čárkou, mějte na paměti, že nemají vždy přesnou reprezentaci v paměti. To může vést k neočekávaným výsledkům z určitých operací, jako je porovnání hodnot a [operátor mod](mod-operator.md). Další informace najdete v tématu [řešení potíží s datovými typy](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).

## <a name="comparing-strings"></a>Porovnávání řetězců
 Při porovnávání řetězců jsou řetězcové výrazy vyhodnocovány na základě pořadí řazení podle abecedy, které závisí na `Option Compare` nastavení.

 `Option Compare Binary`porovnávání řetězců základů v pořadí řazení odvozené z interních binárních reprezentace znaků. Pořadí řazení je určeno znakovou stránkou. Následující příklad ukazuje typické binární pořadí řazení.

 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

 `Option Compare Text`porovnávání řetězců základů nerozlišuje velká a malá písmena. určuje pořadí řazení textu určené národním prostředím vaší aplikace. Při nastavování `Option Compare Text` a řazení znaků v předchozím příkladu platí následující pořadí řazení textu:

 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`

### <a name="locale-dependence"></a>Závislost národního prostředí
 Když nastavíte `Option Compare Text` , výsledek porovnání řetězců může záviset na národním prostředí, ve kterém je aplikace spuštěná. Dva znaky se můžou porovnat stejně jako v jednom národním prostředí, ale ne v jiném. Pokud používáte porovnání řetězců k rozhodování o důležitých rozhodnutích, například o tom, jestli se má přijmout pokus o přihlášení, měli byste být upozorňováni na citlivost národního prostředí. Zvažte buď nastavení `Option Compare Binary` , nebo volání metody <xref:Microsoft.VisualBasic.Strings.StrComp%2A> , která vezme národní prostředí v úvahu.

## <a name="typeless-programming-with-relational-comparison-operators"></a>Programování bez beztypových relačních operátorů porovnání
 Použití relačních operátorů porovnání s `Object` výrazy není v rámci povoleno `Option Strict On` . Když `Option Strict` je `Off` , a buď `expression1` nebo `expression2` je `Object` výraz, běhové typy určují, jak jsou porovnány. Následující tabulka ukazuje, jak jsou porovnány výrazy a výsledek porovnání v závislosti na typu modulu runtime operandů.

|Pokud jsou operandy|Porovnání je|
|---------------------|-------------------|
|Protokoly`String`|Porovnání řazení založené na charakteristikách řazení řetězců.|
|Oba číslice|Objekty převedené na `Double` číselné porovnání|
|Jedna číselná a jedna`String`|Je `String` proveden převod na `Double` číselné porovnání. Pokud `String` nelze převést na `Double` , <xref:System.InvalidCastException> je vyvolána výjimka.|
|Oba typy odkazují na jiné než`String`|<xref:System.InvalidCastException>Je vyvolána výjimka.|

 Číselná porovnání se považují `Nothing` za 0. Porovnávání řetězců považuje `Nothing` za `""` (prázdný řetězec).

## <a name="overloading"></a>Přetížení
 Relační operátory porovnání ( `<` . `<=`, `>` , `>=` , `=` , `<>` ) mohou být *přetíženy*, což znamená, že třída nebo struktura může předefinovat jejich chování, pokud operand má typ této třídy nebo struktury. Pokud váš kód používá některý z těchto operátorů v takové třídě nebo struktuře, ujistěte se, že rozumíte předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).

 Všimněte si, že [operátor =](assignment-operator.md) může být přetížen pouze jako relační operátor porovnání, nikoli jako operátor přiřazení.

## <a name="example"></a>Příklad
 Následující příklad ukazuje různé způsoby použití relačních relačních operátorů, které slouží k porovnání výrazů. Relační operátory porovnání vracejí `Boolean` výsledek, který představuje, zda se vyhodnocuje uvedený výraz `True` . Použijete-li `>` `<` operátory a na řetězce, bude porovnání provedeno pomocí normálního pořadí řazení řetězců v abecedním pořadí. Tato objednávka může být závislá na nastavení národního prostředí. Bez ohledu na to, zda řazení rozlišuje velká a malá písmena, závisí na nastavení [Možnosti porovnat](../statements/option-compare-statement.md) .

 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]

 V předchozím příkladu se první porovnávání vrátí `False` a zbývající porovnání vrátí `True` .

## <a name="see-also"></a>Viz také

- <xref:System.InvalidCastException>
- [= – Operátor](assignment-operator.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [Řešení potíží s datovými typy](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Operátory porovnání v jazyce Visual Basic](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
