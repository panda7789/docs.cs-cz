---
title: Rozlišení přetěžování (Visual Basic)
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
ms.openlocfilehash: 4f81c7377423899c142c4270f325bbd7ed20b877
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59312238"
---
# <a name="overload-resolution-visual-basic"></a>Rozlišení přetěžování (Visual Basic)
Když kompilátor jazyka Visual Basic dojde během volání procedury, která je definována v několika přetížené verze, kompilátor musí rozhodnout, které přetížení volání. Dělá to pomocí následujících kroků:  
  
1. **Přístupnost** Eliminuje žádného přetížení s úrovní přístupu, který brání volání volající kód.  
  
2. **Počet parametrů.** Eliminuje žádného přetížení, která definuje různý počet parametrů než je zadaný ve volání.  
  
3. **Datové typy parametrů.** Kompilátor dává přednost metody instance prostřednictvím metody rozšíření. Pokud se najde libovolnou metodu instance, který se vyžaduje jenom na rozšiřující převody tak, aby odpovídaly volání procedury, se zahodí všechny metody rozšíření a kompilátor pokračuje pouze kandidáty metodu instance. Pokud se nenajde žádný takový metodu instance, bude pokračovat s instancí a metody rozšíření.  
  
     V tomto kroku eliminuje žádného přetížení, pro které datové typy argumentů volání nelze převést na parametr typy definované v přetížení.  
  
4. **Zužující převody.** Eliminuje žádného přetížení, která vyžaduje zúžení převodu z: volání typy argumentů pro typy definované parametrů. Je hodnota true Určuje, zda přepnout kontrola typu ([Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) je `On` nebo `Off`.  
  
5. **Rozšiřující nejnižší.** Kompilátor považuje za zbývající přetížení v párech. Pro každý pár porovná datové typy definované parametry. Pokud se typy v jednom ze všech přetížení rozšířit na odpovídající typy v jiném, kompilátor eliminuje ten. To znamená zachová přetížení, která vyžaduje nejnižší možné rozšíření.  
  
6. **Jeden Release Candidate.** Pokračuje v considering přetížení v párech až do pouze jedno přetížení zůstane a přeloží volání tohoto přetížení. Pokud kompilátor nemůže snížit přetížení k jedné Release candidate, dojde k chybě.  
  
 Následující obrázek znázorňuje proces, který určuje, které sada přetížené verze volání.  
  
 ![Vývojový diagram procesu rozlišení přetížení](./media/overload-resolution/determine-overloaded-version.gif "řešení mezi přetížené verze")    
  
 Následující příklad ukazuje tento proces řešení přetížení.  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 Při prvním volání, kompilátor eliminuje první přetížení, protože typ prvního argumentu (`Short`) zužuje na typ odpovídající parametru (`Byte`). Eliminuje pak třetí přetížení, protože typ každého argumentu ve druhé přetížení (`Short` a `Single`) rozšiřuje na odpovídající typ v třetí přetížení (`Integer` a `Single`). Druhé přetížení vyžaduje méně rozšíření, takže kompilátor používá volání.  
  
 V druhém volání nelze odstranit kompilátor některý z přetížení na základě zužující. Eliminuje třetí přetížení ze stejného důvodu jako první volání, vzhledem k tomu, že může volat druhé přetížení s méně rozšiřující typy argumentů. Kompilátor však nelze rozlišit mezi první a druhé přetížení. Každá má jeden typ definovaný parametr, který rozšiřuje na odpovídající typ v jiném (`Byte` k `Short`, ale `Single` k `Double`). Kompilátor tedy dojde k chybě rozlišení přetížení.  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>Přetížené volitelné a ParamArray – argumenty  
 Pokud dvě přetížení procedury, mají stejné podpisy, s tím rozdílem, že je deklarován poslední parametr [volitelné](../../../../visual-basic/language-reference/modifiers/optional.md) v jednom a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) , ve druhém přeloží kompilátor volání této procedury jako následující:  
  
|Pokud volání je zadán jako poslední argument|Kompilátor překládá volání přetížení deklarace posledním argumentem jako|  
|---|---|  
|Žádná hodnota (argument vynechán)|`Optional`|  
|Jedinou hodnotu|`Optional`|  
|Dvě nebo více hodnot v seznamu odděleném čárkami|`ParamArray`|  
|Pole z jakékoli délky (včetně prázdné pole)|`ParamArray`|  
  
## <a name="see-also"></a>Viz také:

- [Nepovinné parametry](./optional-parameters.md)
- [Pole parametrů](./parameter-arrays.md)
- [Přetížení procedury](./procedure-overloading.md)
- [Řešení potíží s procedurami](./troubleshooting-procedures.md)
- [Postupy: Definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Postupy: Volání přetížené procedury](./how-to-call-an-overloaded-procedure.md)
- [Postupy: Přetížení procedury, která přebírá volitelné parametry](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Aspekty přetížení procedur](./considerations-in-overloading-procedures.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Rozšiřující metody](./extension-methods.md)
