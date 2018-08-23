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
ms.openlocfilehash: 5de4c90361033df603bb63fbb365514d6bb5ea0c
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2018
ms.locfileid: "42752289"
---
# <a name="how-to-debug-windows-service-applications"></a>Postupy: Ladění aplikací spouštěných jako služby systému Windows
Služba musí být spuštěna v rámci kontextu správce řízení služeb spíše než v rámci sady Visual Studio. Z tohoto důvodu ladění služby není tak přímočaré jako ladění jiných typů aplikací Visual Studio. Chcete-li ladit službu, musíte spustit službu a potom připojit ladicí program k procesu, ve kterém je spuštěná. Potom můžete ladit svoji aplikaci pomocí všech standardních funkcí ladění sady Visual Studio.  
  
> [!CAUTION]
>  Byste neměli připojovat k procesu, pokud si nejste jisti, co proces je a nerozumíte jeho následkům připojením a pravděpodobně tento proces se ruší. Například pokud jste se připojit k procesu přihlašování do systému Windows a poté zastavte ladění, systém bude pozastaven, protože nemůže pracovat bez přihlašování do systému Windows.  
  
 Ladicí program lze připojit pouze ke spuštěné službě. Proces připojení přeruší aktuální fungování služby; není ve skutečnosti nezastaví ani nepozastaví zpracování služby. To znamená pokud vaše služba je spuštěna při zahájení ladění, je technicky vzato stále ve stavu spuštěno jako ladění, ale jeho zpracování bylo pozastaveno.  
  
 Po připojení k procesu, můžete nastavit zarážky a tyto použít k ladění kódu. Jakmile ukončíte dialogové okno, které slouží k připojení k procesu, jste skutečně v režimu ladění. Správce řízení služeb můžete použít pro spuštění, zastavení, pozastavení a pokračování ve službě a tím zasáhnutím zarážek, které jste nastavili. Tuto fiktivní službu můžete později odeberete po úspěšném ladění.  
  
 Tento článek se týká ladění služby, na kterém běží na místním počítači, ale můžete také ladit službách Windows, které jsou spuštěné ve vzdáleném počítači. Zobrazit [vzdálené ladění](/visualstudio/debugger/debug-installed-app-package).  
  
> [!NOTE]
>  Ladění <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda může být obtížné, protože správce řízení služeb má omezení 30 sekundách na všechny pokusy o spuštění služby. Další informace najdete v tématu [řešení potíží: ladění služeb Windows](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).  
  
