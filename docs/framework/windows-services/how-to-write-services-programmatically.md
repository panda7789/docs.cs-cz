---
title: 'Postupy: Zápis služeb prostřednictvím kódu programu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
author: ghogen
manager: douge
ms.openlocfilehash: 99fd44723bba21127e2a5e0ba3e9bfc4b90b52d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-services-programmatically"></a><span data-ttu-id="54305-102">Postupy: Zápis služeb prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="54305-102">How to: Write Services Programmatically</span></span>
<span data-ttu-id="54305-103">Pokud se rozhodnete použít projektu šablony služeb systému Windows, můžete napsat vlastní služby nastavením dědičnosti a dalších prvků infrastruktury sami.</span><span class="sxs-lookup"><span data-stu-id="54305-103">If you choose not to use the Windows Service project template, you can write your own services by setting up the inheritance and other infrastructure elements yourself.</span></span> <span data-ttu-id="54305-104">Při vytváření služby prostřednictvím kódu programu, je třeba provést několik kroků, které pro vás by jinak zpracovat šablony:</span><span class="sxs-lookup"><span data-stu-id="54305-104">When you create a service programmatically, you must perform several steps that the template would otherwise handle for you:</span></span>  
  
-   <span data-ttu-id="54305-105">Třídě služby je potřeba nastavit dědění z <xref:System.ServiceProcess.ServiceBase> třídy.</span><span class="sxs-lookup"><span data-stu-id="54305-105">You must set up your service class to inherit from the <xref:System.ServiceProcess.ServiceBase> class.</span></span>  
  
-   <span data-ttu-id="54305-106">Musíte vytvořit `Main` metodu pro projekt služby, který definuje spuštění služeb a volání <xref:System.ServiceProcess.ServiceBase.Run%2A> metoda na ně.</span><span class="sxs-lookup"><span data-stu-id="54305-106">You must create a `Main` method for your service project that defines the services to run and calls the <xref:System.ServiceProcess.ServiceBase.Run%2A> method on them.</span></span>  
  
-   <span data-ttu-id="54305-107">Je nutné přepsat <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedury a vyplňte kód, chcete, aby se spouštěly.</span><span class="sxs-lookup"><span data-stu-id="54305-107">You must override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures and fill in any code you want them to run.</span></span>  
  
### <a name="to-write-a-service-programmatically"></a><span data-ttu-id="54305-108">Pro zápis služby prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="54305-108">To write a service programmatically</span></span>  
  
1.  <span data-ttu-id="54305-109">Vytvořit prázdný projekt a vytvořte odkaz na obory názvů potřeby pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="54305-109">Create an empty project and create a reference to the necessary namespaces by following these steps:</span></span>  
  
    1.  <span data-ttu-id="54305-110">V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **odkazy** uzel a klikněte na tlačítko **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="54305-110">In **Solution Explorer**, right-click the **References** node and click **Add Reference**.</span></span>  
  
    2.  <span data-ttu-id="54305-111">Na **rozhraní .NET Framework** kartě, přejděte na **System.dll** a klikněte na tlačítko **vyberte**.</span><span class="sxs-lookup"><span data-stu-id="54305-111">On the **.NET Framework** tab, scroll to **System.dll** and click **Select**.</span></span>  
  
    3.  <span data-ttu-id="54305-112">Přejděte na **System.ServiceProcess.dll** a klikněte na tlačítko **vyberte**.</span><span class="sxs-lookup"><span data-stu-id="54305-112">Scroll to **System.ServiceProcess.dll** and click **Select**.</span></span>  
  
    4.  <span data-ttu-id="54305-113">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="54305-113">Click **OK**.</span></span>  
  
2.  <span data-ttu-id="54305-114">Přidejte třídu a nakonfigurujte ji dědění z <xref:System.ServiceProcess.ServiceBase>:</span><span class="sxs-lookup"><span data-stu-id="54305-114">Add a class and configure it to inherit from <xref:System.ServiceProcess.ServiceBase>:</span></span>  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3.  <span data-ttu-id="54305-115">Přidejte následující kód do konfigurace vaší služby třídy:</span><span class="sxs-lookup"><span data-stu-id="54305-115">Add the following code to configure your service class:</span></span>  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4.  <span data-ttu-id="54305-116">Vytvoření `Main` metody pro třídu a použijte jej k definování službu bude obsahovat vlastní třídy; `userService1` je název třídy:</span><span class="sxs-lookup"><span data-stu-id="54305-116">Create a `Main` method for your class, and use it to define the service your class will contain; `userService1` is the name of the class:</span></span>  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5.  <span data-ttu-id="54305-117">Přepsání <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda a definujte jakékoli zpracovávání chcete dojít, když je spuštěna.</span><span class="sxs-lookup"><span data-stu-id="54305-117">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and define any processing you want to occur when your service is started.</span></span>  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6.  <span data-ttu-id="54305-118">Přepsat jiné metody, které chcete definovat vlastní zpracování a napsat kód, aby určila provedení akcí, kterou služba má provést v každém případu.</span><span class="sxs-lookup"><span data-stu-id="54305-118">Override any other methods you want to define custom processing for, and write code to determine the actions the service should take in each case.</span></span>  
  
7.  <span data-ttu-id="54305-119">Přidejte nezbytné instalační programy pro aplikaci služby.</span><span class="sxs-lookup"><span data-stu-id="54305-119">Add the necessary installers for your service application.</span></span> <span data-ttu-id="54305-120">Další informace najdete v tématu [postupy: Přidání instalačních programů pro vaše aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="54305-120">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
8.  <span data-ttu-id="54305-121">Sestavení projektu výběrem **sestavit řešení** z **sestavení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="54305-121">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="54305-122">Není stisknutím klávesy F5 spusťte projekt – služba projektu nelze spustit tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="54305-122">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
9. <span data-ttu-id="54305-123">Vytvoření projektu instalace a vlastní akce pro instalaci služby.</span><span class="sxs-lookup"><span data-stu-id="54305-123">Create a setup project and the custom actions to install your service.</span></span> <span data-ttu-id="54305-124">Příklad, naleznete v části [návod: vytváření aplikace služby systému Windows v Návrháři součástí](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="54305-124">For an example, see [Walkthrough: Creating a Windows Service Application in the Component Designer](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
10. <span data-ttu-id="54305-125">Nainstalujte službu.</span><span class="sxs-lookup"><span data-stu-id="54305-125">Install the service.</span></span> <span data-ttu-id="54305-126">Další informace najdete v tématu [postupy: instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="54305-126">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54305-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="54305-127">See Also</span></span>  
 [<span data-ttu-id="54305-128">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="54305-128">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="54305-129">Postupy: Vytváření služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="54305-129">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [<span data-ttu-id="54305-130">Postupy: Přidání instalačních programů do aplikace služby</span><span class="sxs-lookup"><span data-stu-id="54305-130">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="54305-131">Postupy: Protokolování informací o službách</span><span class="sxs-lookup"><span data-stu-id="54305-131">How to: Log Information About Services</span></span>](../../../docs/framework/windows-services/how-to-log-information-about-services.md)  
 [<span data-ttu-id="54305-132">Návod: Vytvoření aplikace služby systému Windows v návrháři součástí</span><span class="sxs-lookup"><span data-stu-id="54305-132">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
