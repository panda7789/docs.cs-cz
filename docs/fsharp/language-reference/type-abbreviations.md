---
title: "Zkratky typů (F#)"
description: "Další informace o F # zkratky typů pojmenovat typu smysluplnější abyste snadněji kódu."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 560af74f-935f-415c-af56-604cddb9da6b
ms.openlocfilehash: 235c0240fe89d203b9474dec2b3f91947f453cd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="type-abbreviations"></a><span data-ttu-id="d9553-104">Zkratky typů</span><span class="sxs-lookup"><span data-stu-id="d9553-104">Type Abbreviations</span></span>

<span data-ttu-id="d9553-105">A *– zkratka typu* je alias nebo alternativní název typu.</span><span class="sxs-lookup"><span data-stu-id="d9553-105">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="d9553-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9553-106">Syntax</span></span>

```fsharp
type type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="d9553-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d9553-107">Remarks</span></span>
<span data-ttu-id="d9553-108">Zkratky typů můžete poskytnout typu více smysluplný název, abyste snadněji kódu.</span><span class="sxs-lookup"><span data-stu-id="d9553-108">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="d9553-109">Můžete je také použít k vytvoření snadno použitelný názvu pro typ, který je jinak náročná zapsat. Kromě toho aby bylo snazší změna základního typu beze změny jejího kódu, který používá typ můžete zkratky typů.</span><span class="sxs-lookup"><span data-stu-id="d9553-109">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="d9553-110">Toto je zkratka jednoduchého typu.</span><span class="sxs-lookup"><span data-stu-id="d9553-110">The following is a simple type abbreviation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="d9553-111">Zkratky typů může zahrnovat obecné parametry, jako v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="d9553-111">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="d9553-112">V předchozí kód `Transform` je zkratka typu, který představuje funkci, která přijímá jeden argument libovolného typu a který vrací jedinou hodnotu stejného typu.</span><span class="sxs-lookup"><span data-stu-id="d9553-112">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="d9553-113">Zkratky typů nejsou zachována v rozhraní .NET Framework MSIL kódu.</span><span class="sxs-lookup"><span data-stu-id="d9553-113">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="d9553-114">Proto při použití sestavení F # z jiný jazyk rozhraní .NET Framework, musíte použít název základního typu pro zkratka typu.</span><span class="sxs-lookup"><span data-stu-id="d9553-114">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="d9553-115">Zkratky typů můžete použít taky u měrné jednotky.</span><span class="sxs-lookup"><span data-stu-id="d9553-115">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="d9553-116">Další informace najdete v tématu [měrné jednotky](units-of-measure.md).</span><span class="sxs-lookup"><span data-stu-id="d9553-116">For more information, see [Units of Measure](units-of-measure.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="d9553-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9553-117">See Also</span></span>
[<span data-ttu-id="d9553-118">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="d9553-118">F# Language Reference</span></span>](index.md)

