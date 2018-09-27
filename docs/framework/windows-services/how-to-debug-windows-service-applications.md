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
ms.openlocfilehash: 3f8dfff59acaa10fa99874dde2eb6eb6ed04e8fb
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47399934"
---
# <a name="how-to-debug-windows-service-applications"></a><span data-ttu-id="05b1c-102">Postupy: Ladění aplikací spouštěných jako služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="05b1c-102">How to: Debug Windows Service Applications</span></span>
<span data-ttu-id="05b1c-103">Služba musí být spuštěna v rámci kontextu správce řízení služeb spíše než v rámci sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="05b1c-103">A service must be run from within the context of the Services Control Manager rather than from within Visual Studio.</span></span> <span data-ttu-id="05b1c-104">Z tohoto důvodu ladění služby není tak přímočaré jako ladění jiných typů aplikací Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="05b1c-104">For this reason, debugging a service is not as straightforward as debugging other Visual Studio application types.</span></span> <span data-ttu-id="05b1c-105">Chcete-li ladit službu, musíte spustit službu a potom připojit ladicí program k procesu, ve kterém je spuštěná.</span><span class="sxs-lookup"><span data-stu-id="05b1c-105">To debug a service, you must start the service and then attach a debugger to the process in which it is running.</span></span> <span data-ttu-id="05b1c-106">Potom můžete ladit svoji aplikaci pomocí všech standardních funkcí ladění sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="05b1c-106">You can then debug your application by using all of the standard debugging functionality of Visual Studio.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="05b1c-107">Byste neměli připojovat k procesu, pokud si nejste jisti, co proces je a nerozumíte jeho následkům připojením a pravděpodobně tento proces se ruší.</span><span class="sxs-lookup"><span data-stu-id="05b1c-107">You should not attach to a process unless you know what the process is and understand the consequences of attaching to and possibly killing that process.</span></span> <span data-ttu-id="05b1c-108">Například pokud jste se připojit k procesu přihlašování do systému Windows a poté zastavte ladění, systém bude pozastaven, protože nemůže pracovat bez přihlašování do systému Windows.</span><span class="sxs-lookup"><span data-stu-id="05b1c-108">For example, if you attach to the WinLogon process and then stop debugging, the system will halt because it can’t operate without WinLogon.</span></span>  
  
 <span data-ttu-id="05b1c-109">Ladicí program lze připojit pouze ke spuštěné službě.</span><span class="sxs-lookup"><span data-stu-id="05b1c-109">You can attach the debugger only to a running service.</span></span> <span data-ttu-id="05b1c-110">Proces připojení přeruší aktuální fungování služby; není ve skutečnosti nezastaví ani nepozastaví zpracování služby.</span><span class="sxs-lookup"><span data-stu-id="05b1c-110">The attachment process interrupts the current functioning of your service; it doesn’t actually stop or pause the service's processing.</span></span> <span data-ttu-id="05b1c-111">To znamená pokud vaše služba je spuštěna při zahájení ladění, je technicky vzato stále ve stavu spuštěno jako ladění, ale jeho zpracování bylo pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="05b1c-111">That is, if your service is running when you begin debugging, it is still technically in the Started state as you debug it, but its processing has been suspended.</span></span>  
  
 <span data-ttu-id="05b1c-112">Po připojení k procesu, můžete nastavit zarážky a tyto použít k ladění kódu.</span><span class="sxs-lookup"><span data-stu-id="05b1c-112">After attaching to the process, you can set breakpoints and use these to debug your code.</span></span> <span data-ttu-id="05b1c-113">Jakmile ukončíte dialogové okno, které slouží k připojení k procesu, jste skutečně v režimu ladění.</span><span class="sxs-lookup"><span data-stu-id="05b1c-113">Once you exit the dialog box you use to attach to the process, you are effectively in debug mode.</span></span> <span data-ttu-id="05b1c-114">Správce řízení služeb můžete použít pro spuštění, zastavení, pozastavení a pokračování ve službě a tím zasáhnutím zarážek, které jste nastavili.</span><span class="sxs-lookup"><span data-stu-id="05b1c-114">You can use the Services Control Manager to start, stop, pause and continue your service, thus hitting the breakpoints you've set.</span></span> <span data-ttu-id="05b1c-115">Tuto fiktivní službu můžete později odeberete po úspěšném ladění.</span><span class="sxs-lookup"><span data-stu-id="05b1c-115">You can later remove this dummy service after debugging is successful.</span></span>  
  
 <span data-ttu-id="05b1c-116">Tento článek se týká ladění služby, na kterém běží na místním počítači, ale můžete také ladit službách Windows, které jsou spuštěné ve vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="05b1c-116">This article covers debugging a service that's running on the local computer, but you can also debug Windows Services that are running on a remote computer.</span></span> <span data-ttu-id="05b1c-117">Zobrazit [vzdálené ladění](/visualstudio/debugger/debug-installed-app-package).</span><span class="sxs-lookup"><span data-stu-id="05b1c-117">See [Remote Debugging](/visualstudio/debugger/debug-installed-app-package).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05b1c-118">Ladění <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda může být obtížné, protože správce řízení služeb má omezení 30 sekundách na všechny pokusy o spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="05b1c-118">Debugging the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method can be difficult because the Services Control Manager imposes a 30-second limit on all attempts to start a service.</span></span> <span data-ttu-id="05b1c-119">Další informace najdete v tématu [řešení potíží: ladění služeb Windows](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span><span class="sxs-lookup"><span data-stu-id="05b1c-119">For more information, see [Troubleshooting: Debugging Windows Services](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="05b1c-120">Chcete-li získat důležité informace pro ladění, ladicího programu sady Visual Studio potřebuje k vyhledání souborů symbolů pro binární soubory, které jsou právě laděny.</span><span class="sxs-lookup"><span data-stu-id="05b1c-120">To get meaningful information for debugging, the Visual Studio debugger needs to find symbol files for the binaries that are being debugged.</span></span> <span data-ttu-id="05b1c-121">Pokud ladíte službu, kterou jste vytvořili v sadě Visual Studio, jsou soubory symbolů (soubory PDB) ve stejné složce jako knihovna nebo spustitelný soubor a automaticky ladicí program je načte.</span><span class="sxs-lookup"><span data-stu-id="05b1c-121">If you are debugging a service that you built in Visual Studio, the symbol files (.pdb files) are in the same folder as the executable or library, and the debugger loads them automatically.</span></span> <span data-ttu-id="05b1c-122">Pokud ladíte služba, která se nepovedlo vytvořit, musí nejprve najít symboly pro službu a ujistěte se, že jsou dostupné pomocí ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="05b1c-122">If you are debugging a service that you didn't build, you should first find symbols for the service and make sure they can be found by the debugger.</span></span> <span data-ttu-id="05b1c-123">Zobrazit [zadání symbolu (.pdb) a zdrojové soubory](https://msdn.microsoft.com/library/1105e169-5272-4e7c-b3e7-cda1b7798a6b).</span><span class="sxs-lookup"><span data-stu-id="05b1c-123">See [Specify Symbol (.pdb) and Source Files](https://msdn.microsoft.com/library/1105e169-5272-4e7c-b3e7-cda1b7798a6b).</span></span> <span data-ttu-id="05b1c-124">Pokud ladíte systémový proces nebo chcete mít symboly pro systémová volání ve vašich službách, měli byste přidat servery symbolů společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="05b1c-124">If you're debugging a system process or want to have symbols for system calls in your services, you should add the Microsoft Symbol Servers.</span></span> <span data-ttu-id="05b1c-125">Zobrazit [symboly ladění](/windows/desktop/DxTechArts/debugging-with-symbols).</span><span class="sxs-lookup"><span data-stu-id="05b1c-125">See [Debugging Symbols](/windows/desktop/DxTechArts/debugging-with-symbols).</span></span>  
  
### <a name="to-debug-a-service"></a><span data-ttu-id="05b1c-126">Ladění služby</span><span class="sxs-lookup"><span data-stu-id="05b1c-126">To debug a service</span></span>  
  
1.  <span data-ttu-id="05b1c-127">Vytvoření služby v konfiguraci ladění.</span><span class="sxs-lookup"><span data-stu-id="05b1c-127">Build your service in the Debug configuration.</span></span>  
  
2.  <span data-ttu-id="05b1c-128">Nainstalujte svoji službu.</span><span class="sxs-lookup"><span data-stu-id="05b1c-128">Install your service.</span></span> <span data-ttu-id="05b1c-129">Další informace najdete v tématu [postupy: instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="05b1c-129">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
3.  <span data-ttu-id="05b1c-130">Spusťte službu buď ze **správce řízení služeb**, **Průzkumníka serveru**, nebo z kódu.</span><span class="sxs-lookup"><span data-stu-id="05b1c-130">Start your service, either from **Services Control Manager**, **Server Explorer**, or from code.</span></span> <span data-ttu-id="05b1c-131">Další informace najdete v tématu [postupy: spuštění služby](../../../docs/framework/windows-services/how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="05b1c-131">For more information, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span>  
  
4.  <span data-ttu-id="05b1c-132">Spuštění sady Visual Studio s přihlašovacími údaji správce, takže se můžete připojit k systémovým procesům.</span><span class="sxs-lookup"><span data-stu-id="05b1c-132">Start Visual Studio with administrative credentials so you can attach to system processes.</span></span>  
  
5.  <span data-ttu-id="05b1c-133">(Volitelné) Na řádku nabídek sady Visual Studio, zvolte **nástroje**, **možnosti**.</span><span class="sxs-lookup"><span data-stu-id="05b1c-133">(Optional) On the Visual Studio menu bar, choose **Tools**, **Options**.</span></span> <span data-ttu-id="05b1c-134">V **možnosti** dialogového okna zvolte **ladění**, **symboly**, vyberte **Microsoft Symbol Servers** zaškrtněte políčko a klikněte na tlačítko **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="05b1c-134">In the **Options** dialog box, choose **Debugging**, **Symbols**, select the **Microsoft Symbol Servers** check box, and then choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="05b1c-135">V panelu nabídky zvolte **připojit k procesu** z **ladění** nebo **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="05b1c-135">On the menu bar, choose **Attach to Process** from the **Debug** or **Tools** menu.</span></span> <span data-ttu-id="05b1c-136">(Klávesnice: Ctrl + Alt + P)</span><span class="sxs-lookup"><span data-stu-id="05b1c-136">(Keyboard: Ctrl+Alt+P)</span></span>  
  
     <span data-ttu-id="05b1c-137">**Procesy** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="05b1c-137">The **Processes** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="05b1c-138">Vyberte **Zobrazit procesy všech uživatelů** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="05b1c-138">Select the **Show processes from all users** check box.</span></span>  
  
8.  <span data-ttu-id="05b1c-139">V **procesy k dispozici** části, vyberte proces pro vaši službu a pak zvolte **připojit**.</span><span class="sxs-lookup"><span data-stu-id="05b1c-139">In the **Available Processes** section, choose the process for your service, and then choose **Attach**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="05b1c-140">Proces bude mít stejný název jako spustitelný soubor pro vaši službu.</span><span class="sxs-lookup"><span data-stu-id="05b1c-140">The process will have the same name as the executable file for your service.</span></span>  
  
     <span data-ttu-id="05b1c-141">**Připojit k procesu** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="05b1c-141">The **Attach to Process** dialog box appears.</span></span>  
  
9. <span data-ttu-id="05b1c-142">Vyberte příslušné možnosti a klikněte na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="05b1c-142">Choose the appropriate options, and then choose **OK** to close the dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="05b1c-143">Nyní jste v režimu ladění.</span><span class="sxs-lookup"><span data-stu-id="05b1c-143">You are now in debug mode.</span></span>  
  
10. <span data-ttu-id="05b1c-144">Nastavte všechny zarážky, které chcete použít ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="05b1c-144">Set any breakpoints you want to use in your code.</span></span>  
  
11. <span data-ttu-id="05b1c-145">Přístup ke správci řízení služeb a manipulaci s vaší služby, zastavení odesílání, pozastavení a pokračovat příkazy, aby narazily na zarážky.</span><span class="sxs-lookup"><span data-stu-id="05b1c-145">Access the Services Control Manager and manipulate your service, sending stop, pause, and continue commands to hit your breakpoints.</span></span> <span data-ttu-id="05b1c-146">Další informace o spuštění Správce řízení služeb, naleznete v tématu [postupy: spuštění služby](../../../docs/framework/windows-services/how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="05b1c-146">For more information about running the Services Control Manager, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span> <span data-ttu-id="05b1c-147">Viz také [řešení potíží: ladění služeb Windows](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span><span class="sxs-lookup"><span data-stu-id="05b1c-147">Also, see [Troubleshooting: Debugging Windows Services](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span></span>  
  
## <a name="debugging-tips-for-windows-services"></a><span data-ttu-id="05b1c-148">Tipy pro ladění pro služby Windows</span><span class="sxs-lookup"><span data-stu-id="05b1c-148">Debugging Tips for Windows Services</span></span>  
 <span data-ttu-id="05b1c-149">Připojení k procesu služby umožňuje ladit nejvíce, ale ne všechny kód za danou službu.</span><span class="sxs-lookup"><span data-stu-id="05b1c-149">Attaching to the service's process allows you to debug most, but not all, the code for that service.</span></span> <span data-ttu-id="05b1c-150">Například protože služba již byla spuštěna, nelze ladit kód v služby <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody nebo kód v `Main` metodu, která slouží k zavedení služby tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="05b1c-150">For example, because the service has already been started, you cannot debug the code in the service's <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method or the code in the `Main` method that is used to load the service this way.</span></span> <span data-ttu-id="05b1c-151">Jedním ze způsobů, chcete-li toto omezení je vytvořit dočasnou druhou službu v aplikaci služby, která existuje pouze pro ladění.</span><span class="sxs-lookup"><span data-stu-id="05b1c-151">One way to work around this limitation is to create a temporary second service in your service application that exists only to aid in debugging.</span></span> <span data-ttu-id="05b1c-152">Můžete nainstalovat obě služby a potom spusťte tuto fiktivní službu k načtení procesu služby.</span><span class="sxs-lookup"><span data-stu-id="05b1c-152">You can install both services, and then start this dummy service to load the service process.</span></span> <span data-ttu-id="05b1c-153">Jakmile dočasná služba spustí proces, můžete použít **ladění** nabídky v sadě Visual Studio se připojit k procesu služby.</span><span class="sxs-lookup"><span data-stu-id="05b1c-153">Once the temporary service has started the process, you can use the **Debug** menu in Visual Studio to attach to the service process.</span></span>  
  
 <span data-ttu-id="05b1c-154">Pokuste se přidat volání <xref:System.Threading.Thread.Sleep%2A> metodu pro akci zpoždění, dokud se vám nedaří připojit k procesu.</span><span class="sxs-lookup"><span data-stu-id="05b1c-154">Try adding calls to the <xref:System.Threading.Thread.Sleep%2A> method to delay action until you’re able to attach to the process.</span></span>  
  
 <span data-ttu-id="05b1c-155">Zkuste zobrazení změnit program regulární konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="05b1c-155">Try changing the program to a regular console application.</span></span> <span data-ttu-id="05b1c-156">Chcete-li to provést, přepište `Main` metodu následujícím způsobem, takže může běžet jako služba Windows i konzolovou aplikaci, v závislosti na tom, jak je spuštěno.</span><span class="sxs-lookup"><span data-stu-id="05b1c-156">To do this, rewrite the `Main` method as follows so it can run both as a Windows Service and as a console application, depending on how it's started.</span></span>  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a><span data-ttu-id="05b1c-157">Postupy: spuštění služby Windows jako konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="05b1c-157">How to: Run a Windows Service as a console application</span></span>  
  
1.  <span data-ttu-id="05b1c-158">Přidejte metodu k službě, na kterém běží <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody:</span><span class="sxs-lookup"><span data-stu-id="05b1c-158">Add a method to your service that runs the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods:</span></span>  
  
    ```csharp  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2.  <span data-ttu-id="05b1c-159">Přepsání `Main` metodu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="05b1c-159">Rewrite the `Main` method as follows:</span></span>  
  
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
  
3.  <span data-ttu-id="05b1c-160">V **aplikace** karta Vlastnosti projektu, nastavte **typ výstupu** k **konzolovou aplikaci**.</span><span class="sxs-lookup"><span data-stu-id="05b1c-160">In the **Application** tab of the project's properties, set the **Output type** to **Console Application**.</span></span>  
  
4.  <span data-ttu-id="05b1c-161">Zvolte **spustit ladění** (F5).</span><span class="sxs-lookup"><span data-stu-id="05b1c-161">Choose **Start Debugging** (F5).</span></span>  
  
5.  <span data-ttu-id="05b1c-162">Znovu spustit program jako službu Windows, nainstalujte ji a spusťte jej jako obvykle pro službu Windows.</span><span class="sxs-lookup"><span data-stu-id="05b1c-162">To run the program as a Windows Service again, install it and start it as usual for a Windows Service.</span></span> <span data-ttu-id="05b1c-163">Není nutné tyto změny vrátit.</span><span class="sxs-lookup"><span data-stu-id="05b1c-163">It's not necessary to reverse these changes.</span></span>  
  
 <span data-ttu-id="05b1c-164">V některých případech, například pokud chcete ladit problém, který nastane pouze při spuštění systému budete muset použít ladicí program Windows.</span><span class="sxs-lookup"><span data-stu-id="05b1c-164">In some cases, such as when you want to debug an issue that occurs only on system startup, you have to use the Windows debugger.</span></span> <span data-ttu-id="05b1c-165">Nainstalujte [ladění nástroje pro Windows](https://msdn.microsoft.com/windows/hardware/hh852365) uvidíme [jak ladit služby Windows](https://support.microsoft.com/kb/824344).</span><span class="sxs-lookup"><span data-stu-id="05b1c-165">Install [Debugging Tools for Windows](https://msdn.microsoft.com/windows/hardware/hh852365) and see [How to debug Windows Services](https://support.microsoft.com/kb/824344).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05b1c-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="05b1c-166">See Also</span></span>  
 [<span data-ttu-id="05b1c-167">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="05b1c-167">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="05b1c-168">Postupy: Instalace a odinstalace služeb</span><span class="sxs-lookup"><span data-stu-id="05b1c-168">How to: Install and Uninstall Services</span></span>](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [<span data-ttu-id="05b1c-169">Postupy: Spuštění služeb</span><span class="sxs-lookup"><span data-stu-id="05b1c-169">How to: Start Services</span></span>](../../../docs/framework/windows-services/how-to-start-services.md)  
 [<span data-ttu-id="05b1c-170">Ladění služby</span><span class="sxs-lookup"><span data-stu-id="05b1c-170">Debugging a Service</span></span>](/windows/desktop/Services/debugging-a-service)
