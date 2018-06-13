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
manager: douge
ms.openlocfilehash: 2c73ccd75bdbd1298371921bababa87ba4520495
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518047"
---
# <a name="how-to-debug-windows-service-applications"></a><span data-ttu-id="1d822-102">Postupy: Ladění aplikací spouštěných jako služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="1d822-102">How to: Debug Windows Service Applications</span></span>
<span data-ttu-id="1d822-103">Služba musí být spuštěn v kontextu správci řízení služeb a nikoli z v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1d822-103">A service must be run from within the context of the Services Control Manager rather than from within Visual Studio.</span></span> <span data-ttu-id="1d822-104">Z tohoto důvodu ladění služby není stejně jednoduché jako ladění jinými typy aplikací Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1d822-104">For this reason, debugging a service is not as straightforward as debugging other Visual Studio application types.</span></span> <span data-ttu-id="1d822-105">K ladění služby, musíte spustit službu a pak připojit ladicí program k procesu, ve kterém je spuštěna.</span><span class="sxs-lookup"><span data-stu-id="1d822-105">To debug a service, you must start the service and then attach a debugger to the process in which it is running.</span></span> <span data-ttu-id="1d822-106">Potom můžete ladění aplikace s použitím všechny standardní ladění funkce sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1d822-106">You can then debug your application by using all of the standard debugging functionality of Visual Studio.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="1d822-107">Nesmí se připojit k procesu, ledaže byste věděli, co proces a chápu důsledky se připojuje k a které by mohly mít ukončení tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="1d822-107">You should not attach to a process unless you know what the process is and understand the consequences of attaching to and possibly killing that process.</span></span> <span data-ttu-id="1d822-108">Například pokud připojit k procesu přihlášení do systému Windows a potom zastavte ladění, systém se zastaví protože nemůže pracovat bez přihlášení do systému Windows.</span><span class="sxs-lookup"><span data-stu-id="1d822-108">For example, if you attach to the WinLogon process and then stop debugging, the system will halt because it can’t operate without WinLogon.</span></span>  
  
 <span data-ttu-id="1d822-109">Ladicí program můžete připojit pouze k spuštěnou službu.</span><span class="sxs-lookup"><span data-stu-id="1d822-109">You can attach the debugger only to a running service.</span></span> <span data-ttu-id="1d822-110">Proces přílohy přerušení aktuální fungování služby; není ve skutečnosti zastavení nebo pozastavení služby zpracování.</span><span class="sxs-lookup"><span data-stu-id="1d822-110">The attachment process interrupts the current functioning of your service; it doesn’t actually stop or pause the service's processing.</span></span> <span data-ttu-id="1d822-111">To znamená pokud je vaše služba spuštěná, abyste před zahájením ladění, je stále technicky ve stavu spuštěno jako ladění ji, ale jeho zpracování bylo pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="1d822-111">That is, if your service is running when you begin debugging, it is still technically in the Started state as you debug it, but its processing has been suspended.</span></span>  
  
 <span data-ttu-id="1d822-112">Po připojení k procesu, můžete nastavit zarážky a tyto slouží k ladění kódu.</span><span class="sxs-lookup"><span data-stu-id="1d822-112">After attaching to the process, you can set breakpoints and use these to debug your code.</span></span> <span data-ttu-id="1d822-113">Po ukončení dialogu, který používáte pro připojení k procesu jste efektivně v režimu ladění.</span><span class="sxs-lookup"><span data-stu-id="1d822-113">Once you exit the dialog box you use to attach to the process, you are effectively in debug mode.</span></span> <span data-ttu-id="1d822-114">Správci řízení služeb můžete použít k spuštění, zastavení, pozastavení a pokračování služby, proto zarážek, které jste nastavili.</span><span class="sxs-lookup"><span data-stu-id="1d822-114">You can use the Services Control Manager to start, stop, pause and continue your service, thus hitting the breakpoints you've set.</span></span> <span data-ttu-id="1d822-115">Později můžete odebrat tuto službu fiktivní po úspěšné ladění.</span><span class="sxs-lookup"><span data-stu-id="1d822-115">You can later remove this dummy service after debugging is successful.</span></span>  
  
 <span data-ttu-id="1d822-116">Tento článek se zabývá ladění služba, která běží na místním počítači, ale můžete také ladění služby systému Windows, který běží na vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="1d822-116">This article covers debugging a service that's running on the local computer, but you can also debug Windows Services that are running on a remote computer.</span></span> <span data-ttu-id="1d822-117">V tématu [vzdálené ladění](/visualstudio/debugger/debug-installed-app-package).</span><span class="sxs-lookup"><span data-stu-id="1d822-117">See [Remote Debugging](/visualstudio/debugger/debug-installed-app-package).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d822-118">Ladění <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda může být složité, protože správci řízení služeb ukládá limitu 30 sekund na všechny pokusy o spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="1d822-118">Debugging the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method can be difficult because the Services Control Manager imposes a 30-second limit on all attempts to start a service.</span></span> <span data-ttu-id="1d822-119">Další informace najdete v tématu [řešení potíží: ladění služby systému Windows](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span><span class="sxs-lookup"><span data-stu-id="1d822-119">For more information, see [Troubleshooting: Debugging Windows Services](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="1d822-120">Získat důležité informace pro ladění, je potřeba najít soubory symbolů pro binární soubory, které se právě ladí ladicího programu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1d822-120">To get meaningful information for debugging, the Visual Studio debugger needs to find symbol files for the binaries that are being debugged.</span></span> <span data-ttu-id="1d822-121">Pokud ladíte služba, která jste vytvořili v sadě Visual Studio, soubory symbolů (soubory PDB) jsou ve stejné složce jako spustitelný soubor nebo knihovny a ladicí program načítá je automaticky.</span><span class="sxs-lookup"><span data-stu-id="1d822-121">If you are debugging a service that you built in Visual Studio, the symbol files (.pdb files) are in the same folder as the executable or library, and the debugger loads them automatically.</span></span> <span data-ttu-id="1d822-122">Pokud ladíte služba, která nebyla sestavení, doporučujeme nejprve najít symboly pro službu a ujistěte se, že najdete pomocí ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="1d822-122">If you are debugging a service that you didn't build, you should first find symbols for the service and make sure they can be found by the debugger.</span></span> <span data-ttu-id="1d822-123">V tématu [zadání symbolu (.pdb) a zdrojových souborů](http://msdn.microsoft.com/library/1105e169-5272-4e7c-b3e7-cda1b7798a6b).</span><span class="sxs-lookup"><span data-stu-id="1d822-123">See [Specify Symbol (.pdb) and Source Files](http://msdn.microsoft.com/library/1105e169-5272-4e7c-b3e7-cda1b7798a6b).</span></span> <span data-ttu-id="1d822-124">Pokud ladíte systémový proces nebo chcete mít symboly pro systémová volání v službách, měli byste přidat servery Microsoft symbolů.</span><span class="sxs-lookup"><span data-stu-id="1d822-124">If you're debugging a system process or want to have symbols for system calls in your services, you should add the Microsoft Symbol Servers.</span></span> <span data-ttu-id="1d822-125">V tématu [symboly ladění](http://msdn.microsoft.com/windows/desktop/ee416588.aspx).</span><span class="sxs-lookup"><span data-stu-id="1d822-125">See [Debugging Symbols](http://msdn.microsoft.com/windows/desktop/ee416588.aspx).</span></span>  
  
### <a name="to-debug-a-service"></a><span data-ttu-id="1d822-126">K ladění služby</span><span class="sxs-lookup"><span data-stu-id="1d822-126">To debug a service</span></span>  
  
1.  <span data-ttu-id="1d822-127">Vytvoření služby v konfiguraci ladění.</span><span class="sxs-lookup"><span data-stu-id="1d822-127">Build your service in the Debug configuration.</span></span>  
  
2.  <span data-ttu-id="1d822-128">Instalace služby.</span><span class="sxs-lookup"><span data-stu-id="1d822-128">Install your service.</span></span> <span data-ttu-id="1d822-129">Další informace najdete v tématu [postupy: instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="1d822-129">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
3.  <span data-ttu-id="1d822-130">Spuštění služby, buď z **správci řízení služeb**, **Průzkumníka serveru**, nebo z kódu.</span><span class="sxs-lookup"><span data-stu-id="1d822-130">Start your service, either from **Services Control Manager**, **Server Explorer**, or from code.</span></span> <span data-ttu-id="1d822-131">Další informace najdete v tématu [postupy: spuštění služby](../../../docs/framework/windows-services/how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="1d822-131">For more information, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span>  
  
4.  <span data-ttu-id="1d822-132">Spuštění sady Visual Studio s přihlašovacími údaji správce, takže se můžete připojit k systémovým procesům.</span><span class="sxs-lookup"><span data-stu-id="1d822-132">Start Visual Studio with administrative credentials so you can attach to system processes.</span></span>  
  
5.  <span data-ttu-id="1d822-133">(Volitelné) Na panelu nabídek Visual Studio zvolte **nástroje**, **možnosti**.</span><span class="sxs-lookup"><span data-stu-id="1d822-133">(Optional) On the Visual Studio menu bar, choose **Tools**, **Options**.</span></span> <span data-ttu-id="1d822-134">V **možnosti** dialogovém okně vyberte **ladění**, **symboly**, vyberte **servery symbolů Microsoft** zaškrtněte políčko a potom vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="1d822-134">In the **Options** dialog box, choose **Debugging**, **Symbols**, select the **Microsoft Symbol Servers** check box, and then choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="1d822-135">Na řádku nabídek zvolte **připojit k procesu** z **ladění** nebo **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="1d822-135">On the menu bar, choose **Attach to Process** from the **Debug** or **Tools** menu.</span></span> <span data-ttu-id="1d822-136">(Klávesové: Ctrl + Alt + P)</span><span class="sxs-lookup"><span data-stu-id="1d822-136">(Keyboard: Ctrl+Alt+P)</span></span>  
  
     <span data-ttu-id="1d822-137">**Procesy** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="1d822-137">The **Processes** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="1d822-138">Vyberte **Zobrazit procesy od všech uživatelů** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="1d822-138">Select the **Show processes from all users** check box.</span></span>  
  
8.  <span data-ttu-id="1d822-139">V **dostupné procesy** část, zvolte proces pro vaši službu a pak zvolte **Attach**.</span><span class="sxs-lookup"><span data-stu-id="1d822-139">In the **Available Processes** section, choose the process for your service, and then choose **Attach**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="1d822-140">Proces bude mít stejný název jako spustitelný soubor pro vaši službu.</span><span class="sxs-lookup"><span data-stu-id="1d822-140">The process will have the same name as the executable file for your service.</span></span>  
  
     <span data-ttu-id="1d822-141">**Připojit k procesu** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="1d822-141">The **Attach to Process** dialog box appears.</span></span>  
  
9. <span data-ttu-id="1d822-142">Vyberte požadované možnosti a pak zvolte **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="1d822-142">Choose the appropriate options, and then choose **OK** to close the dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1d822-143">Nyní jste v režimu ladění.</span><span class="sxs-lookup"><span data-stu-id="1d822-143">You are now in debug mode.</span></span>  
  
10. <span data-ttu-id="1d822-144">Nastavte všechny zarážky, které chcete použít v kódu.</span><span class="sxs-lookup"><span data-stu-id="1d822-144">Set any breakpoints you want to use in your code.</span></span>  
  
11. <span data-ttu-id="1d822-145">Přístup k správci řízení služeb a manipulaci s vaší služby, odesílání zastavení, pozastavení a pokračovat příkazy a stiskněte váš zarážky.</span><span class="sxs-lookup"><span data-stu-id="1d822-145">Access the Services Control Manager and manipulate your service, sending stop, pause, and continue commands to hit your breakpoints.</span></span> <span data-ttu-id="1d822-146">Další informace o spouštění správci řízení služeb najdete v tématu [postupy: spuštění služby](../../../docs/framework/windows-services/how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="1d822-146">For more information about running the Services Control Manager, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span> <span data-ttu-id="1d822-147">Další informace naleznete v [řešení potíží: ladění služby systému Windows](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span><span class="sxs-lookup"><span data-stu-id="1d822-147">Also, see [Troubleshooting: Debugging Windows Services](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span></span>  
  
## <a name="debugging-tips-for-windows-services"></a><span data-ttu-id="1d822-148">Ladění tipy pro služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="1d822-148">Debugging Tips for Windows Services</span></span>  
 <span data-ttu-id="1d822-149">Připojení k procesu služby umožňuje ladit nejvíce, ale ne všechny kód pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="1d822-149">Attaching to the service's process allows you to debug most, but not all, the code for that service.</span></span> <span data-ttu-id="1d822-150">Například, protože služba již byla spuštěna, nelze ladění kódu v rámci služby <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda nebo kód `Main` metoda, která se používá k načtení služby tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="1d822-150">For example, because the service has already been started, you cannot debug the code in the service's <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method or the code in the `Main` method that is used to load the service this way.</span></span> <span data-ttu-id="1d822-151">Jeden způsob, jak toto omezení obejít je vytvoření dočasné druhý služby v aplikaci služby, které existuje jenom k ladění.</span><span class="sxs-lookup"><span data-stu-id="1d822-151">One way to work around this limitation is to create a temporary second service in your service application that exists only to aid in debugging.</span></span> <span data-ttu-id="1d822-152">Můžete nainstalovat obě služby a spusťte tuto službu fiktivní načíst proces služby.</span><span class="sxs-lookup"><span data-stu-id="1d822-152">You can install both services, and then start this dummy service to load the service process.</span></span> <span data-ttu-id="1d822-153">Až službu dočasné zahájil proces, můžete pomocí **ladění** nabídky v sadě Visual Studio pro připojení k procesu služby.</span><span class="sxs-lookup"><span data-stu-id="1d822-153">Once the temporary service has started the process, you can use the **Debug** menu in Visual Studio to attach to the service process.</span></span>  
  
 <span data-ttu-id="1d822-154">Zkuste přidat volání <xref:System.Threading.Thread.Sleep%2A> metoda zpoždění akci, až budete moct připojit k procesu.</span><span class="sxs-lookup"><span data-stu-id="1d822-154">Try adding calls to the <xref:System.Threading.Thread.Sleep%2A> method to delay action until you’re able to attach to the process.</span></span>  
  
 <span data-ttu-id="1d822-155">Zkuste změnit program na regulární konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="1d822-155">Try changing the program to a regular console application.</span></span> <span data-ttu-id="1d822-156">Chcete-li to provést, přepište `Main` metoda následujícím způsobem, takže ho můžete spustit jako služby systému Windows i jako konzolové aplikace, v závislosti na tom, jak je spuštěno.</span><span class="sxs-lookup"><span data-stu-id="1d822-156">To do this, rewrite the `Main` method as follows so it can run both as a Windows Service and as a console application, depending on how it's started.</span></span>  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a><span data-ttu-id="1d822-157">Postupy: spouštění služby systému Windows jako konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="1d822-157">How to: Run a Windows Service as a console application</span></span>  
  
1.  <span data-ttu-id="1d822-158">Přidání metody do vaší služby, která běží <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody:</span><span class="sxs-lookup"><span data-stu-id="1d822-158">Add a method to your service that runs the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods:</span></span>  
  
    ```  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2.  <span data-ttu-id="1d822-159">Přepisování `Main` metoda následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="1d822-159">Rewrite the `Main` method as follows:</span></span>  
  
    ```  
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
    ```  
  
3.  <span data-ttu-id="1d822-160">V **aplikace** s vlastnostmi projektu, nastavte **výstupní typ** k **konzolové aplikace**.</span><span class="sxs-lookup"><span data-stu-id="1d822-160">In the **Application** tab of the project's properties, set the **Output type** to **Console Application**.</span></span>  
  
4.  <span data-ttu-id="1d822-161">Zvolte **spustit ladění** (F5).</span><span class="sxs-lookup"><span data-stu-id="1d822-161">Choose **Start Debugging** (F5).</span></span>  
  
5.  <span data-ttu-id="1d822-162">Znovu spustit program jako služby systému Windows, nainstalujte ji a spusťte jej jako obvykle pro službu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="1d822-162">To run the program as a Windows Service again, install it and start it as usual for a Windows Service.</span></span> <span data-ttu-id="1d822-163">Není nutné provést tyto změny.</span><span class="sxs-lookup"><span data-stu-id="1d822-163">It's not necessary to reverse these changes.</span></span>  
  
 <span data-ttu-id="1d822-164">V některých případech, například pokud chcete ladit problém, který nastane pouze při spuštění systému budete muset použít ladicí program systému Windows.</span><span class="sxs-lookup"><span data-stu-id="1d822-164">In some cases, such as when you want to debug an issue that occurs only on system startup, you have to use the Windows debugger.</span></span> <span data-ttu-id="1d822-165">Nainstalujte [ladicích nástrojů pro systém Windows](http://msdn.microsoft.com/windows/hardware/hh852365) a zobrazit [ladění služby systému Windows](http://support.microsoft.com/kb/824344).</span><span class="sxs-lookup"><span data-stu-id="1d822-165">Install [Debugging Tools for Windows](http://msdn.microsoft.com/windows/hardware/hh852365) and see [How to debug Windows Services](http://support.microsoft.com/kb/824344).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d822-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d822-166">See Also</span></span>  
 [<span data-ttu-id="1d822-167">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="1d822-167">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="1d822-168">Postupy: Instalace a odinstalace služeb</span><span class="sxs-lookup"><span data-stu-id="1d822-168">How to: Install and Uninstall Services</span></span>](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [<span data-ttu-id="1d822-169">Postupy: Spuštění služeb</span><span class="sxs-lookup"><span data-stu-id="1d822-169">How to: Start Services</span></span>](../../../docs/framework/windows-services/how-to-start-services.md)  
 [<span data-ttu-id="1d822-170">Ladění služby</span><span class="sxs-lookup"><span data-stu-id="1d822-170">Debugging a Service</span></span>](http://msdn.microsoft.com/library/windows/desktop/ms682546.aspx)
