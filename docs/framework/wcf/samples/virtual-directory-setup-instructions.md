---
title: Pokyny pro instalaci virtuálního adresáře
ms.date: 03/30/2017
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
ms.openlocfilehash: 6dccc5174e3fb9ab67023310d8c060d598a707c9
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038649"
---
# <a name="virtual-directory-setup-instructions"></a>Pokyny pro instalaci virtuálního adresáře
Ukázky Windows Communication Foundation (WCF) mají za cíl sdílet společný virtuální adresář s názvem ServiceModelSamples, který je namapován na složku%SystemDrive%\inetpub\wwwroot\servicemodelsamples.  
  
> [!NOTE]
> Jednotka% SystemDrive% je obvykle C: nebo D:, v závislosti na umístění jednotky, kde je nainstalovaná Internetová informační služba (IIS).  
  
 Můžete spustit soubory Setupvroot. bat a cleanupvroot. bat z [procesu jednorázového nastavení pro Windows Communication Foundation Samples pro](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) vytvoření virtuálního adresáře. Pokud budete chtít vytvořit virtuální adresář ručně, použijte následující postupy.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a>Vytvoření virtuálního adresáře ve službě IIS 7,0 nebo 7,5  
  
1. V nabídce **Start** klikněte na tlačítko **Spustit**a zadejte příkaz **inetmgr** . tím otevřete modul snap-in konzoly MMC Internetová informační služba (IIS).  
  
2. V levém podokně rozbalte uzel s názvem počítače a potom rozbalte uzel **lokality** .  
  
3. Klikněte pravým tlačítkem na **výchozí web**a pak vyberte **Přidat aplikaci** . otevře se **okno Přidat aplikaci**.  
  
4. V okně zadejte `servicemodelsamples` alias pro virtuální adresář, který vytváříte.  
  
5. Vytvořte následující adresář:%SystemDrive%\inetpub\wwwroot\servicemodelsamples  
  
6. Nastavte fyzickou cestu na%SystemDrive%\inetpub\wwwroot\servicemodelsamples.  Většina ukázek WCF při sestavení zkopíruje spustitelné soubory služby do tohoto umístění.  
  
7. Klikněte na **OK**. Webová aplikace je nyní vytvořena pro ukázky WCF.  
  
    > [!NOTE]
    > Tato úloha musí být prováděna pouze jednou, protože všechny ukázky služby WCF používají stejnou webovou aplikaci ServiceModelSamples.  
  
    > [!NOTE]
    > Pro účely této dokumentace je termínem `virtual directory` synonymum. `Web application`  
  
     Kromě vytváření virtuálního adresáře musíte také nastavit jeho vlastnosti, aby bylo možné spouštět služby WCF. Podrobnosti najdete níže.  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a>Vytvoření virtuálního adresáře ve službě IIS 5,1 nebo 6,0  
  
1. Otevřete okno příkazového řádku a zadejte `start inetmgr` a otevřete modul snap-in konzoly MMC Internetová informační služba (IIS).  
  
2. V levém podokně rozbalte uzel s názvem počítače a potom rozbalte uzel **weby** .  
  
3. Klikněte pravým tlačítkem na **výchozí web** a vyberte **Nový, virtuální adresář** . otevře se Průvodce vytvořením virtuálního adresáře.  
  
4. V průvodci zadejte `servicemodelsamples` alias pro virtuální adresář, který vytváříte.  
  
5. Nastavte cestu na%SystemDrive%\inetpub\wwwroot\servicemodelsamples. Většina ukázek WCF při sestavení zkopíruje spustitelné soubory služby do tohoto umístění.  
  
6. Klikněte na **Další**.  
  
7. Ve výchozím nastavení jsou zaškrtnuta následující zaškrtávací políčka:  
  
    - **Read**  
  
    - **Spouštění skriptů (například ASP)**  
  
8. Klikněte na tlačítko **Další**a dokončete průvodce kliknutím na tlačítko **Dokončit** .  
  
    > [!NOTE]
    > Tato úloha se musí provést jenom jednou, protože všechny ukázky WCF používají stejný virtuální adresář ServiceModelSamples.  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a>Nastavení dalších vlastností virtuálního adresáře ve službě IIS 7,0 nebo 7,5  
  
1. Klikněte na uzel ServiceModelSamples. Podél dolního okraje okna jsou uvedena dvě zobrazení. Vyberte **zobrazení funkcí** , pokud ještě není vybrané.  
  
2. Dvakrát klikněte na položku pro **procházení adresářů**.  
  
3. V podokně Akce vyberte možnost **Povolit** . To umožňuje přístup k adresáři adresáře pomocí aplikace Internet Explorer, která pomáhá při ladění služby.  
  
 Nakonec musíte nastavit vlastnosti zabezpečení pro složku ServiceModelSamples, aby k ní měli přístup jiní uživatelé. Podrobnosti najdete níže.  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a>Nastavení dalších vlastností virtuálního adresáře ve službě IIS 5,1 nebo 6,0  
  
1. Klikněte pravým tlačítkem na uzel ServiceModelSamples a pak klikněte na **vlastnosti**.  
  
2. Ve výchozím nastavení jsou zaškrtnuta následující zaškrtávací políčka:  
  
    - **Read**  
  
    - **Protokolovat návštěvy**  
  
    - **Index tohoto prostředku**  
  
3. Zaškrtněte políčko **procházení adresářů** . To umožňuje přístup k adresáři adresáře pomocí aplikace Internet Explorer, která pomáhá při ladění služby.  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a>Nastavení vlastností zabezpečení složky ve službě IIS 7,0 nebo 7,5  
  
