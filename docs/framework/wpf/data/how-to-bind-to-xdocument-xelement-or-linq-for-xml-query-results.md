---
title: 'Postupy: Vytvoření vazby k XDocument, XElement nebo LINQ pro výsledky XQuery'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to XDocument
- data binding [WPF], binding to XElement
ms.assetid: 6a629a49-fe1c-465d-b76a-3dcbf4307b64
ms.openlocfilehash: afecb87dcfce1a8c48f1b2108edeae3cfd2aa16f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62020956"
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a><span data-ttu-id="540e6-102">Postupy: Vytvoření vazby k XDocument, XElement nebo LINQ pro výsledky XQuery</span><span class="sxs-lookup"><span data-stu-id="540e6-102">How to: Bind to XDocument, XElement, or LINQ for XML Query Results</span></span>
<span data-ttu-id="540e6-103">Tento příklad ukazuje, jak vytvořit vazbu dat XML do <xref:System.Windows.Controls.ItemsControl> pomocí <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="540e6-103">This example demonstrates how to bind XML data to an <xref:System.Windows.Controls.ItemsControl> using <xref:System.Xml.Linq.XDocument>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="540e6-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="540e6-104">Example</span></span>  
 <span data-ttu-id="540e6-105">Definuje následující kód XAML <xref:System.Windows.Controls.ItemsControl> a obsahuje šablonu dat pro datový typ `Planet` v `http://planetsNS` oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="540e6-105">The following XAML code defines an <xref:System.Windows.Controls.ItemsControl> and includes a data template for data of type `Planet` in the `http://planetsNS` XML namespace.</span></span> <span data-ttu-id="540e6-106">Datový typ XML, který zabírá oboru názvů musí obsahovat obor názvů ve složených závorkách, a pokud se zobrazí, kde se může zobrazit rozšíření značek XAML, musí být obor názvů se řídicí sekvence složenou závorku.</span><span class="sxs-lookup"><span data-stu-id="540e6-106">An XML data type that occupies a namespace must include the namespace in braces, and if it appears where a XAML markup extension could appear, it must precede the namespace with a brace escape sequence.</span></span> <span data-ttu-id="540e6-107">Tento kód váže k dynamické vlastnosti, které odpovídají <xref:System.Xml.Linq.XContainer.Element%2A> a <xref:System.Xml.Linq.XElement.Attribute%2A> metody <xref:System.Xml.Linq.XElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="540e6-107">This code binds to dynamic properties that correspond to the <xref:System.Xml.Linq.XContainer.Element%2A> and <xref:System.Xml.Linq.XElement.Attribute%2A> methods of the <xref:System.Xml.Linq.XElement> class.</span></span> <span data-ttu-id="540e6-108">Dynamické vlastnosti umožňují XAML vytvořit vazbu na dynamické vlastnosti, které sdílejí názvy metod.</span><span class="sxs-lookup"><span data-stu-id="540e6-108">Dynamic properties enable XAML to bind to dynamic properties that share the names of methods.</span></span> <span data-ttu-id="540e6-109">Další informace najdete v tématu [XML dynamické vlastnosti LINQ to](/visualstudio/designers/linq-to-xml-dynamic-properties).</span><span class="sxs-lookup"><span data-stu-id="540e6-109">To learn more, see [LINQ to XML Dynamic Properties](/visualstudio/designers/linq-to-xml-dynamic-properties).</span></span> <span data-ttu-id="540e6-110">Všimněte si, jak výchozí deklaraci oboru názvů pro XML se nevztahují na názvy atributů.</span><span class="sxs-lookup"><span data-stu-id="540e6-110">Notice how the default namespace declaration for the XML does not apply to attribute names.</span></span>  
  
 [!code-xaml[XLinqExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
[!code-xaml[XLinqExample#ItemsControl](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]  
  
 <span data-ttu-id="540e6-111">Následující volání kódu C# <xref:System.Xml.Linq.XDocument.Load%2A> a nastavuje kontext dat panelu zásobníku pro všechny dílčí prvky prvku s názvem `SolarSystemPlanets` v `http://planetsNS` oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="540e6-111">The following C# code calls <xref:System.Xml.Linq.XDocument.Load%2A> and sets the stack panel data context to all subelements of the element named `SolarSystemPlanets` in the `http://planetsNS` XML namespace.</span></span>  
  
 [!code-csharp[XLinqExample#LoadDCFromFile](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
 [!code-vb[XLinqExample#LoadDCFromFile](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]  
  
 <span data-ttu-id="540e6-112">XML data mohou být uložena jako prostředků XAML pomocí <xref:System.Windows.Data.ObjectDataProvider>.</span><span class="sxs-lookup"><span data-stu-id="540e6-112">XML data can be stored as a XAML resource using <xref:System.Windows.Data.ObjectDataProvider>.</span></span> <span data-ttu-id="540e6-113">Kompletní příklad naleznete v tématu [zdrojový kód L2DBForm.xaml](/visualstudio/designers/l2dbform-xaml-source-code).</span><span class="sxs-lookup"><span data-stu-id="540e6-113">For a complete example, see  [L2DBForm.xaml source code](/visualstudio/designers/l2dbform-xaml-source-code).</span></span> <span data-ttu-id="540e6-114">Následující příklad ukazuje, jak kód můžete nastavit kontext dat do objektu prostředku.</span><span class="sxs-lookup"><span data-stu-id="540e6-114">The following sample shows how code can set the data context to an object resource.</span></span>  
  
 [!code-csharp[XLinqExample#LoadDCFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
 [!code-vb[XLinqExample#LoadDCFromXAML](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]  
  
 <span data-ttu-id="540e6-115">Dynamické vlastnosti, které mapují na <xref:System.Xml.Linq.XContainer.Element%2A> a <xref:System.Xml.Linq.XElement.Attribute%2A> poskytují flexibilitu v rámci XAML.</span><span class="sxs-lookup"><span data-stu-id="540e6-115">The dynamic properties that map to <xref:System.Xml.Linq.XContainer.Element%2A> and <xref:System.Xml.Linq.XElement.Attribute%2A> provide flexibility within XAML.</span></span> <span data-ttu-id="540e6-116">Kód můžete také navázat pro výsledky XML dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="540e6-116">Your code can also bind to the results of a LINQ for XML query.</span></span> <span data-ttu-id="540e6-117">Tento příklad vytvoří vazbu na výsledky dotazu seřazené podle hodnotu elementu.</span><span class="sxs-lookup"><span data-stu-id="540e6-117">This example binds to query results ordered by an element value.</span></span>  
  
 [!code-csharp[XLinqExample#BindToResults](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
 [!code-vb[XLinqExample#BindToResults](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]  
  
## <a name="see-also"></a><span data-ttu-id="540e6-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="540e6-118">See also</span></span>

- [<span data-ttu-id="540e6-119">Přehled zdrojů vazby</span><span class="sxs-lookup"><span data-stu-id="540e6-119">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="540e6-120">Přehled datové vazby WPF s LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="540e6-120">WPF Data Binding with LINQ to XML Overview</span></span>](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)
- [<span data-ttu-id="540e6-121">Příklad datové vazby WPF pomocí LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="540e6-121">WPF Data Binding Using LINQ to XML Example</span></span>](/visualstudio/designers/wpf-data-binding-using-linq-to-xml-example)
- [<span data-ttu-id="540e6-122">Dynamické vlastnosti LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="540e6-122">LINQ to XML Dynamic Properties</span></span>](/visualstudio/designers/linq-to-xml-dynamic-properties)
