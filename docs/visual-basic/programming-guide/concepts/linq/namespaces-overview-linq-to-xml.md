---
title: "Přehled oborů názvů (technologie LINQ to XML)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8eb31fa-4b26-4acf-8050-6e705687f458
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 082172720abd39634f7183367d4d7b8d53d2bb7e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="namespaces-overview-linq-to-xml"></a><span data-ttu-id="e596d-102">Přehled oborů názvů (technologie LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="e596d-102">Namespaces Overview (LINQ to XML)</span></span>
<span data-ttu-id="e596d-103">Toto téma představuje obory názvů, <xref:System.Xml.Linq.XName> třída a <xref:System.Xml.Linq.XNamespace> třídy.</span><span class="sxs-lookup"><span data-stu-id="e596d-103">This topic introduces namespaces, the <xref:System.Xml.Linq.XName> class, and the <xref:System.Xml.Linq.XNamespace> class.</span></span>  
  
## <a name="xml-names"></a><span data-ttu-id="e596d-104">Názvy XML</span><span class="sxs-lookup"><span data-stu-id="e596d-104">XML Names</span></span>  
 <span data-ttu-id="e596d-105">Názvy XML jsou často zdroj složitostí při programování XML.</span><span class="sxs-lookup"><span data-stu-id="e596d-105">XML names are often a source of complexity in XML programming.</span></span> <span data-ttu-id="e596d-106">Název XML se skládá z oboru názvů XML (také nazývané identifikátor URI oboru názvů XML) a místní název.</span><span class="sxs-lookup"><span data-stu-id="e596d-106">An XML name consists of an XML namespace (also called an XML namespace URI) and a local name.</span></span> <span data-ttu-id="e596d-107">Je podobná oboru názvů v oboru názvů XML [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]– na základě programu.</span><span class="sxs-lookup"><span data-stu-id="e596d-107">An XML namespace is similar to a namespace in a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]-based program.</span></span> <span data-ttu-id="e596d-108">Umožňuje jednoznačně kvalifikovat názvy elementů a atributů.</span><span class="sxs-lookup"><span data-stu-id="e596d-108">It enables you to uniquely qualify the names of elements and attributes.</span></span> <span data-ttu-id="e596d-109">To pomáhá zabránit konflikty v názvech mezi různé části dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="e596d-109">This helps avoid name conflicts between various parts of an XML document.</span></span> <span data-ttu-id="e596d-110">Pokud máte deklarován obor názvů XML, můžete vybrat místní název, který se musí být jedinečný v daném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e596d-110">When you have declared an XML namespace, you can select a local name that only has to be unique within that namespace.</span></span>  
  
 <span data-ttu-id="e596d-111">Další aspekt názvů XML je XML *předpony oboru názvů*.</span><span class="sxs-lookup"><span data-stu-id="e596d-111">Another aspect of XML names is XML *namespace prefixes*.</span></span> <span data-ttu-id="e596d-112">XML – předpony způsobit, že většina složitost názvů XML.</span><span class="sxs-lookup"><span data-stu-id="e596d-112">XML prefixes cause most of the complexity of XML names.</span></span> <span data-ttu-id="e596d-113">Tyto předpony umožňují vytvořit zástupce pro obor názvů XML, který zkracují a nerozumí dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="e596d-113">These prefixes enable you to create a shortcut for an XML namespace, which makes the XML document more concise and understandable.</span></span> <span data-ttu-id="e596d-114">XML – předpony však závisí na jejich kontext, který má význam, který přidá složitost.</span><span class="sxs-lookup"><span data-stu-id="e596d-114">However, XML prefixes depend on their context to have meaning, which adds complexity.</span></span> <span data-ttu-id="e596d-115">Například předpona XML `aw` může být spojeny s jeden obor názvů XML v jedné části stromu XML a s jiný obor názvů XML v různých součástí stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="e596d-115">For example, the XML prefix `aw` could be associated with one XML namespace in one part of an XML tree, and with a different XML namespace in a different part of the XML tree.</span></span>  
  
 <span data-ttu-id="e596d-116">Při použití [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] s Visual Basic a XML – literály, musíte použít předpony oboru názvů při práci s dokumenty v oborech názvů.</span><span class="sxs-lookup"><span data-stu-id="e596d-116">When using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] with Visual Basic and XML literals, you must use namespace prefixes when working with documents in namespaces.</span></span>  
  
 <span data-ttu-id="e596d-117">V [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], je třída, která představuje názvy XML <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="e596d-117">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the class that represents XML names is <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="e596d-118">Často se názvy XML v průběhu zobrazit [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] rozhraní API, a bez ohledu na název XML je potřeba, najdete <xref:System.Xml.Linq.XName> parametr.</span><span class="sxs-lookup"><span data-stu-id="e596d-118">XML names appear frequently throughout the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API, and wherever an XML name is required, you will find an <xref:System.Xml.Linq.XName> parameter.</span></span> <span data-ttu-id="e596d-119">Nicméně, občas pracovat přímo se <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="e596d-119">However, you rarely work directly with an <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="e596d-120"><xref:System.Xml.Linq.XName>obsahuje implicitní převod z řetězce.</span><span class="sxs-lookup"><span data-stu-id="e596d-120"><xref:System.Xml.Linq.XName> contains an implicit conversion from string.</span></span>  
  
 <span data-ttu-id="e596d-121">Další informace naleznete v tématu <xref:System.Xml.Linq.XNamespace> a <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="e596d-121">For more information, see <xref:System.Xml.Linq.XNamespace> and <xref:System.Xml.Linq.XName>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e596d-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="e596d-122">See Also</span></span>  
 [<span data-ttu-id="e596d-123">Práce s obory názvů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e596d-123">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
