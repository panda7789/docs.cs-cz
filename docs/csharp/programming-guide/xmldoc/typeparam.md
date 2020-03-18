---
title: <typeparam> - Průvodce programováním jazyka C#
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 867ecacf58f95533395ded203a8f17bc92558ccf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793369"
---
# <a name="typeparam-c-programming-guide"></a><span data-ttu-id="a3c19-102">\<typeparam> (průvodce programováním C#)</span><span class="sxs-lookup"><span data-stu-id="a3c19-102">\<typeparam> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="a3c19-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3c19-103">Syntax</span></span>

```xml
<typeparam name="name">description</typeparam>
```

## <a name="parameters"></a><span data-ttu-id="a3c19-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="a3c19-104">Parameters</span></span>

- `name`

  <span data-ttu-id="a3c19-105">Název parametru typu.</span><span class="sxs-lookup"><span data-stu-id="a3c19-105">The name of the type parameter.</span></span> <span data-ttu-id="a3c19-106">Název uzavřete do uvozovek (" ").</span><span class="sxs-lookup"><span data-stu-id="a3c19-106">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="a3c19-107">Popis parametru typu.</span><span class="sxs-lookup"><span data-stu-id="a3c19-107">A description for the type parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="a3c19-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a3c19-108">Remarks</span></span>

<span data-ttu-id="a3c19-109">Značka `<typeparam>` by měla být použita v komentáři pro obecný typ nebo deklaraci metody k popisu parametru typu.</span><span class="sxs-lookup"><span data-stu-id="a3c19-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="a3c19-110">Přidejte značku pro každý parametr typu obecného typu nebo metody.</span><span class="sxs-lookup"><span data-stu-id="a3c19-110">Add a tag for each type parameter of the generic type or method.</span></span>

<span data-ttu-id="a3c19-111">Další informace naleznete [v tématu Generics](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="a3c19-111">For more information, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="a3c19-112">Text značky `<typeparam>` se zobrazí v intelliSense, webové zprávě s komentářem kódu [prohlížeče objektů.](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser)</span><span class="sxs-lookup"><span data-stu-id="a3c19-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) code comment web report.</span></span>

<span data-ttu-id="a3c19-113">Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.</span><span class="sxs-lookup"><span data-stu-id="a3c19-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="a3c19-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="a3c19-114">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="a3c19-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="a3c19-115">See also</span></span>

- [<span data-ttu-id="a3c19-116">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="a3c19-116">C# reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="a3c19-117">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="a3c19-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="a3c19-118">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="a3c19-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
