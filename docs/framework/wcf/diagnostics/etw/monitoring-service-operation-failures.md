---
title: "Sledování selhání operací služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59472ba3-8ebf-4479-bd7b-f440d5e636cb
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 42506f7f32d0174b4f980f4e94d370cf4c137276
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="monitoring-service-operation-failures"></a><span data-ttu-id="9ef29-102">Sledování selhání operací služby</span><span class="sxs-lookup"><span data-stu-id="9ef29-102">Monitoring Service Operation Failures</span></span>
<span data-ttu-id="9ef29-103">Pokud je povolené analytické trasování pro aplikaci, selhání služby se dá snadno sledovat v prohlížeči událostí.</span><span class="sxs-lookup"><span data-stu-id="9ef29-103">If analytic tracing is enabled for an application, service failures can easily be monitored in the event viewer.</span></span>  <span data-ttu-id="9ef29-104">Toto téma ukazuje, jak k určení, kdy dojde k selhání operace služby, a jak zjistit, co způsobilo selhání.</span><span class="sxs-lookup"><span data-stu-id="9ef29-104">This topic demonstrates how to determine when a service operation fails, and how to determine what caused the failure.</span></span>  
  
### <a name="determining-service-operation-failure-information"></a><span data-ttu-id="9ef29-105">Určení informace o selhání operaci služby</span><span class="sxs-lookup"><span data-stu-id="9ef29-105">Determining service operation failure information</span></span>  
  
1.  <span data-ttu-id="9ef29-106">Otevřete Prohlížeč událostí kliknutím **spustit**, **spustit**a zadáním `eventvwr.exe`.</span><span class="sxs-lookup"><span data-stu-id="9ef29-106">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
2.  <span data-ttu-id="9ef29-107">Pokud jste nepovolili analytické trasování, rozbalte položku **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **serveru aplikace – aplikace** .</span><span class="sxs-lookup"><span data-stu-id="9ef29-107">If you haven’t enabled analytic tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="9ef29-108">Vyberte **zobrazení**, **ukazují analytické a ladicí protokoly**.</span><span class="sxs-lookup"><span data-stu-id="9ef29-108">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="9ef29-109">Klikněte pravým tlačítkem na **analytické** a vyberte **povolit protokol**.</span><span class="sxs-lookup"><span data-stu-id="9ef29-109">Right-click **Analytic** and select **Enable Log**.</span></span> <span data-ttu-id="9ef29-110">Ponechte prohlížeče událostí otevřete tak, aby trasování lze zobrazit po operaci služby se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="9ef29-110">Leave Event Viewer open so that traces can be viewed after the service operation fails.</span></span>  
  
3.  <span data-ttu-id="9ef29-111">Dále otevřete vytvořené v ukázce [kurzu Začínáme](../../../../../docs/framework/wcf/getting-started-tutorial.md) v [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] Všimněte si, že je nutné spustit [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] jako správce, aby bylo možné vytvořit službu.</span><span class="sxs-lookup"><span data-stu-id="9ef29-111">Next, open the sample created in the [Getting Started Tutorial](../../../../../docs/framework/wcf/getting-started-tutorial.md) in [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] Note that you must run [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] as an administrator so that the service can be created.</span></span> <span data-ttu-id="9ef29-112">Pokud máte [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] ukázky nainstalován, můžete otevřít [Začínáme](../../../../../docs/framework/wcf/samples/getting-started-sample.md), obsahující dokončený projekt vytvořený v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="9ef29-112">If you have the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] samples installed, you can open the [Getting Started](../../../../../docs/framework/wcf/samples/getting-started-sample.md), which contains the completed project created in the tutorial.</span></span>  
  
4.  <span data-ttu-id="9ef29-113">V souboru Program.cs v projektu serveru, přidejte následující řádek kódu na začátek `Divide` metoda v `CalculatorService` třídy:</span><span class="sxs-lookup"><span data-stu-id="9ef29-113">In the Program.cs file in the Server project, add the following line of code to the start of the `Divide` method in the `CalculatorService` class:</span></span>  
  
    ```  
    if (n2 == 0) throw new DivideByZeroException();  
    ```  
  
5.  <span data-ttu-id="9ef29-114">V souboru Program.cs v projektu klienta změňte hodnotu přiřazenou value2 na nulu:</span><span class="sxs-lookup"><span data-stu-id="9ef29-114">In the Program.cs file in the Client project, change the value assigned to value2 to zero:</span></span>  
  
    ```  
    //Call the Divide service operation  
    value1 = 22.00D;  
    value2 = 0.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0}, {1}) = {2}", value1, value2, result);  
    ```  
  
6.  <span data-ttu-id="9ef29-115">Spuštění aplikace serveru bez ladění stisknutím kombinace kláves **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="9ef29-115">Execute the server application without debugging by pressing **Ctrl+F5**.</span></span>  
  
7.  <span data-ttu-id="9ef29-116">Otevřete příkazový řádek sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9ef29-116">Open a Visual Studio command prompt.</span></span>  <span data-ttu-id="9ef29-117">Přejděte do adresáře klienta a klient pro spuštění z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="9ef29-117">Navigate to the client directory and execute the client from the command line.</span></span>  
  
8.  <span data-ttu-id="9ef29-118">V prohlížeči událostí zakázat a aktualizujte protokol analytické a seřaďte události podle ID události.</span><span class="sxs-lookup"><span data-stu-id="9ef29-118">In Event Viewer, disable and refresh the Analytic log and sort the events by Event ID.</span></span>  <span data-ttu-id="9ef29-119">Vyhledejte událost s ID události [219 - ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md), který popisuje selhání služby.</span><span class="sxs-lookup"><span data-stu-id="9ef29-119">Look for an event with Event ID [219 - ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md), which describes the service failure.</span></span>  
  
    ```Output  
    There was an unhandled exception of type 'System.DivideByZeroException' during message processing.  Full Exception ToString: System.DivideByZeroException: Attempted to divide by zero.  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="9ef29-120">Události jsou do vyrovnávací paměti při odesílání do prohlížeče událostí; událost selhání nemusí zobrazit hned.</span><span class="sxs-lookup"><span data-stu-id="9ef29-120">Events are buffered when being sent to the event viewer; the failure event may not appear right away.</span></span>
