---
title: "Literál komentáře XML (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 36be34ac22cfe926a2eea946f5e4c4eb534de696
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xml-comment-literal-visual-basic"></a><span data-ttu-id="12b9d-102">Literál komentáře XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12b9d-102">XML Comment Literal (Visual Basic)</span></span>
<span data-ttu-id="12b9d-103">Literál představující <xref:System.Xml.Linq.XComment> objektu.</span><span class="sxs-lookup"><span data-stu-id="12b9d-103">A literal representing an <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12b9d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12b9d-104">Syntax</span></span>  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a><span data-ttu-id="12b9d-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="12b9d-105">Parts</span></span>  
  
|<span data-ttu-id="12b9d-106">Termín</span><span class="sxs-lookup"><span data-stu-id="12b9d-106">Term</span></span>|<span data-ttu-id="12b9d-107">Definice</span><span class="sxs-lookup"><span data-stu-id="12b9d-107">Definition</span></span>|  
|---|---|  
|`<!--`|<span data-ttu-id="12b9d-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="12b9d-108">Required.</span></span> <span data-ttu-id="12b9d-109">Označuje začátek komentáře XML.</span><span class="sxs-lookup"><span data-stu-id="12b9d-109">Denotes the start of the XML comment.</span></span>|  
|`content`|<span data-ttu-id="12b9d-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="12b9d-110">Required.</span></span> <span data-ttu-id="12b9d-111">Text, který se zobrazí v komentáře XML.</span><span class="sxs-lookup"><span data-stu-id="12b9d-111">Text to appear in the XML comment.</span></span> <span data-ttu-id="12b9d-112">Nemůže obsahovat dvě pomlčky (-) nebo končit pomlčkou přiléhající k uzavírací značku.</span><span class="sxs-lookup"><span data-stu-id="12b9d-112">Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.</span></span>|  
|`-->`|<span data-ttu-id="12b9d-113">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="12b9d-113">Required.</span></span> <span data-ttu-id="12b9d-114">Označuje konec komentáře XML.</span><span class="sxs-lookup"><span data-stu-id="12b9d-114">Denotes the end of the XML comment.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="12b9d-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="12b9d-115">Return Value</span></span>  
 <span data-ttu-id="12b9d-116"><xref:System.Xml.Linq.XComment> Objektu.</span><span class="sxs-lookup"><span data-stu-id="12b9d-116">An <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12b9d-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12b9d-117">Remarks</span></span>  
 <span data-ttu-id="12b9d-118">XML – literály komentář neobsahují obsah dokumentu; obsahují informace o dokumentu.</span><span class="sxs-lookup"><span data-stu-id="12b9d-118">XML comment literals do not contain document content; they contain information about the document.</span></span> <span data-ttu-id="12b9d-119">V části komentáře XML končí pořadí "-->".</span><span class="sxs-lookup"><span data-stu-id="12b9d-119">The XML comment section ends with the sequence "-->".</span></span> <span data-ttu-id="12b9d-120">To znamená následující body:</span><span class="sxs-lookup"><span data-stu-id="12b9d-120">This implies the following points:</span></span>  
  
-   <span data-ttu-id="12b9d-121">Výraz vložené v literál komentáře jazyka XML nelze použít, protože oddělovače embedded výraz platný obsah komentáře XML.</span><span class="sxs-lookup"><span data-stu-id="12b9d-121">You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.</span></span>  
  
-   <span data-ttu-id="12b9d-122">Komentář oddílech XML nemůže být vnořena, protože `content` nemůže obsahovat hodnotu "-->".</span><span class="sxs-lookup"><span data-stu-id="12b9d-122">XML comment sections cannot be nested, because `content` cannot contain the value "-->".</span></span>  
  
 <span data-ttu-id="12b9d-123">Literál komentáře jazyka XML je možné přiřadit do proměnné, nebo můžete zahrnout do literál XML elementu.</span><span class="sxs-lookup"><span data-stu-id="12b9d-123">You can assign an XML comment literal to a variable, or you can include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="12b9d-124">Literál XML může zahrnovat více řádků bez použití znaky pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="12b9d-124">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="12b9d-125">Tato funkce umožňuje kopírovat obsah z dokumentu XML a vložte ji přímo do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span><span class="sxs-lookup"><span data-stu-id="12b9d-125">This feature enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span></span>  
  
 <span data-ttu-id="12b9d-126">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilátoru převede literál XML komentář k volání <xref:System.Xml.Linq.XComment.%23ctor%2A> konstruktor.</span><span class="sxs-lookup"><span data-stu-id="12b9d-126">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12b9d-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="12b9d-127">Example</span></span>  
 <span data-ttu-id="12b9d-128">Následující příklad vytvoří komentáře jazyka XML, který obsahuje text "Toto je komentář".</span><span class="sxs-lookup"><span data-stu-id="12b9d-128">The following example creates an XML comment that contains the text "This is a comment".</span></span>  
  
 [!code-vb[VbXMLSamples#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-comment-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="12b9d-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="12b9d-129">See Also</span></span>  
 <xref:System.Xml.Linq.XComment>  
 [<span data-ttu-id="12b9d-130">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="12b9d-130">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="12b9d-131">XML – literály</span><span class="sxs-lookup"><span data-stu-id="12b9d-131">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="12b9d-132">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="12b9d-132">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
