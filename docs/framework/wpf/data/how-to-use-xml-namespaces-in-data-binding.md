---
title: 'Postupy: Použití oborů názvů XML v datové vazbě'
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: 9d8ddc5445bac28c68cd6cc99acf3313613a8c7f
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919671"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a><span data-ttu-id="6c94d-102">Postupy: Použití oborů názvů XML v datové vazbě</span><span class="sxs-lookup"><span data-stu-id="6c94d-102">How to: Use XML Namespaces in Data Binding</span></span>
## <a name="example"></a><span data-ttu-id="6c94d-103">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c94d-103">Example</span></span>
 <span data-ttu-id="6c94d-104">Tento příklad ukazuje, jak zpracovat obory názvů zadané ve zdroji vazby [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6c94d-104">This example shows how to handle namespaces specified in your [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] binding source.</span></span>

 <span data-ttu-id="6c94d-105">Pokud [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data obsahují následující [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] definice oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="6c94d-105">If your [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data has the following [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace definition:</span></span>

 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`

 <span data-ttu-id="6c94d-106">Můžete použít prvek <xref:System.Windows.Data.XmlNamespaceMapping> pro mapování oboru názvů na <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6c94d-106">You can use the <xref:System.Windows.Data.XmlNamespaceMapping> element to map the namespace to a <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, as in the following example.</span></span> <span data-ttu-id="6c94d-107">Pak můžete použít <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> pro odkazování na obor názvů [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6c94d-107">You can then use the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> to refer to the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace.</span></span> <span data-ttu-id="6c94d-108"><xref:System.Windows.Controls.ListBox> v tomto příkladu zobrazuje *název* a *DC: datum* každé *položky*.</span><span class="sxs-lookup"><span data-stu-id="6c94d-108">The <xref:System.Windows.Controls.ListBox> in this example displays the *title* and *dc:date* of each *item*.</span></span>

 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]

 <span data-ttu-id="6c94d-109">Všimněte si, že <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, které zadáte, se nemusí shodovat s tím, který se používá ve zdroji [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]; Pokud se změní předpona ve zdroji [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], vaše mapování pořád funguje.</span><span class="sxs-lookup"><span data-stu-id="6c94d-109">Note that the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> you specify does not have to match the one used in the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] source; if the prefix changes in the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] source your mapping still works.</span></span>

 <span data-ttu-id="6c94d-110">V tomto konkrétním příkladu [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data pocházejí z webové služby, ale element <xref:System.Windows.Data.XmlNamespaceMapping> funguje také s vloženými [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] nebo [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]mi daty v vloženém souboru.</span><span class="sxs-lookup"><span data-stu-id="6c94d-110">In this particular example, the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data comes from a web service, but the <xref:System.Windows.Data.XmlNamespaceMapping> element also works with inline [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] or [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data in an embedded file.</span></span>

## <a name="see-also"></a><span data-ttu-id="6c94d-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c94d-111">See also</span></span>

- [<span data-ttu-id="6c94d-112">Vytvoření vazby k datům XML pomocí objektu XMLDataProvider a dotazů XPath</span><span class="sxs-lookup"><span data-stu-id="6c94d-112">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="6c94d-113">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="6c94d-113">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="6c94d-114">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="6c94d-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
