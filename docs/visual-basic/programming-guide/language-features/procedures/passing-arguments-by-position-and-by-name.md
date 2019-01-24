---
title: Předávání argumentů podle pozice a názvu (Visual Basic)
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
ms.openlocfilehash: 78c5303461ecf25a1487e072f4f6be25bde98dca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587460"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>Předávání argumentů podle pozice a názvu (Visual Basic)
Při volání `Sub` nebo `Function` postup, můžete předat argumenty *umístěním* – v pořadí, v jakém jsou uvedeny v definici procedury – nebo můžete předat je *podle názvu*, bez ohledem na pozici.  
  
 Při předání argumentu podle názvu, můžete zadat argument deklarován název následovaný dvojtečkou a znaménko rovná se (`:=`) následovaný hodnotu argumentu. Můžete zadat pojmenované argumenty v libovolném pořadí.  
  
 Například následující `Sub` procedura má tři argumenty:  
  
 [!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]  
  
 Při volání tohoto postupu můžete zadat argumentů podle pozice, podle názvu nebo s použitím kombinaci obou.  
  
## <a name="passing-arguments-by-position"></a>Předávání argumentů podle pozice  
 Můžete volat `Display` metoda s argumenty předány podle pozice a oddělených čárkami, jak je znázorněno v následujícím příkladu:  
  
[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)] 
  
 Pokud volitelný argument v seznamu poziční argument vynecháte, je třeba držet místo něj čárkou. Následující příklad volá `Display` metody bez `age` argument:  
  
[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)] 
  
## <a name="passing-arguments-by-name"></a>Předávání argumentů podle názvu  
 Alternativně můžete volat `Display` s argumenty předány podle názvu, také oddělených čárkami, jak je znázorněno v následujícím příkladu:  
  
[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)] 

 Předávání argumentů podle názvu tímto způsobem je užitečné zejména při volání procedury, která má více než jeden volitelný argument. Pokud zadáte argumenty podle názvu, není nutné používat po sobě jdoucích čárek k označení chybí poziční argumenty. Předávání argumentů podle názvu také usnadňuje sledovat, které argumenty předáváte a ty, které se vynechá.  
  
## <a name="mixing-arguments-by-position-and-by-name"></a>Kombinace argumentů podle pozice a názvu  

Můžete zadat argumentů podle pozice a podle názvu ve volání jedné postupem, jak je znázorněno v následujícím příkladu:  
  
[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)] 
  
 V předchozím příkladu je nezbytné k uložení místo vynechaný žádné další čárka `age` argument, protože `birth` je předán podle názvu.  
  
Ve verzích jazyka Visual Basic před 15.5 Pokud dodání argumentů podle pozice a názvu, poziční argumenty kombinaci musí všechny být první. Jakmile zadáte argument podle názvu, všechny zbývající argumenty musí všechny předávat podle názvu.  Například následující volání `Display` metoda zobrazí chyba kompilátoru [BC30241: Očekával se pojmenovaný argument](../../../misc/bc30241.md).

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)] 

Od verze 15.5 jazyka Visual Basic, poziční argumenty lze použít pojmenované argumenty v případě koncové poziční argumenty nejsou ve správné pozici. Je-li zkompilovat v rámci jazyka Visual Basic 15.5, předchozího volání `Display` metoda se zkompiluje úspěšně a už vygeneruje Chyba kompilátoru [BC30241](../../../misc/bc30241.md).  

Tato schopnost kombinovat a párovat s názvem a poziční argumenty v libovolném pořadí je zvlášť užitečné, pokud chcete použít pojmenovaný argument, aby váš kód lépe čitelný. Například následující `Person` konstruktoru třídy vyžaduje dva argumenty typu `Person`, které může být `Nothing`. 

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)] 

Smíšené pojmenované a poziční argumenty, které pomáhá provádět záměru kódu vymazat při použití hodnoty `father` a `mother` argumenty `Nothing`:

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)] 

Pro použít poziční argumenty s pojmenovanými argumenty, je nutné přidat následující prvek do projektu jazyka Visual Basic (\*.vbproj) souboru:

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

Další informace najdete v části [nastavení verze jazyka Visual Basic](../../../language-reference/configure-language-version.md).

## <a name="restrictions-on-supplying-arguments-by-name"></a>Omezení pro poskytnutí argumentů podle názvu  

Argumenty nelze předávat podle názvu myslet povinnými argumenty. Vynechat jenom volitelné argumenty.  
  
Pole parametrů nelze předat podle názvu. Je to proto, že při volání postupu zadáte nekonečný počet oddělovači argumentů pole parametrů a kompilátor nelze přidružit k více než jeden argument jeden název.  
  
## <a name="see-also"></a>Viz také:
- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)
- [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)
- [Nepovinné parametry](./optional-parameters.md)
- [Pole parametrů](./parameter-arrays.md)
- [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)
- [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
