---
title: "Publikování služby WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c806b253-cd47-4b96-b831-e73cbf08808f
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 526544118432eb263cc856931d9f4943b9918d93
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-service-publishing"></a>Publikování služby WCF
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]Služba publikování vám usnadní pokročíte z časná vývojového prostředí poskytované [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hostitele služby a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] testovacího klienta ve skutečnosti nasazení aplikace do produkčního prostředí pro účely testování. Než provedete na plán konečné nasazení, můžete použít [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] službu publikování ověřte, že vaše [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služba provádí správně a je připravena k publikování. Můžete také nasadit vaší [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby knihovny na různé cílové umístění pro testování.  
  
## <a name="supported-services-and-target-locations"></a>Podporované služby a cílové umístění  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Služba publikování podporuje publikování [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby vytvořené z sady [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] knihovna šablon služeb a jejich odpovídající šablony položek, které zahrnují následující:  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Šablona služby knihovny pomocí šablony položky.  
  
-   Knihovna syndikace Service.  
  
 Tyto šablony služby můžete najít tak, že zvolíte **soubor** -> **nový projekt** -> **jazyka Visual Basic** nebo **Visual C#**  ->  **WCF**. Pro další šablony WCF v tomto umístění (včetně aplikace pracovního postupu služby WCF a aplikace služby WCF) můžete publikovat pomocí [jedním kliknutím publikování pro webové aplikace](https://msdn.microsoft.com/en-us/library/dd465337\(v=vs.110\).aspx).  
  
 Služby mohou být publikovány do následujícího umístění target.  
  
-   Místní služba IIS.  
  
-   Systém souborů.  
  
-   Server FTP.  
  
## <a name="using-wcf-service-publishing"></a>WCF pomocí publikování služby  
 Proveďte následující kroky k nasazení implementace služby:  
  
1.  Otevřete Visual Studio se zvýšeným oprávněním (klikněte pravým tlačítkem na spustitelný soubor a spusťte ji pomocí "Spustit jako správce").  Pokud používáte službu IIS 7.0 nebo novější, ujistěte se, že jste nainstalovali pomocí součásti "Kompatibilita metabáze služby IIS a služby IIS 6 konfigurace" ", nebo vypnout funkce systému Windows" v Ovládacích panelech.  
  
2.  Otevřete projekt služby, vyberte **sestavení**->**publikovat \<název projektu >** z hlavní nabídky, nebo klikněte pravým tlačítkem na projekt v **Průzkumníku řešení**a klikněte na tlačítko **publikovat**.  
  
3.  **Publikovat** se zobrazí v okně. Klikněte **...** . Zadejte cílové umístění, které byste měli nasadit službu do tlačítko. Můžete vybrat k nasazení aplikace do místní služby IIS, systém souborů nebo serveru FTP. Pokud nasazení aplikace do místní služby IIS, můžete vybrat svůj web a kliknutím na vytvořit webovou aplikaci v části, **vytvořit novou webovou aplikaci** ikonu v pravém horním rohu.  
  
4.  Po kliknutí na tlačítko **publikovat** v hlavním okně Visual Studio nasadí aplikaci do zadané cílové umístění a zkopíruje soubory Web.config, .svc a sestavení do cílový adresář. . Název .svc bude "ProjectName.ServiceName.svc". Po službu úspěšně publikována, naleznete v okně výstupu Visual Studio, která vypadá podobně jako "Připojení k HYPERLINK"http://localhost/WebApplicationFolderName"http://localhost/WebApplicationFolderName..." hotlink. Můžete, stiskněte klávesu CTRL a klikněte na odkaz, otevře se stránka prohlížeče v sadě Visual Studio zobrazíte strukturu adresáře služby.  
  
     Pokud nelze přejděte na web, může to, protože directory prohlížeč není povolena ve službě IIS. Postupujte podle tipy v části "Věcí můžete zkusit" povolit. Alternativně můžete přímo zadat"HYPERLINK"http://localhost/WebApplicationFolderName"http://localhost/WebApplicationFolderName/ProjectName.ServiceName.svc" Chcete-li zobrazit stránku služby.  
  
 Můžete použít **publikovat** zadat, pokud chcete zkopírovat sestavení, konfiguraci a soubor .svc pro všechny služby, které jsou definované v projektu do cílového umístění a přepsat existující soubory v cílovém umístění.  
  
 Pokud si zvolíte pro nasazení aplikace do místní služby IIS, se může zobrazit chyby týkající se instalace služby IIS. Zkontrolujte, zda je služba IIS správně nainstalován. Můžete zadat "HYPERLINK"http://localhost"http://localhost" v prohlížeči a zkontrolujte, zda se zobrazuje výchozí stránka služby IIS, protože.  V některých případech může být způsobeno problémy pomocí technologie ASP.NET nebo [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] nesprávné registrace ve službě IIS. Otevřete příkazový řádek sady Visual Studio a spusťte příkaz "aspnet_regiis.exe - ir" o vyřešení problémů s registrací ASP.NET nebo spusťte příkaz "ServiceModelReg.exe – ia" na opravu WCF registrace problémy.  
  
## <a name="files-generated-for-publishing"></a>Soubory vytvořené pro publikování  
 Před [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] knihovna service může být Web hostovaný, tyto soubory jsou generovány nástrojem: soubory sestavení, soubor Web.config a .svc soubor. Všechny soubory se zkopírují do cílového umístění. Služba je pak publikován.  
  
### <a name="assembly-files"></a>Soubory sestavení  
 Při publikování [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby pomocí tohoto nástroje, služba je zpoplatněna automaticky nejprve a soubory sestavení jsou generovány v projektu služby po sestavení.  
  
### <a name="svc-file"></a>. Soubor SVC  
 Operaci publikování vygeneruje pro každý soubor *.svc [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby, zda soubor existuje nebo Ne, aby platnosti verze. Existují dva různé typy souborů svc: jeden pro [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] knihovny služby a knihovna syndikace Service a další pro sekvenční a stav počítače pracovního postupu služby knihovny. Generovaný objekt \*.svc soubor zkopírován do kořenové složky v cílovém umístění.  
  
### <a name="webconfig-file"></a>Soubor Web.config  
 Pokaždé, když pro konkrétní cílové umístění, publikování projektu služby se vytvoří soubor Web.config.  
  
 Vygenerovaný soubor Web.config obsahuje webové části, které jsou užitečné pro hostování webů a obsah souboru App.config pro [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] knihovny služby s následujícími změnami:  
  
-   Základní adresa je vyloučen.  
  
-   Nastavení v `<diagnostics>` element nevylučují Pokud chcete zachovat nastavení trasování cílové platformy.  
  
## <a name="publishing-wcf-services-with-non-http-bindings-to-iis"></a>Publikování služby WCF s HTTP vazby služby IIS  
 Pokud používáte IIS 7.0 nebo novější, můžete publikovat [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby s jiným protokolem než HTTP vazby do služby IIS. Budete muset provést některé předběžné konfigurace. Další informace najdete v tématech v [hostování v aktivační službě procesů systému Windows](../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
## <a name="security"></a>Zabezpečení  
 Publikování do místní služby IIS vyžaduje oprávnění správce, protože služba IIS vyžaduje spuštění v účtu správce. Pokud uživatel bez oprávnění správce otevře [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] publikování služby, služby IIS není k dispozici jako cílové umístění. Publikování v systému souborů nebo server FTP funguje bez oprávnění správce.  
  
## <a name="see-also"></a>Viz také  
 [Šablony sady Visual Studio WCF](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [Hostitel služby WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [Testovacího klienta WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
