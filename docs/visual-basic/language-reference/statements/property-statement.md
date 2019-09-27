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
ms.openlocfilehash: 2c3e417aad404171a43342dc92773615ec350ef5
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332748"
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

- `attributelist`

  Volitelný parametr. Seznam atributů, které se vztahují k této vlastnosti nebo proceduře `Get` nebo `Set`. Viz [seznam atributů](attribute-list.md).

- `Default`

  Volitelný parametr. Určuje, že tato vlastnost je výchozí vlastností třídy nebo struktury, ve které je definována. Výchozí vlastnosti musí přijímat parametry a lze je nastavit a načíst bez zadání názvu vlastnosti. Pokud vlastnost deklarujete jako `Default`, nemůžete použít `Private` u vlastnosti ani u obou jeho procedur vlastností.

- `accessmodifier`

  Volitelné v příkazu `Property` a maximálně jeden z příkazů `Get` a `Set`. Může být jedna z následujících akcí:

  - [Public](../modifiers/public.md)

  - [Protected](../modifiers/protected.md)

  - [Friend](../modifiers/friend.md)

  - [Private](../modifiers/private.md)

  - [Protected Friend](../modifiers/protected-friend.md)

  - [Private Protected](../modifiers/private-protected.md)

  Podívejte [se na úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

- `propertymodifiers`

  Volitelný parametr. Může být jedna z následujících akcí:

  - [Overloads](../modifiers/overloads.md)

  - [Overrides](../modifiers/overrides.md)

  - [Overridable](../modifiers/overridable.md)

  - [NotOverridable](../modifiers/notoverridable.md)

  - [MustOverride](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  Volitelný parametr. Viz [Shared](../modifiers/shared.md).

- `Shadows`

  Volitelný parametr. Viz [Shadows](../modifiers/shadows.md).

- `ReadOnly`

  Volitelný parametr. Zobrazit [jen pro čtení](../modifiers/readonly.md).

- `WriteOnly`

  Volitelný parametr. Viz [WriteOnly](../modifiers/writeonly.md).

- `Iterator`

  Volitelný parametr. Podívejte se na [iterátor](../modifiers/iterator.md).

- `name`

  Povinný parametr. Název vlastnosti Viz [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md).

- `parameterlist`

  Volitelný parametr. Seznam místních názvů proměnných reprezentujících parametry této vlastnosti a možné další parametry procedury `Set`. Viz [seznam parametrů](parameter-list.md).

- `returntype`

  Vyžaduje se, pokud je `Option Strict` `On`. Datový typ hodnoty vrácené touto vlastností

- `Implements`

  Volitelný parametr. Označuje, že tato vlastnost implementuje jednu nebo více vlastností, každý z nich definovaný v rozhraní implementovaném touto vlastností, která obsahuje třídu nebo strukturu. Viz [příkaz Implements](implements-statement.md).

- `implementslist`

  Vyžaduje se, pokud je dodána hodnota `Implements`. Seznam implementovaných vlastností.

  `implementedproperty [ , implementedproperty ... ]`

  Každý `implementedproperty` má následující syntaxi a části:

  `interface.definedname`

  |Částí|Popis|
  |---|---|
  |`interface`|Povinný parametr. Název rozhraní implementovaného touto vlastností, která obsahuje třídu nebo strukturu.|
  |`definedname`|Povinný parametr. Název, podle kterého je vlastnost definovaná v `interface`.|

- `Get`

  Volitelný parametr. Vyžaduje se, pokud je vlastnost označená `ReadOnly`. Spustí proceduru vlastnosti `Get`, která se používá k vrácení hodnoty vlastnosti.  Příkaz `Get` se nepoužívá s [automaticky implementovanými vlastnostmi](../../programming-guide/language-features/procedures/auto-implemented-properties.md).

- `statements`

  Volitelný parametr. Blok příkazů, které se mají spustit v proceduře `Get` nebo `Set`.

- `End Get`

  Ukončí proceduru vlastnosti `Get`.

- `Set`

  Volitelný parametr. Vyžaduje se, pokud je vlastnost označená `WriteOnly`. Spustí proceduru vlastnosti `Set`, která se používá k uložení hodnoty vlastnosti.  Příkaz `Set` se nepoužívá s [automaticky implementovanými vlastnostmi](../../programming-guide/language-features/procedures/auto-implemented-properties.md).

- `End Set`

  Ukončí proceduru vlastnosti `Set`.

- `End Property`

  Ukončí definici této vlastnosti.

## <a name="remarks"></a>Poznámky

Příkaz `Property` zavádí deklaraci vlastnosti. Vlastnost může mít proceduru @no__t 0 (jen pro čtení), proceduru `Set` (jen pro zápis) nebo obojí (pro čtení i zápis). Při použití automaticky implementované vlastnosti můžete vynechat postup `Get` a `Set`. Další informace najdete v tématu věnovaném [automaticky implementovaným vlastnostem](../../programming-guide/language-features/procedures/auto-implemented-properties.md).

@No__t-0 můžete použít pouze na úrovni třídy. To znamená, že *kontext deklarace* pro vlastnost musí být třída, struktura, modul nebo rozhraní a nemůže se jednat o zdrojový soubor, obor názvů, proceduru nebo blok. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](declaration-contexts-and-default-access-levels.md).

Ve výchozím nastavení vlastnosti používají veřejný přístup. Úroveň přístupu vlastnosti můžete upravit pomocí modifikátoru přístupu u příkazu `Property` a volitelně můžete upravit jedno z jeho procedur vlastností na úroveň přístupu s více omezujícími právy.

Visual Basic před přiřazením vlastností předává parametr do procedury `Set`. Pokud nezadáte parametr pro `Set`, integrované vývojové prostředí (IDE) používá implicitní parametr s názvem `value`. Tento parametr obsahuje hodnotu, která má být přiřazena vlastnosti. Tuto hodnotu obvykle ukládáte do privátní místní proměnné a vrátíte ji pokaždé, když je volána procedura `Get`.

## <a name="rules"></a>Pravidly

- **Smíšené úrovně přístupu.** Pokud definujete vlastnost pro čtení i zápis, můžete volitelně zadat jinou úroveň přístupu pro proceduru `Get` nebo `Set`, ale ne pro obě. Pokud to uděláte, musí být úroveň přístupu k této proceduře přísnější než úroveň přístupu vlastnosti. Například pokud je vlastnost deklarována `Friend`, můžete deklarovat proceduru `Set` `Private`, ale ne `Public`.

  Pokud definujete vlastnost `ReadOnly` nebo `WriteOnly`, bude jediná procedura vlastnosti (`Get` nebo `Set` v uvedeném pořadí) představovat všechny vlastnosti. Pro takový postup nemůžete deklarovat jinou úroveň přístupu, protože by se pro vlastnost nastavily dvě úrovně přístupu.

- **Návratový typ** Příkaz `Property` může deklarovat datový typ hodnoty, kterou vrátí. Můžete zadat libovolný datový typ nebo název výčtu, struktury, třídy nebo rozhraní.

  Pokud nezadáte `returntype`, vlastnost vrátí hodnotu `Object`.

- **Provádění.** Pokud tato vlastnost používá klíčové slovo `Implements`, obsahující třídu nebo strukturu musí mít příkaz `Implements` hned za příkazem `Class` nebo `Structure`. Příkaz `Implements` musí zahrnovat každé rozhraní zadané v `implementslist`. Název, kterým rozhraní definuje `Property` (v `definedname`), ale nemusí být stejný jako název této vlastnosti (v `name`).

## <a name="behavior"></a>Chování

- **Návrat z procedury vlastnosti.** Když se procedura `Get` nebo `Set` vrátí k volajícímu kódu, provádění pokračuje příkazem po příkazu, který ho vyvolal.

  Příkazy `Exit Property` a `Return` způsobují bezprostřední ukončení procedury vlastnosti. Libovolný počet příkazů `Exit Property` a `Return` se může objevit kdekoli v proceduře a můžete kombinovat příkazy `Exit Property` a `Return`.

- **Návratová hodnota** Chcete-li vrátit hodnotu z procedury `Get`, můžete buď přiřadit hodnotu k názvu vlastnosti, nebo ji zahrnout do příkazu `Return`. Následující příklad přiřadí návratovou hodnotu k názvu vlastnosti `quoteForTheDay` a pak použije příkaz `Exit Property`, který se má vrátit.

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]

  Použijete-li `Exit Property` bez přiřazení hodnoty k `name`, procedura `Get` vrátí výchozí hodnotu pro datový typ vlastnosti.

  Příkaz `Return` v současné době přiřadí návratovou hodnotu procedury `Get` a ukončí proceduru. Následující příklad ukazuje toto.

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]

## <a name="example"></a>Příklad

Následující příklad deklaruje vlastnost ve třídě.

[!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]

## <a name="see-also"></a>Viz také:

- [Automaticky implementované vlastnosti](../../programming-guide/language-features/procedures/auto-implemented-properties.md)
- [Objekty a třídy](../../programming-guide/language-features/objects-and-classes/index.md)
- [Příkaz Get](get-statement.md)
- [Příkaz Set](set-statement.md)
- [Seznam parametrů](parameter-list.md)
- [Výchozí](../modifiers/default.md)
