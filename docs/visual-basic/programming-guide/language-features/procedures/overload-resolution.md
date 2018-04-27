---
title: Rozlišení přetěžování (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- overload resolution
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedure overloading [Visual Basic], overload resolution
- signatures [Visual Basic], procedure
- overloads [Visual Basic], resolution
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e62560d853c95bc4bba6ba829d8579ee4388858e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="overload-resolution-visual-basic"></a>Rozlišení přetěžování (Visual Basic)
Když Visual Basic – kompilátor dojde volání procedury, která je definována v několika verzích přetížené, kompilátor musíte rozhodnout, které přetížení volání. Dělá to pomocí následujících kroků:  
  
1.  **Přístupnost** Eliminuje žádné přetížení s úroveň přístupu, která brání jeho volání volající kód.  
  
2.  **Počet parametrů.** Eliminuje žádné přetížení, které definuje jiný počet parametrů, než se zadávají ve volání.  
  
3.  **Datové typy parametrů.** Kompilátor poskytuje instance metody předvoleb nad rozšiřující metody. Pokud se najde libovolné metody instance, který vyžaduje pouze rozšiřující převody tak, aby odpovídaly volání procedury, všechny rozšiřující metody jsou vyřazen a kompilátor pokračuje pouze kandidáty metoda instance. Pokud se žádná instance metoda nenajde, pokračuje v instanci a rozšiřující metody.  
  
     V tomto kroku eliminuje žádné přetížení, pro který datové typy argumentů volání nelze převést na typy parametrů, které jsou definované v přetížení.  
  
4.  **Zužující převody.** Eliminuje žádné přetížení, které vyžaduje zužující převod z volání typy argumentů pro typy definované parametrů. To platí určení, zda kontrola typu přepnout ([Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) je `On` nebo `Off`.  
  
5.  **Minimálně rozšíření.** Kompilátor zvažuje zbývající přetížení v párech. Pro každý pár porovná datové typy definovaných parametrů. Pokud typy v jednom z přetížení všechny rozšířit na odpovídající typy v dalších, kompilátor eliminuje ty druhé. To znamená zachová přetížení, která vyžaduje nejnižší možné rozšíření.  
  
6.  **Na jednom uchazeči.** Pokračuje considering přetížení v párech dokud jenom jeden přetížení zůstane a jeho přeloží volání této přetížení. Pokud kompilátor nelze zmenšit přetížení do jediného kandidáta, vygeneruje se chyba.  
  
 Následující obrázek znázorňuje proces, který určuje, které sady přetížené verze volat.  
  
 ![Vývojový diagram procesu rozlišení přetěžování](./media/overloadres.gif "OverloadRes")  
Řešení mezi přetížené verze  
  
 Následující příklad znázorňuje tento proces rozlišení přetížení.  
  
 [!code-vb[VbVbcnProcedures#62](./codesnippet/VisualBasic/overload-resolution_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#63](./codesnippet/VisualBasic/overload-resolution_2.vb)]  
  
 Při prvním volání do kompilátoru eliminuje první přetížení, protože typ prvního argumentu (`Short`) zmenší tak, aby typ odpovídající parametru (`Byte`). Protože každý argument typ v druhé přetížení pak eliminuje třetí přetížení (`Short` a `Single`) rozšiřuje odpovídající typ v třetí přetížení (`Integer` a `Single`). Druhý přetížení vyžaduje méně rozšíření, kompilátor použije pro volání.  
  
 V druhé volání do kompilátoru nelze eliminovat žádné přetížení na základě zužující. Eliminuje třetí přetížení ze stejného důvodu jako první volání, protože ji můžete volat druhý přetížení s menší rozšiřující s typy argumentů. Kompilátor však nelze vyřešit mezi prvním a druhém přetížení. Každá z nich má jeden typ definované parametru, která rozšiřuje odpovídající typ v dalších (`Byte` k `Short`, ale `Single` k `Double`). Kompilátor proto vygeneruje chybu rozlišení přetížení.  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>Přetížený volitelné a ParamArray – argumenty  
 Pokud dva přetížení procedury mít identické podpisy s tím rozdílem, že je deklarovaná poslední parametr [volitelné](../../../../visual-basic/language-reference/modifiers/optional.md) v jednom a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) do druhé kompilátor přeloží volání této procedury jako následovně:  
  
|Pokud poskytuje poslední argument jako volání|Kompilátor přeloží volání přetížení poslední argument jako deklarace|  
|---|---|  
|Žádná hodnota (argument vynechán)|`Optional`|  
|jednu hodnotu|`Optional`|  
|Dvě nebo více hodnot v seznamu odděleném čárkami|`ParamArray`|  
|Pole s žádné délkou (včetně prázdné pole)|`ParamArray`|  
  
## <a name="see-also"></a>Viz také  
 [Nepovinné parametry](./optional-parameters.md)  
 [Pole parametrů](./parameter-arrays.md)  
 [Přetížení procedury](./procedure-overloading.md)  
 [Řešení potíží s procedurami](./troubleshooting-procedures.md)  
 [Postupy: Definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Postupy: Volání přetížené procedury](./how-to-call-an-overloaded-procedure.md)  
 [Postupy: Přetížení procedury, která přebírá nepovinné parametry](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Aspekty přetížení procedur](./considerations-in-overloading-procedures.md)  
 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [Rozšiřující metody](./extension-methods.md)
