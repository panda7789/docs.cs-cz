---
title: "Postupy: Zpřístupnění dat pro připojení v jazyku XAML"
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
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c342f0d635a9220a88a2af79c76e2c1580dee2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="83cb0-102">Postupy: Zpřístupnění dat pro připojení v jazyku XAML</span><span class="sxs-lookup"><span data-stu-id="83cb0-102">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="83cb0-103">Toto téma popisuje různé způsoby můžete zpřístupnit data pro vazbu v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], v závislosti na potřebách vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="83cb0-103">This topic discusses the different ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83cb0-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="83cb0-104">Example</span></span>  
 <span data-ttu-id="83cb0-105">Pokud máte [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objektu, kterou chcete vytvořit vazbu k z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jedním ze způsobů, které můžete zpřístupnit objekt vazba je pro definování jako prostředek a pojmenujte ho `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="83cb0-105">If you have a [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="83cb0-106">V následujícím příkladu, máte `Person` objekt s řetězec vlastnost s názvem `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="83cb0-106">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="83cb0-107">`Person` Objekt je definován v oboru názvů názvem `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="83cb0-107">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#instantiation)]  
[!code-xaml[SimpleBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#2)]  
  
 <span data-ttu-id="83cb0-108">Potom můžete vázat na objekt v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="83cb0-108">You can then bind to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as shown in the following example.</span></span>  
  
 [!code-xaml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 <span data-ttu-id="83cb0-109">Alternativně můžete použít <xref:System.Windows.Data.ObjectDataProvider> třídy, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="83cb0-109">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example.</span></span>  
  
 [!code-xaml[SimpleBinding#ODPCP](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml#odpcp)]  
  
 <span data-ttu-id="83cb0-110">Můžete definovat vazby stejným způsobem jako:</span><span class="sxs-lookup"><span data-stu-id="83cb0-110">You define the binding the same way:</span></span>  
  
 [!code-xaml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 <span data-ttu-id="83cb0-111">V tomto konkrétním příkladu je výsledek stejný: máte <xref:System.Windows.Controls.TextBlock> s textového obsahu `Joe`.</span><span class="sxs-lookup"><span data-stu-id="83cb0-111">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="83cb0-112">Ale <xref:System.Windows.Data.ObjectDataProvider> třída poskytuje funkce, jako je možnost vytvořit vazbu na výsledek metody.</span><span class="sxs-lookup"><span data-stu-id="83cb0-112">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="83cb0-113">Můžete použít <xref:System.Windows.Data.ObjectDataProvider> třídy, pokud potřebujete funkci poskytuje.</span><span class="sxs-lookup"><span data-stu-id="83cb0-113">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="83cb0-114">Ale pokud vytváříte vazbu na objekt, který byl vytvořen, budete muset nastavit `DataContext` v kódu, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="83cb0-114">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="83cb0-115">Pro přístup k [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dat pro použití vazby <xref:System.Windows.Data.XmlDataProvider> třídy najdete v tématu [vazby na Data XML pomocí služby XMLDataProvider a dotazy jazyka XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span><span class="sxs-lookup"><span data-stu-id="83cb0-115">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="83cb0-116">Pro přístup k [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dat pro použití vazby <xref:System.Windows.Data.ObjectDataProvider> třídy najdete v tématu [vytvořit vazbu na XDocument, XElement nebo LINQ na výsledky dotazu XML](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span><span class="sxs-lookup"><span data-stu-id="83cb0-116">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="83cb0-117">Informace o různých způsobech, můžete zadat data jsou vytvoření vazby na najdete v tématu [určit zdroj vazby](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md).</span><span class="sxs-lookup"><span data-stu-id="83cb0-117">For information about the different ways you can specify the data you are binding to, see [Specify the Binding Source](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="83cb0-118">Informace o jaké typy dat můžete vázat na nebo jak implementovat vlastní [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objekty pro vazbu, najdete v části [Přehled zdrojů vazby](../../../../docs/framework/wpf/data/binding-sources-overview.md).</span><span class="sxs-lookup"><span data-stu-id="83cb0-118">For information about what types of data you can bind to or how to implement your own [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objects for binding, see [Binding Sources Overview](../../../../docs/framework/wpf/data/binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83cb0-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="83cb0-119">See Also</span></span>  
 [<span data-ttu-id="83cb0-120">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="83cb0-120">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="83cb0-121">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="83cb0-121">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
