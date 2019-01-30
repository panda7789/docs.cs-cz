---
title: Doporučené značky pro dokumentační komentáře - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: a6d07b6c288ebbe24c9cf5c531ef333946855f82
ms.sourcegitcommit: e39d93d358974b9ed4541cedf4e25c0101015c3c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2019
ms.locfileid: "55204714"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="a3a79-102">Doporučené značky pro dokumentační komentáře (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="a3a79-102">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="a3a79-103">Kompilátor jazyka C# zpracuje komentáře dokumentace ve vašem kódu a je ve formátu XML do souboru, jehož název zadáte **/doc** možnost příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a3a79-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="a3a79-104">Chcete-li vytvořit finální dokumentaci na základě souboru generovaného kompilátorem, můžete vytvořit vlastní nástroj nebo použít nástroj, jako [DocFX](https://dotnet.github.io/docfx/) nebo [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="a3a79-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="a3a79-105">Značky jsou zpracovány konstrukcí jako jsou typy a členy typu.</span><span class="sxs-lookup"><span data-stu-id="a3a79-105">Tags are processed on code constructs such as types and type members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3a79-106">Dokumentační komentáře nelze použít pro obor názvů.</span><span class="sxs-lookup"><span data-stu-id="a3a79-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="a3a79-107">Kompilátor bude zpracovávat všechny značky, který je platný kód XML.</span><span class="sxs-lookup"><span data-stu-id="a3a79-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="a3a79-108">Následující značky poskytují funkce obecně používaných v dokumentaci pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="a3a79-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="a3a79-109">Značky</span><span class="sxs-lookup"><span data-stu-id="a3a79-109">Tags</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="a3a79-110">\<c></span><span class="sxs-lookup"><span data-stu-id="a3a79-110">\<c></span></span>](../../../csharp/programming-guide/xmldoc/code-inline.md)|[<span data-ttu-id="a3a79-111">\<para></span><span class="sxs-lookup"><span data-stu-id="a3a79-111">\<para></span></span>](../../../csharp/programming-guide/xmldoc/para.md)|<span data-ttu-id="a3a79-112">[\<see>](../../../csharp/programming-guide/xmldoc/see.md)\*</span><span class="sxs-lookup"><span data-stu-id="a3a79-112">[\<see>](../../../csharp/programming-guide/xmldoc/see.md)\*</span></span>|  
|[<span data-ttu-id="a3a79-113">\<code></span><span class="sxs-lookup"><span data-stu-id="a3a79-113">\<code></span></span>](../../../csharp/programming-guide/xmldoc/code.md)|<span data-ttu-id="a3a79-114">[\<Param >](../../../csharp/programming-guide/xmldoc/param.md)\*</span><span class="sxs-lookup"><span data-stu-id="a3a79-114">[\<param>](../../../csharp/programming-guide/xmldoc/param.md)\*</span></span>|<span data-ttu-id="a3a79-115">[\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="a3a79-115">[\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md)\*</span></span>|  
|[<span data-ttu-id="a3a79-116">\<example></span><span class="sxs-lookup"><span data-stu-id="a3a79-116">\<example></span></span>](../../../csharp/programming-guide/xmldoc/example.md)|[<span data-ttu-id="a3a79-117">\<paramref></span><span class="sxs-lookup"><span data-stu-id="a3a79-117">\<paramref></span></span>](../../../csharp/programming-guide/xmldoc/paramref.md)|[<span data-ttu-id="a3a79-118">\<summary></span><span class="sxs-lookup"><span data-stu-id="a3a79-118">\<summary></span></span>](../../../csharp/programming-guide/xmldoc/summary.md)|  
|<span data-ttu-id="a3a79-119">[\<exception>](../../../csharp/programming-guide/xmldoc/exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="a3a79-119">[\<exception>](../../../csharp/programming-guide/xmldoc/exception.md)\*</span></span>|<span data-ttu-id="a3a79-120">[\<permission>](../../../csharp/programming-guide/xmldoc/permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="a3a79-120">[\<permission>](../../../csharp/programming-guide/xmldoc/permission.md)\*</span></span>|<span data-ttu-id="a3a79-121">[\<typeparam >](../../../csharp/programming-guide/xmldoc/typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="a3a79-121">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)\*</span></span>|  
|<span data-ttu-id="a3a79-122">[\<include>](../../../csharp/programming-guide/xmldoc/include.md)\*</span><span class="sxs-lookup"><span data-stu-id="a3a79-122">[\<include>](../../../csharp/programming-guide/xmldoc/include.md)\*</span></span>|[<span data-ttu-id="a3a79-123">\<remarks></span><span class="sxs-lookup"><span data-stu-id="a3a79-123">\<remarks></span></span>](../../../csharp/programming-guide/xmldoc/remarks.md)|[<span data-ttu-id="a3a79-124">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="a3a79-124">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)|  
|[<span data-ttu-id="a3a79-125">\<list></span><span class="sxs-lookup"><span data-stu-id="a3a79-125">\<list></span></span>](../../../csharp/programming-guide/xmldoc/list.md)|[<span data-ttu-id="a3a79-126">\<returns></span><span class="sxs-lookup"><span data-stu-id="a3a79-126">\<returns></span></span>](../../../csharp/programming-guide/xmldoc/returns.md)|[<span data-ttu-id="a3a79-127">\<value></span><span class="sxs-lookup"><span data-stu-id="a3a79-127">\<value></span></span>](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 <span data-ttu-id="a3a79-128">(\* označuje, že kompilátor ověří syntaxi.)</span><span class="sxs-lookup"><span data-stu-id="a3a79-128">(\* denotes that the compiler verifies syntax.)</span></span>  
  
 <span data-ttu-id="a3a79-129">Pokud chcete ostré závorky se zobrazí v textu Dokumentační komentář, použijte `<` a `>`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a3a79-129">If you want angle brackets to appear in the text of a documentation comment, use `<` and `>`, as shown in the following example.</span></span>  
  
```csharp  
/// <summary cref="C < T >">  
/// </summary>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a3a79-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3a79-130">See also</span></span>

- [<span data-ttu-id="a3a79-131">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a3a79-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="a3a79-132">/ DOC (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="a3a79-132">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="a3a79-133">Dokumentační komentáře XML</span><span class="sxs-lookup"><span data-stu-id="a3a79-133">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
