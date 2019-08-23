---
title: Pokyny k hostování služby IIS
ms.date: 03/30/2017
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
ms.openlocfilehash: 226b47bfd90dc4cffb0a364a804016043cc25d02
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929113"
---
# <a name="internet-information-service-hosting-instructions"></a>Pokyny k hostování služby IIS
Chcete-li spustit ukázky, které jsou hostovány službou Internetová informační služba (IIS), je nutné zajistit, aby služba IIS byla správně nainstalována a spuštěna.  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a>Instalace IIS verze 7,5 v systému Windows Server 2008 R2  
  
1. Z **Správce serveru**vyberte **role.** V části **Souhrn rolí**klikněte na **Přidat role**.  
  
2. Kliknutím na tlačítko **Další** zobrazíte dialogové okno **Vybrat role serveru** .  
  
3. V seznamu **role** vyberte **aplikační server** a pak dvakrát klikněte na tlačítko **Další** , aby se zobrazil dialog **Vybrat služby rolí** pro roli aplikačního serveru.  
  
4. Zaškrtněte políčko **webový server (IIS)** . Pokud se zobrazí výzva k instalaci dalších služeb rolí a funkcí, klikněte na **Přidat požadované funkce**. Dvojím kliknutím na tlačítko **Další** zobrazíte dialogové okno **Vybrat služby rolí** pro roli webového serveru (IIS).  
  
5. Rozbalte položku **Nástroje pro správu**a poté rozbalte možnost **Kompatibilita správy služby IIS 6**. Vyberte **Nástroje pro skriptování služby IIS 6**. Pokud se zobrazí výzva k instalaci dalších služeb rolí a funkcí, klikněte na **Přidat požadované služby rolí**. Klikněte na **Další**.  
  
6. Pokud je souhrn výběrů správný, klikněte na **nainstalovat**.  
  
7. Po dokončení instalace klikněte na **Zavřít**.  
  
### <a name="to-install-iis-version-75-on-windows-7"></a>Instalace IIS verze 7,5 ve Windows 7  
  
1. Klikněte na tlačítko **Start**a poté na příkaz **Ovládací panely**.  
  
2. Otevřete skupinu **programy** .  
  
3. V části **programy a funkce**klikněte na **zapnout nebo vypnout funkce systému Windows**.  
  
4. Zobrazí se dialogové okno **řízení uživatelských účtů** . Klikněte na **Pokračovat**.  
  
5. Zobrazí se dialogové okno **funkce systému Windows** . Rozbalte položku s označením **Internetová informační služba**.  
  
6. Rozbalte položku označené **webové služby**.  
  
7. Rozbalte položku **funkce pro vývoj aplikací**s popisky.  
  
8. Ujistěte se, že jsou vybrané následující položky:  
  
    1. **Rozšiřitelnost rozhraní .NET**  
  
    2. **ASP.NET**  
  
    3. **Rozšíření ISAPI**  
  
    4. **Filtry ISAPI**  
  
9. V části položka označená jako **webové služby**rozbalte možnost **běžné funkce protokolu HTTP**.  
  
10. Ujistěte se, že je vybraný **statický obsah** .  
  
11. Pod položkou označený **World World Web Services**rozbalte **zabezpečení**.  
  
12. Ujistěte se, že je vybráno **ověřování systému Windows** .  
  
13. V adresáři **Internetová informační služba** rozbalte položku nástroje s popisem **webové správy**a pak vyberte možnost **Konzola pro správu služby IIS**.  
  
14. Rozbalte položku označená **Kompatibilita správy služby IIS 6**a pak vyberte **Nástroje pro skriptování služby IIS 6**.  
  
15. V adresáři **Internetová informační služba** rozbalte položku s názvem **Microsoft .NET Framework 3.5.1**a pak vyberte **Windows Communication Foundation aktivace protokolem HTTP**.  
  
16. Klikněte na **OK**.  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a>Instalace IIS verze 7,0 v systému Windows Server 2008  
  
1. Z **Správce serveru**vyberte **role**. V části **Souhrn rolí**klikněte na **Přidat role**.  
  
2. Kliknutím na tlačítko **Další** zobrazíte dialogové okno **Vybrat role serveru** .  
  
3. V seznamu **role** vyberte **aplikační server** a pak dvakrát klikněte na tlačítko **Další** , aby se zobrazil dialog **Vybrat služby rolí** pro roli aplikačního serveru.  
  
4. Vyberte zaškrtávací políčko **webový server (IIS)** . Pokud se zobrazí výzva k instalaci dalších služeb rolí a funkcí, klikněte na **Přidat požadované funkce**. Dvojím kliknutím na tlačítko **Další** zobrazíte dialogové okno **Vybrat služby rolí** pro roli webového serveru (IIS).  
  
