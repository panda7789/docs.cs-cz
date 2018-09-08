---
title: Omezení přístupnosti přístupového objektu (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accesibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: 66e6f0da417e62bb592fdd8654f85cdb80ccf9bc
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44197201"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a>Omezení přístupnosti přístupového objektu (Průvodce programováním v C#)
[Získat](../../../csharp/language-reference/keywords/get.md) a [nastavit](../../../csharp/language-reference/keywords/set.md) části vlastnost nebo indexer, se nazývají *přistupující objekty*. Ve výchozím nastavení mají stejnou viditelnost těchto přístupových objektů, nebo úroveň přístupu: u vlastnost nebo indexovací člen, ke kterému patří. Další informace najdete v tématu [úrovní přístupu](../../../csharp/language-reference/keywords/accessibility-levels.md). Někdy je však užitečný k omezení přístupu k jednomu z těchto přístupových objektů. Obvykle to zahrnuje omezení přístupnost `set` přístupového objektu při zachování `get` přistupující objekt veřejně přístupná. Příklad:  
  
 [!code-csharp[csProgGuideIndexers#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_1.cs)]  
  
 V tomto příkladu vlastnost s názvem `Name` definuje `get` a `set` přistupujícího objektu. `get` Přistupující objekt obdrží úrovni přístupu, samotná hodnota vlastnosti `public` v tomto případě while `set` přístupový objekt je explicitně s omezením pomocí specifikátoru použitím [chráněné](../../../csharp/language-reference/keywords/protected.md) modifikátor přístupu k přístupový objekt samotný.  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a>Omezení přístupu modifikátory přístupu na přístupových objektů  
 Pomocí modifikátory přistupující objekt vlastnosti nebo indexery podléhá tyto podmínky:  
  
-   Přístupový objekt Modifikátory nelze použít na rozhraní nebo explicitní [rozhraní](../../../csharp/language-reference/keywords/interface.md) implementace členu.  
  
-   Modifikátory přístupového objektu můžete použít pouze v případě, že vlastnost nebo indexovací člen jsou obě `set` a `get` přistupující objekty. V takovém případě modifikátor můžou běžet na jedné ze dvou přístupových objektů.  
  
-   Pokud má vlastnost nebo indexer [přepsat](../../../csharp/language-reference/keywords/override.md) modifikátor, modifikátor přístupového objektu musí odpovídat přistupující objekt přepsané přístupového objektu, případné.  
  
-   Usnadnění úrovní na přistupujícím objektu musí být více omezující než úroveň přístupnost na vlastnost nebo indexovací člen, samotného.  
  
## <a name="access-modifiers-on-overriding-accessors"></a>Modifikátory přístupu pro přepsání přístupové objekty  
 Při přepsání vlastnost nebo indexovací člen přepsané přistupující objekty musí být přístupná pro přepsání kódu. Také úroveň usnadnění jak vlastnost nebo indexer a že přístupové objekty musí odpovídat odpovídající přepsané vlastnosti nebo indexeru a přístupové objekty. Příklad:  
  
 [!code-csharp[csProgGuideIndexers#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_2.cs)]  
  
## <a name="implementing-interfaces"></a>Implementace rozhraní  
 Při použití přístupový objekt pro implementaci rozhraní přistupujícím objektu nemusí mít modifikátor přístupu. Nicméně Pokud implementujete rozhraní pomocí jeden přistupující objekt, jako například `get`, další přístupový objekt může mít modifikátor přístupu, jako v následujícím příkladu:  
  
 [!code-csharp[csProgGuideIndexers#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_3.cs)]  
  
## <a name="accessor-accessibility-domain"></a>Doména přístupnosti přístupového objektu  
 Pokud použijete modifikátor přístupu nastaven na přístupový objekt, [doména přístupnosti](../../../csharp/language-reference/keywords/accessibility-domain.md) přistupujícím objektu je určen tento modifikátor.  
  
 Pokud jste nepoužili modifikátor přístupu nastaven na přistupujícím objektu, tak doména přístupnosti přístupového objektu se určuje podle úrovně přístupnosti vlastnost nebo indexer.  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje tři třídy `BaseClass`, `DerivedClass`, a `MainClass`. Existují dvě vlastnosti na `BaseClass`, `Name` a `Id` v obou třídách. Tento příklad ukazuje, jak vlastnost `Id` na `DerivedClass` může být skryta vlastnost `Id` na `BaseClass` při použití modifikátor omezení přístupu, jako [chráněné](../../../csharp/language-reference/keywords/protected.md) nebo [ privátní](../../../csharp/language-reference/keywords/private.md). Proto když přiřadit hodnoty této vlastnosti, vlastnost na `BaseClass` třída se nazývá místo. Nahrazení modifikátor přístupu podle [veřejné](../../../csharp/language-reference/keywords/public.md) zpřístupní vlastnosti.  
  
 Tento příklad také ukazuje, že modifikátor omezení přístupu, jako `private` nebo `protected`na `set` přistupující objekt `Name` vlastnost v `DerivedClass` brání v přístupu k přistupujícím objektu a vygeneruje chybu, pokud přiřadíte ho.  
  
 [!code-csharp[csProgGuideIndexers#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_4.cs)]  
  
## <a name="comments"></a>Komentáře  
 Všimněte si, že pokud nahradíte deklarace `new private string Id` podle `new public string Id`, získáte výstup:  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [Indexery](../../../csharp/programming-guide/indexers/index.md)  
- [Modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
