---
title: Set – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.Set
helpviewer_keywords:
- property procedures [Visual Basic], Set statements
- Set statement [Visual Basic]
- Set statement [Visual Basic], syntax
- write-only properties
- properties [Visual Basic], write-only
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
ms.openlocfilehash: 49d4c36805b64d7232a94e818256723a0437b6ef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404184"
---
# <a name="set-statement-visual-basic"></a>Set – příkaz (Visual Basic)
Deklaruje `Set` proceduru vlastnosti použitou k přiřazení hodnoty k vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a>Součásti  
 `attributelist`  
 Nepovinný parametr. Viz [seznam atributů](attribute-list.md).  
  
 `accessmodifier`  
 Volitelné na maximálně jeden z `Get` `Set` příkazů a v této vlastnosti. Může to být jedna z následujících:  
  
- [Proti](../modifiers/protected.md)  
  
- [Friend](../modifiers/friend.md)  
  
- [Hlášen](../modifiers/private.md)  
  
- `Protected Friend`  
  
 Podívejte [se na úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).  
  
 `value`  
 Povinná hodnota. Parametr, který obsahuje novou hodnotu pro vlastnost.  
  
 `datatype`  
 Požadováno v `Option Strict` případě `On` , že je. Datový typ `value` parametru Zadaný datový typ musí být stejný jako datový typ vlastnosti, kde `Set` je tento příkaz deklarován.  
  
 `statements`  
 Nepovinný parametr. Jeden nebo více příkazů, které se spouštějí při `Set` volání procedury vlastnosti.  
  
 `End Set`  
 Povinná hodnota. Ukončí definici `Set` procedury vlastnosti.  
  
## <a name="remarks"></a>Poznámky  
 Každá vlastnost musí mít `Set` proceduru vlastnosti, pokud není označena vlastnost `ReadOnly` . `Set`Procedura slouží k nastavení hodnoty vlastnosti.  
  
 Visual Basic automaticky volá `Set` proceduru vlastnosti, pokud příkaz přiřazení poskytuje hodnotu, která má být uložena ve vlastnosti.  
  
 Visual Basic předá `Set` proceduře během přiřazení vlastností parametr. Pokud nezadáte parametr pro `Set` , integrované vývojové prostředí (IDE) používá implicitní parametr s názvem `value` . Parametr obsahuje hodnotu, která má být přiřazena vlastnosti. Tuto hodnotu obvykle ukládáte do privátní místní proměnné a vrátíte ji pokaždé, když `Get` je procedura volána.  
  
 Tělo deklarace vlastnosti může obsahovat pouze vlastnosti `Get` a `Set` procedury mezi [příkazem Property](property-statement.md) a `End Property` příkazem. Nemůže uložit cokoli jiného než tyto postupy. Konkrétně nemůže uložit aktuální hodnotu vlastnosti. Tuto hodnotu je nutné uložit mimo vlastnost, protože pokud ji uložíte uvnitř některého z procedur vlastnosti, druhá procedura vlastnosti k ní nemá přístup. Obvyklým přístupem je uložení hodnoty do [soukromé](../modifiers/private.md) proměnné deklarované na stejné úrovni jako vlastnost. Musíte definovat `Set` proceduru uvnitř vlastnosti, na kterou se vztahuje.  
  
 `Set`Pokud použijete `accessmodifier` příkaz v příkazu, použije se výchozí hodnota úrovně přístupu jeho obsahující vlastnosti `Set` .  
  
## <a name="rules"></a>Pravidla  
  
- **Smíšené úrovně přístupu.** Pokud definujete vlastnost pro čtení i zápis, můžete volitelně zadat jinou úroveň přístupu pro `Get` `Set` proceduru nebo, ale ne obojí. Pokud to uděláte, musí být úroveň přístupu k této proceduře přísnější než úroveň přístupu vlastnosti. Například pokud je vlastnost deklarována `Friend` , můžete deklarovat `Set` proceduru `Private` , ale ne `Public` .  
  
     Pokud definujete `WriteOnly` vlastnost, `Set` procedura představuje celou vlastnost. Nemůžete deklarovat jinou úroveň přístupu pro `Set` , protože by se pro vlastnost nastavily dvě úrovně přístupu.  
  
## <a name="behavior"></a>Chování  
  
- **Návrat z procedury vlastnosti.** Když se `Set` procedura vrátí na volající kód, provádění pokračuje po příkazu, který poskytl hodnotu, která má být uložena.  
  
     `Set`procedury vlastnosti mohou vracet buď pomocí [příkazu return](return-statement.md) , nebo [příkazu exit](exit-statement.md).  
  
     `Exit Property`Příkazy a `Return` způsobují bezprostřední ukončení procedury vlastnosti. Libovolný počet `Exit Property` příkazů a `Return` se může objevit kdekoli v proceduře a můžete kombinovat `Exit Property` a `Return` příkazy.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Set` příkaz k nastavení hodnoty vlastnosti.  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>Viz také

- [Get – příkaz](get-statement.md)
- [Property – příkaz](property-statement.md)
- [Sub – příkaz](sub-statement.md)
- [Procedury vlastnosti](../../programming-guide/language-features/procedures/property-procedures.md)
