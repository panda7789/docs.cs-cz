---
title: Pokyny k hostování služby IIS
ms.date: 03/30/2017
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
ms.openlocfilehash: 5d315fa482e423461eab171a19746b6ea792aac5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="internet-information-service-hosting-instructions"></a>Pokyny k hostování služby IIS
Ke spuštění ukázky, které jsou hostované pomocí Internetové informační služby (IIS), musí se ujistěte, že služba IIS je správně nainstalován a běží.  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a>Instalace služby IIS verze 7.5 na Windows Server 2008 R2  
  
1.  Z **správce serveru**, vyberte **role.** V části **Souhrn rolí**, klikněte na tlačítko **přidat role**.  
  
2.  Klikněte na tlačítko **Další** zobrazíte **vybrat role serveru** dialogové okno.  
  
3.  Vyberte **aplikační Server** z **role** seznamu a pak klikněte na tlačítko **Další** dvakrát zobrazíte **vybrat služby rolí** dialogové okno pro Role aplikačního serveru.  
  
4.  Vyberte **webového serveru (IIS)** zaškrtávací políčko. Pokud se zobrazí výzva k instalaci další služby rolí a funkcí, klikněte na tlačítko **přidat požadované funkce**. Klikněte na tlačítko **Další** dvakrát zobrazíte **vybrat služby rolí** dialogové okno pro roli webového serveru (IIS).  
  
5.  Rozbalte položku **nástroje pro správu**a potom rozbalte **IIS 6 Management Compatibility**. Vyberte **IIS nástroje pro skriptování 6**. Pokud se zobrazí výzva k instalaci další služby rolí a funkcí, klikněte na tlačítko **přidat požadované služby rolí**. Klikněte na tlačítko **Další**.  
  
6.  Pokud souhrn výběr správné, klikněte na tlačítko **nainstalovat**.  
  
7.  Po dokončení instalace, klikněte na tlačítko **Zavřít**.  
  
### <a name="to-install-iis-version-75-on-windows-7"></a>Instalace služby IIS verze 7.5 na systému Windows 7  
  
1.  Klikněte na tlačítko **spustit**a potom klikněte na **ovládací panely**.  
  
2.  Otevřete **programy** skupiny.  
  
3.  V části **programy a funkce**, klikněte na tlačítko **zapnout nebo vypnout funkce systému Windows**.  
  
4.  **Řízení uživatelských účtů** se zobrazí dialogové okno. Klikněte na tlačítko **pokračovat**.  
  
5.  **Funkce systému Windows** se zobrazí dialogové okno. Rozbalte položky s popiskem **Internetová informační služba**.  
  
6.  Rozbalte položky s popiskem **webové služby**.  
  
7.  Rozbalte položky s popiskem **funkce pro vývoj aplikací**.  
  
8.  Zkontrolujte, zda že jsou vybrány následující položky:  
  
    1.  **Rozšiřitelnost rozhraní .NET**  
  
    2.  **ASP.NET**  
  
    3.  **Rozšíření ISAPI**  
  
    4.  **Filtry ISAPI**  
  
9. V části položka s názvem bez přípony **webové služby**, rozbalte položku **společné funkce protokolu Http**.  
  
10. Zajistěte, aby **statický obsah** je vybrána.  
  
11. V části položka s názvem bez přípony **webové služby**, rozbalte položku **zabezpečení**.  
  
12. Ujistěte se, že **ověřování systému Windows** je vybrána.  
  
13. V části **Internetová informační služba** adresáře, rozbalte položku s popiskem **nástroje webové správy**a potom vyberte **konzoly pro správu služby IIS**.  
  
14. Rozbalte položky s popiskem **IIS 6 Management Compatibility**a potom vyberte **nástroje pro skriptování na služby IIS 6**.  
  
15. V části **Internetová informační služba** adresáře, rozbalte položku s popiskem **rozhraní Microsoft .NET Framework 3.5.1**a potom vyberte **aktivace Windows Communication Foundation Http**.  
  
16. Click **OK**.  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a>Chcete-li nainstalovat službu IIS 7.0 v systému Windows Server 2008  
  
1.  Z **správce serveru**, vyberte **role**. V části **Souhrn rolí**, klikněte na tlačítko **přidat role**.  
  
2.  Klikněte na tlačítko **Další** zobrazíte **vybrat role serveru** dialogové okno.  
  
3.  Vyberte **aplikační Server** z **role** seznamu a pak klikněte na tlačítko **Další** dvakrát zobrazíte **vybrat služby rolí** dialogové okno pro Role aplikačního serveru.  
  
4.  Vyberte **webového serveru (IIS)** zaškrtávací políčko. Pokud se zobrazí výzva k instalaci další služby rolí a funkcí, klikněte na tlačítko **přidat požadované funkce**. Klikněte na tlačítko **Další** dvakrát zobrazíte **vybrat služby rolí** dialogové okno pro roli webového serveru (IIS).  
  
