---
title: Vývoj a nasazení služeb WCF Data Services
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- deploying [WCF Data Services
- developing applications [WCF Data Services]
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
ms.openlocfilehash: a3eaea7218b3226fde43aa76bbafe602fc198947
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329320"
---
# <a name="develop-and-deploy-wcf-data-services"></a>Vývoj a nasazení služeb WCF Data Services

Toto téma obsahuje informace o vývoji a nasazení služeb WCF Data Services. Obecnější informace o služeb WCF Data Services najdete v tématu [Začínáme](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md) a [přehled](../../../../docs/framework/data/wcf/wcf-data-services-overview.md).

## <a name="develop-wcf-data-services"></a>Vývoj služeb WCF Data Services

Při použití služby WCF Data Services k vytvoření datové služby, který podporuje [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)], je třeba během vývoje provést následující základní kroky:

1. **Definování datového modelu**

     WCF Data Services podporuje řadu poskytovatelů datových služeb, které vám umožňují definovat datový model založený na datech z různých zdrojů dat, od relačních databází s pozdní vazbou datové typy. Další informace najdete v tématu [zprostředkovatelé dat služby](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).

2. **Vytvoření datové služby**

     Nejzákladnější datová služba zpřístupní třídu, která dědí z <xref:System.Data.Services.DataService%601> třídy s typem `T` , který je kvalifikovaný v oboru názvů názvu kontejneru entity. Další informace najdete v tématu [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).

3. **Konfigurace datové služby**

     Ve výchozím nastavení služby WCF Data Services zakáže přístup k prostředkům, které jsou vystaveny kontejnerem entity. <xref:System.Data.Services.DataServiceConfiguration> Rozhraní umožňuje konfigurovat přístup k prostředkům a operacím služby, zadat podporovanou verzi protokolu OData a definovat další chování v rámci služeb, například chování dávek nebo maximální počet entit, které mohou být vráceny. v informačním kanálu jednu odpověď. Další informace najdete v tématu [konfigurace datové služby](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).

Toto téma popisuje zejména vývoji a nasazení datových služeb pomocí sady Visual Studio. Informace o flexibilitě, kterou služba WCF Data Services pro vystavení dat jako k datovým kanálům OData najdete v tématu [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).

### <a name="choose-a-development-web-server"></a>Zvolte vývojovému webovému serveru

