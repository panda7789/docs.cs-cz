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
ms.openlocfilehash: 63a394bd30b3586f084dc1a2320fa9133da19b64
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44037104"
---
# <a name="xslt-parameters"></a><span data-ttu-id="91125-102">Parametry XSLT</span><span class="sxs-lookup"><span data-stu-id="91125-102">XSLT Parameters</span></span>
<span data-ttu-id="91125-103">Parametry XSLT se přidají do <xref:System.Xml.Xsl.XsltArgumentList> pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="91125-103">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="91125-104">Úplný název a identifikátor URI oboru názvů jsou spojeny s parametrem objektu v daném čase.</span><span class="sxs-lookup"><span data-stu-id="91125-104">A qualified name and namespace URI are associated with the parameter object at that time.</span></span>  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="91125-105">Chcete-li použít parametr XSLT</span><span class="sxs-lookup"><span data-stu-id="91125-105">To use an XSLT parameter</span></span>  
  
1.  <span data-ttu-id="91125-106">Vytvoření <xref:System.Xml.Xsl.XsltArgumentList> objektu a přidejte parametr pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="91125-106">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the parameter using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span>  
  
2.  <span data-ttu-id="91125-107">Volání parametru z šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="91125-107">Call the parameter from the style sheet.</span></span>  
  
3.  <span data-ttu-id="91125-108">Předání <xref:System.Xml.Xsl.XsltArgumentList> objektu <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="91125-108">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="parameter-types"></a><span data-ttu-id="91125-109">Typy parametrů</span><span class="sxs-lookup"><span data-stu-id="91125-109">Parameter Types</span></span>  
 <span data-ttu-id="91125-110">Parametr objektu by měl odpovídat typu W3C.</span><span class="sxs-lookup"><span data-stu-id="91125-110">The parameter object should correspond to a W3C type.</span></span> <span data-ttu-id="91125-111">Následující tabulka uvádí odpovídající typy W3C odpovídající třídy rozhraní Microsoft .NET (typ), a určuje, zda je typ W3C XPath typ nebo typ XSLT.</span><span class="sxs-lookup"><span data-stu-id="91125-111">The following table shows the corresponding W3C types, the equivalent Microsoft .NET classes (type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="91125-112">Typ W3C</span><span class="sxs-lookup"><span data-stu-id="91125-112">W3C type</span></span>|<span data-ttu-id="91125-113">Ekvivalentní třída rozhraní .NET (typ)</span><span class="sxs-lookup"><span data-stu-id="91125-113">Equivalent .NET class (type)</span></span>|<span data-ttu-id="91125-114">Typ XPath nebo XSLT</span><span class="sxs-lookup"><span data-stu-id="91125-114">XPath or XSLT type</span></span>|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="91125-115">XPath</span><span class="sxs-lookup"><span data-stu-id="91125-115">XPath</span></span>|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="91125-116">XPath</span><span class="sxs-lookup"><span data-stu-id="91125-116">XPath</span></span>|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="91125-117">XPath</span><span class="sxs-lookup"><span data-stu-id="91125-117">XPath</span></span>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="91125-118">XSLT</span><span class="sxs-lookup"><span data-stu-id="91125-118">XSLT</span></span>|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="91125-119">XPath</span><span class="sxs-lookup"><span data-stu-id="91125-119">XPath</span></span>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> <span data-ttu-id="91125-120">**[] Objektem XPathNavigator nastaveným na**</span><span class="sxs-lookup"><span data-stu-id="91125-120">**XPathNavigator[]**</span></span>|<span data-ttu-id="91125-121">XPath</span><span class="sxs-lookup"><span data-stu-id="91125-121">XPath</span></span>|  
  
 <span data-ttu-id="91125-122">\* Toto je shodné s sadu uzlu, která obsahuje jeden uzel.</span><span class="sxs-lookup"><span data-stu-id="91125-122">\*This is equivalent to a node set that contains a single node.</span></span>  
  
 <span data-ttu-id="91125-123">Pokud parametr objektu není jeden z výše uvedených tříd, je převeden podle následujících pravidel.</span><span class="sxs-lookup"><span data-stu-id="91125-123">If the parameter object is not one of the above classes, it is converted according to the following rules.</span></span> <span data-ttu-id="91125-124">Common language runtime (CLR) číselné typy jsou převedeny na <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="91125-124">Common language runtime (CLR) numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="91125-125"><xref:System.DateTime> Typ je převeden na <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="91125-125">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="91125-126"><xref:System.Xml.XPath.IXPathNavigable> typy budou převedené na <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="91125-126"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="91125-127">**[] Objektem XPathNavigator nastaveným na** je převedena na <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="91125-127">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="91125-128">Všechny ostatní typy vyvolat chybu.</span><span class="sxs-lookup"><span data-stu-id="91125-128">All other types throw an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91125-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="91125-129">Example</span></span>  
 <span data-ttu-id="91125-130">V následujícím příkladu <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metodu pro vytvoření parametr pro uložení vypočítané datum slevy.</span><span class="sxs-lookup"><span data-stu-id="91125-130">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold calculated discount date.</span></span> <span data-ttu-id="91125-131">Slevy se počítá na 20 dní od data objednávky.</span><span class="sxs-lookup"><span data-stu-id="91125-131">The discount date is calculated to be 20 days from the order date.</span></span>  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="91125-132">Vstup</span><span class="sxs-lookup"><span data-stu-id="91125-132">Input</span></span>  
  
##### <a name="orderxml"></a><span data-ttu-id="91125-133">Order.XML</span><span class="sxs-lookup"><span data-stu-id="91125-133">order.xml</span></span>  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a><span data-ttu-id="91125-134">discount.xsl</span><span class="sxs-lookup"><span data-stu-id="91125-134">discount.xsl</span></span>  
 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="91125-135">Výstup</span><span class="sxs-lookup"><span data-stu-id="91125-135">Output</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a><span data-ttu-id="91125-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91125-136">See also</span></span>

- [<span data-ttu-id="91125-137">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="91125-137">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
