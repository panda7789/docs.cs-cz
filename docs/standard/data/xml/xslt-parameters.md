---
title: Parametry XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
ms.openlocfilehash: 7651360b375071c48ba0d23b64881ac794e51e86
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282529"
---
# <a name="xslt-parameters"></a><span data-ttu-id="13261-102">Parametry XSLT</span><span class="sxs-lookup"><span data-stu-id="13261-102">XSLT Parameters</span></span>
<span data-ttu-id="13261-103">Parametry XSLT jsou přidány do <xref:System.Xml.Xsl.XsltArgumentList> <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metody pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="13261-103">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="13261-104">Úplný název a identifikátor URI oboru názvů jsou v daném čase přidruženy k objektu Parameter.</span><span class="sxs-lookup"><span data-stu-id="13261-104">A qualified name and namespace URI are associated with the parameter object at that time.</span></span>  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="13261-105">Použití parametru XSLT</span><span class="sxs-lookup"><span data-stu-id="13261-105">To use an XSLT parameter</span></span>  
  
1. <span data-ttu-id="13261-106">Vytvořte <xref:System.Xml.Xsl.XsltArgumentList> objekt a přidejte parametr pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="13261-106">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the parameter using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span>  
  
2. <span data-ttu-id="13261-107">Zavolejte parametr ze seznamu stylů.</span><span class="sxs-lookup"><span data-stu-id="13261-107">Call the parameter from the style sheet.</span></span>  
  
3. <span data-ttu-id="13261-108">Předat <xref:System.Xml.Xsl.XsltArgumentList> objekt <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metodě.</span><span class="sxs-lookup"><span data-stu-id="13261-108">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="parameter-types"></a><span data-ttu-id="13261-109">Typy parametrů</span><span class="sxs-lookup"><span data-stu-id="13261-109">Parameter Types</span></span>  
 <span data-ttu-id="13261-110">Objekt Parameter by měl odpovídat typu W3C.</span><span class="sxs-lookup"><span data-stu-id="13261-110">The parameter object should correspond to a W3C type.</span></span> <span data-ttu-id="13261-111">V následující tabulce jsou uvedeny odpovídající typy W3C, ekvivalentní třídy Microsoft .NET (typ) a zda typ W3C je typ XPath nebo typ XSLT.</span><span class="sxs-lookup"><span data-stu-id="13261-111">The following table shows the corresponding W3C types, the equivalent Microsoft .NET classes (type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="13261-112">Typ W3C</span><span class="sxs-lookup"><span data-stu-id="13261-112">W3C type</span></span>|<span data-ttu-id="13261-113">Ekvivalentní třída .NET (typ)</span><span class="sxs-lookup"><span data-stu-id="13261-113">Equivalent .NET class (type)</span></span>|<span data-ttu-id="13261-114">Typ XPath nebo XSLT</span><span class="sxs-lookup"><span data-stu-id="13261-114">XPath or XSLT type</span></span>|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="13261-115">XPath</span><span class="sxs-lookup"><span data-stu-id="13261-115">XPath</span></span>|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="13261-116">XPath</span><span class="sxs-lookup"><span data-stu-id="13261-116">XPath</span></span>|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="13261-117">XPath</span><span class="sxs-lookup"><span data-stu-id="13261-117">XPath</span></span>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="13261-118">SOUBORU</span><span class="sxs-lookup"><span data-stu-id="13261-118">XSLT</span></span>|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="13261-119">XPath</span><span class="sxs-lookup"><span data-stu-id="13261-119">XPath</span></span>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> <span data-ttu-id="13261-120">**XPathNavigator []**</span><span class="sxs-lookup"><span data-stu-id="13261-120">**XPathNavigator[]**</span></span>|<span data-ttu-id="13261-121">XPath</span><span class="sxs-lookup"><span data-stu-id="13261-121">XPath</span></span>|  
  
 <span data-ttu-id="13261-122">\* To je ekvivalent sady uzlů, která obsahuje jeden uzel.</span><span class="sxs-lookup"><span data-stu-id="13261-122">\*This is equivalent to a node set that contains a single node.</span></span>  
  
 <span data-ttu-id="13261-123">Pokud objekt Parameter není jedna z výše uvedených tříd, je převedena podle následujících pravidel.</span><span class="sxs-lookup"><span data-stu-id="13261-123">If the parameter object is not one of the above classes, it is converted according to the following rules.</span></span> <span data-ttu-id="13261-124">Číselné typy modulu CLR (Common Language Runtime) jsou převedeny na <xref:System.Double> .</span><span class="sxs-lookup"><span data-stu-id="13261-124">Common language runtime (CLR) numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="13261-125"><xref:System.DateTime>Typ je převeden na <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="13261-125">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="13261-126"><xref:System.Xml.XPath.IXPathNavigable>typy jsou převedeny na <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="13261-126"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="13261-127">**Prvek XPathNavigator []** je převeden na <xref:System.Xml.XPath.XPathNodeIterator> .</span><span class="sxs-lookup"><span data-stu-id="13261-127">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="13261-128">Všechny ostatní typy vyvolávají chybu.</span><span class="sxs-lookup"><span data-stu-id="13261-128">All other types throw an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13261-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="13261-129">Example</span></span>  
 <span data-ttu-id="13261-130">Následující příklad používá <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metodu k vytvoření parametru pro uchování počítaného data slevy.</span><span class="sxs-lookup"><span data-stu-id="13261-130">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold calculated discount date.</span></span> <span data-ttu-id="13261-131">Datum slevy se počítá jako 20 dní od data objednávky.</span><span class="sxs-lookup"><span data-stu-id="13261-131">The discount date is calculated to be 20 days from the order date.</span></span>  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="13261-132">Vstup</span><span class="sxs-lookup"><span data-stu-id="13261-132">Input</span></span>  
  
##### <a name="orderxml"></a><span data-ttu-id="13261-133">Order. XML</span><span class="sxs-lookup"><span data-stu-id="13261-133">order.xml</span></span>  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a><span data-ttu-id="13261-134">sleva. xsl</span><span class="sxs-lookup"><span data-stu-id="13261-134">discount.xsl</span></span>  
 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="13261-135">Výstup</span><span class="sxs-lookup"><span data-stu-id="13261-135">Output</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a><span data-ttu-id="13261-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="13261-136">See also</span></span>

- [<span data-ttu-id="13261-137">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="13261-137">XSLT Transformations</span></span>](xslt-transformations.md)
