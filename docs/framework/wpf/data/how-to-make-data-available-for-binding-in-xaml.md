---
title: 'Postupy: Zpřístupnění dat pro připojení v jazyku XAML'
description: Seznamte se s různými způsoby, jak můžete data zpřístupnit v závislosti na potřebách vaší aplikace v Windows Presentation Foundation (WPF).
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 16618ce8b19f5dd5854c4d126e7fc455f0428a28
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620791"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="67912-103">Postupy: Zpřístupnění dat pro připojení v jazyku XAML</span><span class="sxs-lookup"><span data-stu-id="67912-103">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="67912-104">Toto téma popisuje různé způsoby, jak můžete zpřístupnit data pro vazby v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] závislosti na potřebách vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="67912-104">This topic discusses various ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67912-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="67912-105">Example</span></span>  
 <span data-ttu-id="67912-106">Pokud máte objekt modulu CLR (Common Language Runtime), na který chcete vytvořit vazbu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , jedním ze způsobů, jak lze objekt zpřístupnit pro vazbu, je definovat jako prostředek a poskytnout mu `x:Key` .</span><span class="sxs-lookup"><span data-stu-id="67912-106">If you have a common language runtime (CLR) object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="67912-107">V následujícím příkladu máte `Person` objekt s vlastností řetězce s názvem `PersonName` .</span><span class="sxs-lookup"><span data-stu-id="67912-107">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="67912-108">`Person`Objekt (v zobrazeném řádku, který obsahuje `<src>` element) je definován v oboru názvů s názvem `SDKSample` .</span><span class="sxs-lookup"><span data-stu-id="67912-108">The `Person` object (in the line shown highlighted that contains the `<src>` element) is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="67912-109">Ovládací prvek lze následně navazovat <xref:System.Windows.Controls.TextBlock> na objekt v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , protože zvýrazněný řádek, který obsahuje prvek, se `<TextBlock>` zobrazí.</span><span class="sxs-lookup"><span data-stu-id="67912-109">You can then bind the <xref:System.Windows.Controls.TextBlock> control to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as the highlighted line that contains the `<TextBlock>` element shows.</span></span>
  
 <span data-ttu-id="67912-110">Alternativně můžete použít <xref:System.Windows.Data.ObjectDataProvider> třídu, jak je uvedeno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="67912-110">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example:</span></span>  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 <span data-ttu-id="67912-111">Vazbu lze definovat stejným způsobem jako zvýrazněný řádek, který obsahuje `<TextBlock>` prvek.</span><span class="sxs-lookup"><span data-stu-id="67912-111">You define the binding the same way, as the highlighted line that contains the `<TextBlock>` element shows.</span></span>  
  
 <span data-ttu-id="67912-112">V tomto konkrétním příkladu je výsledek stejný: máte <xref:System.Windows.Controls.TextBlock> textový obsah `Joe` .</span><span class="sxs-lookup"><span data-stu-id="67912-112">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="67912-113"><xref:System.Windows.Data.ObjectDataProvider>Třída však poskytuje funkce, jako je možnost svázání s výsledkem metody.</span><span class="sxs-lookup"><span data-stu-id="67912-113">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="67912-114">Můžete použít <xref:System.Windows.Data.ObjectDataProvider> třídu, pokud potřebujete funkce, které poskytuje.</span><span class="sxs-lookup"><span data-stu-id="67912-114">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="67912-115">Pokud však vytváříte vazbu na objekt, který již byl vytvořen, je nutné nastavit `DataContext` v kódu, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="67912-115">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="67912-116">Chcete-li získat přístup k datům XML pro vazbu pomocí <xref:System.Windows.Data.XmlDataProvider> třídy, přečtěte si téma [vazba na data XML pomocí dotazů XmlDataProvider a XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span><span class="sxs-lookup"><span data-stu-id="67912-116">To access XML data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="67912-117">Chcete-li získat přístup k datům XML pro vazbu pomocí <xref:System.Windows.Data.ObjectDataProvider> třídy, přečtěte si téma [vazba na XDocument, XELEMENT nebo LINQ pro výsledky dotazu XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span><span class="sxs-lookup"><span data-stu-id="67912-117">To access XML data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="67912-118">Informace o mnoha způsobech, kterými můžete zadat data, k jejichž vytváření vytváříte, najdete v tématu [určení zdroje vazby](how-to-specify-the-binding-source.md).</span><span class="sxs-lookup"><span data-stu-id="67912-118">For information about many ways you can specify the data you are binding to, see [Specify the Binding Source](how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="67912-119">Informace o tom, jaké typy dat můžete svázat nebo jak implementovat vlastní objekty modulu CLR (Common Language Runtime) pro vazbu, najdete v tématu [Přehled zdrojů vazby](binding-sources-overview.md).</span><span class="sxs-lookup"><span data-stu-id="67912-119">For information about what types of data you can bind to or how to implement your own common language runtime (CLR) objects for binding, see [Binding Sources Overview](binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67912-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="67912-120">See also</span></span>

- [<span data-ttu-id="67912-121">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="67912-121">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="67912-122">– postupy</span><span class="sxs-lookup"><span data-stu-id="67912-122">How-to Topics</span></span>](data-binding-how-to-topics.md)
