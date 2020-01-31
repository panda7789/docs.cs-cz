---
title: <param> – C# Průvodce programováním
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: d16070a82531519dd276b2ea999623017769d716
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789763"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="8b68f-102">> param \<C# (Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="8b68f-102">\<param> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="8b68f-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b68f-103">Syntax</span></span>

```xml
<param name="name">description</param>
```

## <a name="parameters"></a><span data-ttu-id="8b68f-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b68f-104">Parameters</span></span>

- `name`

  <span data-ttu-id="8b68f-105">Název parametru metody.</span><span class="sxs-lookup"><span data-stu-id="8b68f-105">The name of a method parameter.</span></span> <span data-ttu-id="8b68f-106">Název uzavřete do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="8b68f-106">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="8b68f-107">Popis parametru</span><span class="sxs-lookup"><span data-stu-id="8b68f-107">A description for the parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="8b68f-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b68f-108">Remarks</span></span>

<span data-ttu-id="8b68f-109">Značka > param \<by měla být použita v komentáři pro deklaraci metody pro popis jednoho z parametrů pro metodu.</span><span class="sxs-lookup"><span data-stu-id="8b68f-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="8b68f-110">Chcete-li dokumentovat více parametrů, použijte více značek > param \<.</span><span class="sxs-lookup"><span data-stu-id="8b68f-110">To document multiple parameters, use multiple \<param> tags.</span></span>

<span data-ttu-id="8b68f-111">Text značky > param \<se zobrazí v IntelliSense, v Prohlížeč objektů a v webové sestavě komentáře kódu.</span><span class="sxs-lookup"><span data-stu-id="8b68f-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>

<span data-ttu-id="8b68f-112">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="8b68f-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="8b68f-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="8b68f-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a><span data-ttu-id="8b68f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b68f-114">See also</span></span>

- [<span data-ttu-id="8b68f-115">C#Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="8b68f-115">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="8b68f-116">Doporučené značky pro dokumentační komentáře</span><span class="sxs-lookup"><span data-stu-id="8b68f-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
