---
title: 'Postupy: Vytvoření procedury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: da4cc299fbe35702990a62b5bf824e3ac71d5902
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-procedure-visual-basic"></a>Postupy: Vytvoření procedury (Visual Basic)
Uzavřete procedury mezi počáteční příkaz deklarace (`Sub` nebo `Function`) a příkazu koncová deklarace (`End Sub` nebo `End Function`). Všechny postup kód je mezi těmito příkazy.  
  
 Procedury nemůže obsahovat jinou proceduru, jeho počáteční a koncovou příkazy musí být mimo jiné procedury.  
  
 Pokud máte kód, který provádí stejnou úlohu na různých místech, můžete napsat úlohy jednou jako proceduru a poté ji volat z různých místech v kódu.  
  
### <a name="to-create-a-procedure-that-does-not-return-a-value"></a>K vytvoření procedury, která nevrátí hodnotu  
  
1.  Mimo jiné postup použijte `Sub` prohlášení, za nímž následuje `End Sub` příkaz.  
  
2.  V `Sub` prohlášení, postupujte podle `Sub` – klíčové slovo s názvem postup, pak se seznam parametrů v závorkách.  
  
3.  Umístit postup kód příkazy mezi `Sub` a `End Sub` příkazy.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>K vytvoření procedury, která vrátí hodnotu  
  
1.  Mimo jiné postup použijte `Function` prohlášení, za nímž následuje `End Function` příkaz.  
  
2.  V `Function` prohlášení, postupujte podle `Function` – klíčové slovo s názvem postup, pak se seznam parametrů v závorkách a potom `As` klauzule určující datový typ vrácené hodnoty.  
  
3.  Umístit postup kód příkazy mezi `Function` a `End Function` příkazy.  
  
4.  Použití `Return` příkaz k vrácení hodnoty volání kódu.  
  
### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a>Připojit nový postup s původním, opakovaných bloky kódu  
  
1.  Zajistěte, aby že definovat nový postup na místě, kde původní kód k němu má přístup.  
  
2.  V bloku vaše staré, opakovaných kódu nahraďte příkazy, které provádějí opakované úlohy s jediný příkaz, který volá `Sub` nebo `Function` postupu.  
  
3.  Pokud je vaše postupu `Function` , vrátí hodnotu, ujistěte se, že volání údajů provádí akce s vrácené hodnoty, jako je například ukládání do proměnné, jinak hodnota budou ztraceny.  
  
## <a name="example"></a>Příklad  
 Následující `Function` postup vypočítá nejdelší straně nebo přepony trojúhelníku vpravo, pro zbývající dvě strany zadané hodnoty.  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure_1.vb)]  
  
## <a name="see-also"></a>Viz také

 [Procedury](./index.md)  
 [Procedury Sub](./sub-procedures.md)  
 [Procedury funkce](./function-procedures.md)  
 [Procedury vlastnosti](./property-procedures.md)  
 [Procedury operátoru](./operator-procedures.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Rekurzivní procedury](./recursive-procedures.md)  
 [Přetížení procedury](./procedure-overloading.md)  
 [Objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Objektově orientované programování (Visual Basic)](../../concepts/object-oriented-programming.md)  
