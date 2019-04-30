---
title: Doporučené značky XML pro dokumentační komentáře (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: e59ee25b22c51e47dc83233af33099e6c55de87b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940853"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="a39aa-102">Doporučené značky XML pro dokumentační komentáře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a39aa-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="a39aa-103">Kompilátor jazyka Visual Basic můžete zpracovat dokumentační komentáře v kódu do souboru XML.</span><span class="sxs-lookup"><span data-stu-id="a39aa-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="a39aa-104">Další nástroje můžete použít ke zpracování souboru XML do dokumentace ke službě.</span><span class="sxs-lookup"><span data-stu-id="a39aa-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="a39aa-105">Komentáře XML jsou povolené konstrukcí jako jsou typy a členy typu.</span><span class="sxs-lookup"><span data-stu-id="a39aa-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="a39aa-106">Pro částečné typy mají pouze jednu část typu komentáře XML, ačkoli neexistuje žádné omezení komentování jejích členů.</span><span class="sxs-lookup"><span data-stu-id="a39aa-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a39aa-107">Dokumentační komentáře nelze použít pro obory názvů.</span><span class="sxs-lookup"><span data-stu-id="a39aa-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="a39aa-108">Důvodem je, že jeden obor názvů může zahrnovat několik sestavení, a ne všechna sestavení mají být načteny současně.</span><span class="sxs-lookup"><span data-stu-id="a39aa-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="a39aa-109">Kompilátor zpracovává všechny značky, který je platný kód XML.</span><span class="sxs-lookup"><span data-stu-id="a39aa-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="a39aa-110">Následující značky poskytuje běžně používané funkce v dokumentaci pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="a39aa-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="a39aa-111">\<c></span><span class="sxs-lookup"><span data-stu-id="a39aa-111">\<c></span></span>](../../../visual-basic/language-reference/xmldoc/c.md)|[<span data-ttu-id="a39aa-112">\<code></span><span class="sxs-lookup"><span data-stu-id="a39aa-112">\<code></span></span>](../../../visual-basic/language-reference/xmldoc/code.md)|[<span data-ttu-id="a39aa-113">\<example></span><span class="sxs-lookup"><span data-stu-id="a39aa-113">\<example></span></span>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|<span data-ttu-id="a39aa-114">[\<Výjimka >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a39aa-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span></span>|<span data-ttu-id="a39aa-115">[\<Zahrnout >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a39aa-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span></span>|[<span data-ttu-id="a39aa-116">\<list></span><span class="sxs-lookup"><span data-stu-id="a39aa-116">\<list></span></span>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[<span data-ttu-id="a39aa-117">\<para></span><span class="sxs-lookup"><span data-stu-id="a39aa-117">\<para></span></span>](../../../visual-basic/language-reference/xmldoc/para.md)|<span data-ttu-id="a39aa-118">[\<Param >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a39aa-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span></span>|[<span data-ttu-id="a39aa-119">\<paramref></span><span class="sxs-lookup"><span data-stu-id="a39aa-119">\<paramref></span></span>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|<span data-ttu-id="a39aa-120">[\<oprávnění >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a39aa-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span></span>|[<span data-ttu-id="a39aa-121">\<remarks></span><span class="sxs-lookup"><span data-stu-id="a39aa-121">\<remarks></span></span>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[<span data-ttu-id="a39aa-122">\<returns></span><span class="sxs-lookup"><span data-stu-id="a39aa-122">\<returns></span></span>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|<span data-ttu-id="a39aa-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a39aa-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span></span>|<span data-ttu-id="a39aa-124">[\<SeeAlso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a39aa-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span></span>|[<span data-ttu-id="a39aa-125">\<summary></span><span class="sxs-lookup"><span data-stu-id="a39aa-125">\<summary></span></span>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|<span data-ttu-id="a39aa-126">[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a39aa-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span></span>|[<span data-ttu-id="a39aa-127">\<value></span><span class="sxs-lookup"><span data-stu-id="a39aa-127">\<value></span></span>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 <span data-ttu-id="a39aa-128">(<sup>1</sup> kompilátor ověří syntaxi.)</span><span class="sxs-lookup"><span data-stu-id="a39aa-128">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a39aa-129">Pokud chcete ostré závorky se zobrazí v textu Dokumentační komentář, použijte `&lt;` a `&gt;`.</span><span class="sxs-lookup"><span data-stu-id="a39aa-129">If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`.</span></span> <span data-ttu-id="a39aa-130">Například řetězec `"&lt;text in angle brackets&gt;"` se zobrazí jako `<text in angle brackets>`.</span><span class="sxs-lookup"><span data-stu-id="a39aa-130">For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a39aa-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a39aa-131">See also</span></span>

- [<span data-ttu-id="a39aa-132">Dokumentace kódu s XML</span><span class="sxs-lookup"><span data-stu-id="a39aa-132">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="a39aa-133">/doc</span><span class="sxs-lookup"><span data-stu-id="a39aa-133">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)
- [<span data-ttu-id="a39aa-134">Postupy: Vytvoření dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="a39aa-134">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
