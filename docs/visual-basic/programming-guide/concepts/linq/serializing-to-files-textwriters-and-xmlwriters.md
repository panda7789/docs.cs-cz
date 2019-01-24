---
title: Serializace do souborů, tříd a XmlWriters3
ms.date: 07/20/2015
ms.assetid: 7a0c24df-79ef-41a0-87f5-e6cf79382da9
ms.openlocfilehash: a9908f04e2621da15f065a86feccc5af5cdac96d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658988"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="1892e-102">Serializace do souborů, tříd a XmlWriter</span><span class="sxs-lookup"><span data-stu-id="1892e-102">Serializing to Files, TextWriters, and XmlWriters</span></span>
<span data-ttu-id="1892e-103">Může serializovat stromů XML <xref:System.IO.File>, <xref:System.IO.TextWriter>, nebo <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="1892e-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="1892e-104">Může serializovat libovolné součásti XML, včetně <xref:System.Xml.Linq.XDocument> a <xref:System.Xml.Linq.XElement>, na řetězec pomocí `ToString` metody.</span><span class="sxs-lookup"><span data-stu-id="1892e-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>  
  
 <span data-ttu-id="1892e-105">Pokud chcete potlačit formátování při serializaci do řetězce, můžete použít <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="1892e-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="1892e-106">Thedefault chování při serializaci do souboru se má formátovat dokument (odsazení) výsledného kódu XML.</span><span class="sxs-lookup"><span data-stu-id="1892e-106">Thedefault behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="1892e-107">Při odsazení, není zachována nevýznamné prázdné znaky ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="1892e-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="1892e-108">K serializaci formátování, použijte jednu z přetížení z následujících metod, které nepřebírají <xref:System.Xml.Linq.SaveOptions> jako argument:</span><span class="sxs-lookup"><span data-stu-id="1892e-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="1892e-109">Pokud chcete možnost odsazení a nevýznamné mezeru ve stromové struktuře XML, použijte jednu z přetížených z následujících metod, které provede <xref:System.Xml.Linq.SaveOptions> jako argument:</span><span class="sxs-lookup"><span data-stu-id="1892e-109">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="1892e-110">Příklady naleznete v tématu příslušný odkaz.</span><span class="sxs-lookup"><span data-stu-id="1892e-110">For examples, see the appropriate reference topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1892e-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1892e-111">See also</span></span>
- [<span data-ttu-id="1892e-112">Serializace stromů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1892e-112">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
