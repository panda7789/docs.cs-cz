---
title: "Serializace k souborům, TextWriters a XmlWriters1"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c2207ee3cf5bf1c89a01ba14875e788ceb53b01c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="3472e-102">Serializace k souborům, TextWriters a XmlWriters</span><span class="sxs-lookup"><span data-stu-id="3472e-102">Serializing to Files, TextWriters, and XmlWriters</span></span>
<span data-ttu-id="3472e-103">Může serializovat stromů XML <xref:System.IO.File>, <xref:System.IO.TextWriter>, nebo <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="3472e-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="3472e-104">Může serializovat libovolné součásti XML, včetně <xref:System.Xml.Linq.XDocument> a <xref:System.Xml.Linq.XElement>, na řetězec pomocí `ToString` metoda.</span><span class="sxs-lookup"><span data-stu-id="3472e-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>  
  
 <span data-ttu-id="3472e-105">Pokud chcete potlačit, formátování při serializaci do řetězce, můžete použít <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="3472e-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="3472e-106">Thedefault chování při serializaci do souboru je formátovat dokument (odsazení) výsledný soubor XML.</span><span class="sxs-lookup"><span data-stu-id="3472e-106">Thedefault behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="3472e-107">Při odsazení, není zachována zanedbatelný mezer ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="3472e-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="3472e-108">K serializaci s formátování, použijte jednu z následujících metod, které nepřebírají přetížení <xref:System.Xml.Linq.SaveOptions> jako argument:</span><span class="sxs-lookup"><span data-stu-id="3472e-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="3472e-109">Pokud chcete, aby možnost, není pro odsazení a zachovat zanedbatelný mezer ve stromové struktuře XML, použijte jednu z přetížení následující metody, která přebírá <xref:System.Xml.Linq.SaveOptions> jako argument:</span><span class="sxs-lookup"><span data-stu-id="3472e-109">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="3472e-110">Příklady najdete v tématu odpovídající odkaz.</span><span class="sxs-lookup"><span data-stu-id="3472e-110">For examples, see the appropriate reference topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3472e-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="3472e-111">See Also</span></span>  
 [<span data-ttu-id="3472e-112">Serializace XML stromů (C#)</span><span class="sxs-lookup"><span data-stu-id="3472e-112">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
