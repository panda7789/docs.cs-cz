---
title: <param> – Průvodce programováním v C#
description: Další informace o XML <param> Inteligentní. Tato značka se používá v komentáři pro deklaraci metody k popisu jednoho z parametrů pro metodu.
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: a9e3b2e86528afcbe1330788e248f0143efb5c1b
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381551"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="c80d6-105">\<param>(Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="c80d6-105">\<param> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="c80d6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c80d6-106">Syntax</span></span>

```xml
<param name="name">description</param>
```

## <a name="parameters"></a><span data-ttu-id="c80d6-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="c80d6-107">Parameters</span></span>

- `name`

  <span data-ttu-id="c80d6-108">Název parametru metody.</span><span class="sxs-lookup"><span data-stu-id="c80d6-108">The name of a method parameter.</span></span> <span data-ttu-id="c80d6-109">Název uzavřete do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="c80d6-109">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="c80d6-110">Popis parametru</span><span class="sxs-lookup"><span data-stu-id="c80d6-110">A description for the parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="c80d6-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c80d6-111">Remarks</span></span>

<span data-ttu-id="c80d6-112">`<param>`Značka by měla být použita v komentáři pro deklaraci metody pro popis jednoho z parametrů pro metodu.</span><span class="sxs-lookup"><span data-stu-id="c80d6-112">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="c80d6-113">Chcete-li dokumentovat více parametrů, použijte více `<param>` značek.</span><span class="sxs-lookup"><span data-stu-id="c80d6-113">To document multiple parameters, use multiple `<param>` tags.</span></span>

<span data-ttu-id="c80d6-114">Text `<param>` značky je zobrazen v IntelliSense, prohlížeč objektů a webové sestavy komentáře kódu.</span><span class="sxs-lookup"><span data-stu-id="c80d6-114">The text for the `<param>` tag is displayed in IntelliSense, the Object Browser, and the Code Comment Web Report.</span></span>

<span data-ttu-id="c80d6-115">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="c80d6-115">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="c80d6-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="c80d6-116">Example</span></span>

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a><span data-ttu-id="c80d6-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c80d6-117">See also</span></span>

- [<span data-ttu-id="c80d6-118">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="c80d6-118">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="c80d6-119">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="c80d6-119">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
