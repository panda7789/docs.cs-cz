---
title: Vývoj a nasazení služeb WCF Data Services
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- deploying [WCF Data Services
- developing applications [WCF Data Services]
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
ms.openlocfilehash: 61527e51ea4d28cfe4589f6bed32b3c505443c22
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121174"
---
# <a name="develop-and-deploy-wcf-data-services"></a>Vývoj a nasazení datových služeb WCF

Tento článek obsahuje informace o vývoji a nasazování wcf datových služeb. Další základní informace o datových službách WCF naleznete [v tématech Začínáme](getting-started-with-wcf-data-services.md) a [Přehled](wcf-data-services-overview.md).

## <a name="develop-wcf-data-services"></a>Vývoj datových služeb WCF

Při použití wcf datové služby k vytvoření datové služby, která podporuje protokol OData (Open Data Protocol), je nutné provést následující základní úkoly během vývoje:

1. **Definování datového modelu**

     WCF Data Services podporuje řadu poskytovatelů datových služeb, které umožňují definovat datový model založený na datech z různých zdrojů dat, od relačních databází až po datové typy s pozdní vazbou. Další informace naleznete v tématu [Poskytovatelé datových služeb](data-services-providers-wcf-data-services.md).

2. **Vytvoření datové služby**

     Nejzákladnější datová služba zpřístupňuje třídu, která dědí z <xref:System.Data.Services.DataService%601> třídy, s typem, `T` který je název kontejneru entity kvalifikovaným pro obor názvů. Další informace naleznete [v tématu Definování datových služeb WCF](defining-wcf-data-services.md).

3. **Konfigurace datové služby**

     Ve výchozím nastavení WCF data services zakáže přístup k prostředkům, které jsou vystaveny kontejneru entity. Rozhraní <xref:System.Data.Services.DataServiceConfiguration> umožňuje konfigurovat přístup k prostředkům a operacím služby, určit podporovanou verzi OData a definovat další chování pro celou službu, jako je například dávkování chování nebo maximální počet entit, které mohou být vráceny v jednom kanálu odpovědí. Další informace naleznete [v tématu Configuring the Data Service](configuring-the-data-service-wcf-data-services.md).

Tento článek se zabývá především vývoj a nasazení datových služeb pomocí sady Visual Studio. Informace o flexibilitě poskytované službou WCF Data Services pro vystavení dat jako datových kanálů OData naleznete [v tématu Definování datových služeb WCF](defining-wcf-data-services.md).

### <a name="choose-a-development-web-server"></a>Volba vývojového webového serveru

Při vývoji wcf datové služby jako ASP.NET aplikace nebo ASP.NET webu pomocí Sady Visual Studio 2015, máte na výběr z webových serverů, na kterých chcete spustit datovou službu během vývoje. Následující webové servery se integrují se souborem Visual Studio, aby bylo snazší testovat a ladit datové služby v místním počítači.

1. **Místní server služby IIS**

     Pokud vytvoříte datovou službu, která je ASP.NET aplikace nebo ASP.NET webu spuštěného v internetové informační službě (IIS), doporučujeme vyvíjet a testovat datovou službu pomocí služby IIS v místním počítači. Spuštění datové služby ve službě IIS usnadňuje sledování požadavků HTTP během ladění. Zároveň vám to umožňuje předem stanovit práva, jež služba IIS potřebuje pro přístup k souborům, databázím a jiným prostředkům vyžadovaným datovou službou. Chcete-li spustit datovou službu ve službě IIS, musíte zajistit, aby byly služby IIS i WCF (Windows Communication Foundation) správně nainstalovány a nakonfigurovány, a udělit přístup k účtům služby IIS v systému souborů a databázích. Další informace naleznete v [tématu How to: Develop a WCF Data Service Running on IIS](how-to-develop-a-wcf-data-service-running-on-iis.md).

    > [!NOTE]
    > Chcete-li, aby vývojový prostředí bylo možné nakonfigurovat místní server služby IIS, je nutné spustit aplikaci Visual Studio s právy správce.

2. **Vývojový server sady Visual Studio**

     Visual Studio obsahuje integrovaný webový server Visual Studio Development Server, který je výchozím webovým serverem pro ASP.NET projekty. Tento webový server je určen ke spouštění ASP.NET projektů v místním počítači během vývoje. [WCF Data Services rychlý start ukazuje,](quickstart-wcf-data-services.md) jak vytvořit datovou službu, která běží v Visual Studio Development Server.

     Při vývoji datové služby pomocí vývojového serveru Visual Studio byste si měli být vědomi následujících omezení:

    - Tento server je přístupný pouze v místním počítači.

    - Tento server naslouchá `localhost` na konkrétním portu a na konkrétním portu, nikoli na portu 80, což je výchozí port pro zprávy HTTP. Další informace naleznete [v tématu Webové servery v sadě Visual Studio pro ASP.NET webových projektech](https://docs.microsoft.com/previous-versions/aspnet/58wxa9w5(v=vs.120)).

    - Tento server spouští datovou službu v kontextu aktuálního uživatelského účtu. Pokud například používáte jako uživatel na úrovni správce, bude mít datová služba spuštěná na vývojovém serveru sady Visual Studio oprávnění na úrovni správce. To může vést k tomu, že datová služba bude mít přístup k prostředkům, ke kterým nemá při nasazení na server služby IIS přístupová práva.

    - Tento server neobsahuje nadstandardní funkce služby IIS, jako je například ověřování.

    - Tento server nemůže zpracovat blokové datové proudy HTTP, které jsou odesílány jako výchozí klientem služby WCF Data Services při přístupu k velkým binárním datům z datové služby. Další informace naleznete v tématu [Streaming Provider](streaming-provider-wcf-data-services.md).

    - Tento server má problémy`.`se zpracováním znaku tečka ( ) v adrese URL, i když tento znak je podporován WCF datové služby v klíčových hodnot.

    > [!TIP]
    > I když můžete pomocí visual studio development server otestovat datové služby během vývoje, měli byste je otestovat znovu po nasazení na webový server, na který je spuštěna služba IIS.

3. **Vývojové prostředí Windows Azure**

     Nástroje Windows Azure pro Visual Studio obsahují integrovanou sadu nástrojů pro vývoj služeb Windows Azure ve Visual Studiu. Pomocí těchto nástrojů můžete vyvíjet datové služby, které lze nasazovat na platformě Azure, a před nasazením je otestovat v místním počítači. Tyto nástroje použijte při vývoji datové služby, která běží na platformě Windows Azure, pomocí těchto nástrojů. Informace o instalaci nástrojů najdete v [tématu Nástroje Azure pro Visual Studio 2015](../../../azure/sdk/vs2015-install.md). Další informace o vývoji datové služby, která běží ve Windows Azure, najdete v příspěvku [nasazení služby OData ve Windows Azure](https://docs.microsoft.com/archive/blogs/astoriateam/deploying-an-odata-service-in-windows-azure).

### <a name="development-tips"></a>Tipy pro vývoj

Při vývoji datových služeb je vhodné zvážit následující faktory:

- Určete požadavky na zabezpečení datové služby a to, zda chcete uživatele ověřovat nebo omezit přístup pro konkrétní uživatele. Další informace naleznete [v tématu Zabezpečení služby WCF Data Services](securing-wcf-data-services.md).

- Při ladění datové služby může být velmi užitečný kontrolní program HTTP, který umožňuje kontrolovat obsah zpráv požadavků a odpovědí. K inspekci požadavků HTTP a odpovědí z datové služby lze využít jakýkoli síťový analyzátor paketů, který zobrazuje surové pakety.

- Při ladění datové služby můžete chtít získat další informace o chybě z datové služby než během běžného provozu. Další informace o chybě z datové služby můžete <xref:System.Data.Services.DataServiceConfiguration> `true` získat nastavením <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> vlastnosti <xref:System.ServiceModel.Description.ServiceDebugBehavior> v to a `true`nastavením vlastnosti atributu ve třídě datové služby na . Další informace naleznete v příspěvku [Ladění WCF Data Services](https://docs.microsoft.com/archive/blogs/phaniraj/debugging-wcf-data-services). Můžete také povolit trasování v WCF zobrazit výjimky vyvolané ve vrstvě zasílání zpráv HTTP. Další informace naleznete [v tématu Konfigurace trasování](../../wcf/diagnostics/tracing/configuring-tracing.md).

- Datová služba je obvykle vyvinuta jako projekt aplikace ASP.NET, ale můžete také vytvořit datovou službu jako projekt ASP.NET webu v sadě Visual Studio. Informace o rozdílech mezi dvěma typy projektů naleznete v tématu [Projekty webových aplikací versus Projekty webu v sadě Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd547590(v=vs.110)).

- Při vytváření datové služby pomocí dialogového okna **Přidat novou položku** v sadě Visual Studio je datová služba hostována ASP.NET ve službě IIS. Zatímco ASP.NET a služba IIS jsou výchozím hostitelem pro datovou službu, jsou podporovány další možnosti hostování. Další informace naleznete [v tématu Hostování datové služby](hosting-the-data-service-wcf-data-services.md).

## <a name="deploy-wcf-data-services"></a>Nasazení datových služeb WCF

Služba WCF Data Service nabízí flexibilitu při výběru procesu, který je hostitelem datové služby. Pomocí sady Visual Studio můžete nasadit datovou službu na následující platformy:

- **Webový server hostovaný službou IIS**

    Pokud je datová služba vyvinuta jako projekt ASP.NET, lze ji nasadit na webový server služby IIS pomocí standardních procesů nasazení ASP.NET.  Visual Studio poskytuje následující technologie nasazení pro ASP.NET, v závislosti na druhu ASP.NET projektu, který je hostitelem datové služby, kterou nasazujete.

  - **Technologie nasazení pro ASP.NET webových aplikací**

    - [Postup: Vytvoření balíčku webového nasazení v sadě Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd465323(v=vs.110))

    - [Postup: Nasazení webového projektu pomocí publikování jedním kliknutím v sadě Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd465337(v=vs.110))

  - **Technologie nasazení pro ASP.NET weby**

    - [Postup: Kopírování souborů webu pomocí nástroje Kopírovat web](https://docs.microsoft.com/previous-versions/aspnet/c95809c0(v=vs.100))

    - [Postup: Publikování webů](https://docs.microsoft.com/previous-versions/aspnet/20yh9f1b(v=vs.100))

    - [Návod: Nasazení webové aplikace ASP.NET pomocí xcopy](https://docs.microsoft.com/previous-versions/aspnet/f735abw9(v=vs.100))

     Další informace o možnostech nasazení pro ASP.NET aplikaci naleznete v [tématu Přehled nasazení webu pro sady Visual Studio a ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/dd394698(v=vs.110)).

    > [!TIP]
    > Než datovou službu nasadíte do služby IIS, nezapomeňte otestovat nasazení na webový server, na kterém je spuštěna služba IIS. Další informace naleznete v [tématu How to: Develop a WCF Data Service Running on IIS](how-to-develop-a-wcf-data-service-running-on-iis.md).

- **Microsoft Azure**

     Datovou službu do Windows Azure můžete nasadit pomocí nástrojů Windows Azure pro Visual Studio. Nástroje Windows Azure pro Visual Studio si můžete stáhnout ze služby [Stažení softwaru .](https://go.microsoft.com/fwlink/?LinkID=201848) Další informace o nasazení datové služby do Windows Azure najdete v příspěvku [nasazení služby OData ve Windows Azure](https://docs.microsoft.com/archive/blogs/astoriateam/deploying-an-odata-service-in-windows-azure).

### <a name="deployment-considerations"></a>Důležité informace o nasazení

Při nasazování datových služeb je vhodné zvážit následující faktory:

- Při nasazení datové služby, která používá zprostředkovatele Entity Framework pro přístup k databázi serveru SQL Server, může být také muset šířit datové struktury, data nebo obojí s nasazením datové služby. Visual Studio můžete automaticky vytvářet skripty (.sql soubory) k tomu v cílové databázi a tyto skripty mohou být zahrnuty do balíčku nasazení webu ASP.NET aplikace. Další informace naleznete v [tématu How to: Deploy a Database With a Web Application Project](https://docs.microsoft.com/previous-versions/dd465343(v=vs.100)). U webu ASP.NET to lze provést pomocí **Průvodce publikováním databáze** v sadě Visual Studio. Další informace naleznete [v tématu Publishing a SQL Database](https://docs.microsoft.com/previous-versions/aspnet/bb907585(v=vs.100)).

- Vzhledem k tomu, že služba WCF Data Services obsahuje základní implementaci WCF, můžete pomocí služby Windows Server AppFabric sledovat datovou službu nasazenou do služby IIS spuštěnou v systému Windows Server. Další informace o použití windows server appfabric u sledování datové služby, naleznete v post [sledování WCF datové služby s Windows Server AppFabric](https://docs.microsoft.com/archive/blogs/rjacobs/tracking-wcf-data-services-with-windows-server-appfabric).

## <a name="see-also"></a>Viz také

- [Hostování datové služby](hosting-the-data-service-wcf-data-services.md)
- [Zabezpečení datových služeb WCF Data Services](securing-wcf-data-services.md)
- [Definování datových služeb WCF Data Services](defining-wcf-data-services.md)
