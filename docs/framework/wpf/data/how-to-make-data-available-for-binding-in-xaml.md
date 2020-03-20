---
title: 'Postupy: Zpřístupnění dat pro připojení v jazyku XAML'
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 91e89dbf36024c31f4afcd9b6d956944baf13576
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174183"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="43c27-102">Postupy: Zpřístupnění dat pro připojení v jazyku XAML</span><span class="sxs-lookup"><span data-stu-id="43c27-102">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="43c27-103">Toto téma popisuje různé způsoby, jak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]můžete zpřístupnit data pro vazbu v aplikaci v závislosti na potřebách aplikace.</span><span class="sxs-lookup"><span data-stu-id="43c27-103">This topic discusses various ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43c27-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="43c27-104">Example</span></span>  
 <span data-ttu-id="43c27-105">Pokud máte objekt CLR (COMMON Language runtime), na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]který chcete vytvořit vazbu `x:Key`, jedním ze způsobů, jak objekt zpřístupnit pro vazbu, je definovat jej jako prostředek a poskytnout mu .</span><span class="sxs-lookup"><span data-stu-id="43c27-105">If you have a common language runtime (CLR) object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="43c27-106">V následujícím příkladu máte `Person` objekt s vlastností string s názvem `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="43c27-106">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="43c27-107">Objekt `Person` (v zobrazeném řádku, `<src>` který obsahuje prvek) je `SDKSample`definován v oboru názvů nazývaném .</span><span class="sxs-lookup"><span data-stu-id="43c27-107">The `Person` object (in the line shown highlighted that contains the `<src>` element) is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="43c27-108">Potom můžete svázat <xref:System.Windows.Controls.TextBlock> ovládací prvek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]s objektem v , `<TextBlock>` jak ukazuje zvýrazněný řádek, který obsahuje prvek.</span><span class="sxs-lookup"><span data-stu-id="43c27-108">You can then bind the <xref:System.Windows.Controls.TextBlock> control to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as the highlighted line that contains the `<TextBlock>` element shows.</span></span>
  
 <span data-ttu-id="43c27-109">Případně můžete použít třídu, <xref:System.Windows.Data.ObjectDataProvider> jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="43c27-109">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example:</span></span>  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 <span data-ttu-id="43c27-110">Vazbu definujete stejným způsobem, jako se zobrazí `<TextBlock>` zvýrazněný řádek, který obsahuje prvek.</span><span class="sxs-lookup"><span data-stu-id="43c27-110">You define the binding the same way, as the highlighted line that contains the `<TextBlock>` element shows.</span></span>  
  
 <span data-ttu-id="43c27-111">V tomto konkrétním příkladu je výsledek stejný: máte <xref:System.Windows.Controls.TextBlock> `Joe`s textovým obsahem .</span><span class="sxs-lookup"><span data-stu-id="43c27-111">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="43c27-112">Třída však <xref:System.Windows.Data.ObjectDataProvider> poskytuje funkce, jako je například schopnost vázat na výsledek metody.</span><span class="sxs-lookup"><span data-stu-id="43c27-112">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="43c27-113">Třídu můžete použít, <xref:System.Windows.Data.ObjectDataProvider> pokud potřebujete funkce, které poskytuje.</span><span class="sxs-lookup"><span data-stu-id="43c27-113">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="43c27-114">Pokud však jste vazby na objekt, který již byl `DataContext` vytvořen, je třeba nastavit v kódu, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="43c27-114">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="43c27-115">Informace o přístupu k <xref:System.Windows.Data.XmlDataProvider> datům XML pro vazbu pomocí třídy naleznete [v tématu Vazba na data XML pomocí dotazů XMLDataProvider a XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span><span class="sxs-lookup"><span data-stu-id="43c27-115">To access XML data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="43c27-116">Informace o přístupu k <xref:System.Windows.Data.ObjectDataProvider> datům XML pro vazbu pomocí třídy naleznete v [tématu Vazba na XDocument, XElement nebo LINQ pro výsledky dotazů XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span><span class="sxs-lookup"><span data-stu-id="43c27-116">To access XML data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="43c27-117">Informace o mnoha způsobech, jak můžete určit data, ke které jste vazby, naleznete [v tématu Určení zdroje vazby](how-to-specify-the-binding-source.md).</span><span class="sxs-lookup"><span data-stu-id="43c27-117">For information about many ways you can specify the data you are binding to, see [Specify the Binding Source](how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="43c27-118">Informace o tom, jaké typy dat můžete vázat nebo jak implementovat vlastní objekty CLR (COMMON Language runtime) pro vazbu, naleznete v [tématu Přehled zdrojů vazby](binding-sources-overview.md).</span><span class="sxs-lookup"><span data-stu-id="43c27-118">For information about what types of data you can bind to or how to implement your own common language runtime (CLR) objects for binding, see [Binding Sources Overview](binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43c27-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="43c27-119">See also</span></span>

- [<span data-ttu-id="43c27-120">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="43c27-120">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="43c27-121">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="43c27-121">How-to Topics</span></span>](data-binding-how-to-topics.md)
