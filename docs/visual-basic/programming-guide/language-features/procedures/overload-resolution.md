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
ms.openlocfilehash: bcb99ef3845c1ce3998dc9dc8d9f1d335515c0a9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364367"
---
# <a name="overload-resolution-visual-basic"></a>Rozlišení přetěžování (Visual Basic)
Když kompilátor Visual Basic narazí na volání procedury, která je definována v několika přetížených verzích, kompilátor musí rozhodnout, který z přetížení má zavolat. Provede to provedením následujících kroků:  
  
1. **Přístup.** Eliminuje jakékoli přetížení s úrovní přístupu, která brání volajícímu kódu v jeho volání.  
  
2. **Počet parametrů** Eliminuje jakékoli přetížení, které definuje jiný počet parametrů, než je zadáno ve volání.  
  
3. **Datové typy parametrů.** Kompilátor poskytuje přednost metodám instance před rozšiřujícími metodami. Pokud je nalezena kterákoli metoda instance, která vyžaduje pouze rozšiřující převody, aby odpovídaly volání procedury, všechny metody rozšíření jsou vynechány a kompilátor pokračuje pouze kandidáty metody instance. Pokud není nalezena žádná taková metoda instance, bude pokračovat s instancí i metodami rozšíření.  
  
     V tomto kroku eliminuje jakékoli přetížení, pro které nelze převést datové typy argumentů volání na typy parametrů definované v přetížení.  
  
4. **Zužující převody.** Eliminuje jakékoli přetížení, které vyžaduje zúžení převodu typů argumentů volání na definované typy parametrů. To platí bez ohledu na to, zda je přepínač pro kontrolu typu ([příkaz Option Strict](../../../language-reference/statements/option-strict-statement.md)) `On` nebo `Off` .  
  
5. **Nejméně rozšiřování.** Kompilátor považuje zbývající přetížení ve dvojicích. Pro každou dvojici porovnává datové typy definovaných parametrů. Pokud jsou typy v jednom z přetížení všechny rozšířeny na odpovídající typy v druhé, kompilátor eliminuje druhé. To znamená, že zachovává přetížení, které vyžaduje nejmenší množství rozšiřování.  
  
6. **Jeden kandidát.** Pokračuje v zvažování přetížení ve dvojicích, dokud nezůstane pouze jedno přetížení a překládá volání tohoto přetížení. Pokud kompilátor nemůže snížit přetížení na jednoho kandidáta, vygeneruje chybu.  
  
 Následující obrázek znázorňuje proces, který určuje, který ze sady přetížených verzí je volána.  
  
 ![Diagram toku procesu rozlišení přetížení](./media/overload-resolution/determine-overloaded-version.gif "Řešení mezi přetíženými verzemi")
  
 Následující příklad znázorňuje tento proces řešení přetížení.  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 Při prvním volání kompilátor eliminuje první přetížení, protože typ prvního argumentu ( `Short` ) je zúžen na typ odpovídajícího parametru ( `Byte` ). Pak eliminuje třetí přetížení, protože každý argument typu v druhém přetížení ( `Short` a `Single` ) se rozšíří na odpovídající typ třetí přetížení ( `Integer` a `Single` ). Druhé přetížení vyžaduje méně rozšiřování, takže ho kompilátor použije pro volání.  
  
 Ve druhém volání kompilátor nemůže eliminovat žádné přetížení na základě zúžení. Vylučuje třetí přetížení pro stejný důvod jako v prvním volání, protože může zavolat druhé přetížení s menším rozšiřováním typů argumentů. Kompilátor však nemůže vyřešit mezi prvním a druhým přetížením. Každý má jeden definovaný typ parametru, který rozšiřuje na odpovídající typ v druhé ( `Byte` na `Short` , ale `Single` do `Double` ). Kompilátor proto vygeneruje chybu rozlišení přetížení.  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>Přetížené argumenty Optional a ParamArray  
 Pokud dvě přetížení procedury mají stejné signatury s tím rozdílem, že poslední parametr je deklarován jako [volitelné](../../../language-reference/modifiers/optional.md) v jednom a [ParamArray](../../../language-reference/modifiers/paramarray.md) v druhé, kompilátor vyřeší volání této procedury následujícím způsobem:  
  
|Pokud volání dodá poslední argument jako|Kompilátor vyřeší volání přetížení, které deklaruje poslední argument jako|  
|---|---|  
|Žádná hodnota (argument byl vynechán)|`Optional`|  
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
- [Přetížení](../../../language-reference/modifiers/overloads.md)
- [Metody rozšíření](./extension-methods.md)
