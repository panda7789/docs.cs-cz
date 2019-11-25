---
title: Volitelné parametry
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [Visual Basic], optional
- Visual Basic code, procedures
- procedures [Visual Basic], optional arguments
- optional arguments
- named arguments [Visual Basic], and optional arguments
- optional parameters
- Optional keyword [Visual Basic], optional arguments
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], and named arguments
ms.assetid: 398d2845-1069-4e94-b934-a73b545c8b87
ms.openlocfilehash: d859f7eaaefa051cfdf703d8589bc8c679a3ee85
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345968"
---
# <a name="optional-parameters-visual-basic"></a>Volitelné parametry (Visual Basic)
Můžete určit, že parametr procedury je volitelný, a při volání této procedury se nemusí zadávat žádný argument. *Optional parameters* are indicated by the `Optional` keyword in the procedure definition. Platí následující pravidla:  
  
- Každý volitelný parametr v definici procedury musí mít výchozí hodnotu.  
  
- Výchozí hodnota volitelného parametru musí být konstantní výraz.  
  
- Každý parametr, který v definici procedury následuje za volitelným parametrem, musí být také volitelný.  
  
 Následující syntaxe znázorňuje deklaraci procedury s volitelným parametrem:  
  
```vb  
Sub name(ByVal parameter1 As datatype1, Optional ByVal parameter2 As datatype2 = defaultvalue)  
```  
  
## <a name="calling-procedures-with-optional-parameters"></a>Volání procedur s volitelnými parametry  
 Při volání procedury s volitelným parametrem se můžete rozhodnout, zda zadáte argument. Pokud ho nezadáte, použije procedura výchozí hodnotu deklarovanou pro tento parametr.  
  
 Pokud v seznamu argumentů vynecháte jeden nebo více volitelných argumentů, označíte jejich pozice pomocí po sobě jdoucích čárek. V následujícím ukázkovém volání je zadán první a čtvrtý argument, ale nikoli druhý a třetí:  
  
```vb  
Sub name(argument 1, , , argument 4)  
```  
  
 The following example makes several calls to the `MsgBox` function. `MsgBox` has one required parameter and two optional parameters.  
  
 The first call to `MsgBox` supplies all three arguments in the order that `MsgBox` defines them. Ve druhém volání je zadán pouze povinný argument. Ve třetím a čtvrtém volání je zadán první a třetí argument. Třetí volání tak činí podle pozice a čtvrté volání podle názvu.  
  
 [!code-vb[VbVbcnProcedures#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#47)]  
  
## <a name="determining-whether-an-optional-argument-is-present"></a>Určení, zda existuje volitelný argument  
 Procedura nedokáže za běhu zjistit, zda byl daný argument vynechán nebo zda volající kód explicitně poskytuje výchozí hodnotu. Pokud to potřebujete rozlišit, můžete jako výchozí nastavit nějakou nepravděpodobnou hodnotu. The following procedure defines the optional parameter `office`, and tests for its default value, `QJZ`, to see if it has been omitted in the call:  
  
 [!code-vb[VbVbcnProcedures#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#46)]  
  
 If the optional parameter is a reference type such as a `String`, you can use `Nothing` as the default value, provided this is not an expected value for the argument.  
  
## <a name="optional-parameters-and-overloading"></a>Volitelné parametry a přetěžování  
 Proceduru s volitelnými parametry lze definovat také pomocí přetěžování. Pokud máte jeden volitelný parametr, můžete definovat dvě přetížené verze procedury – jednu s parametrem a druhou bez parametru. S rostoucím počtem volitelných parametrů se zvyšuje složitost. Výhodou ale je, že máte absolutní jistotu, zda volající program poskytl jednotlivé volitelné argumenty.  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)
- [Předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md)
- [Pole parametrů](./parameter-arrays.md)
- [Přetížení procedury](./procedure-overloading.md)
- [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)
- [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
