---
title: 'Postupy: Přetížení procedury, která přebírá volitelné parametry'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
ms.openlocfilehash: 9ae6818b1e03ccd00ed554e98690e02ffa45de99
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387839"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a>Postupy: Přetížení procedury, která přebírá volitelné parametry (Visual Basic)
Pokud má procedura jeden nebo více [volitelných](../../../language-reference/modifiers/optional.md) parametrů, nelze definovat přetíženou verzi odpovídající jakémukoli z jeho implicitních přetížení. Další informace naleznete v části "implicitní přetížení pro volitelné parametry" v tématu Co je [třeba v postupech přetížení](./considerations-in-overloading-procedures.md).  
  
## <a name="one-optional-parameter"></a>Jeden volitelný parametr  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a>Přetížení procedury, která přijímá jeden volitelný parametr  
  
1. Napsat `Sub` `Function` příkaz deklarace nebo, který obsahuje volitelný parametr v seznamu parametrů. Nepoužívejte `Optional` klíčové slovo v této přetížené verzi.  
  
2. Předchází `Sub` klíčové slovo or `Function` s klíčovým slovem [přetížení](../../../language-reference/modifiers/overloads.md) .  
  
3. Napište kód procedury, který by měl být proveden, když volající kód dodá volitelný argument.  
  
4. V případě potřeby postup ukončete `End Sub` pomocí `End Function` příkazu nebo.  
  
5. Napište druhý příkaz deklarace, který je totožný s první deklarací s tím rozdílem, že nezahrnuje volitelný parametr v seznamu parametrů.  
  
6. Napište kód procedury, který by měl být proveden, když volající kód nedodá nepovinný argument. V případě potřeby postup ukončete `End Sub` pomocí `End Function` příkazu nebo.  
  
     Následující příklad ukazuje proceduru, která je definována s volitelným parametrem, ekvivalentní sadou dvou přetížených procedur a nakonec příklady obou neplatných a platných přetížených verzí.  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a>Několik volitelných parametrů  
 Postup s více než jedním volitelným parametrem obvykle vyžaduje více než dvě přetížené verze. Například pokud existují dva volitelné parametry a volající kód může dodat nebo vynechat každou z nich nezávisle na sobě, potřebujete čtyři přetížené verze, jednu pro každou možnou kombinaci zadaných argumentů.  
  
 Jak se zvyšuje počet nepovinných parametrů, složitost přetížení se zvyšuje. Pokud nejsou některé kombinace dodaných argumentů přijatelné, pro N nepovinné parametry potřebujete 2 ^ N přetížené verze. V závislosti na povaze postupu se můžete setkat s tím, že jasnost logiky odůvodňuje další úsilí o definování všech přetížených verzí.  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a>Přetížení procedury, která přijímá více než jeden volitelný parametr  
  
1. Určete, které kombinace dodaných volitelných argumentů jsou přijatelné pro logiku procedury. Pokud jeden volitelný parametr závisí na jiném, může dojít k nepřijatelné kombinaci. Například pokud jeden parametr akceptuje jméno osoby a druhý akceptuje stáří osoby, kombinace argumentů, které poskytují věk, ale vynechání názvu je nepřijatelná.  
  
2. Pro každou přijatelnou kombinaci dodaných volitelných argumentů napište `Sub` `Function` příkaz nebo deklaraci příkazu, který definuje odpovídající seznam parametrů. Nepoužívejte `Optional` klíčové slovo.  
  
3. V každé deklaraci uveďte klíčové slovo `Sub` OR `Function` s klíčovým slovem [Overloads](../../../language-reference/modifiers/overloads.md) .  
  
4. Po každé deklaraci zapište kód procedury, která by měla být provedena, když volající kód dodá seznam argumentů odpovídajících tomuto seznamu parametrů deklarace.  
  
5. V případě potřeby ukončete jednotlivé postupy pomocí `End Sub` `End Function` příkazu nebo.  
  
## <a name="see-also"></a>Viz také

- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Volitelné parametry](./optional-parameters.md)
- [Pole parametrů](./parameter-arrays.md)
- [Přetížení procedury](./procedure-overloading.md)
- [Řešení potíží s procedurami](./troubleshooting-procedures.md)
- [Postupy: Definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Postupy: Volání přetížené procedury](./how-to-call-an-overloaded-procedure.md)
- [Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů.](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Rozlišení přetěžování](./overload-resolution.md)
