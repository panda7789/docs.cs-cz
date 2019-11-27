---
title: Get – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.Get
helpviewer_keywords:
- Get statement [Visual Basic], syntax
- Get statement [Visual Basic]
- properties [Visual Basic], read-only
- read-only properties
- Get keyword [Visual Basic]
- property procedures [Visual Basic], Get statements
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
ms.openlocfilehash: 9560faf90d531c32f104dbd053a7c1f5584cfb1b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351176"
---
# <a name="get-statement"></a>Get – příkaz
Deklaruje proceduru vlastnosti `Get`, která slouží k načtení hodnoty vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`attributelist`|Volitelná. Viz [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Volitelné na maximálně jeden z příkazů `Get` a `Set` v této vlastnosti. Může být jedna z následujících akcí:<br /><br /> -   [chráněno](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [přítel](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [privátní](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Podívejte [se na úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`statements`|Volitelná. Jeden nebo více příkazů, které se spouštějí při volání procedury vlastnosti `Get`.|  
|`End Get`|Požadováno. Ukončí definici procedury vlastnosti `Get`.|  
  
## <a name="remarks"></a>Poznámky  
 Každá vlastnost musí mít proceduru `Get` vlastnost, pokud vlastnost není označena `WriteOnly`. Procedura `Get` slouží k vrácení aktuální hodnoty vlastnosti.  
  
 Visual Basic automaticky volá `Get` proceduru vlastnosti, když výraz požaduje hodnotu vlastnosti.  
  
 Tělo deklarace vlastnosti může obsahovat pouze `Get` vlastnosti a procedury `Set` mezi [příkazem Property](../../../visual-basic/language-reference/statements/property-statement.md) a příkazem `End Property`. Nemůže uložit cokoli jiného než tyto postupy. Konkrétně nemůže uložit aktuální hodnotu vlastnosti. Tuto hodnotu je nutné uložit mimo vlastnost, protože pokud ji uložíte uvnitř některého z procedur vlastnosti, druhá procedura vlastnosti k ní nemá přístup. Obvyklým přístupem je uložení hodnoty do [soukromé](../../../visual-basic/language-reference/modifiers/private.md) proměnné deklarované na stejné úrovni jako vlastnost. Musíte definovat `Get` proceduru uvnitř vlastnosti, na kterou se vztahuje.  
  
 Pokud nepoužijete `accessmodifier` v příkazu `Get`, bude výchozí hodnota `Get` nastavena na úroveň přístupu jeho obsahující vlastnosti.  
  
## <a name="rules"></a>Pravidla  
  
- **Smíšené úrovně přístupu.** Pokud definujete vlastnost pro čtení i zápis, můžete volitelně zadat jinou úroveň přístupu pro `Get` nebo `Set` postup, ale ne obojí. Pokud to uděláte, musí být úroveň přístupu k této proceduře přísnější než úroveň přístupu vlastnosti. Například pokud je vlastnost deklarována `Friend`, můžete deklarovat `Get` proceduru `Private`, ale ne `Public`.  
  
     Pokud definujete vlastnost `ReadOnly`, bude procedura `Get` představovat celou vlastnost. Pro `Get`nemůžete deklarovat jinou úroveň přístupu, protože by se pro vlastnost nastavily dvě úrovně přístupu.  
  
- **Návratový typ** [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md) může deklarovat datový typ hodnoty, kterou vrátí. `Get` procedura tento datový typ automaticky vrátí. Můžete zadat libovolný datový typ nebo název výčtu, struktury, třídy nebo rozhraní.  
  
     Pokud příkaz `Property` neurčí `returntype`, procedura vrátí `Object`.  
  
## <a name="behavior"></a>Chování  
  
- **Návrat z procedury.** Když se `Get` procedura vrátí k volajícímu kódu, provádění pokračuje v rámci příkazu, který požadoval hodnotu vlastnosti.  
  
     procedury vlastnosti `Get` mohou vracet hodnotu buď pomocí [příkazu return](../../../visual-basic/language-reference/statements/return-statement.md) , nebo přiřazením návratové hodnoty názvu vlastnosti. Další informace naleznete v tématu "návratová hodnota" v [příkazu Function](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     Příkazy `Exit Property` a `Return` způsobují bezprostřední ukončení procedury vlastnosti. Libovolný počet `Exit Property` a `Return` příkazů se může objevit kdekoli v proceduře a můžete kombinovat `Exit Property` a `Return` příkazy.  
  
- **Návratová hodnota** Chcete-li vrátit hodnotu z `Get` postup, můžete buď přiřadit hodnotu k názvu vlastnosti nebo ji zahrnout do [příkazu return](../../../visual-basic/language-reference/statements/return-statement.md). Příkaz `Return` současně přiřadí návratovou hodnotu procedury `Get` a ukončí proceduru.  
  
     Použijete-li `Exit Property` bez přiřazení hodnoty k názvu vlastnosti, procedura `Get` vrátí výchozí hodnotu pro datový typ vlastnosti. Další informace naleznete v tématu "návratová hodnota" v [příkazu Function](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     Následující příklad ukazuje dva způsoby, jak vlastnost jen pro čtení `quoteForTheDay` může vracet hodnotu uloženou v soukromé proměnné `quoteValue`.  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá příkaz `Get` pro návrat hodnoty vlastnosti.  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Set](../../../visual-basic/language-reference/statements/set-statement.md)
- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Příkaz Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Návod: Definování tříd](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
