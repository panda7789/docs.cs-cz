---
title: Omezení přístupnosti přístupového přístupu – programovací příručka jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accessibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: a332fef814f0c81914eb7b8c308de68f719fbaac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714695"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a>Omezení přístupnosti přístupového objektu (Průvodce programováním v C#)
Get [get](../../language-reference/keywords/get.md) a [set](../../language-reference/keywords/set.md) části vlastnosti nebo indexeru se nazývají *přístupové objekty*. Ve výchozím nastavení tyto přístupové objekty mají stejnou viditelnost nebo úroveň přístupu vlastnosti nebo indexeru, ke kterému patří. Další informace naleznete v [tématu úrovně usnadnění přístupu](../../language-reference/keywords/accessibility-levels.md). Někdy je však užitečné omezit přístup k jednomu z těchto přistupujících typů. Obvykle to zahrnuje omezení přístupu `set` přistupujícího `get` objektu při zachování přístupu veřejně přístupné. Například:  
  
 [!code-csharp[csProgGuideIndexers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#6)]  
  
 V tomto příkladu `Name` vlastnost s `get` `set` názvem definuje a přistupující objekt. Přistupující `get` objekt obdrží úroveň usnadnění `public` samotné vlastnosti, `set` v tomto případě zatímco přistupující objekt je explicitně omezen použitím [modifikátoru chráněného](../../language-reference/keywords/protected.md) přístupu na samotného přistupujícího objektu.  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a>Omezení modifikátorů přístupu u přistupujících  
 Použití modifikátorů přistupujícího objektu na vlastnosti nebo indexery podléhá těmto podmínkám:  
  
- Modifikátory přistupujícího objektu nelze použít v rozhraní nebo explicitní implementaci člena [rozhraní.](../../language-reference/keywords/interface.md)  
  
- Modifikátory přistupujícího objektu můžete použít `set` `get` pouze v případě, že vlastnost nebo indexer má oba a přistupující objekty. V tomto případě modifikátor je povoleno pouze na jeden ze dvou přistupujících částí.  
  
- Pokud vlastnost nebo indexer má [přepsání](../../language-reference/keywords/override.md) modifikátor, modifikátor přistupujícího objektu musí odpovídat přistupujícího objektu, pokud existuje.  
  
- Úroveň usnadnění na přistupujícího objektu musí být více omezující než úroveň usnadnění na vlastnost nebo indexer u samotného indexeru.  
  
## <a name="access-modifiers-on-overriding-accessors"></a>Modifikátory přístupu k přepsání přístupů  
 Když přepíšete vlastnost nebo indexer, musí být přepsané přístupové objekty přístupné pro přepsání kódu. Přístupka vlastnost/indexer a jeho přístupové objekty musí odpovídat odpovídající přepsané vlastnost/indexer a jeho přístupové objekty. Například:  
  
 [!code-csharp[csProgGuideIndexers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#7)]  
  
## <a name="implementing-interfaces"></a>Implementace rozhraní  
 Při použití přistupujícího objektu k implementaci rozhraní, přistupující objekt nemusí mít modifikátor přístupu. Pokud však implementujete rozhraní pomocí `get`jednoho přistupujícího objektu, například , může mít druhý přistupující objekt modifikátor přístupu, jako v následujícím příkladu:  
  
 [!code-csharp[csProgGuideIndexers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#8)]  
  
## <a name="accessor-accessibility-domain"></a>Přistupující doména přístupového přístupu  
 Pokud použijete modifikátor přístupu na přistupujícího objektu, [doména usnadnění](../../language-reference/keywords/accessibility-domain.md) přistupujícího objektu je určena tímto modifikátorem.  
  
 Pokud jste nepoužili modifikátor přístupu na přistupujícího objektu, doména usnadnění přistupujícího objektu je určena úroveň usnadnění vlastnosti nebo indexeru.  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje tři `BaseClass` `DerivedClass`třídy `MainClass`, a . Existují dvě vlastnosti `BaseClass` `Name` na `Id` , a na obou třídách. Příklad ukazuje, jak `Id` `DerivedClass` může být vlastnost `Id` skryta vlastností při `BaseClass` použití omezujícího modifikátoru přístupu, například [chráněné](../../language-reference/keywords/protected.md) nebo [soukromé](../../language-reference/keywords/private.md). Proto při přiřazení hodnot této vlastnosti, `BaseClass` vlastnost na třídu je volána místo. Nahrazení modifikátor přístupu [veřejným](../../language-reference/keywords/public.md) zpřístupní vlastnost.  
  
 Příklad také ukazuje, že omezující modifikátor přístupu, `private` například `Name` nebo `DerivedClass` `protected`, na `set` přistupující objekt vlastnosti v příkazu zabraňuje přístupu k přistupujícímu objektu a generuje chybu, když k němu přiřadíte.  
  
 [!code-csharp[csProgGuideIndexers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#5)]  
  
## <a name="comments"></a>Komentáře  
 Všimněte si, že `new private string Id` `new public string Id`pokud nahradíte prohlášení , získáte výstup:  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Vlastnosti](./properties.md)
- [Indexery](../indexers/index.md)
- [Modifikátory přístupu](./access-modifiers.md)
