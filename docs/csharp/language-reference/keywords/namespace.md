---
description: klíčové slovo Namespace – Referenční dokumentace jazyka C#
title: klíčové slovo Namespace – Referenční dokumentace jazyka C#
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: a6cfd1c3d37cbdef1f0dd72ddca85ce91f2e183b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139577"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="c094c-103">namespace (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c094c-103">namespace (C# Reference)</span></span>

<span data-ttu-id="c094c-104">`namespace`Klíčové slovo slouží k deklaraci oboru, který obsahuje sadu souvisejících objektů.</span><span class="sxs-lookup"><span data-stu-id="c094c-104">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="c094c-105">Obor názvů můžete použít k uspořádání prvků kódu a k vytvoření globálně jedinečných typů.</span><span class="sxs-lookup"><span data-stu-id="c094c-105">You can use a namespace to organize code elements and to create globally unique types.</span></span>

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a><span data-ttu-id="c094c-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c094c-106">Remarks</span></span>

<span data-ttu-id="c094c-107">V rámci oboru názvů můžete deklarovat nula nebo více následujících typů:</span><span class="sxs-lookup"><span data-stu-id="c094c-107">Within a namespace, you can declare zero or more of the following types:</span></span>

- <span data-ttu-id="c094c-108">jiný obor názvů</span><span class="sxs-lookup"><span data-stu-id="c094c-108">another namespace</span></span>

- [<span data-ttu-id="c094c-109">Deník</span><span class="sxs-lookup"><span data-stu-id="c094c-109">class</span></span>](class.md)

- [<span data-ttu-id="c094c-110">prostředí</span><span class="sxs-lookup"><span data-stu-id="c094c-110">interface</span></span>](interface.md)

- [<span data-ttu-id="c094c-111">nemají</span><span class="sxs-lookup"><span data-stu-id="c094c-111">struct</span></span>](../builtin-types/struct.md)

- [<span data-ttu-id="c094c-112">vytváření</span><span class="sxs-lookup"><span data-stu-id="c094c-112">enum</span></span>](../builtin-types/enum.md)

- [<span data-ttu-id="c094c-113">dostával</span><span class="sxs-lookup"><span data-stu-id="c094c-113">delegate</span></span>](../builtin-types/reference-types.md#the-delegate-type)

<span data-ttu-id="c094c-114">Bez ohledu na to, jestli explicitně deklarujete obor názvů ve zdrojovém souboru C#, kompilátor přidá výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="c094c-114">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="c094c-115">Tento nepojmenovaný obor názvů, který se někdy označuje jako globální obor názvů, se nachází v každém souboru.</span><span class="sxs-lookup"><span data-stu-id="c094c-115">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="c094c-116">Libovolný identifikátor v globálním oboru názvů je k dispozici pro použití v pojmenovaném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c094c-116">Any identifier in the global namespace is available for use in a named namespace.</span></span>

<span data-ttu-id="c094c-117">Obory názvů mají implicitně veřejný přístup a nelze je upravovat.</span><span class="sxs-lookup"><span data-stu-id="c094c-117">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="c094c-118">Diskuzi o modifikátorech přístupu, které můžete přiřadit k prvkům v oboru názvů, najdete v tématu [modifikátory přístupu](access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="c094c-118">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](access-modifiers.md).</span></span>

<span data-ttu-id="c094c-119">Je možné definovat obor názvů ve dvou nebo více deklaracích.</span><span class="sxs-lookup"><span data-stu-id="c094c-119">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="c094c-120">Například následující příklad definuje dvě třídy jako součást `MyCompany` oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="c094c-120">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a><span data-ttu-id="c094c-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="c094c-121">Example</span></span>

<span data-ttu-id="c094c-122">Následující příklad ukazuje, jak zavolat statickou metodu ve vnořeném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c094c-122">The following example shows how to call a static method in a nested namespace.</span></span>

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="c094c-123">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c094c-123">C# language specification</span></span>

<span data-ttu-id="c094c-124">Další informace najdete v části [obory názvů](~/_csharplang/spec/namespaces.md) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="c094c-124">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c094c-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="c094c-125">See also</span></span>

- [<span data-ttu-id="c094c-126">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="c094c-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c094c-127">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c094c-127">C# keywords</span></span>](index.md)
- [<span data-ttu-id="c094c-128">using</span><span class="sxs-lookup"><span data-stu-id="c094c-128">using</span></span>](using-directive.md)
- [<span data-ttu-id="c094c-129">Použití static</span><span class="sxs-lookup"><span data-stu-id="c094c-129">using static</span></span>](using-static.md)
- [<span data-ttu-id="c094c-130">Kvalifikátor aliasu oboru názvů `::`</span><span class="sxs-lookup"><span data-stu-id="c094c-130">Namespace alias qualifier `::`</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="c094c-131">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="c094c-131">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
