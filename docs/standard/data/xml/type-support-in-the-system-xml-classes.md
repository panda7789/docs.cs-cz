---
title: Podpora typu v třídách System.Xml
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
ms.openlocfilehash: 8ceda15cb8463db3e81260529ebb1e3a67a0c1af
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84283296"
---
# <a name="type-support-in-the-systemxml-classes"></a><span data-ttu-id="be614-102">Podpora typu v třídách System.Xml</span><span class="sxs-lookup"><span data-stu-id="be614-102">Type Support in the System.Xml Classes</span></span>
<span data-ttu-id="be614-103">V .NET Framework verze 2,0 byly základní třídy XML vylepšeny, aby zahrnovaly funkce podpory typů.</span><span class="sxs-lookup"><span data-stu-id="be614-103">In the .NET Framework version 2.0, the core XML classes have been enhanced to include type support features.</span></span> <span data-ttu-id="be614-104"><xref:System.Xml.XmlReader>Třídy, <xref:System.Xml.XmlWriter> a <xref:System.Xml.XPath.XPathNavigator> zahrnují funkce podpory typů včetně možnosti konverze mezi typy schémat XML a typy modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="be614-104">The <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes include type support features including the ability to convert between XML Schema types and common language runtime (CLR) types.</span></span>  
  
 <span data-ttu-id="be614-105">V .NET Framework verze 2,0 byly <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> <xref:System.Xml.XPath.XPathNavigator> vylepšeny třídy, a, aby zahrnovaly funkce podpory typů.</span><span class="sxs-lookup"><span data-stu-id="be614-105">In the .NET Framework version 2.0, the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes have been enhanced to include type support features.</span></span>  
  
- <span data-ttu-id="be614-106"><xref:System.Xml.XmlReader>Třídy a <xref:System.Xml.XPath.XPathNavigator> zahrnují vlastnost **SchemaInfo** , která vrací informace o schématu v uzlu.</span><span class="sxs-lookup"><span data-stu-id="be614-106">The <xref:System.Xml.XmlReader> and <xref:System.Xml.XPath.XPathNavigator> classes each include a **SchemaInfo** property that returns the schema information on a node.</span></span>  
  
- <span data-ttu-id="be614-107">**ReadContentAs** a **metody ReadElementContentAs** a metody <xref:System.Xml.XmlReader> třídy čtou textovou hodnotu a převedou je na hodnotu CLR v jediném volání metody.</span><span class="sxs-lookup"><span data-stu-id="be614-107">The **ReadContentAs** and **ReadElementContentAs** and methods on the <xref:System.Xml.XmlReader> class read a text value and convert it to a CLR value in a single method call.</span></span>  
  
- <span data-ttu-id="be614-108"><xref:System.Xml.XmlWriter.WriteValue%2A>Metoda na <xref:System.Xml.XmlWriter> třídě PŘEVEDE typ CLR na typ schématu XML při zapisování XML.</span><span class="sxs-lookup"><span data-stu-id="be614-108">The <xref:System.Xml.XmlWriter.WriteValue%2A> method on the <xref:System.Xml.XmlWriter> class converts a CLR type to an XML Schema type when writing out XML.</span></span>  
  
- <span data-ttu-id="be614-109">**ValueAs** a <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> třídy vracejí hodnotu uzlu a převedou je na hodnotu CLR v rámci jediného volání metody.</span><span class="sxs-lookup"><span data-stu-id="be614-109">The **ValueAs** and <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> properties on the <xref:System.Xml.XPath.XPathNavigator> class return a node value and convert it to a CLR value in a single method call.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="be614-110">V .NET Framework verze 1,0 <xref:System.Xml.XmlConvert> byla třída nutná k převedení mezi schématy XML a typy CLR.</span><span class="sxs-lookup"><span data-stu-id="be614-110">In the .NET Framework version 1.0 the <xref:System.Xml.XmlConvert> class was needed to convert between XML Schema and CLR types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="be614-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="be614-111">In This Section</span></span>  
 [<span data-ttu-id="be614-112">Mapování datových typů XML na typy CLR</span><span class="sxs-lookup"><span data-stu-id="be614-112">Mapping XML Data Types to CLR Types</span></span>](mapping-xml-data-types-to-clr-types.md)  
 <span data-ttu-id="be614-113">Popisuje výchozí mapování datových typů XML na typy CLR.</span><span class="sxs-lookup"><span data-stu-id="be614-113">Describes the default mappings of XML data types to CLR types.</span></span>  
  
 [<span data-ttu-id="be614-114">Poznámky k implementaci podpory typů XML</span><span class="sxs-lookup"><span data-stu-id="be614-114">XML Type Support Implementation Notes</span></span>](xml-type-support-implementation-notes.md)  
 <span data-ttu-id="be614-115">Popisuje některé podrobnosti implementace podpory typu.</span><span class="sxs-lookup"><span data-stu-id="be614-115">Discusses some of the type support implementation details.</span></span>  
  
 [<span data-ttu-id="be614-116">Převod datových typů XML</span><span class="sxs-lookup"><span data-stu-id="be614-116">Conversion of XML Data Types</span></span>](conversion-of-xml-data-types.md)  
 <span data-ttu-id="be614-117">Popisuje, jak použít <xref:System.Xml.XmlConvert> třídu pro převod mezi typy schématu XML a CLR.</span><span class="sxs-lookup"><span data-stu-id="be614-117">Describes how to use the <xref:System.Xml.XmlConvert> class to convert between XML Schema and CLR types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="be614-118">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="be614-118">Related Sections</span></span>  
 [<span data-ttu-id="be614-119">Přístup k datům XML silného typu pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="be614-119">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](accessing-strongly-typed-xml-data-using-xpathnavigator.md)
