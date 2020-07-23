---
title: 'Postupy: Zaznamenávání informací o službách'
description: Dozvíte se, jak protokolovat informace o službách. Nastavte vlastnost AutoLog, pokud chcete, aby projekt služby systému Windows spolupracoval s protokolem událostí aplikace.
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
ms.openlocfilehash: 6ebce5464dc25ba4101b3898ee791714f8efc5d6
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925745"
---
# <a name="how-to-log-information-about-services"></a><span data-ttu-id="114fc-104">Postupy: Zaznamenávání informací o službách</span><span class="sxs-lookup"><span data-stu-id="114fc-104">How to: Log Information About Services</span></span>
<span data-ttu-id="114fc-105">Ve výchozím nastavení mají všechny projekty služby systému Windows schopnost pracovat s protokolem událostí aplikace a zapisovat do něj informace a výjimky.</span><span class="sxs-lookup"><span data-stu-id="114fc-105">By default, all Windows Service projects have the ability to interact with the Application event log and write information and exceptions to it.</span></span> <span data-ttu-id="114fc-106">Vlastnost můžete použít <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> k určení, zda chcete tuto funkci ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="114fc-106">You use the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to indicate whether you want this functionality in your application.</span></span> <span data-ttu-id="114fc-107">Ve výchozím nastavení je protokolování zapnuté pro každou službu, kterou vytvoříte pomocí šablony projektu služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="114fc-107">By default, logging is turned on for any service you create with the Windows Service project template.</span></span> <span data-ttu-id="114fc-108">Můžete použít statickou formu <xref:System.Diagnostics.EventLog> třídy k zápisu informací o službě do protokolu bez nutnosti vytvořit instanci <xref:System.Diagnostics.EventLog> komponenty nebo ručně zaregistrovat zdroj.</span><span class="sxs-lookup"><span data-stu-id="114fc-108">You can use a static form of the <xref:System.Diagnostics.EventLog> class to write service information to a log without having to create an instance of an <xref:System.Diagnostics.EventLog> component or manually register a source.</span></span>  
  
 <span data-ttu-id="114fc-109">Instalační program pro vaši službu automaticky zaregistruje každou službu v projektu jako platný zdroj událostí s protokolem aplikace v počítači, kde je služba nainstalovaná, pokud je zapnuté protokolování.</span><span class="sxs-lookup"><span data-stu-id="114fc-109">The installer for your service automatically registers each service in your project as a valid source of events with the Application log on the computer where the service is installed, when logging is turned on.</span></span> <span data-ttu-id="114fc-110">Služba protokoluje informace pokaždé, když je služba spuštěná, zastavená, pozastavená, obnovená, nainstalovaná nebo odinstalovaná.</span><span class="sxs-lookup"><span data-stu-id="114fc-110">The service logs information each time the service is started, stopped, paused, resumed, installed, or uninstalled.</span></span> <span data-ttu-id="114fc-111">Také protokoluje všechny chyby, ke kterým dojde.</span><span class="sxs-lookup"><span data-stu-id="114fc-111">It also logs any failures that occur.</span></span> <span data-ttu-id="114fc-112">Pokud používáte výchozí chování, nemusíte psát žádný kód pro zápis položek do protokolu. Služba to zpracuje automaticky.</span><span class="sxs-lookup"><span data-stu-id="114fc-112">You do not need to write any code to write entries to the log when using the default behavior; the service handles this for you automatically.</span></span>  
  
 <span data-ttu-id="114fc-113">Pokud chcete zapisovat do protokolu událostí, který je jiný než protokol aplikace, musíte nastavit <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost na `false` , vytvořit vlastní protokol událostí v rámci kódu služby a zaregistrovat službu jako platný zdroj záznamů pro tento protokol.</span><span class="sxs-lookup"><span data-stu-id="114fc-113">If you want to write to an event log other than the Application log, you must set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`, create your own custom event log within your services code, and register your service as a valid source of entries for that log.</span></span> <span data-ttu-id="114fc-114">Pak musíte napsat kód pro záznam záznamů do protokolu pokaždé, když se vyskytne akce, které vás zajímá.</span><span class="sxs-lookup"><span data-stu-id="114fc-114">You must then write code to record entries to the log whenever an action you're interested in occurs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="114fc-115">Pokud použijete vlastní protokol událostí a nakonfigurujete k zápisu do aplikace služby, nemusíte se před nastavením vlastnosti služby v kódu pokoušet o přístup k protokolu událostí <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> .</span><span class="sxs-lookup"><span data-stu-id="114fc-115">If you use a custom event log and configure your service application to write to it, you must not attempt to access the event log before setting the service's <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property in your code.</span></span> <span data-ttu-id="114fc-116">Protokol událostí potřebuje tuto hodnotu vlastnosti k registraci vaší služby jako platného zdroje událostí.</span><span class="sxs-lookup"><span data-stu-id="114fc-116">The event log needs this property's value to register your service as a valid source of events.</span></span>  
  
### <a name="to-enable-default-event-logging-for-your-service"></a><span data-ttu-id="114fc-117">Povolení protokolování výchozích událostí pro vaši službu</span><span class="sxs-lookup"><span data-stu-id="114fc-117">To enable default event logging for your service</span></span>  
  
- <span data-ttu-id="114fc-118">Nastavte <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost pro komponentu na `true` .</span><span class="sxs-lookup"><span data-stu-id="114fc-118">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `true`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="114fc-119">Ve výchozím nastavení je tato vlastnost nastavena na hodnotu `true` .</span><span class="sxs-lookup"><span data-stu-id="114fc-119">By default, this property is set to `true`.</span></span> <span data-ttu-id="114fc-120">Tuto možnost nemusíte explicitně nastavovat, pokud nevytváříte komplexnější zpracování, jako je například vyhodnocení podmínky a nastavení <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnosti na základě výsledku této podmínky.</span><span class="sxs-lookup"><span data-stu-id="114fc-120">You do not need to set this explicitly unless you are building more complex processing, such as evaluating a condition and then setting the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property based on the result of that condition.</span></span>  
  
### <a name="to-disable-event-logging-for-your-service"></a><span data-ttu-id="114fc-121">Zakázání protokolování událostí pro vaši službu</span><span class="sxs-lookup"><span data-stu-id="114fc-121">To disable event logging for your service</span></span>  
  
- <span data-ttu-id="114fc-122">Nastavte <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost pro komponentu na `false` .</span><span class="sxs-lookup"><span data-stu-id="114fc-122">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `false`.</span></span>  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a><span data-ttu-id="114fc-123">Nastavení protokolování do vlastního protokolu</span><span class="sxs-lookup"><span data-stu-id="114fc-123">To set up logging to a custom log</span></span>  
  
1. <span data-ttu-id="114fc-124">Nastavte <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost na hodnotu `false` .</span><span class="sxs-lookup"><span data-stu-id="114fc-124">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="114fc-125">Aby <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> bylo možné použít vlastní protokol, je nutné nastavit hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="114fc-125">You must set <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> to false in order to use a custom log.</span></span>  
  
2. <span data-ttu-id="114fc-126">Nastavení instance <xref:System.Diagnostics.EventLog> komponenty v aplikaci služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="114fc-126">Set up an instance of an <xref:System.Diagnostics.EventLog> component in your Windows Service application.</span></span>  
  
3. <span data-ttu-id="114fc-127">Vytvořte vlastní protokol voláním <xref:System.Diagnostics.EventLog.CreateEventSource%2A> metody a zadáním zdrojového řetězce a názvu souboru protokolu, který chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="114fc-127">Create a custom log by calling the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method and specifying the source string and the name of the log file you want to create.</span></span>  
  
4. <span data-ttu-id="114fc-128">Nastavte <xref:System.Diagnostics.EventLog.Source%2A> vlastnost u <xref:System.Diagnostics.EventLog> instance komponenty na zdrojový řetězec, který jste vytvořili v kroku 3.</span><span class="sxs-lookup"><span data-stu-id="114fc-128">Set the <xref:System.Diagnostics.EventLog.Source%2A> property on the <xref:System.Diagnostics.EventLog> component instance to the source string you created in step 3.</span></span>  
  
5. <span data-ttu-id="114fc-129">Zapište své položky přístupem k <xref:System.Diagnostics.EventLog.WriteEntry%2A> metodě v <xref:System.Diagnostics.EventLog> instanci komponenty.</span><span class="sxs-lookup"><span data-stu-id="114fc-129">Write your entries by accessing the <xref:System.Diagnostics.EventLog.WriteEntry%2A> method on the <xref:System.Diagnostics.EventLog> component instance.</span></span>  
  
     <span data-ttu-id="114fc-130">Následující kód ukazuje, jak nastavit protokolování do vlastního protokolu.</span><span class="sxs-lookup"><span data-stu-id="114fc-130">The following code shows how to set up logging to a custom log.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="114fc-131">V tomto příkladu kódu <xref:System.Diagnostics.EventLog> je instance komponenty pojmenována `eventLog1` ( `EventLog1` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="114fc-131">In this code example, an instance of an <xref:System.Diagnostics.EventLog> component is named `eventLog1` (`EventLog1` in Visual Basic).</span></span> <span data-ttu-id="114fc-132">Pokud jste vytvořili instanci s jiným názvem v kroku 2, změňte kód odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="114fc-132">If you created an instance with another name in step 2, change the code accordingly.</span></span>  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="114fc-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="114fc-133">See also</span></span>

- [<span data-ttu-id="114fc-134">Představení aplikací spouštěných jako služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="114fc-134">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
