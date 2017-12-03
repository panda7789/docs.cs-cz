---
title: "Pokyny pro instalaci virtuálního adresáře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 72487c4a6720f80119beb837fbb3b5ea25ac3b93
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="virtual-directory-setup-instructions"></a>Pokyny pro instalaci virtuálního adresáře
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Ukázky jsou určeny k sdílejí společný virtuální adresář s názvem servicemodelsamples, který je namapovaný na %SystemDrive%\inetpub\wwwroot\servicemodelsamples složky.  
  
> [!NOTE]
>  % SystemDrive % je obvykle C: nebo D:, v závislosti na umístění jednotky, kde je nainstalován Internetové informační služby (IIS).  
  
 Můžete spouštět soubory Setupvroot.bat a Cleanupvroot.bat z [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) se vytvořit virtuální adresář. Pokud ale chcete ručně vytvořit virtuální adresář, použijte následující postupy.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a>Chcete-li vytvořit virtuální adresář ve službě IIS 7.0 nebo 7.5  
  
1.  Z **spustit** nabídky, klikněte na tlačítko **spustit**, pak zadejte **inetmgr** otevřete modul snap-in konzoly MMC Internetové informační služby (IIS).  
  
2.  V levém podokně rozbalte uzel s názvem počítače a pak rozbalte **lokality** uzlu.  
  
3.  Klikněte pravým tlačítkem na **Default Web Site**a potom vyberte **přidat aplikaci** otevřete **okna Přidat aplikaci**.  
  
4.  V okně zadejte `servicemodelsamples` jako alias pro virtuální adresář, který vytvoříte.  
  
5.  Vytvořte na následující adresář: %SystemDrive%\inetpub\wwwroot\servicemodelsamples  
  
6.  Nastavte na % SystemDrive%\inetpub\wwwroot\servicemodelsamples fyzickou cestu.  Většina Ukázky WCF zkopírujte služby spustitelné soubory do tohoto umístění při sestavení.  
  
