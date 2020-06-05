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
ms.openlocfilehash: af57fc7d55c5cfda24a2fd9406b17dedee898760
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400096"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="1fb14-102">Doporučené značky XML pro dokumentační komentáře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1fb14-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="1fb14-103">Kompilátor Visual Basic může zpracovat dokumentační komentáře ve vašem kódu do souboru XML.</span><span class="sxs-lookup"><span data-stu-id="1fb14-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="1fb14-104">Pomocí dalších nástrojů můžete zpracovat soubor XML v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="1fb14-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="1fb14-105">Komentáře XML jsou povoleny v konstrukcích kódu, jako jsou typy a členy typu.</span><span class="sxs-lookup"><span data-stu-id="1fb14-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="1fb14-106">U částečných typů může mít komentáře XML pouze jednu část typu, přestože neexistuje žádné omezení na komentování členů.</span><span class="sxs-lookup"><span data-stu-id="1fb14-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1fb14-107">Komentáře k dokumentaci nelze použít na obory názvů.</span><span class="sxs-lookup"><span data-stu-id="1fb14-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="1fb14-108">Důvodem je, že jeden obor názvů může zahrnovat několik sestavení a nemusí být načtena všechna sestavení současně.</span><span class="sxs-lookup"><span data-stu-id="1fb14-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="1fb14-109">Kompilátor zpracovává všechny značky, které jsou platné XML.</span><span class="sxs-lookup"><span data-stu-id="1fb14-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="1fb14-110">Následující značky poskytují běžně používané funkce v dokumentaci uživatele.</span><span class="sxs-lookup"><span data-stu-id="1fb14-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[\<c>](c.md)|[\<code>](code.md)|[\<example>](example.md)|  
|<span data-ttu-id="1fb14-111">[\<exception>](exception.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1fb14-111">[\<exception>](exception.md) <sup>1</sup></span></span>|<span data-ttu-id="1fb14-112">[\<include>](include.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1fb14-112">[\<include>](include.md) <sup>1</sup></span></span>|[\<list>](list.md)|  
|[\<para>](para.md)|<span data-ttu-id="1fb14-113">[\<param>](param.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1fb14-113">[\<param>](param.md) <sup>1</sup></span></span>|[\<paramref>](paramref.md)|  
|<span data-ttu-id="1fb14-114">[\<permission>](permission.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1fb14-114">[\<permission>](permission.md) <sup>1</sup></span></span>|[\<remarks>](remarks.md)|[\<returns>](returns.md)|  
|<span data-ttu-id="1fb14-115">[\<see>](see.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1fb14-115">[\<see>](see.md) <sup>1</sup></span></span>|<span data-ttu-id="1fb14-116">[\<seealso>](seealso.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1fb14-116">[\<seealso>](seealso.md) <sup>1</sup></span></span>|[\<summary>](summary.md)|  
|<span data-ttu-id="1fb14-117">[\<typeparam>](typeparam.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1fb14-117">[\<typeparam>](typeparam.md) <sup>1</sup></span></span>|[\<value>](value.md)||  
  
 <span data-ttu-id="1fb14-118">(<sup>1</sup> kompilátor ověřuje syntaxi.)</span><span class="sxs-lookup"><span data-stu-id="1fb14-118">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1fb14-119">Pokud chcete, aby se v textu komentáře k dokumentaci zobrazovaly lomené závorky, použijte `&lt;` a `&gt;` .</span><span class="sxs-lookup"><span data-stu-id="1fb14-119">If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`.</span></span> <span data-ttu-id="1fb14-120">Například řetězec se `"&lt;text in angle brackets&gt;"` zobrazí jako `<text in angle brackets>` .</span><span class="sxs-lookup"><span data-stu-id="1fb14-120">For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fb14-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="1fb14-121">See also</span></span>

- [<span data-ttu-id="1fb14-122">Dokumentace kódu s XML</span><span class="sxs-lookup"><span data-stu-id="1fb14-122">Documenting Your Code with XML</span></span>](../../programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="1fb14-123">-doc</span><span class="sxs-lookup"><span data-stu-id="1fb14-123">-doc</span></span>](../../reference/command-line-compiler/doc.md)
- [<span data-ttu-id="1fb14-124">Postupy: Vytvoření dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="1fb14-124">How to: Create XML Documentation</span></span>](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
