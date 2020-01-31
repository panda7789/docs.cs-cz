---
title: Průvodce C# programováním <typeparamref>
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 266eadad322fd3c4167c7a911cb57ef1e1333012
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789662"
---
# <a name="typeparamref-c-programming-guide"></a><span data-ttu-id="85205-102">\<typeparamref > (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="85205-102">\<typeparamref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="85205-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85205-103">Syntax</span></span>

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="85205-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="85205-104">Parameters</span></span>

- `name`

  <span data-ttu-id="85205-105">Název parametru typu.</span><span class="sxs-lookup"><span data-stu-id="85205-105">The name of the type parameter.</span></span> <span data-ttu-id="85205-106">Název uzavřete do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="85205-106">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="85205-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="85205-107">Remarks</span></span>

<span data-ttu-id="85205-108">Další informace o parametrech typu v obecných typech a metodách naleznete v tématu [generické](../generics/index.md)typy.</span><span class="sxs-lookup"><span data-stu-id="85205-108">For more information on type parameters in generic types and methods, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="85205-109">Pomocí této značky můžete uživatelům souboru dokumentace povolit formátování určitého slova nějakým způsobem, například kurzívou.</span><span class="sxs-lookup"><span data-stu-id="85205-109">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>

<span data-ttu-id="85205-110">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="85205-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="85205-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="85205-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="85205-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85205-112">See also</span></span>

- [<span data-ttu-id="85205-113">C#Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="85205-113">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="85205-114">Doporučené značky pro dokumentační komentáře</span><span class="sxs-lookup"><span data-stu-id="85205-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
