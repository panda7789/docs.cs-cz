---
title: Literál komentáře XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: 1f8526c4b67b7d975b11f6ef5dada2b45bb6b1df
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56964176"
---
# <a name="xml-comment-literal-visual-basic"></a><span data-ttu-id="f22d1-102">Literál komentáře XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f22d1-102">XML Comment Literal (Visual Basic)</span></span>
<span data-ttu-id="f22d1-103">Literál představující <xref:System.Xml.Linq.XComment> objektu.</span><span class="sxs-lookup"><span data-stu-id="f22d1-103">A literal representing an <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f22d1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f22d1-104">Syntax</span></span>  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a><span data-ttu-id="f22d1-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="f22d1-105">Parts</span></span>  
  
|<span data-ttu-id="f22d1-106">Termín</span><span class="sxs-lookup"><span data-stu-id="f22d1-106">Term</span></span>|<span data-ttu-id="f22d1-107">Definice</span><span class="sxs-lookup"><span data-stu-id="f22d1-107">Definition</span></span>|  
|---|---|  
|`<!--`|<span data-ttu-id="f22d1-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f22d1-108">Required.</span></span> <span data-ttu-id="f22d1-109">Označuje začátek komentáře XML.</span><span class="sxs-lookup"><span data-stu-id="f22d1-109">Denotes the start of the XML comment.</span></span>|  
|`content`|<span data-ttu-id="f22d1-110">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f22d1-110">Required.</span></span> <span data-ttu-id="f22d1-111">Text, který se zobrazí v komentáři XML.</span><span class="sxs-lookup"><span data-stu-id="f22d1-111">Text to appear in the XML comment.</span></span> <span data-ttu-id="f22d1-112">Nesmí obsahovat dvě pomlčky (-) nebo končit pomlčkou za uzavírací značku.</span><span class="sxs-lookup"><span data-stu-id="f22d1-112">Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.</span></span>|  
|`-->`|<span data-ttu-id="f22d1-113">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f22d1-113">Required.</span></span> <span data-ttu-id="f22d1-114">Označuje konec komentáře XML.</span><span class="sxs-lookup"><span data-stu-id="f22d1-114">Denotes the end of the XML comment.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="f22d1-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f22d1-115">Return Value</span></span>  
 <span data-ttu-id="f22d1-116"><xref:System.Xml.Linq.XComment> Objektu.</span><span class="sxs-lookup"><span data-stu-id="f22d1-116">An <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f22d1-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f22d1-117">Remarks</span></span>  
 <span data-ttu-id="f22d1-118">Literály XML komentář neobsahují obsah dokumentu obsahují informace o dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f22d1-118">XML comment literals do not contain document content; they contain information about the document.</span></span> <span data-ttu-id="f22d1-119">Část Komentář XML se končí pořadí "-->".</span><span class="sxs-lookup"><span data-stu-id="f22d1-119">The XML comment section ends with the sequence "-->".</span></span> <span data-ttu-id="f22d1-120">Z toho vyplývá následující body:</span><span class="sxs-lookup"><span data-stu-id="f22d1-120">This implies the following points:</span></span>  
  
-   <span data-ttu-id="f22d1-121">Vložený výraz v literál komentáře XML nejde použít, protože vložený výraz oddělovače jsou platný obsah komentáře XML.</span><span class="sxs-lookup"><span data-stu-id="f22d1-121">You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.</span></span>  
  
-   <span data-ttu-id="f22d1-122">Oddíly Komentář XML nemůže být vnořena, protože `content` nemůže obsahovat hodnotu "-->".</span><span class="sxs-lookup"><span data-stu-id="f22d1-122">XML comment sections cannot be nested, because `content` cannot contain the value "-->".</span></span>  
  
 <span data-ttu-id="f22d1-123">Literál komentáře XML můžete přiřadit k proměnné nebo je můžete zahrnout do literálů XML element.</span><span class="sxs-lookup"><span data-stu-id="f22d1-123">You can assign an XML comment literal to a variable, or you can include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f22d1-124">Literál XML může zahrnovat více řádků bez použití znaků pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="f22d1-124">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="f22d1-125">Tato funkce umožňuje kopírovat obsah z dokumentu XML a vložte ho přímo do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f22d1-125">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="f22d1-126">Kompilátor jazyka Visual Basic převede literál komentáře XML na volání <xref:System.Xml.Linq.XComment.%23ctor%2A> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="f22d1-126">The Visual Basic compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f22d1-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="f22d1-127">Example</span></span>  
 <span data-ttu-id="f22d1-128">Následující příklad vytvoří komentáře XML, který obsahuje text "Toto je komentář".</span><span class="sxs-lookup"><span data-stu-id="f22d1-128">The following example creates an XML comment that contains the text "This is a comment".</span></span>  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="f22d1-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f22d1-129">See also</span></span>
- <xref:System.Xml.Linq.XComment>
- [<span data-ttu-id="f22d1-130">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="f22d1-130">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="f22d1-131">Literály XML</span><span class="sxs-lookup"><span data-stu-id="f22d1-131">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="f22d1-132">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f22d1-132">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
