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
ms.openlocfilehash: 3a3f6edc974448ddab9fe30e97bdc1130d3b97dc
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449969"
---
# <a name="how-to-bind-to-a-web-service"></a><span data-ttu-id="cd151-102">Postupy: Připojení k webové službě</span><span class="sxs-lookup"><span data-stu-id="cd151-102">How to: Bind to a Web Service</span></span>
<span data-ttu-id="cd151-103">Tento příklad ukazuje, jak vytvořit vazby k objektům vráceným voláními metody webové služby.</span><span class="sxs-lookup"><span data-stu-id="cd151-103">This example shows how to bind to objects returned by Web service method calls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd151-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd151-104">Example</span></span>  
 <span data-ttu-id="cd151-105">V tomto příkladu se používá služba obsahu MTPS (MSDN/TechNet Publishing System) k načtení seznamu jazyků podporovaných zadaným dokumentem.</span><span class="sxs-lookup"><span data-stu-id="cd151-105">This example uses the MSDN/TechNet Publishing System (MTPS) Content Service to retrieve the list of languages supported by a specified document.</span></span>  
  
 <span data-ttu-id="cd151-106">Před voláním webové služby je nutné vytvořit odkaz na ni.</span><span class="sxs-lookup"><span data-stu-id="cd151-106">Before you call a Web service, you need to create a reference to it.</span></span> <span data-ttu-id="cd151-107">Chcete-li vytvořit webový odkaz na službu MTPS pomocí sady Visual Studio, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="cd151-107">To create a Web reference to the MTPS service using Visual Studio, follow the following steps:</span></span>  
  
1. <span data-ttu-id="cd151-108">Otevřete projekt v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cd151-108">Open your project in Visual Studio.</span></span>  
  
2. <span data-ttu-id="cd151-109">V nabídce **projekt** klikněte na příkaz **Přidat webový odkaz**.</span><span class="sxs-lookup"><span data-stu-id="cd151-109">From the **Project** menu, click **Add Web Reference**.</span></span>  
  
3. <span data-ttu-id="cd151-110">V dialogovém okně nastavte **adresu URL** na [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span><span class="sxs-lookup"><span data-stu-id="cd151-110">In the dialog box, set the **URL** to [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span></span>  
  
4. <span data-ttu-id="cd151-111">Stiskněte tlačítko **Přejít** a pak **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="cd151-111">Press **Go** and then **Add Reference**.</span></span>  
  
 <span data-ttu-id="cd151-112">Dále zavoláte metodu webové služby a nastavíte <xref:System.Windows.FrameworkElement.DataContext%2A> příslušného ovládacího prvku nebo okna na vrácený objekt.</span><span class="sxs-lookup"><span data-stu-id="cd151-112">Next, you call the Web service method and set the <xref:System.Windows.FrameworkElement.DataContext%2A> of the appropriate control or window to the returned object.</span></span> <span data-ttu-id="cd151-113">Metoda `GetContent` služby MTPS používá odkaz na objekt `getContentRequest`.</span><span class="sxs-lookup"><span data-stu-id="cd151-113">The `GetContent` method of the MTPS service takes a reference to the `getContentRequest` object.</span></span> <span data-ttu-id="cd151-114">Proto následující příklad nejprve nastaví objekt žádosti:</span><span class="sxs-lookup"><span data-stu-id="cd151-114">Therefore, the following example first sets up a request object:</span></span>  
  
 [!code-csharp[BindToWebService#Namespace](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 <span data-ttu-id="cd151-115">Po nastavení <xref:System.Windows.FrameworkElement.DataContext%2A> můžete vytvořit vazby na vlastnosti objektu, na který byl <xref:System.Windows.FrameworkElement.DataContext%2A> nastaven.</span><span class="sxs-lookup"><span data-stu-id="cd151-115">After the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set, you can create bindings to the properties of the object that the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set to.</span></span> <span data-ttu-id="cd151-116">V tomto příkladu je <xref:System.Windows.FrameworkElement.DataContext%2A> nastavena na objekt `getContentResponse` vrácený metodou `GetContent`.</span><span class="sxs-lookup"><span data-stu-id="cd151-116">In this example, the <xref:System.Windows.FrameworkElement.DataContext%2A> is set to the `getContentResponse` object returned by the `GetContent` method.</span></span> <span data-ttu-id="cd151-117">V následujícím příkladu se <xref:System.Windows.Controls.ItemsControl> váže k a zobrazí `locale` hodnoty `availableVersionsAndLocales` `getContentResponse`.</span><span class="sxs-lookup"><span data-stu-id="cd151-117">In the following example, the <xref:System.Windows.Controls.ItemsControl> binds to and displays the `locale` values of `availableVersionsAndLocales` of `getContentResponse`.</span></span>  
  
 [!code-xaml[BindToWebService#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 <span data-ttu-id="cd151-118">Informace o struktuře `getContentResponse`najdete v [dokumentaci ke službě obsahu](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span><span class="sxs-lookup"><span data-stu-id="cd151-118">For information about the structure of `getContentResponse`, see [Content Service documentation](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd151-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd151-119">See also</span></span>

- [<span data-ttu-id="cd151-120">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="cd151-120">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="cd151-121">Přehled zdrojů vazby</span><span class="sxs-lookup"><span data-stu-id="cd151-121">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="cd151-122">Zpřístupnění dat pro vazbu v jazyku XAML</span><span class="sxs-lookup"><span data-stu-id="cd151-122">Make Data Available for Binding in XAML</span></span>](how-to-make-data-available-for-binding-in-xaml.md)
