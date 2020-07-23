---
title: 'Postupy: Ladění aplikací spouštěných jako služby systému Windows'
description: Pochopte, jak ladit aplikace služby systému Windows, které nejsou stejně jednoduché pro ladění jako jiné typy aplikací sady Visual Studio.
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- Windows NT services, debugging
- Windows Service applications, debugging
- services, debugging
ms.assetid: 63ab0800-0f05-4f1e-88e6-94c73fd920a2
author: ghogen
ms.openlocfilehash: fb58f2ff4f480347f0f233ecd9a619cf287cfdfd
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925758"
---
# <a name="how-to-debug-windows-service-applications"></a><span data-ttu-id="3bb37-103">Postupy: Ladění aplikací spouštěných jako služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="3bb37-103">How to: Debug Windows Service Applications</span></span>
<span data-ttu-id="3bb37-104">Služba musí být spuštěna v kontextu správce řízení služeb, nikoli v rámci sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3bb37-104">A service must be run from within the context of the Services Control Manager rather than from within Visual Studio.</span></span> <span data-ttu-id="3bb37-105">Z tohoto důvodu ladění služby není tak jednoduché jako ladění jiných typů aplikací sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3bb37-105">For this reason, debugging a service is not as straightforward as debugging other Visual Studio application types.</span></span> <span data-ttu-id="3bb37-106">Chcete-li ladit službu, je nutné spustit službu a potom připojit ladicí program k procesu, ve kterém je spuštěna.</span><span class="sxs-lookup"><span data-stu-id="3bb37-106">To debug a service, you must start the service and then attach a debugger to the process in which it is running.</span></span> <span data-ttu-id="3bb37-107">Pak můžete ladit aplikaci pomocí všech standardních funkcí ladění sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3bb37-107">You can then debug your application by using all of the standard debugging functionality of Visual Studio.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="3bb37-108">K procesu se nemusíte připojovat, Pokud nevíte, co proces je, a porozumět důsledkům připojení a případně usmrcení tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="3bb37-108">You should not attach to a process unless you know what the process is and understand the consequences of attaching to and possibly killing that process.</span></span> <span data-ttu-id="3bb37-109">Například pokud se připojíte k procesu WinLogon a pak zastavíte ladění, systém se zastaví, protože nemůže pracovat bez procesu WinLogon.</span><span class="sxs-lookup"><span data-stu-id="3bb37-109">For example, if you attach to the WinLogon process and then stop debugging, the system will halt because it can’t operate without WinLogon.</span></span>  
  
 <span data-ttu-id="3bb37-110">Ladicí program lze připojit pouze ke spuštěné službě.</span><span class="sxs-lookup"><span data-stu-id="3bb37-110">You can attach the debugger only to a running service.</span></span> <span data-ttu-id="3bb37-111">Proces přílohy přerušuje aktuální fungování vaší služby. ve skutečnosti se nezastaví nebo nezastaví zpracování služby.</span><span class="sxs-lookup"><span data-stu-id="3bb37-111">The attachment process interrupts the current functioning of your service; it doesn’t actually stop or pause the service's processing.</span></span> <span data-ttu-id="3bb37-112">To znamená, že pokud vaše služba běží při zahájení ladění, je při ladění stále technicky ve stavu spuštěno, ale jeho zpracování bylo pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="3bb37-112">That is, if your service is running when you begin debugging, it is still technically in the Started state as you debug it, but its processing has been suspended.</span></span>  
  
 <span data-ttu-id="3bb37-113">Po připojení k procesu můžete nastavit zarážky a použít je k ladění kódu.</span><span class="sxs-lookup"><span data-stu-id="3bb37-113">After attaching to the process, you can set breakpoints and use these to debug your code.</span></span> <span data-ttu-id="3bb37-114">Po zavření dialogového okna, které použijete k připojení k procesu, budete efektivně v režimu ladění.</span><span class="sxs-lookup"><span data-stu-id="3bb37-114">Once you exit the dialog box you use to attach to the process, you are effectively in debug mode.</span></span> <span data-ttu-id="3bb37-115">Správce řízení služeb můžete použít ke spuštění, zastavení, pozastavení a pokračování služby, čímž se zastaví zarážky, které jste nastavili.</span><span class="sxs-lookup"><span data-stu-id="3bb37-115">You can use the Services Control Manager to start, stop, pause and continue your service, thus hitting the breakpoints you've set.</span></span> <span data-ttu-id="3bb37-116">Po úspěšném ladění můžete tuto fiktivní službu odebrat později.</span><span class="sxs-lookup"><span data-stu-id="3bb37-116">You can later remove this dummy service after debugging is successful.</span></span>  
  
 <span data-ttu-id="3bb37-117">Tento článek popisuje ladění služby spuštěné v místním počítači, ale můžete také ladit služby systému Windows, které jsou spuštěny na vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="3bb37-117">This article covers debugging a service that's running on the local computer, but you can also debug Windows Services that are running on a remote computer.</span></span> <span data-ttu-id="3bb37-118">Viz téma [vzdálené ladění](/visualstudio/debugger/debug-installed-app-package).</span><span class="sxs-lookup"><span data-stu-id="3bb37-118">See [Remote Debugging](/visualstudio/debugger/debug-installed-app-package).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3bb37-119">Ladění <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody může být obtížné, protože správce řízení služeb má za následek limit 30 sekund pro všechny pokusy o spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="3bb37-119">Debugging the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method can be difficult because the Services Control Manager imposes a 30-second limit on all attempts to start a service.</span></span> <span data-ttu-id="3bb37-120">Další informace najdete v tématu [řešení potíží: ladění služeb systému Windows](troubleshooting-debugging-windows-services.md).</span><span class="sxs-lookup"><span data-stu-id="3bb37-120">For more information, see [Troubleshooting: Debugging Windows Services](troubleshooting-debugging-windows-services.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="3bb37-121">Chcete-li získat smysluplné informace pro ladění, ladicí program sady Visual Studio potřebuje najít soubory symbolů pro binární soubory, které jsou laděny.</span><span class="sxs-lookup"><span data-stu-id="3bb37-121">To get meaningful information for debugging, the Visual Studio debugger needs to find symbol files for the binaries that are being debugged.</span></span> <span data-ttu-id="3bb37-122">Pokud ladíte službu, kterou jste vytvořili v aplikaci Visual Studio, soubory symbolů (soubory. pdb) jsou ve stejné složce jako spustitelný soubor nebo knihovna a ladicí program je načte automaticky.</span><span class="sxs-lookup"><span data-stu-id="3bb37-122">If you are debugging a service that you built in Visual Studio, the symbol files (.pdb files) are in the same folder as the executable or library, and the debugger loads them automatically.</span></span> <span data-ttu-id="3bb37-123">Pokud ladíte službu, kterou jste nesestavili, měli byste nejprve vyhledat symboly pro službu a ověřit, zda je lze najít pomocí ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="3bb37-123">If you are debugging a service that you didn't build, you should first find symbols for the service and make sure they can be found by the debugger.</span></span> <span data-ttu-id="3bb37-124">Viz [určení symbolu (. pdb) a zdrojových souborů v ladicím programu sady Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span><span class="sxs-lookup"><span data-stu-id="3bb37-124">See [Specify Symbol (.pdb) and Source Files in the Visual Studio Debugger](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span></span> <span data-ttu-id="3bb37-125">Pokud ladíte systémový proces nebo chcete mít symboly pro systémová volání ve vašich službách, měli byste přidat servery symbolů společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3bb37-125">If you're debugging a system process or want to have symbols for system calls in your services, you should add the Microsoft Symbol Servers.</span></span> <span data-ttu-id="3bb37-126">Viz [symboly ladění](/windows/desktop/DxTechArts/debugging-with-symbols).</span><span class="sxs-lookup"><span data-stu-id="3bb37-126">See [Debugging Symbols](/windows/desktop/DxTechArts/debugging-with-symbols).</span></span>  
  
### <a name="to-debug-a-service"></a><span data-ttu-id="3bb37-127">Ladění služby</span><span class="sxs-lookup"><span data-stu-id="3bb37-127">To debug a service</span></span>  
  
1. <span data-ttu-id="3bb37-128">Sestavte službu v konfiguraci ladění.</span><span class="sxs-lookup"><span data-stu-id="3bb37-128">Build your service in the Debug configuration.</span></span>  
  
2. <span data-ttu-id="3bb37-129">Nainstalujte svoji službu.</span><span class="sxs-lookup"><span data-stu-id="3bb37-129">Install your service.</span></span> <span data-ttu-id="3bb37-130">Další informace najdete v tématu [Postupy: instalace a odinstalace služeb](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="3bb37-130">For more information, see [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).</span></span>  
  
3. <span data-ttu-id="3bb37-131">Spusťte službu, buď ze **správce řízení služeb**, **Průzkumník serveru**, nebo z kódu.</span><span class="sxs-lookup"><span data-stu-id="3bb37-131">Start your service, either from **Services Control Manager**, **Server Explorer**, or from code.</span></span> <span data-ttu-id="3bb37-132">Další informace naleznete v tématu [How to: Start Services](how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="3bb37-132">For more information, see [How to: Start Services](how-to-start-services.md).</span></span>  
  
4. <span data-ttu-id="3bb37-133">Spusťte Visual Studio s přihlašovacími údaji správce, abyste se mohli připojit k systémovým procesům.</span><span class="sxs-lookup"><span data-stu-id="3bb37-133">Start Visual Studio with administrative credentials so you can attach to system processes.</span></span>  
  
5. <span data-ttu-id="3bb37-134">Volitelné Na řádku nabídek sady Visual Studio vyberte **nástroje**, **Možnosti**.</span><span class="sxs-lookup"><span data-stu-id="3bb37-134">(Optional) On the Visual Studio menu bar, choose **Tools**, **Options**.</span></span> <span data-ttu-id="3bb37-135">V dialogovém okně **Možnosti** zvolte možnost **ladění**, **symboly**, zaškrtněte políčko **Microsoft Symbol Servers** a pak klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="3bb37-135">In the **Options** dialog box, choose **Debugging**, **Symbols**, select the **Microsoft Symbol Servers** check box, and then choose the **OK** button.</span></span>  
  
6. <span data-ttu-id="3bb37-136">Na panelu nabídek vyberte v nabídce **ladit** nebo **nástroje** možnost **připojit k procesu** .</span><span class="sxs-lookup"><span data-stu-id="3bb37-136">On the menu bar, choose **Attach to Process** from the **Debug** or **Tools** menu.</span></span> <span data-ttu-id="3bb37-137">(Klávesnice: CTRL + ALT + P)</span><span class="sxs-lookup"><span data-stu-id="3bb37-137">(Keyboard: Ctrl+Alt+P)</span></span>  
  
     <span data-ttu-id="3bb37-138">Zobrazí se dialogové okno **procesy** .</span><span class="sxs-lookup"><span data-stu-id="3bb37-138">The **Processes** dialog box appears.</span></span>  
  
7. <span data-ttu-id="3bb37-139">Zaškrtněte políčko **Zobrazit procesy všech uživatelů** .</span><span class="sxs-lookup"><span data-stu-id="3bb37-139">Select the **Show processes from all users** check box.</span></span>  
  
8. <span data-ttu-id="3bb37-140">V části **Dostupné procesy** zvolte proces pro vaši službu a pak zvolte **připojit**.</span><span class="sxs-lookup"><span data-stu-id="3bb37-140">In the **Available Processes** section, choose the process for your service, and then choose **Attach**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="3bb37-141">Tento proces bude mít stejný název jako spustitelný soubor pro vaši službu.</span><span class="sxs-lookup"><span data-stu-id="3bb37-141">The process will have the same name as the executable file for your service.</span></span>  
  
     <span data-ttu-id="3bb37-142">Zobrazí se dialogové okno **připojit k procesu** .</span><span class="sxs-lookup"><span data-stu-id="3bb37-142">The **Attach to Process** dialog box appears.</span></span>  
  
9. <span data-ttu-id="3bb37-143">Zvolte příslušné možnosti a pak kliknutím na **tlačítko OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="3bb37-143">Choose the appropriate options, and then choose **OK** to close the dialog box.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3bb37-144">Nyní jste v režimu ladění.</span><span class="sxs-lookup"><span data-stu-id="3bb37-144">You are now in debug mode.</span></span>  
  
10. <span data-ttu-id="3bb37-145">Nastavte všechny zarážky, které chcete použít ve svém kódu.</span><span class="sxs-lookup"><span data-stu-id="3bb37-145">Set any breakpoints you want to use in your code.</span></span>  
  
11. <span data-ttu-id="3bb37-146">Přístup ke Správci řízení služeb a manipulaci se službou, odesílání příkazů zastavit, pozastavit a pokračovat, aby byly zasaženy vaše zarážky.</span><span class="sxs-lookup"><span data-stu-id="3bb37-146">Access the Services Control Manager and manipulate your service, sending stop, pause, and continue commands to hit your breakpoints.</span></span> <span data-ttu-id="3bb37-147">Další informace o spuštění Správce řízení služeb naleznete v tématu [How to: Start Services](how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="3bb37-147">For more information about running the Services Control Manager, see [How to: Start Services](how-to-start-services.md).</span></span> <span data-ttu-id="3bb37-148">Přečtěte si také téma [řešení potíží: ladění služeb systému Windows](troubleshooting-debugging-windows-services.md).</span><span class="sxs-lookup"><span data-stu-id="3bb37-148">Also, see [Troubleshooting: Debugging Windows Services](troubleshooting-debugging-windows-services.md).</span></span>  
  
## <a name="debugging-tips-for-windows-services"></a><span data-ttu-id="3bb37-149">Tipy pro ladění pro služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="3bb37-149">Debugging Tips for Windows Services</span></span>  
 <span data-ttu-id="3bb37-150">Připojení k procesu služby vám umožní ladit většinu, ale ne vše, kód pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="3bb37-150">Attaching to the service's process allows you to debug most, but not all, the code for that service.</span></span> <span data-ttu-id="3bb37-151">Například vzhledem k tomu, že služba již byla spuštěna, nelze ladit kód v <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodě služby nebo kód v `Main` metodě, která slouží k načtení služby tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="3bb37-151">For example, because the service has already been started, you cannot debug the code in the service's <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method or the code in the `Main` method that is used to load the service this way.</span></span> <span data-ttu-id="3bb37-152">Jedním ze způsobů, jak toto omezení obejít, je vytvořit dočasnou druhou službu ve vaší aplikaci služby, která existuje jenom k podpoře ladění.</span><span class="sxs-lookup"><span data-stu-id="3bb37-152">One way to work around this limitation is to create a temporary second service in your service application that exists only to aid in debugging.</span></span> <span data-ttu-id="3bb37-153">Můžete nainstalovat obě služby a potom spustit tuto fiktivní službu pro načtení procesu služby.</span><span class="sxs-lookup"><span data-stu-id="3bb37-153">You can install both services, and then start this dummy service to load the service process.</span></span> <span data-ttu-id="3bb37-154">Jakmile dočasná služba spustí proces, můžete použít nabídku **ladit** v aplikaci Visual Studio k připojení k procesu služby.</span><span class="sxs-lookup"><span data-stu-id="3bb37-154">Once the temporary service has started the process, you can use the **Debug** menu in Visual Studio to attach to the service process.</span></span>  
  
 <span data-ttu-id="3bb37-155">Zkuste přidat volání do <xref:System.Threading.Thread.Sleep%2A> metody pro zpoždění akce, dokud se nebudete moct připojit k procesu.</span><span class="sxs-lookup"><span data-stu-id="3bb37-155">Try adding calls to the <xref:System.Threading.Thread.Sleep%2A> method to delay action until you’re able to attach to the process.</span></span>  
  
 <span data-ttu-id="3bb37-156">Zkuste změnit program na běžnou konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3bb37-156">Try changing the program to a regular console application.</span></span> <span data-ttu-id="3bb37-157">Pokud to chcete provést, přepište `Main` metodu následujícím způsobem, aby ji bylo možné spustit jak jako službu systému Windows, tak jako konzolovou aplikaci v závislosti na tom, jak je spuštěna.</span><span class="sxs-lookup"><span data-stu-id="3bb37-157">To do this, rewrite the `Main` method as follows so it can run both as a Windows Service and as a console application, depending on how it's started.</span></span>  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a><span data-ttu-id="3bb37-158">Postupy: spuštění služby systému Windows jako konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="3bb37-158">How to: Run a Windows Service as a console application</span></span>  
  
1. <span data-ttu-id="3bb37-159">Přidejte do služby metodu, která spouští <xref:System.ServiceProcess.ServiceBase.OnStart%2A> <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody a:</span><span class="sxs-lookup"><span data-stu-id="3bb37-159">Add a method to your service that runs the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods:</span></span>  
  
    ```csharp  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2. <span data-ttu-id="3bb37-160">Přepište `Main` metodu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="3bb37-160">Rewrite the `Main` method as follows:</span></span>  
  
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
  
3. <span data-ttu-id="3bb37-161">Na kartě **aplikace** vlastností projektu nastavte **Typ výstupu** na **konzolovou aplikaci**.</span><span class="sxs-lookup"><span data-stu-id="3bb37-161">In the **Application** tab of the project's properties, set the **Output type** to **Console Application**.</span></span>  
  
4. <span data-ttu-id="3bb37-162">Vyberte možnost **Spustit ladění** (F5).</span><span class="sxs-lookup"><span data-stu-id="3bb37-162">Choose **Start Debugging** (F5).</span></span>  
  
5. <span data-ttu-id="3bb37-163">Chcete-li program znovu spustit jako službu systému Windows, nainstalujte jej a spusťte jej obvyklým způsobem pro službu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="3bb37-163">To run the program as a Windows Service again, install it and start it as usual for a Windows Service.</span></span> <span data-ttu-id="3bb37-164">Nemusíte tyto změny měnit.</span><span class="sxs-lookup"><span data-stu-id="3bb37-164">It's not necessary to reverse these changes.</span></span>  
  
 <span data-ttu-id="3bb37-165">V některých případech, například pokud chcete ladit problém, ke kterému dochází pouze při spuštění systému, je nutné použít ladicí program systému Windows.</span><span class="sxs-lookup"><span data-stu-id="3bb37-165">In some cases, such as when you want to debug an issue that occurs only on system startup, you have to use the Windows debugger.</span></span> <span data-ttu-id="3bb37-166">[Stáhněte si sadu Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk) a podívejte se, [jak ladit služby systému Windows](https://support.microsoft.com/kb/824344).</span><span class="sxs-lookup"><span data-stu-id="3bb37-166">[Download the Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk) and see [How to debug Windows Services](https://support.microsoft.com/kb/824344).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bb37-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="3bb37-167">See also</span></span>

- [<span data-ttu-id="3bb37-168">Představení aplikací spouštěných jako služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="3bb37-168">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="3bb37-169">Postupy: Instalace a odinstalace služeb</span><span class="sxs-lookup"><span data-stu-id="3bb37-169">How to: Install and Uninstall Services</span></span>](how-to-install-and-uninstall-services.md)
- [<span data-ttu-id="3bb37-170">Postupy: Spuštění služby</span><span class="sxs-lookup"><span data-stu-id="3bb37-170">How to: Start Services</span></span>](how-to-start-services.md)
- [<span data-ttu-id="3bb37-171">Ladění služby</span><span class="sxs-lookup"><span data-stu-id="3bb37-171">Debugging a Service</span></span>](/windows/desktop/Services/debugging-a-service)
