---
title: Omezení přístupnost přístupového objektu – Průvodce programováním v C#
description: Přístupové objekty get a set vlastnosti v jazyce C# mají ve výchozím nastavení stejnou viditelnost nebo úroveň přístupu jako vlastnost, ke které patří. Můžete omezit přístup.
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accessibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: 18fd1d58dc6125b5180118b2e0d3edc885a4b971
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863965"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a><span data-ttu-id="cd498-104">Omezení přístupnosti přístupového objektu (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="cd498-104">Restricting Accessor Accessibility (C# Programming Guide)</span></span>
<span data-ttu-id="cd498-105">Části [Get](../../language-reference/keywords/get.md) a [set](../../language-reference/keywords/set.md) vlastnosti nebo indexeru se nazývají *přistupující objekty*.</span><span class="sxs-lookup"><span data-stu-id="cd498-105">The [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) portions of a property or indexer are called *accessors*.</span></span> <span data-ttu-id="cd498-106">Ve výchozím nastavení mají tyto přistupující objekty stejnou viditelnost nebo úroveň přístupu k vlastnosti nebo indexeru, ke kterému patří.</span><span class="sxs-lookup"><span data-stu-id="cd498-106">By default these accessors have the same visibility or access level of the property or indexer to which they belong.</span></span> <span data-ttu-id="cd498-107">Další informace najdete v tématu [úrovně usnadnění](../../language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="cd498-107">For more information, see [accessibility levels](../../language-reference/keywords/accessibility-levels.md).</span></span> <span data-ttu-id="cd498-108">Někdy je ale užitečné omezit přístup k jednomu z těchto přístupových objektů.</span><span class="sxs-lookup"><span data-stu-id="cd498-108">However, it is sometimes useful to restrict access to one of these accessors.</span></span> <span data-ttu-id="cd498-109">Obvykle to zahrnuje omezení dostupnosti `set` přístupového objektu a zároveň zachování `get` veřejně přístupného přístupového objektu.</span><span class="sxs-lookup"><span data-stu-id="cd498-109">Typically, this involves restricting the accessibility of the `set` accessor, while keeping the `get` accessor publicly accessible.</span></span> <span data-ttu-id="cd498-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="cd498-110">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#6)]  
  
 <span data-ttu-id="cd498-111">V tomto příkladu vlastnost s názvem `Name` definuje `get` a `set` přistupující objekt.</span><span class="sxs-lookup"><span data-stu-id="cd498-111">In this example, a property called `Name` defines a `get` and `set` accessor.</span></span> <span data-ttu-id="cd498-112">`get`Přistupující objekt obdrží úroveň přístupnosti samotné vlastnosti, `public` v tomto případě `set` je přístup explicitně omezen použitím modifikátoru [Protected](../../language-reference/keywords/protected.md) Access na samotný přistupující objekt.</span><span class="sxs-lookup"><span data-stu-id="cd498-112">The `get` accessor receives the accessibility level of the property itself, `public` in this case, while the `set` accessor is explicitly restricted by applying the [protected](../../language-reference/keywords/protected.md) access modifier to the accessor itself.</span></span>  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a><span data-ttu-id="cd498-113">Omezení pro modifikátory přístupu u přístupových objektů</span><span class="sxs-lookup"><span data-stu-id="cd498-113">Restrictions on Access Modifiers on Accessors</span></span>  
 <span data-ttu-id="cd498-114">Používání modifikátorů přístupových objektů pro vlastnosti nebo indexery podléhá těmto podmínkám:</span><span class="sxs-lookup"><span data-stu-id="cd498-114">Using the accessor modifiers on properties or indexers is subject to these conditions:</span></span>  
  
- <span data-ttu-id="cd498-115">Nemůžete použít modifikátory přístupového objektu na rozhraní nebo explicitní implementaci člena [rozhraní](../../language-reference/keywords/interface.md) .</span><span class="sxs-lookup"><span data-stu-id="cd498-115">You cannot use accessor modifiers on an interface or an explicit [interface](../../language-reference/keywords/interface.md) member implementation.</span></span>  
  
- <span data-ttu-id="cd498-116">Můžete použít modifikátory přístupového objektu pouze v případě, že vlastnost nebo indexer mají oba `set` a `get` přístupové objekty.</span><span class="sxs-lookup"><span data-stu-id="cd498-116">You can use accessor modifiers only if the property or indexer has both `set` and `get` accessors.</span></span> <span data-ttu-id="cd498-117">V tomto případě je modifikátor povolen pouze pro jeden ze dvou přístupových objektů.</span><span class="sxs-lookup"><span data-stu-id="cd498-117">In this case, the modifier is permitted on only one of the two accessors.</span></span>  
  
- <span data-ttu-id="cd498-118">Pokud má vlastnost nebo indexer modifikátor [přepsání](../../language-reference/keywords/override.md) , musí modifikátor přistupujícího objektu odpovídat přístupovému objektu přepsaného přístupového objektu, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="cd498-118">If the property or indexer has an [override](../../language-reference/keywords/override.md) modifier, the accessor modifier must match the accessor of the overridden accessor, if any.</span></span>  
  
- <span data-ttu-id="cd498-119">Úroveň přístupnosti u přístupového objektu musí být více omezující než úroveň přístupnosti samotné vlastnosti nebo indexeru samotného.</span><span class="sxs-lookup"><span data-stu-id="cd498-119">The accessibility level on the accessor must be more restrictive than the accessibility level on the property or indexer itself.</span></span>  
  
## <a name="access-modifiers-on-overriding-accessors"></a><span data-ttu-id="cd498-120">Modifikátory přístupu k přepsání přístupových objektů</span><span class="sxs-lookup"><span data-stu-id="cd498-120">Access Modifiers on Overriding Accessors</span></span>  
 <span data-ttu-id="cd498-121">Při přepsání vlastnosti nebo indexeru musí být přepsané přistupující objekty přístupné přepsání kódu.</span><span class="sxs-lookup"><span data-stu-id="cd498-121">When you override a property or indexer, the overridden accessors must be accessible to the overriding code.</span></span> <span data-ttu-id="cd498-122">Přístupnost vlastnosti/indexeru i jeho přistupujících objektů musí být také shodná s odpovídající přepsanou vlastností/indexerem a jeho přistupujícími objekty.</span><span class="sxs-lookup"><span data-stu-id="cd498-122">Also, the accessibility of both the property/indexer and its accessors must match the corresponding overridden property/indexer and its accessors.</span></span> <span data-ttu-id="cd498-123">Příklad:</span><span class="sxs-lookup"><span data-stu-id="cd498-123">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#7)]  
  
## <a name="implementing-interfaces"></a><span data-ttu-id="cd498-124">Implementace rozhraní</span><span class="sxs-lookup"><span data-stu-id="cd498-124">Implementing Interfaces</span></span>  
 <span data-ttu-id="cd498-125">Použijete-li přistupující objekt k implementaci rozhraní, přistupující objekt nemusí mít modifikátor přístupu.</span><span class="sxs-lookup"><span data-stu-id="cd498-125">When you use an accessor to implement an interface, the accessor may not have an access modifier.</span></span> <span data-ttu-id="cd498-126">Nicméně pokud implementujete rozhraní pomocí jednoho přístupového objektu, například `get` , druhý přistupující objekt může mít modifikátor přístupu, jak je uvedeno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="cd498-126">However, if you implement the interface using one accessor, such as `get`, the other accessor can have an access modifier, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#8)]  
  
## <a name="accessor-accessibility-domain"></a><span data-ttu-id="cd498-127">Doména přístupnosti přístupového objektu</span><span class="sxs-lookup"><span data-stu-id="cd498-127">Accessor Accessibility Domain</span></span>  
 <span data-ttu-id="cd498-128">Použijete-li modifikátor přístupu u přístupového objektu, je [doména přístupnosti](../../language-reference/keywords/accessibility-domain.md) přistupujícího objektu určena tímto modifikátorem.</span><span class="sxs-lookup"><span data-stu-id="cd498-128">If you use an access modifier on the accessor, the [accessibility domain](../../language-reference/keywords/accessibility-domain.md) of the accessor is determined by this modifier.</span></span>  
  
 <span data-ttu-id="cd498-129">Pokud jste nepoužili modifikátor přístupu u přístupového objektu, je doména přístupnosti přistupujícího objektu určena úrovní přístupnosti vlastnosti nebo indexerem.</span><span class="sxs-lookup"><span data-stu-id="cd498-129">If you did not use an access modifier on the accessor, the accessibility domain of the accessor is determined by the accessibility level of the property or indexer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd498-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd498-130">Example</span></span>  
 <span data-ttu-id="cd498-131">Následující příklad obsahuje tři třídy, `BaseClass` , a `DerivedClass` `MainClass` .</span><span class="sxs-lookup"><span data-stu-id="cd498-131">The following example contains three classes, `BaseClass`, `DerivedClass`, and `MainClass`.</span></span> <span data-ttu-id="cd498-132">Existují dvě vlastnosti v `BaseClass` `Name` a `Id` v obou třídách.</span><span class="sxs-lookup"><span data-stu-id="cd498-132">There are two properties on the `BaseClass`, `Name` and `Id` on both classes.</span></span> <span data-ttu-id="cd498-133">Příklad ukazuje, jak vlastnost `Id` on `DerivedClass` může být skryta vlastností `Id` `BaseClass` při použití modifikátoru restriktivního přístupu, jako je například [Protected](../../language-reference/keywords/protected.md) nebo [Private](../../language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="cd498-133">The example demonstrates how the property `Id` on `DerivedClass` can be hidden by the property `Id` on `BaseClass` when you use a restrictive access modifier such as [protected](../../language-reference/keywords/protected.md) or [private](../../language-reference/keywords/private.md).</span></span> <span data-ttu-id="cd498-134">Proto když přiřadíte hodnoty k této vlastnosti, vlastnost `BaseClass` třídy je volána místo toho.</span><span class="sxs-lookup"><span data-stu-id="cd498-134">Therefore, when you assign values to this property, the property on the `BaseClass` class is called instead.</span></span> <span data-ttu-id="cd498-135">Nahrazením modifikátoru přístupu [veřejným](../../language-reference/keywords/public.md) vlastnost zpřístupníte přístup k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cd498-135">Replacing the access modifier by [public](../../language-reference/keywords/public.md) will make the property accessible.</span></span>  
  
 <span data-ttu-id="cd498-136">Příklad také ukazuje, že omezující modifikátor přístupu, například `private` nebo `protected` , v přístupovém `set` objektu `Name` vlastnosti v systému `DerivedClass` zabraňuje přístup k přístupovému objektu a generuje chybu, když k ní přiřadíte chybu.</span><span class="sxs-lookup"><span data-stu-id="cd498-136">The example also demonstrates that a restrictive access modifier, such as `private` or `protected`, on the `set` accessor of the `Name` property in `DerivedClass` prevents access to the accessor and generates an error when you assign to it.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#5)]  
  
## <a name="comments"></a><span data-ttu-id="cd498-137">Komentáře</span><span class="sxs-lookup"><span data-stu-id="cd498-137">Comments</span></span>  
 <span data-ttu-id="cd498-138">Všimněte si, že pokud nahradíte deklaraci `new private string Id` pomocí `new public string Id` , získáte výstup:</span><span class="sxs-lookup"><span data-stu-id="cd498-138">Notice that if you replace the declaration `new private string Id` by `new public string Id`, you get the output:</span></span>  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a><span data-ttu-id="cd498-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd498-139">See also</span></span>

- [<span data-ttu-id="cd498-140">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="cd498-140">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="cd498-141">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="cd498-141">Properties</span></span>](./properties.md)
- [<span data-ttu-id="cd498-142">Indexery</span><span class="sxs-lookup"><span data-stu-id="cd498-142">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="cd498-143">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="cd498-143">Access Modifiers</span></span>](./access-modifiers.md)
