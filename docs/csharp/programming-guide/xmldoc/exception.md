---
title: <exception>– Průvodce programováním v C#
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: fb193c586456497ee60aad941d56241ad7c6b63a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287379"
---
# <a name="exception-c-programming-guide"></a><span data-ttu-id="4bf27-102">\<exception>(Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="4bf27-102">\<exception> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="4bf27-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4bf27-103">Syntax</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="parameters"></a><span data-ttu-id="4bf27-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="4bf27-104">Parameters</span></span>

- <span data-ttu-id="4bf27-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="4bf27-105">cref = " `member`"</span></span>

  <span data-ttu-id="4bf27-106">Odkaz na výjimku, která je k dispozici z aktuálního prostředí kompilace.</span><span class="sxs-lookup"><span data-stu-id="4bf27-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="4bf27-107">Kompilátor kontroluje, zda daná výjimka existuje, a překládá se na `member` kanonický název elementu ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="4bf27-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="4bf27-108">`member`v uvozovkách ("") se musí vyskytovat.</span><span class="sxs-lookup"><span data-stu-id="4bf27-108">`member` must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="4bf27-109">Další informace o tom, jak formátovat `member` pro odkazování na obecný typ, naleznete v tématu [zpracování souboru XML](processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="4bf27-109">For more information on how to format `member` to reference a generic type, see [Processing the XML File](processing-the-xml-file.md).</span></span>

- `description`

  <span data-ttu-id="4bf27-110">Popis výjimky</span><span class="sxs-lookup"><span data-stu-id="4bf27-110">A description of the exception.</span></span>

## <a name="remarks"></a><span data-ttu-id="4bf27-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4bf27-111">Remarks</span></span>

<span data-ttu-id="4bf27-112">`<exception>`Značka umožňuje určit, které výjimky mohou být vyvolány.</span><span class="sxs-lookup"><span data-stu-id="4bf27-112">The `<exception>` tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="4bf27-113">Tato značka se dá použít na definice pro metody, vlastnosti, události a indexery.</span><span class="sxs-lookup"><span data-stu-id="4bf27-113">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>

<span data-ttu-id="4bf27-114">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="4bf27-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="4bf27-115">Další informace o zpracování výjimek naleznete v tématu [výjimky a zpracování výjimek](../exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="4bf27-115">For more information about exception handling, see [Exceptions and Exception Handling](../exceptions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="4bf27-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="4bf27-116">Example</span></span>

[!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]

## <a name="see-also"></a><span data-ttu-id="4bf27-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="4bf27-117">See also</span></span>

- [<span data-ttu-id="4bf27-118">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="4bf27-118">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="4bf27-119">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="4bf27-119">Recommended tags for documentation comments</span></span>](recommended-tags-for-documentation-comments.md)
