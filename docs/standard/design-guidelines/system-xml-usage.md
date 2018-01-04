---
title: "System.Xml využití"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 956cc0ba37c06b39ed32500209e1af47d4035c84
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="systemxml-usage"></a><span data-ttu-id="2ec1a-102">System.Xml využití</span><span class="sxs-lookup"><span data-stu-id="2ec1a-102">System.Xml Usage</span></span>
<span data-ttu-id="2ec1a-103">Tato část pojednává o použití několik typů, které se nacházejí v <xref:System.Xml?displayProperty=nameWithType> obory názvů, které můžete použít k reprezentování XML data.</span><span class="sxs-lookup"><span data-stu-id="2ec1a-103">This section talks about usage of several types residing in <xref:System.Xml?displayProperty=nameWithType> namespaces that can be used to represent XML data.</span></span>  
  
 <span data-ttu-id="2ec1a-104">**X nesmí** použít <xref:System.Xml.XmlNode> nebo <xref:System.Xml.XmlDocument> představují XML data.</span><span class="sxs-lookup"><span data-stu-id="2ec1a-104">**X DO NOT** use <xref:System.Xml.XmlNode> or <xref:System.Xml.XmlDocument> to represent XML data.</span></span> <span data-ttu-id="2ec1a-105">Upřednostnit pomocí instance <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, nebo podtypů <xref:System.Xml.Linq.XNode> místo.</span><span class="sxs-lookup"><span data-stu-id="2ec1a-105">Favor using instances of <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, or subtypes of <xref:System.Xml.Linq.XNode> instead.</span></span> <span data-ttu-id="2ec1a-106">`XmlNode`a `XmlDocument` nejsou navrženy pro vystavení veřejné rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="2ec1a-106">`XmlNode` and `XmlDocument` are not designed for exposing in public APIs.</span></span>  
  
 <span data-ttu-id="2ec1a-107">**PROVEĎTE ✓** použít `XmlReader`, `IXPathNavigable`, nebo podtypů `XNode` jako vstup nebo výstup členy, kteří přijímají nebo vrátit kód XML.</span><span class="sxs-lookup"><span data-stu-id="2ec1a-107">**✓ DO** use `XmlReader`, `IXPathNavigable`, or subtypes of `XNode` as input or output of members that accept or return XML.</span></span>  
  
 <span data-ttu-id="2ec1a-108">Pomocí těchto abstrakce místo `XmlDocument`, `XmlNode`, nebo <xref:System.Xml.XPath.XPathDocument>, protože to oddělí metody z konkrétní implementace dokumentu XML v paměti a umožňuje jim pro práci s virtuální zdroje dat XML, které zveřejňují `XNode` , `XmlReader`, nebo <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="2ec1a-108">Use these abstractions instead of `XmlDocument`, `XmlNode`, or <xref:System.Xml.XPath.XPathDocument>, because this decouples the methods from specific implementations of an in-memory XML document and allows them to work with virtual XML data sources that expose `XNode`, `XmlReader`, or <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="2ec1a-109">**X nesmí** podtřídami `XmlDocument` Pokud budete chtít vytvořit typ představující zobrazení základní objekt model nebo zdroj dat XML.</span><span class="sxs-lookup"><span data-stu-id="2ec1a-109">**X DO NOT** subclass `XmlDocument` if you want to create a type representing an XML view of an underlying object model or data source.</span></span>  
  
 <span data-ttu-id="2ec1a-110">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="2ec1a-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="2ec1a-111">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="2ec1a-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ec1a-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ec1a-112">See Also</span></span>  
 [<span data-ttu-id="2ec1a-113">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="2ec1a-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="2ec1a-114">Pokyny k používání</span><span class="sxs-lookup"><span data-stu-id="2ec1a-114">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
