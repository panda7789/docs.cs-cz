---
title: Pokyny pro instalaci virtuálního adresáře
ms.date: 03/30/2017
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
ms.openlocfilehash: 7999a040dc14d75a34b75f320982dd3118eae670
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225583"
---
# <a name="virtual-directory-setup-instructions"></a>Pokyny pro instalaci virtuálního adresáře
Ukázky Windows Communication Foundation (WCF) jsou určené ke sdílení běžné virtuální adresář s názvem servicemodelsamples, která je namapována na složku %SystemDrive%\inetpub\wwwroot\servicemodelsamples.  
  
> [!NOTE]
>  Jednotka % SystemDrive % je obvykle C: a D:, v závislosti na umístění disku instalaci Internetové informační služby (IIS).  
  
 Můžete spouštět Setupvroot.bat a Cleanupvroot.bat soubory z [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) vytvořit virtuální adresář. Pokud chcete ručně vytvořit virtuální adresář, použijte následující postupy.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a>Chcete-li vytvořit virtuální adresář ve službě IIS 7.0 nebo 7.5  
  
1.  Z **Start** nabídky, klikněte na tlačítko **spustit**, zadejte **inetmgr** otevřete modul snap-in konzoly MMC Internetové informační služby (IIS).  
  
2.  V levém podokně rozbalte uzel s názvem počítače a potom rozbalte **lokality** uzlu.  
  
3.  Klikněte pravým tlačítkem na **výchozí webový server**a pak vyberte **přidat aplikaci** otevřít **okna Přidat aplikaci**.  
  
4.  V okně zadejte `servicemodelsamples` jako alias pro virtuální adresář, který vytváříte.  
  
5.  Vytvořit následující složku: %SystemDrive%\inetpub\wwwroot\servicemodelsamples  
  
6.  Nastavte na % SystemDrive%\inetpub\wwwroot\servicemodelsamples fyzickou cestu.  Většina Ukázky WCF zkopírujte do tohoto umístění při vytváření služby spustitelné soubory.  
  
7.  Klikněte na **OK**. Webová aplikace je vytvořený pro ukázky WCF.  
  
    > [!NOTE]
    >  Tato úloha musí pouze jednou provést, protože všechny ukázky WCF používají stejné servicemodelsamples webové aplikace.  
  
    > [!NOTE]
    >  Pro účely této dokumentace termín `virtual directory` je synonymní s `Web application`.  
  
     Kromě vytvoření virtuálního adresáře, musíte také nastavit jeho vlastnosti umožňující spuštění služeb WCF. Podrobnosti najdete níže.  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a>Chcete-li vytvořit virtuální adresář v IIS 5.1 a 6.0  
  
1.  Otevřete okno příkazového řádku a zadejte `start inetmgr` otevřete modul snap-in konzoly MMC Internetové informační služby (IIS).  
  
2.  V levém podokně rozbalte uzel s názvem počítače a potom rozbalte **weby** uzlu.  
  
3.  Klikněte pravým tlačítkem na **výchozí webový server** a vyberte **nový, virtuální adresář** otevřete Průvodce vytvořením virtuálního adresáře.  
  
4.  V průvodci zadejte `servicemodelsamples` jako alias pro virtuální adresář, který vytváříte.  
  
5.  Nastavení cesty k % SystemDrive%\inetpub\wwwroot\servicemodelsamples. Většina Ukázky WCF zkopírujte do tohoto umístění při vytváření služby spustitelné soubory.  
  
6.  Klikněte na **Další**.  
  
7.  Ve výchozím nastavení jsou vybrány následující políčka:  
  
    -   **Číst**  
  
    -   **Spouštění skriptů (například ASP)**  
  
8.  Klikněte na tlačítko **Další**a potom klikněte na tlačítko **Dokončit** kroky průvodce dokončete.  
  
    > [!NOTE]
    >  Tato úloha musí pouze jednou provést, protože všechny ukázky WCF používají servicemodelsamples virtuální adresář.  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a>Chcete-li nastavit vlastnosti další virtuální adresáře ve službě IIS 7.0 nebo 7.5  
  
1.  Klikněte na uzel servicemodelsamples. V dolní části okna jsou uvedeny dvě zobrazení. Vyberte **zobrazení funkcí** Pokud ještě není vybraná.  
  
2.  Dvakrát klikněte na položku **procházení adresářů**.  
  
3.  V podokně Akce, vyberte **povolit** možnost. Umožňuje získat přístup k adresáři adresáře pomocí aplikace Internet Explorer, který pomáhá při ladění služby.  
  
 Nakonec musíte nastavit vlastnosti zabezpečení servicemodelsamples složky, aby mohla být přístup i jiní. Podrobnosti najdete níže.  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a>Chcete-li nastavit vlastnosti další virtuální adresář IIS 5.1 a 6.0  
  
1.  Klikněte pravým tlačítkem na uzel servicemodelsamples a potom klikněte na tlačítko **vlastnosti**.  
  
2.  Ve výchozím nastavení jsou vybrány následující políčka:  
  
    -   **Číst**  
  
    -   **Navštíví protokolu**  
  
    -   **Xovat tento prostředek**  
  
3.  Vyberte **procházení adresářů** zaškrtávací políčko. Umožňuje získat přístup k adresáři adresáře pomocí aplikace Internet Explorer, který pomáhá při ladění služby.  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a>Chcete-li nastavit vlastnosti zabezpečení složky ve službě IIS 7.0 nebo 7.5  
  
1.  Přejděte na % SystemDrive%\inetpub\wwwroot\servicemodelsamples.  
  
