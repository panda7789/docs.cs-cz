---
title: Pokyny k hostování služby IIS
ms.date: 03/30/2017
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
ms.openlocfilehash: a537f37132e5014901d415cd96bc72a55ae0b750
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64600253"
---
# <a name="internet-information-service-hosting-instructions"></a>Pokyny k hostování služby IIS
Ke spuštění ukázky, které jsou hostované v Internetové informační služby (IIS), musí se ujistěte, že IIS je správně nainstalován a běží.  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a>Chcete-li nainstalovat službu IIS verze 7.5 na Windows Server 2008 R2  
  
1. Z **správce serveru**vyberte **role.** V části **Souhrn rolí**, klikněte na tlačítko **přidat role**.  
  
2. Klikněte na tlačítko **Další** zobrazíte **vybrat role serveru** dialogového okna.  
  
3. Vyberte **aplikační Server** z **role** seznamu a potom klikněte na tlačítko **Další** dvakrát zobrazíte **vybrat služby rolí** dialogové okno pro Role aplikačního serveru.  
  
4. Vyberte **webového serveru (IIS)** zaškrtávací políčko. Pokud se zobrazí výzva k instalaci služeb rolí a funkcí, klikněte na tlačítko **přidat požadované funkce**. Klikněte na tlačítko **Další** dvakrát zobrazíte **vybrat služby rolí** dialogové okno pro roli webového serveru (IIS).  
  
5. Rozbalte **nástroje pro správu**a potom rozbalte **IIS 6 Management Compatibility**. Vyberte **IIS 6 Scripting Tools**. Pokud se zobrazí výzva k instalaci služeb rolí a funkcí, klikněte na tlačítko **přidat požadované služby rolí**. Klikněte na **Další**.  
  
6. Pokud správnost souhrn výběry, klikněte na tlačítko **nainstalovat**.  
  
7. Po dokončení instalace klikněte na tlačítko **Zavřít**.  
  
### <a name="to-install-iis-version-75-on-windows-7"></a>Chcete-li nainstalovat službu IIS verze 7.5 na Windows 7  
  
1. Klikněte na tlačítko **Start**a potom klikněte na tlačítko **ovládací panely**.  
  
2. Otevřít **programy** skupiny.  
  
3. V části **programy a funkce**, klikněte na tlačítko **zapnout nebo vypnout funkce Windows**.  
  
4. **Řízení uživatelských účtů** se zobrazí dialogové okno. Klikněte na **Pokračovat**.  
  
5. **Funkce Windows** se zobrazí dialogové okno. Rozbalte položky označené **Internetová informační služba**.  
  
6. Rozbalte položky označené **webové služby**.  
  
7. Rozbalte položky označené **funkce pro vývoj aplikací**.  
  
8. Ujistěte se, zda že jsou vybrány následující položky:  
  
    1. **Rozšiřitelnost rozhraní .NET**  
  
    2. **ASP.NET**  
  
    3. **Rozšíření ISAPI**  
  
    4. **Filtry ISAPI**  
  
9. V části položky označené **webové služby**, rozbalte **společné funkce protokolu Http**.  
  
10. Ujistěte se, že **statický obsah** zaškrtnuto.  
  
11. V části položky označené **webové služby**, rozbalte **zabezpečení**.  
  
12. Ujistěte se, že **ověřování Windows** zaškrtnuto.  
  
13. V části **Internetová informační služba** adresáře, rozbalte položku s popiskem **nástroje webové správy**a pak vyberte **Konzola pro správu služby IIS**.  
  
14. Rozbalte položky označené **IIS 6 Management Compatibility**a pak vyberte **IIS 6 Scripting Tools**.  
  
15. V části **Internetová informační služba** adresáře, rozbalte položku s popiskem **rozhraní Microsoft .NET Framework 3.5.1**a pak vyberte **aktivace Windows Communication Foundation Http**.  
  
16. Klikněte na **OK**.  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a>Chcete-li nainstalovat službu IIS verze 7.0 ve Windows serveru 2008  
  
1. Z **správce serveru**vyberte **role**. V části **Souhrn rolí**, klikněte na tlačítko **přidat role**.  
  
2. Klikněte na tlačítko **Další** zobrazíte **vybrat role serveru** dialogového okna.  
  
3. Vyberte **aplikační Server** z **role** seznamu a potom klikněte na tlačítko **Další** dvakrát zobrazíte **vybrat služby rolí** dialogové okno pro Role aplikačního serveru.  
  
4. Vyberte **webového serveru (IIS)** zaškrtávací políčko. Pokud se zobrazí výzva k instalaci služeb rolí a funkcí, klikněte na tlačítko **přidat požadované funkce**. Klikněte na tlačítko **Další** dvakrát zobrazíte **vybrat služby rolí** dialogové okno pro roli webového serveru (IIS).  
  
