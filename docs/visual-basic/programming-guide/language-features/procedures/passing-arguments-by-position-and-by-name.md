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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49e313b2d5aa8302ea4b99e643e09f7b43659785
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>Předávání argumentů podle pozice a názvu (Visual Basic)
Při volání `Sub` nebo `Function` postupu můžete předat argumenty *umístěním* – v pořadí, ve kterém se zobrazí v postupu pro definici – nebo můžete je předat *podle názvu*, bez ohledem na pozici.  
  
 Při předání argumentu podle názvu, zadáte argument je deklarovaný název následovaný dvojtečkou a symbolem rovná (`:=`), za nímž následují hodnota argumentu. Můžete zadat pojmenované argumenty v libovolném pořadí.  
  
 Například následující `Sub` procedura používá tři argumenty:  
  
 [!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]  
  
 Při volání tohoto postupu můžete zadat argumentů podle pozice, podle názvu nebo pomocí kombinaci těchto dvou možností.  
  
## <a name="passing-arguments-by-position"></a>Předávání argumentů podle pozice  
 Můžete volat `Display` metoda s argumenty předaná pozice a oddělená čárkami, jak je znázorněno v následujícím příkladu:  
  
[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)] 
  
 Pokud vynecháte za volitelným argumentem v seznamu poziční argument, musí obsahovat příslušné místo oddělujte čárkami. Následující příklad volání `Display` metoda bez `age` argument:  
  
[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)] 
  
## <a name="passing-arguments-by-name"></a>Předávání argumentů podle názvu  
 Alternativně můžete volat `Display` s argumentů předaných podle názvu, také oddělená čárkami, jak je znázorněno v následujícím příkladu:  
  
[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)] 

 Předávání argumentů podle názvu tímto způsobem je obzvláště užitečná při volání procedury, která má více než jeden nepovinný argument. Pokud zadáte argumenty podle názvu, nemáte použít po sobě jdoucích čárkami k označení chybí poziční argumenty. Předávání argumentů podle názvu taky usnadní ke sledování které argumenty jsou předávání a ty, které jsou vynechá.  
  
## <a name="mixing-arguments-by-position-and-by-name"></a>Kombinování argumentů podle pozice a názvu  

Argumentů podle pozice a podle názvu ve volání jedinou proceduru, můžete zadat, jak je znázorněno v následujícím příkladu:  
  
[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)] 
  
 V předchozím příkladu, je potřeba k umístění na místo vynechání žádné další čárkami `age` argument, protože `birth` je předán podle názvu.  
  
Ve verzi jazyka Visual Basic před 15,5 když zadáte argumenty podle směs pozice a názvu, poziční argumenty musí všechny nejdřív se musí uvést. Jakmile zadáte argument podle názvu, všechny zbývající argumenty, musí všechny být předán podle názvu.  Například následující volání do `Display` metoda zobrazí chyba kompilátoru [BC30241: argument očekávání s názvem](../../../misc/bc30241.md).

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)] 

Od verze Visual Basic 15,5, poziční argumenty lze použít pojmenované argumenty v případě koncová poziční argumenty jsou ve správné pozici. Pokud zkompilovat pod 15,5 Visual Basic, předchozí volání `Display` metoda zkompiluje úspěšně a už vygeneruje Chyba kompilátoru [BC30241](../../../misc/bc30241.md).  

Tato schopnost kombinovat a párovat pojmenované a poziční argumenty v libovolném pořadí je zvláště užitečné, pokud chcete používat s názvem argument tak čitelnost kódu. Například následující `Person` konstruktoru třídy vyžaduje dva argumenty typu `Person`, které může být `Nothing`. 

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)] 

Pomocí smíšený pojmenované a poziční argumenty pomáhá, aby byl záměr kódu vymazat, když hodnota `father` a `mother` argumenty je `Nothing`:

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)] 

Chcete-li postupovat podle poziční argumenty s pojmenované argumenty, je nutné přidat následující element do projektu jazyka Visual Basic (\*.vbproj) souboru:

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

## <a name="restrictions-on-supplying-arguments-by-name"></a>Omezení pro zadávání argumenty podle názvu  

Nelze předat argumenty podle názvu, abyste nemuseli zadávat povinnými argumenty. Pouze volitelné argumenty, můžete vynechat.  
  
Pole parametrů nelze předat podle názvu. Je to proto, že při volání postupu zadáte nekonečný počet textový soubor s oddělovači argumenty pro parametr pole a kompilátor nelze přidružit více než jeden argument s jedním názvem.  
  
## <a name="see-also"></a>Viz také  
 [Procedury](./index.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)  
 [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)  
 [Nepovinné parametry](./optional-parameters.md)  
 [Pole parametrů](./parameter-arrays.md)  
 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
