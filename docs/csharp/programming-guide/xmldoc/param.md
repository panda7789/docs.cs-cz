---
title: <param> – Průvodce programováním v C#
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 396ed716c246091a674268020261069f36dd2be8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287321"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="c0c8d-102">\<param>(Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="c0c8d-102">\<param> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="c0c8d-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0c8d-103">Syntax</span></span>

```xml
<param name="name">description</param>
```

## <a name="parameters"></a><span data-ttu-id="c0c8d-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="c0c8d-104">Parameters</span></span>

- `name`

  <span data-ttu-id="c0c8d-105">Název parametru metody.</span><span class="sxs-lookup"><span data-stu-id="c0c8d-105">The name of a method parameter.</span></span> <span data-ttu-id="c0c8d-106">Název uzavřete do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="c0c8d-106">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="c0c8d-107">Popis parametru</span><span class="sxs-lookup"><span data-stu-id="c0c8d-107">A description for the parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="c0c8d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c0c8d-108">Remarks</span></span>

<span data-ttu-id="c0c8d-109">`<param>`Značka by měla být použita v komentáři pro deklaraci metody pro popis jednoho z parametrů pro metodu.</span><span class="sxs-lookup"><span data-stu-id="c0c8d-109">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="c0c8d-110">Chcete-li dokumentovat více parametrů, použijte více `<param>` značek.</span><span class="sxs-lookup"><span data-stu-id="c0c8d-110">To document multiple parameters, use multiple `<param>` tags.</span></span>

<span data-ttu-id="c0c8d-111">Text `<param>` značky je zobrazen v IntelliSense, prohlížeč objektů a webové sestavy komentáře kódu.</span><span class="sxs-lookup"><span data-stu-id="c0c8d-111">The text for the `<param>` tag is displayed in IntelliSense, the Object Browser, and the Code Comment Web Report.</span></span>

<span data-ttu-id="c0c8d-112">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="c0c8d-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="c0c8d-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="c0c8d-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a><span data-ttu-id="c0c8d-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0c8d-114">See also</span></span>

- [<span data-ttu-id="c0c8d-115">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="c0c8d-115">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="c0c8d-116">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="c0c8d-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
