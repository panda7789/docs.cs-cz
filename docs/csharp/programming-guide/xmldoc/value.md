---
title: <value> – C# Průvodce programováním
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 120805346672738e614743ab8c98388b8dbac0f7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793353"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="d56e2-102">> hodnota \<(C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="d56e2-102">\<value> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="d56e2-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d56e2-103">Syntax</span></span>

```xml
<value>property-description</value>
```

## <a name="parameters"></a><span data-ttu-id="d56e2-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="d56e2-104">Parameters</span></span>

- `property-description`

  <span data-ttu-id="d56e2-105">Popis vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d56e2-105">A description for the property.</span></span>

## <a name="remarks"></a><span data-ttu-id="d56e2-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d56e2-106">Remarks</span></span>

<span data-ttu-id="d56e2-107">Hodnota \<> tag umožňuje popsat hodnotu, kterou vlastnost představuje.</span><span class="sxs-lookup"><span data-stu-id="d56e2-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="d56e2-108">Všimněte si, že při přidání vlastnosti přes průvodce kódem ve vývojovém prostředí sady Visual Studio .NET bude přidána značka [\<summary >](./summary.md) pro novou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d56e2-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="d56e2-109">Měli byste pak ručně přidat \<Value > tag k popisu hodnoty, kterou vlastnost představuje.</span><span class="sxs-lookup"><span data-stu-id="d56e2-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>

<span data-ttu-id="d56e2-110">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="d56e2-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="d56e2-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="d56e2-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a><span data-ttu-id="d56e2-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d56e2-112">See also</span></span>

- [<span data-ttu-id="d56e2-113">C#Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="d56e2-113">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="d56e2-114">Doporučené značky pro dokumentační komentáře</span><span class="sxs-lookup"><span data-stu-id="d56e2-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