2.  Klikněte pravým tlačítkem na složku servicemodelsamples a klikněte na tlačítko **sdílenou složku** nebo **sdílenou složku s**.  
  
3.  Klikněte na šipku dolů nalevo od **přidat** tlačítko.  
  
4.  Vyberte **najít** položka. **Vybrat uživatele nebo skupiny** otevře se okno.  
  
5.  Klikněte na tlačítko **Advanced**.  
  
6.  Klikněte na tlačítko **umístění**. **Umístění** okna je teď otevřené.  
  
7.  Vyberte položku pro počítač používá. Je důležité vybrat místním počítači a ne položka pro všechny domény nebo sítě, které jsou uvedeny. Jakmile vyberete počítač, klikněte na tlačítko **OK**.  
  
8.  Klikněte na tlačítko **najít**. Tím vyplníte výsledky hledání s objekty přidružené k místnímu počítači.  
  
9. Najít **IIS_IUSRS** položku **název (relativní rozlišující název)** sloupec. Vyberte tuto položku a klikněte na tlačítko **OK** hledání zavřete okno výsledků.  
  
10. Klikněte na tlačítko **OK** zavřete **vybrat uživatele nebo skupiny** okna.  
  
11. Klikněte na tlačítko **sdílené složky** a zachová tak změny.  
  
12. Po povolení sdílení změn se dokončí, klikněte na tlačítko **provádí** zavřete **sdílení souborů** okna.  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a>Chcete-li nastavit vlastnosti zabezpečení složky v IIS 5.1 a 6.0  
  
1.  Přejděte na % SystemDrive%\inetpub\wwwroot\servicemodelsamples.  
  
2.  Klikněte pravým tlačítkem myši **servicemodelsamples** složku a pak klikněte na tlačítko **sdílení a zabezpečení.**  
  
3.  Klikněte na tlačítko **zabezpečení** kartu.  
  
4.  Pokud používáte IIS 6.0 v **skupiny nebo jméno uživatele** zaškrtněte políčko, zda **účet Guest Internet** je uvedena.  
  
     Pokud není uvedená:  
  
    1.  Klikněte na tlačítko **Start** a potom klikněte na tlačítko **ovládací panely**.  
  
    2.  Pokud se nezobrazí **uživatelské účty** ikonu, klikněte na tlačítko **přepnout na zobrazení kategorií**.  
  
    3.  Klikněte na tlačítko **uživatelské účty** ikonu.  
  
    4.  V části "nebo vyberte ikonu ovládacího prvku panelu," klikněte na tlačítko **uživatelské účty**.  
  
    5.  V **uživatelské účty** dialogové okno, klikněte na tlačítko **Upřesnit** kartu.  
  
    6.  Klikněte na tlačítko **Advanced**.  
  
    7.  V **místní uživatelé a skupiny** dialogové okno, rozbalte kliknutím **uživatelé** složky.  
  
    8.  V pravém podokně klikněte dvakrát na **účet Guest Internet**.  
  
    9. V **vlastnosti** dialogové okno, zkopírujte název použit jako účet guest Internet. Ve výchozím nastavení název začíná řetězcem "USR_", za nímž následuje název počítače.  
  
    10. Zavřít **vlastnosti** dialogové okno.  
  
    11. Zavřít **místní uživatelé a skupiny** dialogové okno.  
  
    12. Zavřít **uživatelské účty** dialogové okno.  
  
    13. Zavřete druhou **uživatelské účty** dialogové okno.  
  
    14. V **servicemodelsamples vlastnosti** dialogovém okně **zabezpečení** klikněte na tlačítko **přidat**.  
  
    15. Zadejte název počítače, za nímž následuje zpětné lomítko a poté vložte název účtu uživatele Internet, například myMachineName\\InternetGuestAccountName %  
  
    16. Klikněte na tlačítko **Kontrola názvů** aby se ověřilo přidání. Pokud je platný, je název velkými písmeny a podtržené.  
  
5.  Pro službu IIS 6.0, zkontrolujte také, že síťová služba je uveden v **skupiny nebo jméno uživatele** pole.  
  
     Pokud není uvedená síť služby:  
  
    1.  Klikněte na **Přidat**.  
  
    2.  V **vybrat uživatele nebo skupiny** dialogové okno, zadejte název počítače, a potom je zpětným lomítkem.  
  
    3.  Typ **služby** za zpětným lomítkem (bez mezer).  
  
    4.  Klikněte na tlačítko **zkontrolovat názvy**.  
  
    5.  Pokud je nalezeno více jmen, vyberte **síťová služba** a klikněte na tlačítko **OK**.  
  
    6.  Klikněte na tlačítko **OK** zavřete **vybrat uživatele nebo skupiny** dialogové okno.  
  
6.  Pokud používáte Windows XP SP2 se služba IIS 5.1, zkontrolujte, že jsou v uvedené Internet účet Guest a ASPNET **skupiny nebo jméno uživatele** pole.  
  
     Všimněte si, že uživatel ASPNET může být členem předdefinované **uživatelé** skupiny zabezpečení. Pokud ano, pak v případě **uživatelé** skupina je uvedena v dialogovém okně, není potřeba ho přidat jako samostatné položky do seznamu povolených uživatelů.  
  
     Chcete-li zkontrolovat, jestli ASPNET je součástí **uživatelé** skupiny zabezpečení:  
  
    1.  Na **Start** nabídky, klikněte na tlačítko **ovládací panely**.  
  
    2.  Klikněte na tlačítko **uživatelské účty** ikonu.  
  
    3.  V **skupiny** sloupce, zkontrolujte, že hodnota **ASPNET** "uživatelů."  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k hostování služby IIS](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
