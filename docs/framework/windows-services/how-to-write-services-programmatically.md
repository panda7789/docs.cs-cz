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
ms.openlocfilehash: 5637d569ad5261bff6865af4ab2ed8b7631d2d38
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053562"
---
# <a name="how-to-write-services-programmatically"></a><span data-ttu-id="d4856-102">Postupy: Zápis služeb prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="d4856-102">How to: Write Services Programmatically</span></span>
<span data-ttu-id="d4856-103">Pokud se rozhodnete nepoužívat šablonu projektu služby systému Windows, můžete napsat vlastní služby nastavením dědičnosti a dalších prvků infrastruktury sami.</span><span class="sxs-lookup"><span data-stu-id="d4856-103">If you choose not to use the Windows Service project template, you can write your own services by setting up the inheritance and other infrastructure elements yourself.</span></span> <span data-ttu-id="d4856-104">Když vytvoříte službu programově, je nutné provést několik kroků, které vám jinak, než to šablona zpracuje:</span><span class="sxs-lookup"><span data-stu-id="d4856-104">When you create a service programmatically, you must perform several steps that the template would otherwise handle for you:</span></span>  
  
- <span data-ttu-id="d4856-105">Je nutné nastavit třídu služby tak, aby dědila z <xref:System.ServiceProcess.ServiceBase> třídy.</span><span class="sxs-lookup"><span data-stu-id="d4856-105">You must set up your service class to inherit from the <xref:System.ServiceProcess.ServiceBase> class.</span></span>  
  
- <span data-ttu-id="d4856-106">Musíte vytvořit `Main` metodu pro projekt služby, který definuje služby, které mají být spuštěny, a <xref:System.ServiceProcess.ServiceBase.Run%2A> zavolá metodu na nich.</span><span class="sxs-lookup"><span data-stu-id="d4856-106">You must create a `Main` method for your service project that defines the services to run and calls the <xref:System.ServiceProcess.ServiceBase.Run%2A> method on them.</span></span>  
  
- <span data-ttu-id="d4856-107">Musíte přepsat postupy <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> a vyplnit libovolný kód, který chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="d4856-107">You must override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures and fill in any code you want them to run.</span></span>  
  
### <a name="to-write-a-service-programmatically"></a><span data-ttu-id="d4856-108">Programové vytvoření služby</span><span class="sxs-lookup"><span data-stu-id="d4856-108">To write a service programmatically</span></span>  
  
1. <span data-ttu-id="d4856-109">Pomocí následujících kroků vytvořte prázdný projekt a vytvořte odkaz na potřebné obory názvů:</span><span class="sxs-lookup"><span data-stu-id="d4856-109">Create an empty project and create a reference to the necessary namespaces by following these steps:</span></span>  
  
    1. <span data-ttu-id="d4856-110">V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **odkazy** a klikněte na **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="d4856-110">In **Solution Explorer**, right-click the **References** node and click **Add Reference**.</span></span>  
  
    2. <span data-ttu-id="d4856-111">Na kartě **.NET Framework** přejděte na **System. dll** a klikněte na **Vybrat**.</span><span class="sxs-lookup"><span data-stu-id="d4856-111">On the **.NET Framework** tab, scroll to **System.dll** and click **Select**.</span></span>  
  
    3. <span data-ttu-id="d4856-112">Přejděte na **System. ServiceProcess. dll** a klikněte na **Vybrat**.</span><span class="sxs-lookup"><span data-stu-id="d4856-112">Scroll to **System.ServiceProcess.dll** and click **Select**.</span></span>  
  
    4. <span data-ttu-id="d4856-113">Klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="d4856-113">Click **OK**.</span></span>  
  
2. <span data-ttu-id="d4856-114">Přidejte třídu a nakonfigurujte ji, aby dědila <xref:System.ServiceProcess.ServiceBase>:</span><span class="sxs-lookup"><span data-stu-id="d4856-114">Add a class and configure it to inherit from <xref:System.ServiceProcess.ServiceBase>:</span></span>  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3. <span data-ttu-id="d4856-115">Přidejte následující kód pro konfiguraci třídy služby:</span><span class="sxs-lookup"><span data-stu-id="d4856-115">Add the following code to configure your service class:</span></span>  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4. <span data-ttu-id="d4856-116">Vytvořte `Main` metodu pro třídu a použijte ji k definování služby, kterou bude vaše třída obsahovat; `userService1` je název třídy:</span><span class="sxs-lookup"><span data-stu-id="d4856-116">Create a `Main` method for your class, and use it to define the service your class will contain; `userService1` is the name of the class:</span></span>  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5. <span data-ttu-id="d4856-117">Přepište <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodu a definujte jakékoli zpracování, které má být provedeno při spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="d4856-117">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and define any processing you want to occur when your service is started.</span></span>  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6. <span data-ttu-id="d4856-118">Přepište jakékoli jiné metody, pro které chcete definovat vlastní zpracování, a napište kód, který určí akce, které by měla služba provádět v každém případě.</span><span class="sxs-lookup"><span data-stu-id="d4856-118">Override any other methods you want to define custom processing for, and write code to determine the actions the service should take in each case.</span></span>  
  
7. <span data-ttu-id="d4856-119">Přidejte nezbytné instalační programy pro aplikaci služby.</span><span class="sxs-lookup"><span data-stu-id="d4856-119">Add the necessary installers for your service application.</span></span> <span data-ttu-id="d4856-120">Další informace najdete v tématu [Postup: Přidání instalačních programů do aplikace služby](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="d4856-120">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>  
  
8. <span data-ttu-id="d4856-121">Sestavte projekt výběrem možnosti **Sestavit řešení** v nabídce **sestavení** .</span><span class="sxs-lookup"><span data-stu-id="d4856-121">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d4856-122">Netiskněte klávesu F5 pro spuštění projektu – projekt služby nemůžete tímto způsobem spustit.</span><span class="sxs-lookup"><span data-stu-id="d4856-122">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
9. <span data-ttu-id="d4856-123">Vytvořte projekt instalace a vlastní akce pro instalaci služby.</span><span class="sxs-lookup"><span data-stu-id="d4856-123">Create a setup project and the custom actions to install your service.</span></span> <span data-ttu-id="d4856-124">Příklad naleznete v tématu [Návod: Vytvoření aplikace služby systému Windows v Návrháři komponent](walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="d4856-124">For an example, see [Walkthrough: Creating a Windows Service Application in the Component Designer](walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
10. <span data-ttu-id="d4856-125">Nainstalujte službu.</span><span class="sxs-lookup"><span data-stu-id="d4856-125">Install the service.</span></span> <span data-ttu-id="d4856-126">Další informace najdete v tématu [Postupy: instalace a odinstalace služeb](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="d4856-126">For more information, see [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4856-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4856-127">See also</span></span>

- [<span data-ttu-id="d4856-128">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="d4856-128">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="d4856-129">Postupy: Vytváření služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="d4856-129">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)
- [<span data-ttu-id="d4856-130">Postupy: Přidání instalačních programů do aplikace služby</span><span class="sxs-lookup"><span data-stu-id="d4856-130">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="d4856-131">Postupy: Zaznamenávání informací o službách</span><span class="sxs-lookup"><span data-stu-id="d4856-131">How to: Log Information About Services</span></span>](how-to-log-information-about-services.md)
- [<span data-ttu-id="d4856-132">Návod: Vytvoření aplikace služby systému Windows v návrháři součástí</span><span class="sxs-lookup"><span data-stu-id="d4856-132">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
