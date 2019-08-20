---
title: Omezení přístupnosti přístupového objektu – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accessibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: ca990693d29f8c8abd2e4ba2488a429a797afaec
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596170"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a>Omezení přístupnosti přístupového objektu (Průvodce programováním v C#)
Části [Get](../../language-reference/keywords/get.md) a [set](../../language-reference/keywords/set.md) vlastnosti nebo indexeru se nazývají *přistupující objekty*. Ve výchozím nastavení mají tyto přistupující objekty stejnou viditelnost nebo úroveň přístupu k vlastnosti nebo indexeru, ke kterému patří. Další informace najdete v tématu [úrovně usnadnění](../../language-reference/keywords/accessibility-levels.md). Někdy je ale užitečné omezit přístup k jednomu z těchto přístupových objektů. Obvykle to zahrnuje omezení dostupnosti `set` přístupového objektu a zároveň `get` zachování veřejně přístupného přístupového objektu. Příklad:  
  
 [!code-csharp[csProgGuideIndexers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#6)]  
  
 V tomto příkladu vlastnost s názvem `Name` `get` definuje a `set` přistupující objekt. Přistupující objekt obdrží úroveň přístupnosti samotné vlastnosti, `public` v `set` tomto případě je přístup explicitně omezen použitím modifikátoru [Protected](../../language-reference/keywords/protected.md) Access na samotný přistupující objekt. `get`  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a>Omezení pro modifikátory přístupu u přístupových objektů  
 Používání modifikátorů přístupových objektů pro vlastnosti nebo indexery podléhá těmto podmínkám:  
  
- Nemůžete použít modifikátory přístupového objektu na rozhraní nebo explicitní implementaci člena [rozhraní](../../language-reference/keywords/interface.md) .  
  
- Můžete použít modifikátory přístupového objektu pouze v případě, že vlastnost nebo indexer `set` mají `get` oba a přístupové objekty. V tomto případě je modifikátor povolen pouze pro jeden ze dvou přístupových objektů.  
  
- Pokud má vlastnost nebo indexer modifikátor [přepsání](../../language-reference/keywords/override.md) , musí modifikátor přistupujícího objektu odpovídat přístupovému objektu přepsaného přístupového objektu, pokud existuje.  
  
- Úroveň přístupnosti u přístupového objektu musí být více omezující než úroveň přístupnosti samotné vlastnosti nebo indexeru samotného.  
  
## <a name="access-modifiers-on-overriding-accessors"></a>Modifikátory přístupu k přepsání přístupových objektů  
 Při přepsání vlastnosti nebo indexeru musí být přepsané přistupující objekty přístupné přepsání kódu. Přístupnost vlastnosti/indexeru i jeho přistupujících objektů musí být také shodná s odpovídající přepsanou vlastností/indexerem a jeho přistupujícími objekty. Příklad:  
  
 [!code-csharp[csProgGuideIndexers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#7)]  
  
## <a name="implementing-interfaces"></a>Implementace rozhraní  
 Použijete-li přistupující objekt k implementaci rozhraní, přistupující objekt nemusí mít modifikátor přístupu. Nicméně pokud implementujete rozhraní pomocí jednoho přístupového objektu, například `get`, druhý přistupující objekt může mít modifikátor přístupu, jak je uvedeno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideIndexers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#8)]  
  
## <a name="accessor-accessibility-domain"></a>Doména přístupnosti přístupového objektu  
 Použijete-li modifikátor přístupu u přístupového objektu, je [doména](../../language-reference/keywords/accessibility-domain.md) přístupnosti přistupujícího objektu určena tímto modifikátorem.  
  
 Pokud jste nepoužili modifikátor přístupu u přístupového objektu, je doména přístupnosti přistupujícího objektu určena úrovní přístupnosti vlastnosti nebo indexerem.  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje tři třídy, `BaseClass`, `DerivedClass` `MainClass`a. Existují dvě vlastnosti v `BaseClass` `Name` a `Id` v obou třídách. Příklad ukazuje, `Id` jak vlastnost on `DerivedClass` `BaseClass` může být skryta vlastností `Id` při použití modifikátoru restriktivního přístupu, jako je například [Protected](../../language-reference/keywords/protected.md) nebo [Private](../../language-reference/keywords/private.md). Proto když přiřadíte hodnoty k této vlastnosti, vlastnost `BaseClass` třídy je volána místo toho. Nahrazením modifikátoru přístupu [veřejným](../../language-reference/keywords/public.md) vlastnost zpřístupníte přístup k vlastnosti.  
  
 Příklad také ukazuje, že omezující modifikátor přístupu, například `private` nebo `protected`, `Name` na `set` přístup k vlastnosti v `DerivedClass` systému brání přístup k přístupovému objektu a generuje chybu při přiřazení k její.  
  
 [!code-csharp[csProgGuideIndexers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#5)]  
  
## <a name="comments"></a>Komentáře  
 Všimněte si, že pokud nahradíte `new private string Id` deklaraci pomocí `new public string Id`, získáte výstup:  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Vlastnosti](./properties.md)
- [Indexery](../indexers/index.md)
- [Modifikátory přístupu](./access-modifiers.md)
