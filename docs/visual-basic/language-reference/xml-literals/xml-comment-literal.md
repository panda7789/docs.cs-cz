---
title: Literál komentáře XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: 8d9db66aabe344bd5c8f9a92ac8618b7bc1abb43
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349388"
---
# <a name="xml-comment-literal-visual-basic"></a><span data-ttu-id="92d49-102">Literál komentáře XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92d49-102">XML Comment Literal (Visual Basic)</span></span>
<span data-ttu-id="92d49-103">Literál představující objekt <xref:System.Xml.Linq.XComment>.</span><span class="sxs-lookup"><span data-stu-id="92d49-103">A literal representing an <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92d49-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92d49-104">Syntax</span></span>  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a><span data-ttu-id="92d49-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="92d49-105">Parts</span></span>  
  
|<span data-ttu-id="92d49-106">Termín</span><span class="sxs-lookup"><span data-stu-id="92d49-106">Term</span></span>|<span data-ttu-id="92d49-107">Definice</span><span class="sxs-lookup"><span data-stu-id="92d49-107">Definition</span></span>|  
|---|---|  
|`<!--`|<span data-ttu-id="92d49-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="92d49-108">Required.</span></span> <span data-ttu-id="92d49-109">Označuje začátek komentáře XML.</span><span class="sxs-lookup"><span data-stu-id="92d49-109">Denotes the start of the XML comment.</span></span>|  
|`content`|<span data-ttu-id="92d49-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="92d49-110">Required.</span></span> <span data-ttu-id="92d49-111">Text, který se má zobrazit v komentáři XML</span><span class="sxs-lookup"><span data-stu-id="92d49-111">Text to appear in the XML comment.</span></span> <span data-ttu-id="92d49-112">Nemůže obsahovat řadu dvou spojovníků (--) nebo končit spojovníkem, které je vedle uzavírací značky.</span><span class="sxs-lookup"><span data-stu-id="92d49-112">Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.</span></span>|  
|`-->`|<span data-ttu-id="92d49-113">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="92d49-113">Required.</span></span> <span data-ttu-id="92d49-114">Označuje konec komentáře XML.</span><span class="sxs-lookup"><span data-stu-id="92d49-114">Denotes the end of the XML comment.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="92d49-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="92d49-115">Return Value</span></span>  
 <span data-ttu-id="92d49-116">Objekt <xref:System.Xml.Linq.XComment>.</span><span class="sxs-lookup"><span data-stu-id="92d49-116">An <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92d49-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="92d49-117">Remarks</span></span>  
 <span data-ttu-id="92d49-118">Literály komentářů XML neobsahují obsah dokumentu. obsahují informace o dokumentu.</span><span class="sxs-lookup"><span data-stu-id="92d49-118">XML comment literals do not contain document content; they contain information about the document.</span></span> <span data-ttu-id="92d49-119">Oddíl komentáře XML končí sekvencí "-->".</span><span class="sxs-lookup"><span data-stu-id="92d49-119">The XML comment section ends with the sequence "-->".</span></span> <span data-ttu-id="92d49-120">To zahrnuje následující body:</span><span class="sxs-lookup"><span data-stu-id="92d49-120">This implies the following points:</span></span>  
  
- <span data-ttu-id="92d49-121">V literálu komentáře XML nemůžete použít vložený výraz, protože oddělovače vložených výrazů jsou platným obsahem komentáře XML.</span><span class="sxs-lookup"><span data-stu-id="92d49-121">You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.</span></span>  
  
- <span data-ttu-id="92d49-122">Oddíly komentářů XML nemůžou být vnořené, protože `content` nesmí obsahovat hodnotu-->.</span><span class="sxs-lookup"><span data-stu-id="92d49-122">XML comment sections cannot be nested, because `content` cannot contain the value "-->".</span></span>  
  
 <span data-ttu-id="92d49-123">Můžete přiřadit literál komentáře XML proměnné nebo ji můžete zahrnout do literálu elementu XML.</span><span class="sxs-lookup"><span data-stu-id="92d49-123">You can assign an XML comment literal to a variable, or you can include it in an XML element literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92d49-124">Literál XML může zahrnovat více řádků bez použití znaků pro pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="92d49-124">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="92d49-125">Tato funkce umožňuje kopírovat obsah z dokumentu XML a vložit ho přímo do Visual Basic programu.</span><span class="sxs-lookup"><span data-stu-id="92d49-125">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="92d49-126">Kompilátor Visual Basic převádí literál komentáře XML na volání konstruktoru <xref:System.Xml.Linq.XComment.%23ctor%2A>.</span><span class="sxs-lookup"><span data-stu-id="92d49-126">The Visual Basic compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92d49-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="92d49-127">Example</span></span>  
 <span data-ttu-id="92d49-128">Následující příklad vytvoří komentář XML, který obsahuje text "Toto je komentář".</span><span class="sxs-lookup"><span data-stu-id="92d49-128">The following example creates an XML comment that contains the text "This is a comment".</span></span>  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="92d49-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="92d49-129">See also</span></span>

- <xref:System.Xml.Linq.XComment>
- [<span data-ttu-id="92d49-130">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="92d49-130">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="92d49-131">Literály XML</span><span class="sxs-lookup"><span data-stu-id="92d49-131">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="92d49-132">Vytváření XML v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="92d49-132">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
