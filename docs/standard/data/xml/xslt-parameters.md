---
title: Parametry XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef57d16c52100398919563205a97205be3c5dd7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570626"
---
# <a name="xslt-parameters"></a><span data-ttu-id="4db22-102">Parametry XSLT</span><span class="sxs-lookup"><span data-stu-id="4db22-102">XSLT Parameters</span></span>
<span data-ttu-id="4db22-103">Parametry XSLT jsou přidány do <xref:System.Xml.Xsl.XsltArgumentList> pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="4db22-103">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="4db22-104">Kvalifikovaný název a identifikátor URI oboru názvů jsou přidruženy k objektu parametru v daném čase.</span><span class="sxs-lookup"><span data-stu-id="4db22-104">A qualified name and namespace URI are associated with the parameter object at that time.</span></span>  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="4db22-105">Použití parametru XSLT</span><span class="sxs-lookup"><span data-stu-id="4db22-105">To use an XSLT parameter</span></span>  
  
1.  <span data-ttu-id="4db22-106">Vytvoření <xref:System.Xml.Xsl.XsltArgumentList> objektu a přidejte parametr pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="4db22-106">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the parameter using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span>  
  
2.  <span data-ttu-id="4db22-107">Parametr volejte z této šablony.</span><span class="sxs-lookup"><span data-stu-id="4db22-107">Call the parameter from the style sheet.</span></span>  
  
3.  <span data-ttu-id="4db22-108">Předat <xref:System.Xml.Xsl.XsltArgumentList> do objektu <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="4db22-108">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="parameter-types"></a><span data-ttu-id="4db22-109">Typy parametrů</span><span class="sxs-lookup"><span data-stu-id="4db22-109">Parameter Types</span></span>  
 <span data-ttu-id="4db22-110">Objekt parametr by měl odpovídat typu W3C.</span><span class="sxs-lookup"><span data-stu-id="4db22-110">The parameter object should correspond to a W3C type.</span></span> <span data-ttu-id="4db22-111">Následující tabulka uvádí odpovídající typy W3C ekvivalentní třídy rozhraní Microsoft .NET (typ), a zda je typ W3C XPath typ nebo typ XSLT.</span><span class="sxs-lookup"><span data-stu-id="4db22-111">The following table shows the corresponding W3C types, the equivalent Microsoft .NET classes (type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="4db22-112">Typ W3C</span><span class="sxs-lookup"><span data-stu-id="4db22-112">W3C type</span></span>|<span data-ttu-id="4db22-113">Ekvivalentní třída .NET (typ)</span><span class="sxs-lookup"><span data-stu-id="4db22-113">Equivalent .NET class (type)</span></span>|<span data-ttu-id="4db22-114">Typ XPath nebo XSLT</span><span class="sxs-lookup"><span data-stu-id="4db22-114">XPath or XSLT type</span></span>|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="4db22-115">XPath</span><span class="sxs-lookup"><span data-stu-id="4db22-115">XPath</span></span>|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="4db22-116">XPath</span><span class="sxs-lookup"><span data-stu-id="4db22-116">XPath</span></span>|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="4db22-117">XPath</span><span class="sxs-lookup"><span data-stu-id="4db22-117">XPath</span></span>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="4db22-118">XSLT</span><span class="sxs-lookup"><span data-stu-id="4db22-118">XSLT</span></span>|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="4db22-119">XPath</span><span class="sxs-lookup"><span data-stu-id="4db22-119">XPath</span></span>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> <span data-ttu-id="4db22-120">**[] Objektem XPathNavigator nastaveným na**</span><span class="sxs-lookup"><span data-stu-id="4db22-120">**XPathNavigator[]**</span></span>|<span data-ttu-id="4db22-121">XPath</span><span class="sxs-lookup"><span data-stu-id="4db22-121">XPath</span></span>|  
  
 <span data-ttu-id="4db22-122">\* Jde o ekvivalent sada uzlů, který obsahuje jeden uzel.</span><span class="sxs-lookup"><span data-stu-id="4db22-122">\*This is equivalent to a node set that contains a single node.</span></span>  
  
 <span data-ttu-id="4db22-123">Pokud objekt parametr není jedním z výše uvedených tříd, převede se podle následujících pravidel.</span><span class="sxs-lookup"><span data-stu-id="4db22-123">If the parameter object is not one of the above classes, it is converted according to the following rules.</span></span> <span data-ttu-id="4db22-124">Common language runtime (CLR) číselnými typy jsou převedeny na <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="4db22-124">Common language runtime (CLR) numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="4db22-125"><xref:System.DateTime> Typ je převeden na <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="4db22-125">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="4db22-126"><xref:System.Xml.XPath.IXPathNavigable> typy budou převedené na <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="4db22-126"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="4db22-127">**[] Objektem XPathNavigator nastaveným na** jsou převedeny na <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="4db22-127">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="4db22-128">Všechny ostatní typy vyvolána chyba.</span><span class="sxs-lookup"><span data-stu-id="4db22-128">All other types throw an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4db22-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="4db22-129">Example</span></span>  
 <span data-ttu-id="4db22-130">Následující příklad používá <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metodu pro vytvoření parametr pro uložení počítané datum slevy.</span><span class="sxs-lookup"><span data-stu-id="4db22-130">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold calculated discount date.</span></span> <span data-ttu-id="4db22-131">Datum slevy je vypočítána na 20 dní od data pořadí.</span><span class="sxs-lookup"><span data-stu-id="4db22-131">The discount date is calculated to be 20 days from the order date.</span></span>  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="4db22-132">Vstup</span><span class="sxs-lookup"><span data-stu-id="4db22-132">Input</span></span>  
  
##### <a name="orderxml"></a><span data-ttu-id="4db22-133">Order.XML</span><span class="sxs-lookup"><span data-stu-id="4db22-133">order.xml</span></span>  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a><span data-ttu-id="4db22-134">discount.xsl</span><span class="sxs-lookup"><span data-stu-id="4db22-134">discount.xsl</span></span>  
 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="4db22-135">Výstup</span><span class="sxs-lookup"><span data-stu-id="4db22-135">Output</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4db22-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="4db22-136">See Also</span></span>  
 [<span data-ttu-id="4db22-137">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="4db22-137">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
