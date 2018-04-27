---
title: Doporučené značky XML pro dokumentační komentáře (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7815d4c9fddc4e760c7495ef7a2509c55141e96e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="cfa67-102">Doporučené značky XML pro dokumentační komentáře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cfa67-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="cfa67-103">Visual Basic – kompilátor může zpracovat dokumentační komentáře v kódu do souboru XML.</span><span class="sxs-lookup"><span data-stu-id="cfa67-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="cfa67-104">Další nástroje můžete používat ke zpracování souboru XML do dokumentace.</span><span class="sxs-lookup"><span data-stu-id="cfa67-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="cfa67-105">XML – komentáře na kód konstruktory, jako jsou typy jsou povoleny a zadejte členy.</span><span class="sxs-lookup"><span data-stu-id="cfa67-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="cfa67-106">Pro částečné typy pouze jednu část typu může mít komentáře XML, i když neexistuje žádné omezení na komentářů její členy.</span><span class="sxs-lookup"><span data-stu-id="cfa67-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cfa67-107">Dokumentační komentáře nelze použít na obory názvů.</span><span class="sxs-lookup"><span data-stu-id="cfa67-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="cfa67-108">Důvodem je, že několik sestavení může mít rozsah jeden obor názvů, a ne všechny sestavení musí být načíst ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="cfa67-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="cfa67-109">Kompilátor zpracovává všechny značky, který je platný kód XML.</span><span class="sxs-lookup"><span data-stu-id="cfa67-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="cfa67-110">Následující značky poskytují běžně používané funkce v dokumentaci pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="cfa67-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="cfa67-111">\<c ></span><span class="sxs-lookup"><span data-stu-id="cfa67-111">\<c></span></span>](../../../visual-basic/language-reference/xmldoc/c.md)|[<span data-ttu-id="cfa67-112">\<kód ></span><span class="sxs-lookup"><span data-stu-id="cfa67-112">\<code></span></span>](../../../visual-basic/language-reference/xmldoc/code.md)|[<span data-ttu-id="cfa67-113">\<Příklad ></span><span class="sxs-lookup"><span data-stu-id="cfa67-113">\<example></span></span>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|<span data-ttu-id="cfa67-114">[\<Výjimka >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="cfa67-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span></span>|<span data-ttu-id="cfa67-115">[\<Zahrnout >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="cfa67-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span></span>|[<span data-ttu-id="cfa67-116">\<Seznam ></span><span class="sxs-lookup"><span data-stu-id="cfa67-116">\<list></span></span>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[<span data-ttu-id="cfa67-117">\<para ></span><span class="sxs-lookup"><span data-stu-id="cfa67-117">\<para></span></span>](../../../visual-basic/language-reference/xmldoc/para.md)|<span data-ttu-id="cfa67-118">[\<Param >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="cfa67-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span></span>|[<span data-ttu-id="cfa67-119">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="cfa67-119">\<paramref></span></span>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|<span data-ttu-id="cfa67-120">[\<oprávnění >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="cfa67-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span></span>|[<span data-ttu-id="cfa67-121">\<Poznámky ></span><span class="sxs-lookup"><span data-stu-id="cfa67-121">\<remarks></span></span>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[<span data-ttu-id="cfa67-122">\<Vrátí ></span><span class="sxs-lookup"><span data-stu-id="cfa67-122">\<returns></span></span>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|<span data-ttu-id="cfa67-123">[\<v tématu >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="cfa67-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span></span>|<span data-ttu-id="cfa67-124">[\<Viz také >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="cfa67-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span></span>|[<span data-ttu-id="cfa67-125">\<Souhrn ></span><span class="sxs-lookup"><span data-stu-id="cfa67-125">\<summary></span></span>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|<span data-ttu-id="cfa67-126">[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="cfa67-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span></span>|[<span data-ttu-id="cfa67-127">\<Hodnota ></span><span class="sxs-lookup"><span data-stu-id="cfa67-127">\<value></span></span>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 <span data-ttu-id="cfa67-128">(<sup>1</sup> kompilátor ověří syntaxi.)</span><span class="sxs-lookup"><span data-stu-id="cfa67-128">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cfa67-129">Pokud chcete lomené závorky, než se objeví v text komentáře dokumentace, použijte `<` a `>`.</span><span class="sxs-lookup"><span data-stu-id="cfa67-129">If you want angle brackets to appear in the text of a documentation comment, use `<` and `>`.</span></span> <span data-ttu-id="cfa67-130">Například řetězec `"<text in angle brackets>"` se zobrazí jako `<text in angle``brackets>`.</span><span class="sxs-lookup"><span data-stu-id="cfa67-130">For example, the string `"<text in angle brackets>"` will appear as `<text in angle``brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfa67-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="cfa67-131">See Also</span></span>  
 [<span data-ttu-id="cfa67-132">Dokumentace kódu s XML</span><span class="sxs-lookup"><span data-stu-id="cfa67-132">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [<span data-ttu-id="cfa67-133">/doc</span><span class="sxs-lookup"><span data-stu-id="cfa67-133">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [<span data-ttu-id="cfa67-134">Postupy: Vytvoření dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="cfa67-134">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
