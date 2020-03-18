---
title: Doporučené značky pro komentáře k dokumentaci – průvodce programováním jazyka C#
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: c746615d0d7a7a3058fbe2f8506a7a7c5c4a8779
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789729"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="d3540-102">Doporučené značky pro komentáře k dokumentaci (průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d3540-102">Recommended tags for documentation comments (C# programming guide)</span></span>

<span data-ttu-id="d3540-103">Kompilátor Jazyka C# zpracovává komentáře dokumentace ve vašem kódu a formátuje je jako XML v souboru, jehož název zadáte v možnosti příkazového řádku **/doc.**</span><span class="sxs-lookup"><span data-stu-id="d3540-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="d3540-104">Chcete-li vytvořit konečnou dokumentaci založenou na souboru generovaném kompilátorem, můžete vytvořit vlastní nástroj nebo použít nástroj, jako je [DocFX](https://dotnet.github.io/docfx/) nebo [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="d3540-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

<span data-ttu-id="d3540-105">Značky jsou zpracovány na konstrukce kódu, jako jsou typy a členy typu.</span><span class="sxs-lookup"><span data-stu-id="d3540-105">Tags are processed on code constructs such as types and type members.</span></span>

> [!NOTE]
> <span data-ttu-id="d3540-106">Komentáře dokumentace nelze použít v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d3540-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="d3540-107">Kompilátor zpracuje všechny značky, které jsou platné XML.</span><span class="sxs-lookup"><span data-stu-id="d3540-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="d3540-108">Následující značky poskytují obecně používané funkce v uživatelské dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="d3540-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="d3540-109">Značky</span><span class="sxs-lookup"><span data-stu-id="d3540-109">Tags</span></span>  
  
|||||  
|---|---|---|---|
|[<span data-ttu-id="d3540-110">\<c></span><span class="sxs-lookup"><span data-stu-id="d3540-110">\<c></span></span>](./code-inline.md)|[<span data-ttu-id="d3540-111">\<para></span><span class="sxs-lookup"><span data-stu-id="d3540-111">\<para></span></span>](./para.md)|<span data-ttu-id="d3540-112">[\<viz>](./see.md)\*</span><span class="sxs-lookup"><span data-stu-id="d3540-112">[\<see>](./see.md)\*</span></span>|[<span data-ttu-id="d3540-113">\<hodnota></span><span class="sxs-lookup"><span data-stu-id="d3540-113">\<value></span></span>](./value.md)  
|[<span data-ttu-id="d3540-114">\<kód></span><span class="sxs-lookup"><span data-stu-id="d3540-114">\<code></span></span>](./code.md)|<span data-ttu-id="d3540-115">[\<param>](./param.md)\*</span><span class="sxs-lookup"><span data-stu-id="d3540-115">[\<param>](./param.md)\*</span></span>|<span data-ttu-id="d3540-116">[\<seealso>](./seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="d3540-116">[\<seealso>](./seealso.md)\*</span></span>|  
|[<span data-ttu-id="d3540-117">\<příklad></span><span class="sxs-lookup"><span data-stu-id="d3540-117">\<example></span></span>](./example.md)|[<span data-ttu-id="d3540-118">\<paramref></span><span class="sxs-lookup"><span data-stu-id="d3540-118">\<paramref></span></span>](./paramref.md)|[<span data-ttu-id="d3540-119">\<souhrnný></span><span class="sxs-lookup"><span data-stu-id="d3540-119">\<summary></span></span>](./summary.md)|  
|<span data-ttu-id="d3540-120">[\<výjimka>](./exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="d3540-120">[\<exception>](./exception.md)\*</span></span>|<span data-ttu-id="d3540-121">[\<>oprávnění](./permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="d3540-121">[\<permission>](./permission.md)\*</span></span>|<span data-ttu-id="d3540-122">[\<typeparam>](./typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="d3540-122">[\<typeparam>](./typeparam.md)\*</span></span>|  
|<span data-ttu-id="d3540-123">[\<patří>](./include.md)\*</span><span class="sxs-lookup"><span data-stu-id="d3540-123">[\<include>](./include.md)\*</span></span>|[<span data-ttu-id="d3540-124">\<poznámky></span><span class="sxs-lookup"><span data-stu-id="d3540-124">\<remarks></span></span>](./remarks.md)|[<span data-ttu-id="d3540-125">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="d3540-125">\<typeparamref></span></span>](./typeparamref.md)|  
|[<span data-ttu-id="d3540-126">\<seznam></span><span class="sxs-lookup"><span data-stu-id="d3540-126">\<list></span></span>](./list.md)|[<span data-ttu-id="d3540-127">\<inheritdoc></span><span class="sxs-lookup"><span data-stu-id="d3540-127">\<inheritdoc></span></span>](./inheritdoc.md)|[<span data-ttu-id="d3540-128">\<vrátí></span><span class="sxs-lookup"><span data-stu-id="d3540-128">\<returns></span></span>](./returns.md)|
  
<span data-ttu-id="d3540-129">(\* označuje, že kompilátor ověřuje syntaxi.)</span><span class="sxs-lookup"><span data-stu-id="d3540-129">(\* denotes that the compiler verifies syntax.)</span></span>

<span data-ttu-id="d3540-130">Pokud chcete, aby se v textu komentáře k dokumentaci zobrazovaly `<` `>` úhlové `&lt;` `&gt;` závorky, použijte kódování HTML a které je a v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d3540-130">If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively.</span></span> <span data-ttu-id="d3540-131">Toto kódování je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d3540-131">This encoding is shown in the following example.</span></span>

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a><span data-ttu-id="d3540-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3540-132">See also</span></span>

- [<span data-ttu-id="d3540-133">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="d3540-133">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="d3540-134">-doc (možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d3540-134">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="d3540-135">Komentáře dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="d3540-135">XML documentation comments</span></span>](./index.md)