5. Rozbalte **nástroje pro správu**a potom rozbalte **IIS 6 Management Compatibility**. Vyberte **IIS 6 Scripting Tools**. Pokud se zobrazí výzva k instalaci služeb rolí a funkcí, klikněte na tlačítko **přidat požadované služby rolí**. Klikněte na **Další**.  
  
6. Pokud správnost souhrn výběry, klikněte na tlačítko **nainstalovat**.  
  
7. Po dokončení instalace klikněte na tlačítko **Zavřít**.  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a>Chcete-li nainstalovat službu IIS verze 7.0 v systému Windows Vista  
  
1. Klikněte na tlačítko Start a potom klikněte na ovládacích panelech.  
  
2. Vyberte **programy** skupiny.  
  
3. V části **programy a funkce**, klikněte na tlačítko **zapnout nebo vypnout funkce Windows**.  
  
4. **Řízení uživatelských účtů** se zobrazí dialogové okno. Klikněte na **Pokračovat**.  
  
5. **Funkce Windows** se zobrazí dialogové okno. Rozbalte položky označené **Internetová informační služba**.  
  
6. Rozbalte položky označené **webové služby**.  
  
7. Rozbalte položky označené **funkce pro vývoj aplikací**.  
  
8. Ujistěte se, zda že jsou vybrány následující položky:  
  
    1. **Rozšiřitelnost rozhraní .NET**  
  
    2. **ASP.NET**  
  
    3. **Rozšíření ISAPI**  
  
    4. **Filtry ISAPI**  
  
9. Rozbalte položky označené **nástroje webové správy**a pak vyberte **konzolu pro správu IIS**.  
  
10. V části položky označené **webové služby**, rozbalte **společné funkce protokolu Http**.  
  
11. Ujistěte se, že **statický obsah** zaškrtnuto.  
  
12. V části položky označené **webové služby**, rozbalte **zabezpečení**.  
  
13. Ujistěte se, že **ověřování Windows** zaškrtnuto.  
  
14. Rozbalte položky označené **IIS 6 Management Compatibility**a pak vyberte **IIS 6 Scripting Tools**.  
  
15. Rozbalte položky označené **rozhraní Microsoft .NET Framework 3.0**a pak vyberte **aktivace Windows Communication Foundation Http**.  
  
16. Klikněte na **OK**.  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a>Chcete-li nainstalovat službu IIS verze 6.0 v systému Windows Server 2003  
  
1. Z **Správa serveru**, klikněte na tlačítko **přidat nebo odebrat roli**a potom klikněte na tlačítko **Další**.  
  
2. Vyberte **aplikační server (IIS, ASP.NET)** z **Role serveru** seznamu a potom klikněte na tlačítko **Další**.  
  
3. Vyberte **povolit technologii ASP.NET** zaškrtněte políčko a potom klikněte na tlačítko **Další**.  
  
4. Pokud správnost souhrn výběry, klikněte na tlačítko Další.  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a>Chcete-li nainstalovat službu IIS verze 5.1 na Windows XP s aktualizací Service Pack 2 a aktualizací Service Pack 3 nainstalovat  
  
1. V Ovládacích panelech klikněte na tlačítko **přidat nebo odebrat programy**.  
  
2. V **přidat nebo odebrat programy** dialogové okno, klikněte na tlačítko **přidat nebo odebrat součásti Windows**.  
  
3. V **Průvodce součásti Windows**, vyberte **Internetové informační služby (IIS)** zaškrtněte políčko a potom klikněte na tlačítko **Další**.  
  
4. Pokud **soubory potřebné** dialogové okno se zobrazí, vložte instalační disk operačního systému, přejděte do složky i386 a pak klikněte na tlačítko **OK**.  
  
5. Po dokončení instalace klikněte na tlačítko **Dokončit**.  
  
6. Zavřete **přidat nebo odebrat programy** dialogové okno a potom zavřete **ovládací panely**.  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a>Ověření instalace služby IIS a ASP.NET  
  
1. Uložte soubor HTML najdete na konci tohoto tématu v kořenovém adresáři \InetPub\wwwroot a pojmenujte ho Default.aspx.  
  
2. Otevřete okno prohlížeče.  
  
3. Typ `http://localhost/Default.aspx` do pole adresy a potom stiskněte klávesu ENTER.  
  
4. By se zobrazit webovou stránku s textem "Hello World".  
  
> [!NOTE]
>  Pokaždé, když instalujete novou verzi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], je nutné znovu zaregistrovat aspnet_isapi jako rozšíření webové služby pro službu IIS. Uděláte to tak, vydávat `aspnet_regiis –I –enable` příkazu.  
  
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
