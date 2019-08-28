---
title: 'Postupy: Ladění aplikací spouštěných jako služby systému Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- Windows NT services, debugging
- Windows Service applications, debugging
- services, debugging
ms.assetid: 63ab0800-0f05-4f1e-88e6-94c73fd920a2
author: ghogen
ms.openlocfilehash: 74f834261d464430547ba3e1113db0ea780f593e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044446"
---
# <a name="how-to-debug-windows-service-applications"></a><span data-ttu-id="f9d78-102">Postupy: Ladění aplikací spouštěných jako služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="f9d78-102">How to: Debug Windows Service Applications</span></span>
<span data-ttu-id="f9d78-103">Služba musí být spuštěna v kontextu správce řízení služeb, nikoli v rámci sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f9d78-103">A service must be run from within the context of the Services Control Manager rather than from within Visual Studio.</span></span> <span data-ttu-id="f9d78-104">Z tohoto důvodu ladění služby není tak jednoduché jako ladění jiných typů aplikací sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f9d78-104">For this reason, debugging a service is not as straightforward as debugging other Visual Studio application types.</span></span> <span data-ttu-id="f9d78-105">Chcete-li ladit službu, je nutné spustit službu a potom připojit ladicí program k procesu, ve kterém je spuštěna.</span><span class="sxs-lookup"><span data-stu-id="f9d78-105">To debug a service, you must start the service and then attach a debugger to the process in which it is running.</span></span> <span data-ttu-id="f9d78-106">Pak můžete ladit aplikaci pomocí všech standardních funkcí ladění sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f9d78-106">You can then debug your application by using all of the standard debugging functionality of Visual Studio.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="f9d78-107">K procesu se nemusíte připojovat, Pokud nevíte, co proces je, a porozumět důsledkům připojení a případně usmrcení tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="f9d78-107">You should not attach to a process unless you know what the process is and understand the consequences of attaching to and possibly killing that process.</span></span> <span data-ttu-id="f9d78-108">Například pokud se připojíte k procesu WinLogon a pak zastavíte ladění, systém se zastaví, protože nemůže pracovat bez procesu WinLogon.</span><span class="sxs-lookup"><span data-stu-id="f9d78-108">For example, if you attach to the WinLogon process and then stop debugging, the system will halt because it can’t operate without WinLogon.</span></span>  
  
 <span data-ttu-id="f9d78-109">Ladicí program lze připojit pouze ke spuštěné službě.</span><span class="sxs-lookup"><span data-stu-id="f9d78-109">You can attach the debugger only to a running service.</span></span> <span data-ttu-id="f9d78-110">Proces přílohy přerušuje aktuální fungování vaší služby. ve skutečnosti se nezastaví nebo nezastaví zpracování služby.</span><span class="sxs-lookup"><span data-stu-id="f9d78-110">The attachment process interrupts the current functioning of your service; it doesn’t actually stop or pause the service's processing.</span></span> <span data-ttu-id="f9d78-111">To znamená, že pokud vaše služba běží při zahájení ladění, je při ladění stále technicky ve stavu spuštěno, ale jeho zpracování bylo pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="f9d78-111">That is, if your service is running when you begin debugging, it is still technically in the Started state as you debug it, but its processing has been suspended.</span></span>  
  
 <span data-ttu-id="f9d78-112">Po připojení k procesu můžete nastavit zarážky a použít je k ladění kódu.</span><span class="sxs-lookup"><span data-stu-id="f9d78-112">After attaching to the process, you can set breakpoints and use these to debug your code.</span></span> <span data-ttu-id="f9d78-113">Po zavření dialogového okna, které použijete k připojení k procesu, budete efektivně v režimu ladění.</span><span class="sxs-lookup"><span data-stu-id="f9d78-113">Once you exit the dialog box you use to attach to the process, you are effectively in debug mode.</span></span> <span data-ttu-id="f9d78-114">Správce řízení služeb můžete použít ke spuštění, zastavení, pozastavení a pokračování služby, čímž se zastaví zarážky, které jste nastavili.</span><span class="sxs-lookup"><span data-stu-id="f9d78-114">You can use the Services Control Manager to start, stop, pause and continue your service, thus hitting the breakpoints you've set.</span></span> <span data-ttu-id="f9d78-115">Po úspěšném ladění můžete tuto fiktivní službu odebrat později.</span><span class="sxs-lookup"><span data-stu-id="f9d78-115">You can later remove this dummy service after debugging is successful.</span></span>  
  
 <span data-ttu-id="f9d78-116">Tento článek popisuje ladění služby spuštěné v místním počítači, ale můžete také ladit služby systému Windows, které jsou spuštěny na vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="f9d78-116">This article covers debugging a service that's running on the local computer, but you can also debug Windows Services that are running on a remote computer.</span></span> <span data-ttu-id="f9d78-117">Viz téma [vzdálené ladění](/visualstudio/debugger/debug-installed-app-package).</span><span class="sxs-lookup"><span data-stu-id="f9d78-117">See [Remote Debugging](/visualstudio/debugger/debug-installed-app-package).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9d78-118"><xref:System.ServiceProcess.ServiceBase.OnStart%2A> Ladění metody může být obtížné, protože správce řízení služeb má za následek limit 30 sekund pro všechny pokusy o spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="f9d78-118">Debugging the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method can be difficult because the Services Control Manager imposes a 30-second limit on all attempts to start a service.</span></span> <span data-ttu-id="f9d78-119">Další informace najdete v tématu [řešení potíží: Ladění služeb](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md)systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f9d78-119">For more information, see [Troubleshooting: Debugging Windows Services](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="f9d78-120">Chcete-li získat smysluplné informace pro ladění, ladicí program sady Visual Studio potřebuje najít soubory symbolů pro binární soubory, které jsou laděny.</span><span class="sxs-lookup"><span data-stu-id="f9d78-120">To get meaningful information for debugging, the Visual Studio debugger needs to find symbol files for the binaries that are being debugged.</span></span> <span data-ttu-id="f9d78-121">Pokud ladíte službu, kterou jste vytvořili v aplikaci Visual Studio, soubory symbolů (soubory. pdb) jsou ve stejné složce jako spustitelný soubor nebo knihovna a ladicí program je načte automaticky.</span><span class="sxs-lookup"><span data-stu-id="f9d78-121">If you are debugging a service that you built in Visual Studio, the symbol files (.pdb files) are in the same folder as the executable or library, and the debugger loads them automatically.</span></span> <span data-ttu-id="f9d78-122">Pokud ladíte službu, kterou jste nesestavili, měli byste nejprve vyhledat symboly pro službu a ověřit, zda je lze najít pomocí ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="f9d78-122">If you are debugging a service that you didn't build, you should first find symbols for the service and make sure they can be found by the debugger.</span></span> <span data-ttu-id="f9d78-123">Viz [určení symbolu (. pdb) a zdrojových souborů v ladicím programu sady Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span><span class="sxs-lookup"><span data-stu-id="f9d78-123">See [Specify Symbol (.pdb) and Source Files in the Visual Studio Debugger](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span></span> <span data-ttu-id="f9d78-124">Pokud ladíte systémový proces nebo chcete mít symboly pro systémová volání ve vašich službách, měli byste přidat servery symbolů společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f9d78-124">If you're debugging a system process or want to have symbols for system calls in your services, you should add the Microsoft Symbol Servers.</span></span> <span data-ttu-id="f9d78-125">Viz [symboly ladění](/windows/desktop/DxTechArts/debugging-with-symbols).</span><span class="sxs-lookup"><span data-stu-id="f9d78-125">See [Debugging Symbols](/windows/desktop/DxTechArts/debugging-with-symbols).</span></span>  
  
### <a name="to-debug-a-service"></a><span data-ttu-id="f9d78-126">Ladění služby</span><span class="sxs-lookup"><span data-stu-id="f9d78-126">To debug a service</span></span>  
  
1. <span data-ttu-id="f9d78-127">Sestavte službu v konfiguraci ladění.</span><span class="sxs-lookup"><span data-stu-id="f9d78-127">Build your service in the Debug configuration.</span></span>  
  
2. <span data-ttu-id="f9d78-128">Nainstalujte svoji službu.</span><span class="sxs-lookup"><span data-stu-id="f9d78-128">Install your service.</span></span> <span data-ttu-id="f9d78-129">Další informace najdete v tématu [jak: Nainstalujte a odinstalujte](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)služby.</span><span class="sxs-lookup"><span data-stu-id="f9d78-129">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
3. <span data-ttu-id="f9d78-130">Spusťte službu, buď ze **správce řízení služeb**, **Průzkumník serveru**, nebo z kódu.</span><span class="sxs-lookup"><span data-stu-id="f9d78-130">Start your service, either from **Services Control Manager**, **Server Explorer**, or from code.</span></span> <span data-ttu-id="f9d78-131">Další informace najdete v tématu [jak: Spusťte služby](../../../docs/framework/windows-services/how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="f9d78-131">For more information, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span>  
  
4. <span data-ttu-id="f9d78-132">Spusťte Visual Studio s přihlašovacími údaji správce, abyste se mohli připojit k systémovým procesům.</span><span class="sxs-lookup"><span data-stu-id="f9d78-132">Start Visual Studio with administrative credentials so you can attach to system processes.</span></span>  
  
5. <span data-ttu-id="f9d78-133">Volitelné Na řádku nabídek sady Visual Studio vyberte **nástroje**, **Možnosti**.</span><span class="sxs-lookup"><span data-stu-id="f9d78-133">(Optional) On the Visual Studio menu bar, choose **Tools**, **Options**.</span></span> <span data-ttu-id="f9d78-134">V dialogovém okně **Možnosti** zvolte možnost **ladění**, **symboly**, zaškrtněte políčko **Microsoft Symbol Servers** a pak klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="f9d78-134">In the **Options** dialog box, choose **Debugging**, **Symbols**, select the **Microsoft Symbol Servers** check box, and then choose the **OK** button.</span></span>  
  
6. <span data-ttu-id="f9d78-135">Na panelu nabídek vyberte v nabídce **ladit** nebo **nástroje** možnost **připojit k procesu** .</span><span class="sxs-lookup"><span data-stu-id="f9d78-135">On the menu bar, choose **Attach to Process** from the **Debug** or **Tools** menu.</span></span> <span data-ttu-id="f9d78-136">Kombinace CTRL + ALT + P)</span><span class="sxs-lookup"><span data-stu-id="f9d78-136">(Keyboard: Ctrl+Alt+P)</span></span>  
  
     <span data-ttu-id="f9d78-137">Zobrazí se dialogové okno **procesy** .</span><span class="sxs-lookup"><span data-stu-id="f9d78-137">The **Processes** dialog box appears.</span></span>  
  
7. <span data-ttu-id="f9d78-138">Zaškrtněte políčko **Zobrazit procesy všech uživatelů** .</span><span class="sxs-lookup"><span data-stu-id="f9d78-138">Select the **Show processes from all users** check box.</span></span>  
  
8. <span data-ttu-id="f9d78-139">V části **Dostupné procesy** zvolte proces pro vaši službu a pak zvolte **připojit**.</span><span class="sxs-lookup"><span data-stu-id="f9d78-139">In the **Available Processes** section, choose the process for your service, and then choose **Attach**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="f9d78-140">Tento proces bude mít stejný název jako spustitelný soubor pro vaši službu.</span><span class="sxs-lookup"><span data-stu-id="f9d78-140">The process will have the same name as the executable file for your service.</span></span>  
  
     <span data-ttu-id="f9d78-141">**Připojit k procesu** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="f9d78-141">The **Attach to Process** dialog box appears.</span></span>  
  
9. <span data-ttu-id="f9d78-142">Zvolte příslušné možnosti a pak kliknutím na **tlačítko OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="f9d78-142">Choose the appropriate options, and then choose **OK** to close the dialog box.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f9d78-143">Nyní jste v režimu ladění.</span><span class="sxs-lookup"><span data-stu-id="f9d78-143">You are now in debug mode.</span></span>  
  
10. <span data-ttu-id="f9d78-144">Nastavte všechny zarážky, které chcete použít ve svém kódu.</span><span class="sxs-lookup"><span data-stu-id="f9d78-144">Set any breakpoints you want to use in your code.</span></span>  
  
11. <span data-ttu-id="f9d78-145">Přístup ke Správci řízení služeb a manipulaci se službou, odesílání příkazů zastavit, pozastavit a pokračovat, aby byly zasaženy vaše zarážky.</span><span class="sxs-lookup"><span data-stu-id="f9d78-145">Access the Services Control Manager and manipulate your service, sending stop, pause, and continue commands to hit your breakpoints.</span></span> <span data-ttu-id="f9d78-146">Další informace o spuštění Správce řízení služeb naleznete v tématu [How to: Spusťte služby](../../../docs/framework/windows-services/how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="f9d78-146">For more information about running the Services Control Manager, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span> <span data-ttu-id="f9d78-147">Přečtěte si [také téma řešení potíží: Ladění služeb](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md)systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f9d78-147">Also, see [Troubleshooting: Debugging Windows Services](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span></span>  
  
## <a name="debugging-tips-for-windows-services"></a><span data-ttu-id="f9d78-148">Tipy pro ladění pro služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="f9d78-148">Debugging Tips for Windows Services</span></span>  
 <span data-ttu-id="f9d78-149">Připojení k procesu služby vám umožní ladit většinu, ale ne vše, kód pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="f9d78-149">Attaching to the service's process allows you to debug most, but not all, the code for that service.</span></span> <span data-ttu-id="f9d78-150">Například vzhledem k tomu, že služba již byla spuštěna, nelze ladit kód v <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodě služby nebo kód `Main` v metodě, která slouží k načtení služby tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="f9d78-150">For example, because the service has already been started, you cannot debug the code in the service's <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method or the code in the `Main` method that is used to load the service this way.</span></span> <span data-ttu-id="f9d78-151">Jedním ze způsobů, jak toto omezení obejít, je vytvořit dočasnou druhou službu ve vaší aplikaci služby, která existuje jenom k podpoře ladění.</span><span class="sxs-lookup"><span data-stu-id="f9d78-151">One way to work around this limitation is to create a temporary second service in your service application that exists only to aid in debugging.</span></span> <span data-ttu-id="f9d78-152">Můžete nainstalovat obě služby a potom spustit tuto fiktivní službu pro načtení procesu služby.</span><span class="sxs-lookup"><span data-stu-id="f9d78-152">You can install both services, and then start this dummy service to load the service process.</span></span> <span data-ttu-id="f9d78-153">Jakmile dočasná služba spustí proces, můžete použít nabídku **ladit** v aplikaci Visual Studio k připojení k procesu služby.</span><span class="sxs-lookup"><span data-stu-id="f9d78-153">Once the temporary service has started the process, you can use the **Debug** menu in Visual Studio to attach to the service process.</span></span>  
  
 <span data-ttu-id="f9d78-154">Zkuste přidat volání do <xref:System.Threading.Thread.Sleep%2A> metody pro zpoždění akce, dokud se nebudete moct připojit k procesu.</span><span class="sxs-lookup"><span data-stu-id="f9d78-154">Try adding calls to the <xref:System.Threading.Thread.Sleep%2A> method to delay action until you’re able to attach to the process.</span></span>  
  
 <span data-ttu-id="f9d78-155">Zkuste změnit program na běžnou konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f9d78-155">Try changing the program to a regular console application.</span></span> <span data-ttu-id="f9d78-156">Pokud to chcete provést, přepište `Main` metodu následujícím způsobem, aby ji bylo možné spustit jak jako službu systému Windows, tak jako konzolovou aplikaci v závislosti na tom, jak je spuštěna.</span><span class="sxs-lookup"><span data-stu-id="f9d78-156">To do this, rewrite the `Main` method as follows so it can run both as a Windows Service and as a console application, depending on how it's started.</span></span>  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a><span data-ttu-id="f9d78-157">Postupy: Spuštění služby systému Windows jako konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="f9d78-157">How to: Run a Windows Service as a console application</span></span>  
  
1. <span data-ttu-id="f9d78-158">Přidejte do služby metodu, která spouští <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody a: <xref:System.ServiceProcess.ServiceBase.OnStop%2A></span><span class="sxs-lookup"><span data-stu-id="f9d78-158">Add a method to your service that runs the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods:</span></span>  
  
    ```csharp  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2. <span data-ttu-id="f9d78-159">Přepište `Main` metodu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f9d78-159">Rewrite the `Main` method as follows:</span></span>  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        if (Environment.UserInteractive)  
        {  
            MyNewService service1 = new MyNewService(args);  
            service1.TestStartupAndStop(args);  
        }  
        else  
        {  
            // Put the body of your old Main method here.  
        }  
    }
    ```  
  
3. <span data-ttu-id="f9d78-160">Na kartě **aplikace** vlastností projektu nastavte **Typ výstupu** na **konzolovou aplikaci**.</span><span class="sxs-lookup"><span data-stu-id="f9d78-160">In the **Application** tab of the project's properties, set the **Output type** to **Console Application**.</span></span>  
  
4. <span data-ttu-id="f9d78-161">Vyberte možnost **Spustit ladění** (F5).</span><span class="sxs-lookup"><span data-stu-id="f9d78-161">Choose **Start Debugging** (F5).</span></span>  
  
5. <span data-ttu-id="f9d78-162">Chcete-li program znovu spustit jako službu systému Windows, nainstalujte jej a spusťte jej obvyklým způsobem pro službu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f9d78-162">To run the program as a Windows Service again, install it and start it as usual for a Windows Service.</span></span> <span data-ttu-id="f9d78-163">Nemusíte tyto změny měnit.</span><span class="sxs-lookup"><span data-stu-id="f9d78-163">It's not necessary to reverse these changes.</span></span>  
  
 <span data-ttu-id="f9d78-164">V některých případech, například pokud chcete ladit problém, ke kterému dochází pouze při spuštění systému, je nutné použít ladicí program systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f9d78-164">In some cases, such as when you want to debug an issue that occurs only on system startup, you have to use the Windows debugger.</span></span> <span data-ttu-id="f9d78-165">[Stáhněte si sadu Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk) a podívejte se, [jak ladit služby systému Windows](https://support.microsoft.com/kb/824344).</span><span class="sxs-lookup"><span data-stu-id="f9d78-165">[Download the Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk) and see [How to debug Windows Services](https://support.microsoft.com/kb/824344).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9d78-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9d78-166">See also</span></span>

- [<span data-ttu-id="f9d78-167">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="f9d78-167">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="f9d78-168">Postupy: Instalace a odinstalace služeb</span><span class="sxs-lookup"><span data-stu-id="f9d78-168">How to: Install and Uninstall Services</span></span>](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)
- [<span data-ttu-id="f9d78-169">Postupy: Spustit služby</span><span class="sxs-lookup"><span data-stu-id="f9d78-169">How to: Start Services</span></span>](../../../docs/framework/windows-services/how-to-start-services.md)
- [<span data-ttu-id="f9d78-170">Ladění služby</span><span class="sxs-lookup"><span data-stu-id="f9d78-170">Debugging a Service</span></span>](/windows/desktop/Services/debugging-a-service)
