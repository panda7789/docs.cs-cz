---
title: Podpora typu v třídách System.Xml
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bb47eec7153624b1822b6393bb4a1621b1cd63db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026884"
---
# <a name="type-support-in-the-systemxml-classes"></a><span data-ttu-id="9b94a-102">Podpora typu v třídách System.Xml</span><span class="sxs-lookup"><span data-stu-id="9b94a-102">Type Support in the System.Xml Classes</span></span>
<span data-ttu-id="9b94a-103">V rozhraní .NET Framework verze 2.0 mají základní třídy XML vylepšené a zahrnují typ funkce podpory.</span><span class="sxs-lookup"><span data-stu-id="9b94a-103">In the .NET Framework version 2.0, the core XML classes have been enhanced to include type support features.</span></span> <span data-ttu-id="9b94a-104"><xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, A <xref:System.Xml.XPath.XPathNavigator> třídy zahrnují funkce podpory typu, včetně možnosti pro převod mezi typy schémat XML a běžné language runtime (CLR) typy.</span><span class="sxs-lookup"><span data-stu-id="9b94a-104">The <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes include type support features including the ability to convert between XML Schema types and common language runtime (CLR) types.</span></span>  
  
 <span data-ttu-id="9b94a-105">V rozhraní .NET Framework verze 2.0 <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, a <xref:System.Xml.XPath.XPathNavigator> třídy vylepšené a zahrnují typ funkce podpory.</span><span class="sxs-lookup"><span data-stu-id="9b94a-105">In the .NET Framework version 2.0, the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes have been enhanced to include type support features.</span></span>  
  
- <span data-ttu-id="9b94a-106"><xref:System.Xml.XmlReader> a <xref:System.Xml.XPath.XPathNavigator> třídy každý zahrnují **položka SchemaInfo** vlastnost, která vrátí informace o schématu na uzlu.</span><span class="sxs-lookup"><span data-stu-id="9b94a-106">The <xref:System.Xml.XmlReader> and <xref:System.Xml.XPath.XPathNavigator> classes each include a **SchemaInfo** property that returns the schema information on a node.</span></span>  
  
- <span data-ttu-id="9b94a-107">**ReadContentAs** a **ReadElementContentAs** a metody <xref:System.Xml.XmlReader> třídy číst textové hodnoty a převeďte jej na hodnotu CLR v rámci jednoho volání metody.</span><span class="sxs-lookup"><span data-stu-id="9b94a-107">The **ReadContentAs** and **ReadElementContentAs** and methods on the <xref:System.Xml.XmlReader> class read a text value and convert it to a CLR value in a single method call.</span></span>  
  
- <span data-ttu-id="9b94a-108"><xref:System.Xml.XmlWriter.WriteValue%2A> Metodu <xref:System.Xml.XmlWriter> třídy při výpisu XML převádí typ CLR na typ schématu XML.</span><span class="sxs-lookup"><span data-stu-id="9b94a-108">The <xref:System.Xml.XmlWriter.WriteValue%2A> method on the <xref:System.Xml.XmlWriter> class converts a CLR type to an XML Schema type when writing out XML.</span></span>  
  
- <span data-ttu-id="9b94a-109">**ValueAs** a <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> třídy vrátit hodnotu uzlu a převeďte jej na hodnotu CLR v rámci jednoho volání metody.</span><span class="sxs-lookup"><span data-stu-id="9b94a-109">The **ValueAs** and <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> properties on the <xref:System.Xml.XPath.XPathNavigator> class return a node value and convert it to a CLR value in a single method call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b94a-110">V rozhraní .NET Framework verze 1.0 <xref:System.Xml.XmlConvert> třídy byly potřebné pro převod mezi typy schématu XML a CLR.</span><span class="sxs-lookup"><span data-stu-id="9b94a-110">In the .NET Framework version 1.0 the <xref:System.Xml.XmlConvert> class was needed to convert between XML Schema and CLR types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b94a-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9b94a-111">In This Section</span></span>  
 [<span data-ttu-id="9b94a-112">Mapování datových typů XML na typy CLR</span><span class="sxs-lookup"><span data-stu-id="9b94a-112">Mapping XML Data Types to CLR Types</span></span>](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 <span data-ttu-id="9b94a-113">Popisuje výchozí mapování datových typů XML na typy CLR.</span><span class="sxs-lookup"><span data-stu-id="9b94a-113">Describes the default mappings of XML data types to CLR types.</span></span>  
  
 [<span data-ttu-id="9b94a-114">Poznámky k implementaci podpory typů XML</span><span class="sxs-lookup"><span data-stu-id="9b94a-114">XML Type Support Implementation Notes</span></span>](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 <span data-ttu-id="9b94a-115">Tento článek popisuje některé podrobnosti o podpoře implementace typu.</span><span class="sxs-lookup"><span data-stu-id="9b94a-115">Discusses some of the type support implementation details.</span></span>  
  
 [<span data-ttu-id="9b94a-116">Převod datových typů XML</span><span class="sxs-lookup"><span data-stu-id="9b94a-116">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 <span data-ttu-id="9b94a-117">Popisuje způsob použití <xref:System.Xml.XmlConvert> pro převod mezi typy schématu XML a CLR.</span><span class="sxs-lookup"><span data-stu-id="9b94a-117">Describes how to use the <xref:System.Xml.XmlConvert> class to convert between XML Schema and CLR types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9b94a-118">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="9b94a-118">Related Sections</span></span>  
 [<span data-ttu-id="9b94a-119">Přístup k datům XML silného typu pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="9b94a-119">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
