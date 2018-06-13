---
title: 'Postupy: Použití oborů názvů XML v datové vazbě'
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: 483b59bb7cea25617c832b96690f742b8b64b3e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556897"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a><span data-ttu-id="323d7-102">Postupy: Použití oborů názvů XML v datové vazbě</span><span class="sxs-lookup"><span data-stu-id="323d7-102">How to: Use XML Namespaces in Data Binding</span></span>
## <a name="example"></a><span data-ttu-id="323d7-103">Příklad</span><span class="sxs-lookup"><span data-stu-id="323d7-103">Example</span></span>  
 <span data-ttu-id="323d7-104">Tento příklad ukazuje, jak pracovat s obory názvů zadaný ve vaší [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] vazby zdroje.</span><span class="sxs-lookup"><span data-stu-id="323d7-104">This example shows how to handle namespaces specified in your [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] binding source.</span></span>  
  
 <span data-ttu-id="323d7-105">Pokud vaše [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data mají následující [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] definici oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="323d7-105">If your [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data has the following [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace definition:</span></span>  
  
 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`  
  
 <span data-ttu-id="323d7-106">Můžete použít <xref:System.Windows.Data.XmlNamespaceMapping> element k mapování oboru názvů <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="323d7-106">You can use the <xref:System.Windows.Data.XmlNamespaceMapping> element to map the namespace to a <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, as in the following example.</span></span> <span data-ttu-id="323d7-107">Pak můžete použít <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> k odkazování na [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="323d7-107">You can then use the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> to refer to the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace.</span></span> <span data-ttu-id="323d7-108"><xref:System.Windows.Controls.ListBox> v tomto příkladu se zobrazí *název* a *dc:date* jednotlivých *položky*.</span><span class="sxs-lookup"><span data-stu-id="323d7-108">The <xref:System.Windows.Controls.ListBox> in this example displays the *title* and *dc:date* of each *item*.</span></span>  
  
 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]  
  
 <span data-ttu-id="323d7-109">Všimněte si, že <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> zadáte tak, aby odpovídaly používaný v nemá [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] zdroje; Pokud se změní předponu v [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] zdroj vaší mapování pořád funguje.</span><span class="sxs-lookup"><span data-stu-id="323d7-109">Note that the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> you specify does not have to match the one used in the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] source; if the prefix changes in the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] source your mapping still works.</span></span>  
  
 <span data-ttu-id="323d7-110">V tomto konkrétním příkladu [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data pocházejí z webové služby, ale <xref:System.Windows.Data.XmlNamespaceMapping> element funguje taky s vložené [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] nebo [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dat ve vloženém souboru.</span><span class="sxs-lookup"><span data-stu-id="323d7-110">In this particular example, the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data comes from a web service, but the <xref:System.Windows.Data.XmlNamespaceMapping> element also works with inline [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] or [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data in an embedded file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="323d7-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="323d7-111">See Also</span></span>  
 [<span data-ttu-id="323d7-112">Vytvoření vazby k datům XML pomocí objektu XMLDataProvider a dotazů XPath</span><span class="sxs-lookup"><span data-stu-id="323d7-112">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)  
 [<span data-ttu-id="323d7-113">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="323d7-113">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="323d7-114">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="323d7-114">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
