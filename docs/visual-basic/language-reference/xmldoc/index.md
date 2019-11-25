---
title: Recommended XML Tags for Documentation Comments
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: 093c967557b899c8661fdec348d421996e948b94
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352336"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="90fdc-102">Doporučené značky XML pro dokumentační komentáře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90fdc-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="90fdc-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span><span class="sxs-lookup"><span data-stu-id="90fdc-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="90fdc-104">You can use additional tools to process the XML file into documentation.</span><span class="sxs-lookup"><span data-stu-id="90fdc-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="90fdc-105">XML comments are allowed on code constructs such as types and type members.</span><span class="sxs-lookup"><span data-stu-id="90fdc-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="90fdc-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span><span class="sxs-lookup"><span data-stu-id="90fdc-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="90fdc-107">Documentation comments cannot be applied to namespaces.</span><span class="sxs-lookup"><span data-stu-id="90fdc-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="90fdc-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span><span class="sxs-lookup"><span data-stu-id="90fdc-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="90fdc-109">The compiler processes any tag that is valid XML.</span><span class="sxs-lookup"><span data-stu-id="90fdc-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="90fdc-110">The following tags provide commonly used functionality in user documentation.</span><span class="sxs-lookup"><span data-stu-id="90fdc-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="90fdc-111">\<c></span><span class="sxs-lookup"><span data-stu-id="90fdc-111">\<c></span></span>](../../../visual-basic/language-reference/xmldoc/c.md)|[<span data-ttu-id="90fdc-112">\<code></span><span class="sxs-lookup"><span data-stu-id="90fdc-112">\<code></span></span>](../../../visual-basic/language-reference/xmldoc/code.md)|[<span data-ttu-id="90fdc-113">\<example></span><span class="sxs-lookup"><span data-stu-id="90fdc-113">\<example></span></span>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|<span data-ttu-id="90fdc-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="90fdc-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span></span>|<span data-ttu-id="90fdc-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="90fdc-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span></span>|[<span data-ttu-id="90fdc-116">\<list></span><span class="sxs-lookup"><span data-stu-id="90fdc-116">\<list></span></span>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[<span data-ttu-id="90fdc-117">\<para></span><span class="sxs-lookup"><span data-stu-id="90fdc-117">\<para></span></span>](../../../visual-basic/language-reference/xmldoc/para.md)|<span data-ttu-id="90fdc-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="90fdc-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span></span>|[<span data-ttu-id="90fdc-119">\<paramref></span><span class="sxs-lookup"><span data-stu-id="90fdc-119">\<paramref></span></span>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|<span data-ttu-id="90fdc-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="90fdc-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span></span>|[<span data-ttu-id="90fdc-121">\<remarks></span><span class="sxs-lookup"><span data-stu-id="90fdc-121">\<remarks></span></span>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[<span data-ttu-id="90fdc-122">\<returns></span><span class="sxs-lookup"><span data-stu-id="90fdc-122">\<returns></span></span>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|<span data-ttu-id="90fdc-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="90fdc-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span></span>|<span data-ttu-id="90fdc-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="90fdc-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span></span>|[<span data-ttu-id="90fdc-125">\<summary></span><span class="sxs-lookup"><span data-stu-id="90fdc-125">\<summary></span></span>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|<span data-ttu-id="90fdc-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="90fdc-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span></span>|[<span data-ttu-id="90fdc-127">\<value></span><span class="sxs-lookup"><span data-stu-id="90fdc-127">\<value></span></span>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 <span data-ttu-id="90fdc-128">(<sup>1</sup> The compiler verifies syntax.)</span><span class="sxs-lookup"><span data-stu-id="90fdc-128">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="90fdc-129">If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`.</span><span class="sxs-lookup"><span data-stu-id="90fdc-129">If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`.</span></span> <span data-ttu-id="90fdc-130">For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.</span><span class="sxs-lookup"><span data-stu-id="90fdc-130">For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90fdc-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="90fdc-131">See also</span></span>

- [<span data-ttu-id="90fdc-132">Dokumentace kódu s XML</span><span class="sxs-lookup"><span data-stu-id="90fdc-132">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="90fdc-133">-doc</span><span class="sxs-lookup"><span data-stu-id="90fdc-133">-doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)
- [<span data-ttu-id="90fdc-134">Postupy: Vytvoření dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="90fdc-134">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
