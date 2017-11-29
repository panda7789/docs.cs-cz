---
title: "GetXmlNamespace – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 47ba67bc58debf8f144f6468bf510932414c0698
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="9b0c6-102">GetXmlNamespace – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b0c6-102">GetXmlNamespace Operator (Visual Basic)</span></span>
<span data-ttu-id="9b0c6-103">Získá <xref:System.Xml.Linq.XNamespace> objekt, který odpovídá zadané předpony oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="9b0c6-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b0c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b0c6-104">Syntax</span></span>  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="9b0c6-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="9b0c6-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="9b0c6-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="9b0c6-106">Optional.</span></span> <span data-ttu-id="9b0c6-107">Řetězec, který identifikuje Předpona oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="9b0c6-107">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="9b0c6-108">Pokud je zadaný, tento řetězec musí být platný identifikátor XML.</span><span class="sxs-lookup"><span data-stu-id="9b0c6-108">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="9b0c6-109">Další informace najdete v tématu [názvy z deklarovaný XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="9b0c6-109">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="9b0c6-110">Pokud žádná předpona. není zadaný, je vrácen výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="9b0c6-110">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="9b0c6-111">Pokud není zadán žádný výchozí obor názvů, je vrácena prázdného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9b0c6-111">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b0c6-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9b0c6-112">Return Value</span></span>  
 <span data-ttu-id="9b0c6-113"><xref:System.Xml.Linq.XNamespace> Objekt, který odpovídá Předpona oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="9b0c6-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b0c6-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9b0c6-114">Remarks</span></span>  
 <span data-ttu-id="9b0c6-115">`GetXmlNamespace` Získá operátor <xref:System.Xml.Linq.XNamespace> objekt, který odpovídá Předpona oboru názvů XML `xmlNamespacePrefix`.</span><span class="sxs-lookup"><span data-stu-id="9b0c6-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="9b0c6-116">XML – předpony oboru názvů přímo v literály XML a vlastnosti osy XML můžete použít.</span><span class="sxs-lookup"><span data-stu-id="9b0c6-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="9b0c6-117">Ale musí používat `GetXmlNamespace` operátor převést předpony oboru názvů <xref:System.Xml.Linq.XNamespace> objektu před použitím v kódu.</span><span class="sxs-lookup"><span data-stu-id="9b0c6-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="9b0c6-118">Přidáte-název nekvalifikované elementu k <xref:System.Xml.Linq.XNamespace> objekt, který chcete získat plně kvalifikovaný <xref:System.Xml.Linq.XName> objektu, který mnoho [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] metody vyžadují.</span><span class="sxs-lookup"><span data-stu-id="9b0c6-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b0c6-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="9b0c6-119">Example</span></span>  
 <span data-ttu-id="9b0c6-120">Následující příklad importuje `ns` jako předponu oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="9b0c6-120">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="9b0c6-121">Poté použije Předpona oboru názvů k vytvoření literál XML a přístup k první podřízený uzel, který má úplný název `ns:phone`.</span><span class="sxs-lookup"><span data-stu-id="9b0c6-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="9b0c6-122">Poté předá tento podřízený uzel k `ShowName` podprogramu, který vytvoří úplný název pomocí `GetXmlNamespace` operátor.</span><span class="sxs-lookup"><span data-stu-id="9b0c6-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="9b0c6-123">`ShowName` Podprogramu pak předá kvalifikovaný název do <xref:System.Xml.Linq.XNode.Ancestors%2A> metoda získat nadřazené `ns:contact` uzlu.</span><span class="sxs-lookup"><span data-stu-id="9b0c6-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/getxmlnamespace-operator_1.vb)]  
  
 <span data-ttu-id="9b0c6-124">Při volání `TestGetXmlNamespace.RunSample()`, zobrazí se okno se zprávou, která obsahuje následující text:</span><span class="sxs-lookup"><span data-stu-id="9b0c6-124">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="9b0c6-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="9b0c6-125">See Also</span></span>  
 [<span data-ttu-id="9b0c6-126">Imports – příkaz (Namespace XML)</span><span class="sxs-lookup"><span data-stu-id="9b0c6-126">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
 [<span data-ttu-id="9b0c6-127">Přístup XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9b0c6-127">Accessing XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
