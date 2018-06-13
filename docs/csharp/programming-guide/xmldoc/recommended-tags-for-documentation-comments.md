---
title: Doporučené značky pro dokumentační komentáře (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: 54047746db672efbf626eb2d3fc301b341cc49f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338475"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="b2266-102">Doporučené značky pro dokumentační komentáře (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="b2266-102">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="b2266-103">Kompilátor jazyka C# zpracovává dokumentační komentáře v kódu a je ve formátu XML v souboru s názvem zadáte v **/doc** možnost příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="b2266-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="b2266-104">K vytvoření konečné dokumentaci založenou na soubor generované kompilátorem, můžete vytvořit vlastní nástroj nebo pomocí nástroje, jako například [aplikaci Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="b2266-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="b2266-105">Značky jsou zpracovávány na kód konstruktory, jako jsou typy a členy typu.</span><span class="sxs-lookup"><span data-stu-id="b2266-105">Tags are processed on code constructs such as types and type members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2266-106">Dokumentační komentáře nelze použít pro obor názvů.</span><span class="sxs-lookup"><span data-stu-id="b2266-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="b2266-107">Kompilátor zpracuje všechny značky, který je platný kód XML.</span><span class="sxs-lookup"><span data-stu-id="b2266-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="b2266-108">Následující značky poskytují funkce obvykle používané v dokumentaci pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="b2266-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="b2266-109">Značky</span><span class="sxs-lookup"><span data-stu-id="b2266-109">Tags</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="b2266-110">\<c ></span><span class="sxs-lookup"><span data-stu-id="b2266-110">\<c></span></span>](../../../csharp/programming-guide/xmldoc/code-inline.md)|[<span data-ttu-id="b2266-111">\<para ></span><span class="sxs-lookup"><span data-stu-id="b2266-111">\<para></span></span>](../../../csharp/programming-guide/xmldoc/para.md)|<span data-ttu-id="b2266-112">[\<v tématu >](../../../csharp/programming-guide/xmldoc/see.md)\*</span><span class="sxs-lookup"><span data-stu-id="b2266-112">[\<see>](../../../csharp/programming-guide/xmldoc/see.md)\*</span></span>|  
|[<span data-ttu-id="b2266-113">\<kód ></span><span class="sxs-lookup"><span data-stu-id="b2266-113">\<code></span></span>](../../../csharp/programming-guide/xmldoc/code.md)|<span data-ttu-id="b2266-114">[\<Param >](../../../csharp/programming-guide/xmldoc/param.md)\*</span><span class="sxs-lookup"><span data-stu-id="b2266-114">[\<param>](../../../csharp/programming-guide/xmldoc/param.md)\*</span></span>|<span data-ttu-id="b2266-115">[\<Viz také >](../../../csharp/programming-guide/xmldoc/seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="b2266-115">[\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md)\*</span></span>|  
|[<span data-ttu-id="b2266-116">\<Příklad ></span><span class="sxs-lookup"><span data-stu-id="b2266-116">\<example></span></span>](../../../csharp/programming-guide/xmldoc/example.md)|[<span data-ttu-id="b2266-117">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="b2266-117">\<paramref></span></span>](../../../csharp/programming-guide/xmldoc/paramref.md)|[<span data-ttu-id="b2266-118">\<Souhrn ></span><span class="sxs-lookup"><span data-stu-id="b2266-118">\<summary></span></span>](../../../csharp/programming-guide/xmldoc/summary.md)|  
|<span data-ttu-id="b2266-119">[\<Výjimka >](../../../csharp/programming-guide/xmldoc/exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="b2266-119">[\<exception>](../../../csharp/programming-guide/xmldoc/exception.md)\*</span></span>|<span data-ttu-id="b2266-120">[\<oprávnění >](../../../csharp/programming-guide/xmldoc/permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="b2266-120">[\<permission>](../../../csharp/programming-guide/xmldoc/permission.md)\*</span></span>|<span data-ttu-id="b2266-121">[\<typeparam >](../../../csharp/programming-guide/xmldoc/typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="b2266-121">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)\*</span></span>|  
|<span data-ttu-id="b2266-122">[\<Zahrnout >](../../../csharp/programming-guide/xmldoc/include.md)\*</span><span class="sxs-lookup"><span data-stu-id="b2266-122">[\<include>](../../../csharp/programming-guide/xmldoc/include.md)\*</span></span>|[<span data-ttu-id="b2266-123">\<Poznámky ></span><span class="sxs-lookup"><span data-stu-id="b2266-123">\<remarks></span></span>](../../../csharp/programming-guide/xmldoc/remarks.md)|[<span data-ttu-id="b2266-124">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="b2266-124">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)|  
|[<span data-ttu-id="b2266-125">\<Seznam ></span><span class="sxs-lookup"><span data-stu-id="b2266-125">\<list></span></span>](../../../csharp/programming-guide/xmldoc/list.md)|[<span data-ttu-id="b2266-126">\<Vrátí ></span><span class="sxs-lookup"><span data-stu-id="b2266-126">\<returns></span></span>](../../../csharp/programming-guide/xmldoc/returns.md)|[<span data-ttu-id="b2266-127">\<Hodnota ></span><span class="sxs-lookup"><span data-stu-id="b2266-127">\<value></span></span>](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 <span data-ttu-id="b2266-128">(\* označuje, že kompilátor ověří syntaxi.)</span><span class="sxs-lookup"><span data-stu-id="b2266-128">(\* denotes that the compiler verifies syntax.)</span></span>  
  
 <span data-ttu-id="b2266-129">Pokud chcete lomené závorky, než se objeví v text komentáře dokumentace, použijte `<` a `>`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b2266-129">If you want angle brackets to appear in the text of a documentation comment, use `<` and `>`, as shown in the following example.</span></span>  
  
```xml  
/// <summary cref="C < T >">  
/// </summary>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b2266-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2266-130">See Also</span></span>  
 [<span data-ttu-id="b2266-131">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b2266-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b2266-132">/ DOC (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="b2266-132">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [<span data-ttu-id="b2266-133">Dokumentační komentáře XML</span><span class="sxs-lookup"><span data-stu-id="b2266-133">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
