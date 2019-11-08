---
title: 'Postupy: Použití oborů názvů XML v datové vazbě'
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: f6e6e042fa5583fcf91bd15c524537490fb6670c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740571"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a><span data-ttu-id="7ad7a-102">Postupy: Použití oborů názvů XML v datové vazbě</span><span class="sxs-lookup"><span data-stu-id="7ad7a-102">How to: Use XML Namespaces in Data Binding</span></span>
## <a name="example"></a><span data-ttu-id="7ad7a-103">Příklad</span><span class="sxs-lookup"><span data-stu-id="7ad7a-103">Example</span></span>
 <span data-ttu-id="7ad7a-104">Tento příklad ukazuje, jak zpracovat obory názvů zadané ve zdroji vazby XML.</span><span class="sxs-lookup"><span data-stu-id="7ad7a-104">This example shows how to handle namespaces specified in your XML binding source.</span></span>

 <span data-ttu-id="7ad7a-105">Pokud data XML mají následující definici oboru názvů XML:</span><span class="sxs-lookup"><span data-stu-id="7ad7a-105">If your XML data has the following XML namespace definition:</span></span>

 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`

 <span data-ttu-id="7ad7a-106">Můžete použít prvek <xref:System.Windows.Data.XmlNamespaceMapping> pro mapování oboru názvů na <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7ad7a-106">You can use the <xref:System.Windows.Data.XmlNamespaceMapping> element to map the namespace to a <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, as in the following example.</span></span> <span data-ttu-id="7ad7a-107">Pak můžete použít <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> pro odkazování na obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="7ad7a-107">You can then use the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> to refer to the XML namespace.</span></span> <span data-ttu-id="7ad7a-108"><xref:System.Windows.Controls.ListBox> v tomto příkladu zobrazuje *název* a *DC: datum* každé *položky*.</span><span class="sxs-lookup"><span data-stu-id="7ad7a-108">The <xref:System.Windows.Controls.ListBox> in this example displays the *title* and *dc:date* of each *item*.</span></span>

 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]

 <span data-ttu-id="7ad7a-109">Všimněte si, že <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, které zadáte, se nemusí shodovat s tím, který se používá ve zdroji XML; Pokud se změní předpona ve zdroji XML, vaše mapování pořád funguje.</span><span class="sxs-lookup"><span data-stu-id="7ad7a-109">Note that the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> you specify does not have to match the one used in the XML source; if the prefix changes in the XML source your mapping still works.</span></span>

 <span data-ttu-id="7ad7a-110">V tomto konkrétním příkladu data XML přicházejí z webové služby, ale prvek <xref:System.Windows.Data.XmlNamespaceMapping> také funguje s vloženými daty XML nebo XML v vloženém souboru.</span><span class="sxs-lookup"><span data-stu-id="7ad7a-110">In this particular example, the XML data comes from a web service, but the <xref:System.Windows.Data.XmlNamespaceMapping> element also works with inline XML or XML data in an embedded file.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ad7a-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7ad7a-111">See also</span></span>

- [<span data-ttu-id="7ad7a-112">Vytvoření vazby k datům XML pomocí objektu XMLDataProvider a dotazů XPath</span><span class="sxs-lookup"><span data-stu-id="7ad7a-112">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="7ad7a-113">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="7ad7a-113">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="7ad7a-114">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="7ad7a-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
