---
title: Publikování služby WCF
ms.date: 03/30/2017
ms.assetid: c806b253-cd47-4b96-b831-e73cbf08808f
ms.openlocfilehash: 33725c2f393529a7e59ed0b3ae1db01a359fb9a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791206"
---
# <a name="wcf-service-publishing"></a>Publikování služby WCF

Publikování služby Windows Communication Foundation (WCF) vám pomůže v rané fázi vývojového prostředí ve skutečnosti nasazení aplikace do produkčního prostředí pro účely testování poskytované hostitel služby WCF a testovací klient WCF průběh. Předtím, než jste se zavázali k plánu poslední nasazení, můžete pro publikování služby Windows Communication Foundation (WCF) k ověření, že vaše služba WCF správně proveden a je připravená k publikování. Můžete také nasadit knihovny služby WCF na různé cílové umístění pro testování.

## <a name="supported-services-and-target-locations"></a>Podporované služby a cílové umístění

Publikování služby WCF podporuje publikování služby WCF vytvořené ze souboru šablony knihovny služby WCF a jejich odpovídající šablony položek, které zahrnují následující:

- Šablona knihovny služby WCF pomocí šablony položky.

- Knihovna služby syndikace.

Tyto šablony služeb můžete najít výběrem **souboru** > **nový projekt** > [**jazyka Visual Basic** nebo **Visual C#** ] > **WCF**. Pro další šablony WCF v tomto umístění (včetně aplikace služeb pracovního postupu WCF a aplikace služby WCF), které můžete publikovat pomocí [jedním kliknutím pro publikování webových aplikací](https://docs.microsoft.com/previous-versions/aspnet/dd465337(v=vs.110)).

Službě mohou být publikovány do následujícího umístění, cíl.

- Místní služba IIS.

- Systém souborů.

- Server FTP.

## <a name="using-wcf-service-publishing"></a>Pomocí technologie WCF publikování služby

Proveďte následující kroky k nasazení implementaci služby:

1. Otevřete Visual Studio se zvýšenými oprávněními (pravým tlačítkem na spustitelný soubor a zvolte **spustit jako správce** ho otevřete).  Pokud používáte IIS 7.0 nebo novější, ujistěte se, že jste nainstalovali "Kompatibilita metabáze služby IIS a služby IIS6, která konfigurace" součást "Windows zapnout nebo vypnout funkce" pomocí ovládacího panelu.

2. Otevřete projekt služby, vyberte **sestavení** > **publikovat \<název projektu >** z hlavní nabídky, nebo klikněte pravým tlačítkem na projekt v **Průzkumníka řešení**a klikněte na tlačítko **publikovat**.

3. **Publikovat** zobrazí se okno. Klikněte na tlačítko **...** . tlačítko k určení, které byste měli nasadit službu do cílového umístění. Můžete vybrat k nasazení aplikace do místní služby IIS, systém souborů nebo FTP. Pokud nasazení aplikace do místní služby IIS, můžete vybrat svůj web a vytvoření webové aplikace v něm, kliknutím **vytvořit novou webovou aplikaci** ikonu v pravém horním rohu.

4. Po kliknutí na **publikovat** v hlavním okně aplikace Visual Studio nasadí aplikaci do zadané cílové umístění a zkopíruje soubory Web.config, svc a sestavení do cílového adresáře. . Název .svc bude "ProjectName.ServiceName.svc". Po publikování úspěšně, můžete najít hotlink v okně Výstup Visual Studia, který vypadá podobně jako "připojení k `http://localhost/WebApplicationFolderName...`". Můžete stisknutím klávesy CTRL a klikněte na odkaz a otevřete stránku prohlížeče v sadě Visual Studio, chcete-li zobrazit strukturu adresářů služby.

     Pokud nelze přejít na web, může, protože adresář prohlížeči není povoleno ve službě IIS. Postupujte podle tipy v části "Věcí můžete zkusit", aby je. Alternativně můžete přímo zadat `http://localhost/WebApplicationFolderName/ProjectName.ServiceName.svc` zobrazíte stránku vaší služby.

Můžete použít **publikovat** k určení, pokud chcete zkopírovat sestavení, konfiguraci a souboru .svc pro všechny služby, které jsou definované v projektu do cílového umístění a přepsat existující soubory v cílovém umístění.

Pokud budete chtít nasadit aplikaci do místní služby IIS, může dojít k chyby související s instalací služby IIS. Ujistěte se prosím, že je správně nainstalována služba IIS. Můžete zadat `http://localhost` v adresním řádku prohlížeče a mohli zkontrolovat, jestli se výchozí stránka služby IIS se zobrazí. V některých případech může být způsobeno za nevhodný registrace technologie ASP.NET nebo WCF v IIS také problémy. Můžete otevřít Developer Command Prompt pro sadu Visual Studio a spusťte příkaz `aspnet_regiis.exe -ir` opravit potíže s registrací technologie ASP.NET nebo spusťte příkaz `ServiceModelReg.exe –ia` Chcete-li vyřešit potíže s registrací WCF.

## <a name="files-generated-for-publishing"></a>Soubory vytvořené pro publikování
 Před knihovny služby WCF hostované webové, pomocí nástroje jsou generovány následující soubory: soubory sestavení, soubor Web.config a souboru SVC. Všechny soubory se zkopírují do cílového umístění. Služba se potom zveřejní.

### <a name="assembly-files"></a>Soubory sestavení
 Při publikování služby WCF pomocí tohoto nástroje, služba se automaticky sestaveny jako první a soubory sestavení jsou vygenerovány v projektu služby po sestavení.

### <a name="svc-file"></a>. Soubor SVC File
 Operaci publikování generuje soubor *.svc pro každou službu WCF, zda soubor existuje nebo Ne, aby platnost verze. Existují dva různé typy souborů svc: jeden pro knihovny služby WCF a knihovna služby syndikace a jinou pro sekvenční a knihovna služby pracovního postupu stavu počítače. Vygenerovaný \*.svc soubor je zkopírován do kořenové složky v cílovém umístění.

### <a name="webconfig-file"></a>Web.config File
 Pokaždé, když do určité cílové umístění publikování projektu služby se vytvoří soubor Web.config.

 Vygenerovaný soubor Web.config obsahuje webové části, které jsou užitečné pro hostování webů a obsahu souboru App.config pro knihovnu služby WCF s následujícími změnami:

- Základní adresa je vyloučený.

- V nastavení `<diagnostics>` element jsou vyloučeny zachovat nastavení trasování cílové platformy.

## <a name="publishing-wcf-services-with-non-http-bindings-to-iis"></a>Publikování služby WCF pomocí protokolu HTTP vazby služby IIS
 Pokud používáte IIS 7.0 nebo novější, můžete publikovat služby WCF s jiným protokolem než HTTP vazby služby IIS. Budete muset provést některé před konfigurací. Další informace najdete v tématu témat na [hostování v aktivační službě procesů Windows](../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).

## <a name="security"></a>Zabezpečení
 Publikování do místní služby IIS vyžaduje oprávnění správce, protože služba IIS vyžaduje spuštěné v účtu správce. Pokud se uživatel bez oprávnění správce spustí publikování služby WCF, služba IIS není k dispozici jako cílové umístění. Publikování v systému souborů nebo FTP funguje bez oprávnění správce.

## <a name="see-also"></a>Viz také:

- [Šablony sady Visual Studio pro WCF](../../../docs/framework/wcf/wcf-vs-templates.md)
- [Hostitel služby WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
- [Testovací klient WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)