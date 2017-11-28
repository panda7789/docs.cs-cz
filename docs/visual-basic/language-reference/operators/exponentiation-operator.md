---
title: "^ – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponention
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e7159f289b687055c7d75cc8da58d6f76607a83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a>^ – operátor (Visual Basic)
Umocní jedno číslo na mocninu vyjádřenou druhým číslem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
number ^ exponent  
```  
  
## <a name="parts"></a>Součásti  
 `number`  
 Požadováno. Jakýkoli číselný výraz.  
  
 `exponent`  
 Požadováno. Jakýkoli číselný výraz.  
  
## <a name="result"></a>Výsledek  
 Výsledkem je `number` umocněné z `exponent`, vždy jako `Double` hodnotu.  
  
## <a name="supported-types"></a>Podporované typy  
 `Double`. Operandy žádné jiného typu se převedou na `Double`.  
  
## <a name="remarks"></a>Poznámky  
 Visual Basic vždy provede exponenciální zápis v [dvojitý datový typ](../../../visual-basic/language-reference/data-types/double-data-type.md).  
  
 Hodnota `exponent` může být zlomkové záporné nebo obojí.  
  
 Pokud se více než jeden exponenciální zápis se provádí v jeden výraz `^` operátor je vyhodnocena jako jeho zjištění zleva doprava.  
  
> [!NOTE]
>  `^` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura. Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `^` operátor umožňuje aktivovat číslo na mocninu exponentem. Výsledkem je první operand umocněné druhého.  
  
 [!code-vb[VbVbalrOperators#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-operator_1.vb)]  
  
 V předchozím příkladu poskytne následující výsledky:  
  
 `exp1`je nastavena na 4 (2 spolehlivosti).  
  
 `exp2`je nastavena na 19683 (na třetí, 3 pak tuto hodnotu na třetí).  
  
 `exp3`je nastavena na-125 (-5 umocněnou).  
  
 `exp4`je nastavena na 625 (čtvrtý exponentem -5).  
  
 `exp5`je nastaven na hodnotu 2 (datové krychle kořen 8).  
  
 `exp6`je nastavena na 0,5 (1.0 dělený kořenové datové krychle 8).  
  
 Poznámka: význam závorkách ve výrazech v předchozím příkladu. Z důvodu *operátorů*, Visual Basic obvykle provádí `^` i unární operátor před všech ostatních `–` operátor. Pokud `exp4` a `exp6` měl vypočítána bez závorek, by je tvořen následující výsledky:  
  
 `exp4 = -5 ^ 4`se počítá jako – (5 čtvrtý exponentem), což by způsobilo-625.  
  
 `exp6 = 8 ^ -1.0 / 3.0`se počítá jako (8 power – 1 nebo 0,125) dělený 3.0, který by způsobilo 0.041666666666666666666666666666667.  
  
## <a name="see-also"></a>Viz také  
 [^ = – Operátor](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)  
 [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Aritmetické operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