> [!WARNING]
>  Chcete-li získat důležité informace pro ladění, ladicího programu sady Visual Studio potřebuje k vyhledání souborů symbolů pro binární soubory, které jsou právě laděny. Pokud ladíte službu, kterou jste vytvořili v sadě Visual Studio, jsou soubory symbolů (soubory PDB) ve stejné složce jako knihovna nebo spustitelný soubor a automaticky ladicí program je načte. Pokud ladíte služba, která se nepovedlo vytvořit, musí nejprve najít symboly pro službu a ujistěte se, že jsou dostupné pomocí ladicího programu. Zobrazit [zadání symbolu (.pdb) a zdrojové soubory](http://msdn.microsoft.com/library/1105e169-5272-4e7c-b3e7-cda1b7798a6b). Pokud ladíte systémový proces nebo chcete mít symboly pro systémová volání ve vašich službách, měli byste přidat servery symbolů společnosti Microsoft. Zobrazit [symboly ladění](/windows/desktop/DxTechArts/debugging-with-symbols).  
  
### <a name="to-debug-a-service"></a>Ladění služby  
  
1.  Vytvoření služby v konfiguraci ladění.  
  
2.  Nainstalujte svoji službu. Další informace najdete v tématu [postupy: instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
3.  Spusťte službu buď ze **správce řízení služeb**, **Průzkumníka serveru**, nebo z kódu. Další informace najdete v tématu [postupy: spuštění služby](../../../docs/framework/windows-services/how-to-start-services.md).  
  
4.  Spuštění sady Visual Studio s přihlašovacími údaji správce, takže se můžete připojit k systémovým procesům.  
  
5.  (Volitelné) Na řádku nabídek sady Visual Studio, zvolte **nástroje**, **možnosti**. V **možnosti** dialogového okna zvolte **ladění**, **symboly**, vyberte **Microsoft Symbol Servers** zaškrtněte políčko a klikněte na tlačítko **OK** tlačítko.  
  
6.  V panelu nabídky zvolte **připojit k procesu** z **ladění** nebo **nástroje** nabídky. (Klávesnice: Ctrl + Alt + P)  
  
     **Procesy** zobrazí se dialogové okno.  
  
7.  Vyberte **Zobrazit procesy všech uživatelů** zaškrtávací políčko.  
  
8.  V **procesy k dispozici** části, vyberte proces pro vaši službu a pak zvolte **připojit**.  
  
    > [!TIP]
    >  Proces bude mít stejný název jako spustitelný soubor pro vaši službu.  
  
     **Připojit k procesu** zobrazí se dialogové okno.  
  
9. Vyberte příslušné možnosti a klikněte na tlačítko **OK** zavřete dialogové okno.  
  
    > [!NOTE]
    >  Nyní jste v režimu ladění.  
  
10. Nastavte všechny zarážky, které chcete použít ve vašem kódu.  
  
11. Přístup ke správci řízení služeb a manipulaci s vaší služby, zastavení odesílání, pozastavení a pokračovat příkazy, aby narazily na zarážky. Další informace o spuštění Správce řízení služeb, naleznete v tématu [postupy: spuštění služby](../../../docs/framework/windows-services/how-to-start-services.md). Viz také [řešení potíží: ladění služeb Windows](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).  
  
## <a name="debugging-tips-for-windows-services"></a>Tipy pro ladění pro služby Windows  
 Připojení k procesu služby umožňuje ladit nejvíce, ale ne všechny kód za danou službu. Například protože služba již byla spuštěna, nelze ladit kód v služby <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody nebo kód v `Main` metodu, která slouží k zavedení služby tímto způsobem. Jedním ze způsobů, chcete-li toto omezení je vytvořit dočasnou druhou službu v aplikaci služby, která existuje pouze pro ladění. Můžete nainstalovat obě služby a potom spusťte tuto fiktivní službu k načtení procesu služby. Jakmile dočasná služba spustí proces, můžete použít **ladění** nabídky v sadě Visual Studio se připojit k procesu služby.  
  
 Pokuste se přidat volání <xref:System.Threading.Thread.Sleep%2A> metodu pro akci zpoždění, dokud se vám nedaří připojit k procesu.  
  
 Zkuste zobrazení změnit program regulární konzolové aplikace. Chcete-li to provést, přepište `Main` metodu následujícím způsobem, takže může běžet jako služba Windows i konzolovou aplikaci, v závislosti na tom, jak je spuštěno.  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a>Postupy: spuštění služby Windows jako konzolové aplikace  
  
1.  Přidejte metodu k službě, na kterém běží <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody:  
  
    ```csharp  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2.  Přepsání `Main` metodu následujícím způsobem:  
  
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
  
3.  V **aplikace** karta Vlastnosti projektu, nastavte **typ výstupu** k **konzolovou aplikaci**.  
  
4.  Zvolte **spustit ladění** (F5).  
  
5.  Znovu spustit program jako službu Windows, nainstalujte ji a spusťte jej jako obvykle pro službu Windows. Není nutné tyto změny vrátit.  
  
 V některých případech, například pokud chcete ladit problém, který nastane pouze při spuštění systému budete muset použít ladicí program Windows. Nainstalujte [ladění nástroje pro Windows](http://msdn.microsoft.com/windows/hardware/hh852365) uvidíme [jak ladit služby Windows](http://support.microsoft.com/kb/824344).  
  
## <a name="see-also"></a>Viz také  
 [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Postupy: Instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [Postupy: Spuštění služeb](../../../docs/framework/windows-services/how-to-start-services.md)  
 [Ladění služby](/windows/desktop/Services/debugging-a-service)
