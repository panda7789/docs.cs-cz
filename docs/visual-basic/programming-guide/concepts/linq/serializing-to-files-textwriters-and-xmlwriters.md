---
title: Serializace do souborů, TextWriter a XmlWriters3
ms.date: 07/20/2015
ms.assetid: 7a0c24df-79ef-41a0-87f5-e6cf79382da9
ms.openlocfilehash: d8b929ef02b8fd9c6a9f29ea997a754699a6e1c4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403560"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="66ebe-102">Serializace do tříd File, TextWriter a XmlWriter</span><span class="sxs-lookup"><span data-stu-id="66ebe-102">Serializing to Files, TextWriters, and XmlWriters</span></span>

<span data-ttu-id="66ebe-103">Můžete serializovat stromy XML na <xref:System.IO.File> , <xref:System.IO.TextWriter> nebo <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="66ebe-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="66ebe-104">Můžete serializovat jakoukoli komponentu XML, včetně <xref:System.Xml.Linq.XDocument> a <xref:System.Xml.Linq.XElement> , do řetězce pomocí `ToString` metody.</span><span class="sxs-lookup"><span data-stu-id="66ebe-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>

<span data-ttu-id="66ebe-105">Pokud chcete potlačit formátování při serializaci na řetězec, můžete použít <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="66ebe-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="66ebe-106">Výchozí chování při serializaci do souboru je formátování (odsazení) výsledného dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="66ebe-106">The default behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="66ebe-107">Při odsazení se nezachovají nevýznamné prázdné znaky ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="66ebe-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="66ebe-108">Chcete-li serializovat s formátováním, použijte jedno z přetížení následujících metod, které nevezmou <xref:System.Xml.Linq.SaveOptions> jako argument:</span><span class="sxs-lookup"><span data-stu-id="66ebe-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="66ebe-109">Chcete-li, aby možnost neodsazena a zachovala nevýznamné prázdné znaky ve stromu XML, použijte jedno z přetížení následujících metod, které přebírají <xref:System.Xml.Linq.SaveOptions> jako argument:</span><span class="sxs-lookup"><span data-stu-id="66ebe-109">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="66ebe-110">Příklady najdete v příslušném referenčním tématu.</span><span class="sxs-lookup"><span data-stu-id="66ebe-110">For examples, see the appropriate reference topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="66ebe-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="66ebe-111">See also</span></span>

- [<span data-ttu-id="66ebe-112">Serializace stromů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66ebe-112">Serializing XML Trees (Visual Basic)</span></span>](serializing-xml-trees.md)
