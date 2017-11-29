---
title: "Doporučené značky pro dokumentační komentáře (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4d558bbe58d1f4a1c290b4f36718293d5ba1c734
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="28c1b-102">Doporučené značky pro dokumentační komentáře (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="28c1b-102">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="28c1b-103">Kompilátor jazyka C# zpracovává dokumentační komentáře v kódu a je ve formátu XML v souboru s názvem zadáte v **/doc** možnost příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="28c1b-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="28c1b-104">K vytvoření konečné dokumentaci založenou na soubor generované kompilátorem, můžete vytvořit vlastní nástroj nebo pomocí nástroje, jako například [aplikaci Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="28c1b-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="28c1b-105">Značky jsou zpracovávány na kód konstruktory, jako jsou typy a členy typu.</span><span class="sxs-lookup"><span data-stu-id="28c1b-105">Tags are processed on code constructs such as types and type members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28c1b-106">Dokumentační komentáře nelze použít pro obor názvů.</span><span class="sxs-lookup"><span data-stu-id="28c1b-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="28c1b-107">Kompilátor zpracuje všechny značky, který je platný kód XML.</span><span class="sxs-lookup"><span data-stu-id="28c1b-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="28c1b-108">Následující značky poskytují funkce obvykle používané v dokumentaci pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="28c1b-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="28c1b-109">Značky</span><span class="sxs-lookup"><span data-stu-id="28c1b-109">Tags</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="28c1b-110">\<c ></span><span class="sxs-lookup"><span data-stu-id="28c1b-110">\<c></span></span>](../../../csharp/programming-guide/xmldoc/code-inline.md)|[<span data-ttu-id="28c1b-111">\<para ></span><span class="sxs-lookup"><span data-stu-id="28c1b-111">\<para></span></span>](../../../csharp/programming-guide/xmldoc/para.md)|<span data-ttu-id="28c1b-112">[\<v tématu >](../../../csharp/programming-guide/xmldoc/see.md)*</span><span class="sxs-lookup"><span data-stu-id="28c1b-112">[\<see>](../../../csharp/programming-guide/xmldoc/see.md)*</span></span>|  
|[<span data-ttu-id="28c1b-113">\<kód ></span><span class="sxs-lookup"><span data-stu-id="28c1b-113">\<code></span></span>](../../../csharp/programming-guide/xmldoc/code.md)|<span data-ttu-id="28c1b-114">[\<Param >](../../../csharp/programming-guide/xmldoc/param.md)*</span><span class="sxs-lookup"><span data-stu-id="28c1b-114">[\<param>](../../../csharp/programming-guide/xmldoc/param.md)*</span></span>|<span data-ttu-id="28c1b-115">[\<Viz také >](../../../csharp/programming-guide/xmldoc/seealso.md)*</span><span class="sxs-lookup"><span data-stu-id="28c1b-115">[\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md)*</span></span>|  
|[<span data-ttu-id="28c1b-116">\<Příklad ></span><span class="sxs-lookup"><span data-stu-id="28c1b-116">\<example></span></span>](../../../csharp/programming-guide/xmldoc/example.md)|[<span data-ttu-id="28c1b-117">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="28c1b-117">\<paramref></span></span>](../../../csharp/programming-guide/xmldoc/paramref.md)|[<span data-ttu-id="28c1b-118">\<Souhrn ></span><span class="sxs-lookup"><span data-stu-id="28c1b-118">\<summary></span></span>](../../../csharp/programming-guide/xmldoc/summary.md)|  
|<span data-ttu-id="28c1b-119">[\<Výjimka >](../../../csharp/programming-guide/xmldoc/exception.md)*</span><span class="sxs-lookup"><span data-stu-id="28c1b-119">[\<exception>](../../../csharp/programming-guide/xmldoc/exception.md)*</span></span>|<span data-ttu-id="28c1b-120">[\<oprávnění >](../../../csharp/programming-guide/xmldoc/permission.md)*</span><span class="sxs-lookup"><span data-stu-id="28c1b-120">[\<permission>](../../../csharp/programming-guide/xmldoc/permission.md)*</span></span>|<span data-ttu-id="28c1b-121">[\<typeparam >](../../../csharp/programming-guide/xmldoc/typeparam.md)*</span><span class="sxs-lookup"><span data-stu-id="28c1b-121">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)*</span></span>|  
|<span data-ttu-id="28c1b-122">[\<Zahrnout >](../../../csharp/programming-guide/xmldoc/include.md)*</span><span class="sxs-lookup"><span data-stu-id="28c1b-122">[\<include>](../../../csharp/programming-guide/xmldoc/include.md)*</span></span>|[<span data-ttu-id="28c1b-123">\<Poznámky ></span><span class="sxs-lookup"><span data-stu-id="28c1b-123">\<remarks></span></span>](../../../csharp/programming-guide/xmldoc/remarks.md)|[<span data-ttu-id="28c1b-124">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="28c1b-124">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)|  
|[<span data-ttu-id="28c1b-125">\<Seznam ></span><span class="sxs-lookup"><span data-stu-id="28c1b-125">\<list></span></span>](../../../csharp/programming-guide/xmldoc/list.md)|[<span data-ttu-id="28c1b-126">\<Vrátí ></span><span class="sxs-lookup"><span data-stu-id="28c1b-126">\<returns></span></span>](../../../csharp/programming-guide/xmldoc/returns.md)|[<span data-ttu-id="28c1b-127">\<Hodnota ></span><span class="sxs-lookup"><span data-stu-id="28c1b-127">\<value></span></span>](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 <span data-ttu-id="28c1b-128">(* označuje, že kompilátor ověří syntaxi.)</span><span class="sxs-lookup"><span data-stu-id="28c1b-128">(* denotes that the compiler verifies syntax.)</span></span>  
  
 <span data-ttu-id="28c1b-129">Pokud chcete lomené závorky, než se objeví v text komentáře dokumentace, použijte `<` a `>`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="28c1b-129">If you want angle brackets to appear in the text of a documentation comment, use `<` and `>`, as shown in the following example.</span></span>  
  
```xml  
/// <summary cref="C < T >">  
/// </summary>  
```  
  
## <a name="see-also"></a><span data-ttu-id="28c1b-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="28c1b-130">See Also</span></span>  
 [<span data-ttu-id="28c1b-131">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="28c1b-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="28c1b-132">/ DOC (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="28c1b-132">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [<span data-ttu-id="28c1b-133">Dokumentační komentáře XML</span><span class="sxs-lookup"><span data-stu-id="28c1b-133">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
