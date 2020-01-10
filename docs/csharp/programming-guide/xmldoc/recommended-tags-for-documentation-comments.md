---
title: Doporučené značky pro dokumentační komentáře – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: 15a183d72a7d3e47f99227cea2cf870ad2f98d18
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75696529"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="ab1c5-102">Doporučené značky pro dokumentační komentáře (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="ab1c5-102">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="ab1c5-103">C# Kompilátor zpracovává dokumentační komentáře ve vašem kódu a formátuje je jako XML v souboru, jehož název zadáte v parametru příkazového řádku **/doc** .</span><span class="sxs-lookup"><span data-stu-id="ab1c5-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="ab1c5-104">Chcete-li vytvořit konečnou dokumentaci založenou na souboru generovaném kompilátorem, můžete vytvořit vlastní nástroj nebo použít nástroj, jako je [DocFX](https://dotnet.github.io/docfx/) nebo [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="ab1c5-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="ab1c5-105">Značky jsou zpracovávány na konstrukcích kódu, jako jsou typy a členy typu.</span><span class="sxs-lookup"><span data-stu-id="ab1c5-105">Tags are processed on code constructs such as types and type members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab1c5-106">Komentáře k dokumentaci nelze použít pro obor názvů.</span><span class="sxs-lookup"><span data-stu-id="ab1c5-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="ab1c5-107">Kompilátor zpracuje všechny značky, které jsou platné XML.</span><span class="sxs-lookup"><span data-stu-id="ab1c5-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="ab1c5-108">Následující značky poskytují všeobecně používané funkce v dokumentaci uživatele.</span><span class="sxs-lookup"><span data-stu-id="ab1c5-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="ab1c5-109">Značky</span><span class="sxs-lookup"><span data-stu-id="ab1c5-109">Tags</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="ab1c5-110">\<c></span><span class="sxs-lookup"><span data-stu-id="ab1c5-110">\<c></span></span>](./code-inline.md)|[<span data-ttu-id="ab1c5-111">\<para></span><span class="sxs-lookup"><span data-stu-id="ab1c5-111">\<para></span></span>](./para.md)|<span data-ttu-id="ab1c5-112">[\<see>](./see.md)\*</span><span class="sxs-lookup"><span data-stu-id="ab1c5-112">[\<see>](./see.md)\*</span></span>|  
|[<span data-ttu-id="ab1c5-113">kód \<</span><span class="sxs-lookup"><span data-stu-id="ab1c5-113">\<code></span></span>](./code.md)|<span data-ttu-id="ab1c5-114">[\<param](./param.md)\*</span><span class="sxs-lookup"><span data-stu-id="ab1c5-114">[\<param>](./param.md)\*</span></span>|<span data-ttu-id="ab1c5-115">[\<seealso >](./seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="ab1c5-115">[\<seealso>](./seealso.md)\*</span></span>|  
|[<span data-ttu-id="ab1c5-116">\<příklad ></span><span class="sxs-lookup"><span data-stu-id="ab1c5-116">\<example></span></span>](./example.md)|[<span data-ttu-id="ab1c5-117">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="ab1c5-117">\<paramref></span></span>](./paramref.md)|[<span data-ttu-id="ab1c5-118">\<summary></span><span class="sxs-lookup"><span data-stu-id="ab1c5-118">\<summary></span></span>](./summary.md)|  
|<span data-ttu-id="ab1c5-119">[\<exception>](./exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="ab1c5-119">[\<exception>](./exception.md)\*</span></span>|<span data-ttu-id="ab1c5-120">[> oprávnění\<](./permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="ab1c5-120">[\<permission>](./permission.md)\*</span></span>|<span data-ttu-id="ab1c5-121">[\<typeparam >](./typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="ab1c5-121">[\<typeparam>](./typeparam.md)\*</span></span>|  
|<span data-ttu-id="ab1c5-122">[\<include>](./include.md)\*</span><span class="sxs-lookup"><span data-stu-id="ab1c5-122">[\<include>](./include.md)\*</span></span>|[<span data-ttu-id="ab1c5-123">\<remarks></span><span class="sxs-lookup"><span data-stu-id="ab1c5-123">\<remarks></span></span>](./remarks.md)|[<span data-ttu-id="ab1c5-124">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="ab1c5-124">\<typeparamref></span></span>](./typeparamref.md)|  
|[<span data-ttu-id="ab1c5-125">\<list></span><span class="sxs-lookup"><span data-stu-id="ab1c5-125">\<list></span></span>](./list.md)|[<span data-ttu-id="ab1c5-126">\<returns></span><span class="sxs-lookup"><span data-stu-id="ab1c5-126">\<returns></span></span>](./returns.md)|[<span data-ttu-id="ab1c5-127">\<value></span><span class="sxs-lookup"><span data-stu-id="ab1c5-127">\<value></span></span>](./value.md)|  
  
 <span data-ttu-id="ab1c5-128">(\* označuje, že kompilátor ověřuje syntaxi.)</span><span class="sxs-lookup"><span data-stu-id="ab1c5-128">(\* denotes that the compiler verifies syntax.)</span></span>  
  
 <span data-ttu-id="ab1c5-129">Pokud chcete, aby se v textu komentáře k dokumentaci zobrazovaly lomené závorky, použijte kódování HTML `<` a `>`, které `&lt;` a `&gt;`.</span><span class="sxs-lookup"><span data-stu-id="ab1c5-129">If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively.</span></span> <span data-ttu-id="ab1c5-130">Toto kódování je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ab1c5-130">This encoding is shown in the following example:</span></span>
  
```csharp  
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```
  
## <a name="see-also"></a><span data-ttu-id="ab1c5-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab1c5-131">See also</span></span>

- [<span data-ttu-id="ab1c5-132">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ab1c5-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ab1c5-133">-doc (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="ab1c5-133">-doc (C# Compiler Options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="ab1c5-134">Dokumentační komentáře XML</span><span class="sxs-lookup"><span data-stu-id="ab1c5-134">XML Documentation Comments</span></span>](./index.md)
