---
title: 'Postupy: Připojení k webové službě'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], Web service
- Web service binding [WPF]
- data binding [WPF], Web service
ms.assetid: 77e2d373-69ba-4cbd-b6f5-2c83c38fc98b
ms.openlocfilehash: 75d9d5b6981f868c7a172edd7f23cf923fedd525
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557287"
---
# <a name="how-to-bind-to-a-web-service"></a><span data-ttu-id="6935b-102">Postupy: Připojení k webové službě</span><span class="sxs-lookup"><span data-stu-id="6935b-102">How to: Bind to a Web Service</span></span>
<span data-ttu-id="6935b-103">Tento příklad ukazuje, jak vytvořit vazbu na objektů vrácený volání metody webové služby.</span><span class="sxs-lookup"><span data-stu-id="6935b-103">This example shows how to bind to objects returned by Web service method calls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6935b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="6935b-104">Example</span></span>  
 <span data-ttu-id="6935b-105">Tento příklad používá [služba obsah na webu MSDN nebo TechNet publikování systému (MTPS)](http://go.microsoft.com/fwlink/?LinkId=95677) načíst seznam jazyků – podpora zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="6935b-105">This example uses the [MSDN/TechNet Publishing System (MTPS) Content Service](http://go.microsoft.com/fwlink/?LinkId=95677) to retrieve the list of languages supported by a specified document.</span></span>  
  
 <span data-ttu-id="6935b-106">Před voláním webové služby, musíte vytvořit odkaz na něj.</span><span class="sxs-lookup"><span data-stu-id="6935b-106">Before you call a Web service, you need to create a reference to it.</span></span> <span data-ttu-id="6935b-107">Chcete-li vytvořit odkaz na použití služby MTPS [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="6935b-107">To create a Web reference to the MTPS service using [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], follow the following steps:</span></span>  
  
1.  <span data-ttu-id="6935b-108">Otevřete projekt v [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6935b-108">Open your project in [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].</span></span>  
  
2.  <span data-ttu-id="6935b-109">Z **projektu** nabídky, klikněte na tlačítko **přidat odkaz na Web**.</span><span class="sxs-lookup"><span data-stu-id="6935b-109">From the **Project** menu, click **Add Web Reference**.</span></span>  
  
3.  <span data-ttu-id="6935b-110">V dialogovém okně Nastavení **URL** k [ http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl ](http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span><span class="sxs-lookup"><span data-stu-id="6935b-110">In the dialog box, set the **URL** to [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span></span>  
  
4.  <span data-ttu-id="6935b-111">Stiskněte klávesu **přejděte** a potom **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="6935b-111">Press **Go** and then **Add Reference**.</span></span>  
  
 <span data-ttu-id="6935b-112">Pak zavolejte metodu webové služby a nastavte <xref:System.Windows.FrameworkElement.DataContext%2A> vhodný ovládací prvek nebo okna vráceného objektu.</span><span class="sxs-lookup"><span data-stu-id="6935b-112">Next, you call the Web service method and set the <xref:System.Windows.FrameworkElement.DataContext%2A> of the appropriate control or window to the returned object.</span></span> <span data-ttu-id="6935b-113">**GetContent** metoda služby MTPS přebírá odkaz na **getContentRequest** objektu.</span><span class="sxs-lookup"><span data-stu-id="6935b-113">The **GetContent** method of the MTPS service takes a reference to the **getContentRequest** object.</span></span> <span data-ttu-id="6935b-114">Následující příklad proto nejprve nastavuje objekt žádosti:</span><span class="sxs-lookup"><span data-stu-id="6935b-114">Therefore, the following example first sets up a request object:</span></span>  
  
 [!code-csharp[BindToWebService#Namespace](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 <span data-ttu-id="6935b-115">Po <xref:System.Windows.FrameworkElement.DataContext%2A> byl nastaven, můžete vytvořit vazby vlastností objektu, který <xref:System.Windows.FrameworkElement.DataContext%2A> byla nastavena na.</span><span class="sxs-lookup"><span data-stu-id="6935b-115">After the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set, you can create bindings to the properties of the object that the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set to.</span></span> <span data-ttu-id="6935b-116">V tomto příkladu <xref:System.Windows.FrameworkElement.DataContext%2A> je nastaven na **getContentResponse** objekt vrácený **GetContent** metoda.</span><span class="sxs-lookup"><span data-stu-id="6935b-116">In this example, the <xref:System.Windows.FrameworkElement.DataContext%2A> is set to the **getContentResponse** object returned by the **GetContent** method.</span></span> <span data-ttu-id="6935b-117">V následujícím příkladu <xref:System.Windows.Controls.ItemsControl> váže a zobrazí **národního prostředí** hodnoty **availableVersionsAndLocales** z **getContentResponse**.</span><span class="sxs-lookup"><span data-stu-id="6935b-117">In the following example, the <xref:System.Windows.Controls.ItemsControl> binds to and displays the **locale** values of **availableVersionsAndLocales** of **getContentResponse**.</span></span>  
  
 [!code-xaml[BindToWebService#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 <span data-ttu-id="6935b-118">Informace o struktuře **getContentResponse**, najdete v části [služba obsah dokumentaci](http://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span><span class="sxs-lookup"><span data-stu-id="6935b-118">For information about the structure of **getContentResponse**, see [Content Service documentation](http://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6935b-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="6935b-119">See Also</span></span>  
 [<span data-ttu-id="6935b-120">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="6935b-120">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="6935b-121">Přehled zdrojů vazby</span><span class="sxs-lookup"><span data-stu-id="6935b-121">Binding Sources Overview</span></span>](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [<span data-ttu-id="6935b-122">Zpřístupnění dat pro vazbu v jazyku XAML</span><span class="sxs-lookup"><span data-stu-id="6935b-122">Make Data Available for Binding in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)
