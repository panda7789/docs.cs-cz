---
title: Publikování služby WCF
ms.date: 03/30/2017
ms.assetid: c806b253-cd47-4b96-b831-e73cbf08808f
ms.openlocfilehash: 90d2a841fa5ce14b1ad5295b3bb6493df0350339
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321240"
---
# <a name="wcf-service-publishing"></a>Publikování služby WCF

Publikování služby Windows Communication Foundation (WCF) vám pomůže s tím, jak se chystáte v předčasném vývojovém prostředí poskytovaném hostitelem služby WCF a testovacím klientem WCF ke skutečnému nasazování aplikace do provozního prostředí pro účely testování. Než začnete s konečným plánem nasazení, můžete použít publikování služby Windows Communication Foundation (WCF) k ověření, že služba WCF správně funguje a je připravena k publikování. Můžete také zvolit nasazení knihoven služby WCF do různých cílových umístění pro účely testování.

## <a name="supported-services-and-target-locations"></a>Podporované služby a cílová umístění

Publikování služby WCF podporuje publikování služeb WCF vytvořených ze sady šablon knihovny služby WCF a jejich odpovídajících šablon položek, které zahrnují následující:

- Šablona knihovny služby WCF s šablonou položky

- Knihovna služby syndikace.

Tyto šablony služby můžete najít kliknutím na **soubor** > **Nový projekt** > [**Visual Basic** nebo **Visual C#** ] > **WCF**. Pro jiné šablony WCF v tomto umístění (včetně aplikace služby pracovního postupu WCF a aplikace služby WCF) můžete publikovat pomocí [publikování jedním kliknutím pro webové aplikace](https://docs.microsoft.com/previous-versions/aspnet/dd465337(v=vs.110)).

Službu lze publikovat do následujících cílových umístění.

- Místní služba IIS.

- Systém souborů.

- Server FTP.

## <a name="using-wcf-service-publishing"></a>Používání publikování služby WCF

Provedením následujících kroků nasaďte implementaci služby:

1. Otevřete Visual Studio se zvýšenými oprávněními (klikněte pravým tlačítkem na spustitelný soubor a vyberte **Spustit jako správce** a otevřete ho).  Pokud používáte službu IIS 7,0 nebo novější, ujistěte se, že máte nainstalovanou součást "kompatibilita konfigurace metabáze služby IIS a IIS6 Configuration" pomocí příkazu "zapnout nebo vypnout funkce systému Windows" v Ovládacích panelech.

2. Otevřete projekt služby, v hlavní nabídce vyberte **Build** > **publikovat \<Project název >** nebo klikněte pravým tlačítkem na projekt v **Průzkumník řešení** a klikněte na **publikovat**.

3. Zobrazí se okno **publikovat** . Klikněte na **...** . tlačítko pro určení cílového umístění, do kterého má být služba nasazena. Můžete vybrat možnost nasazení aplikace do místní služby IIS, systému souborů nebo serveru FTP. Pokud nasazujete aplikaci do místní služby IIS, můžete vybrat svůj web a vytvořit svou webovou aplikaci kliknutím na ikonu **vytvořit novou webovou aplikaci** v pravém horním rohu.

4. Po kliknutí na **publikovat** v hlavním okně aplikace Visual Studio nasadí aplikaci do zadaného cílového umístění a zkopíruje soubory Web. config,. svc a Assembly do cílového adresáře. . Název. svc bude "ProjectName. ServiceName. svc". Po úspěšném publikování služby můžete najít hotlink v okně výstupu sady Visual Studio, které vypadá podobně jako "připojení k `http://localhost/WebApplicationFolderName...`". Můžete stisknout klávesu CTRL a kliknout na odkaz pro otevření stránky prohlížeče v rámci sady Visual Studio a zobrazení struktury adresáře služby.

     Pokud nemůžete přejít na web, může to být způsobeno tím, že prohlížeč adresářů není ve službě IIS povolen. Pokud ho chcete povolit, postupujte podle tipů v části Co je možné vyzkoušet. Případně můžete přímo zadat `http://localhost/WebApplicationFolderName/ProjectName.ServiceName.svc` a zobrazit tak stránku služby.

**Publikování** můžete použít k určení, zda chcete zkopírovat sestavení, konfiguraci a soubor. svc pro všechny služby definované v projektu do cílového umístění a přepsat stávající soubory v cílovém umístění.

Pokud se rozhodnete nasadit aplikaci do místní služby IIS, může dojít k chybám souvisejícím s nastavením služby IIS. Ujistěte se prosím, že je služba IIS správně nainstalovaná. Do adresního řádku prohlížeče můžete zadat `http://localhost` a ověřit, jestli se zobrazí výchozí stránka IIS. V některých případech mohou být problémy také způsobeny nesprávným registrací ASP.NET nebo WCF ve službě IIS. Můžete otevřít Developer Command Prompt pro Visual Studio a spuštěním příkazu `aspnet_regiis.exe -ir` opravit problémy s registrací ASP.NET nebo spuštěním příkazu `ServiceModelReg.exe –ia` opravit problémy s registrací WCF.

## <a name="files-generated-for-publishing"></a>Soubory vygenerované pro publikování
 Předtím, než může být knihovna služby WCF hostitelem webu, jsou generovány následující soubory nástroje: soubory sestavení, soubor Web. config a soubor. svc. Všechny soubory jsou zkopírovány do cílového umístění. Služba je pak publikovaná.

### <a name="assembly-files"></a>Soubory sestavení
 Při publikování služby WCF pomocí tohoto nástroje je služba automaticky sestavena a soubory sestavení jsou po sestavení generovány v projektu služby.

### <a name="svc-file"></a>. Soubor SVC
 Operace publikování vygeneruje soubor *. svc pro každou službu WCF, zda soubor existuje, nebo ne, aby se zajistila platnost verze. Existují dva různé druhy souborů svc: jeden pro knihovnu služby WCF a knihovnu služby syndikace a druhý pro knihovnu služby pracovního postupu stavového a stavového stroje. Vygenerovaný @no__t soubor -0. svc je zkopírován do kořenové složky v cílovém umístění.

### <a name="webconfig-file"></a>Soubor Web. config
 Pokaždé, když je projekt služby publikován do konkrétního cílového umístění, vytvoří se soubor Web. config.

 Vygenerovaný soubor Web. config obsahuje webové oddíly, které jsou užitečné pro hostování webů, a obsah souboru App. config pro knihovnu služby WCF s následujícími změnami:

- Základní adresa je vyloučena.

- Nastavení v elementu `<diagnostics>` jsou vyloučena, aby se zachovala nastavení trasování cílové platformy.

## <a name="publishing-wcf-services-with-non-http-bindings-to-iis"></a>Publikování služeb WCF s vazbami jiného typu než HTTP do služby IIS
 Pokud používáte službu IIS 7.0 nebo novější, můžete publikovat služby WCF s vazbami jiného typu než HTTP do služby IIS. Musíte provést některé předběžné konfigurace. Další informace najdete v tématech o [hostování v aktivační službě procesů systému Windows](./feature-details/hosting-in-windows-process-activation-service.md).

## <a name="security"></a>Zabezpečení
 Publikování do místní služby IIS vyžaduje oprávnění správce, protože služba IIS vyžaduje, aby běžela v účtu správce. Pokud uživatel bez oprávnění správce otevře publikování služby WCF, služba IIS není k dispozici jako cílové umístění. Publikování do systému souborů nebo serveru FTP funguje bez oprávnění správce.

## <a name="see-also"></a>Viz také:

- [Šablony sady Visual Studio pro WCF](wcf-vs-templates.md)
- [Hostitel služby WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
- [Testovací klient WCF (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
