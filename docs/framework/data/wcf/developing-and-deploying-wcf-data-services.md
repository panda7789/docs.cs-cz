---
title: "Vývoj a nasazení služby WCF Data Services"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- deploying [WCF Data Services
- developing applications [WCF Data Services]
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 87a074b96583f44e8655c9efde145e28b490f6e9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="developing-and-deploying-wcf-data-services"></a>Vývoj a nasazení služby WCF Data Services
Toto téma obsahuje informace o vývoji a nasazení [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Pro další základní informace o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], najdete v části [Začínáme](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md) a [přehled](../../../../docs/framework/data/wcf/wcf-data-services-overview.md).  
  
## <a name="developing-wcf-data-services"></a>Vývoj služeb WCF Data Services  
 Při použití [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] k vytvoření služby data, která podporuje [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)], proveďte následující úkoly základní během vývoje:  
  
1.  **Definují model dat**  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]podporuje celou řadu dat poskytovatelé služeb, které umožňují definovat datový model na základě dat z různých zdrojů dat, z relační databáze pozdní vazbou datové typy. Další informace najdete v tématu [zprostředkovatelé dat služby](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).  
  
2.  **Vytvoření datové služby**  
  
     Službu nejzákladnější data zpřístupní třídu, která dědí z <xref:System.Data.Services.DataService%601> třídy s typem `T` který je obor názvů kvalifikovaný název kontejneru entit. Další informace najdete v tématu [definování datových služeb WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).  
  
