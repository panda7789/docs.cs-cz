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
# <a name="how-to-debug-windows-service-applications"></a>Postupy: Ladění aplikací spouštěných jako služby systému Windows
Služba musí být spuštěna v kontextu správce řízení služeb, nikoli v rámci sady Visual Studio. Z tohoto důvodu ladění služby není tak jednoduché jako ladění jiných typů aplikací sady Visual Studio. Chcete-li ladit službu, je nutné spustit službu a potom připojit ladicí program k procesu, ve kterém je spuštěna. Pak můžete ladit aplikaci pomocí všech standardních funkcí ladění sady Visual Studio.  
  
> [!CAUTION]
> K procesu se nemusíte připojovat, Pokud nevíte, co proces je, a porozumět důsledkům připojení a případně usmrcení tohoto procesu. Například pokud se připojíte k procesu WinLogon a pak zastavíte ladění, systém se zastaví, protože nemůže pracovat bez procesu WinLogon.  
  
 Ladicí program lze připojit pouze ke spuštěné službě. Proces přílohy přerušuje aktuální fungování vaší služby. ve skutečnosti se nezastaví nebo nezastaví zpracování služby. To znamená, že pokud vaše služba běží při zahájení ladění, je při ladění stále technicky ve stavu spuštěno, ale jeho zpracování bylo pozastaveno.  
  
 Po připojení k procesu můžete nastavit zarážky a použít je k ladění kódu. Po zavření dialogového okna, které použijete k připojení k procesu, budete efektivně v režimu ladění. Správce řízení služeb můžete použít ke spuštění, zastavení, pozastavení a pokračování služby, čímž se zastaví zarážky, které jste nastavili. Po úspěšném ladění můžete tuto fiktivní službu odebrat později.  
  
 Tento článek popisuje ladění služby spuštěné v místním počítači, ale můžete také ladit služby systému Windows, které jsou spuštěny na vzdáleném počítači. Viz téma [vzdálené ladění](/visualstudio/debugger/debug-installed-app-package).  
  
> [!NOTE]
> <xref:System.ServiceProcess.ServiceBase.OnStart%2A> Ladění metody může být obtížné, protože správce řízení služeb má za následek limit 30 sekund pro všechny pokusy o spuštění služby. Další informace najdete v tématu [řešení potíží: Ladění služeb](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md)systému Windows.  
  
> [!WARNING]
> Chcete-li získat smysluplné informace pro ladění, ladicí program sady Visual Studio potřebuje najít soubory symbolů pro binární soubory, které jsou laděny. Pokud ladíte službu, kterou jste vytvořili v aplikaci Visual Studio, soubory symbolů (soubory. pdb) jsou ve stejné složce jako spustitelný soubor nebo knihovna a ladicí program je načte automaticky. Pokud ladíte službu, kterou jste nesestavili, měli byste nejprve vyhledat symboly pro službu a ověřit, zda je lze najít pomocí ladicího programu. Viz [určení symbolu (. pdb) a zdrojových souborů v ladicím programu sady Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger). Pokud ladíte systémový proces nebo chcete mít symboly pro systémová volání ve vašich službách, měli byste přidat servery symbolů společnosti Microsoft. Viz [symboly ladění](/windows/desktop/DxTechArts/debugging-with-symbols).  
  
### <a name="to-debug-a-service"></a>Ladění služby  
  
1. Sestavte službu v konfiguraci ladění.  
  
2. Nainstalujte svoji službu. Další informace najdete v tématu [jak: Nainstalujte a odinstalujte](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)služby.  
  
3. Spusťte službu, buď ze **správce řízení služeb**, **Průzkumník serveru**, nebo z kódu. Další informace najdete v tématu [jak: Spusťte služby](../../../docs/framework/windows-services/how-to-start-services.md).  
  
4. Spusťte Visual Studio s přihlašovacími údaji správce, abyste se mohli připojit k systémovým procesům.  
  
