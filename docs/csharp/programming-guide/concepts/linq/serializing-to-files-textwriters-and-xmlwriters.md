---
title: Serializace do tříd File, TextWriter a XmlWriter
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 20cb84a9f79ca8de3e86a996f18c388dc53340ae
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868847"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="261ae-102">Serializace do tříd File, TextWriter a XmlWriter</span><span class="sxs-lookup"><span data-stu-id="261ae-102">Serializing to Files, TextWriters, and XmlWriters</span></span>

<span data-ttu-id="261ae-103">Můžete serializovat stromy XML na <xref:System.IO.File> <xref:System.IO.TextWriter>, nebo <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="261ae-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="261ae-104">Můžete serializovat jakoukoli komponentu XML, včetně <xref:System.Xml.Linq.XDocument> a <xref:System.Xml.Linq.XElement>, do řetězce pomocí `ToString` metody.</span><span class="sxs-lookup"><span data-stu-id="261ae-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>

<span data-ttu-id="261ae-105">Pokud chcete potlačit formátování při serializaci na řetězec, můžete použít <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="261ae-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="261ae-106">Výchozí chování při serializaci do souboru je formátování (odsazení) výsledného dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="261ae-106">The default behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="261ae-107">Při odsazení se nezachovají nevýznamné prázdné znaky ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="261ae-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="261ae-108">Chcete-li serializovat s formátováním, použijte jedno z přetížení následujících metod, které nevezmou <xref:System.Xml.Linq.SaveOptions> jako argument:</span><span class="sxs-lookup"><span data-stu-id="261ae-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="261ae-109">Chcete-li, aby možnost neodsazena a zachovala nevýznamné prázdné znaky ve stromu XML, použijte jedno z přetížení následujících metod, které přebírají <xref:System.Xml.Linq.SaveOptions> jako argument:</span><span class="sxs-lookup"><span data-stu-id="261ae-109">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="261ae-110">Příklady najdete v příslušném referenčním tématu.</span><span class="sxs-lookup"><span data-stu-id="261ae-110">For examples, see the appropriate reference topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="261ae-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="261ae-111">See also</span></span>

- [<span data-ttu-id="261ae-112">Serializace stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="261ae-112">Serializing XML Trees (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
