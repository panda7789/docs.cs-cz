---
title: Doporučené značky pro dokumentační komentáře – C# Průvodce programováním
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: c746615d0d7a7a3058fbe2f8506a7a7c5c4a8779
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789729"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="2356e-102">Doporučené značky pro dokumentační komentáře (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="2356e-102">Recommended tags for documentation comments (C# programming guide)</span></span>

<span data-ttu-id="2356e-103">C# Kompilátor zpracovává dokumentační komentáře ve vašem kódu a formátuje je jako XML v souboru, jehož název zadáte v parametru příkazového řádku **/doc** .</span><span class="sxs-lookup"><span data-stu-id="2356e-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="2356e-104">Chcete-li vytvořit konečnou dokumentaci založenou na souboru generovaném kompilátorem, můžete vytvořit vlastní nástroj nebo použít nástroj, jako je [DocFX](https://dotnet.github.io/docfx/) nebo [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="2356e-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

<span data-ttu-id="2356e-105">Značky jsou zpracovávány na konstrukcích kódu, jako jsou typy a členy typu.</span><span class="sxs-lookup"><span data-stu-id="2356e-105">Tags are processed on code constructs such as types and type members.</span></span>

> [!NOTE]
> <span data-ttu-id="2356e-106">Komentáře k dokumentaci nelze použít pro obor názvů.</span><span class="sxs-lookup"><span data-stu-id="2356e-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="2356e-107">Kompilátor zpracuje všechny značky, které jsou platné XML.</span><span class="sxs-lookup"><span data-stu-id="2356e-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="2356e-108">Následující značky poskytují všeobecně používané funkce v dokumentaci uživatele.</span><span class="sxs-lookup"><span data-stu-id="2356e-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="2356e-109">Značky</span><span class="sxs-lookup"><span data-stu-id="2356e-109">Tags</span></span>  
  
|||||  
|---|---|---|---|
|[<span data-ttu-id="2356e-110">\<c></span><span class="sxs-lookup"><span data-stu-id="2356e-110">\<c></span></span>](./code-inline.md)|[<span data-ttu-id="2356e-111">\<para></span><span class="sxs-lookup"><span data-stu-id="2356e-111">\<para></span></span>](./para.md)|<span data-ttu-id="2356e-112">[\<see>](./see.md)\*</span><span class="sxs-lookup"><span data-stu-id="2356e-112">[\<see>](./see.md)\*</span></span>|[<span data-ttu-id="2356e-113">\<value></span><span class="sxs-lookup"><span data-stu-id="2356e-113">\<value></span></span>](./value.md)  
|[<span data-ttu-id="2356e-114">kód \<</span><span class="sxs-lookup"><span data-stu-id="2356e-114">\<code></span></span>](./code.md)|<span data-ttu-id="2356e-115">[\<param](./param.md)\*</span><span class="sxs-lookup"><span data-stu-id="2356e-115">[\<param>](./param.md)\*</span></span>|<span data-ttu-id="2356e-116">[\<seealso >](./seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="2356e-116">[\<seealso>](./seealso.md)\*</span></span>|  
|[<span data-ttu-id="2356e-117">\<příklad ></span><span class="sxs-lookup"><span data-stu-id="2356e-117">\<example></span></span>](./example.md)|[<span data-ttu-id="2356e-118">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="2356e-118">\<paramref></span></span>](./paramref.md)|[<span data-ttu-id="2356e-119">\<summary></span><span class="sxs-lookup"><span data-stu-id="2356e-119">\<summary></span></span>](./summary.md)|  
|<span data-ttu-id="2356e-120">[\<exception>](./exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="2356e-120">[\<exception>](./exception.md)\*</span></span>|<span data-ttu-id="2356e-121">[> oprávnění\<](./permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="2356e-121">[\<permission>](./permission.md)\*</span></span>|<span data-ttu-id="2356e-122">[\<typeparam >](./typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="2356e-122">[\<typeparam>](./typeparam.md)\*</span></span>|  
|<span data-ttu-id="2356e-123">[\<include>](./include.md)\*</span><span class="sxs-lookup"><span data-stu-id="2356e-123">[\<include>](./include.md)\*</span></span>|[<span data-ttu-id="2356e-124">\<remarks></span><span class="sxs-lookup"><span data-stu-id="2356e-124">\<remarks></span></span>](./remarks.md)|[<span data-ttu-id="2356e-125">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="2356e-125">\<typeparamref></span></span>](./typeparamref.md)|  
|[<span data-ttu-id="2356e-126">\<list></span><span class="sxs-lookup"><span data-stu-id="2356e-126">\<list></span></span>](./list.md)|[<span data-ttu-id="2356e-127">\<inheritdoc ></span><span class="sxs-lookup"><span data-stu-id="2356e-127">\<inheritdoc></span></span>](./inheritdoc.md)|[<span data-ttu-id="2356e-128">\<returns></span><span class="sxs-lookup"><span data-stu-id="2356e-128">\<returns></span></span>](./returns.md)|
  
<span data-ttu-id="2356e-129">(\* označuje, že kompilátor ověřuje syntaxi.)</span><span class="sxs-lookup"><span data-stu-id="2356e-129">(\* denotes that the compiler verifies syntax.)</span></span>

<span data-ttu-id="2356e-130">Pokud chcete, aby se v textu komentáře k dokumentaci zobrazovaly lomené závorky, použijte kódování HTML `<` a `>`, které `&lt;` a `&gt;`.</span><span class="sxs-lookup"><span data-stu-id="2356e-130">If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively.</span></span> <span data-ttu-id="2356e-131">Toto kódování je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2356e-131">This encoding is shown in the following example.</span></span>

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a><span data-ttu-id="2356e-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2356e-132">See also</span></span>

- [<span data-ttu-id="2356e-133">C#Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="2356e-133">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="2356e-134">-doc (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="2356e-134">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="2356e-135">Dokumentační komentáře XML</span><span class="sxs-lookup"><span data-stu-id="2356e-135">XML documentation comments</span></span>](./index.md)
