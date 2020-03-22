---
title: Rozlišení přetěžování
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- overload resolution
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedure overloading [Visual Basic], overload resolution
- signatures [Visual Basic], procedure
- overloads [Visual Basic], resolution
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
ms.openlocfilehash: 84d52bbbfb34c2e5d67ed6a1810ab3e32fafda22
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266869"
---
# <a name="overload-resolution-visual-basic"></a>Rozlišení přetěžování (Visual Basic)
Když kompilátor jazyka narazí na volání procedury, která je definována v několika přetížených verzích, musí kompilátor rozhodnout, které přetížení volat. Provede to provedením následujících kroků:  
  
1. **Usnadnění.** Eliminuje jakékoli přetížení s úrovní přístupu, která zabraňuje volání kódu z volání.  
  
2. **Počet parametrů.** Eliminuje jakékoli přetížení, které definuje jiný počet parametrů, než jsou zadány ve volání.  
  
3. **Datové typy parametrů.** Kompilátor dává metody instance přednost před metodami rozšíření. Pokud je nalezena jakákoli metoda instance, která vyžaduje pouze rozšiřující převody tak, aby odpovídaly volání procedury, jsou vynechány všechny metody rozšíření a kompilátor pokračuje pouze s kandidáty metody instance. Pokud není nalezena žádná taková metoda instance, pokračuje metodou instance i rozšíření.  
  
     V tomto kroku eliminuje přetížení, pro které datové typy volající argumenty nelze převést na typy parametrů definované v přetížení.  
  
4. **Zužující převody.** Eliminuje jakékoli přetížení, které vyžaduje zužující převod z volajících typů argumentů na definované typy parametrů. To platí bez ohledu na to, zda `On` je `Off`přepínač kontroly typu ([Příkaz striktní možnosti](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) nebo .  
  
5. **Nejméně se rozšiřuje.** Kompilátor bere v úvahu zbývající přetížení v párech. Pro každou dvojici porovnává datové typy definovaných parametrů. Pokud typy v jednom z přetížení všechny rozšířit na odpovídající typy v druhé, kompilátor eliminuje druhé. To znamená, že zachová přetížení, které vyžaduje nejmenší množství rozšíření.  
  
6. **Jediného kandidáta.** Pokračuje s ohledem přetížení v párech, dokud zůstane pouze jedno přetížení a řeší volání tohoto přetížení. Pokud kompilátor nemůže snížit přetížení na jednoho kandidáta, generuje chybu.  
  
 Následující obrázek znázorňuje proces, který určuje, které ze sady přetížených verzí volat.  
  
 ![Vývojový diagram procesu řešení přetížení](./media/overload-resolution/determine-overloaded-version.gif "Řešení mezi přetížené verze")
  
 Následující příklad ilustruje tento proces řešení přetížení.  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 V prvním volání kompilátor eliminuje první přetížení, protože typ`Short`prvního argumentu ( ) se`Byte`zužuje na typ odpovídajícího parametru ( ). Potom eliminuje třetí přetížení, protože každý typ argumentu v druhém`Short` přetížení ( a `Single`)`Integer` `Single`rozšiřuje na odpovídající typ ve třetím přetížení ( a ). Druhé přetížení vyžaduje méně rozšíření, takže kompilátor používá pro volání.  
  
 V druhém volání kompilátor nelze vyloučit žádné přetížení na základě zúžení. Eliminuje třetí přetížení ze stejného důvodu jako v prvním volání, protože může volat druhé přetížení s menším rozšířením typů argumentů. Kompilátor však nelze vyřešit mezi první a druhé přetížení. Každý z nich má jeden definovaný typ parametru,`Byte` `Short`který `Single` se `Double`rozšiřuje na odpovídající typ v druhém ( do , ale na ). Kompilátor proto generuje chybu řešení přetížení.  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>Přetížené volitelné a paramarray argumenty  
 Pokud dvě přetížení procedury mají identické podpisy s tím rozdílem, že poslední parametr je deklarován [Volitelné](../../../../visual-basic/language-reference/modifiers/optional.md) v jednom a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) v druhé, kompilátor řeší volání tohoto postupu takto:  
  
|Pokud volání poskytne poslední argument jako|Kompilátor řeší volání přetížení deklarující poslední argument jako|  
|---|---|  
|Žádná hodnota (argument vynechán)|`Optional`|  
|Jedna hodnota|`Optional`|  
|Dvě nebo více hodnot v seznamu odděleném čárkami|`ParamArray`|  
|Pole libovolné délky (včetně prázdného pole)|`ParamArray`|  
  
## <a name="see-also"></a>Viz také

- [Volitelné parametry](./optional-parameters.md)
- [Pole parametrů](./parameter-arrays.md)
- [Přetížení procedury](./procedure-overloading.md)
- [Řešení potíží s procedurami](./troubleshooting-procedures.md)
- [Postupy: Definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Postupy: Volání přetížené procedury](./how-to-call-an-overloaded-procedure.md)
- [Postupy: Přetížení procedury, která přebírá nepovinné parametry](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů.](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Aspekty přetížení procedur](./considerations-in-overloading-procedures.md)
- [Přetížení](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Metody rozšíření](./extension-methods.md)
