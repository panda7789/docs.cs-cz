---
title: Property – příkaz (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.PropertySet
- vb.Property
- vb.PropertyGet
helpviewer_keywords:
- Property statement [Visual Basic]
- default modifier
- property procedures [Visual Basic], Property statements
- Property keyword [Visual Basic]
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
ms.openlocfilehash: 21ca15d6a6939d884c7e6abedc1f7919be079edd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43420378"
---
# <a name="property-statement"></a>Property – příkaz
Deklaruje název vlastnosti a procedury vlastnosti používané k ukládání a načítání hodnoty vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
[ <attributelist> ] [ Default ] [ accessmodifier ]   
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ] [ Iterator ]  
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]  
    [ <attributelist> ] [ accessmodifier ] Get  
        [ statements ]  
    End Get  
    [ <attributelist> ] [ accessmodifier ] Set ( ByVal value As returntype [, parameterlist ] )  
        [ statements ]  
    End Set  
End Property  
- or -  
[ <attributelist> ] [ Default ] [ accessmodifier ]   
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ]   
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]  
```  
  
## <a name="parts"></a>Součásti  
  
-   `attributelist`  
  
     Volitelné. Seznam atributů, které se vztahují k této vlastnosti nebo `Get` nebo `Set` postup. Zobrazit [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
-   `Default`  
  
     Volitelné. Určuje, že tato vlastnost je výchozí vlastnost pro třídu nebo strukturu, na kterém je definována. Výchozí vlastnosti musí přijímat parametry a může být nastavit a načíst bez určení názvu vlastnosti. Je-li deklarována vlastnost jako `Default`, nemůžete použít `Private` na vlastnost nebo některý z jeho procedury vlastností.  
  
-   `accessmodifier`  
  
     Volitelné na `Property` příkazu a jenom jedna z `Get` a `Set` příkazy. Může být jedna z následujících akcí:  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [Chráněné typu Friend](../../language-reference/modifiers/protected-friend.md) 

    - [Privátní, chráněné](../../language-reference/modifiers/private-protected.md)
  
     Zobrazit [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
-   `propertymodifiers`  
  
     Volitelné. Může být jedna z následujících akcí:  
  
    -   [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     Volitelné. Zobrazit [sdílené](../../../visual-basic/language-reference/modifiers/shared.md).  
  
-   `Shadows`  
  
     Volitelné. Zobrazit [stíny](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
-   `ReadOnly`  
  
     Volitelné. Zobrazit [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
-   `WriteOnly`  
  
     Volitelné. Zobrazit [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).  
  
-   `Iterator`  
  
     Volitelné. Zobrazit [iterátoru](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
-   `name`  
  
     Požadováno. Název vlastnosti Zobrazit [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   `parameterlist`  
  
     Volitelné. Seznam představující parametry této vlastnosti a je to možné další parametry místní názvy proměnných `Set` postup. Zobrazit [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md).  
  
-   `returntype`  
  
     Požadováno pokud `Option Strict` je `On`. Datový typ hodnoty vrácené touto vlastností.  
  
-   `Implements`  
  
     Volitelné. Označuje, že tato vlastnost implementuje jednu nebo více vlastností, každý z nich definované v rozhraní implementované obsahující třídu nebo strukturu tuto vlastnost. Zobrazit [implementuje příkaz](../../../visual-basic/language-reference/statements/implements-statement.md).  
  
-   `implementslist`  
  
     Požadováno pokud `Implements` pochází. Seznam vlastností se implementuje.  
  
     `implementedproperty [ , implementedproperty ... ]`  
  
     Každý `implementedproperty` má následující syntaxi a části:  
  
     `interface.definedname`  
  
    |Část|Popis|  
    |---|---|  
    |`interface`|Požadováno. Název rozhraní implementovaná touto vlastností obsahující třídy nebo struktury.|  
    |`definedname`|Požadováno. Název, podle kterého je vlastnost definována v `interface`.|  
  
-   `Get`  
  
     Volitelné. Povinné, pokud je vlastnost označena `WriteOnly`. Spustí `Get` procedura property, který se používá k vrácení hodnoty vlastnosti.  
  
-   `statements`  
  
     Volitelné. Blok příkazů ke spuštění v rámci `Get` nebo `Set` postup.  
  
-   `End Get`  
  
     Ukončuje `Get` procedura property.  
  
-   `Set`  
  
     Volitelné. Povinné, pokud je vlastnost označena `ReadOnly`. Spustí `Set` procedura property, který se používá k uložení hodnoty vlastnosti.  
  
-   `End Set`  
  
     Ukončuje `Set` procedura property.  
  
-   `End Property`  
  
     Ukončí definici této vlastnosti.  
  
## <a name="remarks"></a>Poznámky  
 `Property` Příkaz zavádí deklaraci vlastnosti. Vlastnost může mít `Get` procedury (jen pro čtení), `Set` postupu (pouze pro zápis) nebo obě (čtení a zápis). Můžete vynechat `Get` a `Set` procedury při použití automaticky implementované vlastnosti. Další informace najdete v tématu [implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).  
  
 Můžete použít `Property` pouze na úrovni třídy. To znamená, že *kontext deklarace* pro vlastnost musí být třída, struktura, modul nebo rozhraní a nemůže být zdrojový soubor, obor názvů, procedura nebo blok. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Ve výchozím nastavení použijte vlastnosti veřejný přístup. Úroveň přístupu k vlastnosti s modifikátor přístupu můžete upravit na `Property` příkaz kde můžete volitelně nastavit jeden z jeho vlastnost postupy do více omezující úrovně přístupu.  
  
 Visual Basic předá parametr `Set` postupu během přiřazení vlastnosti. Pokud nezadáte parametr `Set`, integrované vývojové prostředí (IDE) používá implicitní parametr s názvem `value`. Tento parametr obsahuje hodnotu pro přiřazení k vlastnosti. Obvykle tuto hodnotu v privátní místní proměnné a vrácení pokaždé, když `Get` volání procedury.  
  
## <a name="rules"></a>pravidla  
  
-   **Smíšenými úrovněmi přístupu.** Pokud definujete vlastnosti pro čtení i zápis, Volitelně můžete zadat úroveň různý přístup pro buď `Get` nebo `Set` postup, ale ne obojí. Pokud to uděláte, musí být více omezující než úroveň přístupu vlastnosti úroveň řízení přístupu. Například, pokud je deklarována vlastnost `Friend`, lze deklarovat `Set` postup `Private`, ale ne `Public`.  
  
     Pokud definujete `ReadOnly` nebo `WriteOnly` vlastnosti, procedury jedné vlastnosti (`Get` nebo `Set`v uvedeném pořadí) představuje všechny vlastnosti. Úroveň různý přístup pro tento postup nemůže deklarovat, protože dvě úrovně přístupu pro vlastnost, která byste nastavili.  
  
-   **Návratový typ.** `Property` Příkazu můžete deklarovat datový typ hodnoty vrácením. Můžete zadat libovolný datový typ nebo název výčtu, strukturu, třídu nebo rozhraní.  
  
     Pokud nezadáte `returntype`, vrátí vlastnost `Object`.  
  
-   **Implementace.** Pokud tuto vlastnost používá `Implements` – klíčové slovo, obsahuje třídu nebo strukturu, musíte mít `Implements` příkaz ihned po jeho `Class` nebo `Structure` příkaz. `Implements` Příkazu musí obsahovat každé rozhraní, udávaná v `implementslist`. Ale název, pomocí kterého rozhraní definuje `Property` (v `definedname`) nebude muset být stejný jako název této vlastnosti (v `name`).  
  
## <a name="behavior"></a>Chování  
  
-   **Návrat z procedury vlastnosti.** Když `Get` nebo `Set` postup vrátí volajícímu kódu, provádění pokračuje s příkazu za příkazem, která je vyvolána.  
  
     `Exit Property` a `Return` příkazy způsobit okamžité ukončení z procedury vlastnosti. Libovolný počet `Exit Property` a `Return` příkazů může vyskytovat kdekoli v postupu, a je možné kombinovat `Exit Property` a `Return` příkazy.  
  
-   **Vrátí hodnotu.** Pro navrácení hodnoty z `Get` postup, můžete přiřadit hodnoty pro název vlastnosti, nebo ho v `Return` příkazu. Následující příklad přiřadí návratovou hodnotu pro název vlastnosti `quoteForTheDay` a použije je `Exit Property` příkazu vrátit.  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_2.vb)]  
  
     Pokud používáte `Exit Property` bez přiřazení hodnoty k `name`, `Get` procedura vrací výchozí hodnota pro typ dat vlastnosti.  
  
     `Return` Příkaz v době, přiřadí `Get` procedura vracet hodnotu a ukončí proceduru. Následující příklad ukazuje to.  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_3.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje vlastnosti ve třídě.  
  
 [!code-vb[VbVbalrStatements#51](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_4.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Automaticky implementované vlastnosti](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)  
 [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Příkaz Get](../../../visual-basic/language-reference/statements/get-statement.md)  
 [Příkaz Set](../../../visual-basic/language-reference/statements/set-statement.md)  
 [Seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [Default](../../../visual-basic/language-reference/modifiers/default.md)