7.  Click **OK**. Webová aplikace je nyní vytvořen pro ukázky WCF.  
  
    > [!NOTE]
    >  Tato úloha musí provést pouze jednou, protože všechny [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ukázky použijte stejné servicemodelsamples webové aplikace.  
  
    > [!NOTE]
    >  Pro účely této dokumentace termín `virtual directory` je totožná s `Web application`.  
  
     Kromě vytvoření virtuálního adresáře, musíte taky nastavit její vlastnosti, aby povolit [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spuštění služeb. Níže naleznete podrobnosti.  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a>Chcete-li vytvořit virtuální adresář v IIS 5.1 nebo 6.0  
  
1.  Otevřete okno příkazového řádku a zadejte `start inetmgr` otevřete modul snap-in konzoly MMC Internetové informační služby (IIS).  
  
2.  V levém podokně rozbalte uzel s názvem počítače a pak rozbalte **weby** uzlu.  
  
3.  Klikněte pravým tlačítkem na **Default Web Site** a vyberte **nový, virtuální adresář** otevřete Průvodce vytvořením virtuálního adresáře.  
  
4.  V průvodci zadejte `servicemodelsamples` jako alias pro virtuální adresář, který vytvoříte.  
  
5.  Nastavte cestu k % SystemDrive%\inetpub\wwwroot\servicemodelsamples. Většina [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ukázky zkopírujte služby spustitelné soubory do tohoto umístění při sestavení.  
  
6.  Klikněte na tlačítko **Další**.  
  
7.  Ve výchozím nastavení jsou vybrány následující zaškrtávací políčka:  
  
    -   **Pro čtení**  
  
    -   **Spouštění skriptů (například ASP)**  
  
8.  Klikněte na tlačítko **Další**a potom klikněte na **Dokončit** dokončete průvodce.  
  
    > [!NOTE]
    >  Tato úloha musí provést pouze jednou, protože všechny [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ukázky používat stejné servicemodelsamples virtuální adresář.  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a>Chcete-li nastavit další virtuální adresář vlastnosti ve službě IIS 7.0 nebo 7.5  
  
1.  Klikněte na uzel servicemodelsamples. Ve spodní části okna jsou uvedeny dvě zobrazení. Vyberte **zobrazení funkcí** Pokud již není vybrána.  
  
2.  Dvakrát klikněte na položku **procházení adresářů**.  
  
3.  V podokně Akce vyberte **povolit** možnost. To umožňuje přístup k adresáři adresáře v aplikaci Internet Explorer, která pomáhá při ladění služby.  
  
 Nakonec musíte nastavit vlastnosti zabezpečení servicemodelsamples složky, aby mělo přístup ostatní uživatelé. Níže naleznete podrobnosti.  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a>Chcete-li nastavit vlastnosti další virtuální adresář v IIS 5.1 a 6.0  
  
1.  Klikněte pravým tlačítkem na uzel servicemodelsamples a pak klikněte na tlačítko **vlastnosti**.  
  
2.  Ve výchozím nastavení jsou vybrány následující zaškrtávací políčka:  
  
    -   **Pro čtení**  
  
    -   **Navštíví protokolu**  
  
    -   **Index tento prostředek**  
  
3.  Vyberte **procházení adresářů** zaškrtávací políčko. To umožňuje přístup k adresáři adresáře v aplikaci Internet Explorer, která pomáhá při ladění služby.  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a>Chcete-li nastavit vlastnosti zabezpečení složky ve službě IIS 7.0 nebo 7.5  
  
1.  Přejděte na % SystemDrive%\inetpub\wwwroot\servicemodelsamples.  
  
2.  Klikněte pravým tlačítkem na složku servicemodelsamples a klikněte na tlačítko **sdílené složky** nebo **sdílenou složku s**.  
  
3.  Klikněte na šipku nalevo od **přidat** tlačítko.  
  
4.  Vyberte **najít** položku. **Vybrat uživatele nebo skupiny** otevře se okno.  
  
5.  Klikněte na tlačítko **rozšířené**.  
  
6.  Klikněte na tlačítko **umístění**. **Umístění** je nyní otevřené okno.  
  
7.  Vyberte položku pro počítač používá. Je důležité vybrat místní počítač a ne položka pro všechny domény nebo sítě, které jsou uvedeny. Po výběru počítače, klikněte na tlačítko **OK**.  
  
8.  Klikněte na tlačítko **najít**. Tím vyplníte výsledků hledání s objekty přidružené k místním počítači.  
  
9. Najít **IIS_IUSRS** položku **název (relativní rozlišující název)** sloupce. Vyberte tuto položku a klikněte na **OK** hledání zavřete okno výsledků.  
  
10. Klikněte na tlačítko **OK** zavřete **vybrat uživatele nebo skupiny** okno.  
  
11. Klikněte na tlačítko **sdílenou složku** a zachová tak změny.  
  
12. Po dokončení se změny povolit sdílení, klikněte na tlačítko **provádí** zavřete **sdílení souborů** okno.  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a>Nastavit vlastnosti zabezpečení složky v IIS 5.1 nebo 6.0  
  
1.  Přejděte na % SystemDrive%\inetpub\wwwroot\servicemodelsamples.  
  
2.  Klikněte pravým tlačítkem myši **servicemodelsamples** složku a pak klikněte na tlačítko **sdílení a zabezpečení.**  
  
3.  Klikněte **zabezpečení** kartě.  
  
4.  Pokud používáte služby IIS 6.0, **skupiny nebo jméno uživatele** zaškrtněte políčko zda **účtu Guest Internet** je uveden.  
  
     Pokud v seznamu není:  
  
    1.  Klikněte na tlačítko **spustit** a pak klikněte na **ovládací panely**.  
  
    2.  Pokud se nezobrazí **uživatelské účty** ikonu, klikněte na tlačítko **přepnout na zobrazení kategorií**.  
  
    3.  Klikněte **uživatelské účty** ikonu.  
  
    4.  V části "nebo vyberte ikonu Ovládací panely," klikněte na tlačítko **uživatelské účty**.  
  
    5.  V **uživatelské účty** dialogové okno, klikněte **Upřesnit** kartě.  
  
    6.  Klikněte na tlačítko **rozšířené**.  
  
    7.  V **místní uživatelé a skupiny** dialogové okno, rozbalte kliknutím **uživatelé** složky.  
  
    8.  V pravém podokně klikněte dvakrát na **účtu Guest Internet**.  
  
    9. V **vlastnosti** dialogové okno, kopie tento název používá jako účet guest Internetu. Ve výchozím nastavení název začíná řetězcem "USR_" a název počítače.  
  
    10. Zavřít **vlastnosti** dialogové okno.  
  
    11. Zavřít **místní uživatelé a skupiny** dialogové okno.  
  
    12. Zavřít **uživatelské účty** dialogové okno.  
  
    13. Zavřete dalších **uživatelské účty** dialogové okno.  
  
    14. V **servicemodelsamples vlastnosti** v dialogovém **zabezpečení** , klikněte na **přidat**.  
  
    15. Zadejte název počítače, za nímž následuje zpětné lomítko, pak vložit název účtu uživatele Internetu, například myMachineName\\InternetGuestAccountName %  
  
    16. Klikněte na tlačítko **Kontrola názvů** ověření přidání. Pokud je platný, název je v velkými písmeny a jsou podtržené.  
  
5.  Pro služby IIS 6.0, také zkontrolujte, jestli síťové služby je uvedený v **skupiny nebo jméno uživatele** pole.  
  
     Pokud není uvedené síťové služby:  
  
    1.  Klikněte na tlačítko **přidat**.  
  
    2.  V **vybrat uživatele nebo skupiny** dialogové okno, zadejte název počítače, následuje zpětné lomítko.  
  
    3.  Typ **služby** po zpětné lomítko (bez mezery).  
  
    4.  Klikněte na tlačítko **Zkontrolujte názvy**.  
  
    5.  Pokud je nalezeno více jmen, vyberte **síťové služby** a klikněte na tlačítko **OK**.  
  
    6.  Klikněte na tlačítko **OK** zavřete **vybrat uživatele nebo skupiny** dialogové okno.  
  
6.  Pokud používáte systém Windows XP SP2 se služba IIS 5.1, zkontrolujte, jestli jsou v uvedený účet Guest Internet a ASPNET **skupiny nebo jméno uživatele** pole.  
  
     Upozorňujeme, že uživatel ASPNET může být člen předdefinované **uživatelé** skupiny zabezpečení. Pokud ano, pak pokud **uživatelé** skupina je uvedena v dialogovém okně, není potřeba ji přidat jako samostatný položky do seznamu povolených uživatelů.  
  
     Zkontrolujte, zda ASPNET je součástí **uživatelé** skupiny zabezpečení:  
  
    1.  Na **spustit** nabídky, klikněte na tlačítko **ovládací panely**.  
  
    2.  Klikněte **uživatelské účty** ikonu.  
  
    3.  V **skupiny** sloupce, zkontrolujte, zda hodnota **ASPNET** je "Uživatelé."  
  
## <a name="see-also"></a>Viz také  
 [Internetové informace o pokyny k hostování služby](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
