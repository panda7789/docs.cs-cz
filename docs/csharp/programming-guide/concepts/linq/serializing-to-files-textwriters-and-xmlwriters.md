---
title: Serializace do tříd File, TextWriter a XmlWriter
description: Přečtěte si o možnostech serializace stromů XML do souboru, TextWriter nebo XmlWriter v jazyce C# pomocí metod ToString nebo Save.
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 43c51ae7e9bf1a7848d45fd900424d6186671e53
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302383"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="1f1b6-103">Serializace do tříd File, TextWriter a XmlWriter</span><span class="sxs-lookup"><span data-stu-id="1f1b6-103">Serializing to Files, TextWriters, and XmlWriters</span></span>

<span data-ttu-id="1f1b6-104">Můžete serializovat stromy XML na <xref:System.IO.File> , <xref:System.IO.TextWriter> nebo <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="1f1b6-104">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="1f1b6-105">Můžete serializovat jakoukoli komponentu XML, včetně <xref:System.Xml.Linq.XDocument> a <xref:System.Xml.Linq.XElement> , do řetězce pomocí `ToString` metody.</span><span class="sxs-lookup"><span data-stu-id="1f1b6-105">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>

<span data-ttu-id="1f1b6-106">Pokud chcete potlačit formátování při serializaci na řetězec, můžete použít <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="1f1b6-106">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="1f1b6-107">Výchozí chování při serializaci do souboru je formátování (odsazení) výsledného dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="1f1b6-107">The default behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="1f1b6-108">Při odsazení se nezachovají nevýznamné prázdné znaky ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="1f1b6-108">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="1f1b6-109">Chcete-li serializovat s formátováním, použijte jedno z přetížení následujících metod, které nevezmou <xref:System.Xml.Linq.SaveOptions> jako argument:</span><span class="sxs-lookup"><span data-stu-id="1f1b6-109">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="1f1b6-110">Chcete-li, aby možnost neodsazena a zachovala nevýznamné prázdné znaky ve stromu XML, použijte jedno z přetížení následujících metod, které přebírají <xref:System.Xml.Linq.SaveOptions> jako argument:</span><span class="sxs-lookup"><span data-stu-id="1f1b6-110">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="1f1b6-111">Příklady najdete v příslušném referenčním tématu.</span><span class="sxs-lookup"><span data-stu-id="1f1b6-111">For examples, see the appropriate reference topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f1b6-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1f1b6-112">See also</span></span>

- [<span data-ttu-id="1f1b6-113">Serializace stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="1f1b6-113">Serializing XML Trees (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
