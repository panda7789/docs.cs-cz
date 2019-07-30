---
title: Zkratky typů
description: Přečtěte F# si o zkratkách typů, aby bylo možné zadat smysluplnější název, aby bylo snazší číst kód.
ms.date: 05/16/2016
ms.openlocfilehash: 339b22a675e3f1ad8a3da207053e611942b55a22
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630210"
---
# <a name="type-abbreviations"></a><span data-ttu-id="56bd4-103">Zkratky typů</span><span class="sxs-lookup"><span data-stu-id="56bd4-103">Type Abbreviations</span></span>

<span data-ttu-id="56bd4-104">*Zkratka typu* je alias nebo alternativní název pro typ.</span><span class="sxs-lookup"><span data-stu-id="56bd4-104">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="56bd4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56bd4-105">Syntax</span></span>

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="56bd4-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="56bd4-106">Remarks</span></span>

<span data-ttu-id="56bd4-107">Můžete použít zkratky typů k poskytnutí smysluplného názvu typu, aby bylo snazší číst kód.</span><span class="sxs-lookup"><span data-stu-id="56bd4-107">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="56bd4-108">Můžete je také použít k vytvoření snadno použitelného názvu pro typ, který je jinak nenáročný na zápis. Kromě toho můžete použít zkratky typů pro snadnější změnu nadřazeného typu bez změny veškerého kódu, který používá typ.</span><span class="sxs-lookup"><span data-stu-id="56bd4-108">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="56bd4-109">Následuje zkratka jednoduchého typu.</span><span class="sxs-lookup"><span data-stu-id="56bd4-109">The following is a simple type abbreviation.</span></span>

<span data-ttu-id="56bd4-110">Dostupnost zkratek typu se nastaví na `public`výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="56bd4-110">Accessibility of type abbreviations defaults to `public`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="56bd4-111">Zkratky typů mohou zahrnovat obecné parametry, jako v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="56bd4-111">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="56bd4-112">V předchozím kódu `Transform` je zkratka typu, která představuje funkci, která přijímá jeden argument libovolného typu a který vrací jedinou hodnotu stejného typu.</span><span class="sxs-lookup"><span data-stu-id="56bd4-112">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="56bd4-113">V kódu .NET Framework jazyka MSIL nejsou zachovány zkratky typů.</span><span class="sxs-lookup"><span data-stu-id="56bd4-113">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="56bd4-114">Proto pokud použijete F# sestavení z jiného .NET Framework jazyka, je nutné použít název základního typu pro zkratku typu.</span><span class="sxs-lookup"><span data-stu-id="56bd4-114">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="56bd4-115">Zkratky typů lze také použít pro měrné jednotky.</span><span class="sxs-lookup"><span data-stu-id="56bd4-115">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="56bd4-116">Další informace najdete v tématu měrné [jednotky](units-of-measure.md).</span><span class="sxs-lookup"><span data-stu-id="56bd4-116">For more information, see [Units of Measure](units-of-measure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="56bd4-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56bd4-117">See also</span></span>

- [<span data-ttu-id="56bd4-118">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="56bd4-118">F# Language Reference</span></span>](index.md)
