---
title: 'Postupy: Zaznamenávání informací o službách'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutoLog property
- services, logging information
- Windows Service applications, logging information about
- event logs, service applications
- application event logs, service applications
- logs, service applications
ms.assetid: c0d8140f-c055-4d8e-a2e0-37358a550116
author: ghogen
manager: douge
ms.openlocfilehash: a046c62de8789cbe438dcc849ffc23991a803ea2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-log-information-about-services"></a><span data-ttu-id="320d3-102">Postupy: Zaznamenávání informací o službách</span><span class="sxs-lookup"><span data-stu-id="320d3-102">How to: Log Information About Services</span></span>
<span data-ttu-id="320d3-103">Všechny projekty služby systému Windows ve výchozím nastavení, mají možnost využívat v protokolu událostí aplikace a do něj zapisovat informace a výjimky.</span><span class="sxs-lookup"><span data-stu-id="320d3-103">By default, all Windows Service projects have the ability to interact with the Application event log and write information and exceptions to it.</span></span> <span data-ttu-id="320d3-104">Můžete použít <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost označující, zda chcete tuto funkci v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="320d3-104">You use the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to indicate whether you want this functionality in your application.</span></span> <span data-ttu-id="320d3-105">Ve výchozím nastavení je protokolování zapnuto služby, které vytvoříte pomocí šablony projektu služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="320d3-105">By default, logging is turned on for any service you create with the Windows Service project template.</span></span> <span data-ttu-id="320d3-106">Můžete použít statické formu <xref:System.Diagnostics.EventLog> třída pro psaní informace o službě do protokolů, aniž by bylo nutné vytvořit instanci <xref:System.Diagnostics.EventLog> součást nebo ručně zaregistrovat zdroj.</span><span class="sxs-lookup"><span data-stu-id="320d3-106">You can use a static form of the <xref:System.Diagnostics.EventLog> class to write service information to a log without having to create an instance of an <xref:System.Diagnostics.EventLog> component or manually register a source.</span></span>  
  
 <span data-ttu-id="320d3-107">Instalační program služby automaticky registruje každé služby v projektu jako platný zdroj události protokolu aplikace v počítači, kterém je nainstalována služba, když je zapnuté protokolování.</span><span class="sxs-lookup"><span data-stu-id="320d3-107">The installer for your service automatically registers each service in your project as a valid source of events with the Application log on the computer where the service is installed, when logging is turned on.</span></span> <span data-ttu-id="320d3-108">Služba zaznamená do protokolu informace pokaždé, když služba spuštění, zastavení, pozastavena, byl obnoven, nainstalován nebo odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="320d3-108">The service logs information each time the service is started, stopped, paused, resumed, installed, or uninstalled.</span></span> <span data-ttu-id="320d3-109">Zaznamená také všechny chyby, ke kterým dochází.</span><span class="sxs-lookup"><span data-stu-id="320d3-109">It also logs any failures that occur.</span></span> <span data-ttu-id="320d3-110">Není potřeba psaní jakéhokoli kódu službě zapisovat položky protokolu, při použití výchozí chování; Služba zpracovává to pro vás automaticky.</span><span class="sxs-lookup"><span data-stu-id="320d3-110">You do not need to write any code to write entries to the log when using the default behavior; the service handles this for you automatically.</span></span>  
  
 <span data-ttu-id="320d3-111">Pokud chcete zapisovat do protokolu událostí, než v protokolu aplikace, je nutné nastavit <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost `false`, vytvořte vlastní vlastní protokol událostí v kódu služby a registraci služby jako platný zdroj položek pro tento protokol.</span><span class="sxs-lookup"><span data-stu-id="320d3-111">If you want to write to an event log other than the Application log, you must set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`, create your own custom event log within your services code, and register your service as a valid source of entries for that log.</span></span> <span data-ttu-id="320d3-112">Pak musíte napsat kódu k zaznamenání položky do protokolu vždy, když akce, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="320d3-112">You must then write code to record entries to the log whenever an action you're interested in occurs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="320d3-113">Pokud používáte vlastní protokol událostí a konfiguraci aplikace služby pro zápis do, nesmíte pokoušet přístup k protokolu událostí před nastavením služby <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastností v kódu.</span><span class="sxs-lookup"><span data-stu-id="320d3-113">If you use a custom event log and configure your service application to write to it, you must not attempt to access the event log before setting the service's <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property in your code.</span></span> <span data-ttu-id="320d3-114">Protokol událostí, musí tato vlastnost hodnotu k registraci služby jako platný zdroj událostí.</span><span class="sxs-lookup"><span data-stu-id="320d3-114">The event log needs this property's value to register your service as a valid source of events.</span></span>  
  
### <a name="to-enable-default-event-logging-for-your-service"></a><span data-ttu-id="320d3-115">Povolení protokolování událostí výchozí služby</span><span class="sxs-lookup"><span data-stu-id="320d3-115">To enable default event logging for your service</span></span>  
  
-   <span data-ttu-id="320d3-116">Nastavte <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost pro příslušné součásti na `true`.</span><span class="sxs-lookup"><span data-stu-id="320d3-116">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="320d3-117">Ve výchozím nastavení je tato vlastnost nastavena `true`.</span><span class="sxs-lookup"><span data-stu-id="320d3-117">By default, this property is set to `true`.</span></span> <span data-ttu-id="320d3-118">Není nutné explicitně nastavit Pokud vytváříte složitější zpracování, např. vyhodnocení podmínku a pak nastavení <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastností na základě výsledku této podmínky.</span><span class="sxs-lookup"><span data-stu-id="320d3-118">You do not need to set this explicitly unless you are building more complex processing, such as evaluating a condition and then setting the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property based on the result of that condition.</span></span>  
  
### <a name="to-disable-event-logging-for-your-service"></a><span data-ttu-id="320d3-119">Zakázání protokolování událostí pro služby</span><span class="sxs-lookup"><span data-stu-id="320d3-119">To disable event logging for your service</span></span>  
  
-   <span data-ttu-id="320d3-120">Nastavte <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost pro příslušné součásti na `false`.</span><span class="sxs-lookup"><span data-stu-id="320d3-120">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `false`.</span></span>  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a><span data-ttu-id="320d3-121">Nastavení protokolování do vlastní protokolu</span><span class="sxs-lookup"><span data-stu-id="320d3-121">To set up logging to a custom log</span></span>  
  
1.  <span data-ttu-id="320d3-122">Nastavte <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="320d3-122">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="320d3-123">Je nutné nastavit <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> na hodnotu false, aby bylo možné používat vlastní protokol.</span><span class="sxs-lookup"><span data-stu-id="320d3-123">You must set <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> to false in order to use a custom log.</span></span>  
  
2.  <span data-ttu-id="320d3-124">Nastavit instanci <xref:System.Diagnostics.EventLog> součásti v aplikaci služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="320d3-124">Set up an instance of an <xref:System.Diagnostics.EventLog> component in your Windows Service application.</span></span>  
  
3.  <span data-ttu-id="320d3-125">Vytvořit vlastní protokol voláním <xref:System.Diagnostics.EventLog.CreateEventSource%2A> metoda a zadání zdrojový řetězec a název protokolu soubor chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="320d3-125">Create a custom log by calling the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method and specifying the source string and the name of the log file you want to create.</span></span>  
  
4.  <span data-ttu-id="320d3-126">Nastavte <xref:System.Diagnostics.EventLog.Source%2A> vlastnost <xref:System.Diagnostics.EventLog> instanci komponenty zdrojový řetězec, který jste vytvořili v kroku 3.</span><span class="sxs-lookup"><span data-stu-id="320d3-126">Set the <xref:System.Diagnostics.EventLog.Source%2A> property on the <xref:System.Diagnostics.EventLog> component instance to the source string you created in step 3.</span></span>  
  
5.  <span data-ttu-id="320d3-127">Zapisovat vaše položky přímým přístupem <xref:System.Diagnostics.EventLog.WriteEntry%2A> metodu <xref:System.Diagnostics.EventLog> instanci součásti.</span><span class="sxs-lookup"><span data-stu-id="320d3-127">Write your entries by accessing the <xref:System.Diagnostics.EventLog.WriteEntry%2A> method on the <xref:System.Diagnostics.EventLog> component instance.</span></span>  
  
     <span data-ttu-id="320d3-128">Následující kód ukazuje, jak nastavit protokolování do vlastního protokolu.</span><span class="sxs-lookup"><span data-stu-id="320d3-128">The following code shows how to set up logging to a custom log.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="320d3-129">V tomto příkladu kódu, instance <xref:System.Diagnostics.EventLog> komponenta má název `eventLog1` (`EventLog1` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="320d3-129">In this code example, an instance of an <xref:System.Diagnostics.EventLog> component is named `eventLog1` (`EventLog1` in Visual Basic).</span></span> <span data-ttu-id="320d3-130">Pokud jste vytvořili instanci s jiným názvem v kroku 2, změňte kód odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="320d3-130">If you created an instance with another name in step 2, change the code accordingly.</span></span>  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="320d3-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="320d3-131">See Also</span></span>  
 [<span data-ttu-id="320d3-132">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="320d3-132">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
