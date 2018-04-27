---
title: Property – příkaz
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 41
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 558b62dd8c676532355ef12134ad8cb803b70796
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="property-statement"></a>Property – příkaz
Deklaruje název vlastnosti a vlastnosti postupy používají k ukládání a načítání hodnoty vlastnosti.  
  
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
  
     Volitelné. Seznam atributů, které platí pro tuto vlastnost nebo `Get` nebo `Set` postupu. V tématu [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
-   `Default`  
  
     Volitelné. Určuje, že je tato vlastnost Výchozí vlastnost pro třídu nebo strukturu, na kterém je definovaný. Výchozí vlastnosti musí přijmout parametry a může být nastavit a načíst bez zadání názvu vlastnosti. Pokud je deklarovat vlastnost jako `Default`, nemůžete použít `Private` na vlastnost nebo na některý z jeho procedury vlastností.  
  
-   `accessmodifier`  
  
     Volitelné na `Property` příkaz a na maximálně jedno z `Get` a `Set` příkazy. Může být jedna z následujících akcí:  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     V tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
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
  
     Volitelné. V tématu [sdílené](../../../visual-basic/language-reference/modifiers/shared.md).  
  
-   `Shadows`  
  
     Volitelné. V tématu [stínů](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
-   `ReadOnly`  
  
     Volitelné. V tématu [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
-   `WriteOnly`  
  
     Volitelné. V tématu [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).  
  
-   `Iterator`  
  
     Volitelné. V tématu [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
-   `name`  
  
     Požadováno. Název vlastnosti V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   `parameterlist`  
  
     Volitelné. Seznam představující parametry této vlastnosti a možné další parametry místní názvy proměnných `Set` postupu. V tématu [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md).  
  
-   `returntype`  
  
     Požadováno pokud `Option``Strict` je `On`. Datový typ hodnoty vrácené tuto vlastnost.  
  
-   `Implements`  
  
     Volitelné. Označuje, že tato vlastnost implementuje jednu nebo více vlastností, každé z nich definované v rozhraní implementované obsahující třídu nebo strukturu tuto vlastnost. V tématu [implementuje příkaz](../../../visual-basic/language-reference/statements/implements-statement.md).  
  
-   `implementslist`  
  
     Požadováno pokud `Implements` pochází. Seznam vlastností se implementuje.  
  
     `implementedproperty [ , implementedproperty ... ]`  
  
     Každý `implementedproperty` má následující syntaxe a částí:  
  
     `interface.definedname`  
  
    |Část|Popis|  
    |---|---|  
    |`interface`|Požadováno. Název rozhraní implementované tato vlastnost obsahující třídu nebo strukturu.|  
    |`definedname`|Požadováno. Název, podle kterého je vlastnost definována v `interface`.|  
  
-   `Get`  
  
     Volitelné. Vyžaduje, pokud je vlastnost označena `WriteOnly`. Spustí `Get` procedury vlastnosti, která se používá k vrácení hodnoty vlastnosti.  
  
-   `statements`  
  
     Volitelné. Blok příkazů ke spuštění v rámci `Get` nebo `Set` postupu.  
  
-   `End Get`  
  
     Ukončí `Get` procedura property.  
  
-   `Set`  
  
     Volitelné. Vyžaduje, pokud je vlastnost označena `ReadOnly`. Spustí `Set` procedury vlastnosti, která se používá k ukládání hodnotu vlastnosti.  
  
-   `End Set`  
  
     Ukončí `Set` procedura property.  
  
-   `End Property`  
  
     Ukončí definici této vlastnosti.  
  
## <a name="remarks"></a>Poznámky  
 `Property` Příkaz zavádí deklarace vlastnosti. Může mít vlastnost `Get` postupu (jen pro čtení), `Set` procedura (pouze pro zápis) nebo obě (pro čtení a zápis). Můžete vynechat `Get` a `Set` procedury při použití ve automaticky implementované vlastnosti. Další informace najdete v tématu [Auto-Implemented vlastnosti](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).  
  
 Můžete použít `Property` jenom na úrovni třídy. To znamená *deklarace kontextu* pro vlastnost musí být třída, struktura, modul nebo rozhraní a nemůže být zdrojový soubor, obor názvů, postup nebo bloku. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Ve výchozím nastavení použijte vlastnosti veřejný přístup. Úroveň přístupu vlastnosti s – modifikátor přístupu můžete upravit na `Property` příkaz a můžete případně upravit jeden z jeho vlastnost postupů k více omezující úroveň přístupu.  
  
 Parametr, který se předá jazyka Visual Basic `Set` postup při přiřazení vlastnosti. Pokud nezadáte parametr pro `Set`, integrované vývojové prostředí (IDE) používá implicitní parametr s názvem `value`. Tento parametr obsahuje hodnota, která má být přiřazeno k vlastnosti. Obvykle uložte tuto hodnotu v privátní místní proměnné a obnoví v něm vždy, když `Get` procedura je volána.  
  
## <a name="rules"></a>Pravidla  
  
-   **Smíšenými úrovněmi přístupu.** Pokud definujete vlastnost pro čtení a zápis, Volitelně můžete zadat úroveň různý přístup pro buď `Get` nebo `Set` postup, ale ne obojí. Pokud to uděláte, musí být úroveň přístupu postup více omezující než úroveň přístupu vlastnosti. Například, pokud je deklarovaná vlastnost `Friend`, můžou deklarovat `Set` postup `Private`, ale ne `Public`.  
  
     Pokud definujete `ReadOnly` nebo `WriteOnly` vlastnost, postup jedinou vlastností (`Get` nebo `Set`, v uvedeném pořadí) představuje všechny vlastnosti. Vzhledem k tomu, který se nastavuje dvě úrovně přístupu pro vlastnost nelze deklarovat různý přístup úroveň pro tento postup.  
  
-   **Návratový typ.** `Property` Příkaz můžou deklarovat datový typ hodnoty, vrátí hodnotu. Můžete zadat jakýkoli datový typ nebo název výčtu, struktura, třídy nebo rozhraní.  
  
     Pokud nezadáte `returntype`, vrátí vlastnost `Object`.  
  
-   **Implementace.** Pokud tuto vlastnost používá `Implements` – klíčové slovo, obsahující třídu nebo strukturu, musíte mít `Implements` bezprostředně za jeho `Class` nebo `Structure` příkaz. `Implements` Příkaz musí zahrnovat každé rozhraní zadaný v `implementslist`. Ale název, podle kterého rozhraní definuje `Property` (v `definedname`) nemusí být stejný jako název této vlastnosti (v `name`).  
  
## <a name="behavior"></a>Chování  
  
-   **Vrácení z procedury vlastnosti.** Když `Get` nebo `Set` postup vrátí kód volání, provádění pokračuje s příkazem následující příkaz, která je volána.  
  
     `Exit Property` a `Return` příkazy způsobí okamžité ukončení z procedury vlastnosti. Libovolný počet `Exit Property` a `Return` příkazy může vyskytovat kdekoli v postupu, a je možné kombinovat `Exit Property` a `Return` příkazy.  
  
-   **Vrátí hodnotu.** Vrácení hodnoty z `Get` postup, můžete přiřadit hodnotu pro název vlastnosti nebo ji v zahrnout `Return` příkaz. Následující příklad přiřadí návratovou hodnotu pro název vlastnosti `quoteForTheDay` a použije je `Exit Property` příkaz, který má vrátit.  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_2.vb)]  
  
     Pokud používáte `Exit Property` bez přiřazení hodnoty k `name`, `Get` postup vrátí výchozí hodnota pro typ dat vlastnosti.  
  
     `Return` Příkaz ve stejnou dobu přiřazuje `Get` postup vracet hodnotu a ukončí proceduru. Následující příklad ukazuje to.  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_3.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje vlastnost v třídě.  
  
 [!code-vb[VbVbalrStatements#51](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_4.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Automaticky implementované vlastnosti](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)  
 [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Příkaz Get](../../../visual-basic/language-reference/statements/get-statement.md)  
 [Příkaz Set](../../../visual-basic/language-reference/statements/set-statement.md)  
 [Seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [Default](../../../visual-basic/language-reference/modifiers/default.md)
