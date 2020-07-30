---
title: <value> – Průvodce programováním v C#
description: Další informace o XML <value> Inteligentní. Tato značka umožňuje popsat hodnotu, kterou vlastnost představuje.
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: d8294b477d7067653c71d1ec2047a85a0bfe6d02
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380771"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="2a216-105">\<value>(Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="2a216-105">\<value> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="2a216-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a216-106">Syntax</span></span>

```xml
<value>property-description</value>
```

## <a name="parameters"></a><span data-ttu-id="2a216-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="2a216-107">Parameters</span></span>

- `property-description`

  <span data-ttu-id="2a216-108">Popis vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2a216-108">A description for the property.</span></span>

## <a name="remarks"></a><span data-ttu-id="2a216-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2a216-109">Remarks</span></span>

<span data-ttu-id="2a216-110">`<value>`Značka umožňuje popsat hodnotu, kterou vlastnost představuje.</span><span class="sxs-lookup"><span data-stu-id="2a216-110">The `<value>` tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="2a216-111">Když přidáte vlastnost prostřednictvím průvodce kódem ve vývojovém prostředí sady Visual Studio .NET, přidá se [\<summary>](./summary.md) značka pro novou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2a216-111">When you add a property via code wizard in the Visual Studio .NET development environment, it adds a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="2a216-112">Měli byste pak ručně přidat `<value>` značku pro popis hodnoty, kterou vlastnost představuje.</span><span class="sxs-lookup"><span data-stu-id="2a216-112">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>

<span data-ttu-id="2a216-113">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="2a216-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="2a216-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="2a216-114">Example</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a><span data-ttu-id="2a216-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2a216-115">See also</span></span>

- [<span data-ttu-id="2a216-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="2a216-116">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="2a216-117">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="2a216-117">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
