---
title: 'Postupy: Zápis služeb prostřednictvím kódu programu'
description: Nastavení dědičnosti a dalších prvků infrastruktury můžete zobrazit tak, že si nastavili způsob, jak psát služby programově.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
author: ghogen
ms.openlocfilehash: 9693e3d387f38319519ab04211d8219fe1e5dda1
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925706"
---
# <a name="how-to-write-services-programmatically"></a><span data-ttu-id="a0eca-103">Postupy: Zápis služeb prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="a0eca-103">How to: Write Services Programmatically</span></span>
<span data-ttu-id="a0eca-104">Pokud se rozhodnete nepoužívat šablonu projektu služby systému Windows, můžete napsat vlastní služby nastavením dědičnosti a dalších prvků infrastruktury sami.</span><span class="sxs-lookup"><span data-stu-id="a0eca-104">If you choose not to use the Windows Service project template, you can write your own services by setting up the inheritance and other infrastructure elements yourself.</span></span> <span data-ttu-id="a0eca-105">Když vytvoříte službu programově, je nutné provést několik kroků, které vám jinak, než to šablona zpracuje:</span><span class="sxs-lookup"><span data-stu-id="a0eca-105">When you create a service programmatically, you must perform several steps that the template would otherwise handle for you:</span></span>  
  
- <span data-ttu-id="a0eca-106">Je nutné nastavit třídu služby tak, aby dědila z <xref:System.ServiceProcess.ServiceBase> třídy.</span><span class="sxs-lookup"><span data-stu-id="a0eca-106">You must set up your service class to inherit from the <xref:System.ServiceProcess.ServiceBase> class.</span></span>  
  
- <span data-ttu-id="a0eca-107">Musíte vytvořit `Main` metodu pro projekt služby, který definuje služby, které mají být spuštěny, a zavolá <xref:System.ServiceProcess.ServiceBase.Run%2A> metodu na nich.</span><span class="sxs-lookup"><span data-stu-id="a0eca-107">You must create a `Main` method for your service project that defines the services to run and calls the <xref:System.ServiceProcess.ServiceBase.Run%2A> method on them.</span></span>  
  
- <span data-ttu-id="a0eca-108">Musíte přepsat <xref:System.ServiceProcess.ServiceBase.OnStart%2A> <xref:System.ServiceProcess.ServiceBase.OnStop%2A> postupy a a vyplnit libovolný kód, který chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="a0eca-108">You must override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures and fill in any code you want them to run.</span></span>  
  
### <a name="to-write-a-service-programmatically"></a><span data-ttu-id="a0eca-109">Programové vytvoření služby</span><span class="sxs-lookup"><span data-stu-id="a0eca-109">To write a service programmatically</span></span>  
  
1. <span data-ttu-id="a0eca-110">Pomocí následujících kroků vytvořte prázdný projekt a vytvořte odkaz na potřebné obory názvů:</span><span class="sxs-lookup"><span data-stu-id="a0eca-110">Create an empty project and create a reference to the necessary namespaces by following these steps:</span></span>  
  
    1. <span data-ttu-id="a0eca-111">V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **odkazy** a klikněte na **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="a0eca-111">In **Solution Explorer**, right-click the **References** node and click **Add Reference**.</span></span>  
  
    2. <span data-ttu-id="a0eca-112">Na kartě **.NET Framework** se posuňte na **System.dll** a klikněte na **Vybrat**.</span><span class="sxs-lookup"><span data-stu-id="a0eca-112">On the **.NET Framework** tab, scroll to **System.dll** and click **Select**.</span></span>  
  
    3. <span data-ttu-id="a0eca-113">Posuňte se na **System.ServiceProcess.dll** a klikněte na **Vybrat**.</span><span class="sxs-lookup"><span data-stu-id="a0eca-113">Scroll to **System.ServiceProcess.dll** and click **Select**.</span></span>  
  
    4. <span data-ttu-id="a0eca-114">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="a0eca-114">Click **OK**.</span></span>  
  
