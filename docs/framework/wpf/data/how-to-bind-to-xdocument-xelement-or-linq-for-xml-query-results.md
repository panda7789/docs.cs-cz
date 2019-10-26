---
title: 'Postupy: Připojení k XDocument, XElement nebo LINQ pro výsledky XML dotazu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to XDocument
- data binding [WPF], binding to XElement
ms.assetid: 6a629a49-fe1c-465d-b76a-3dcbf4307b64
ms.openlocfilehash: 070f67f30613d4522a48e08fd1c208fbe5887525
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920113"
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a><span data-ttu-id="e6355-102">Postupy: Připojení k XDocument, XElement nebo LINQ pro výsledky XML dotazu</span><span class="sxs-lookup"><span data-stu-id="e6355-102">How to: Bind to XDocument, XElement, or LINQ for XML Query Results</span></span>

<span data-ttu-id="e6355-103">Tento příklad ukazuje, jak vytvořit vazby dat XML k <xref:System.Windows.Controls.ItemsControl> pomocí <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="e6355-103">This example demonstrates how to bind XML data to an <xref:System.Windows.Controls.ItemsControl> using <xref:System.Xml.Linq.XDocument>.</span></span>

## <a name="example"></a><span data-ttu-id="e6355-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e6355-104">Example</span></span>

<span data-ttu-id="e6355-105">Následující kód XAML definuje <xref:System.Windows.Controls.ItemsControl> a obsahuje datovou šablonu pro data typu `Planet` v oboru názvů XML `http://planetsNS`.</span><span class="sxs-lookup"><span data-stu-id="e6355-105">The following XAML code defines an <xref:System.Windows.Controls.ItemsControl> and includes a data template for data of type `Planet` in the `http://planetsNS` XML namespace.</span></span> <span data-ttu-id="e6355-106">Datový typ XML, který zabírá obor názvů, musí obsahovat obor názvů v závorkách a pokud se zobrazí, kde se může zobrazit rozšíření značek XAML, musí předcházet tomuto oboru názvů řídicí sekvencí závorky.</span><span class="sxs-lookup"><span data-stu-id="e6355-106">An XML data type that occupies a namespace must include the namespace in braces, and if it appears where a XAML markup extension could appear, it must precede the namespace with a brace escape sequence.</span></span> <span data-ttu-id="e6355-107">Tento kód se váže k dynamickým vlastnostem, které odpovídají <xref:System.Xml.Linq.XContainer.Element%2A> a <xref:System.Xml.Linq.XElement.Attribute%2A> metod třídy <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="e6355-107">This code binds to dynamic properties that correspond to the <xref:System.Xml.Linq.XContainer.Element%2A> and <xref:System.Xml.Linq.XElement.Attribute%2A> methods of the <xref:System.Xml.Linq.XElement> class.</span></span> <span data-ttu-id="e6355-108">Dynamické vlastnosti umožňují, aby se XAML váže k dynamickým vlastnostem, které sdílejí názvy metod.</span><span class="sxs-lookup"><span data-stu-id="e6355-108">Dynamic properties enable XAML to bind to dynamic properties that share the names of methods.</span></span> <span data-ttu-id="e6355-109">Další informace najdete v tématu [LINQ to XML dynamické vlastnosti](linq-to-xml-dynamic-properties.md).</span><span class="sxs-lookup"><span data-stu-id="e6355-109">To learn more, see [LINQ to XML dynamic properties](linq-to-xml-dynamic-properties.md).</span></span> <span data-ttu-id="e6355-110">Všimněte si, jak výchozí deklaraci oboru názvů pro XML neplatí pro názvy atributů.</span><span class="sxs-lookup"><span data-stu-id="e6355-110">Notice how the default namespace declaration for the XML does not apply to attribute names.</span></span>

[!code-xaml[XLinqExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]
[!code-xaml[XLinqExample#ItemsControl](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]

<span data-ttu-id="e6355-111">Následující C# kód volá<xref:System.Xml.Linq.XDocument.Load%2A>a nastaví kontext dat panelu zásobníku na všechny dílčí prvky elementu s názvem`SolarSystemPlanets`v oboru názvů XML`http://planetsNS`.</span><span class="sxs-lookup"><span data-stu-id="e6355-111">The following C# code calls <xref:System.Xml.Linq.XDocument.Load%2A> and sets the stack panel data context to all subelements of the element named `SolarSystemPlanets` in the `http://planetsNS` XML namespace.</span></span>

[!code-csharp[XLinqExample#LoadDCFromFile](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
[!code-vb[XLinqExample#LoadDCFromFile](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]

<span data-ttu-id="e6355-112">Data XML lze uložit jako prostředek XAML pomocí <xref:System.Windows.Data.ObjectDataProvider>.</span><span class="sxs-lookup"><span data-stu-id="e6355-112">XML data can be stored as a XAML resource using <xref:System.Windows.Data.ObjectDataProvider>.</span></span> <span data-ttu-id="e6355-113">Úplný příklad naleznete v tématu [zdrojový kód zdrojový kód L2DBForm. XAML](l2dbform-xaml-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="e6355-113">For a complete example, see  [L2DBForm.xaml source code](l2dbform-xaml-source-code.md).</span></span> <span data-ttu-id="e6355-114">Následující příklad ukazuje, jak kód může nastavit kontext dat na prostředek objektu.</span><span class="sxs-lookup"><span data-stu-id="e6355-114">The following sample shows how code can set the data context to an object resource.</span></span>

[!code-csharp[XLinqExample#LoadDCFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
[!code-vb[XLinqExample#LoadDCFromXAML](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]

<span data-ttu-id="e6355-115">Dynamické vlastnosti, které jsou mapovány na <xref:System.Xml.Linq.XContainer.Element%2A> a <xref:System.Xml.Linq.XElement.Attribute%2A> poskytují flexibilitu v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="e6355-115">The dynamic properties that map to <xref:System.Xml.Linq.XContainer.Element%2A> and <xref:System.Xml.Linq.XElement.Attribute%2A> provide flexibility within XAML.</span></span> <span data-ttu-id="e6355-116">Váš kód může také vytvořit vazby k výsledkům dotazu LINQ for XML.</span><span class="sxs-lookup"><span data-stu-id="e6355-116">Your code can also bind to the results of a LINQ for XML query.</span></span> <span data-ttu-id="e6355-117">Tento příklad váže k výsledkům dotazu seřazenými podle hodnoty elementu.</span><span class="sxs-lookup"><span data-stu-id="e6355-117">This example binds to query results ordered by an element value.</span></span>

[!code-csharp[XLinqExample#BindToResults](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
[!code-vb[XLinqExample#BindToResults](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]

## <a name="see-also"></a><span data-ttu-id="e6355-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6355-118">See also</span></span>

- [<span data-ttu-id="e6355-119">Přehled zdrojů vazby</span><span class="sxs-lookup"><span data-stu-id="e6355-119">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="e6355-120">Přehled datové vazby WPF s LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="e6355-120">WPF Data Binding with LINQ to XML Overview</span></span>](wpf-data-binding-with-linq-to-xml-overview.md)
- [<span data-ttu-id="e6355-121">Příklad datové vazby WPF pomocí LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="e6355-121">WPF Data Binding Using LINQ to XML Example</span></span>](linq-to-xml-data-binding-sample.md)
- [<span data-ttu-id="e6355-122">Dynamické vlastnosti LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="e6355-122">LINQ to XML Dynamic Properties</span></span>](linq-to-xml-dynamic-properties.md)
