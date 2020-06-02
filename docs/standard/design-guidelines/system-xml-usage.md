---
title: Použití System.Xml
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
ms.openlocfilehash: 07828219f2e17be925d060fa3bb33a9209ecb62b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291666"
---
# <a name="systemxml-usage"></a><span data-ttu-id="cf9c1-102">Použití System.Xml</span><span class="sxs-lookup"><span data-stu-id="cf9c1-102">System.Xml Usage</span></span>
<span data-ttu-id="cf9c1-103">Tato část pojednává o použití několika typů umístěných v <xref:System.Xml?displayProperty=nameWithType> oborech názvů, které lze použít k reprezentaci dat XML.</span><span class="sxs-lookup"><span data-stu-id="cf9c1-103">This section talks about usage of several types residing in <xref:System.Xml?displayProperty=nameWithType> namespaces that can be used to represent XML data.</span></span>

 <span data-ttu-id="cf9c1-104">❌Nepoužívejte <xref:System.Xml.XmlNode> nebo <xref:System.Xml.XmlDocument> k reprezentaci dat XML.</span><span class="sxs-lookup"><span data-stu-id="cf9c1-104">❌ DO NOT use <xref:System.Xml.XmlNode> or <xref:System.Xml.XmlDocument> to represent XML data.</span></span> <span data-ttu-id="cf9c1-105">Místo toho používejte instance typu <xref:System.Xml.XPath.IXPathNavigable> , <xref:System.Xml.XmlReader> , <xref:System.Xml.XmlWriter> nebo <xref:System.Xml.Linq.XNode> .</span><span class="sxs-lookup"><span data-stu-id="cf9c1-105">Favor using instances of <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, or subtypes of <xref:System.Xml.Linq.XNode> instead.</span></span> <span data-ttu-id="cf9c1-106">`XmlNode`a `XmlDocument` nejsou navržené pro vystavení ve veřejných rozhraních API.</span><span class="sxs-lookup"><span data-stu-id="cf9c1-106">`XmlNode` and `XmlDocument` are not designed for exposing in public APIs.</span></span>

 <span data-ttu-id="cf9c1-107">✔️ použít `XmlReader` , `IXPathNavigable` nebo podtypy `XNode` jako vstup nebo výstup členů, kteří přijímají nebo vracejí kód XML.</span><span class="sxs-lookup"><span data-stu-id="cf9c1-107">✔️ DO use `XmlReader`, `IXPathNavigable`, or subtypes of `XNode` as input or output of members that accept or return XML.</span></span>

 <span data-ttu-id="cf9c1-108">Použijte tyto abstrakce namísto `XmlDocument` , `XmlNode` , nebo <xref:System.Xml.XPath.XPathDocument> , protože se tím odpojí metody od konkrétních implementací dokumentu XML v paměti a umožňuje jim pracovat s virtuálními zdroji dat XML, které zveřejňují `XNode` , `XmlReader` nebo <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="cf9c1-108">Use these abstractions instead of `XmlDocument`, `XmlNode`, or <xref:System.Xml.XPath.XPathDocument>, because this decouples the methods from specific implementations of an in-memory XML document and allows them to work with virtual XML data sources that expose `XNode`, `XmlReader`, or <xref:System.Xml.XPath.XPathNavigator>.</span></span>

 <span data-ttu-id="cf9c1-109">❌Nepoužívejte podtřídu `XmlDocument` , pokud chcete vytvořit typ reprezentující zobrazení XML základního objektového modelu nebo zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="cf9c1-109">❌ DO NOT subclass `XmlDocument` if you want to create a type representing an XML view of an underlying object model or data source.</span></span>

 <span data-ttu-id="cf9c1-110">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="cf9c1-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="cf9c1-111">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="cf9c1-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="cf9c1-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf9c1-112">See also</span></span>

- [<span data-ttu-id="cf9c1-113">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="cf9c1-113">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="cf9c1-114">Pokyny k použití</span><span class="sxs-lookup"><span data-stu-id="cf9c1-114">Usage Guidelines</span></span>](usage-guidelines.md)
