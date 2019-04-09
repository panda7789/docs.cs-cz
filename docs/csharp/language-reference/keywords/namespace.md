---
title: klíčové slovo oboru názvů - C# odkaz
ms.custom: seoapril2019
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: 4859c361b3321c1144204f63896152694f6ac5c9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148756"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="b96e9-102">namespace (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b96e9-102">namespace (C# Reference)</span></span>

<span data-ttu-id="b96e9-103">`namespace` – Klíčové slovo se používá k deklarování oboru, který obsahuje sadu souvisejících objektů.</span><span class="sxs-lookup"><span data-stu-id="b96e9-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="b96e9-104">Obor názvů slouží k uspořádání prvků kódu a vytváření globálně jedinečných typů.</span><span class="sxs-lookup"><span data-stu-id="b96e9-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a><span data-ttu-id="b96e9-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b96e9-105">Remarks</span></span>

<span data-ttu-id="b96e9-106">V rámci oboru názvů můžete deklarovat nula nebo více z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="b96e9-106">Within a namespace, you can declare zero or more of the following types:</span></span>

- <span data-ttu-id="b96e9-107">jiný obor názvů</span><span class="sxs-lookup"><span data-stu-id="b96e9-107">another namespace</span></span>

- [<span data-ttu-id="b96e9-108">třída</span><span class="sxs-lookup"><span data-stu-id="b96e9-108">class</span></span>](class.md)

- [<span data-ttu-id="b96e9-109">rozhraní</span><span class="sxs-lookup"><span data-stu-id="b96e9-109">interface</span></span>](interface.md)

- [<span data-ttu-id="b96e9-110">struct </span><span class="sxs-lookup"><span data-stu-id="b96e9-110">struct</span></span>](struct.md)

- [<span data-ttu-id="b96e9-111">enum</span><span class="sxs-lookup"><span data-stu-id="b96e9-111">enum</span></span>](enum.md)

- [<span data-ttu-id="b96e9-112">delegát</span><span class="sxs-lookup"><span data-stu-id="b96e9-112">delegate</span></span>](delegate.md)

<span data-ttu-id="b96e9-113">Zda explicitně deklarovat oboru názvů do zdrojového souboru jazyka C#, kompilátor přidá výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="b96e9-113">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="b96e9-114">Tato nepojmenovaného oboru názvů, někdy označovány jako globální obor názvů, je k dispozici v každém souboru.</span><span class="sxs-lookup"><span data-stu-id="b96e9-114">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="b96e9-115">Žádný identifikátor v globálním oboru názvů je k dispozici pro použití s názvem oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b96e9-115">Any identifier in the global namespace is available for use in a named namespace.</span></span>

<span data-ttu-id="b96e9-116">Obory názvů mají implicitně veřejný přístup, a to není možné upravit.</span><span class="sxs-lookup"><span data-stu-id="b96e9-116">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="b96e9-117">Informace o přístupu modifikátory přístupu můžete přiřadit na prvky v oboru názvů, naleznete v tématu [modifikátory přístupu](access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="b96e9-117">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](access-modifiers.md).</span></span>

<span data-ttu-id="b96e9-118">Je možné definovat ve dvou nebo více deklarací oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b96e9-118">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="b96e9-119">Například následující příklad definuje dvě třídy jako součást `MyCompany` obor názvů:</span><span class="sxs-lookup"><span data-stu-id="b96e9-119">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a><span data-ttu-id="b96e9-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="b96e9-120">Example</span></span>

<span data-ttu-id="b96e9-121">Následující příklad ukazuje, jak zavolat statickou metodu ve vnořené oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b96e9-121">The following example shows how to call a static method in a nested namespace.</span></span>

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="related-resources"></a><span data-ttu-id="b96e9-122">Související prostředky</span><span class="sxs-lookup"><span data-stu-id="b96e9-122">Related resources</span></span>

<span data-ttu-id="b96e9-123">Další informace o použití oboru názvů naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="b96e9-123">For more information about using namespaces, see the following topics:</span></span>

- [<span data-ttu-id="b96e9-124">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="b96e9-124">Namespaces</span></span>](../../programming-guide/namespaces/index.md)

- [<span data-ttu-id="b96e9-125">Použití oboru názvů</span><span class="sxs-lookup"><span data-stu-id="b96e9-125">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)

- [<span data-ttu-id="b96e9-126">Postupy: Použití aliasu globálního oboru názvů</span><span class="sxs-lookup"><span data-stu-id="b96e9-126">How to: Use the Global Namespace Alias</span></span>](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a><span data-ttu-id="b96e9-127">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b96e9-127">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b96e9-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b96e9-128">See also</span></span>

- [<span data-ttu-id="b96e9-129">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b96e9-129">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="b96e9-130">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="b96e9-130">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b96e9-131">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b96e9-131">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b96e9-132">Klíčová slova oboru názvů</span><span class="sxs-lookup"><span data-stu-id="b96e9-132">Namespace Keywords</span></span>](namespace-keywords.md)
- [<span data-ttu-id="b96e9-133">používání</span><span class="sxs-lookup"><span data-stu-id="b96e9-133">using</span></span>](using-directive.md)
- [<span data-ttu-id="b96e9-134">Pomocí statické</span><span class="sxs-lookup"><span data-stu-id="b96e9-134">using static</span></span>](using-static.md)