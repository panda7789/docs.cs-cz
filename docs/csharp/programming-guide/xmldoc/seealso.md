---
title: <seealso> – Průvodce programováním v C#
description: Naučte se používat XML. <seealso> Inteligentní. Tato značka vám umožní určit text, který se může zobrazit v části Viz také.
ms.date: 07/20/2015
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
ms.openlocfilehash: e8618ef352a4fa7f0fd4c88733c6568b0e12e376
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380641"
---
# <a name="seealso-c-programming-guide"></a><span data-ttu-id="e4f48-105">\<seealso>(Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="e4f48-105">\<seealso> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="e4f48-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4f48-106">Syntax</span></span>

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="e4f48-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="e4f48-107">Parameters</span></span>

- <span data-ttu-id="e4f48-108">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="e4f48-108">cref = " `member`"</span></span>

  <span data-ttu-id="e4f48-109">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="e4f48-109">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="e4f48-110">Kompilátor kontroluje, zda daný prvek kódu existuje a zda předává `member` do názvu prvku ve výstupním souboru XML.`member`</span><span class="sxs-lookup"><span data-stu-id="e4f48-110">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="e4f48-111">v uvozovkách ("") se musí vyskytovat.</span><span class="sxs-lookup"><span data-stu-id="e4f48-111">must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="e4f48-112">Informace o tom, jak vytvořit odkaz cref na obecný typ, naleznete v tématu [atribut cref](./cref-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="e4f48-112">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="e4f48-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e4f48-113">Remarks</span></span>

<span data-ttu-id="e4f48-114">`<seealso>`Značka vám umožní určit text, který se může objevit v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="e4f48-114">The `<seealso>` tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="e4f48-115">Slouží [\<see>](./see.md) k zadání odkazu z textu.</span><span class="sxs-lookup"><span data-stu-id="e4f48-115">Use [\<see>](./see.md) to specify a link from within text.</span></span>

<span data-ttu-id="e4f48-116">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="e4f48-116">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="e4f48-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4f48-117">Example</span></span>

<span data-ttu-id="e4f48-118">Příklad použití naleznete v tématu [\<summary>](./summary.md) \<seealso> .</span><span class="sxs-lookup"><span data-stu-id="e4f48-118">See [\<summary>](./summary.md) for an example of using \<seealso>.</span></span>

## <a name="see-also"></a><span data-ttu-id="e4f48-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4f48-119">See also</span></span>

- [<span data-ttu-id="e4f48-120">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="e4f48-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="e4f48-121">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="e4f48-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
