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
# <a name="how-to-debug-windows-service-applications"></a>Postupy: Ladění aplikací spouštěných jako služby systému Windows
Služba musí být spuštěn v kontextu správci řízení služeb a nikoli z v sadě Visual Studio. Z tohoto důvodu ladění služby není stejně jednoduché jako ladění jinými typy aplikací Visual Studio. K ladění služby, musíte spustit službu a pak připojit ladicí program k procesu, ve kterém je spuštěna. Potom můžete ladění aplikace s použitím všechny standardní ladění funkce sady Visual Studio.  
  
> [!CAUTION]
>  Nesmí se připojit k procesu, ledaže byste věděli, co proces a chápu důsledky se připojuje k a které by mohly mít ukončení tohoto procesu. Například pokud připojit k procesu přihlášení do systému Windows a potom zastavte ladění, systém se zastaví protože nemůže pracovat bez přihlášení do systému Windows.  
  
 Ladicí program můžete připojit pouze k spuštěnou službu. Proces přílohy přerušení aktuální fungování služby; není ve skutečnosti zastavení nebo pozastavení služby zpracování. To znamená pokud je vaše služba spuštěná, abyste před zahájením ladění, je stále technicky ve stavu spuštěno jako ladění ji, ale jeho zpracování bylo pozastaveno.  
  
 Po připojení k procesu, můžete nastavit zarážky a tyto slouží k ladění kódu. Po ukončení dialogu, který používáte pro připojení k procesu jste efektivně v režimu ladění. Správci řízení služeb můžete použít k spuštění, zastavení, pozastavení a pokračování služby, proto zarážek, které jste nastavili. Později můžete odebrat tuto službu fiktivní po úspěšné ladění.  
  
 Tento článek se zabývá ladění služba, která běží na místním počítači, ale můžete také ladění služby systému Windows, který běží na vzdáleném počítači. V tématu [vzdálené ladění](/visualstudio/debugger/debug-installed-app-package).  
  
> [!NOTE]
>  Ladění <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda může být složité, protože správci řízení služeb ukládá limitu 30 sekund na všechny pokusy o spuštění služby. Další informace najdete v tématu [řešení potíží: ladění služby systému Windows](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).  
  
