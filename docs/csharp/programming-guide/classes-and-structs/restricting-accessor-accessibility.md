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
# <a name="restricting-accessor-accessibility-c-programming-guide"></a><span data-ttu-id="c154b-102">Omezení přístupnosti přístupového objektu (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="c154b-102">Restricting Accessor Accessibility (C# Programming Guide)</span></span>
<span data-ttu-id="c154b-103">Get [get](../../language-reference/keywords/get.md) a [set](../../language-reference/keywords/set.md) části vlastnosti nebo indexeru se nazývají *přístupové objekty*.</span><span class="sxs-lookup"><span data-stu-id="c154b-103">The [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) portions of a property or indexer are called *accessors*.</span></span> <span data-ttu-id="c154b-104">Ve výchozím nastavení tyto přístupové objekty mají stejnou viditelnost nebo úroveň přístupu vlastnosti nebo indexeru, ke kterému patří.</span><span class="sxs-lookup"><span data-stu-id="c154b-104">By default these accessors have the same visibility or access level of the property or indexer to which they belong.</span></span> <span data-ttu-id="c154b-105">Další informace naleznete v [tématu úrovně usnadnění přístupu](../../language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="c154b-105">For more information, see [accessibility levels](../../language-reference/keywords/accessibility-levels.md).</span></span> <span data-ttu-id="c154b-106">Někdy je však užitečné omezit přístup k jednomu z těchto přistupujících typů.</span><span class="sxs-lookup"><span data-stu-id="c154b-106">However, it is sometimes useful to restrict access to one of these accessors.</span></span> <span data-ttu-id="c154b-107">Obvykle to zahrnuje omezení přístupu `set` přistupujícího `get` objektu při zachování přístupu veřejně přístupné.</span><span class="sxs-lookup"><span data-stu-id="c154b-107">Typically, this involves restricting the accessibility of the `set` accessor, while keeping the `get` accessor publicly accessible.</span></span> <span data-ttu-id="c154b-108">Například:</span><span class="sxs-lookup"><span data-stu-id="c154b-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#6)]  
  
 <span data-ttu-id="c154b-109">V tomto příkladu `Name` vlastnost s `get` `set` názvem definuje a přistupující objekt.</span><span class="sxs-lookup"><span data-stu-id="c154b-109">In this example, a property called `Name` defines a `get` and `set` accessor.</span></span> <span data-ttu-id="c154b-110">Přistupující `get` objekt obdrží úroveň usnadnění `public` samotné vlastnosti, `set` v tomto případě zatímco přistupující objekt je explicitně omezen použitím [modifikátoru chráněného](../../language-reference/keywords/protected.md) přístupu na samotného přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="c154b-110">The `get` accessor receives the accessibility level of the property itself, `public` in this case, while the `set` accessor is explicitly restricted by applying the [protected](../../language-reference/keywords/protected.md) access modifier to the accessor itself.</span></span>  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a><span data-ttu-id="c154b-111">Omezení modifikátorů přístupu u přistupujících</span><span class="sxs-lookup"><span data-stu-id="c154b-111">Restrictions on Access Modifiers on Accessors</span></span>  
 <span data-ttu-id="c154b-112">Použití modifikátorů přistupujícího objektu na vlastnosti nebo indexery podléhá těmto podmínkám:</span><span class="sxs-lookup"><span data-stu-id="c154b-112">Using the accessor modifiers on properties or indexers is subject to these conditions:</span></span>  
  
- <span data-ttu-id="c154b-113">Modifikátory přistupujícího objektu nelze použít v rozhraní nebo explicitní implementaci člena [rozhraní.](../../language-reference/keywords/interface.md)</span><span class="sxs-lookup"><span data-stu-id="c154b-113">You cannot use accessor modifiers on an interface or an explicit [interface](../../language-reference/keywords/interface.md) member implementation.</span></span>  
  
- <span data-ttu-id="c154b-114">Modifikátory přistupujícího objektu můžete použít `set` `get` pouze v případě, že vlastnost nebo indexer má oba a přistupující objekty.</span><span class="sxs-lookup"><span data-stu-id="c154b-114">You can use accessor modifiers only if the property or indexer has both `set` and `get` accessors.</span></span> <span data-ttu-id="c154b-115">V tomto případě modifikátor je povoleno pouze na jeden ze dvou přistupujících částí.</span><span class="sxs-lookup"><span data-stu-id="c154b-115">In this case, the modifier is permitted on only one of the two accessors.</span></span>  
  
- <span data-ttu-id="c154b-116">Pokud vlastnost nebo indexer má [přepsání](../../language-reference/keywords/override.md) modifikátor, modifikátor přistupujícího objektu musí odpovídat přistupujícího objektu, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="c154b-116">If the property or indexer has an [override](../../language-reference/keywords/override.md) modifier, the accessor modifier must match the accessor of the overridden accessor, if any.</span></span>  
  
- <span data-ttu-id="c154b-117">Úroveň usnadnění na přistupujícího objektu musí být více omezující než úroveň usnadnění na vlastnost nebo indexer u samotného indexeru.</span><span class="sxs-lookup"><span data-stu-id="c154b-117">The accessibility level on the accessor must be more restrictive than the accessibility level on the property or indexer itself.</span></span>  
  
## <a name="access-modifiers-on-overriding-accessors"></a><span data-ttu-id="c154b-118">Modifikátory přístupu k přepsání přístupů</span><span class="sxs-lookup"><span data-stu-id="c154b-118">Access Modifiers on Overriding Accessors</span></span>  
 <span data-ttu-id="c154b-119">Když přepíšete vlastnost nebo indexer, musí být přepsané přístupové objekty přístupné pro přepsání kódu.</span><span class="sxs-lookup"><span data-stu-id="c154b-119">When you override a property or indexer, the overridden accessors must be accessible to the overriding code.</span></span> <span data-ttu-id="c154b-120">Přístupka vlastnost/indexer a jeho přístupové objekty musí odpovídat odpovídající přepsané vlastnost/indexer a jeho přístupové objekty.</span><span class="sxs-lookup"><span data-stu-id="c154b-120">Also, the accessibility of both the property/indexer and its accessors must match the corresponding overridden property/indexer and its accessors.</span></span> <span data-ttu-id="c154b-121">Například:</span><span class="sxs-lookup"><span data-stu-id="c154b-121">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#7)]  
  
## <a name="implementing-interfaces"></a><span data-ttu-id="c154b-122">Implementace rozhraní</span><span class="sxs-lookup"><span data-stu-id="c154b-122">Implementing Interfaces</span></span>  
 <span data-ttu-id="c154b-123">Při použití přistupujícího objektu k implementaci rozhraní, přistupující objekt nemusí mít modifikátor přístupu.</span><span class="sxs-lookup"><span data-stu-id="c154b-123">When you use an accessor to implement an interface, the accessor may not have an access modifier.</span></span> <span data-ttu-id="c154b-124">Pokud však implementujete rozhraní pomocí `get`jednoho přistupujícího objektu, například , může mít druhý přistupující objekt modifikátor přístupu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c154b-124">However, if you implement the interface using one accessor, such as `get`, the other accessor can have an access modifier, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#8)]  
  
## <a name="accessor-accessibility-domain"></a><span data-ttu-id="c154b-125">Přistupující doména přístupového přístupu</span><span class="sxs-lookup"><span data-stu-id="c154b-125">Accessor Accessibility Domain</span></span>  
 <span data-ttu-id="c154b-126">Pokud použijete modifikátor přístupu na přistupujícího objektu, [doména usnadnění](../../language-reference/keywords/accessibility-domain.md) přistupujícího objektu je určena tímto modifikátorem.</span><span class="sxs-lookup"><span data-stu-id="c154b-126">If you use an access modifier on the accessor, the [accessibility domain](../../language-reference/keywords/accessibility-domain.md) of the accessor is determined by this modifier.</span></span>  
  
 <span data-ttu-id="c154b-127">Pokud jste nepoužili modifikátor přístupu na přistupujícího objektu, doména usnadnění přistupujícího objektu je určena úroveň usnadnění vlastnosti nebo indexeru.</span><span class="sxs-lookup"><span data-stu-id="c154b-127">If you did not use an access modifier on the accessor, the accessibility domain of the accessor is determined by the accessibility level of the property or indexer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c154b-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="c154b-128">Example</span></span>  
 <span data-ttu-id="c154b-129">Následující příklad obsahuje tři `BaseClass` `DerivedClass`třídy `MainClass`, a .</span><span class="sxs-lookup"><span data-stu-id="c154b-129">The following example contains three classes, `BaseClass`, `DerivedClass`, and `MainClass`.</span></span> <span data-ttu-id="c154b-130">Existují dvě vlastnosti `BaseClass` `Name` na `Id` , a na obou třídách.</span><span class="sxs-lookup"><span data-stu-id="c154b-130">There are two properties on the `BaseClass`, `Name` and `Id` on both classes.</span></span> <span data-ttu-id="c154b-131">Příklad ukazuje, jak `Id` `DerivedClass` může být vlastnost `Id` skryta vlastností při `BaseClass` použití omezujícího modifikátoru přístupu, například [chráněné](../../language-reference/keywords/protected.md) nebo [soukromé](../../language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="c154b-131">The example demonstrates how the property `Id` on `DerivedClass` can be hidden by the property `Id` on `BaseClass` when you use a restrictive access modifier such as [protected](../../language-reference/keywords/protected.md) or [private](../../language-reference/keywords/private.md).</span></span> <span data-ttu-id="c154b-132">Proto při přiřazení hodnot této vlastnosti, `BaseClass` vlastnost na třídu je volána místo.</span><span class="sxs-lookup"><span data-stu-id="c154b-132">Therefore, when you assign values to this property, the property on the `BaseClass` class is called instead.</span></span> <span data-ttu-id="c154b-133">Nahrazení modifikátor přístupu [veřejným](../../language-reference/keywords/public.md) zpřístupní vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c154b-133">Replacing the access modifier by [public](../../language-reference/keywords/public.md) will make the property accessible.</span></span>  
  
 <span data-ttu-id="c154b-134">Příklad také ukazuje, že omezující modifikátor přístupu, `private` například `Name` nebo `DerivedClass` `protected`, na `set` přistupující objekt vlastnosti v příkazu zabraňuje přístupu k přistupujícímu objektu a generuje chybu, když k němu přiřadíte.</span><span class="sxs-lookup"><span data-stu-id="c154b-134">The example also demonstrates that a restrictive access modifier, such as `private` or `protected`, on the `set` accessor of the `Name` property in `DerivedClass` prevents access to the accessor and generates an error when you assign to it.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#5)]  
  
## <a name="comments"></a><span data-ttu-id="c154b-135">Komentáře</span><span class="sxs-lookup"><span data-stu-id="c154b-135">Comments</span></span>  
 <span data-ttu-id="c154b-136">Všimněte si, že `new private string Id` `new public string Id`pokud nahradíte prohlášení , získáte výstup:</span><span class="sxs-lookup"><span data-stu-id="c154b-136">Notice that if you replace the declaration `new private string Id` by `new public string Id`, you get the output:</span></span>  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a><span data-ttu-id="c154b-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="c154b-137">See also</span></span>

- [<span data-ttu-id="c154b-138">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c154b-138">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c154b-139">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c154b-139">Properties</span></span>](./properties.md)
- [<span data-ttu-id="c154b-140">Indexery</span><span class="sxs-lookup"><span data-stu-id="c154b-140">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="c154b-141">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="c154b-141">Access Modifiers</span></span>](./access-modifiers.md)
