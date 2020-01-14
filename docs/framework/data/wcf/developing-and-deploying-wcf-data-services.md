---
title: Vývoj a nasazení služeb WCF Data Services
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- deploying [WCF Data Services
- developing applications [WCF Data Services]
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
ms.openlocfilehash: e34f7c8a0194e3901453923530a5cd07202801f6
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937461"
---
# <a name="develop-and-deploy-wcf-data-services"></a>Vývoj a nasazení WCF Data Services

Toto téma poskytuje informace o vývoji a nasazení WCF Data Services. Další základní informace o WCF Data Services najdete v tématu [Začínáme](getting-started-with-wcf-data-services.md) a [Přehled](wcf-data-services-overview.md).

## <a name="develop-wcf-data-services"></a>Vývoj WCF Data Services

Když použijete WCF Data Services k vytvoření datové služby, která podporuje protokol OData (Open Data Protocol), musíte během vývoje provádět následující základní úlohy:

1. **Definování datového modelu**

     WCF Data Services podporuje různé poskytovatele datových služeb, které umožňují definovat datový model na základě dat z nejrůznějších zdrojů dat od relačních databází až po datové typy s pozdní vazbou. Další informace najdete v tématu [poskytovatelé Data Services](data-services-providers-wcf-data-services.md).

2. **Vytvoření datové služby**

     Většina základních datových služeb zpřístupňuje třídu, která dědí z třídy <xref:System.Data.Services.DataService%601>, s typem `T`, který je kvalifikovaný název oboru názvů kontejneru entit. Další informace najdete v tématu [definování WCF Data Services](defining-wcf-data-services.md).

3. **Konfigurace datové služby**

     Ve výchozím nastavení WCF Data Services zakáže přístup k prostředkům, které jsou zpřístupněny kontejnerem entit. Rozhraní <xref:System.Data.Services.DataServiceConfiguration> umožňuje nakonfigurovat přístup k prostředkům a operacím služby, určit podporovanou verzi OData a definovat další chování v rámci služby, jako je například chování dávkování nebo maximální počet entit, které mohou být vráceny v jednom kanálu odpovědí. Další informace najdete v tématu [konfigurace datové služby](configuring-the-data-service-wcf-data-services.md).

Toto téma se zabývá hlavně vývojem a nasazením datových služeb pomocí sady Visual Studio. Informace o flexibilitě poskytované WCF Data Services pro vystavení dat jako kanálů OData najdete v tématu věnovaném [definování WCF Data Services](defining-wcf-data-services.md).

### <a name="choose-a-development-web-server"></a>Zvolit vývojový webový server

Při vývoji datové služby WCF jako aplikace ASP.NET nebo webu ASP.NET pomocí sady Visual Studio 2015 můžete vybrat webové servery, na kterých chcete spustit datovou službu během vývoje. Následující webové servery jsou integrovány se sadou Visual Studio, které usnadňují testování a ladění datových služeb v místním počítači.

1. **Místní server služby IIS**

     Když vytváříte datovou službu, která je ASP.NET aplikací nebo webu ASP.NET, která běží na Internetová informační služba (IIS), doporučujeme vyvíjet a testovat datovou službu pomocí služby IIS v místním počítači. Spuštění datové služby ve službě IIS usnadňuje sledování požadavků HTTP během ladění. Zároveň vám to umožňuje předem stanovit práva, jež služba IIS potřebuje pro přístup k souborům, databázím a jiným prostředkům vyžadovaným datovou službou. Chcete-li spustit datovou službu ve službě IIS, je nutné zajistit, aby byla správně nainstalována a nakonfigurována služba IIS i Windows Communication Foundation (WCF) a aby bylo možné udělit přístup k účtům služby IIS v systému souborů a databázích. Další informace naleznete v tématu [How to: vývoj a WCF Data Service běžící na službě IIS](how-to-develop-a-wcf-data-service-running-on-iis.md).

    > [!NOTE]
    > Je nutné spustit aplikaci Visual Studio s oprávněními správce, aby bylo možné v prostředí vývoje nakonfigurovat místní server služby IIS.

2. **Vývojový server sady Visual Studio**

     Visual Studio obsahuje vestavěný webový server, vývojový server sady Visual Studio, což je výchozí webový server pro projekty ASP.NET. Tento webový server je navržen tak, aby během vývoje spouštěl projekty ASP.NET v místním počítači. V [WCF Data Services rychlém](quickstart-wcf-data-services.md) startu se dozvíte, jak vytvořit datovou službu, která běží na vývojovém serveru sady Visual Studio.

     Při použití vývojového serveru sady Visual Studio pro vývoj datové služby byste měli mít na paměti následující omezení:

    - Tento server je přístupný pouze v místním počítači.

    - Tento server naslouchá na `localhost` a na specifickém portu, nikoli na portu 80, což je výchozí port pro zprávy HTTP. Další informace naleznete v tématu [webové servery v aplikaci Visual Studio pro webové projekty ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/58wxa9w5(v=vs.120)).

    - Tento server spouští datovou službu v kontextu aktuálního uživatelského účtu. Pokud například používáte jako uživatel na úrovni správce, datová služba spuštěná na vývojovém serveru sady Visual Studio bude mít oprávnění na úrovni správce. To může vést k tomu, že datová služba bude mít přístup k prostředkům, ke kterým nemá při nasazení na server služby IIS přístupová práva.

    - Tento server neobsahuje nadstandardní funkce služby IIS, jako je například ověřování.

    - Tento server nemůže zpracovávat datové proudy HTTP, které jsou při přístupu k velkým binárním datům z datové služby automaticky odesílány klientem WCF Data Services. Další informace najdete v tématu [poskytovatel streamování](streaming-provider-wcf-data-services.md).

    - Tento server má potíže se zpracováním znaku tečky (`.`) v adrese URL, i když je tento znak podporován WCF Data Services v klíčových hodnotách.

    > [!TIP]
    > I když můžete k testování datových služeb během vývoje použít vývojový server sady Visual Studio, měli byste je po nasazení na webový server, na kterém je spuštěna služba IIS, znovu otestovat.

3. **Vývojové prostředí Windows Azure**

     Nástroje Windows Azure pro Visual Studio obsahují integrovanou sadu nástrojů pro vývoj služeb Windows Azure v sadě Visual Studio. Pomocí těchto nástrojů můžete vyvíjet datové služby, které lze nasazovat na platformě Azure, a před nasazením je otestovat v místním počítači. Tyto nástroje použijte při používání sady Visual Studio k vývoji datových služeb, které běží na platformě Windows Azure. Nástroje Windows Azure pro Visual Studio si můžete stáhnout z webu [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkID=201848). Další informace o vývoji datové služby, která běží na platformě Windows Azure, najdete v příspěvku [nasazení služby OData v systému Windows Azure](https://docs.microsoft.com/archive/blogs/astoriateam/deploying-an-odata-service-in-windows-azure).

### <a name="development-tips"></a>Tipy pro vývoj

Při vývoji datových služeb je vhodné zvážit následující faktory:

- Určete požadavky na zabezpečení datové služby a to, zda chcete uživatele ověřovat nebo omezit přístup pro konkrétní uživatele. Další informace najdete v tématu [zabezpečení WCF Data Services](securing-wcf-data-services.md).

- Při ladění datové služby může být velmi užitečný kontrolní program HTTP, který umožňuje kontrolovat obsah zpráv požadavků a odpovědí. K inspekci požadavků HTTP a odpovědí z datové služby lze využít jakýkoli síťový analyzátor paketů, který zobrazuje surové pakety.

- Při ladění datové služby může být vhodné získat více informací o chybě datové služby než při běžném provozu. Další informace o chybě datové služby můžete získat nastavením vlastnosti <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> v <xref:System.Data.Services.DataServiceConfiguration> na `true` a nastavením vlastnosti <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> atributu <xref:System.ServiceModel.Description.ServiceDebugBehavior> pro třídu datové služby na `true`. Další informace najdete v [WCF Data Services po ladění](https://blogs.msdn.microsoft.com/phaniraj/?m=20086). Můžete také povolit trasování ve WCF pro zobrazení výjimek vyvolaných ve vrstvě zasílání zpráv HTTP. Další informace najdete v tématu [Konfigurace trasování](../../wcf/diagnostics/tracing/configuring-tracing.md).

- Datová služba je obvykle vyvinuta jako projekt aplikace ASP.NET, ale můžete také vytvořit datovou službu jako projekt ASP.NET webu v aplikaci Visual Studio. Informace o rozdílech mezi těmito dvěma typy projektů naleznete v tématu [projekty webových aplikací a webové projekty v aplikaci Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd547590(v=vs.110)).

- Při vytváření datové služby pomocí dialogového okna **Přidat novou položku** v aplikaci Visual Studio je datová služba hostována službou ASP.NET ve službě IIS. I když je ASP.NET a IIS výchozím hostitelem pro datovou službu, podporují se další možnosti hostování. Další informace najdete v tématu [hostování datové služby](hosting-the-data-service-wcf-data-services.md).

## <a name="deploy-wcf-data-services"></a>Nasazení WCF Data Services

Služba WCF Data Service nabízí flexibilitu při výběru procesu, který je hostitelem datové služby. Pomocí sady Visual Studio můžete nasadit datovou službu na následující platformy:

- **Webový server hostovaný službou IIS**

    Pokud je datová služba vyvíjena jako projekt ASP.NET, je možné ji nasadit na webový server služby IIS pomocí standardních procesů nasazení ASP.NET.  Visual Studio poskytuje následující technologie nasazení pro ASP.NET, v závislosti na druhu projektu ASP.NET, který hostuje datovou službu, kterou nasazujete.

  - **Technologie nasazení pro webové aplikace v ASP.NET**

    - [Postupy: vytvoření balíčku pro nasazení webu v aplikaci Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd465323(v=vs.110))

    - [Postupy: nasazení webového projektu pomocí publikování jedním kliknutím v aplikaci Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd465337(v=vs.110))

  - **Technologie nasazení pro weby ASP.NET**

    - [Postupy: kopírování souborů webu pomocí nástroje pro kopírování webu](https://docs.microsoft.com/previous-versions/aspnet/c95809c0(v=vs.100))

    - [Postupy: publikování webů](https://docs.microsoft.com/previous-versions/aspnet/20yh9f1b(v=vs.100))

    - [Návod: nasazení webové aplikace v ASP.NET pomocí příkazu XCOPY](https://docs.microsoft.com/previous-versions/aspnet/f735abw9(v=vs.100))

     Další informace o možnostech nasazení pro aplikaci ASP.NET najdete v tématu [Přehled nasazení webu pro Visual Studio a ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/dd394698(v=vs.110)).

    > [!TIP]
    > Než datovou službu nasadíte do služby IIS, nezapomeňte otestovat nasazení na webový server, na kterém je spuštěna služba IIS. Další informace naleznete v tématu [How to: vývoj a WCF Data Service běžící na službě IIS](how-to-develop-a-wcf-data-service-running-on-iis.md).

- **Windows Azure**

     Datovou službu můžete nasadit do Windows Azure pomocí nástrojů Windows Azure pro Visual Studio. Nástroje Windows Azure pro Visual Studio si můžete stáhnout z webu [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkID=201848). Další informace o nasazení datové služby do Windows Azure najdete v příspěvku [nasazení služby OData v Microsoft Azure](https://docs.microsoft.com/archive/blogs/astoriateam/deploying-an-odata-service-in-windows-azure).

### <a name="deployment-considerations"></a>Důležité informace o nasazení

Při nasazování datových služeb je vhodné zvážit následující faktory:

- Když nasadíte datovou službu, která pro přístup k databázi SQL Server používá poskytovatele Entity Framework, může být také nutné rozšířit datové struktury, data nebo obojí do nasazení datové služby. Sada Visual Studio může automaticky vytvářet skripty (soubory. SQL) k tomu v cílové databázi a tyto skripty lze zahrnout do balíčku pro nasazení webu aplikace ASP.NET. Další informace najdete v tématu [Postup: nasazení databáze pomocí projektu webové aplikace](https://docs.microsoft.com/previous-versions/dd465343(v=vs.100)). Pro web ASP.NET to můžete provést pomocí **Průvodce publikováním databáze** v aplikaci Visual Studio. Další informace najdete v tématu [publikování SQL Database](https://docs.microsoft.com/previous-versions/aspnet/bb907585(v=vs.100)).

- Vzhledem k tomu, že WCF Data Services zahrnuje základní implementaci služby WCF, můžete použít Windows Server AppFabric k monitorování datové služby nasazené do služby IIS spuštěné v systému Windows Server. Další informace o použití Windows serveru AppFabric ke sledování datové služby najdete v [WCF Data Services příspěvku s Windows serverem AppFabric](https://docs.microsoft.com/archive/blogs/rjacobs/tracking-wcf-data-services-with-windows-server-appfabric).

## <a name="see-also"></a>Viz také:

- [Hostování datové služby](hosting-the-data-service-wcf-data-services.md)
- [Zabezpečení datových služeb WCF Data Services](securing-wcf-data-services.md)
- [Definování datových služeb WCF Data Services](defining-wcf-data-services.md)