> [!WARNING]
>  Získat důležité informace pro ladění, je potřeba najít soubory symbolů pro binární soubory, které se právě ladí ladicího programu sady Visual Studio. Pokud ladíte služba, která jste vytvořili v sadě Visual Studio, soubory symbolů (soubory PDB) jsou ve stejné složce jako spustitelný soubor nebo knihovny a ladicí program načítá je automaticky. Pokud ladíte služba, která nebyla sestavení, doporučujeme nejprve najít symboly pro službu a ujistěte se, že najdete pomocí ladicího programu. V tématu [zadání symbolu (.pdb) a zdrojových souborů](http://msdn.microsoft.com/library/1105e169-5272-4e7c-b3e7-cda1b7798a6b). Pokud ladíte systémový proces nebo chcete mít symboly pro systémová volání v službách, měli byste přidat servery Microsoft symbolů. V tématu [symboly ladění](http://msdn.microsoft.com/windows/desktop/ee416588.aspx).  
  
### <a name="to-debug-a-service"></a>K ladění služby  
  
1.  Vytvoření služby v konfiguraci ladění.  
  
2.  Instalace služby. Další informace najdete v tématu [postupy: instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
3.  Spuštění služby, buď z **správci řízení služeb**, **Průzkumníka serveru**, nebo z kódu. Další informace najdete v tématu [postupy: spuštění služby](../../../docs/framework/windows-services/how-to-start-services.md).  
  
4.  Spuštění sady Visual Studio s přihlašovacími údaji správce, takže se můžete připojit k systémovým procesům.  
  
5.  (Volitelné) Na panelu nabídek Visual Studio zvolte **nástroje**, **možnosti**. V **možnosti** dialogovém okně vyberte **ladění**, **symboly**, vyberte **servery symbolů Microsoft** zaškrtněte políčko a potom vyberte **OK** tlačítko.  
  
6.  Na řádku nabídek zvolte **připojit k procesu** z **ladění** nebo **nástroje** nabídky. (Klávesové: Ctrl + Alt + P)  
  
     **Procesy** zobrazí se dialogové okno.  
  
7.  Vyberte **Zobrazit procesy od všech uživatelů** zaškrtávací políčko.  
  
8.  V **dostupné procesy** část, zvolte proces pro vaši službu a pak zvolte **Attach**.  
  
    > [!TIP]
    >  Proces bude mít stejný název jako spustitelný soubor pro vaši službu.  
  
     **Připojit k procesu** zobrazí se dialogové okno.  
  
9. Vyberte požadované možnosti a pak zvolte **OK** zavřete dialogové okno.  
  
    > [!NOTE]
    >  Nyní jste v režimu ladění.  
  
10. Nastavte všechny zarážky, které chcete použít v kódu.  
  
11. Přístup k správci řízení služeb a manipulaci s vaší služby, odesílání zastavení, pozastavení a pokračovat příkazy a stiskněte váš zarážky. Další informace o spouštění správci řízení služeb najdete v tématu [postupy: spuštění služby](../../../docs/framework/windows-services/how-to-start-services.md). Další informace naleznete v [řešení potíží: ladění služby systému Windows](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).  
  
## <a name="debugging-tips-for-windows-services"></a>Ladění tipy pro služby systému Windows  
 Připojení k procesu služby umožňuje ladit nejvíce, ale ne všechny kód pro tuto službu. Například, protože služba již byla spuštěna, nelze ladění kódu v rámci služby <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda nebo kód `Main` metoda, která se používá k načtení služby tímto způsobem. Jeden způsob, jak toto omezení obejít je vytvoření dočasné druhý služby v aplikaci služby, které existuje jenom k ladění. Můžete nainstalovat obě služby a spusťte tuto službu fiktivní načíst proces služby. Až službu dočasné zahájil proces, můžete pomocí **ladění** nabídky v sadě Visual Studio pro připojení k procesu služby.  
  
 Zkuste přidat volání <xref:System.Threading.Thread.Sleep%2A> metoda zpoždění akci, až budete moct připojit k procesu.  
  
 Zkuste změnit program na regulární konzolové aplikace. Chcete-li to provést, přepište `Main` metoda následujícím způsobem, takže ho můžete spustit jako služby systému Windows i jako konzolové aplikace, v závislosti na tom, jak je spuštěno.  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a>Postupy: spouštění služby systému Windows jako konzolové aplikace  
  
1.  Přidání metody do vaší služby, která běží <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody:  
  
    ```  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2.  Přepisování `Main` metoda následujícím způsobem:  
  
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
  
3.  V **aplikace** s vlastnostmi projektu, nastavte **výstupní typ** k **konzolové aplikace**.  
  
4.  Zvolte **spustit ladění** (F5).  
  
5.  Znovu spustit program jako služby systému Windows, nainstalujte ji a spusťte jej jako obvykle pro službu systému Windows. Není nutné provést tyto změny.  
  
 V některých případech, například pokud chcete ladit problém, který nastane pouze při spuštění systému budete muset použít ladicí program systému Windows. Nainstalujte [ladicích nástrojů pro systém Windows](http://msdn.microsoft.com/windows/hardware/hh852365) a zobrazit [ladění služby systému Windows](http://support.microsoft.com/kb/824344).  
  
## <a name="see-also"></a>Viz také  
 [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Postupy: Instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [Postupy: Spuštění služeb](../../../docs/framework/windows-services/how-to-start-services.md)  
 [Ladění služby](http://msdn.microsoft.com/library/windows/desktop/ms682546.aspx)
