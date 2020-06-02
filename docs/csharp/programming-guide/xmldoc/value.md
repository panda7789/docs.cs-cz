---
title: <value> – Průvodce programováním v C#
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: bd6630a8d5894fda39ad289c8dd584f6d84e5490
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287191"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="1a96b-102">\<value>(Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="1a96b-102">\<value> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="1a96b-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a96b-103">Syntax</span></span>

```xml
<value>property-description</value>
```

## <a name="parameters"></a><span data-ttu-id="1a96b-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a96b-104">Parameters</span></span>

- `property-description`

  <span data-ttu-id="1a96b-105">Popis vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1a96b-105">A description for the property.</span></span>

## <a name="remarks"></a><span data-ttu-id="1a96b-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1a96b-106">Remarks</span></span>

<span data-ttu-id="1a96b-107">`<value>`Značka umožňuje popsat hodnotu, kterou vlastnost představuje.</span><span class="sxs-lookup"><span data-stu-id="1a96b-107">The `<value>` tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="1a96b-108">Když přidáte vlastnost prostřednictvím průvodce kódem ve vývojovém prostředí sady Visual Studio .NET, přidá se [\<summary>](./summary.md) značka pro novou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1a96b-108">When you add a property via code wizard in the Visual Studio .NET development environment, it adds a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="1a96b-109">Měli byste pak ručně přidat `<value>` značku pro popis hodnoty, kterou vlastnost představuje.</span><span class="sxs-lookup"><span data-stu-id="1a96b-109">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>

<span data-ttu-id="1a96b-110">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="1a96b-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="1a96b-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="1a96b-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a><span data-ttu-id="1a96b-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="1a96b-112">See also</span></span>

- [<span data-ttu-id="1a96b-113">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="1a96b-113">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="1a96b-114">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="1a96b-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
