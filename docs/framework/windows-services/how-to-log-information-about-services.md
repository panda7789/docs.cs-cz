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
ms.openlocfilehash: 1ffc698910fe722fe761c62b87b059068d5f243f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935523"
---
# <a name="how-to-log-information-about-services"></a><span data-ttu-id="e7199-102">Postupy: Zaznamenávání informací o službách</span><span class="sxs-lookup"><span data-stu-id="e7199-102">How to: Log Information About Services</span></span>
<span data-ttu-id="e7199-103">Ve výchozím nastavení mají všechny projekty služby systému Windows schopnost pracovat s protokolem událostí aplikace a zapisovat do něj informace a výjimky.</span><span class="sxs-lookup"><span data-stu-id="e7199-103">By default, all Windows Service projects have the ability to interact with the Application event log and write information and exceptions to it.</span></span> <span data-ttu-id="e7199-104"><xref:System.ServiceProcess.ServiceBase.AutoLog%2A> Vlastnost můžete použít k určení, zda chcete tuto funkci ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e7199-104">You use the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to indicate whether you want this functionality in your application.</span></span> <span data-ttu-id="e7199-105">Ve výchozím nastavení je protokolování zapnuté pro každou službu, kterou vytvoříte pomocí šablony projektu služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="e7199-105">By default, logging is turned on for any service you create with the Windows Service project template.</span></span> <span data-ttu-id="e7199-106">Můžete použít statickou formu <xref:System.Diagnostics.EventLog> třídy k zápisu informací o službě do protokolu bez nutnosti vytvořit instanci <xref:System.Diagnostics.EventLog> komponenty nebo ručně zaregistrovat zdroj.</span><span class="sxs-lookup"><span data-stu-id="e7199-106">You can use a static form of the <xref:System.Diagnostics.EventLog> class to write service information to a log without having to create an instance of an <xref:System.Diagnostics.EventLog> component or manually register a source.</span></span>  
  
 <span data-ttu-id="e7199-107">Instalační program pro vaši službu automaticky zaregistruje každou službu v projektu jako platný zdroj událostí s protokolem aplikace v počítači, kde je služba nainstalovaná, pokud je zapnuté protokolování.</span><span class="sxs-lookup"><span data-stu-id="e7199-107">The installer for your service automatically registers each service in your project as a valid source of events with the Application log on the computer where the service is installed, when logging is turned on.</span></span> <span data-ttu-id="e7199-108">Služba protokoluje informace pokaždé, když je služba spuštěná, zastavená, pozastavená, obnovená, nainstalovaná nebo odinstalovaná.</span><span class="sxs-lookup"><span data-stu-id="e7199-108">The service logs information each time the service is started, stopped, paused, resumed, installed, or uninstalled.</span></span> <span data-ttu-id="e7199-109">Také protokoluje všechny chyby, ke kterým dojde.</span><span class="sxs-lookup"><span data-stu-id="e7199-109">It also logs any failures that occur.</span></span> <span data-ttu-id="e7199-110">Pokud používáte výchozí chování, nemusíte psát žádný kód pro zápis položek do protokolu. Služba to zpracuje automaticky.</span><span class="sxs-lookup"><span data-stu-id="e7199-110">You do not need to write any code to write entries to the log when using the default behavior; the service handles this for you automatically.</span></span>  
  
 <span data-ttu-id="e7199-111">Pokud chcete zapisovat do protokolu událostí, který je jiný než protokol aplikace, musíte nastavit <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost na `false`, vytvořit vlastní protokol událostí v rámci kódu služby a zaregistrovat službu jako platný zdroj záznamů pro tento protokol.</span><span class="sxs-lookup"><span data-stu-id="e7199-111">If you want to write to an event log other than the Application log, you must set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`, create your own custom event log within your services code, and register your service as a valid source of entries for that log.</span></span> <span data-ttu-id="e7199-112">Pak musíte napsat kód pro záznam záznamů do protokolu pokaždé, když se vyskytne akce, které vás zajímá.</span><span class="sxs-lookup"><span data-stu-id="e7199-112">You must then write code to record entries to the log whenever an action you're interested in occurs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e7199-113">Pokud použijete vlastní protokol událostí a nakonfigurujete k zápisu do aplikace služby, nemusíte se před nastavením <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnosti služby v kódu pokoušet o přístup k protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="e7199-113">If you use a custom event log and configure your service application to write to it, you must not attempt to access the event log before setting the service's <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property in your code.</span></span> <span data-ttu-id="e7199-114">Protokol událostí potřebuje tuto hodnotu vlastnosti k registraci vaší služby jako platného zdroje událostí.</span><span class="sxs-lookup"><span data-stu-id="e7199-114">The event log needs this property's value to register your service as a valid source of events.</span></span>  
  
### <a name="to-enable-default-event-logging-for-your-service"></a><span data-ttu-id="e7199-115">Povolení protokolování výchozích událostí pro vaši službu</span><span class="sxs-lookup"><span data-stu-id="e7199-115">To enable default event logging for your service</span></span>  
  
- <span data-ttu-id="e7199-116">Nastavte vlastnost pro komponentu na `true`. <xref:System.ServiceProcess.ServiceBase.AutoLog%2A></span><span class="sxs-lookup"><span data-stu-id="e7199-116">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `true`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e7199-117">Ve výchozím nastavení je tato vlastnost nastavena na `true`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e7199-117">By default, this property is set to `true`.</span></span> <span data-ttu-id="e7199-118">Tuto možnost nemusíte explicitně nastavovat, pokud nevytváříte komplexnější zpracování, jako je například vyhodnocení podmínky a nastavení <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnosti na základě výsledku této podmínky.</span><span class="sxs-lookup"><span data-stu-id="e7199-118">You do not need to set this explicitly unless you are building more complex processing, such as evaluating a condition and then setting the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property based on the result of that condition.</span></span>  
  
### <a name="to-disable-event-logging-for-your-service"></a><span data-ttu-id="e7199-119">Zakázání protokolování událostí pro vaši službu</span><span class="sxs-lookup"><span data-stu-id="e7199-119">To disable event logging for your service</span></span>  
  
- <span data-ttu-id="e7199-120">Nastavte vlastnost pro komponentu na `false`. <xref:System.ServiceProcess.ServiceBase.AutoLog%2A></span><span class="sxs-lookup"><span data-stu-id="e7199-120">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `false`.</span></span>  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a><span data-ttu-id="e7199-121">Nastavení protokolování do vlastního protokolu</span><span class="sxs-lookup"><span data-stu-id="e7199-121">To set up logging to a custom log</span></span>  
  
1. <span data-ttu-id="e7199-122">Nastavte <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="e7199-122">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e7199-123">Aby bylo možné <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> použít vlastní protokol, je nutné nastavit hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="e7199-123">You must set <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> to false in order to use a custom log.</span></span>  
  
2. <span data-ttu-id="e7199-124">Nastavení instance <xref:System.Diagnostics.EventLog> komponenty v aplikaci služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="e7199-124">Set up an instance of an <xref:System.Diagnostics.EventLog> component in your Windows Service application.</span></span>  
  
3. <span data-ttu-id="e7199-125">Vytvořte vlastní protokol voláním <xref:System.Diagnostics.EventLog.CreateEventSource%2A> metody a zadáním zdrojového řetězce a názvu souboru protokolu, který chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="e7199-125">Create a custom log by calling the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method and specifying the source string and the name of the log file you want to create.</span></span>  
  
4. <span data-ttu-id="e7199-126"><xref:System.Diagnostics.EventLog.Source%2A> Nastavte vlastnost <xref:System.Diagnostics.EventLog> u instance komponenty na zdrojový řetězec, který jste vytvořili v kroku 3.</span><span class="sxs-lookup"><span data-stu-id="e7199-126">Set the <xref:System.Diagnostics.EventLog.Source%2A> property on the <xref:System.Diagnostics.EventLog> component instance to the source string you created in step 3.</span></span>  
  
5. <span data-ttu-id="e7199-127">Zapište své položky přístupem k <xref:System.Diagnostics.EventLog.WriteEntry%2A> metodě <xref:System.Diagnostics.EventLog> v instanci komponenty.</span><span class="sxs-lookup"><span data-stu-id="e7199-127">Write your entries by accessing the <xref:System.Diagnostics.EventLog.WriteEntry%2A> method on the <xref:System.Diagnostics.EventLog> component instance.</span></span>  
  
     <span data-ttu-id="e7199-128">Následující kód ukazuje, jak nastavit protokolování do vlastního protokolu.</span><span class="sxs-lookup"><span data-stu-id="e7199-128">The following code shows how to set up logging to a custom log.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e7199-129">V tomto příkladu kódu je instance <xref:System.Diagnostics.EventLog> komponenty pojmenována `eventLog1` (`EventLog1` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="e7199-129">In this code example, an instance of an <xref:System.Diagnostics.EventLog> component is named `eventLog1` (`EventLog1` in Visual Basic).</span></span> <span data-ttu-id="e7199-130">Pokud jste vytvořili instanci s jiným názvem v kroku 2, změňte kód odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="e7199-130">If you created an instance with another name in step 2, change the code accordingly.</span></span>  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="e7199-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7199-131">See also</span></span>

- [<span data-ttu-id="e7199-132">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="e7199-132">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
