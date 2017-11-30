---
title: "With...End With – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.With
helpviewer_keywords:
- With keyword [Visual Basic]
- loop structures [Visual Basic], and With...End With statements
- execution [Visual Basic], on object
- instructions, repeating
- With...End With statements [Visual Basic]
- With statement [Visual Basic]
- With statement [Visual Basic], nesting
- objects [Visual Basic], accessing
- With block
- End keyword [Visual Basic], With...End With statements
ms.assetid: 340d5fbb-4f43-48ec-a024-80843c137817
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aa1f416e1bfdf6cdb51b098c0e2bd5e9912cb309
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="withend-with-statement-visual-basic"></a>With...End With – příkaz (Visual Basic)
Vykoná řadu příkazů, které opakovaně odkazují na jeden objekt nebo strukturu, takže příkazy mohou při přístupu k členům tohoto objektu nebo struktury použít zjednodušenou syntaxi.  Při použití strukturou, můžou jenom číst hodnoty členů, nebo volat metody a dojde k chybě, pokud se pokusíte přiřadit hodnoty členů struktury používán `With...End With` příkaz.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
With objectExpression  
    [ statements ]  
End With  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`objectExpression`|Požadováno. Výraz, který se vyhodnotí na objekt. Výraz může být libovolně složitý a vyhodnotí se pouze jednou. Výraz lze vyhodnotit na libovolný datový typ včetně základních typů.|  
|`statements`|Volitelné. Jeden nebo více příkazů mezi `With` a `End With` , mohou odkazovat na objekt, který je produkovaný vyhodnocení členů `objectExpression`.|  
|`End With`|Požadováno. Ukončí definice `With` bloku.|  
  
## <a name="remarks"></a>Poznámky  
 Pomocí `With...End With`, můžete provádět řadu příkazů na zadaný objekt bez určení názvu objektu vícekrát. V rámci `With` příkaz blok, můžete zadat členem objektu spouštění s dobou, jako kdyby `With` příkaz objekt před jeho.  
  
 Například pokud chcete změnit víc vlastností na jeden objekt, umístěte příkazy přiřazení vlastnosti uvnitř `With...End With` bloku, odkaz na objekt pouze jednou místo jednou pro každou vlastnost přiřazení.  
  
 Pokud váš kód odkazuje na stejný objekt ve více příkazů, získáte následující výhody pomocí `With` příkaz:  
  
-   Nemusíte vyhodnocovat složitý výraz vícekrát ani přiřazovat výsledek k dočasné proměnné, chcete-li na jeho členy odkazovat vícekrát.  
  
-   Odstraněním opakovaných kvalifikačních výrazů zlepšíte přehlednost kódu.  
  
 Datový typ `objectExpression` může být jakákoli třída nebo struktura typ nebo i základní typ jazyka Visual Basic, jako `Integer`.  Pokud `objectExpression` výsledky v jakoukoli jinou hodnotu než objekt, můžete pouze číst hodnoty svých členů nebo volat metody a dojde k chybě, pokud se pokusíte přiřadit hodnoty členů struktury používá v `With...End With` příkaz.  Toto je ke stejné chybě, které byste získali, pokud je vyvolána metoda, která vrátí strukturu a okamžitě získat přístup a přiřazenou hodnotu na člena, výsledku funkce, jako například `GetAPoint().x = 1`.  Problémem je v obou případech to, že tato struktura existuje pouze v zásobníku volání a neexistuje žádný způsob, jak člena změněné struktury v těchto situacích zapsat někam tak, aby jakýkoli jiný kód v programu tuto změnu zpozoroval.  
  
 `objectExpression` Jednou, vyhodnotí při vstupu do bloku. Nelze přiřadit `objectExpression` uvnitř `With` bloku.  
  
 V rámci `With` bloku, dostanete metod a vlastností zadaného objektu bez kvalifikace je. Můžete použít metody a vlastnosti jiného objektu, musíte je ale kvalifikovat pomocí názvů jejich objektů.  
  
 Můžete umístit jeden `With...End With` příkaz v rámci jiného. Vnořené `With...End With` příkazy může být matoucí, pokud nejsou objekty, které jsou právě uvedených vymazat z kontextu. Je nutné zadat plně kvalifikovaný odkaz na objekt, který je v vnější `With` blokovat, pokud objekt se odkazuje z v rámci vnitřní `With` bloku.  
  
 Můžete nemůže provést větvení do `With` blok příkazu z mimo blok.  
  
 Pokud blok neobsahuje cyklus, spustí se příkazy pouze jednou. Je možné vnořovat různé druhy řídicích struktur. Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
>  Můžete použít `With` – klíčové slovo v objektu inicializátory také. Další informace a příklady naleznete v tématu [inicializátory objektů: pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) a [anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
>   
>  Pokud používáte `With` blok jenom k inicializaci vlastnosti nebo pole objektu, který jste právě instanci, zvažte namísto toho použití inicializátoru objektu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu každý `With` bloku provede řadu příkazů na jednoho objektu.  
  
 [!code-vb[VbVbalrWithStatement#2](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/with-end-with-statement_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad vnoří `With…End With` příkazy. V rámci vnořeného `With` příkaz, syntaxe odkazuje na vnitřní objekt.  
  
 [!code-vb[VbVbalrWithStatement#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/with-end-with-statement_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Generic.List%601>  
 [Vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Inicializátory objektů: Pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
