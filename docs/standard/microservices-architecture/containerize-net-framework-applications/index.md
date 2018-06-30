---
title: Migrace aplikací starší monolitický .NET Framework do kontejneru systému Windows
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Migrace aplikací starší monolitický .NET Framework do kontejneru systému Windows
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 01b84d29a559bde02ebd30535488c272d5208167
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106512"
---
# <a name="migrating-legacy-monolithic-net-framework-applications-to-windows-containers"></a>Migrace aplikací starší monolitický .NET Framework do kontejneru systému Windows

*Kontejnery Windows lze použít jako způsob pro zlepšení vývoj a testování prostředích a k nasazení aplikací, které jsou založeny na starší verzi rozhraní .NET Framework technologie, jako je Web* *formulářů. Použití kontejnerů pro starší verze aplikace tímto způsobem se označuje jako "navýšení a shift" scénáře.*

Předchozích částech tohoto průvodce máte prosazovaná mikroslužeb architektura, kde obchodních aplikací rozděleny mezi různé kontejnery, každý službou malé, cílených. Tento cíl má mnoho výhod. Při vývoji nových aplikací důrazně doporučujeme tento přístup. Klíčové podnikové aplikace také těžit dost pro potřeby náklady na rearchitecture a opětovná implementace.

Ale ne každá aplikace bude mít prospěch dost pro potřeby náklady. To neznamená, že tyto aplikace nelze použít ve scénářích kontejneru.

V této části se podíváme na aplikaci pro eShopOnContainers, zobrazí obrázek 7-1. Tato aplikace se použije členové týmu enterprise eShopOnContainers k zobrazení a úpravě katalogu produktů.

![](./media/image1.png)

**Obrázek 7-1**. Aplikace webových formulářů ASP.NET (starší verze technologie) do kontejneru systému Windows

Toto je aplikace webových formulářů, která se používá k procházení a upravit položky katalogu. Webové formuláře závislost znamená, že tato aplikace se nespustí na .NET Core ledaže je přepsaná bez webových formulářů a místo toho používá ASP.NET MVC jádra. Zobrazí se, jak spouštět aplikace, jako je to v kontejnerech beze změn. Zobrazí se taky, jak provést minimální změny pro práci v hybridní režim, kde některé funkce se přesunula do samostatné mikroslužbu, ale většina funkcí zůstane v monolitický aplikace.

## <a name="benefits-of-containerizing-a-monolithic-application"></a>Výhody containerizing monolitický aplikace

