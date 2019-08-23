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
ms.openlocfilehash: 91369392f33f2a86a7a4cb5ffb3faa668c113348
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965401"
---
# <a name="xml-comment-literal-visual-basic"></a><span data-ttu-id="7858a-102">Literál komentáře XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7858a-102">XML Comment Literal (Visual Basic)</span></span>
<span data-ttu-id="7858a-103">Literál představující <xref:System.Xml.Linq.XComment> objekt.</span><span class="sxs-lookup"><span data-stu-id="7858a-103">A literal representing an <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7858a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7858a-104">Syntax</span></span>  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a><span data-ttu-id="7858a-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="7858a-105">Parts</span></span>  
  
|<span data-ttu-id="7858a-106">Termín</span><span class="sxs-lookup"><span data-stu-id="7858a-106">Term</span></span>|<span data-ttu-id="7858a-107">Definice</span><span class="sxs-lookup"><span data-stu-id="7858a-107">Definition</span></span>|  
|---|---|  
|`<!--`|<span data-ttu-id="7858a-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="7858a-108">Required.</span></span> <span data-ttu-id="7858a-109">Označuje začátek komentáře XML.</span><span class="sxs-lookup"><span data-stu-id="7858a-109">Denotes the start of the XML comment.</span></span>|  
|`content`|<span data-ttu-id="7858a-110">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="7858a-110">Required.</span></span> <span data-ttu-id="7858a-111">Text, který se má zobrazit v komentáři XML</span><span class="sxs-lookup"><span data-stu-id="7858a-111">Text to appear in the XML comment.</span></span> <span data-ttu-id="7858a-112">Nemůže obsahovat řadu dvou spojovníků (--) nebo končit spojovníkem, které je vedle uzavírací značky.</span><span class="sxs-lookup"><span data-stu-id="7858a-112">Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.</span></span>|  
|`-->`|<span data-ttu-id="7858a-113">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="7858a-113">Required.</span></span> <span data-ttu-id="7858a-114">Označuje konec komentáře XML.</span><span class="sxs-lookup"><span data-stu-id="7858a-114">Denotes the end of the XML comment.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="7858a-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7858a-115">Return Value</span></span>  
 <span data-ttu-id="7858a-116"><xref:System.Xml.Linq.XComment> Objekt.</span><span class="sxs-lookup"><span data-stu-id="7858a-116">An <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7858a-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7858a-117">Remarks</span></span>  
 <span data-ttu-id="7858a-118">Literály komentářů XML neobsahují obsah dokumentu. obsahují informace o dokumentu.</span><span class="sxs-lookup"><span data-stu-id="7858a-118">XML comment literals do not contain document content; they contain information about the document.</span></span> <span data-ttu-id="7858a-119">Oddíl komentáře XML končí sekvencí "-->".</span><span class="sxs-lookup"><span data-stu-id="7858a-119">The XML comment section ends with the sequence "-->".</span></span> <span data-ttu-id="7858a-120">To zahrnuje následující body:</span><span class="sxs-lookup"><span data-stu-id="7858a-120">This implies the following points:</span></span>  
  
- <span data-ttu-id="7858a-121">V literálu komentáře XML nemůžete použít vložený výraz, protože oddělovače vložených výrazů jsou platným obsahem komentáře XML.</span><span class="sxs-lookup"><span data-stu-id="7858a-121">You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.</span></span>  
  
- <span data-ttu-id="7858a-122">Oddíly komentářů XML nemůžou být vnořené, `content` protože nesmí obsahovat hodnotu-->.</span><span class="sxs-lookup"><span data-stu-id="7858a-122">XML comment sections cannot be nested, because `content` cannot contain the value "-->".</span></span>  
  
 <span data-ttu-id="7858a-123">Můžete přiřadit literál komentáře XML proměnné nebo ji můžete zahrnout do literálu elementu XML.</span><span class="sxs-lookup"><span data-stu-id="7858a-123">You can assign an XML comment literal to a variable, or you can include it in an XML element literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7858a-124">Literál XML může zahrnovat více řádků bez použití znaků pro pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="7858a-124">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="7858a-125">Tato funkce umožňuje kopírovat obsah z dokumentu XML a vložit ho přímo do Visual Basic programu.</span><span class="sxs-lookup"><span data-stu-id="7858a-125">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="7858a-126">Kompilátor Visual Basic převádí literál komentáře XML na volání <xref:System.Xml.Linq.XComment.%23ctor%2A> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="7858a-126">The Visual Basic compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7858a-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="7858a-127">Example</span></span>  
 <span data-ttu-id="7858a-128">Následující příklad vytvoří komentář XML, který obsahuje text "Toto je komentář".</span><span class="sxs-lookup"><span data-stu-id="7858a-128">The following example creates an XML comment that contains the text "This is a comment".</span></span>  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="7858a-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7858a-129">See also</span></span>

- <xref:System.Xml.Linq.XComment>
- [<span data-ttu-id="7858a-130">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="7858a-130">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="7858a-131">Literály XML</span><span class="sxs-lookup"><span data-stu-id="7858a-131">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="7858a-132">Vytváření XML v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7858a-132">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