Při vývoji datových služeb WCF jako [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace nebo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webu pomocí sady Visual Studio 2015, máte možnost volby z webových serverů, na kterém chcete datovou službu spouštět během vývoje. Integrovány následující webové servery pomocí sady Visual Studio, aby bylo snazší pro testování a ladění datových služeb v místním počítači.

1. **Místní server IIS**

     Při vytváření datových služeb je [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace nebo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webovou stránku, na kterém běží v Internetové informační služby (IIS), doporučujeme ji vyvíjet a testovat pomocí služby IIS v místním počítači. Spuštění datové služby ve službě IIS usnadňuje sledování požadavků HTTP během ladění. Zároveň vám to umožňuje předem stanovit práva, jež služba IIS potřebuje pro přístup k souborům, databázím a jiným prostředkům vyžadovaným datovou službou. Ke spuštění datové služby ve službě IIS, musí je zajištěno, že služba IIS a služby Windows Communication Foundation (WCF) jsou správnost instalace a konfigurace a udělit přístup k účtům služby IIS v systému souborů a databáze. Další informace najdete v tématu [jak: Vývoj datové služby WCF ve službě IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).

    > [!NOTE]
    > Visual Studio je nutné spustit s právy správce, chcete-li povolit ve vývojovém prostředí konfiguraci místního serveru služby IIS.

2. **Vývojový server sady Visual Studio**

     Visual Studio zahrnuje vestavěný webový server, Server sady Visual Studio vývoje, což je výchozí webový server pro [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projekty. Tento webový server je navržen pro spouštění [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projekty v místním počítači během vývoje. [Rychlý start služeb WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) ukazuje, jak vytvořit datových služeb běžících v vývojový Server sady Visual Studio.

     Byste měli vědět o následujících omezeních při použití vývojového serveru sady Visual Studio pro vývoj datové služby:

    -   Tento server je přístupný pouze v místním počítači.

    -   Tento server naslouchá na `localhost` a na určitém portu, nikoli na portu 80, který je výchozím portem pro zprávy protokolu HTTP. Další informace najdete v tématu [webové servery v sadě Visual Studio pro webové projekty ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/58wxa9w5(v=vs.120)).

    -   Tento server spouští datovou službu v kontextu aktuálního uživatelského účtu. Například pokud používáte jako uživatel s právy na úrovni správce, datová služba spuštěná na vývojový Server sady Visual Studio bude mít oprávnění na úrovni správce. To může vést k tomu, že datová služba bude mít přístup k prostředkům, ke kterým nemá při nasazení na server služby IIS přístupová práva.

    -   Tento server neobsahuje nadstandardní funkce služby IIS, jako je například ověřování.

    -   Tento server nedokáže zpracovávat blokové datové proudy HTTP, které se odesílají být klient datové služby WCF ve výchozím nastavení při přístupu k velkému objemu binárních dat z datové služby. Další informace najdete v tématu [streamování poskytovatele](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).

    -   Tento server má potíže se zpracováním teček (`.`) znaků v adrese URL, přestože je tento znak v hodnotách klíčů podporován služeb WCF Data Services.

    > [!TIP]
    > I když vývojový Server sady Visual Studio můžete použít k otestování svých datových služeb během vývoje, je však vhodné služby otestovat znovu po nasazení na webový server, na kterém běží služby IIS.

3. **Vývojové prostředí Azure**

     Windows Azure Tools for Visual Studio zahrnuje integrovanou sadu nástrojů pro vývoj služeb Windows Azure v sadě Visual Studio. Pomocí těchto nástrojů můžete vyvíjet datové služby, které lze nasazovat na platformě Azure, a před nasazením je otestovat v místním počítači. Tyto nástroje využijete při vývoji datových služeb, na kterém běží na platformě Windows Azure pomocí sady Visual Studio. Nástroje Windows Azure pro Visual Studio z můžete stáhnout [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkID=201848). Další informace o vývoji datových služeb, který běží na Windows Azure, najdete v příspěvku [nasazení služby OData na platformě Windows Azure](https://go.microsoft.com/fwlink/?LinkId=201847).

### <a name="development-tips"></a>Tipy pro vývoj

Při vývoji datových služeb je vhodné zvážit následující faktory:

-   Určete požadavky na zabezpečení datové služby a to, zda chcete uživatele ověřovat nebo omezit přístup pro konkrétní uživatele. Další informace najdete v tématu [zabezpečení služeb WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).

-   Při ladění datové služby může být velmi užitečný kontrolní program HTTP, který umožňuje kontrolovat obsah zpráv požadavků a odpovědí. K inspekci požadavků HTTP a odpovědí z datové služby lze využít jakýkoli síťový analyzátor paketů, který zobrazuje surové pakety.

-   Při ladění datové služby, můžete získat další informace o chybě z datové služby než při běžném provozu. Můžete získat další informace o chybě z datové služby tak, že nastavíte <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> vlastnost v <xref:System.Data.Services.DataServiceConfiguration> k `true` a nastavením <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> vlastnost <xref:System.ServiceModel.Description.ServiceDebugBehavior> atribut ve třídě datové služby na `true`. Další informace najdete v příspěvku [ladění služeb WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=201868). Můžete také povolit trasování ve službě WCF a zobrazit výjimky vyvolané ve vrstvě zasílání zpráv protokolu HTTP. Další informace najdete v tématu [Konfigurace trasování](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).

-   Datové služby se obvykle vyvíjí jako [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projekt aplikace, ale můžete také vytvořit jako [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webový projekt v sadě Visual Studio. Informace o rozdílech mezi těmito dvěma typy projektů naleznete v tématu [Web Application Projects versus webových projektů v sadě Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd547590(v=vs.110)).

-   Při vytváření datové služby pomocí **přidat novou položku** dialogové okno v sadě Visual Studio, datové služby je hostitelem [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ve službě IIS. Zatímco [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] a služby IIS jsou výchozími hostiteli datové služby, jsou podporována další možnosti hostování. Další informace najdete v tématu [hostitelem datové služby](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md).

## <a name="deploy-wcf-data-services"></a>Nasazení služeb WCF Data Services

Služba WCF Data Service nabízí flexibilitu při výběru procesu, který je hostitelem datové služby. Visual Studio můžete použít k nasazení datové služby na následujících platformách:

-   **Webový server hostovaný ve službě IIS**

     Když datové služby je mimo jiné vyvinuto [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektu, dá se nasadit na webovém serveru IIS s využitím standardu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] procesů nasazení.  Visual Studio poskytuje následující technologie nasazení pro [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], v závislosti na typu z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektu, který je hostitelem datové služby, kterou nasazujete.

    -   **Technologie nasazení pro webové aplikace ASP.NET**

        -   [Postupy: Vytvoření balíčku pro nasazení webu v sadě Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd465323(v=vs.110))

        -   [Postupy: Nasazení webového projektu pomocí jedním kliknutím publikovat v sadě Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd465337(v=vs.110))

    -   **Technologie nasazení pro weby ASP.NET**

        -   [Postupy: Zkopírujte soubory webu pomocí nástroje pro kopírování webu](https://docs.microsoft.com/previous-versions/aspnet/c95809c0(v=vs.100))

        -   [Postupy: Publikování webů](https://docs.microsoft.com/previous-versions/aspnet/20yh9f1b(v=vs.100))

        -   [Návod: Nasazení webové aplikace ASP.NET pomocí příkazu XCOPY](https://docs.microsoft.com/previous-versions/aspnet/f735abw9(v=vs.100))

     Další informace o možnostech nasazení pro [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace, najdete v článku [Přehled nasazení webu pro Visual Studio a ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/dd394698(v=vs.110)).

    > [!TIP]
    > Než datovou službu nasadíte do služby IIS, nezapomeňte otestovat nasazení na webový server, na kterém je spuštěna služba IIS. Další informace najdete v tématu [jak: Vývoj datové služby WCF ve službě IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).

-   **Microsoft Azure**

     Datové služby Windows Azure můžete nasadit pomocí nástroje Windows Azure pro sadu Visual Studio. Nástroje Windows Azure pro Visual Studio z můžete stáhnout [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkID=201848). Další informace o nasazení datových služeb Windows Azure, najdete v příspěvku [nasazení služby OData na platformě Windows Azure](https://go.microsoft.com/fwlink/?LinkId=201847).

### <a name="deployment-considerations"></a>Důležité informace o nasazení

Při nasazování datových služeb je vhodné zvážit následující faktory:

-   Při nasazování datových služeb používá [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] zprostředkovatele pro přístup k databázi SQL serveru, budete také muset datové struktury, data, nebo i s vašimi daty nasazení služby. Visual Studio může automaticky vytvářet skripty (soubory .sql) k tomu v cílové databázi, a tyto skripty mohou být součástí balíčku pro nasazení webu z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace. Další informace najdete v tématu [jak: Nasazení databáze se projekt webové aplikace](https://docs.microsoft.com/previous-versions/dd465343(v=vs.100)). Pro [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webu, Uděláte to tak pomocí **Database Publishing Wizard** v sadě Visual Studio. Další informace najdete v tématu [publikování databáze SQL](https://docs.microsoft.com/previous-versions/aspnet/bb907585(v=vs.100)).

-   Služby WCF Data Services zahrnuje základní implementaci WCF, a proto můžete použít Windows Server AppFabric ke sledování datové služby nasazené ve službě IIS a běžící na Windows serveru. Další informace o používání služby Windows Server AppFabric ke sledování datové služby, najdete v příspěvku [sledování služeb WCF Data Services pomocí služby Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=202005).

## <a name="see-also"></a>Viz také:

- [Hostování datové služby](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)
- [Zabezpečení datových služeb WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)
- [Definování datových služeb WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
