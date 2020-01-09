---
title: Omezení přístupnosti přístupového objektu – C# Průvodce programováním
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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714695"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a>Omezení přístupnosti přístupového objektu (Průvodce programováním v C#)
Části [Get](../../language-reference/keywords/get.md) a [set](../../language-reference/keywords/set.md) vlastnosti nebo indexeru se nazývají *přistupující objekty*. Ve výchozím nastavení mají tyto přistupující objekty stejnou viditelnost nebo úroveň přístupu k vlastnosti nebo indexeru, ke kterému patří. Další informace najdete v tématu [úrovně usnadnění](../../language-reference/keywords/accessibility-levels.md). Někdy je ale užitečné omezit přístup k jednomu z těchto přístupových objektů. Obvykle zahrnuje omezení přístupnosti přístupového objektu `set` a přitom zachování veřejně přístupného přístupového objektu `get`. Příklad:  
  
 [!code-csharp[csProgGuideIndexers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#6)]  
  
 V tomto příkladu vlastnost s názvem `Name` definuje přistupující objekt `get` a `set`. Přistupující objekt `get` obdrží úroveň přístupnosti samotné vlastnosti, `public` v tomto případě, zatímco přístupový objekt `set` je explicitně omezen použitím modifikátoru [Protected](../../language-reference/keywords/protected.md) Access na samotný přistupující objekt.  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a>Omezení pro modifikátory přístupu u přístupových objektů  
 Používání modifikátorů přístupových objektů pro vlastnosti nebo indexery podléhá těmto podmínkám:  
  
- Nemůžete použít modifikátory přístupového objektu na rozhraní nebo explicitní implementaci člena [rozhraní](../../language-reference/keywords/interface.md) .  
  
- Můžete použít modifikátory přístupového objektu pouze v případě, že vlastnost nebo indexer mají přístupové objekty `set` i `get`. V tomto případě je modifikátor povolen pouze pro jeden ze dvou přístupových objektů.  
  
- Pokud má vlastnost nebo indexer modifikátor [přepsání](../../language-reference/keywords/override.md) , musí modifikátor přistupujícího objektu odpovídat přístupovému objektu přepsaného přístupového objektu, pokud existuje.  
  
- Úroveň přístupnosti u přístupového objektu musí být více omezující než úroveň přístupnosti samotné vlastnosti nebo indexeru samotného.  
  
## <a name="access-modifiers-on-overriding-accessors"></a>Modifikátory přístupu k přepsání přístupových objektů  
 Při přepsání vlastnosti nebo indexeru musí být přepsané přistupující objekty přístupné přepsání kódu. Přístupnost vlastnosti/indexeru i jeho přistupujících objektů musí být také shodná s odpovídající přepsanou vlastností/indexerem a jeho přistupujícími objekty. Příklad:  
  
 [!code-csharp[csProgGuideIndexers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#7)]  
  
## <a name="implementing-interfaces"></a>Implementace rozhraní  
 Použijete-li přistupující objekt k implementaci rozhraní, přistupující objekt nemusí mít modifikátor přístupu. Nicméně pokud implementujete rozhraní pomocí jednoho přístupového objektu, například `get`, druhý přistupující objekt může mít modifikátor přístupu, jak je uvedeno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideIndexers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#8)]  
  
## <a name="accessor-accessibility-domain"></a>Doména přístupnosti přístupového objektu  
 Použijete-li modifikátor přístupu u přístupového objektu, je [doména přístupnosti](../../language-reference/keywords/accessibility-domain.md) přistupujícího objektu určena tímto modifikátorem.  
  
 Pokud jste nepoužili modifikátor přístupu u přístupového objektu, je doména přístupnosti přistupujícího objektu určena úrovní přístupnosti vlastnosti nebo indexerem.  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje tři třídy, `BaseClass`, `DerivedClass`a `MainClass`. Existují dvě vlastnosti `BaseClass`, `Name` a `Id` v obou třídách. Příklad ukazuje, jak může být vlastnost `Id` v `DerivedClass` skryta vlastností `Id` na `BaseClass` při použití modifikátoru omezení přístupu, jako je například [Protected](../../language-reference/keywords/protected.md) nebo [Private](../../language-reference/keywords/private.md). Proto když přiřazujete hodnoty k této vlastnosti, je namísto toho volána vlastnost třídy `BaseClass`. Nahrazením modifikátoru přístupu [veřejným](../../language-reference/keywords/public.md) vlastnost zpřístupníte přístup k vlastnosti.  
  
 Příklad také ukazuje, že omezující modifikátor přístupu, například `private` nebo `protected`, v přístupovém objektu `set` vlastnosti `Name` v `DerivedClass` brání přístupu k přístupovému objektu a vygeneruje chybu, když k ní přiřadíte chybu.  
  
 [!code-csharp[csProgGuideIndexers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#5)]  
  
## <a name="comments"></a>Komentáře  
 Všimněte si, že pokud nahradíte deklaraci `new private string Id` `new public string Id`, získáte výstup:  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Vlastnosti](./properties.md)
- [Indexery](../indexers/index.md)
- [Modifikátory přístupu](./access-modifiers.md)
