---
title: Předávání argumentů pozicí nebo názvem
ms.date: 02/01/2018
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
ms.openlocfilehash: b6588335f7634cc87a9fc14cbfc4ba80baad1abb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400853"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>Předávání argumentů podle pozice a názvu (Visual Basic)

Když voláte `Sub` `Function` nebo proceduru, můžete předat argumenty *podle pozice* – v pořadí, ve kterém jsou uvedeny v definici postupu – nebo je můžete předat *podle názvu*, bez ohledu na pozici.

Když předáte argument podle názvu, zadáte deklarovaný název argumentu následovaný`:=`dvojtečkou a rovnítkem ( ), následovaným hodnotou argumentu. Pojmenované argumenty můžete zadat v libovolném pořadí.

Například následující `Sub` postup trvá tři argumenty:

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

Při volání tohoto postupu můžete zadat argumenty podle pozice, podle názvu nebo pomocí kombinace obou.

## <a name="passing-arguments-by-position"></a>Předávání argumentů podle pozice

Můžete volat `Display` metodu s její argumenty předaný pozice a oddělené čárkami, jak je znázorněno v následujícím příkladu:

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

Pokud vynechete volitelný argument v seznamu pozičních argumentů, musíte jeho místo držet čárkou. Následující příklad volá `Display` metodu `age` bez argumentu:

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a>Předávání argumentů podle názvu

Případně můžete volat `Display` s argumenty předanými názvem, také oddělenými čárkami, jak je znázorněno v následujícím příkladu:

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

Předávání argumentů podle názvu tímto způsobem je zvláště užitečné při volání procedury, která má více než jeden volitelný argument. Pokud zadáte argumenty podle názvu, není třeba k označení chybějících pozičních argumentů používat po sobě jdoucí čárky. Předávání argumentů podle názvu také usnadňuje sledování, které argumenty předáváte a které vynecháváte.

## <a name="mixing-arguments-by-position-and-by-name"></a>Míchání argumentů podle pozice a názvu

Argumenty můžete zadat podle pozice i názvu v jednom volání procedury, jak je znázorněno v následujícím příkladu:

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

V předchozím příkladu žádné další čárka je nutné držet `age` místo vynechaného argumentu, since `birth` je předán podle názvu.

Ve verzích jazyka Visual Basic před 15.5 při zadání argumentů kombinací pozice a názvu musí být všechny poziční argumenty na prvním místě. Jakmile zadáte argument podle názvu, všechny zbývající argumenty musí být předány podle názvu.  Například následující volání metody `Display` zobrazí chybu kompilátoru [BC30241: Pojmenovaný argument byl očekáván](../../../misc/bc30241.md).

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

Počínaje Visual Basic 15.5, poziční argumenty mohou následovat pojmenované argumenty, pokud koncové poziční argumenty jsou ve správné poloze. Pokud je zkompilován v jazyce Visual `Display` Basic 15.5, předchozí volání metody zkompiluje úspěšně a již generuje chybu kompilátoru [BC30241](../../../misc/bc30241.md).

Tato schopnost kombinovat pojmenované a poziční argumenty v libovolném pořadí je zvláště užitečné, pokud chcete použít pojmenovaný argument, aby váš kód čitelnější. Například následující `Person` konstruktor třídy vyžaduje dva `Person`argumenty typu `Nothing`, které mohou být .

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

Použití smíšené pojmenované a poziční argumenty pomáhá, aby záměr `father` `mother` kódu jasné, když je hodnota a argumenty `Nothing`:

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

Chcete-li sledovat poziční argumenty s pojmenovanými argumenty,\*musíte do souboru projektu jazyka Visual Basic (.vbproj) přidat následující prvek:

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

Další informace naleznete [v nastavení jazykové verze jazyka Jazyka](../../../language-reference/configure-language-version.md).

## <a name="restrictions-on-supplying-arguments-by-name"></a>Omezení dodávajících argumentů podle názvu

Nelze předat argumenty podle názvu, abyste se vyhnuli zadávání požadovaných argumentů. Vynechat můžete pouze volitelné argumenty.

Pole parametrů nelze předat podle názvu. Důvodem je, že při volání procedury zadáte neurčitý počet argumentů oddělených čárkami pro pole parametrů a kompilátor nemůže přidružit více než jeden argument s jedním názvem.

## <a name="see-also"></a>Viz také

- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)
- [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)
- [Volitelné parametry](./optional-parameters.md)
- [Pole parametrů](./parameter-arrays.md)
- [Volitelné](../../../../visual-basic/language-reference/modifiers/optional.md)
- [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
