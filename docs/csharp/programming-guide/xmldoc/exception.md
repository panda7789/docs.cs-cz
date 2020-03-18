---
title: <exception>- Průvodce programováním jazyka C#
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 14318ac0b0cdf781d0488eecaf934879017d91f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789807"
---
# <a name="exception-c-programming-guide"></a><span data-ttu-id="f5c6f-102">\<výjimka> (průvodce programováním Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="f5c6f-102">\<exception> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="f5c6f-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5c6f-103">Syntax</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="parameters"></a><span data-ttu-id="f5c6f-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5c6f-104">Parameters</span></span>

- <span data-ttu-id="f5c6f-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="f5c6f-105">cref = " `member`"</span></span>

  <span data-ttu-id="f5c6f-106">Odkaz na výjimku, která je k dispozici z aktuálního prostředí kompilace.</span><span class="sxs-lookup"><span data-stu-id="f5c6f-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="f5c6f-107">Kompilátor zkontroluje, zda daná `member` výjimka existuje, a překládá se do názvu kanonického prvku ve výstupním XML.</span><span class="sxs-lookup"><span data-stu-id="f5c6f-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="f5c6f-108">`member`musí být uvedeny v uvozovkách (" ").</span><span class="sxs-lookup"><span data-stu-id="f5c6f-108">`member` must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="f5c6f-109">Další informace o formátování `member` pro odkaz na obecný typ naleznete [v tématu Zpracování souboru XML](processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="f5c6f-109">For more information on how to format `member` to reference a generic type, see [Processing the XML File](processing-the-xml-file.md).</span></span>

- `description`

  <span data-ttu-id="f5c6f-110">Popis výjimky.</span><span class="sxs-lookup"><span data-stu-id="f5c6f-110">A description of the exception.</span></span>

## <a name="remarks"></a><span data-ttu-id="f5c6f-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f5c6f-111">Remarks</span></span>

<span data-ttu-id="f5c6f-112">Značka \<> výjimky umožňuje určit, které výjimky mohou být vyvolány.</span><span class="sxs-lookup"><span data-stu-id="f5c6f-112">The \<exception> tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="f5c6f-113">Tuto značku lze použít pro definice metod, vlastností, událostí a indexerů.</span><span class="sxs-lookup"><span data-stu-id="f5c6f-113">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>

<span data-ttu-id="f5c6f-114">Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.</span><span class="sxs-lookup"><span data-stu-id="f5c6f-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="f5c6f-115">Další informace o zpracování výjimek naleznete v [tématu Výjimky a zpracování výjimek](../exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="f5c6f-115">For more information about exception handling, see [Exceptions and Exception Handling](../exceptions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="f5c6f-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5c6f-116">Example</span></span>

[!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]

## <a name="see-also"></a><span data-ttu-id="f5c6f-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5c6f-117">See also</span></span>

- [<span data-ttu-id="f5c6f-118">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="f5c6f-118">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="f5c6f-119">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="f5c6f-119">Recommended tags for documentation comments</span></span>](recommended-tags-for-documentation-comments.md)