5. Volitelné Na řádku nabídek sady Visual Studio vyberte **nástroje**, **Možnosti**. V dialogovém okně **Možnosti** zvolte možnost **ladění**, **symboly**, zaškrtněte políčko **Microsoft Symbol Servers** a pak klikněte na tlačítko **OK** .  
  
6. Na panelu nabídek vyberte v nabídce **ladit** nebo **nástroje** možnost **připojit k procesu** . Kombinace CTRL + ALT + P)  
  
     Zobrazí se dialogové okno **procesy** .  
  
7. Zaškrtněte políčko **Zobrazit procesy všech uživatelů** .  
  
8. V části **Dostupné procesy** zvolte proces pro vaši službu a pak zvolte **připojit**.  
  
    > [!TIP]
    > Tento proces bude mít stejný název jako spustitelný soubor pro vaši službu.  
  
     **Připojit k procesu** zobrazí se dialogové okno.  
  
9. Zvolte příslušné možnosti a pak kliknutím na **tlačítko OK** zavřete dialogové okno.  
  
    > [!NOTE]
    > Nyní jste v režimu ladění.  
  
10. Nastavte všechny zarážky, které chcete použít ve svém kódu.  
  
11. Přístup ke Správci řízení služeb a manipulaci se službou, odesílání příkazů zastavit, pozastavit a pokračovat, aby byly zasaženy vaše zarážky. Další informace o spuštění Správce řízení služeb naleznete v tématu [How to: Spusťte služby](../../../docs/framework/windows-services/how-to-start-services.md). Přečtěte si [také téma řešení potíží: Ladění služeb](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md)systému Windows.  
  
## <a name="debugging-tips-for-windows-services"></a>Tipy pro ladění pro služby systému Windows  
 Připojení k procesu služby vám umožní ladit většinu, ale ne vše, kód pro tuto službu. Například vzhledem k tomu, že služba již byla spuštěna, nelze ladit kód v <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodě služby nebo kód `Main` v metodě, která slouží k načtení služby tímto způsobem. Jedním ze způsobů, jak toto omezení obejít, je vytvořit dočasnou druhou službu ve vaší aplikaci služby, která existuje jenom k podpoře ladění. Můžete nainstalovat obě služby a potom spustit tuto fiktivní službu pro načtení procesu služby. Jakmile dočasná služba spustí proces, můžete použít nabídku **ladit** v aplikaci Visual Studio k připojení k procesu služby.  
  
 Zkuste přidat volání do <xref:System.Threading.Thread.Sleep%2A> metody pro zpoždění akce, dokud se nebudete moct připojit k procesu.  
  
 Zkuste změnit program na běžnou konzolovou aplikaci. Pokud to chcete provést, přepište `Main` metodu následujícím způsobem, aby ji bylo možné spustit jak jako službu systému Windows, tak jako konzolovou aplikaci v závislosti na tom, jak je spuštěna.  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a>Postupy: Spuštění služby systému Windows jako konzolové aplikace  
  
1. Přidejte do služby metodu, která spouští <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody a: <xref:System.ServiceProcess.ServiceBase.OnStop%2A>  
  
    ```csharp  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2. Přepište `Main` metodu následujícím způsobem:  
  
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
  
3. Na kartě **aplikace** vlastností projektu nastavte **Typ výstupu** na **konzolovou aplikaci**.  
  
4. Vyberte možnost **Spustit ladění** (F5).  
  
5. Chcete-li program znovu spustit jako službu systému Windows, nainstalujte jej a spusťte jej obvyklým způsobem pro službu systému Windows. Nemusíte tyto změny měnit.  
  
 V některých případech, například pokud chcete ladit problém, ke kterému dochází pouze při spuštění systému, je nutné použít ladicí program systému Windows. [Stáhněte si sadu Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk) a podívejte se, [jak ladit služby systému Windows](https://support.microsoft.com/kb/824344).  
  
## <a name="see-also"></a>Viz také:

- [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Postupy: Instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)
- [Postupy: Spustit služby](../../../docs/framework/windows-services/how-to-start-services.md)
- [Ladění služby](/windows/desktop/Services/debugging-a-service)
