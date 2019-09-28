---
title: GetXmlNamespace – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: bfccdcd9b5d35418b206dfa9fefffb5ddab69c66
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592170"
---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="864aa-102">GetXmlNamespace – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="864aa-102">GetXmlNamespace Operator (Visual Basic)</span></span>
<span data-ttu-id="864aa-103">Získá objekt <xref:System.Xml.Linq.XNamespace>, který odpovídá zadané předponě oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="864aa-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="864aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="864aa-104">Syntax</span></span>  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="864aa-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="864aa-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="864aa-106">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="864aa-106">Optional.</span></span> <span data-ttu-id="864aa-107">Řetězec, který identifikuje předponu oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="864aa-107">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="864aa-108">Je-li tento řetězec zadán, musí být platným identifikátorem XML.</span><span class="sxs-lookup"><span data-stu-id="864aa-108">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="864aa-109">Další informace najdete v tématu [Názvy deklarovaných elementů XML a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="864aa-109">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="864aa-110">Pokud není zadána žádná předpona, je vrácen výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="864aa-110">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="864aa-111">Pokud není zadán žádný výchozí obor názvů, je vrácen prázdný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="864aa-111">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="864aa-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="864aa-112">Return Value</span></span>  
 <span data-ttu-id="864aa-113">Objekt <xref:System.Xml.Linq.XNamespace>, který odpovídá předponě oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="864aa-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="864aa-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="864aa-114">Remarks</span></span>  
 <span data-ttu-id="864aa-115">Operátor `GetXmlNamespace` Získá objekt <xref:System.Xml.Linq.XNamespace>, který odpovídá předponě oboru názvů XML `xmlNamespacePrefix`.</span><span class="sxs-lookup"><span data-stu-id="864aa-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="864aa-116">Předpony oboru názvů XML lze použít přímo v literálech XML a vlastnostech osy XML.</span><span class="sxs-lookup"><span data-stu-id="864aa-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="864aa-117">Je však nutné použít operátor `GetXmlNamespace` pro převod předpony oboru názvů na objekt <xref:System.Xml.Linq.XNamespace> předtím, než jej můžete použít ve svém kódu.</span><span class="sxs-lookup"><span data-stu-id="864aa-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="864aa-118">Chcete-li získat plně kvalifikovaný objekt <xref:System.Xml.Linq.XName>, který vyžaduje mnoho metod [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete k objektu <xref:System.Xml.Linq.XNamespace> připojit Nekvalifikovaný název elementu.</span><span class="sxs-lookup"><span data-stu-id="864aa-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="864aa-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="864aa-119">Example</span></span>  
 <span data-ttu-id="864aa-120">Následující příklad importuje `ns` jako předponu oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="864aa-120">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="864aa-121">Poté pomocí předpony oboru názvů vytvoří literál XML a přístup k prvnímu podřízenému uzlu, který má kvalifikovaný název `ns:phone`.</span><span class="sxs-lookup"><span data-stu-id="864aa-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="864aa-122">Pak předá tento podřízený uzel dílčí rutině `ShowName`, která vytvoří kvalifikovaný název pomocí operátoru `GetXmlNamespace`.</span><span class="sxs-lookup"><span data-stu-id="864aa-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="864aa-123">Podprogram `ShowName` poté předává kvalifikovaný název metodě <xref:System.Xml.Linq.XNode.Ancestors%2A> pro získání nadřazeného uzlu `ns:contact`.</span><span class="sxs-lookup"><span data-stu-id="864aa-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 <span data-ttu-id="864aa-124">Když zavoláte `TestGetXmlNamespace.RunSample()`, zobrazí se okno se zprávou, které obsahuje následující text:</span><span class="sxs-lookup"><span data-stu-id="864aa-124">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="864aa-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="864aa-125">See also</span></span>

- [<span data-ttu-id="864aa-126">Příkaz Imports (obor názvů XML)</span><span class="sxs-lookup"><span data-stu-id="864aa-126">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="864aa-127">Přístup k XML v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="864aa-127">Accessing XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
