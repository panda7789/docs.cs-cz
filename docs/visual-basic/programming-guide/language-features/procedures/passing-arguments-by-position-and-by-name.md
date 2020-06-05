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
ms.openlocfilehash: 686b64977f086c8128e56298a0ed8c5aa0c51efa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364029"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>Předávání argumentů podle pozice a názvu (Visual Basic)

Při volání `Sub` `Function` procedury nebo můžete předat argumenty *podle pozice* – v pořadí, v jakém jsou uvedeny v definici procedury, nebo je můžete předat *podle názvu*bez ohledu na pozici.

Pokud předáte argument podle názvu, zadáte deklarovaný název argumentu následovaný dvojtečkou a symbolem rovná se ( `:=` ) následovaný hodnotou argumentu. Pojmenované argumenty můžete dodat v libovolném pořadí.

Například následující `Sub` procedura přijímá tři argumenty:

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

Při volání tohoto postupu můžete dodat argumenty podle pozice, názvu nebo pomocí kombinace obou.

## <a name="passing-arguments-by-position"></a>Předávání argumentů podle pozice

Metodu lze volat `Display` s argumenty předanými pozicí a oddělenými čárkami, jak je znázorněno v následujícím příkladu:

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

Vynecháte-li volitelný argument v seznamu pozičních argumentů, je nutné umístit jeho umístění do čárky. V následujícím příkladu je volána `Display` Metoda bez `age` argumentu:

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a>Předávání argumentů podle názvu

Alternativně můžete volat `Display` s argumenty předanými podle názvu, také oddělené čárkami, jak je znázorněno v následujícím příkladu:

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

Předávání argumentů podle názvu tímto způsobem je zvlášť užitečné při volání procedury, která má více než jeden volitelný argument. Pokud zadáte argumenty podle názvu, nemusíte používat po sobě jdoucí čárky k označení chybějících argumentů. Předávání argumentů podle názvu také usnadňuje sledování předávaného argumentu a těch, které jsou vynechány.

## <a name="mixing-arguments-by-position-and-by-name"></a>Kombinování argumentů podle pozice a názvu

Můžete dodat argumenty podle umístění a podle názvu v rámci jednoho volání procedury, jak je znázorněno v následujícím příkladu:

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

V předchozím příkladu není k dispozici žádná další čárka, která by obsahovala místo vynechaného `age` argumentu, protože `birth` je předána názvem.

Ve verzích Visual Basic před 15,5, pokud zadáváte argumenty podle kombinace pozice a názvu, musí být argumenty pozice napřed. Po zadání argumentu podle názvu musí všechny zbývající argumenty předávat název.  Například následující volání `Display` metody zobrazí chybu kompilátoru [BC30241: očekával se pojmenovaný argument](../../../misc/bc30241.md).

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

Počínaje Visual Basic 15,5 se Poziční argumenty mohou pořídit pojmenovanými argumenty, pokud jsou konečné Poziční argumenty ve správné pozici. Pokud je kompilace v rámci Visual Basic 15,5, předchozí volání `Display` metody se úspěšně zkompiluje a již negeneruje chybu kompilátoru [BC30241](../../../misc/bc30241.md).

Tuto schopnost sloučit a porovnat pojmenované a poziční argumenty v libovolném pořadí je zvláště užitečné, pokud chcete použít pojmenovaný argument k lepšímu čitelnosti kódu. Například následující `Person` konstruktor třídy vyžaduje dva argumenty typu `Person` , oba z nich mohou být `Nothing` .

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

Použití smíšených pojmenovaných a pozičních argumentů pomáhá zajistit, aby byl záměr kódu jasný, pokud `father` je hodnota `mother` argumentů a `Nothing` .

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

Chcete-li následovat Poziční argumenty s pojmenovanými argumenty, je nutné přidat následující prvek do souboru Visual Basic projektu ( \* . vbproj):

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

Další informace najdete v tématu [nastavení jazykové verze Visual Basic](../../../language-reference/configure-language-version.md).

## <a name="restrictions-on-supplying-arguments-by-name"></a>Omezení pro zadání argumentů podle názvu

Argumenty nelze předat podle názvu, abyste se vyhnuli zadávání požadovaných argumentů. Můžete vynechat jenom nepovinné argumenty.

Pole parametrů nelze předat podle názvu. Důvodem je, že při volání procedury zadáte nekonečný počet argumentů oddělených čárkou pro pole parametrů a kompilátor nemůže přidružit více než jeden argument s jediným názvem.

## <a name="see-also"></a>Viz také

- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)
- [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)
- [Volitelné parametry](./optional-parameters.md)
- [Pole parametrů](./parameter-arrays.md)
- [Volitelné](../../../language-reference/modifiers/optional.md)
- [ParamArray](../../../language-reference/modifiers/paramarray.md)
