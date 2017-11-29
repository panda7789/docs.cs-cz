---
title: "Postupy: Přetížení procedury, která přebírá volitelné parametry (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b4a863944d4f9ab265aab52578fbb704ca376de5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a>Postupy: Přetížení procedury, která přebírá volitelné parametry (Visual Basic)
Pokud procedury má jeden nebo více [volitelné](../../../../visual-basic/language-reference/modifiers/optional.md) parametry, nelze definovat přetížené verze odpovídající některý z jeho implicitní přetížení. Další informace najdete v tématu "Implicitní přetížení pro volitelné parametry" v [aspekty přetížení procedur](./considerations-in-overloading-procedures.md).  
  
## <a name="one-optional-parameter"></a>Jeden volitelný parametr  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a>Chcete-li přetížení procedury, která přijímá jeden parametr volitelný  
  
1.  Zápis `Sub` nebo `Function` deklarace příkaz, který obsahuje volitelný parametr v seznamu parametrů. Nepoužívejte `Optional` – klíčové slovo v této verzi přetížená.  
  
2.  Předcházet `Sub` nebo `Function` – klíčové slovo s [přetížení](../../../../visual-basic/language-reference/modifiers/overloads.md) – klíčové slovo.  
  
3.  Psaní kódu postup, který by měl být spuštěn při volání kód poskytuje nepovinný argument.  
  
4.  Ukončení procesu se `End Sub` nebo `End Function` příkaz podle potřeby.  
  
5.  Zápis druhý příkaz deklaraci, která je stejná jako první deklaraci s tím rozdílem, že v seznamu parametrů neobsahoval volitelný parametr.  
  
6.  Psaní kódu postup, který by měl být spuštěn při volání kód neposkytuje nepovinný argument. Ukončení procesu se `End Sub` nebo `End Function` příkaz podle potřeby.  
  
     Následující příklad ukazuje postup definovaný s volitelný parametr ekvivalentní sadu přetížené dva postupy a nakonec příklady neplatný i platný přetížené verze.  
  
     [!code-vb[VbVbcnProcedures#59](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_2.vb)]  
  
     [!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_3.vb)]  
  
## <a name="multiple-optional-parameters"></a>Více volitelné parametry  
 Pro proceduru s více než jeden volitelný parametr musíte obvykle více než dvě přetížené verze. Například pokud existují dvě volitelné parametry a volání kód můžete zadat nebo vynechejte každé z nich nezávisle na druhém, musíte čtyři přetížené verze, jeden pro jednotlivých možných kombinací zadané argumenty.  
  
 Hodnota se zvyšuje počet volitelné parametry, zvyšuje složitost přetížení. Pokud některé kombinace zadané argumenty nejsou přijatelné, pro volitelné parametry N potřebujete 2 ^ N přetížený verze. V závislosti na povaze postup je možné, že přehlednost logiky opravňuje navíc úsilí definice všechny přetížené verze.  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a>Přetížení procedury, která má více než jeden nepovinný parametr  
  
1.  Určete, které kombinace zadaný volitelné argumenty jsou přijatelné pro logiku procedury. Pokud jeden volitelný parametr závisí na jiném, mohou se vyskytnout nepřijatelné kombinaci. Například pokud jméno partnera přijímá jeden parametr a jiné přijímá manžela stáří, kombinace argumentů zadávání stáří, ale bez názvu nepřijatelné.  
  
2.  Pro každou přijatelné kombinaci zadaný volitelné argumenty, zápisu `Sub` nebo `Function` deklarace příkaz, který definuje odpovídající seznam parametrů. Nepoužívejte `Optional` – klíčové slovo.  
  
3.  V každé deklaraci předcházet `Sub` nebo `Function` – klíčové slovo s [přetížení](../../../../visual-basic/language-reference/modifiers/overloads.md) – klíčové slovo.  
  
4.  Následující každá deklarace psát kód postup, který by měl spustit, když kód volání poskytuje seznam argumentů odpovídající seznam parametrů tohoto prohlášení.  
  
5.  Terminate – každý postup s `End Sub` nebo `End Function` příkaz podle potřeby.  
  
## <a name="see-also"></a>Viz také  
 [Postupy](./index.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Volitelné parametry](./optional-parameters.md)  
 [Pole parametrů](./parameter-arrays.md)  
 [Přetížení procedury](./procedure-overloading.md)  
 [Řešení potíží s procedurami](./troubleshooting-procedures.md)  
 [Postupy: definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Postupy: volání přetížené procedury](./how-to-call-an-overloaded-procedure.md)  
 [Postupy: přetížení procedury, která přebírá nekonečný počet parametrů](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Řešení přetížení](./overload-resolution.md)
