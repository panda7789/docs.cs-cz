---
title: Podpora typu v třídách System.Xml
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
ms.openlocfilehash: cec47d40a0353639bc17b880265f7c15f2f53ac4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710099"
---
# <a name="type-support-in-the-systemxml-classes"></a><span data-ttu-id="52ae3-102">Podpora typu v třídách System.Xml</span><span class="sxs-lookup"><span data-stu-id="52ae3-102">Type Support in the System.Xml Classes</span></span>
<span data-ttu-id="52ae3-103">V .NET Framework verze 2,0 byly základní třídy XML vylepšeny, aby zahrnovaly funkce podpory typů.</span><span class="sxs-lookup"><span data-stu-id="52ae3-103">In the .NET Framework version 2.0, the core XML classes have been enhanced to include type support features.</span></span> <span data-ttu-id="52ae3-104">Třídy <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>a <xref:System.Xml.XPath.XPathNavigator> zahrnují funkce podpory typů včetně možnosti konverze mezi typy schémat XML a typy modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="52ae3-104">The <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes include type support features including the ability to convert between XML Schema types and common language runtime (CLR) types.</span></span>  
  
 <span data-ttu-id="52ae3-105">V .NET Framework verze 2,0 byly vylepšeny třídy <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>a <xref:System.Xml.XPath.XPathNavigator>, aby zahrnovaly funkce podpory typů.</span><span class="sxs-lookup"><span data-stu-id="52ae3-105">In the .NET Framework version 2.0, the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes have been enhanced to include type support features.</span></span>  
  
- <span data-ttu-id="52ae3-106">Mezi třídy <xref:System.Xml.XmlReader> a <xref:System.Xml.XPath.XPathNavigator> patří vlastnost **SchemaInfo** , která vrací informace o schématu v uzlu.</span><span class="sxs-lookup"><span data-stu-id="52ae3-106">The <xref:System.Xml.XmlReader> and <xref:System.Xml.XPath.XPathNavigator> classes each include a **SchemaInfo** property that returns the schema information on a node.</span></span>  
  
- <span data-ttu-id="52ae3-107">**ReadContentAs** a **metody ReadElementContentAs** a metody třídy <xref:System.Xml.XmlReader> čtou textovou hodnotu a převedou je na hodnotu CLR v rámci jediné volání metody.</span><span class="sxs-lookup"><span data-stu-id="52ae3-107">The **ReadContentAs** and **ReadElementContentAs** and methods on the <xref:System.Xml.XmlReader> class read a text value and convert it to a CLR value in a single method call.</span></span>  
  
- <span data-ttu-id="52ae3-108">Metoda <xref:System.Xml.XmlWriter.WriteValue%2A> třídy <xref:System.Xml.XmlWriter> při zapisování XML převede typ CLR na typ schématu XML.</span><span class="sxs-lookup"><span data-stu-id="52ae3-108">The <xref:System.Xml.XmlWriter.WriteValue%2A> method on the <xref:System.Xml.XmlWriter> class converts a CLR type to an XML Schema type when writing out XML.</span></span>  
  
- <span data-ttu-id="52ae3-109">Vlastnosti **ValueAs** a <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> třídy <xref:System.Xml.XPath.XPathNavigator> vracejí hodnotu uzlu a převedou je na hodnotu CLR v rámci jediného volání metody.</span><span class="sxs-lookup"><span data-stu-id="52ae3-109">The **ValueAs** and <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> properties on the <xref:System.Xml.XPath.XPathNavigator> class return a node value and convert it to a CLR value in a single method call.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52ae3-110">Ve .NET Framework verze 1,0 byla <xref:System.Xml.XmlConvert> třída nutná k převodu mezi schématy XML a typy CLR.</span><span class="sxs-lookup"><span data-stu-id="52ae3-110">In the .NET Framework version 1.0 the <xref:System.Xml.XmlConvert> class was needed to convert between XML Schema and CLR types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="52ae3-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="52ae3-111">In This Section</span></span>  
 [<span data-ttu-id="52ae3-112">Mapování datových typů XML na typy CLR</span><span class="sxs-lookup"><span data-stu-id="52ae3-112">Mapping XML Data Types to CLR Types</span></span>](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 <span data-ttu-id="52ae3-113">Popisuje výchozí mapování datových typů XML na typy CLR.</span><span class="sxs-lookup"><span data-stu-id="52ae3-113">Describes the default mappings of XML data types to CLR types.</span></span>  
  
 [<span data-ttu-id="52ae3-114">Poznámky k implementaci podpory typů XML</span><span class="sxs-lookup"><span data-stu-id="52ae3-114">XML Type Support Implementation Notes</span></span>](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 <span data-ttu-id="52ae3-115">Popisuje některé podrobnosti implementace podpory typu.</span><span class="sxs-lookup"><span data-stu-id="52ae3-115">Discusses some of the type support implementation details.</span></span>  
  
 [<span data-ttu-id="52ae3-116">Převod datových typů XML</span><span class="sxs-lookup"><span data-stu-id="52ae3-116">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 <span data-ttu-id="52ae3-117">Popisuje, jak použít třídu <xref:System.Xml.XmlConvert> k převedení mezi schématy XML a typy CLR.</span><span class="sxs-lookup"><span data-stu-id="52ae3-117">Describes how to use the <xref:System.Xml.XmlConvert> class to convert between XML Schema and CLR types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="52ae3-118">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="52ae3-118">Related Sections</span></span>  
 [<span data-ttu-id="52ae3-119">Přístup k datům XML silného typu pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="52ae3-119">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
