---
title: 'Postupy: Vytvořit procedury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: 06fed04a0ebe7a0b3111a94308d15d01bcf47c1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636531"
---
# <a name="how-to-create-a-procedure-visual-basic"></a>Postupy: Vytvořit procedury (Visual Basic)
Použijte postup mezi počáteční příkazu deklarace (`Sub` nebo `Function`) a koncové příkazu deklarace (`End Sub` nebo `End Function`). Kód všechny procedury leží mezi těmito příkazy.  
  
 Postup nemůže obsahovat jinou proceduru, takže jeho počáteční a koncové příkazy musí být mimo všechny procedury.  
  
 Pokud máte kód, který provádí stejnou úlohu na různých místech, můžete napsat úlohy jednou jako postup a následně ji zavolat z různých míst v kódu.  
  
### <a name="to-create-a-procedure-that-does-not-return-a-value"></a>Chcete-li vytvořit proceduru, která nevrací hodnotu  
  
1.  Mimo všechny procedury, použijte `Sub` příkazu, za nímž následuje `End Sub` příkazu.  
  
2.  V `Sub` prohlášení, postupujte `Sub` – klíčové slovo s názvem podle postupu, pak se seznam parametrů v závorkách.  
  
3.  Umístit příkazy kódu podle postupu mezi `Sub` a `End Sub` příkazy.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>Chcete-li vytvořit proceduru, která vrací hodnotu  
  
1.  Mimo všechny procedury, použijte `Function` příkazu, za nímž následuje `End Function` příkazu.  
  
2.  V `Function` příkazu, postupujte `Function` – klíčové slovo s názvem podle postupu, pak se seznam parametrů v závorkách a potom `As` klauzule určující datový typ vrácené hodnoty.  
  
3.  Umístit příkazy kódu podle postupu mezi `Function` a `End Function` příkazy.  
  
4.  Použití `Return` příkazu vrátí hodnotu volajícímu kódu.  
  
### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a>Připojit nový postup se starou, opakované bloky kódu  
  
1.  Zkontrolujte, že můžete definovat nové postupu na místě, kde původní kód má přístup k němu.  
  
2.  V bloku vaše staré, opakované kódu nahraďte příkazy, které provádějí opakované úlohy s jeden příkaz, který volá `Sub` nebo `Function` postup.  
  
3.  Pokud je vaše postup `Function` , která vrací hodnotu, ujistěte se, že volání příkazu provede akci s vrácenou hodnotu, jako je ukládání do proměnné, jinak hodnota se ztratí.  
  
## <a name="example"></a>Příklad  
 Následující `Function` postup vypočítá nejdelší strana nebo přepony pravoúhlého trojúhelníku, pro obě strany zadané hodnoty.  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure_1.vb)]  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Procedury Sub](./sub-procedures.md)
- [Procedury funkce](./function-procedures.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Procedury operátoru](./operator-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Rekurzivní procedury](./recursive-procedures.md)
- [Přetížení procedury](./procedure-overloading.md)
- [Objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Objektově orientované programování (Visual Basic)](../../concepts/object-oriented-programming.md)
