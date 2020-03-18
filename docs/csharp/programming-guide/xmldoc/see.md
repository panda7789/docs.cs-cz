---
title: <see>- Průvodce programováním jazyka C#
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: f4834f88c646b44269f8290c2ad08698c34e714a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627669"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="43655-102">\<viz> (průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="43655-102">\<see> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="43655-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43655-103">Syntax</span></span>

```xml
<see cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="43655-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="43655-104">Parameters</span></span>

- <span data-ttu-id="43655-105">cref =`member`" "</span><span class="sxs-lookup"><span data-stu-id="43655-105">cref = "`member`"</span></span>

  <span data-ttu-id="43655-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="43655-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="43655-107">Kompilátor kontroluje, zda daný prvek kódu existuje a zda předává `member` do názvu prvku ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="43655-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="43655-108">Umístěte *člen* do uvozovek (" ").</span><span class="sxs-lookup"><span data-stu-id="43655-108">Place *member* within double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="43655-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="43655-109">Remarks</span></span>

<span data-ttu-id="43655-110">Značka \<viz> umožňuje zadat odkaz z textu.</span><span class="sxs-lookup"><span data-stu-id="43655-110">The \<see> tag lets you specify a link from within text.</span></span> <span data-ttu-id="43655-111">Použijte [ \<také>see](./seealso.md) označuje, že text by měl být umístěn v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="43655-111">Use [\<seealso>](./seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="43655-112">Pomocí [atributu cref](./cref-attribute.md) vytvořte interní hypertextové odkazy na stránky dokumentace pro prvky kódu.</span><span class="sxs-lookup"><span data-stu-id="43655-112">Use the [cref Attribute](./cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span>

<span data-ttu-id="43655-113">Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.</span><span class="sxs-lookup"><span data-stu-id="43655-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="43655-114">Následující příklad ukazuje \<značku> v souhrnné části.</span><span class="sxs-lookup"><span data-stu-id="43655-114">The following example shows a \<see> tag within a summary section.</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a><span data-ttu-id="43655-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="43655-115">See also</span></span>

- [<span data-ttu-id="43655-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="43655-116">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="43655-117">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="43655-117">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
