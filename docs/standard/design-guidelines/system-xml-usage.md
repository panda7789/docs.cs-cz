---
title: Použití System.Xml
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
ms.openlocfilehash: c57f5451526094d58066d7d391f41795f17732de
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709033"
---
# <a name="systemxml-usage"></a><span data-ttu-id="71348-102">Použití System.Xml</span><span class="sxs-lookup"><span data-stu-id="71348-102">System.Xml Usage</span></span>
<span data-ttu-id="71348-103">Tato část pojednává o použití několika typů umístěných v <xref:System.Xml?displayProperty=nameWithType> oborech názvů, které lze použít k reprezentaci dat XML.</span><span class="sxs-lookup"><span data-stu-id="71348-103">This section talks about usage of several types residing in <xref:System.Xml?displayProperty=nameWithType> namespaces that can be used to represent XML data.</span></span>  
  
 <span data-ttu-id="71348-104">**X DO NOT** použít <xref:System.Xml.XmlNode> nebo <xref:System.Xml.XmlDocument> představují XML data.</span><span class="sxs-lookup"><span data-stu-id="71348-104">**X DO NOT** use <xref:System.Xml.XmlNode> or <xref:System.Xml.XmlDocument> to represent XML data.</span></span> <span data-ttu-id="71348-105">Místo toho používejte instance <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>nebo podtypy <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="71348-105">Favor using instances of <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, or subtypes of <xref:System.Xml.Linq.XNode> instead.</span></span> <span data-ttu-id="71348-106">`XmlNode` a `XmlDocument` nejsou navržené pro vystavení ve veřejných rozhraních API.</span><span class="sxs-lookup"><span data-stu-id="71348-106">`XmlNode` and `XmlDocument` are not designed for exposing in public APIs.</span></span>  
  
 <span data-ttu-id="71348-107">**✓ DO** použít `XmlReader`, `IXPathNavigable`, nebo podtypů `XNode` jako vstup nebo výstup členy, kteří přijímají nebo vrátit kód XML.</span><span class="sxs-lookup"><span data-stu-id="71348-107">**✓ DO** use `XmlReader`, `IXPathNavigable`, or subtypes of `XNode` as input or output of members that accept or return XML.</span></span>  
  
 <span data-ttu-id="71348-108">Tyto abstrakce použijte místo `XmlDocument`, `XmlNode`nebo <xref:System.Xml.XPath.XPathDocument>, protože se tím odpojí metody od konkrétních implementací dokumentu XML v paměti a umožňuje jim pracovat s virtuálními zdroji dat XML, které zveřejňují `XNode`, `XmlReader`nebo <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="71348-108">Use these abstractions instead of `XmlDocument`, `XmlNode`, or <xref:System.Xml.XPath.XPathDocument>, because this decouples the methods from specific implementations of an in-memory XML document and allows them to work with virtual XML data sources that expose `XNode`, `XmlReader`, or <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="71348-109">**X DO NOT** podtřídami `XmlDocument` Pokud budete chtít vytvořit typ představující zobrazení základní objekt model nebo zdroj dat XML.</span><span class="sxs-lookup"><span data-stu-id="71348-109">**X DO NOT** subclass `XmlDocument` if you want to create a type representing an XML view of an underlying object model or data source.</span></span>  
  
 <span data-ttu-id="71348-110">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="71348-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="71348-111">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="71348-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71348-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71348-112">See also</span></span>

- [<span data-ttu-id="71348-113">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="71348-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="71348-114">Pokyny k používání</span><span class="sxs-lookup"><span data-stu-id="71348-114">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
