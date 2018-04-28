---
title: Zkratky typů (F#)
description: 'Další informace o F # zkratky typů pojmenovat typu smysluplnější abyste snadněji kódu.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: bf17ee9795947fdc11fe958f09d52f5730b95bf8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="type-abbreviations"></a><span data-ttu-id="07518-103">Zkratky typů</span><span class="sxs-lookup"><span data-stu-id="07518-103">Type Abbreviations</span></span>

<span data-ttu-id="07518-104">A *– zkratka typu* je alias nebo alternativní název typu.</span><span class="sxs-lookup"><span data-stu-id="07518-104">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="07518-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07518-105">Syntax</span></span>

```fsharp
type type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="07518-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="07518-106">Remarks</span></span>
<span data-ttu-id="07518-107">Zkratky typů můžete poskytnout typu více smysluplný název, abyste snadněji kódu.</span><span class="sxs-lookup"><span data-stu-id="07518-107">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="07518-108">Můžete je také použít k vytvoření snadno použitelný názvu pro typ, který je jinak náročná zapsat. Kromě toho aby bylo snazší změna základního typu beze změny jejího kódu, který používá typ můžete zkratky typů.</span><span class="sxs-lookup"><span data-stu-id="07518-108">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="07518-109">Toto je zkratka jednoduchého typu.</span><span class="sxs-lookup"><span data-stu-id="07518-109">The following is a simple type abbreviation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="07518-110">Zkratky typů může zahrnovat obecné parametry, jako v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="07518-110">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="07518-111">V předchozí kód `Transform` je zkratka typu, který představuje funkci, která přijímá jeden argument libovolného typu a který vrací jedinou hodnotu stejného typu.</span><span class="sxs-lookup"><span data-stu-id="07518-111">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="07518-112">Zkratky typů nejsou zachována v rozhraní .NET Framework MSIL kódu.</span><span class="sxs-lookup"><span data-stu-id="07518-112">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="07518-113">Proto při použití sestavení F # z jiný jazyk rozhraní .NET Framework, musíte použít název základního typu pro zkratka typu.</span><span class="sxs-lookup"><span data-stu-id="07518-113">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="07518-114">Zkratky typů můžete použít taky u měrné jednotky.</span><span class="sxs-lookup"><span data-stu-id="07518-114">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="07518-115">Další informace najdete v tématu [měrné jednotky](units-of-measure.md).</span><span class="sxs-lookup"><span data-stu-id="07518-115">For more information, see [Units of Measure](units-of-measure.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="07518-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="07518-116">See Also</span></span>
[<span data-ttu-id="07518-117">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="07518-117">F# Language Reference</span></span>](index.md)

