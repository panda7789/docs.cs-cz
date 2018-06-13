---
title: Publikování služby WCF
ms.date: 03/30/2017
ms.assetid: c806b253-cd47-4b96-b831-e73cbf08808f
ms.openlocfilehash: 258c7e65b69648477e58880f35b100a9378dc9c0
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806458"
---
# <a name="wcf-service-publishing"></a>Publikování služby WCF
Publikování služby Windows Communication Foundation (WCF) usnadňuje pokročíte z časná vývojového prostředí, ve skutečnosti nasazení aplikace do produkčního prostředí pro účely testování poskytované hostitel služby WCF a testovacího klienta WCF. Před potvrzením plán konečné nasazení, můžete pro publikování služby Windows Communication Foundation (WCF) ověřte, zda služby WCF provede správně a je připravena k publikování. Můžete také nasadit knihovnách služby WCF na různé cílové umístění pro testování.  
  
## <a name="supported-services-and-target-locations"></a>Podporované služby a cílové umístění  
 Publikování služby WCF podporuje publikování služby WCF vytvořené ze sady šablony knihoven služby WCF a jejich odpovídající šablony položky, které zahrnují následující:  
  
-   Šablona knihovny služby WCF pomocí šablony položky.  
  
-   Knihovna syndikace Service.  
  
 Tyto šablony služby můžete najít tak, že zvolíte **soubor** -> **nový projekt** -> **jazyka Visual Basic** nebo **Visual C#**  ->  **WCF**. Pro další šablony WCF v tomto umístění (včetně aplikace pracovního postupu služby WCF a aplikace služby WCF) můžete publikovat pomocí [jedním kliknutím publikování pro webové aplikace](https://msdn.microsoft.com/library/dd465337\(v=vs.110\).aspx).  
  
 Služby mohou být publikovány do následujícího umístění target.  
  
-   Místní služba IIS.  
  
-   Systém souborů.  
  
-   Server FTP.  
  
## <a name="using-wcf-service-publishing"></a>WCF pomocí publikování služby  
 Proveďte následující kroky k nasazení implementace služby:  
  
1.  Otevřete Visual Studio se zvýšeným oprávněním (klikněte pravým tlačítkem na spustitelný soubor a spusťte ji pomocí "Spustit jako správce").  Pokud používáte službu IIS 7.0 nebo novější, ujistěte se, že jste nainstalovali pomocí součásti "Kompatibilita metabáze služby IIS a služby IIS 6 konfigurace" ", nebo vypnout funkce systému Windows" v Ovládacích panelech.  
  
2.  Otevřete projekt služby, vyberte **sestavení**->**publikovat \<název projektu >** z hlavní nabídky, nebo klikněte pravým tlačítkem na projekt v **Průzkumníku řešení**a klikněte na tlačítko **publikovat**.  
  
3.  **Publikovat** se zobrazí v okně. Klikněte **...** . Zadejte cílové umístění, které byste měli nasadit službu do tlačítko. Můžete vybrat k nasazení aplikace do místní služby IIS, systém souborů nebo serveru FTP. Pokud nasazení aplikace do místní služby IIS, můžete vybrat svůj web a kliknutím na vytvořit webovou aplikaci v části, **vytvořit novou webovou aplikaci** ikonu v pravém horním rohu.  
  
