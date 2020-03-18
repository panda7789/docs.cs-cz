---
title: <seealso> - Průvodce programováním jazyka C#
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
ms.openlocfilehash: e24d5910ab21f01aebb5a32ce7646cf56886a81a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093458"
---
# <a name="seealso-c-programming-guide"></a><span data-ttu-id="97f4b-102">\<seealso> (Průvodce programováním Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="97f4b-102">\<seealso> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="97f4b-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97f4b-103">Syntax</span></span>

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="97f4b-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="97f4b-104">Parameters</span></span>

- <span data-ttu-id="97f4b-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="97f4b-105">cref = " `member`"</span></span>

  <span data-ttu-id="97f4b-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="97f4b-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="97f4b-107">Kompilátor kontroluje, zda daný prvek kódu existuje a zda předává `member` do názvu prvku ve výstupním souboru XML.`member`</span><span class="sxs-lookup"><span data-stu-id="97f4b-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="97f4b-108">musí být uvedeny v uvozovkách (" ").</span><span class="sxs-lookup"><span data-stu-id="97f4b-108">must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="97f4b-109">Informace o tom, jak vytvořit odkaz na obecný typ, naleznete v [atributu cref](./cref-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="97f4b-109">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="97f4b-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="97f4b-110">Remarks</span></span>

<span data-ttu-id="97f4b-111">Značka \<seealso> umožňuje určit text, který se může chtít zobrazit v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="97f4b-111">The \<seealso> tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="97f4b-112">Pomocí [ \<>můžete](./see.md) zadat odkaz z textu.</span><span class="sxs-lookup"><span data-stu-id="97f4b-112">Use [\<see>](./see.md) to specify a link from within text.</span></span>

<span data-ttu-id="97f4b-113">Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.</span><span class="sxs-lookup"><span data-stu-id="97f4b-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="97f4b-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="97f4b-114">Example</span></span>

<span data-ttu-id="97f4b-115">Viz [ \<souhrnné>](./summary.md) příklad \<použití viz také>.</span><span class="sxs-lookup"><span data-stu-id="97f4b-115">See [\<summary>](./summary.md) for an example of using \<seealso>.</span></span>

## <a name="see-also"></a><span data-ttu-id="97f4b-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="97f4b-116">See also</span></span>

- [<span data-ttu-id="97f4b-117">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="97f4b-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="97f4b-118">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="97f4b-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
