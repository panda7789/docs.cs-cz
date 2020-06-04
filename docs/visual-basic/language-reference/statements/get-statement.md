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
ms.openlocfilehash: 31936fb2c8f658203a43702a2b5fa4ee2481beb5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404599"
---
# <a name="get-statement"></a>Get – příkaz
Deklaruje `Get` proceduru vlastnosti použitou k načtení hodnoty vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a>Součásti  
  
|Pojem|Definice|  
|---|---|  
|`attributelist`|Nepovinný parametr. Viz [seznam atributů](attribute-list.md).|  
|`accessmodifier`|Volitelné na maximálně jeden z `Get` `Set` příkazů a v této vlastnosti. Může to být jedna z následujících:<br /><br /> -   [Proti](../modifiers/protected.md)<br />-   [Friend](../modifiers/friend.md)<br />-   [Hlášen](../modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Podívejte [se na úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).|  
|`statements`|Nepovinný parametr. Jeden nebo více příkazů, které se spouštějí při `Get` volání procedury vlastnosti.|  
|`End Get`|Povinná hodnota. Ukončí definici `Get` procedury vlastnosti.|  
  
## <a name="remarks"></a>Poznámky  
 Každá vlastnost musí mít `Get` proceduru vlastnosti, pokud není označena vlastnost `WriteOnly` . `Get`Procedura slouží k vrácení aktuální hodnoty vlastnosti.  
  
 Visual Basic automaticky volá `Get` proceduru vlastnosti, když výraz vyžádá hodnotu vlastnosti.  
  
 Tělo deklarace vlastnosti může obsahovat pouze vlastnosti `Get` a `Set` procedury mezi [příkazem Property](property-statement.md) a `End Property` příkazem. Nemůže uložit cokoli jiného než tyto postupy. Konkrétně nemůže uložit aktuální hodnotu vlastnosti. Tuto hodnotu je nutné uložit mimo vlastnost, protože pokud ji uložíte uvnitř některého z procedur vlastnosti, druhá procedura vlastnosti k ní nemá přístup. Obvyklým přístupem je uložení hodnoty do [soukromé](../modifiers/private.md) proměnné deklarované na stejné úrovni jako vlastnost. Musíte definovat `Get` proceduru uvnitř vlastnosti, na kterou se vztahuje.  
  
 `Get`Pokud použijete `accessmodifier` příkaz v příkazu, použije se výchozí hodnota úrovně přístupu jeho obsahující vlastnosti `Get` .  
  
## <a name="rules"></a>Pravidla  
  
- **Smíšené úrovně přístupu.** Pokud definujete vlastnost pro čtení i zápis, můžete volitelně zadat jinou úroveň přístupu pro `Get` `Set` proceduru nebo, ale ne obojí. Pokud to uděláte, musí být úroveň přístupu k této proceduře přísnější než úroveň přístupu vlastnosti. Například pokud je vlastnost deklarována `Friend` , můžete deklarovat `Get` proceduru `Private` , ale ne `Public` .  
  
     Pokud definujete `ReadOnly` vlastnost, `Get` procedura představuje celou vlastnost. Nemůžete deklarovat jinou úroveň přístupu pro `Get` , protože by se pro vlastnost nastavily dvě úrovně přístupu.  
  
- **Návratový typ** [Příkaz Property](property-statement.md) může deklarovat datový typ hodnoty, kterou vrátí. `Get`Procedura automaticky vrátí tento datový typ. Můžete zadat libovolný datový typ nebo název výčtu, struktury, třídy nebo rozhraní.  
  
     Pokud `Property` příkaz neurčí `returntype` , procedura vrátí `Object` .  
  
## <a name="behavior"></a>Chování  
  
- **Návrat z procedury.** Když se `Get` procedura vrátí na volající kód, provádění pokračuje v rámci příkazu, který požadoval hodnotu vlastnosti.  
  
     `Get`procedury vlastnosti mohou vracet hodnotu buď pomocí [příkazu return](return-statement.md) , nebo přiřazením návratové hodnoty názvu vlastnosti. Další informace naleznete v tématu "návratová hodnota" v [příkazu Function](function-statement.md).  
  
     `Exit Property`Příkazy a `Return` způsobují bezprostřední ukončení procedury vlastnosti. Libovolný počet `Exit Property` příkazů a `Return` se může objevit kdekoli v proceduře a můžete kombinovat `Exit Property` a `Return` příkazy.  
  
- **Návratová hodnota** Chcete-li vrátit hodnotu z `Get` procedury, můžete buď přiřadit hodnotu k názvu vlastnosti nebo ji zahrnout do [příkazu return](return-statement.md). `Return`Příkaz současně přiřadí `Get` návratovou hodnotu procedury a ukončí proceduru.  
  
     Pokud použijete `Exit Property` bez přiřazení hodnoty k názvu vlastnosti, `Get` procedura vrátí výchozí hodnotu pro datový typ vlastnosti. Další informace naleznete v tématu "návratová hodnota" v [příkazu Function](function-statement.md).  
  
     Následující příklad ukazuje dva způsoby, jak vlastnost jen pro čtení `quoteForTheDay` může vracet hodnotu drženou v soukromé proměnné `quoteValue` .  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Get` příkaz k vrácení hodnoty vlastnosti.  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>Viz také

- [Set – příkaz](set-statement.md)
- [Property – příkaz](property-statement.md)
- [Exit – příkaz](exit-statement.md)
- [Objekty a třídy](../../programming-guide/language-features/objects-and-classes/index.md)
- [Návod: Definování tříd](../../programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