4.  Po kliknutí na tlačítko **publikovat** v hlavním okně Visual Studio nasadí aplikaci do zadané cílové umístění a zkopíruje soubory Web.config, .svc a sestavení do cílový adresář. . Název .svc bude "ProjectName.ServiceName.svc". Po službu úspěšně publikována, můžete najít hotlink v okně výstupu Visual Studio, které bude vypadat podobně jako "Připojení k HYPERLINK"http://localhost/WebApplicationFolderName" http://localhost/WebApplicationFolderName ...". Můžete, stiskněte klávesu CTRL a klikněte na odkaz, otevře se stránka prohlížeče v sadě Visual Studio zobrazíte strukturu adresáře služby.  
  
     Pokud nelze přejděte na web, může to, protože directory prohlížeč není povolena ve službě IIS. Postupujte podle tipy v části "Věcí můžete zkusit" povolit. Alternativně můžete přímo zadat"HYPERLINK"http://localhost/WebApplicationFolderName" http://localhost/WebApplicationFolderName/ProjectName.ServiceName.svc" zobrazíte stránku služby.  
  
 Můžete použít **publikovat** zadat, pokud chcete zkopírovat sestavení, konfiguraci a soubor .svc pro všechny služby, které jsou definované v projektu do cílového umístění a přepsat existující soubory v cílovém umístění.  
  
 Pokud si zvolíte pro nasazení aplikace do místní služby IIS, se může zobrazit chyby týkající se instalace služby IIS. Zkontrolujte, zda je služba IIS správně nainstalován. Můžete zadat "HYPERLINK"http://localhost" http://localhost" v prohlížeči a zkontrolujte jestli výchozí stránka služby IIS se zobrazuje, protože.  V některých případech může být také způsobeno problémy pomocí technologie ASP.NET nebo WCF nesprávné registraci ve službě IIS. Otevřete příkazový řádek sady Visual Studio a spusťte příkaz "aspnet_regiis.exe - ir" o vyřešení problémů s registrací ASP.NET nebo spusťte příkaz "ServiceModelReg.exe – ia" na opravu WCF registrace problémy.  
  
## <a name="files-generated-for-publishing"></a>Soubory vytvořené pro publikování  
 Předtím, než knihovny služby WCF můžete hostuje Web, nástroj generované následující soubory: soubory sestavení, soubor Web.config a .svc soubor. Všechny soubory se zkopírují do cílového umístění. Služba je pak publikován.  
  
### <a name="assembly-files"></a>Soubory sestavení  
 Při publikování služby WCF pomocí tohoto nástroje Služba je zpoplatněna automaticky nejprve a soubory sestavení jsou generovány v projektu služby po sestavení.  
  
### <a name="svc-file"></a>. Soubor SVC  
 Operaci publikování generuje soubor *.svc u každé služby WCF, zda soubor existuje nebo Ne, aby platnosti verze. Existují dva různé typy souborů svc: jeden pro knihovny služby WCF a knihovny Service syndikace a další pro sekvenční a knihovny služby pracovního postupu stav počítače. Generovaný objekt \*.svc soubor zkopírován do kořenové složky v cílovém umístění.  
  
### <a name="webconfig-file"></a>Soubor Web.config  
 Pokaždé, když pro konkrétní cílové umístění, publikování projektu služby se vytvoří soubor Web.config.  
  
 Vygenerovaný soubor Web.config obsahuje webové oddíly, které jsou užitečné pro webového hostingu a obsah souboru App.config pro knihovnu služby WCF s následujícími změnami:  
  
-   Základní adresa je vyloučen.  
  
-   Nastavení v `<diagnostics>` element nevylučují Pokud chcete zachovat nastavení trasování cílové platformy.  
  
## <a name="publishing-wcf-services-with-non-http-bindings-to-iis"></a>Publikování služby WCF s HTTP vazby služby IIS  
 Pokud používáte IIS 7.0 nebo novější, můžete publikovat služby WCF s jiným protokolem než HTTP vazby do služby IIS. Budete muset provést některé předběžné konfigurace. Další informace najdete v tématech v [hostování v aktivační službě procesů systému Windows](../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
## <a name="security"></a>Zabezpečení  
 Publikování do místní služby IIS vyžaduje oprávnění správce, protože služba IIS vyžaduje spuštění v účtu správce. Pokud uživatel bez oprávnění správce otevře publikování služby WCF, není k dispozici jako cílové umístění služby IIS. Publikování v systému souborů nebo server FTP funguje bez oprávnění správce.  
  
## <a name="see-also"></a>Viz také  
 [Šablony sady Visual Studio pro WCF](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [Hostitel služby WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [Testovací klient WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