2. <span data-ttu-id="a0eca-115">Přidejte třídu a nakonfigurujte ji, aby dědila <xref:System.ServiceProcess.ServiceBase> :</span><span class="sxs-lookup"><span data-stu-id="a0eca-115">Add a class and configure it to inherit from <xref:System.ServiceProcess.ServiceBase>:</span></span>  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3. <span data-ttu-id="a0eca-116">Přidejte následující kód pro konfiguraci třídy služby:</span><span class="sxs-lookup"><span data-stu-id="a0eca-116">Add the following code to configure your service class:</span></span>  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4. <span data-ttu-id="a0eca-117">Vytvořte `Main` metodu pro třídu a použijte ji k definování služby, kterou bude třída obsahovat; `userService1` je název třídy:</span><span class="sxs-lookup"><span data-stu-id="a0eca-117">Create a `Main` method for your class, and use it to define the service your class will contain; `userService1` is the name of the class:</span></span>  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5. <span data-ttu-id="a0eca-118">Přepište <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodu a definujte jakékoli zpracování, které má být provedeno při spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="a0eca-118">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and define any processing you want to occur when your service is started.</span></span>  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6. <span data-ttu-id="a0eca-119">Přepište jakékoli jiné metody, pro které chcete definovat vlastní zpracování, a napište kód, který určí akce, které by měla služba provádět v každém případě.</span><span class="sxs-lookup"><span data-stu-id="a0eca-119">Override any other methods you want to define custom processing for, and write code to determine the actions the service should take in each case.</span></span>  
  
7. <span data-ttu-id="a0eca-120">Přidejte nezbytné instalační programy pro aplikaci služby.</span><span class="sxs-lookup"><span data-stu-id="a0eca-120">Add the necessary installers for your service application.</span></span> <span data-ttu-id="a0eca-121">Další informace najdete v tématu [Postup: Přidání instalačních programů do aplikace služby](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="a0eca-121">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>  
  
8. <span data-ttu-id="a0eca-122">Sestavte projekt výběrem možnosti **Sestavit řešení** v nabídce **sestavení** .</span><span class="sxs-lookup"><span data-stu-id="a0eca-122">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a0eca-123">Netiskněte klávesu F5 pro spuštění projektu – projekt služby nemůžete tímto způsobem spustit.</span><span class="sxs-lookup"><span data-stu-id="a0eca-123">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
9. <span data-ttu-id="a0eca-124">Vytvořte projekt instalace a vlastní akce pro instalaci služby.</span><span class="sxs-lookup"><span data-stu-id="a0eca-124">Create a setup project and the custom actions to install your service.</span></span> <span data-ttu-id="a0eca-125">Příklad naleznete v tématu [Návod: Vytvoření aplikace služby systému Windows v Návrháři komponent](walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="a0eca-125">For an example, see [Walkthrough: Creating a Windows Service Application in the Component Designer](walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
10. <span data-ttu-id="a0eca-126">Nainstalujte službu.</span><span class="sxs-lookup"><span data-stu-id="a0eca-126">Install the service.</span></span> <span data-ttu-id="a0eca-127">Další informace najdete v tématu [Postupy: instalace a odinstalace služeb](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="a0eca-127">For more information, see [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0eca-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0eca-128">See also</span></span>

- [<span data-ttu-id="a0eca-129">Představení aplikací spouštěných jako služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="a0eca-129">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="a0eca-130">Postupy: Vytváření služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="a0eca-130">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)
- [<span data-ttu-id="a0eca-131">Postupy: Přidání instalačních programů do aplikace služby</span><span class="sxs-lookup"><span data-stu-id="a0eca-131">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="a0eca-132">Postupy: Zaznamenávání informací o službách</span><span class="sxs-lookup"><span data-stu-id="a0eca-132">How to: Log Information About Services</span></span>](how-to-log-information-about-services.md)
- [<span data-ttu-id="a0eca-133">Návod: Vytvoření aplikace služby systému Windows v návrháři součástí</span><span class="sxs-lookup"><span data-stu-id="a0eca-133">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
