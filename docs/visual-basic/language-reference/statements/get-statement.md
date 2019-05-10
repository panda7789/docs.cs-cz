---
title: Get – příkaz (Visual Basic)
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
ms.openlocfilehash: 33fa6811f952d240fb86bbdf59ca83df0afc03ad
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625520"
---
# <a name="get-statement"></a>Get – příkaz
Deklaruje `Get` vlastnost postup použitý k načtení hodnoty vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`attributelist`|Volitelné. Zobrazit [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Volitelné na nanejvýš jeden z `Get` a `Set` příkazy v této vlastnosti. Může být jedna z následujících akcí:<br /><br /> -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend –](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privátní](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Zobrazit [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`statements`|Volitelné. Jeden nebo více příkazů, které při spuštění `Get` volání procedury vlastnosti.|  
|`End Get`|Povinný parametr. Ukončí definici `Get` procedura property.|  
  
## <a name="remarks"></a>Poznámky  
 Každou vlastnost musí mít `Get` procedura property Pokud je vlastnost označena `WriteOnly`. `Get` Postup se používá k vrácení aktuální hodnoty vlastnosti.  
  
 Visual Basic automaticky volá vlastnosti `Get` postup, pokud výraz vyžaduje hodnotu vlastnosti.  
  
 Text deklarace vlastnosti může obsahovat pouze vlastnosti `Get` a `Set` postupy mezi [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md) a `End Property` příkazu. Nejde uložit nic jiného než tyto postupy. Konkrétně to nejde uložit aktuální hodnota vlastnosti. Tato hodnota mimo vlastnost, musí uložit, protože pokud ukládat v některé z vlastností, jiné procedury vlastnosti nejde získat přístup. Obvyklým přístupem je uložení hodnoty [privátní](../../../visual-basic/language-reference/modifiers/private.md) proměnná deklarovaná na stejné úrovni jako vlastnost. Je nutné definovat `Get` postupu uvnitř vlastnosti, ke kterému se vztahuje.  
  
 `Get` Postup výchozí úroveň přístupu její nadřazenou vlastnost, pokud nechcete použít `accessmodifier` v `Get` příkazu.  
  
## <a name="rules"></a>pravidla  
  
- **Smíšenými úrovněmi přístupu.** Pokud definujete vlastnosti pro čtení i zápis, Volitelně můžete zadat úroveň různý přístup pro buď `Get` nebo `Set` postup, ale ne obojí. Pokud to uděláte, musí být více omezující než úroveň přístupu vlastnosti úroveň řízení přístupu. Například, pokud je deklarována vlastnost `Friend`, lze deklarovat `Get` postup `Private`, ale ne `Public`.  
  
     Pokud definujete `ReadOnly` vlastnost, `Get` postup představuje celou vlastnost. Nelze deklarovat různý přístup úroveň `Get`, protože dvě úrovně přístupu pro vlastnost, která byste nastavili.  
  
- **Návratový typ.** [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md) můžete deklarovat datový typ hodnoty vrácením. `Get` Procedura automaticky vrací, datového typu. Můžete zadat libovolný datový typ nebo název výčtu, strukturu, třídu nebo rozhraní.  
  
     Pokud `Property` příkaz neurčuje `returntype`, vrátí postup `Object`.  
  
## <a name="behavior"></a>Chování  
  
- **Vrácení z procedury.** Když `Get` postup vrátí volajícímu kódu, provádění pokračuje v rámci příkazu, který požadovaná hodnota vlastnosti.  
  
     `Get` procedury vlastnosti může vrátit hodnotu pomocí buď [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md) nebo přiřazením návratovou hodnotu pro název vlastnosti. Další informace najdete v tématu "Vrátit hodnotu" v [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     `Exit Property` a `Return` příkazy způsobit okamžité ukončení z procedury vlastnosti. Libovolný počet `Exit Property` a `Return` příkazů může vyskytovat kdekoli v postupu, a je možné kombinovat `Exit Property` a `Return` příkazy.  
  
- **Vrátí hodnotu.** Pro navrácení hodnoty z `Get` postup, můžete přiřadit hodnoty pro název vlastnosti, nebo ho v [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md). `Return` Příkaz současně přiřadí `Get` procedura vracet hodnotu a ukončí proceduru.  
  
     Pokud používáte `Exit Property` bez přiřazení hodnoty pro název vlastnosti `Get` procedura vrací výchozí hodnota pro typ dat vlastnosti. Další informace najdete v tématu "Vrátit hodnotu" v [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     Následující příklad ukazuje dva způsoby, jak vlastnost jen pro čtení `quoteForTheDay` může vrátit hodnotu obsaženou referenčním v soukromé proměnné `quoteValue`.  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Get` příkazu vrátí hodnotu vlastnosti.  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Set](../../../visual-basic/language-reference/statements/set-statement.md)
- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Příkaz Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Návod: Definování tříd](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
