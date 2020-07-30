---
title: <typeparam> – Průvodce programováním v C#
description: Další informace o XML <typeparam> Inteligentní. Tato značka se používá v komentáři pro obecný typ nebo deklaraci metody pro popis parametru typu.
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 5e5333e384e8c77b500f74ab7c6038146df6e2c0
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380784"
---
# <a name="typeparam-c-programming-guide"></a><span data-ttu-id="8a745-105">\<typeparam>(Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="8a745-105">\<typeparam> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="8a745-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a745-106">Syntax</span></span>

```xml
<typeparam name="name">description</typeparam>
```

## <a name="parameters"></a><span data-ttu-id="8a745-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a745-107">Parameters</span></span>

- `name`

  <span data-ttu-id="8a745-108">Název parametru typu.</span><span class="sxs-lookup"><span data-stu-id="8a745-108">The name of the type parameter.</span></span> <span data-ttu-id="8a745-109">Název uzavřete do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="8a745-109">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="8a745-110">Popis parametru typu.</span><span class="sxs-lookup"><span data-stu-id="8a745-110">A description for the type parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="8a745-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8a745-111">Remarks</span></span>

<span data-ttu-id="8a745-112">`<typeparam>`Značka by měla být použita v komentáři pro obecný typ nebo deklaraci metody pro popis parametru typu.</span><span class="sxs-lookup"><span data-stu-id="8a745-112">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="8a745-113">Přidejte značku pro každý parametr typu obecného typu nebo metody.</span><span class="sxs-lookup"><span data-stu-id="8a745-113">Add a tag for each type parameter of the generic type or method.</span></span>

<span data-ttu-id="8a745-114">Další informace najdete v tématu [Obecné typy](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="8a745-114">For more information, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="8a745-115">Text `<typeparam>` značky bude zobrazen v IntelliSense, Webová sestava komentáře kódu [prohlížeč objektůho okna](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) .</span><span class="sxs-lookup"><span data-stu-id="8a745-115">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) code comment web report.</span></span>

<span data-ttu-id="8a745-116">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="8a745-116">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="8a745-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="8a745-117">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="8a745-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a745-118">See also</span></span>

- [<span data-ttu-id="8a745-119">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="8a745-119">C# reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="8a745-120">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="8a745-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="8a745-121">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="8a745-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
