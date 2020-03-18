---
title: <value> - Průvodce programováním jazyka C#
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 120805346672738e614743ab8c98388b8dbac0f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793353"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="d6e9c-102">\<> hodnoty (průvodce programováním Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d6e9c-102">\<value> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="d6e9c-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6e9c-103">Syntax</span></span>

```xml
<value>property-description</value>
```

## <a name="parameters"></a><span data-ttu-id="d6e9c-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6e9c-104">Parameters</span></span>

- `property-description`

  <span data-ttu-id="d6e9c-105">Popis vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d6e9c-105">A description for the property.</span></span>

## <a name="remarks"></a><span data-ttu-id="d6e9c-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6e9c-106">Remarks</span></span>

<span data-ttu-id="d6e9c-107">Značka \<> hodnoty umožňuje popsat hodnotu, kterou představuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d6e9c-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="d6e9c-108">Všimněte si, že když přidáte vlastnost pomocí průvodce kódem ve vývojovém prostředí Sady Visual Studio .NET, přidá [ \<souhrnnou značku>](./summary.md) pro novou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d6e9c-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="d6e9c-109">Potom byste měli ručně \<přidat hodnotu> značku k popisu hodnoty, která představuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d6e9c-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>

<span data-ttu-id="d6e9c-110">Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.</span><span class="sxs-lookup"><span data-stu-id="d6e9c-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="d6e9c-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6e9c-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a><span data-ttu-id="d6e9c-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6e9c-112">See also</span></span>

- [<span data-ttu-id="d6e9c-113">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="d6e9c-113">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="d6e9c-114">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="d6e9c-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