1. Přejít na%SystemDrive%\inetpub\wwwroot\servicemodelsamples.  
  
2. Klikněte pravým tlačítkem na složku ServiceModelSamples a pak klikněte na **sdílet** nebo **sdílet s**.  
  
3. Klikněte na šipku dolů nalevo od tlačítka **Přidat** .  
  
4. Vyberte položku **Najít** . Otevře se okno **Vybrat uživatele nebo skupiny** .  
  
5. Klikněte na tlačítko **Advanced**.  
  
6. Klikněte na **umístění**. Okno **umístění** je nyní otevřeno.  
  
7. Vyberte položku pro používaný počítač. Je důležité vybrat místní počítač a nikoli položku pro žádné domény nebo sítě, které jsou uvedeny v seznamu. Po výběru počítače klikněte na tlačítko **OK**.  
  
8. Klikněte na **Najít**. Tím se výsledky hledání naplní objekty, které jsou přidružené k místnímu počítači.  
  
9. Najděte položku **IIS_IUSRS** ve sloupci **název (relativní rozlišující název)** . Vyberte tuto položku a kliknutím na tlačítko **OK** zavřete okno výsledků hledání.  
  
10. Kliknutím na tlačítko **OK** zavřete okno **Vybrat uživatele nebo skupiny** .  
  
11. Kliknutím na **sdílet** zachovejte změny.  
  
12. Po dokončení změn pro povolení sdílení klikněte na Hotovo a zavřete okno **sdílení souborů** .  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a>Nastavení vlastností zabezpečení složky ve službě IIS 5,1 nebo 6,0  
  
1. Přejít na%SystemDrive%\inetpub\wwwroot\servicemodelsamples.  
  
2. Klikněte pravým tlačítkem na složku **ServiceModelSamples** a pak klikněte na **sdílení a zabezpečení.**  
  
3. Klikněte na kartu **zabezpečení** .  
  
4. Pokud používáte službu IIS 6,0, v poli **název skupiny nebo jméno uživatele** ověřte, zda je uveden **účet internetového účtu Guest** .  
  
     Pokud není uveden:  
  
    1. Klikněte na tlačítko **Start** a poté na příkaz **Ovládací panely**.  
  
    2. Pokud se nezobrazí ikona **uživatelské účty** , klikněte na **Přepnout do zobrazení kategorií**.  
  
    3. Klikněte na ikonu **uživatelské účty** .  
  
    4. V části nebo vyberte ikonu ovládacího panelu, klikněte na **uživatelské účty**.  
  
    5. V dialogovém okně **uživatelské účty** klikněte na kartu **Upřesnit** .  
  
    6. Klikněte na tlačítko **Advanced**.  
  
    7. V dialogovém okně **místní uživatelé a skupiny** rozbalte složku **Uživatelé** kliknutím.  
  
    8. V pravém podokně dvakrát klikněte na možnost **účet internetového účtu Guest**.  
  
    9. V dialogovém okně **vlastnosti** zkopírujte název používaný jako internetový účet hosta. Ve výchozím nastavení začíná název "USR_" následovaný názvem počítače.  
  
    10. Zavřete dialogové okno **vlastnosti** .  
  
    11. Zavřete dialogové okno **místní uživatelé a skupiny** .  
  
    12. Zavřete dialogové okno **uživatelské účty** .  
  
    13. Zavřete dialogové okno ostatní **uživatelské účty** .  
  
    14. V dialogovém okně **vlastnosti ServiceModelSamples** na kartě **zabezpečení** klikněte na **Přidat**.  
  
    15. Zadejte název počítače následovaný zpětným lomítkem a pak vložte název internetového uživatelského účtu, například myMachineName\\% InternetGuestAccountName%.  
  
    16. Kliknutím na **Kontrola názvů** ověřte přidání. Pokud je platný, jméno je velkými písmeny a je podtržené.  
  
5. V případě služby IIS 6,0 zaškrtněte políčko síťová služba je uvedena v poli **název skupiny nebo jméno uživatele** .  
  
     Pokud síťová služba není uvedená:  
  
    1. Klikněte na **Přidat**.  
  
    2. V dialogovém okně **Vybrat uživatele nebo skupiny** zadejte název počítače následovaný zpětným lomítkem.  
  
    3. Zadejte **službu** za zpětným lomítkem (bez mezer).  
  
    4. Klikněte na tlačítko **kontrolovat jména**.  
  
    5. Pokud je nalezeno více názvů, vyberte **Síťová služba** a klikněte na tlačítko **OK**.  
  
    6. Kliknutím na tlačítko **OK** zavřete dialogové okno **Vybrat uživatele nebo skupiny** .  
  
6. Pokud používáte systém Windows XP SP2 se službou IIS 5,1, zaškrtněte políčko v poli **název skupiny nebo jméno uživatele** .  
  
     Všimněte si, že uživatel ASPNET může být členem předdefinované skupiny zabezpečení **Uživatelé** . Pokud ano, pak pokud je skupina **uživatelů** uvedena v dialogovém okně, není nutné ji přidat jako samostatnou položku do seznamu povolených uživatelů.  
  
     Chcete-li zjistit, zda je ASPNET součástí skupiny zabezpečení **Uživatelé** :  
  
    1. V nabídce **Start** klikněte na příkaz **Ovládací panely**.  
  
    2. Klikněte na ikonu **uživatelské účty** .  
  
    3. Ve sloupci **Skupina** ověřte, že hodnota pro **ASPNET** je "Users".  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k hostování Internetové informační služby](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
