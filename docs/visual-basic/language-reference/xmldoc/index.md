---
title: Doporučené značky XML pro dokumentační komentáře
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
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="b8bcb-102">Doporučené značky XML pro dokumentační komentáře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8bcb-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="b8bcb-103">Kompilátor Visual Basic může zpracovat dokumentační komentáře ve vašem kódu do souboru XML.</span><span class="sxs-lookup"><span data-stu-id="b8bcb-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="b8bcb-104">Pomocí dalších nástrojů můžete zpracovat soubor XML v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="b8bcb-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="b8bcb-105">Komentáře XML jsou povoleny v konstrukcích kódu, jako jsou typy a členy typu.</span><span class="sxs-lookup"><span data-stu-id="b8bcb-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="b8bcb-106">U částečných typů může mít komentáře XML pouze jednu část typu, přestože neexistuje žádné omezení na komentování členů.</span><span class="sxs-lookup"><span data-stu-id="b8bcb-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8bcb-107">Komentáře k dokumentaci nelze použít na obory názvů.</span><span class="sxs-lookup"><span data-stu-id="b8bcb-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="b8bcb-108">Důvodem je, že jeden obor názvů může zahrnovat několik sestavení a nemusí být načtena všechna sestavení současně.</span><span class="sxs-lookup"><span data-stu-id="b8bcb-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="b8bcb-109">Kompilátor zpracovává všechny značky, které jsou platné XML.</span><span class="sxs-lookup"><span data-stu-id="b8bcb-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="b8bcb-110">Následující značky poskytují běžně používané funkce v dokumentaci uživatele.</span><span class="sxs-lookup"><span data-stu-id="b8bcb-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="b8bcb-111">\<c ></span><span class="sxs-lookup"><span data-stu-id="b8bcb-111">\<c></span></span>](../../../visual-basic/language-reference/xmldoc/c.md)|[<span data-ttu-id="b8bcb-112">kód \<></span><span class="sxs-lookup"><span data-stu-id="b8bcb-112">\<code></span></span>](../../../visual-basic/language-reference/xmldoc/code.md)|[<span data-ttu-id="b8bcb-113">\<příklad ></span><span class="sxs-lookup"><span data-stu-id="b8bcb-113">\<example></span></span>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|<span data-ttu-id="b8bcb-114">[výjimka\<>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b8bcb-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span></span>|<span data-ttu-id="b8bcb-115">[\<zahrnout >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b8bcb-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span></span>|[<span data-ttu-id="b8bcb-116">seznam \<></span><span class="sxs-lookup"><span data-stu-id="b8bcb-116">\<list></span></span>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[<span data-ttu-id="b8bcb-117">\<para ></span><span class="sxs-lookup"><span data-stu-id="b8bcb-117">\<para></span></span>](../../../visual-basic/language-reference/xmldoc/para.md)|<span data-ttu-id="b8bcb-118">[\<param >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b8bcb-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span></span>|[<span data-ttu-id="b8bcb-119">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="b8bcb-119">\<paramref></span></span>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|<span data-ttu-id="b8bcb-120">[\<oprávnění >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b8bcb-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span></span>|[<span data-ttu-id="b8bcb-121">\<poznámky ></span><span class="sxs-lookup"><span data-stu-id="b8bcb-121">\<remarks></span></span>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[<span data-ttu-id="b8bcb-122">\<returns></span><span class="sxs-lookup"><span data-stu-id="b8bcb-122">\<returns></span></span>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|<span data-ttu-id="b8bcb-123">[\<zobrazit >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b8bcb-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span></span>|<span data-ttu-id="b8bcb-124">[\<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b8bcb-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span></span>|[<span data-ttu-id="b8bcb-125">\<summary></span><span class="sxs-lookup"><span data-stu-id="b8bcb-125">\<summary></span></span>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|<span data-ttu-id="b8bcb-126">[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b8bcb-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span></span>|[<span data-ttu-id="b8bcb-127">\<value></span><span class="sxs-lookup"><span data-stu-id="b8bcb-127">\<value></span></span>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 <span data-ttu-id="b8bcb-128">(<sup>1</sup> kompilátor ověřuje syntaxi.)</span><span class="sxs-lookup"><span data-stu-id="b8bcb-128">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8bcb-129">Pokud chcete, aby se v textu komentáře k dokumentaci zobrazovaly lomené závorky, použijte `&lt;` a `&gt;`.</span><span class="sxs-lookup"><span data-stu-id="b8bcb-129">If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`.</span></span> <span data-ttu-id="b8bcb-130">Například řetězec `"&lt;text in angle brackets&gt;"` se zobrazí jako `<text in angle brackets>`.</span><span class="sxs-lookup"><span data-stu-id="b8bcb-130">For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8bcb-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8bcb-131">See also</span></span>

- [<span data-ttu-id="b8bcb-132">Dokumentace kódu s XML</span><span class="sxs-lookup"><span data-stu-id="b8bcb-132">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="b8bcb-133">-doc</span><span class="sxs-lookup"><span data-stu-id="b8bcb-133">-doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)
- [<span data-ttu-id="b8bcb-134">Postupy: Vytvoření dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="b8bcb-134">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