5. Rozbalte položku **Nástroje pro správu**a poté rozbalte možnost **Kompatibilita správy služby IIS 6**. Vyberte **Nástroje pro skriptování služby IIS 6**. Pokud se zobrazí výzva k instalaci dalších služeb rolí a funkcí, klikněte na **Přidat požadované služby rolí**. Klikněte na **Další**.  
  
6. Pokud je souhrn výběrů správný, klikněte na **nainstalovat**.  
  
7. Po dokončení instalace klikněte na **Zavřít**.  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a>Instalace IIS verze 7,0 v systému Windows Vista  
  
1. Klikněte na tlačítko Start a poté na příkaz Ovládací panely.  
  
2. Vyberte skupinu **programy** .  
  
3. V části **programy a funkce**klikněte na **zapnout nebo vypnout funkce systému Windows**.  
  
4. Zobrazí se dialogové okno **řízení uživatelských účtů** . Klikněte na **Pokračovat**.  
  
5. Zobrazí se dialogové okno **funkce systému Windows** . Rozbalte položku s označením **Internetová informační služba**.  
  
6. Rozbalte položku označené **webové služby**.  
  
7. Rozbalte položku **funkce pro vývoj aplikací**s popisky.  
  
8. Ujistěte se, že jsou vybrané následující položky:  
  
    1. **Rozšiřitelnost rozhraní .NET**  
  
    2. **ASP.NET**  
  
    3. **Rozšíření ISAPI**  
  
    4. **Filtry ISAPI**  
  
9. Rozbalte položku označené **Nástroje webové správy**a pak vyberte možnost **Konzola pro správu služby IIS**.  
  
10. V části položka označená jako **webové služby**rozbalte možnost **běžné funkce protokolu HTTP**.  
  
11. Ujistěte se, že je vybraný **statický obsah** .  
  
12. Pod položkou označený **World World Web Services**rozbalte **zabezpečení**.  
  
13. Ujistěte se, že je vybráno **ověřování systému Windows** .  
  
14. Rozbalte položku označená **Kompatibilita správy služby IIS 6**a pak vyberte **Nástroje pro skriptování služby IIS 6**.  
  
15. Rozbalte položku s označením **Microsoft .NET Framework 3,0**a potom vyberte **Windows Communication Foundation aktivace protokolem HTTP**.  
  
16. Klikněte na **OK**.  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a>Instalace IIS verze 6,0 v systému Windows Server 2003  
  
1. V nabídce **spravovat server**klikněte na **Přidat nebo odebrat roli**a pak klikněte na **Další**.  
  
2. V seznamu **role serveru** vyberte **aplikační server (IIS, ASP.NET)** a pak klikněte na **Další**.  
  
3. Zaškrtněte políčko **povolit ASP.NET** a potom klikněte na tlačítko **Další**.  
  
4. Je-li Souhrn výběrů správný, klikněte na tlačítko Další.  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a>Instalace IIS verze 5,1 v systému Windows XP s nainstalovanou aktualizací Service Pack 2 a Service Pack 3  
  
1. V Ovládacích panelech klikněte na **Přidat nebo odebrat programy**.  
  
2. V dialogovém okně **Přidat nebo odebrat programy** klikněte na tlačítko **Přidat nebo odebrat součásti systému Windows**.  
  
3. V **Průvodci součástmi systému Windows**zaškrtněte políčko **Internetová informační služba (IIS)** a poté klikněte na tlačítko **Další**.  
  
4. Pokud se zobrazí dialogové okno **potřebné soubory** , vložte instalační disk operačního systému, vyhledejte složku i386 a klikněte na tlačítko **OK**.  
  
5. Po dokončení instalace klikněte na **Dokončit**.  
  
6. Zavřete dialogové okno **Přidat nebo odebrat programy** a pak zavřete **Ovládací panely**.  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a>Ověření instalace služby IIS a ASP.NET  
  
1. Uložte soubor HTML, který najdete na konci tohoto tématu, do kořenového adresáře \InetPub\wwwroot a pojmenujte ho default. aspx.  
  
2. Otevřete okno prohlížeče.  
  
3. Do `http://localhost/Default.aspx` pole Adresa zadejte a stiskněte klávesu ENTER.  
  
4. Měla by se zobrazit webová stránka s textem Hello World.  
  
> [!NOTE]
> Pokaždé, když instalujete novou verzi .NET Framework, je nutné znovu zaregistrovat modul Aspnet_isapi jako rozšíření webové služby pro službu IIS. Provedete to tak, `aspnet_regiis –I –enable` že vydáte příkaz.  
  
## <a name="sample-code"></a>Vzorový kód  
  
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
