---
title: Serializace do tříd File, TextWriter a XmlWriter
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 20cb84a9f79ca8de3e86a996f18c388dc53340ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "68868847"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="6897c-102">Serializace do tříd File, TextWriter a XmlWriter</span><span class="sxs-lookup"><span data-stu-id="6897c-102">Serializing to Files, TextWriters, and XmlWriters</span></span>

<span data-ttu-id="6897c-103">Stromy XML můžete serializovat <xref:System.IO.File>do <xref:System.IO.TextWriter>, a <xref:System.Xml.XmlWriter>nebo .</span><span class="sxs-lookup"><span data-stu-id="6897c-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="6897c-104">Pomocí metody můžete serializovat libovolnou <xref:System.Xml.Linq.XElement>komponentu `ToString` XML, včetně <xref:System.Xml.Linq.XDocument> a , do řetězce.</span><span class="sxs-lookup"><span data-stu-id="6897c-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>

<span data-ttu-id="6897c-105">Pokud chcete potlačit formátování při serializaci na řetězec, můžete <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> použít metodu.</span><span class="sxs-lookup"><span data-stu-id="6897c-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="6897c-106">Výchozí chování při serializaci souboru je formátování (odsazení) výsledného dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="6897c-106">The default behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="6897c-107">Při odsazení se nevýznamné prázdné místo ve stromu XML nezachová.</span><span class="sxs-lookup"><span data-stu-id="6897c-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="6897c-108">Chcete-li serializovat s formátováním, použijte jednu z přetížení následujících metod, které neberou <xref:System.Xml.Linq.SaveOptions> jako argument:</span><span class="sxs-lookup"><span data-stu-id="6897c-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="6897c-109">Pokud chcete možnost neodsadit a zachovat nevýznamné prázdné místo ve stromu XML, použijte jednu <xref:System.Xml.Linq.SaveOptions> z přetížení následujících metod, která bere jako argument:</span><span class="sxs-lookup"><span data-stu-id="6897c-109">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="6897c-110">Příklady naleznete v příslušném referenčním tématu.</span><span class="sxs-lookup"><span data-stu-id="6897c-110">For examples, see the appropriate reference topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="6897c-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="6897c-111">See also</span></span>

- [<span data-ttu-id="6897c-112">Serializace stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="6897c-112">Serializing XML Trees (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