5.  Rozbalte položku **nástroje pro správu**a potom rozbalte **IIS 6 Management Compatibility**. Vyberte **IIS nástroje pro skriptování 6**. Pokud se zobrazí výzva k instalaci další služby rolí a funkcí, klikněte na tlačítko **přidat požadované služby rolí**. Klikněte na tlačítko **Další**.  
  
6.  Pokud souhrn výběr správné, klikněte na tlačítko **nainstalovat**.  
  
7.  Po dokončení instalace, klikněte na tlačítko **Zavřít**.  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a>Chcete-li nainstalovat službu IIS 7.0 v systému Windows Vista  
  
1.  Klikněte na tlačítko Start a pak klikněte na ovládacích panelech.  
  
2.  Vyberte **programy** skupiny.  
  
3.  V části **programy a funkce**, klikněte na tlačítko **zapnout nebo vypnout funkce systému Windows**.  
  
4.  **Řízení uživatelských účtů** se zobrazí dialogové okno. Klikněte na tlačítko **pokračovat**.  
  
5.  **Funkce systému Windows** se zobrazí dialogové okno. Rozbalte položky s popiskem **Internetová informační služba**.  
  
6.  Rozbalte položky s popiskem **webové služby**.  
  
7.  Rozbalte položky s popiskem **funkce pro vývoj aplikací**.  
  
8.  Zkontrolujte, zda že jsou vybrány následující položky:  
  
    1.  **Rozšiřitelnost rozhraní .NET**  
  
    2.  **ASP.NET**  
  
    3.  **Rozšíření ISAPI**  
  
    4.  **Filtry ISAPI**  
  
9. Rozbalte položky s popiskem **nástroje webové správy**a potom vyberte **konzoly pro správu služby IIS**.  
  
10. V části položka s názvem bez přípony **webové služby**, rozbalte položku **společné funkce protokolu Http**.  
  
11. Zajistěte, aby **statický obsah** je vybrána.  
  
12. V části položka s názvem bez přípony **webové služby**, rozbalte položku **zabezpečení**.  
  
13. Zajistěte, aby **ověřování systému Windows** je vybrána.  
  
14. Rozbalte položky s popiskem **IIS 6 Management Compatibility**a potom vyberte **nástroje pro skriptování na služby IIS 6**.  
  
15. Rozbalte položky s popiskem **rozhraní Microsoft .NET Framework 3.0**a potom vyberte **aktivace Windows Communication Foundation Http**.  
  
16. Klikněte na tlačítko**OK**.  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a>Instalace služby IIS verze 6.0 na Windows Server 2003  
  
1.  Z **Správa serveru**, klikněte na tlačítko **přidat nebo odebrat roli**a potom klikněte na **Další**.  
  
2.  Vyberte **aplikační server (IIS, ASP.NET)** z **Role serveru** seznamu a pak klikněte na tlačítko **Další**.  
  
3.  Vyberte **povolit technologii ASP.NET** zaškrtněte políčko a potom klikněte na **Další**.  
  
4.  Pokud souhrn výběr správné, klikněte na tlačítko Další.  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a>Chcete-li nainstalovat službu IIS verze 5.1 v systému Windows XP s aktualizací Service Pack 2 a aktualizací Service Pack 3 nainstalovány  
  
1.  V Ovládacích panelech klikněte na tlačítko **přidat nebo odebrat programy**.  
  
2.  V **přidat nebo odebrat programy** dialogové okno, klikněte na tlačítko **přidat nebo odebrat součásti systému Windows**.  
  
3.  V **Průvodce součástmi systému Windows**, vyberte **Internetové informační služby (IIS)** zaškrtněte políčko a potom klikněte na **Další**.  
  
4.  Pokud **soubory potřebné** se zobrazí dialogové okno, vložte disk instalace operačního systému, přejděte do složky i386 a pak klikněte na tlačítko **OK**.  
  
5.  Po dokončení instalace, klikněte na tlačítko **Dokončit**.  
  
6.  Zavřete **přidat nebo odebrat programy** dialogové okno a potom zavřete **ovládací panely**.  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a>Ověření instalace služby IIS a ASP.NET  
  
1.  Uložte soubor HTML nalezen na konci tohoto tématu v kořenovém adresáři \InetPub\wwwroot s názvem Default.aspx.  
  
2.  Otevřete okno prohlížeče.  
  
3.  Typ `http://localhost/Default.aspx` do pole Adresa a potom stiskněte klávesu ENTER.  
  
4.  Webové stránky s textem "Hello World" by se zobrazit.  
  
> [!NOTE]
>  Pokaždé, když instalujete novou verzi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], je nutné znovu zaregistrovat aspnet_isapi jako rozšíření webové služby pro službu IIS. Uděláte to tak, vydání `aspnet_regiis –I –enable` příkaz.  
  
## <a name="sample-code"></a>Ukázkový kód  
  
```xml  
<html>  
   <body>  
       <form >  
           <h3> Hello World  
           </h3>  
       </form>  
   </body>  
</html>  
```
