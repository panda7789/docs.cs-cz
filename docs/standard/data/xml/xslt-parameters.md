---
title: Parametry XSLT
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b16ad921e5b16ab7564b2ceedab91c6b6073537d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="xslt-parameters"></a><span data-ttu-id="fd622-102">Parametry XSLT</span><span class="sxs-lookup"><span data-stu-id="fd622-102">XSLT Parameters</span></span>
<span data-ttu-id="fd622-103">Parametry XSLT jsou přidány do <xref:System.Xml.Xsl.XsltArgumentList> pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="fd622-103">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="fd622-104">Kvalifikovaný název a identifikátor URI oboru názvů jsou přidruženy k objektu parametru v daném čase.</span><span class="sxs-lookup"><span data-stu-id="fd622-104">A qualified name and namespace URI are associated with the parameter object at that time.</span></span>  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="fd622-105">Použití parametru XSLT</span><span class="sxs-lookup"><span data-stu-id="fd622-105">To use an XSLT parameter</span></span>  
  
1.  <span data-ttu-id="fd622-106">Vytvoření <xref:System.Xml.Xsl.XsltArgumentList> objektu a přidejte parametr pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="fd622-106">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the parameter using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span>  
  
2.  <span data-ttu-id="fd622-107">Parametr volejte z této šablony.</span><span class="sxs-lookup"><span data-stu-id="fd622-107">Call the parameter from the style sheet.</span></span>  
  
3.  <span data-ttu-id="fd622-108">Předat <xref:System.Xml.Xsl.XsltArgumentList> do objektu <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="fd622-108">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="parameter-types"></a><span data-ttu-id="fd622-109">Typy parametrů</span><span class="sxs-lookup"><span data-stu-id="fd622-109">Parameter Types</span></span>  
 <span data-ttu-id="fd622-110">Objekt parametr by měl odpovídat typu W3C.</span><span class="sxs-lookup"><span data-stu-id="fd622-110">The parameter object should correspond to a W3C type.</span></span> <span data-ttu-id="fd622-111">Následující tabulka uvádí odpovídající typy W3C ekvivalentní třídy rozhraní Microsoft .NET (typ), a zda je typ W3C XPath typ nebo typ XSLT.</span><span class="sxs-lookup"><span data-stu-id="fd622-111">The following table shows the corresponding W3C types, the equivalent Microsoft .NET classes (type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="fd622-112">Typ W3C</span><span class="sxs-lookup"><span data-stu-id="fd622-112">W3C type</span></span>|<span data-ttu-id="fd622-113">Ekvivalentní třída .NET (typ)</span><span class="sxs-lookup"><span data-stu-id="fd622-113">Equivalent .NET class (type)</span></span>|<span data-ttu-id="fd622-114">Typ XPath nebo XSLT</span><span class="sxs-lookup"><span data-stu-id="fd622-114">XPath or XSLT type</span></span>|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="fd622-115">XPath</span><span class="sxs-lookup"><span data-stu-id="fd622-115">XPath</span></span>|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="fd622-116">XPath</span><span class="sxs-lookup"><span data-stu-id="fd622-116">XPath</span></span>|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="fd622-117">XPath</span><span class="sxs-lookup"><span data-stu-id="fd622-117">XPath</span></span>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="fd622-118">XSLT</span><span class="sxs-lookup"><span data-stu-id="fd622-118">XSLT</span></span>|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="fd622-119">XPath</span><span class="sxs-lookup"><span data-stu-id="fd622-119">XPath</span></span>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> <span data-ttu-id="fd622-120">**[] Objektem XPathNavigator nastaveným na**</span><span class="sxs-lookup"><span data-stu-id="fd622-120">**XPathNavigator[]**</span></span>|<span data-ttu-id="fd622-121">XPath</span><span class="sxs-lookup"><span data-stu-id="fd622-121">XPath</span></span>|  
  
 <span data-ttu-id="fd622-122">* Jde o ekvivalent sada uzlů, který obsahuje jeden uzel.</span><span class="sxs-lookup"><span data-stu-id="fd622-122">*This is equivalent to a node set that contains a single node.</span></span>  
  
 <span data-ttu-id="fd622-123">Pokud objekt parametr není jedním z výše uvedených tříd, převede se podle následujících pravidel.</span><span class="sxs-lookup"><span data-stu-id="fd622-123">If the parameter object is not one of the above classes, it is converted according to the following rules.</span></span> <span data-ttu-id="fd622-124">Common language runtime (CLR) číselnými typy jsou převedeny na <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="fd622-124">Common language runtime (CLR) numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="fd622-125"><xref:System.DateTime> Typ je převeden na <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="fd622-125">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="fd622-126"><xref:System.Xml.XPath.IXPathNavigable>typy budou převedené na <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="fd622-126"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="fd622-127">**[] Objektem XPathNavigator nastaveným na** jsou převedeny na <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="fd622-127">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="fd622-128">Všechny ostatní typy vyvolána chyba.</span><span class="sxs-lookup"><span data-stu-id="fd622-128">All other types throw an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd622-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="fd622-129">Example</span></span>  
 <span data-ttu-id="fd622-130">Následující příklad používá <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metodu pro vytvoření parametr pro uložení počítané datum slevy.</span><span class="sxs-lookup"><span data-stu-id="fd622-130">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold calculated discount date.</span></span> <span data-ttu-id="fd622-131">Datum slevy je vypočítána na 20 dní od data pořadí.</span><span class="sxs-lookup"><span data-stu-id="fd622-131">The discount date is calculated to be 20 days from the order date.</span></span>  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="fd622-132">Vstup</span><span class="sxs-lookup"><span data-stu-id="fd622-132">Input</span></span>  
  
##### <a name="orderxml"></a><span data-ttu-id="fd622-133">Order.XML</span><span class="sxs-lookup"><span data-stu-id="fd622-133">order.xml</span></span>  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a><span data-ttu-id="fd622-134">discount.xsl</span><span class="sxs-lookup"><span data-stu-id="fd622-134">discount.xsl</span></span>  
 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="fd622-135">Výstup</span><span class="sxs-lookup"><span data-stu-id="fd622-135">Output</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd622-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd622-136">See Also</span></span>  
 [<span data-ttu-id="fd622-137">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="fd622-137">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
