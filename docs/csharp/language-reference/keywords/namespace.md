---
title: klíčové slovo Namespace C# – referenční informace
ms.custom: seoapril2019
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: 04595e96f6f14b8806a2d89625151910cac9e0d2
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345423"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="2d0fe-102">namespace (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="2d0fe-102">namespace (C# Reference)</span></span>

<span data-ttu-id="2d0fe-103">Klíčové slovo `namespace` slouží k deklaraci oboru, který obsahuje sadu souvisejících objektů.</span><span class="sxs-lookup"><span data-stu-id="2d0fe-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="2d0fe-104">Obor názvů můžete použít k uspořádání prvků kódu a k vytvoření globálně jedinečných typů.</span><span class="sxs-lookup"><span data-stu-id="2d0fe-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a><span data-ttu-id="2d0fe-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2d0fe-105">Remarks</span></span>

<span data-ttu-id="2d0fe-106">V rámci oboru názvů můžete deklarovat nula nebo více následujících typů:</span><span class="sxs-lookup"><span data-stu-id="2d0fe-106">Within a namespace, you can declare zero or more of the following types:</span></span>

- <span data-ttu-id="2d0fe-107">jiný obor názvů</span><span class="sxs-lookup"><span data-stu-id="2d0fe-107">another namespace</span></span>

- [<span data-ttu-id="2d0fe-108">class</span><span class="sxs-lookup"><span data-stu-id="2d0fe-108">class</span></span>](class.md)

- [<span data-ttu-id="2d0fe-109">interface</span><span class="sxs-lookup"><span data-stu-id="2d0fe-109">interface</span></span>](interface.md)

- [<span data-ttu-id="2d0fe-110">struct</span><span class="sxs-lookup"><span data-stu-id="2d0fe-110">struct</span></span>](struct.md)

- [<span data-ttu-id="2d0fe-111">enum</span><span class="sxs-lookup"><span data-stu-id="2d0fe-111">enum</span></span>](../builtin-types/enum.md)

- [<span data-ttu-id="2d0fe-112">delegate</span><span class="sxs-lookup"><span data-stu-id="2d0fe-112">delegate</span></span>](../builtin-types/reference-types.md#the-delegate-type)

<span data-ttu-id="2d0fe-113">Bez ohledu na to, jestli explicitně deklarujete obor C# názvů ve zdrojovém souboru, kompilátor přidá výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="2d0fe-113">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="2d0fe-114">Tento nepojmenovaný obor názvů, který se někdy označuje jako globální obor názvů, se nachází v každém souboru.</span><span class="sxs-lookup"><span data-stu-id="2d0fe-114">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="2d0fe-115">Libovolný identifikátor v globálním oboru názvů je k dispozici pro použití v pojmenovaném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2d0fe-115">Any identifier in the global namespace is available for use in a named namespace.</span></span>

<span data-ttu-id="2d0fe-116">Obory názvů mají implicitně veřejný přístup a nelze je upravovat.</span><span class="sxs-lookup"><span data-stu-id="2d0fe-116">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="2d0fe-117">Diskuzi o modifikátorech přístupu, které můžete přiřadit k prvkům v oboru názvů, najdete v tématu [modifikátory přístupu](access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="2d0fe-117">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](access-modifiers.md).</span></span>

<span data-ttu-id="2d0fe-118">Je možné definovat obor názvů ve dvou nebo více deklaracích.</span><span class="sxs-lookup"><span data-stu-id="2d0fe-118">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="2d0fe-119">Například následující příklad definuje dvě třídy jako součást oboru názvů `MyCompany`:</span><span class="sxs-lookup"><span data-stu-id="2d0fe-119">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a><span data-ttu-id="2d0fe-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="2d0fe-120">Example</span></span>

<span data-ttu-id="2d0fe-121">Následující příklad ukazuje, jak zavolat statickou metodu ve vnořeném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2d0fe-121">The following example shows how to call a static method in a nested namespace.</span></span>

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="2d0fe-122">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2d0fe-122">C# language specification</span></span>

<span data-ttu-id="2d0fe-123">Další informace najdete v části [obory názvů](~/_csharplang/spec/namespaces.md) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="2d0fe-123">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2d0fe-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d0fe-124">See also</span></span>

- [<span data-ttu-id="2d0fe-125">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="2d0fe-125">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2d0fe-126">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2d0fe-126">C# keywords</span></span>](index.md)
- [<span data-ttu-id="2d0fe-127">using</span><span class="sxs-lookup"><span data-stu-id="2d0fe-127">using</span></span>](using-directive.md)
- [<span data-ttu-id="2d0fe-128">Použití static</span><span class="sxs-lookup"><span data-stu-id="2d0fe-128">using static</span></span>](using-static.md)
- [<span data-ttu-id="2d0fe-129">`::` kvalifikátoru aliasu oboru názvů</span><span class="sxs-lookup"><span data-stu-id="2d0fe-129">Namespace alias qualifier `::`</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="2d0fe-130">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="2d0fe-130">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
