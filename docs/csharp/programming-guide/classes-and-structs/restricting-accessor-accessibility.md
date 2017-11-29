---
title: "Omezení přístupnosti přístupového objektu (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accesibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a4905885323f59d8b8b2654a5331e02054334398
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a>Omezení přístupnosti přístupového objektu (Průvodce programováním v C#)
[Získat](../../../csharp/language-reference/keywords/get.md) a [nastavit](../../../csharp/language-reference/keywords/set.md) části vlastnosti nebo indexeru se nazývají *přístupové objekty*. Ve výchozím nastavení mají stejné viditelnost těchto přístupových objektů, nebo úroveň přístupu: u vlastnosti nebo indexeru, do které patří. Další informace najdete v tématu [úrovní přístupu](../../../csharp/language-reference/keywords/accessibility-levels.md). Někdy je však vhodné omezit přístup na jednu z těchto přístupových objektů. Obvykle to zahrnuje omezení přístupnosti `set` přistupujícího objektu, při zachování `get` přistupujícího objektu veřejně přístupná. Příklad:  
  
 [!code-csharp[csProgGuideIndexers#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_1.cs)]  
  
 V tomto příkladu vlastnost s názvem `Name` definuje `get` a `set` přistupujícího objektu. `get` Přistupujícího objektu obdrží usnadnění úroveň samotné, vlastnosti `public` v takovém případě při `set` přistupujícího objektu je omezená explicitně použitím [chráněné](../../../csharp/language-reference/keywords/protected.md) – modifikátor přístupu k přistupující objekt sám sebe.  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a>Omezení modifikátory přístupu na přístupové objekty  
 Pomocí modifikátory přistupujícího objektu vlastnosti nebo indexery je nutné splnit následující podmínky:  
  
-   Modifikátory přistupujícího objektu nelze použít na rozhraní nebo pomocí explicitní [rozhraní](../../../csharp/language-reference/keywords/interface.md) implementaci prvku.  
  
-   Modifikátory přistupující objekt můžete použít pouze v případě, že jsou vlastnost nebo indexer má oba `set` a `get` přistupující objekty. V takovém případě je modifikátor povolená na jedné ze dvou přístupových objektů.  
  
-   Pokud má vlastnost nebo indexer [přepsat](../../../csharp/language-reference/keywords/override.md) modifikátor, modifikátor přistupujícího objektu se musí shodovat přistupujícího objektu přepsaného přistupujícího objektu, pokud existuje.  
  
-   Úroveň usnadnění na přistupujícím objektu musí být více omezující než úroveň usnadnění na vlastnost nebo indexer sám sebe.  
  
## <a name="access-modifiers-on-overriding-accessors"></a>Modifikátory přístupu při přepsání přístupové objekty  
 Při přepsání vlastnosti nebo indexeru, musí být přístupný pro kód přepsání přepsaného přistupující objekty. Navíc úroveň usnadnění jak vlastnost/indexeru a že přístupové objekty musí odpovídat odpovídající přepsané vlastnosti nebo indexeru a přístupy. Příklad:  
  
 [!code-csharp[csProgGuideIndexers#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_2.cs)]  
  
## <a name="implementing-interfaces"></a>Implementace rozhraní  
 Pokud používáte přistupující objekt k implementaci rozhraní, nemusí mít přistupující – modifikátor přístupu. Ale pokud budete implementovat rozhraní pomocí jednoho přístupového objektu, například `get`, jiné přistupující objekt může mít – modifikátor přístupu, jako v následujícím příkladu:  
  
 [!code-csharp[csProgGuideIndexers#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_3.cs)]  
  
## <a name="accessor-accessibility-domain"></a>Doména přístupnosti přístupového objektu  
 Používáte-li – modifikátor přístupu přistupujícího objektu, [doména přístupnosti](../../../csharp/language-reference/keywords/accessibility-domain.md) přistupujícího objektu je dáno tento modifikátor.  
  
 Pokud jste nepoužili – modifikátor přístupu na přistupujícím objektu, doména přístupnosti přistupujícího objektu je určen podle usnadnění úroveň vlastnost nebo indexer.  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje tři třídy `BaseClass`, `DerivedClass`, a `MainClass`. Existují dvě vlastnosti na `BaseClass`, `Name` a `Id` u obou tříd. Příklad ukazuje, jak vlastnost `Id` na `DerivedClass` může být skryté vlastností `Id` na `BaseClass` při použití – modifikátor omezující přístupu, jako [chráněné](../../../csharp/language-reference/keywords/protected.md) nebo [ privátní](../../../csharp/language-reference/keywords/private.md). Proto když přiřadit hodnoty této vlastnosti, vlastnost na `BaseClass` třídy se nazývá místo. Nahrazení – modifikátor přístupu podle [veřejné](../../../csharp/language-reference/keywords/public.md) bude zpřístupněte vlastnost.  
  
 Příklad také ukazuje, který modifikátor omezující přístup, například `private` nebo `protected`na `set` přistupujícího `Name` vlastnost v `DerivedClass` brání přístupu na přistupující objekt a vygeneruje se chyba při přiřazení do ho.  
  
 [!code-csharp[csProgGuideIndexers#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_4.cs)]  
  
## <a name="comments"></a>Komentáře  
 Všimněte si, že pokud nahradíte deklaraci `new private string Id` podle `new public string Id`, získat výstup:  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Indexery](../../../csharp/programming-guide/indexers/index.md)  
 [Modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
