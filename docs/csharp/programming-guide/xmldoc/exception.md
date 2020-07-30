---
title: <exception>– Průvodce programováním v C#
description: Přečtěte si o <exception> značce XML. Tato značka vám umožní určit, které výjimky mohou být vyvolány a lze je použít na metody, vlastnosti, události a indexery.
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 22a28f3fe6de5a0db9aea0f1fd7963d4e6fcee05
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381733"
---
# <a name="exception-c-programming-guide"></a><span data-ttu-id="6ff74-104">\<exception>(Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="6ff74-104">\<exception> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="6ff74-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ff74-105">Syntax</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="parameters"></a><span data-ttu-id="6ff74-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ff74-106">Parameters</span></span>

- <span data-ttu-id="6ff74-107">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="6ff74-107">cref = " `member`"</span></span>

  <span data-ttu-id="6ff74-108">Odkaz na výjimku, která je k dispozici z aktuálního prostředí kompilace.</span><span class="sxs-lookup"><span data-stu-id="6ff74-108">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="6ff74-109">Kompilátor kontroluje, zda daná výjimka existuje, a překládá se na `member` kanonický název elementu ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="6ff74-109">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="6ff74-110">`member`v uvozovkách ("") se musí vyskytovat.</span><span class="sxs-lookup"><span data-stu-id="6ff74-110">`member` must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="6ff74-111">Další informace o tom, jak formátovat `member` pro odkazování na obecný typ, naleznete v tématu [zpracování souboru XML](processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="6ff74-111">For more information on how to format `member` to reference a generic type, see [Processing the XML File](processing-the-xml-file.md).</span></span>

- `description`

  <span data-ttu-id="6ff74-112">Popis výjimky</span><span class="sxs-lookup"><span data-stu-id="6ff74-112">A description of the exception.</span></span>

## <a name="remarks"></a><span data-ttu-id="6ff74-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6ff74-113">Remarks</span></span>

<span data-ttu-id="6ff74-114">`<exception>`Značka umožňuje určit, které výjimky mohou být vyvolány.</span><span class="sxs-lookup"><span data-stu-id="6ff74-114">The `<exception>` tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="6ff74-115">Tato značka se dá použít na definice pro metody, vlastnosti, události a indexery.</span><span class="sxs-lookup"><span data-stu-id="6ff74-115">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>

<span data-ttu-id="6ff74-116">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="6ff74-116">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="6ff74-117">Další informace o zpracování výjimek naleznete v tématu [výjimky a zpracování výjimek](../exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="6ff74-117">For more information about exception handling, see [Exceptions and Exception Handling](../exceptions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="6ff74-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ff74-118">Example</span></span>

[!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]

## <a name="see-also"></a><span data-ttu-id="6ff74-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ff74-119">See also</span></span>

- [<span data-ttu-id="6ff74-120">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="6ff74-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="6ff74-121">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="6ff74-121">Recommended tags for documentation comments</span></span>](recommended-tags-for-documentation-comments.md)
