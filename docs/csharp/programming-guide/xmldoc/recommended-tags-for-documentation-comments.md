---
title: Doporučené značky pro dokumentační komentáře - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: fb4d8d4dde38d7cbe1b0434c290dd922b2e328a3
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245584"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="6e628-102">Doporučené značky pro dokumentační komentáře (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="6e628-102">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="6e628-103">Kompilátor jazyka C# zpracuje komentáře dokumentace ve vašem kódu a je ve formátu XML do souboru, jehož název zadáte **/doc** možnost příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="6e628-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="6e628-104">Chcete-li vytvořit finální dokumentaci na základě souboru generovaného kompilátorem, můžete vytvořit vlastní nástroj nebo použít nástroj, jako [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="6e628-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="6e628-105">Značky jsou zpracovány konstrukcí jako jsou typy a členy typu.</span><span class="sxs-lookup"><span data-stu-id="6e628-105">Tags are processed on code constructs such as types and type members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e628-106">Dokumentační komentáře nelze použít pro obor názvů.</span><span class="sxs-lookup"><span data-stu-id="6e628-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="6e628-107">Kompilátor bude zpracovávat všechny značky, který je platný kód XML.</span><span class="sxs-lookup"><span data-stu-id="6e628-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="6e628-108">Následující značky poskytují funkce obecně používaných v dokumentaci pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="6e628-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="6e628-109">Značky</span><span class="sxs-lookup"><span data-stu-id="6e628-109">Tags</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="6e628-110">\<c ></span><span class="sxs-lookup"><span data-stu-id="6e628-110">\<c></span></span>](../../../csharp/programming-guide/xmldoc/code-inline.md)|[<span data-ttu-id="6e628-111">\<para ></span><span class="sxs-lookup"><span data-stu-id="6e628-111">\<para></span></span>](../../../csharp/programming-guide/xmldoc/para.md)|<span data-ttu-id="6e628-112">[\<Zobrazit >](../../../csharp/programming-guide/xmldoc/see.md)\*</span><span class="sxs-lookup"><span data-stu-id="6e628-112">[\<see>](../../../csharp/programming-guide/xmldoc/see.md)\*</span></span>|  
|[<span data-ttu-id="6e628-113">\<kód ></span><span class="sxs-lookup"><span data-stu-id="6e628-113">\<code></span></span>](../../../csharp/programming-guide/xmldoc/code.md)|<span data-ttu-id="6e628-114">[\<Param >](../../../csharp/programming-guide/xmldoc/param.md)\*</span><span class="sxs-lookup"><span data-stu-id="6e628-114">[\<param>](../../../csharp/programming-guide/xmldoc/param.md)\*</span></span>|<span data-ttu-id="6e628-115">[\<SeeAlso >](../../../csharp/programming-guide/xmldoc/seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="6e628-115">[\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md)\*</span></span>|  
|[<span data-ttu-id="6e628-116">\<Příklad ></span><span class="sxs-lookup"><span data-stu-id="6e628-116">\<example></span></span>](../../../csharp/programming-guide/xmldoc/example.md)|[<span data-ttu-id="6e628-117">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="6e628-117">\<paramref></span></span>](../../../csharp/programming-guide/xmldoc/paramref.md)|[<span data-ttu-id="6e628-118">\<Summary ></span><span class="sxs-lookup"><span data-stu-id="6e628-118">\<summary></span></span>](../../../csharp/programming-guide/xmldoc/summary.md)|  
|<span data-ttu-id="6e628-119">[\<výjimky >](../../../csharp/programming-guide/xmldoc/exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="6e628-119">[\<exception>](../../../csharp/programming-guide/xmldoc/exception.md)\*</span></span>|<span data-ttu-id="6e628-120">[\<oprávnění >](../../../csharp/programming-guide/xmldoc/permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="6e628-120">[\<permission>](../../../csharp/programming-guide/xmldoc/permission.md)\*</span></span>|<span data-ttu-id="6e628-121">[\<typeparam >](../../../csharp/programming-guide/xmldoc/typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="6e628-121">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)\*</span></span>|  
|<span data-ttu-id="6e628-122">[\<Zahrnout >](../../../csharp/programming-guide/xmldoc/include.md)\*</span><span class="sxs-lookup"><span data-stu-id="6e628-122">[\<include>](../../../csharp/programming-guide/xmldoc/include.md)\*</span></span>|[<span data-ttu-id="6e628-123">\<REMARKS ></span><span class="sxs-lookup"><span data-stu-id="6e628-123">\<remarks></span></span>](../../../csharp/programming-guide/xmldoc/remarks.md)|[<span data-ttu-id="6e628-124">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="6e628-124">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)|  
|[<span data-ttu-id="6e628-125">\<Seznam ></span><span class="sxs-lookup"><span data-stu-id="6e628-125">\<list></span></span>](../../../csharp/programming-guide/xmldoc/list.md)|[<span data-ttu-id="6e628-126">\<Vrátí ></span><span class="sxs-lookup"><span data-stu-id="6e628-126">\<returns></span></span>](../../../csharp/programming-guide/xmldoc/returns.md)|[<span data-ttu-id="6e628-127">\<Hodnota ></span><span class="sxs-lookup"><span data-stu-id="6e628-127">\<value></span></span>](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 <span data-ttu-id="6e628-128">(\* označuje, že kompilátor ověří syntaxi.)</span><span class="sxs-lookup"><span data-stu-id="6e628-128">(\* denotes that the compiler verifies syntax.)</span></span>  
  
 <span data-ttu-id="6e628-129">Pokud chcete ostré závorky se zobrazí v textu Dokumentační komentář, použijte `<` a `>`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6e628-129">If you want angle brackets to appear in the text of a documentation comment, use `<` and `>`, as shown in the following example.</span></span>  
  
```xml  
/// <summary cref="C < T >">  
/// </summary>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6e628-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e628-130">See Also</span></span>

- [<span data-ttu-id="6e628-131">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6e628-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="6e628-132">/ DOC (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="6e628-132">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
- [<span data-ttu-id="6e628-133">Dokumentační komentáře XML</span><span class="sxs-lookup"><span data-stu-id="6e628-133">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
