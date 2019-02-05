---
title: Rekurzivní procedury (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
ms.openlocfilehash: b5cbe0dfa8053a93cde9c92ffe87f0eae15d3efd
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/05/2019
ms.locfileid: "55739290"
---
# <a name="recursive-procedures-visual-basic"></a>Rekurzivní procedury (Visual Basic)
A *rekurzivní* postup je takový, který zavolá sama sebe. Většinou to není nejúčinnější způsob psaní kódu jazyka Visual Basic.  
  
 Následující postup používá rekurze pro výpočet faktoriálu původní argument.  
  
 [!code-vb[VbVbcnProcedures#51](./codesnippet/VisualBasic/recursive-procedures_1.vb)]  
  
## <a name="considerations-with-recursive-procedures"></a>Informace o rekurzivní procedury  
 **Omezující podmínky**. Je třeba navrhnout rekurzivní procedury pro testování nejméně jedné podmínky, které dokáže ukončit rekurze, a také musí zpracovávat tento případ, ve kterém je splněna žádná z těchto podmínek v rámci dostatečný počet rekurzivních volání. Bez nejméně jedné podmínky, které mohou být splněny bez navrácení služeb po spuštění procedury vysokým rizikem provedení v nekonečné smyčce.  
  
 **Využití paměti**. Vaše aplikace má omezené množství místa pro místní proměnné. Pokaždé, když procedury zavolá sama sebe, používá více toto místo pro další kopie, které své místní proměnné. Pokud tento proces pokračuje po neomezenou dobu, nakonec způsobí <xref:System.StackOverflowException> chyby.  
  
 **Efektivita**. Můžete nahradit téměř vždy smyčku rekurze. Smyčka nemá režii předávání argumentů, inicializace úložiště a vrací hodnoty. Výkon může být mnohem lepší bez rekurzivní volání.  
  
 **Vzájemná rekurze**. Velmi nízký výkon nebo dokonce nekonečnou smyčku, všimnout dva postupy volání mezi sebou. Takový návrh stejným problémům jako v postupu jeden rekurzivní uvede, ale může být obtížnější rozpoznání a ladění.  
  
 **Volání se závorkami**. Když `Function` proceduru volá rekurzivně sama sebe, je nutné postupovat podle název procedury se závorkami, i v případě, že neexistuje žádný seznam argumentů. V opačném případě je název funkce používá jako návratový typ funkce.  
  
 **Testování**. Pokud píšete rekurzivní procedury, měli byste ho otestovat velmi pečlivě zajistit, aby že vždy splňuje některé omezující podmínky. Také se ujistěte, že nelze spustit nedostatek paměti z důvodu existence příliš mnoho rekurzivních volání.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.StackOverflowException>
- [Procedury](./index.md)
- [Procedury Sub](./sub-procedures.md)
- [Procedury funkce](./function-procedures.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Procedury operátoru](./operator-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Přetížení procedury](./procedure-overloading.md)
- [Řešení potíží s procedurami](./troubleshooting-procedures.md)
- [Struktury smyčky](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
