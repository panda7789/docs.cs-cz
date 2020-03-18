---
title: klíčové slovo oboru názvů – odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: b35f0a2a5cc0b2895b491d4ee24f89955f4b8fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77625797"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="ecd50-102">namespace (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ecd50-102">namespace (C# Reference)</span></span>

<span data-ttu-id="ecd50-103">Klíčové `namespace` slovo se používá k deklarování oboru, který obsahuje sadu souvisejících objektů.</span><span class="sxs-lookup"><span data-stu-id="ecd50-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="ecd50-104">Obor názvů můžete použít k uspořádání prvků kódu a k vytvoření globálně jedinečných typů.</span><span class="sxs-lookup"><span data-stu-id="ecd50-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a><span data-ttu-id="ecd50-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ecd50-105">Remarks</span></span>

<span data-ttu-id="ecd50-106">V rámci oboru názvů můžete deklarovat nulu nebo více z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="ecd50-106">Within a namespace, you can declare zero or more of the following types:</span></span>

- <span data-ttu-id="ecd50-107">jiný obor názvů</span><span class="sxs-lookup"><span data-stu-id="ecd50-107">another namespace</span></span>

- [<span data-ttu-id="ecd50-108">Třída</span><span class="sxs-lookup"><span data-stu-id="ecd50-108">class</span></span>](class.md)

- [<span data-ttu-id="ecd50-109">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="ecd50-109">interface</span></span>](interface.md)

- [<span data-ttu-id="ecd50-110">Struct</span><span class="sxs-lookup"><span data-stu-id="ecd50-110">struct</span></span>](../builtin-types/struct.md)

- [<span data-ttu-id="ecd50-111">Výčtu</span><span class="sxs-lookup"><span data-stu-id="ecd50-111">enum</span></span>](../builtin-types/enum.md)

- [<span data-ttu-id="ecd50-112">delegát</span><span class="sxs-lookup"><span data-stu-id="ecd50-112">delegate</span></span>](../builtin-types/reference-types.md#the-delegate-type)

<span data-ttu-id="ecd50-113">Bez ohledu na to, zda explicitně deklarujete obor názvů ve zdrojovém souboru jazyka C#, kompilátor přidá výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="ecd50-113">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="ecd50-114">Tento nepojmenovaný obor názvů, někdy označovaný jako globální obor názvů, je přítomen v každém souboru.</span><span class="sxs-lookup"><span data-stu-id="ecd50-114">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="ecd50-115">Všechny identifikátory v globálním oboru názvů jsou k dispozici pro použití v pojmenovaném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ecd50-115">Any identifier in the global namespace is available for use in a named namespace.</span></span>

<span data-ttu-id="ecd50-116">Obory názvů implicitně mají veřejný přístup a nelze je upravit.</span><span class="sxs-lookup"><span data-stu-id="ecd50-116">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="ecd50-117">Diskuse o modifikátory přístupu, které můžete přiřadit prvkům v oboru názvů, naleznete v [tématu Modifikátory aplikace Access](access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="ecd50-117">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](access-modifiers.md).</span></span>

<span data-ttu-id="ecd50-118">Je možné definovat obor názvů ve dvou nebo více deklaracích.</span><span class="sxs-lookup"><span data-stu-id="ecd50-118">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="ecd50-119">Například následující příklad definuje dvě třídy `MyCompany` jako součást oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="ecd50-119">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a><span data-ttu-id="ecd50-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="ecd50-120">Example</span></span>

<span data-ttu-id="ecd50-121">Následující příklad ukazuje, jak volat statickou metodu v vnořené oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ecd50-121">The following example shows how to call a static method in a nested namespace.</span></span>

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="ecd50-122">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ecd50-122">C# language specification</span></span>

<span data-ttu-id="ecd50-123">Další informace naleznete v části [Namespaces](~/_csharplang/spec/namespaces.md) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="ecd50-123">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ecd50-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="ecd50-124">See also</span></span>

- [<span data-ttu-id="ecd50-125">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="ecd50-125">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ecd50-126">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ecd50-126">C# keywords</span></span>](index.md)
- [<span data-ttu-id="ecd50-127">Pomocí</span><span class="sxs-lookup"><span data-stu-id="ecd50-127">using</span></span>](using-directive.md)
- [<span data-ttu-id="ecd50-128">použití statické</span><span class="sxs-lookup"><span data-stu-id="ecd50-128">using static</span></span>](using-static.md)
- [<span data-ttu-id="ecd50-129">Kvalifikátor aliasu oboru názvů`::`</span><span class="sxs-lookup"><span data-stu-id="ecd50-129">Namespace alias qualifier `::`</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="ecd50-130">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="ecd50-130">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