3.  **Konfigurovat službu data**  
  
     Ve výchozím nastavení [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zakáže přístup k prostředkům, které jsou vystavené kontejner entity. <xref:System.Data.Services.DataServiceConfiguration> Rozhraní umožňuje konfigurovat přístup k prostředkům a služby operations, zadejte podporovanou verzi [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]a definování jiného chování celé služby, jako je například dávkování chování nebo maximální počet entit, které můžete Vrátí se odpověď o jedné informačního kanálu. Další informace najdete v tématu [konfigurace službu Data](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
 Toto téma obsahuje primárně vývoj a nasazení služeb dat pomocí [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]. Informace o flexibilitu poskytované [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] pro vystavení data podle [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informační kanály, najdete v části [definování datových služeb WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).  
  
### <a name="choosing-a-development-web-server"></a>Výběr vývojového webového serveru  
 Pokud vyvíjíte WCF Data Service jako [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace nebo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webu pomocí [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], máte možnost volby webových serverů, na který se má spustit službu data během vývoje. Integrovat následujících webových serverů [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] aby bylo snazší pro testování a ladění vaše datové služby v místním počítači.  
  
1.  **Místní služba IIS serveru**  
  
     Při vytváření datové služby, který je [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace nebo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webu, který běží na Internetové informační služby (IIS), doporučujeme vývoj a testování vaší služby dat pomocí služby IIS v místním počítači. Spuštění datové služby ve službě IIS usnadňuje sledování požadavků HTTP během ladění. Zároveň vám to umožňuje předem stanovit práva, jež služba IIS potřebuje pro přístup k souborům, databázím a jiným prostředkům vyžadovaným datovou službou. Pokud chcete spustit službu vaše data ve službě IIS, je nutné je zajištěno, že obě služby IIS a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] jsou správně nainstalována a nakonfigurována a udělení přístupu k účtům služby IIS v systému souborů a databáze. Další informace najdete v tématu [postup: vývoj WCF Data Service spuštěna ve službě IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).  
  
    > [!NOTE]
    >  Je nutné spustit [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] s právy správce umožňující vývoj prostředí tak, aby konfigurovat místní server služby IIS.  
  
2.  **Vývojový Server sady Visual Studio**  
  
     [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]zahrnuje integrovaného webového serveru, [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] vývojový Server, který je výchozí webový server pro [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projekty. Tento webový server je určená ke spuštění [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projekty v místním počítači během vývoje. [Rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) ukazuje, jak vytvořit službu data, která běží v [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] vývojový Server.  
  
     Byste měli vědět o následujících omezeních při použití [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] vývojový Server k vývoji službu data:  
  
    -   Tento server je přístupný pouze v místním počítači.  
  
    -   Tento server naslouchá na `localhost` a na konkrétní port, nikoli na portu 80, což je výchozí port pro zprávy HTTP. Další informace najdete v tématu [webové servery v sadě Visual Studio pro webové projekty ASP.NET](http://msdn.microsoft.com/en-us/31d4f588-df59-4b7e-b9ea-e1f2dd204328).  
  
    -   Tento server spouští datovou službu v kontextu aktuálního uživatelského účtu. Například, pokud používáte jako uživatel s právy na úrovni správce dat služby spuštěné [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] vývojový Server bude mít oprávnění na úrovni správce. To může vést k tomu, že datová služba bude mít přístup k prostředkům, ke kterým nemá při nasazení na server služby IIS přístupová práva.  
  
    -   Tento server neobsahuje nadstandardní funkce služby IIS, jako je například ověřování.  
  
    -   Tento server nemůže zpracovat bloku HTTP datové proudy, které jsou odesílány být výchozím [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klienta při přístupu k velké binární data ze služby data. Další informace najdete v tématu [streamování zprostředkovatele](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).  
  
    -   Tento server má problémy se zpracováním období (`.`) znaků v adrese URL, i když tento znak podporuje [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] v klíčové hodnoty.  
  
    > [!TIP]
    >  I když můžete použít [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] vývojový Server k otestování dat služby během vývoje, měli byste otestovat znovu po nasazení na webový server se službou IIS.  
  
3.  **Windows Azure vývojové prostředí**  
  
     Nástroje systému Windows Azure pro [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] zahrnuje integrovaná sada nástrojů pro vývoj služby Windows Azure v [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]. Pomocí těchto nástrojů můžete vyvíjet datové služby, které lze nasazovat na platformě Azure, a před nasazením je otestovat v místním počítači. Pomocí těchto nástrojů při použití [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] vyvíjet datové služby, který běží na platformě Windows Azure. Nástroje systému Windows Azure pro si můžete stáhnout [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=201848). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]vývoj služba dat, která běží na systému Windows Azure, najdete v příspěvku [nasazení služby OData v systému Windows Azure](http://go.microsoft.com/fwlink/?LinkId=201847).  
  
### <a name="development-tips"></a>Tipy pro vývoj  
 Při vývoji datových služeb je vhodné zvážit následující faktory:  
  
-   Určete požadavky na zabezpečení datové služby a to, zda chcete uživatele ověřovat nebo omezit přístup pro konkrétní uživatele. Další informace najdete v tématu [zabezpečení služby WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).  
  
-   Při ladění datové služby může být velmi užitečný kontrolní program HTTP, který umožňuje kontrolovat obsah zpráv požadavků a odpovědí. K inspekci požadavků HTTP a odpovědí z datové služby lze využít jakýkoli síťový analyzátor paketů, který zobrazuje surové pakety.  
  
-   Při ladění datové služby může být užitečné získat o chybě z datové služby více informace než v běžném provozu. Další informace o chybě můžete získat od služby data podle nastavení <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> vlastnost v <xref:System.Data.Services.DataServiceConfiguration> k `true` a nastavením <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> vlastnost <xref:System.ServiceModel.Description.ServiceDebugBehavior> atribut na data služby třídu `true`. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]v příspěvku [ladění služby WCF Data Services](http://go.microsoft.com/fwlink/?LinkId=201868). Můžete také povolit trasování v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zobrazíte výjimek vyvolaných ve vrstvě zasílání zpráv protokolu HTTP. Další informace najdete v tématu [Konfigurace trasování](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).  
  
-   Datové služby je obvykle vyvinutý jako [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projekt aplikace, ale můžete také vytvořit je služba data jako [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webový projekt v [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]. Informace o rozdílech mezi těmito dvěma typy projektů najdete v tématu [NIB: projekty webových aplikací a webových projektů v sadě Visual Studio](http://msdn.microsoft.com/en-us/2861815e-f5a2-4378-a2f8-b8a86dc012f5).  
  
-   Při vytváření datové služby pomocí **přidat novou položku** dialogovém okně [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], hostitelem je služba data [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ve službě IIS. Při [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] a služby IIS je výchozího hostitele pro datové služby, jsou podporovány další možnosti hostování. Další informace najdete v tématu [hostující službu Data](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md).  
  
## <a name="deploying-wcf-data-services"></a>Nasazení služeb WCF Data Services  
 Služba WCF Data Service nabízí flexibilitu při výběru procesu, který je hostitelem datové služby. Můžete použít [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] nasazení služby data na následujících platformách:  
  
-   **Hostované službou IIS webový Server**  
  
     Když je služba data vyvinutý jako [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektu, mohou být nasazeny na webovém serveru IIS pomocí standardní [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] procesů nasazení.  [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]poskytuje následující technologie nasazení pro [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], v závislosti na druhu systému [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projekt, který hostuje službu dat, kterou nasazujete.  
  
    -   **Technologie nasazení pro webové aplikace ASP.NET**  
  
        -   [Balíčku pro nasazení webu](http://msdn.microsoft.com/en-us/1f9713c8-9540-494c-b80d-9893b970ad6f)  
  
        -   [Publikování jedním kliknutím](http://msdn.microsoft.com/en-us/59226246-99ad-4aec-975d-7c61e8a8911c)  
  
    -   **Nasazení technologie pro weby technologie ASP.NET**  
  
        -   [Zkopírujte nástroj webu](http://msdn.microsoft.com/library/b819aed4-014b-427e-be80-02317b1bb003)  
  
        -   [Publikování webu nástroje](http://msdn.microsoft.com/library/d0a1a20f-15be-4940-9485-cb8e4aa8181b)  
  
        -   [XCopy](http://msdn.microsoft.com/library/4312c651-2119-49be-bbeb-ee28bdbfe71e)  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Možnosti nasazení pro [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace, najdete v části [Přehled nasazení webu pro Visual Studio a ASP.NET](http://msdn.microsoft.com/en-us/99bd1927-b59f-4e02-87b4-55c6ba2adbc3).  
  
    > [!TIP]
    >  Než datovou službu nasadíte do služby IIS, nezapomeňte otestovat nasazení na webový server, na kterém je spuštěna služba IIS. Další informace najdete v tématu [postup: vývoj WCF Data Service spuštěna ve službě IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).  
  
-   **Windows Azure**  
  
     Datové služby můžete nasadit do systému Windows Azure pomocí nástroje Windows Azure pro [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]. Nástroje systému Windows Azure pro si můžete stáhnout [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=201848). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]nasazení služby data do služby Windows Azure, najdete v příspěvku [nasazení služby OData v systému Windows Azure](http://go.microsoft.com/fwlink/?LinkId=201847).  
  
### <a name="deployment-considerations"></a>Důležité informace o nasazení  
 Při nasazování datových služeb je vhodné zvážit následující faktory:  
  
-   Pokud nasadíte službu data, která používá [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] zprostředkovatele pro přístup k databázi SQL serveru, budete také muset rozšířit datové struktury, data, nebo obě s daty nasazení služby. [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]umožňuje automatické vytvoření skriptů (soubory .sql) k tomu v cílové databázi, a tyto skripty může být zahrnutý v balíčku pro nasazení webu z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace. Další informace najdete v tématu [NIB: postupy: nasazení databáze s projekt webové aplikace](http://msdn.microsoft.com/en-us/683b33f1-8a3d-45cf-af6e-61ab50fc518b). Pro [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webu, můžete to provedete pomocí **Průvodce publikováním databáze** v [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]. Další informace najdete v tématu [nasazení databáze pomocí Průvodce publikováním databáze](http://msdn.microsoft.com/library/1e3682e7-8b57-4da6-a393-af9640ccf8b7).  
  
-   Protože [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] obsahuje základní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementace, můžete použít Windows Server AppFabric monitorovat datové služby nasadit do IIS a běžící v systému Windows Server. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]pomocí sledování na data služby Windows Server AppFabric najdete v příspěvku [sledování služby WCF Data Services s Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=202005).  
  
## <a name="see-also"></a>Viz také  
 [Hostující službu Data](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)  
 [Zabezpečení součásti WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 [Definování datových služeb WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