Catalog.WebForms aplikace je k dispozici v úložišti GitHub eShopOnContainers (<https://github.com/dotnet/eShopOnContainers>). Tato aplikace je samostatná aplikace, webový přístup k úložišti dat vysoké dostupnosti. Existují i tak výhody, na kterém je aplikace spuštěná v kontejneru. Vytvoření bitové kopie pro aplikaci. Od tohoto okamžiku každé nasazení běží ve stejném prostředí. Každý kontejner používá stejnou verzi operačního systému, má stejnou verzi závislostí nainstalována, používá stejné rozhraní a je sestaven pomocí stejného procesu. Zobrazí se aplikace načíst ve Visual Studio 2017 v obrázku 7-2.

![](./media/image2.png)

**Obrázek 7-2**. Správa aplikací webových formulářů v aplikaci Visual Studio 2017 katalogů

Kromě toho vývojáři všechny aplikaci můžete spustit v tomto prostředí konzistentní. Problémy, které se zobrazují pouze u některých verzí se zobrazí okamžitě pro vývojáře, nikoli zpřístupnění v pracovním nebo produkčním prostředí. Rozdíly mezi vývojových prostředí mezi vývojovým týmem podstatné menší po spuštění aplikace v kontejnerech.

Nakonec kontejnerizované aplikací mít plošší křivky Škálováním na více systémů. Je nutné učit jak kontejnerizované aplikací povolit více kontejnerů ve virtuálním počítači nebo více kontejnerů ve fyzickém počítači. Výsledkem je vyšší hustotu a méně požadované prostředky.

Z těchto důvodů zvažte spuštění starší verze aplikace monolitický v kontejner Docker pomocí operace "navýšení a shift". Frázi "navýšení a posunutí" popisuje oboru této úlohy: můžete *navýšení* z fyzický nebo virtuální počítač, bude celá aplikace a *shift* ho do kontejneru. V situacích, ideální není potřeba žádné změny kódu aplikace spouštět v kontejneru.

## <a name="possible-migration-paths"></a>Cesty možné migrace

Jako monolitický aplikace je aplikace Catalog.Webforms jednu webovou aplikaci obsahující všechny kód, včetně knihovny přístup data. Databáze se spustí na samostatný počítač vysokou dostupnost. Tato konfigurace se simuluje v ukázkovém kódu pomocí mock katalogu služeb: Catalog.WebForms aplikaci můžete spustit u falešných dat k simulaci Čistý scénář navýšení a shift. Tento příklad ukazuje ta nejjednodušší cesta migrace, kde přesouváte existující prostředky se mají spustit v kontejneru beze změn kódu. Tato cesta je vhodný pro aplikace, které jsou dokončení a které mají minimálním interakci s funkcí, které přesouváte do mikroslužeb.

Ale eShopOnContainers webu je již přístupu k ukládání dat pomocí mikroslužeb pro různé scénáře. Editor katalogu lze využít katalog mikroslužbu místo přístup k úložišti dat katalogu přímo malé další změny.

Tyto změny ukazují poměrně pro vaše vlastní aplikace. Můžete provést nic z přesunutí stávající aplikace bez změn do kontejnerů k provádění změn malá, které umožňují stávající aplikace pro přístup k některým nové mikroslužeb, na úplně přepisování plně podílet na novou aplikaci Architektura založená na mikroslužby. Správné cestě závisí na náklady migrace a výhody z žádné migrace.

## <a name="application-tour"></a>Prohlídka aplikace

Můžete načíst Catalog.WebForms řešení a spuštění aplikace jako samostatné aplikace. V této konfiguraci místo trvalého úložiště databáze, aplikace používá falešných služby vrátit data. Aplikace používá Autofac (<https://autofac.org/>) jako inverzi kontejneru ovládacích prvků (IOC). Pomocí vkládání závislostí (DI), můžete nakonfigurovat aplikaci, aby používala falešných dat nebo dat služby za provozu katalogu. (Vysvětlíme více o DI krátce.) Kód spuštění načte nastavení useFake ze souborů web.config a nakonfiguruje kontejneru Autofac vložení služba falešných dat nebo služba katalogu za provozu. Pokud spouštíte aplikaci pomocí useFake nastavena na hodnotu false v souboru web.config, najdete v zobrazení katalogu dat aplikace webových formulářů.

Většina postupy používané v této aplikaci by měla být velmi dobře každému uživateli, který byl použit webových formulářů. Ale mikroslužbu katalogu zavádí dvě techniky, které mohou být obeznámeni: závislost vkládání (DI), které již bylo zmíněno dříve, a práci s úložišti asynchronní dat webových formulářů.

DI Invertuje výběr typické objektově orientované strategie zápisu třídy, které přidělují všechny potřebné prostředky. Místo toho třídy žádosti závislé z kontejneru služby. Výhodou DI je, že můžete nahradit externích služeb s fakes (mocks) pro podporu testování nebo jiných prostředích.

Kontejner DI používá konfiguraci appSettings web.config řídit, jestli se má používat data falešných katalogu nebo dynamická data z spuštěné služby. Aplikace registruje objekt modulu HTTP, který vytvoří kontejner a zaregistruje předběžné žádost o obslužnou rutinu vložení závislosti. Zobrazí se tento kód v souboru Modules/AutoFacHttpModule.cs, který vypadá jako v následujícím příkladu:

```cs
private static IContainer CreateContainer()
{
  // Configure AutoFac:
  // Register Containers:

  var settings = WebConfigurationManager.AppSettings;
  var useFake = settings["usefake"];
  bool fake = useFake == "true";
  var builder = new ContainerBuilder();

  if (fake)
  {
    builder.RegisterType<CatalogMockService>()
    .As<ICatalogService>();
  }
  else
  {
    builder.RegisterType<CatalogService>()
    .As<ICatalogService>();
    builder.RegisterType<RequestProvider>()
    .As<IRequestProvider>();
  }

  var container = builder.Build();
  return container;
}

private void InjectDependencies()
{
  if (HttpContext.Current.CurrentHandler is Page page)
  {
    // Get the code-behind class that we may have written
    var pageType = page.GetType().BaseType;

    // Determine if there is a constructor to inject, and grab it
    var ctor = (from c in pageType.GetConstructors()
                where c.GetParameters().Length > 0
                select c).FirstOrDefault();

    if (ctor != null)
    {
      // Resolve the parameters for the constructor
      var args = (from parm in ctor.GetParameters()
                  select Container.Resolve(parm.ParameterType))
                  .ToArray();

      // Execute the constructor method with the arguments resolved
      ctor.Invoke(page, args);
    }

    // Use the Autofac method to inject any
    // properties that can be filled by Autofac
    Container.InjectProperties(page);
  }
}
```

Stránky aplikace (Default.aspx.cs a EditPage.aspx.cs) definovat konstruktory, které provést tyto závislosti. Všimněte si, že výchozí konstruktor je stále přítomen a přístupný. Infrastruktury musí následující kód.

```cs
protected _Default() { }

public _Default(ICatalogService catalog) => this.catalog = catalog;
```

Rozhraní API katalogu jsou všechny asynchronní metody. Webové formuláře teď podporuje tyto pro všechny ovládací prvky data. Aplikace Catalog.WebForms používá vazby modelu pro seznam a upravovat stránky; ovládací prvky na stránkách definovat metody SelectMethod, metoda UpdateMethod, metodu InsertMethod a metoda DeleteMethod vlastnosti, které určují vrácení úloh asynchronní operace. Web Forms – ovládací prvky pochopit, pokud se metody svázán s ovládacím asynchronní. Pouze omezení dojde při použití asynchronních metod vyberte je, že nemůže podporovat stránkování. Podpis stránkování vyžaduje parametr typu out a asynchronních metod nemůže mít výstupní parametry. Tento stejný postup se používá na jiných stránkách, které vyžadují dat ze služby katalogu.

Výchozí konfiguraci pro katalog aplikací webových formulářů využívá catalog.api služby imitovanou implementaci. Tento model používá pevně zakódovaný datovou sadu pro svá data, která zjednodušuje některé úlohy odebráním závislosti na službu catalog.api ve vývojovém prostředí.

## <a name="lifting-and-shifting"></a>Zrušení a s posunem

Visual Studio poskytuje podpory pro containerizing aplikace. Klikněte pravým tlačítkem na uzel projektu a potom vyberte **přidat** a **Docker podporu**. Šablona projektu Docker přidá nový projekt do řešení názvem **docker-tvoří**. Projekt obsahuje Docker prostředky, které tvoří (nebo sestavení) bitové kopie je třeba a spuštění nezbytné kontejnery, jak je znázorněno v obrázek 7-3.

V nejjednodušší navýšení a shift scénářích aplikace bude jedné služby, který používáte pro aplikace webových formulářů. Šablona také změní spuštění projektu tak, aby odkazoval **docker compose** projektu. Kombinace kláves Ctrl + F5 nebo F5 nyní vytvoří bitovou kopii Docker a spustí kontejner Docker.

![](./media/image3.png)

**Obrázek 7-3**. **Docker compose** projekt v řešení webové formuláře

Než spustíte řešení, musí se ujistěte, nakonfigurovat Docker k použití Windows kontejnerů. K tomu, kliknete pravým tlačítkem na hlavním panelu ikonu Docker v systému Windows a vyberte **přepnout do kontejnerů Windows**, jak je znázorněno na obrázku 7 – 4.

![](./media/image4.png)

**Obrázek 7-4**. Přepnutí do kontejneru systému Windows z na hlavním panelu ikonu Docker v systému Windows

Pokud je zobrazeno položky nabídky **přepnout do kontejnerů Linux**, již používáte Docker s kontejnery Windows.

Spuštění řešení restartuje Docker hostitele. Když vytvoříte, vytvoříte aplikaci a bitovou kopii Docker pro projekt webové formuláře. Při prvním to trvá mnoho času. To je proto procesu sestavení vrátí základní bitovou kopii systému Windows Server a další bitovou kopii pro technologii ASP.NET. Následující sestavení a spuštění cykly bude mnohem rychlejší.

Podívejme se hlubší na soubory přidal Docker v šabloně projektů. Můžete ho vytvořit několik souborů. Visual Studio použije tyto soubory vytvořit bitovou kopii Docker a spusťte kontejner. Stejné soubory, které z rozhraní příkazového řádku můžete použít ke spuštění příkazů Docker ručně.

Následující příklad soubor Docker ukazuje základní nastavení pro vytváření obrazem Docker na základě bitové kopie Windows ASP.NET, který spouští stránku ASP.NET.

```
FROM microsoft/aspnet

ARG source

WORKDIR /inetpub/wwwroot

COPY ${source:-obj/Docker/publish} .
```

Tento soubor Docker bude vypadat velmi podobné těm, které jsou vytvořené pro spouštění aplikací ASP.NET Core v kontejnerech Linux. Existují však několik důležitých rozdílů. Nejdůležitější rozdíl je, že základní bitová kopie je společnosti microsoft nebo aspnet, který je aktuální image systému Windows Server, který zahrnuje rozhraní .NET Framework. Další rozdíly jsou, že adresáře zkopírovali ze zdrojového adresáře se liší.

Další soubory v **docker-tvoří** projektu jsou Docker prostředky potřebné k vytváření a konfigurace kontejnerů. Visual Studio umísťuje různé soubory docker-compose.yml v rámci jednoho uzlu, abyste měli na očích, jak se používají. Základní docker-compose soubor obsahuje direktivy, které jsou společné pro všechny konfigurace. Soubor docker-compose.override.yml obsahuje proměnné prostředí a související přepsání pro vývojáře konfigurace. Variant s. vs.debug a. vs.release zadejte nastavení prostředí, které chcete přiřadit a spravovat kontejneru spuštěné Visual Studio.

Integrace sady Visual Studio je součást přidání podpory Docker do vašeho řešení, můžete také sestavit a spustit z příkazového řádku pomocí docker-tvoří až příkaz, protože jste viděli v předchozích částech.

## <a name="getting-data-from-the-existing-catalog-net-core-microservice"></a>Získání dat z existující mikroslužbu .NET Core katalogu

Webové formuláře aplikace pro používání mikroslužbu katalogu eShopOnContainers k získání dat místo použití falešných dat můžete nakonfigurovat. K tomu, upravte soubor web.config a nastavte hodnotu klíče useFake na hodnotu false. Kontejner DI použije třídu, která přistupuje k provozu katalogu mikroslužbu místo třídu, která vrátí data o pevně. Je potřeba žádné další změny kódu.

Přístup k službě za provozu katalogu znamená musíte aktualizovat **docker compose** projektu sestavení obrázek katalogu služby a spusťte kontejner služby katalogu. Docker CE pro Windows podporuje kontejnery Linux a Windows kontejnery, ale není ve stejnou dobu. Pokud chcete spustit mikroslužbu katalogu, budete muset vytvořit bitovou kopii používající mikroslužbu katalogu na vrcholku kontejneru se systémem Windows. Tento přístup vyžaduje jiný soubor Docker mikroslužeb projektu, než jste viděli v předchozích částech. Soubor Dockerfile.windows obsahuje konfigurační nastavení k vytvoření bitové kopie kontejneru katalogu rozhraní API, tak, aby běžel v kontejneru systému Windows – například použít bitovou kopii systému Windows Nano Docker.

Mikroslužbu katalogu spoléhá na databázi systému SQL Server. Proto musíte použít také bitovou kopii systému Windows Docker SQL Server.

Po provedení těchto změn projektu docker-compose nepodporuje více a spusťte aplikaci. Projekt spustí serveru SQL pomocí bitové kopie založené na systému SQL Server systému Windows. Spustí mikroslužbu katalogu v kontejneru systému Windows. A začne kontejneru editor katalogu webových formulářů také v kontejneru systému Windows. Pokud žádné z bitové kopie potřebovat sestavení, jsou nejprve vytvoření bitové kopie.

## <a name="development-and-production-environments"></a>Vývoj a produkční prostředí

Existuje několik rozdílů mezi vývoj konfigurace a konfiguraci výroby. Ve vývojovém prostředí spusťte aplikace webových formulářů, mikroslužbu katalogu a SQL Server v systému Windows kontejnery v rámci stejného hostitele Docker. V předchozích částech jsme uvedených nasazené bitové kopie systému SQL Server na stejném hostiteli Docker jako jiných služeb založených na .NET Core hostiteli Docker systémem Linux. Výhodou spuštění více mikroslužeb ve stejném hostiteli Docker (nebo v clusteru) je menší síťovou komunikaci a komunikace mezi kontejnery má nižší latenci.

Ve vývojovém prostředí je nutné spustit všechny kontejnery v stejné operačního systému. CE docker pro systém Windows nepodporuje spuštěných kontejnerů systémem Windows a Linux ve stejnou dobu. V produkčním prostředí můžete rozhodnout, pokud chcete spustit mikroslužbu katalogu v kontejneru systému Windows v jednom Docker hostiteli (nebo clusteru), nebo můžete nechat webových formulářů, aplikace komunikovat s instancí mikroslužbu katalogu spuštěnému v kontejneru Linux na jiné Docker hostitele. To závisí na tom, jak chcete optimalizovat pro latenci sítě. Ve většině případů budete chtít mikroslužeb, které vaše aplikace závisí na spouštění v stejného Docker hostitele (nebo swarm) pro snadné nasazení a menší latence komunikace. V těchto konfiguracích je pouze nákladná komunikace mezi instancemi mikroslužbu a vysokou dostupnost serverů pro trvalé úložiště.

>[!div class="step-by-step"]
[Předchozí](../net-core-single-containers-linux-windows-server-hosts/index.md)
[další](../multi-container-microservice-net-applications/index.md)
