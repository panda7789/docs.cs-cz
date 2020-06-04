---
title: Parametry a argumenty procedury
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], argument lists
- values [Visual Basic], passing to procedures
- arguments [Visual Basic], passing
- procedures [Visual Basic], parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic procedures
- parameters [Visual Basic], lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- argument lists [Visual Basic]
- procedures [Visual Basic], parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
ms.openlocfilehash: 178206ca2ee103bbdb5a4ac03bca0df903c8c5d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406713"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a>Parametry a argumenty procedury (Visual Basic)
Ve většině případů procedura potřebuje nějaké informace o okolnostech, ve kterých byla volána. Postup, který provádí opakované nebo sdílené úkoly, používá pro každé volání jiné informace. Tyto informace se skládají z proměnných, konstant a výrazů, které procedury předáte při volání.  
  
 *Parametr* představuje hodnotu, kterou procedura očekává při volání metody. Deklarace procedury definuje její parametry.  
  
 Můžete definovat proceduru bez parametrů, jeden parametr nebo více než jeden. Část definice procedury, která určuje parametry, se nazývá *seznam parametrů*.  
  
 *Argument* představuje hodnotu, kterou zadáte parametru procedury při volání procedury. Volající kód dodává argumenty při volání procedury. Část volání procedury, která určuje argumenty, se nazývá *seznam argumentů*.  
  
 Následující ilustrace znázorňuje kód, který volá proceduru `safeSquareRoot` ze dvou různých míst. První volání předává hodnotu proměnné `x` (4,0) parametru `number` a návratová hodnota v `root` (2,0) je přiřazena proměnné `y` . Druhé volání předá hodnotu literálu 9,0 `number` a přiřadí návratovou hodnotu (3,0) proměnné `z` .  
  
 ![Diagram, který ukazuje předání argumentu parametru](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 Další informace najdete v tématu [rozdíly mezi parametry a argumenty](./differences-between-parameters-and-arguments.md).  
  
## <a name="parameter-data-type"></a>Datový typ parametru  
 Můžete definovat datový typ pro parametr pomocí `As` klauzule v jeho deklaraci. Například následující funkce přijímá řetězec a celé číslo.  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 Pokud je přepínač pro kontrolu typu ([Option Strict](../../../language-reference/statements/option-strict-statement.md)) `Off,` `As` klauzule Optional, s výjimkou toho, že pokud některý parametr používá, musí je použít všechny parametry. Pokud je kontrola typu `On` , `As` je vyžadována klauzule pro všechny parametry procedury.  
  
 Pokud volající kód očekává zadání argumentu s datovým typem, který se liší od odpovídajícího parametru, například `Byte` s `String` parametrem, musí provést jednu z následujících akcí:  
  
- Poskytněte pouze argumenty s datovými typy, které se rozšíří na datový typ parametru;  
  
- Nastavte `Option Strict Off` na povolení implicitních zužujících převodů; nebo  
  
- K explicitnímu převodu datového typu použijte klíčové slovo Conversion.  
  
### <a name="type-parameters"></a>Parametry typu  
 *Obecný postup* také definuje jeden nebo více *parametrů typu* kromě jeho běžných parametrů. Obecný postup umožňuje volajícímu kódu předat různým datovým typům při každém volání procedury, takže může přizpůsobit datové typy na požadavky každého jednotlivého volání. Viz [Obecné procedury v Visual Basic](../data-types/generic-procedures.md).  
  
## <a name="see-also"></a>Viz také

- [Procedury](./index.md)
- [Procedury Sub](./sub-procedures.md)
- [Procedury funkcí](./function-procedures.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Procedury operátoru](./operator-procedures.md)
- [Postupy: Definování parametru pro proceduru](./how-to-define-a-parameter-for-a-procedure.md)
- [Postupy: Předání argumentů proceduře](./how-to-pass-arguments-to-a-procedure.md)
- [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)
- [Přetížení procedury](./procedure-overloading.md)
- [Převody typů v jazyce Visual Basic](../data-types/type-conversions.md)
