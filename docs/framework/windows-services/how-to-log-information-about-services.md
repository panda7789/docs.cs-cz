---
title: 'Postupy: Protokolu informace o službách'
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
ms.openlocfilehash: ff3eb0dd27f097899fc19f57142034ffd2bb382a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660137"
---
# <a name="how-to-log-information-about-services"></a><span data-ttu-id="aede5-102">Postupy: Protokolu informace o službách</span><span class="sxs-lookup"><span data-stu-id="aede5-102">How to: Log Information About Services</span></span>
<span data-ttu-id="aede5-103">Všechny projekty služeb Windows ve výchozím nastavení, mají možnost pracovat v protokolu událostí aplikace a do ní zapisovat informace a výjimek.</span><span class="sxs-lookup"><span data-stu-id="aede5-103">By default, all Windows Service projects have the ability to interact with the Application event log and write information and exceptions to it.</span></span> <span data-ttu-id="aede5-104">Můžete použít <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost určit, jestli chcete tuto funkci ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="aede5-104">You use the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to indicate whether you want this functionality in your application.</span></span> <span data-ttu-id="aede5-105">Ve výchozím nastavení je protokolování zapnuto na jakoukoli službu, které vytvoříte pomocí šablony projektu služby Windows.</span><span class="sxs-lookup"><span data-stu-id="aede5-105">By default, logging is turned on for any service you create with the Windows Service project template.</span></span> <span data-ttu-id="aede5-106">Můžete použít statické formu <xref:System.Diagnostics.EventLog> třídu pro zápis služby informace do protokolu bez nutnosti vytvářet instance <xref:System.Diagnostics.EventLog> komponenta nebo ruční registraci zdroje.</span><span class="sxs-lookup"><span data-stu-id="aede5-106">You can use a static form of the <xref:System.Diagnostics.EventLog> class to write service information to a log without having to create an instance of an <xref:System.Diagnostics.EventLog> component or manually register a source.</span></span>  
  
 <span data-ttu-id="aede5-107">Instalační program pro vaši službu automaticky zaregistruje každé služby ve vašem projektu jako platný zdroj události protokolu aplikace na počítači, kde je služba nainstalována, když je vypnuté protokolování.</span><span class="sxs-lookup"><span data-stu-id="aede5-107">The installer for your service automatically registers each service in your project as a valid source of events with the Application log on the computer where the service is installed, when logging is turned on.</span></span> <span data-ttu-id="aede5-108">Služba protokoluje informace pokaždé, když službu je spuštění, zastavení, pozastaveno, obnovení, nainstalované nebo odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="aede5-108">The service logs information each time the service is started, stopped, paused, resumed, installed, or uninstalled.</span></span> <span data-ttu-id="aede5-109">Také zaznamenává všechny chyby, ke kterým dochází.</span><span class="sxs-lookup"><span data-stu-id="aede5-109">It also logs any failures that occur.</span></span> <span data-ttu-id="aede5-110">Není potřeba psát kód pro zápis položky do protokolu, při použití výchozí chování; Služba zpracovává to pro vás automaticky.</span><span class="sxs-lookup"><span data-stu-id="aede5-110">You do not need to write any code to write entries to the log when using the default behavior; the service handles this for you automatically.</span></span>  
  
 <span data-ttu-id="aede5-111">Pokud chcete zapisovat do protokolu událostí než protokolu aplikace, je nutné nastavit <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost `false`vytvořit vlastní vlastního protokolu událostí v rámci vašeho kódu služby a registraci služby jako platný zdroj položek pro tento protokol.</span><span class="sxs-lookup"><span data-stu-id="aede5-111">If you want to write to an event log other than the Application log, you must set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`, create your own custom event log within your services code, and register your service as a valid source of entries for that log.</span></span> <span data-ttu-id="aede5-112">Pak musíte napsat, že se zobrazí kód pro záznam položky protokolu pokaždé, když akce, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="aede5-112">You must then write code to record entries to the log whenever an action you're interested in occurs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aede5-113">Pokud používáte vlastního protokolu událostí a nakonfigurovat aplikaci služby pro zápis do něj, nesmí pokus o přístup do protokolu událostí před nastavením služby <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnosti ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="aede5-113">If you use a custom event log and configure your service application to write to it, you must not attempt to access the event log before setting the service's <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property in your code.</span></span> <span data-ttu-id="aede5-114">V protokolu událostí musí tato vlastnost hodnotu pro registraci služby jako platný zdroj událostí.</span><span class="sxs-lookup"><span data-stu-id="aede5-114">The event log needs this property's value to register your service as a valid source of events.</span></span>  
  
### <a name="to-enable-default-event-logging-for-your-service"></a><span data-ttu-id="aede5-115">Povolení protokolování událostí výchozí pro vaši službu</span><span class="sxs-lookup"><span data-stu-id="aede5-115">To enable default event logging for your service</span></span>  
  
-   <span data-ttu-id="aede5-116">Nastavte <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost pro komponentu do `true`.</span><span class="sxs-lookup"><span data-stu-id="aede5-116">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aede5-117">Ve výchozím nastavení, tato vlastnost nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="aede5-117">By default, this property is set to `true`.</span></span> <span data-ttu-id="aede5-118">Není nutné nastavovat to explicitně, pokud nevytváříte složitější zpracování, jako jsou například vyhodnocení podmínky a pak nastavení <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> nastavenou na výsledek této podmínky.</span><span class="sxs-lookup"><span data-stu-id="aede5-118">You do not need to set this explicitly unless you are building more complex processing, such as evaluating a condition and then setting the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property based on the result of that condition.</span></span>  
  
### <a name="to-disable-event-logging-for-your-service"></a><span data-ttu-id="aede5-119">Chcete-li zakázat protokolování událostí pro vaši službu</span><span class="sxs-lookup"><span data-stu-id="aede5-119">To disable event logging for your service</span></span>  
  
-   <span data-ttu-id="aede5-120">Nastavte <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost pro komponentu do `false`.</span><span class="sxs-lookup"><span data-stu-id="aede5-120">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `false`.</span></span>  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a><span data-ttu-id="aede5-121">Nastavení protokolování do vlastního protokolu</span><span class="sxs-lookup"><span data-stu-id="aede5-121">To set up logging to a custom log</span></span>  
  
1.  <span data-ttu-id="aede5-122">Nastavte <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="aede5-122">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aede5-123">Je nutné nastavit <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> na hodnotu false, aby bylo možné používat vlastní protokol.</span><span class="sxs-lookup"><span data-stu-id="aede5-123">You must set <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> to false in order to use a custom log.</span></span>  
  
2.  <span data-ttu-id="aede5-124">Nastavení instance <xref:System.Diagnostics.EventLog> komponentu v aplikaci služby Windows.</span><span class="sxs-lookup"><span data-stu-id="aede5-124">Set up an instance of an <xref:System.Diagnostics.EventLog> component in your Windows Service application.</span></span>  
  
3.  <span data-ttu-id="aede5-125">Vytvoření vlastního protokolu pomocí volání <xref:System.Diagnostics.EventLog.CreateEventSource%2A> metoda a určení zdrojový řetězec a název protokolu souboru chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="aede5-125">Create a custom log by calling the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method and specifying the source string and the name of the log file you want to create.</span></span>  
  
4.  <span data-ttu-id="aede5-126">Nastavte <xref:System.Diagnostics.EventLog.Source%2A> vlastnost <xref:System.Diagnostics.EventLog> instanci komponenty zdrojový řetězec, který jste vytvořili v kroku 3.</span><span class="sxs-lookup"><span data-stu-id="aede5-126">Set the <xref:System.Diagnostics.EventLog.Source%2A> property on the <xref:System.Diagnostics.EventLog> component instance to the source string you created in step 3.</span></span>  
  
5.  <span data-ttu-id="aede5-127">Zapisovat položky díky přístupu <xref:System.Diagnostics.EventLog.WriteEntry%2A> metodu na <xref:System.Diagnostics.EventLog> instance komponenty.</span><span class="sxs-lookup"><span data-stu-id="aede5-127">Write your entries by accessing the <xref:System.Diagnostics.EventLog.WriteEntry%2A> method on the <xref:System.Diagnostics.EventLog> component instance.</span></span>  
  
     <span data-ttu-id="aede5-128">Následující kód ukazuje, jak nastavit protokolování, aby se vlastní protokol.</span><span class="sxs-lookup"><span data-stu-id="aede5-128">The following code shows how to set up logging to a custom log.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aede5-129">V tomto příkladu kódu, instance <xref:System.Diagnostics.EventLog> komponenta má název `eventLog1` (`EventLog1` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="aede5-129">In this code example, an instance of an <xref:System.Diagnostics.EventLog> component is named `eventLog1` (`EventLog1` in Visual Basic).</span></span> <span data-ttu-id="aede5-130">Pokud jste vytvořili instanci s jiným názvem v kroku 2, kód odpovídajícím způsobem měnit.</span><span class="sxs-lookup"><span data-stu-id="aede5-130">If you created an instance with another name in step 2, change the code accordingly.</span></span>  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="aede5-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aede5-131">See also</span></span>
- [<span data-ttu-id="aede5-132">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="aede5-132">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
