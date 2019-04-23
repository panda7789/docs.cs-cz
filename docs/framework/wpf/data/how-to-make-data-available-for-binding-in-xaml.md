---
title: 'Postupy: Zpřístupnění dat pro vazbu v jazyku XAML'
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 2d51f06da31482c46b04d1eb86172c3eda246c20
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145363"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="2b434-102">Postupy: Zpřístupnění dat pro vazbu v jazyku XAML</span><span class="sxs-lookup"><span data-stu-id="2b434-102">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="2b434-103">Toto téma popisuje různé způsoby, jak můžete zpřístupnit data pro vazbu v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], v závislosti na potřebách vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="2b434-103">This topic discusses various ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b434-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="2b434-104">Example</span></span>  
 <span data-ttu-id="2b434-105">Pokud máte [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objektů chcete svázat z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jedním ze způsobů, které můžete zpřístupnit objekt pro vazbu, je definovat jako prostředek a přiřaďte mu `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="2b434-105">If you have a [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="2b434-106">V následujícím příkladu je nutné `Person` objekt s řetězcovou vlastnost s názvem `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="2b434-106">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="2b434-107">`Person` Objekt (v řádku zobrazeném zvýrazněný, který obsahuje `<src>` element) je definován v oboru názvů volá `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="2b434-107">The `Person` object (in the line shown highlighted that contains the `<src>` element) is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="2b434-108">Potom můžete svázat <xref:System.Windows.Controls.TextBlock> ovládací prvek na objekt v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jak zvýrazněný řádek, který obsahuje `<TextBlock>` ukazuje element.</span><span class="sxs-lookup"><span data-stu-id="2b434-108">You can then bind the <xref:System.Windows.Controls.TextBlock> control to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as the highlighted line that contains the `<TextBlock>` element shows.</span></span> 
  
 <span data-ttu-id="2b434-109">Alternativně můžete použít <xref:System.Windows.Data.ObjectDataProvider> třídy, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="2b434-109">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example:</span></span>  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 <span data-ttu-id="2b434-110">Můžete definovat vazby stejným způsobem jako zvýrazněný řádek, který obsahuje `<TextBlock>` ukazuje element.</span><span class="sxs-lookup"><span data-stu-id="2b434-110">You define the binding the same way, as the highlighted line that contains the `<TextBlock>` element shows.</span></span>  
  
 <span data-ttu-id="2b434-111">V tomto konkrétním příkladu je výsledek stejný: je nutné <xref:System.Windows.Controls.TextBlock> pomocí textového obsahu `Joe`.</span><span class="sxs-lookup"><span data-stu-id="2b434-111">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="2b434-112">Ale <xref:System.Windows.Data.ObjectDataProvider> třída poskytuje funkce, třeba možnost vytvoření vazby mezi výsledkem metody.</span><span class="sxs-lookup"><span data-stu-id="2b434-112">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="2b434-113">Můžete použít <xref:System.Windows.Data.ObjectDataProvider> třídy, pokud potřebujete funkci poskytuje.</span><span class="sxs-lookup"><span data-stu-id="2b434-113">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="2b434-114">Nicméně, pokud vytváříte vazbu na objekt, který již byl vytvořen, je nutné nastavit `DataContext` v kódu, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2b434-114">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="2b434-115">Pro přístup k [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data pomocí vazby <xref:System.Windows.Data.XmlDataProvider> najdete v tématu [svázání dat XML pomocí XMLDataProvider a dotazů XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span><span class="sxs-lookup"><span data-stu-id="2b434-115">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="2b434-116">Pro přístup k [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data pomocí vazby <xref:System.Windows.Data.ObjectDataProvider> najdete v tématu [připojení k XDocument, XElement nebo LINQ pro výsledky XML dotazu](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span><span class="sxs-lookup"><span data-stu-id="2b434-116">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="2b434-117">Informace o mnoha způsoby, jak je možné určit data, vytváříte vazbu s najdete v tématu [určení zdroje připojení](how-to-specify-the-binding-source.md).</span><span class="sxs-lookup"><span data-stu-id="2b434-117">For information about many ways you can specify the data you are binding to, see [Specify the Binding Source](how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="2b434-118">Informace o tom, jaké typy dat lze svázat nebo jak implementovat vlastní [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objekty pro vazbu, naleznete v tématu [Přehled zdrojů vazby](binding-sources-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2b434-118">For information about what types of data you can bind to or how to implement your own [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objects for binding, see [Binding Sources Overview](binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b434-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b434-119">See also</span></span>

- [<span data-ttu-id="2b434-120">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="2b434-120">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="2b434-121">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="2b434-121">How-to Topics</span></span>](data-binding-how-to-topics.md)
