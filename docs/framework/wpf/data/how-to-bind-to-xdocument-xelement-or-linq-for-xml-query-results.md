---
title: "Postupy: Připojení k XDocument, XElement nebo LINQ pro výsledky XML dotazu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to XDocument
- data binding [WPF], binding to XElement
ms.assetid: 6a629a49-fe1c-465d-b76a-3dcbf4307b64
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ceb6023157d487aebeff4fb5335b58c0958f2851
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a><span data-ttu-id="48ba5-102">Postupy: Připojení k XDocument, XElement nebo LINQ pro výsledky XML dotazu</span><span class="sxs-lookup"><span data-stu-id="48ba5-102">How to: Bind to XDocument, XElement, or LINQ for XML Query Results</span></span>
<span data-ttu-id="48ba5-103">Tento příklad ukazuje, jak vytvořit vazbu dat XML do <xref:System.Windows.Controls.ItemsControl> pomocí <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="48ba5-103">This example demonstrates how to bind XML data to an <xref:System.Windows.Controls.ItemsControl> using <xref:System.Xml.Linq.XDocument>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48ba5-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="48ba5-104">Example</span></span>  
 <span data-ttu-id="48ba5-105">Následující kód XAML definuje <xref:System.Windows.Controls.ItemsControl> a obsahuje šablonu dat pro data typu `Planet` v `http://planetsNS` obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="48ba5-105">The following XAML code defines an <xref:System.Windows.Controls.ItemsControl> and includes a data template for data of type `Planet` in the `http://planetsNS` XML namespace.</span></span> <span data-ttu-id="48ba5-106">Datový typ XML, který bude zabírat oboru názvů musí zahrnovat oboru názvů do složených závorek a pokud se zobrazí, kde se může zobrazit rozšíření značek XAML, je třeba zadat jeden obor názvů s řídicí sekvence závorek.</span><span class="sxs-lookup"><span data-stu-id="48ba5-106">An XML data type that occupies a namespace must include the namespace in braces, and if it appears where a XAML markup extension could appear, it must precede the namespace with a brace escape sequence.</span></span> <span data-ttu-id="48ba5-107">Tento kód se váže k dynamické vlastnosti, které odpovídají <xref:System.Xml.Linq.XContainer.Element%2A> a <xref:System.Xml.Linq.XElement.Attribute%2A> metody <xref:System.Xml.Linq.XElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="48ba5-107">This code binds to dynamic properties that correspond to the <xref:System.Xml.Linq.XContainer.Element%2A> and <xref:System.Xml.Linq.XElement.Attribute%2A> methods of the <xref:System.Xml.Linq.XElement> class.</span></span> <span data-ttu-id="48ba5-108">Dynamické vlastnosti povolit XAML pro vazbu k dynamické vlastnosti, které sdílejí názvy metod.</span><span class="sxs-lookup"><span data-stu-id="48ba5-108">Dynamic properties enable XAML to bind to dynamic properties that share the names of methods.</span></span> <span data-ttu-id="48ba5-109">Další informace najdete v tématu [technologie LINQ to XML dynamické vlastnosti](/visualstudio/designers/linq-to-xml-dynamic-properties).</span><span class="sxs-lookup"><span data-stu-id="48ba5-109">To learn more, see [LINQ to XML Dynamic Properties](/visualstudio/designers/linq-to-xml-dynamic-properties).</span></span> <span data-ttu-id="48ba5-110">Všimněte si, jak výchozí deklaraci oboru názvů pro soubor XML nevztahuje na názvy atributů.</span><span class="sxs-lookup"><span data-stu-id="48ba5-110">Notice how the default namespace declaration for the XML does not apply to attribute names.</span></span>  
  
 [!code-xaml[XLinqExample#StackPanelResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
[!code-xaml[XLinqExample#ItemsControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]  
  
 <span data-ttu-id="48ba5-111">Následující volání kódu jazyka C# <xref:System.Xml.Linq.XDocument.Load%2A> a nastaví kontext zásobníku panel data na všechny dílčí prvky elementu s názvem `SolarSystemPlanets` v `http://planetsNS` obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="48ba5-111">The following C# code calls <xref:System.Xml.Linq.XDocument.Load%2A> and sets the stack panel data context to all subelements of the element named `SolarSystemPlanets` in the `http://planetsNS` XML namespace.</span></span>  
  
 [!code-csharp[XLinqExample#LoadDCFromFile](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
 [!code-vb[XLinqExample#LoadDCFromFile](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]  
  
 <span data-ttu-id="48ba5-112">XML data mohou být uloženy ve formě XAML prostředků pomocí <xref:System.Windows.Data.ObjectDataProvider>.</span><span class="sxs-lookup"><span data-stu-id="48ba5-112">XML data can be stored as a XAML resource using <xref:System.Windows.Data.ObjectDataProvider>.</span></span> <span data-ttu-id="48ba5-113">Úplný příklad najdete v tématu [L2DBForm.xaml zdrojový kód](http://msdn.microsoft.com/library/624e96d4-6d27-4195-8ac2-2f3835f6c57e).</span><span class="sxs-lookup"><span data-stu-id="48ba5-113">For a complete example, see  [L2DBForm.xaml Source Code](http://msdn.microsoft.com/library/624e96d4-6d27-4195-8ac2-2f3835f6c57e).</span></span> <span data-ttu-id="48ba5-114">Následující příklad ukazuje, jak kód můžete nastavit kontext dat na prostředek objektu.</span><span class="sxs-lookup"><span data-stu-id="48ba5-114">The following sample shows how code can set the data context to an object resource.</span></span>  
  
 [!code-csharp[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
 [!code-vb[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]  
  
 <span data-ttu-id="48ba5-115">Dynamické vlastnosti, které jsou mapovány na <xref:System.Xml.Linq.XContainer.Element%2A> a <xref:System.Xml.Linq.XElement.Attribute%2A> poskytují flexibilitu v rámci XAML.</span><span class="sxs-lookup"><span data-stu-id="48ba5-115">The dynamic properties that map to <xref:System.Xml.Linq.XContainer.Element%2A> and <xref:System.Xml.Linq.XElement.Attribute%2A> provide flexibility within XAML.</span></span> <span data-ttu-id="48ba5-116">Váš kód můžete také vytvořit vazbu k výsledky LINQ pro dotaz XML.</span><span class="sxs-lookup"><span data-stu-id="48ba5-116">Your code can also bind to the results of a LINQ for XML query.</span></span> <span data-ttu-id="48ba5-117">Tento příklad vytvoří vazbu s výsledky dotazů, které jsou seřazené podle hodnotu elementu.</span><span class="sxs-lookup"><span data-stu-id="48ba5-117">This example binds to query results ordered by an element value.</span></span>  
  
 [!code-csharp[XLinqExample#BindToResults](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
 [!code-vb[XLinqExample#BindToResults](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]  
  
## <a name="see-also"></a><span data-ttu-id="48ba5-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="48ba5-118">See Also</span></span>  
 [<span data-ttu-id="48ba5-119">Přehled zdrojů vazby</span><span class="sxs-lookup"><span data-stu-id="48ba5-119">Binding Sources Overview</span></span>](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [<span data-ttu-id="48ba5-120">Přehled datové vazby WPF s LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="48ba5-120">WPF Data Binding with LINQ to XML Overview</span></span>](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)  
 [<span data-ttu-id="48ba5-121">Příklad datové vazby WPF pomocí LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="48ba5-121">WPF Data Binding Using LINQ to XML Example</span></span>](/visualstudio/designers/wpf-data-binding-using-linq-to-xml-example)  
 [<span data-ttu-id="48ba5-122">Dynamické vlastnosti LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="48ba5-122">LINQ to XML Dynamic Properties</span></span>](/visualstudio/designers/linq-to-xml-dynamic-properties)
