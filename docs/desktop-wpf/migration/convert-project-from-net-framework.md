---
title: Migrace aplikací WPF na .NET Core 3,0
description: Naučte se migrovat aplikaci Windows Presentation Foundation (WPF) na .NET Core 3,0.
author: mjrousos
ms.date: 09/12/2019
ms.author: mikerou
ms.openlocfilehash: ccd2fc5a49d9c2d31c693e48099732614b568c7b
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507452"
---
# <a name="migrating-wpf-apps-to-net-core"></a>Migrace aplikací WPF do .NET Core

Tento článek popisuje kroky potřebné k migraci aplikace Windows Presentation Foundation (WPF) z .NET Framework na .NET Core 3,0. Pokud nemáte k dispozici aplikaci WPF na možnost port, ale chcete si ji vyzkoušet, můžete použít ukázkovou aplikaci pro **obchodní** použití, která je dostupná na [GitHubu](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader). Původní aplikace (cílící .NET Framework 4.7.2) je dostupná ve složce NetFx\BeanTraderClient. Nejdříve vyvysvětlíme kroky nezbytné pro obecně přihlašování aplikací a potom provedeme konkrétní změny, které se vztahují na ukázku pro **obchodníky v bobů** .

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

K migraci na .NET Core musíte nejdřív:

01. Pochopení a aktualizace závislostí NuGet:

    01. Upgradujte závislosti NuGet pro použití `<PackageReference>` formátu.
    01. Zkontrolujte závislosti na nejvyšší úrovni NuGet pro .NET Core nebo .NET Standard Compatibility.
    01. Upgradujte balíčky NuGet na novější verze.
    01. Pomocí [analyzátoru přenositelnosti .NET](../../standard/analyzers/portability-analyzer.md) pochopíte závislosti rozhraní .NET.

01. Migrujte soubor projektu do nového formátu sady SDK:

    01. Vyberte, jestli se mají cílit .NET Core i .NET Framework, nebo jenom .NET Core.
    01. Zkopírujte příslušné vlastnosti souboru projektu a položky do nového souboru projektu.

01. Opravit problémy sestavení:

    01. Přidejte odkaz na balíček [Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility/) .
    01. Najděte a opravte rozdíly na úrovni rozhraní API.
    01. Odeberte části *App. config* jiné než `appSettings` nebo `connectionStrings`.
    01. V případě potřeby znovu vygenerujte generovaný kód.

01. Testování za běhu:

    01. Potvrďte, že portovaná aplikace funguje podle očekávání.
    01. Pozor na <xref:System.NotSupportedException> výjimky.

## <a name="about-the-sample"></a>O ukázce

Tento článek se odkazuje na [ukázkovou aplikaci v programu Bob obchodník](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader) , protože používá nejrůznější závislosti, které jsou podobné těm, které mohou mít reálné aplikace WPF. Aplikace není velká, ale měla by být v souvislosti s složitostí krok z Hello World. Tato aplikace předvádí některé problémy, se kterými se uživatelé mohou setkat při přenosu reálných aplikací. Aplikace komunikuje se službou WCF, takže aby fungovala správně, budete také muset spustit projekt BeanTraderServer (dostupný ve stejném úložišti GitHubu) a ujistit se, že konfigurace BeanTraderClient odkazuje na správný koncový bod. (Ve výchozím nastavení ukázka předpokládá, že server běží na stejném počítači v *http://localhost:8090*, což bude platit, pokud BeanTraderServer spustíte místně.)

Mějte na paměti, že tato ukázková aplikace je určená k tomu, aby se ukázaly problémy s přenosem v .NET Core. Není určeno k předvedení osvědčených postupů pro WPF. Ve skutečnosti záměrně obsahují některé antipatterny, abyste se ujistili, že budete mít k dispozici alespoň několik zajímavých výzev při přenosu.

## <a name="getting-ready"></a>Příprava

Primárním problémem migrace aplikace .NET Framework do .NET Core je, že její závislosti můžou fungovat různě nebo vůbec. Migrace je mnohem jednodušší než při použití. mnoho balíčků NuGet teď cílí na .NET Standard. Počínaje platformou .NET Core 2,0 se .NET Framework a oblasti .NET Core Surface budou podobné. I tak některé rozdíly (v podpoře z balíčků NuGet a v dostupných rozhraních API .NET) zůstanou zachovány. Prvním krokem migrace je Kontrola závislostí aplikace a zajistěte, aby byly odkazy ve formátu, který je snadno migrován do .NET Core.

### <a name="upgrade-to-packagereference-nuget-references"></a>Upgradovat `<PackageReference>` na reference NuGet

Starší projekty .NET Framework obvykle uvádějí své závislosti NuGet v souboru *Packages. config* . Nový formát souboru projektu ve stylu sady SDK odkazuje na balíčky NuGet [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) jako prvky v samotném souboru csproj, nikoli v samostatném konfiguračním souboru.

Při migraci existují dvě výhody použití odkazů ve `<PackageReference>`stylu:

- Toto je styl odkazu NuGet, který je vyžadován pro nový soubor projektu .NET Core. Pokud jste již používali `<PackageReference>`, tyto prvky souboru projektu lze zkopírovat a vložit přímo do nového projektu.
- Na rozdíl od souboru Packages. config `<PackageReference>` elementy odkazují pouze na závislosti nejvyšší úrovně, které váš projekt závisí přímo na úrovni. Všechny ostatní přenositelné balíčky NuGet se určí v době obnovení a zaznamenávají se do automaticky generovaného souboru obj\project.assets.JSON. Díky tomu je mnohem snazší určit závislosti, které má váš projekt, což je užitečné při určování, zda budou nezbytné závislosti fungovat na rozhraní .NET Core nebo ne.

Prvním krokem pro migraci aplikace .NET Framework do .NET Core je aktualizovat ji tak, aby používala `<PackageReference>` odkazy na NuGet. Visual Studio toto dělá jednoduché. Stačí kliknout pravým tlačítkem myši na soubor *Packages. config Packages* v aplikaci Visual Studio **Průzkumník řešení**a pak vyberte **migrovat Packages. config na PackageReference**.

![Upgrade na PackageReference](./media/convert-project-from-net-framework/package-reference-migration.png)

Zobrazí se dialogové okno s vypočítanými závislostmi NuGet nejvyšší úrovně a s žádostí o další balíčky NuGet by se měly zvýšit na nejvyšší úroveň. Žádný z těchto dalších balíčků nemusí být na nejvyšší úrovni pro ukázku pro obchodní dodavatele, takže můžete zrušit kontrolu všech těchto polí. Pak klikněte na tlačítko **OK** a soubor *Packages. config* se odebere `<PackageReference>` a prvky se přidají do souboru projektu.

`<PackageReference>`– odkazy na styl neukládají balíčky NuGet místně do složky Packages. Místo toho jsou uloženy globálně jako optimalizace. Po dokončení migrace upravte soubor CSPROJ a odeberte všechny `<Analyzer>` prvky odkazující na analyzátory, které dříve byly z *.. Adresář \Packages* Nedělejte si starosti; vzhledem k tomu, že stále máte odkazy na balíček NuGet, analyzátory budou zahrnuty v projektu. Stačí vyčistit staré prvky stylu `<Analyzer>` Packages. config.

### <a name="review-nuget-packages"></a>Zkontrolovat balíčky NuGet

Teď, když vidíte balíčky NuGet nejvyšší úrovně, na kterých závisí projekt, můžete zkontrolovat, jestli jsou tyto balíčky dostupné v .NET Core. Můžete určit, jestli balíček podporuje .NET Core, a to tak, že se podíváte na závislosti na [NuGet.org](https://www.nuget.org/). Lokalita vytvořená komunitou [fuget.org](https://www.fuget.org/) zobrazuje tyto informace výrazně v horní části stránky s informacemi o balíčku.

Při cílení na rozhraní .NET Core 3,0 by měly všechny balíčky cílené na rozhraní .NET Core nebo .NET Standard fungovat (vzhledem k tomu, že .NET Core implementuje .NET Standard plochu). V některých případech se konkrétní verze balíčku, který se používá, necílí na rozhraní .NET Core ani .NET Standard, ale novější verze. V takovém případě byste měli zvážit upgrade na nejnovější verzi balíčku.

Můžete použít také balíčky cílené na .NET Framework, ale to přináší nějaké riziko. Rozhraní .NET Core pro .NET Framework závislosti jsou povoleny, protože oblasti .NET Core a .NET Framework Surface jsou natolik podobné, že tyto závislosti *často* fungují. Pokud se však balíček pokusí použít rozhraní .NET API, které není k dispozici v rozhraní .NET Core, dojde k výjimce za běhu. Z tohoto důvodu byste měli odkazovat pouze na .NET Framework balíčky, pokud nejsou k dispozici žádné jiné možnosti a nevíte, že by to mělo za starosti zátěž testu.

Pokud se odkazuje na balíčky, které necílí na rozhraní .NET Core nebo .NET Standard, budete si muset představit další alternativy:

- Existují jiné podobné balíčky, které lze použít místo toho? Někdy autoři NuGet publikují samostatně. Základní verze svých knihoven konkrétně cílí na .NET Core. Balíčky podnikových knihoven představují příklad publikování komunitou. NetCore "alternativy. V ostatních případech jsou pro .NET Standard k dispozici novější sady SDK pro konkrétní službu (někdy s různými názvy balíčků). Pokud nejsou k dispozici žádné alternativy, můžete pokračovat v používání .NET Framework cílené balíčky s vědomím, že je budete muset důkladně otestovat po spuštění v .NET Core.

Ukázka Bob obchodník má následující závislosti NuGet nejvyšší úrovně:

- [**Castle. Windsor, verze 4.1.1**](https://www.castleproject.org/projects/windsor/)  

  Tento balíček cílí na .NET Standard 1,6, takže funguje na .NET Core.

- [**Microsoft. CodeAnalysis. FxCopAnalyzers, verze 2.6.3**](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3)  
  Toto je meta balíček, takže není okamžitě zřejmé, které platformy podporuje, ale [dokumentace](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisfxcopanalyzers) indikuje, že jeho nejnovější verze (2.9.2) bude fungovat jak pro .NET Framework, tak pro .NET Core.

- [**Nito. AsyncEx, verze 4.0.1**](https://www.nuget.org/packages/Nito.AsyncEx/4.0.1)  

  Tento balíček necílí na .NET Core, ale novější verze 5,0. To je běžné při migraci, protože mnoho balíčků NuGet se v poslední době přidalo .NET Standard podpoře, ale starší verze projektu budou pouze cílit .NET Framework. Je-li rozdíl verze pouze dílčí rozdíl verze, je často snadné upgradovat na novější verzi. Vzhledem k tomu, že se jedná o zásadní změnu verze, je nutné upgradovat upgrade, protože by mohlo dojít k zásadním změnám balíčku. K dispozici je cesta s předstihem, i když.

- [**MahApps. metro, verze 1.6.5**](https://www.nuget.org/packages/MahApps.Metro/1.6.5)  

  Tento balíček také necílí na rozhraní .NET Core, ale má novější verzi předběžného (2,0-alfa). Znovu se budete muset podívat na nevyřešené změny, ale novější balíček ho podporuje.

Všechny cílové .NET Standard/. NET Core nebo mají novější verze, a proto se tady nemusejí zablokovat žádné problémy.

### <a name="upgrade-nuget-packages"></a>Upgradovat balíčky NuGet

Pokud je to možné, by bylo vhodné upgradovat verze všech balíčků, které v tomto okamžiku pouze cílí jenom na rozhraní .NET Core nebo .NET Standard s novějšími verzemi (s projektem pořád cílíte .NET Framework), abyste zjistili a vyřešili všechny zásadní změny včas.

Pokud byste nemuseli dělat žádné podstatné změny v existující .NET Framework verzi aplikace, může to počkat, až budete mít nový soubor projektu cílící na .NET Core. Upgrade balíčků NuGet na verze, které jsou kompatibilní s .NET Core, ale předem usnadňuje proces migrace, a to i po vytvoření nového souboru projektu a omezení počtu rozdílů mezi .NET Framework a verzemi .NET Core aplikace.

V případě ukázky na základě obchodníka je možné snadno provést všechny nezbytné upgrady (pomocí Správce balíčků NuGet sady Visual Studio) s jednou výjimkou: upgrade z **MahApps. metro 1.6.5** na **2,0** odhalí zásadní změny související s rozhraními API pro správu motivů a zvýraznění.

V ideálním případě by se aplikace aktualizovala tak, aby používala novější verzi balíčku (vzhledem k tomu, že je pravděpodobnější funkčnost .NET Core). V některých případech ale nemusí být proveditelné. V těchto případech NEUPGRADUJTE **MahApps. metro** , protože potřebné změny jsou netriviální a tento kurz se zaměřuje na migraci na .NET Core 3, ne na **MahApps. Metro 2.** Také se jedná o ne.NET Frameworkou závislost, protože obchodník z aplikace Bob uplatňuje jenom malou část **MahApps. metro**. Budeme samozřejmě potřebovat testování, aby se zajistilo, že vše funguje, až se migrace dokončí. Pokud se jednalo o reálný scénář, mělo by být dobré zaslat problém pro sledování práce, která se má přesunout na **MahApps. metro** verze 2,0, protože migrace teď nevede k nějakému technickému dluhu.

Jakmile se balíčky NuGet aktualizují na nejnovější verze, skupina `<PackageReference>` položek v souboru projektu ukázkového účastníka společnosti Bob by měla vypadat takto.

```xml
<ItemGroup>
  <PackageReference Include="Castle.Windsor">
    <Version>4.1.1</Version>
  </PackageReference>
  <PackageReference Include="MahApps.Metro">
    <Version>1.6.5</Version>
  </PackageReference>
  <PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers">
    <Version>2.9.2</Version>
  </PackageReference>
  <PackageReference Include="Nito.AsyncEx">
    <Version>5.0.0</Version>
  </PackageReference>
</ItemGroup>
```

### <a name="net-framework-portability-analysis"></a>Analýza přenositelnosti .NET Framework

Jakmile porozumíte stavu závislostí NuGet vašeho projektu, další věc, kterou je potřeba zvážit, je .NET Framework závislosti rozhraní API. Nástroj [analyzátor přenositelnosti .NET](../../standard/analyzers/portability-analyzer.md) je užitečný pro porozumění tomu, které rozhraní API .NET vaše projekty používá, jsou k dispozici na jiných platformách .NET.

Nástroj se dodává jako [modul plug-in sady Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), [Nástroj příkazového řádku](https://github.com/Microsoft/dotnet-apiport/releases)nebo zabalený do [jednoduchého grafického uživatelského rozhraní](https://github.com/Microsoft/dotnet-apiport-ui), které zjednodušuje jeho možnosti. Další informace o použití analyzátoru přenositelnosti .NET (port rozhraní API) najdete v tomto příspěvku na blogu v tématu [portování desktopových aplikací do .NET Core](https://devblogs.microsoft.com/dotnet/porting-desktop-apps-to-net-core/) . Pokud dáváte přednost použití příkazového řádku, jsou nezbytné kroky:

1. Stáhněte si [analyzátor přenositelnosti .NET](https://github.com/Microsoft/dotnet-apiport/releases) , pokud ho ještě nemáte.
1. Zajistěte, aby byla aplikace .NET Framework správně předaná sestavení (to je dobrý nápad před migrací bez ohledu na migraci).
1. Spusťte port rozhraní API s příkazovým řádkem.

    ```console
    ApiPort.exe analyze -f <PathToBeanTraderBinaries> -r html -r excel -t ".NET Core"
    ```

    `-f` Argument určuje cestu obsahující binární soubory, které se mají analyzovat. `-r` Argument určuje formát výstupního souboru, který chcete. `-t` Argument určuje, která platforma .NET bude analyzovat využití rozhraní API. V takovém případě chcete .NET Core.

Když otevřete sestavu HTML, v první části se zobrazí všechny analyzované binární soubory a procento používaných rozhraní API .NET, které jsou k dispozici na cílové platformě. Procento není smysluplné. Užitečnější je zobrazit konkrétní chybějící rozhraní API. Chcete-li to provést, buď vyberte název sestavení, nebo se posuňte dolů k sestavám pro jednotlivá sestavení.

Zaměřte se na sestavení, pro která vlastníte zdrojový kód. V sestavě ApiPorta v programu Bob obchodník je například uveden mnoho binárních souborů, ale většina z nich patří do balíčků NuGet. `Castle.Windsor`ukazuje, že závisí na některých rozhraních API System. Web, které chybí v .NET Core. Nejedná se o problém, protože jste předtím `Castle.Windsor` ověřili, že produkt podporuje .NET Core. Pro balíčky NuGet je běžné, že mají různé binární soubory pro použití s různými platformami .NET, takže jestli .NET Framework verze nástroje `Castle.Windsor` používá rozhraní API System. Web nebo not není relevantní, dokud balíček cílí také .NET Standard nebo .NET Core (to dělá).

V případě ukázky pro obchodníka v programu Bob je jediným binárním souborem, který je třeba vzít v úvahu, **BeanTraderClient** a tato sestava uvádí, `System.ServiceModel.ClientBase<T>.Close` že `System.ServiceModel.ClientBase<T>.Open`chybí pouze dvě rozhraní API .NET: a.

![Sestava přenositelnosti BeanTraderClient](./media/convert-project-from-net-framework/portability-report.png)

Je pravděpodobné, že nebudou blokovat problémy, protože rozhraní API klienta WCF jsou v .NET Core podporována (většinou), takže pro tato centrální rozhraní API musí být k dispozici alternativní řešení. Ve skutečnosti se podívejte na `System.ServiceModel`oblast .NET Core Surface (pomocí <https://apisof.net>), že místo toho jsou v .NET Core k dispozici asynchronní alternativy.

Na základě této sestavy a předchozí analýzy závislostí NuGet vypadá to, že by se neměly provádět žádné zásadní problémy migrace ukázkového účastníka z části Bob obchodník do .NET Core. Jste připraveni na další krok, ve kterém bude migrace skutečně zahájena.

## <a name="migrating-the-project-file"></a>Migruje se soubor projektu.

Pokud vaše aplikace nepoužívá nový [Formát souboru projektu ve stylu sady SDK](../../core/tools/csproj.md), budete potřebovat nový soubor projektu pro cílové rozhraní .NET Core. Existující soubor CSPROJ můžete nahradit, nebo pokud upřednostňujete zachování existujícího projektu v jeho aktuálním stavu, můžete přidat nový soubor CSPROJ cílící na rozhraní .NET Core. Můžete sestavit verze aplikace pro .NET Framework a .NET Core s jedním souborem projektu ve stylu sady SDK s [cílením](../../standard/library-guidance/cross-platform-targeting.md) na více verzí (určením více `<TargetFrameworks>` cílů).

Chcete-li vytvořit nový soubor projektu, můžete vytvořit nový projekt WPF v aplikaci Visual Studio nebo použít `dotnet new wpf` příkaz v dočasném adresáři pro vygenerování souboru projektu a potom jej zkopírovat nebo přejmenovat do správného umístění. K dispozici je také nástroj [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017)vytvořený komunitou, který může automatizovat některé migrace souborů projektu. Tento nástroj je užitečný, ale ještě potřebuje člověk ke kontrole výsledků, aby se zajistilo, že všechny podrobnosti migrace jsou správné. Jedna konkrétní oblast, kterou nástroj nezpracovává optimálně, migruje balíčky NuGet ze souborů *Packages. config* . Pokud nástroj běží na souboru projektu, který stále používá soubor *Packages. config* k odkazování na balíčky NuGet, migruje se `<PackageReference>` na prvky automaticky, ale přidá `<PackageReference>` prvky pro *všechny* balíčky místo pouze těch, které mají nejvyšší úroveň. Pokud jste již migrovali na`<PackageReference>` prvky pomocí sady Visual Studio (jak jste to udělali v této ukázce), nástroj může pomáhat se zbytkem převodu. Podobně jako Scott Hanselman doporučuje ve [svém blogovém příspěvku o migraci souborů csproj](https://www.hanselman.com/blog/UpgradingAnExistingNETProjectFilesToTheLeanNewCSPROJFormatFromNETCore.aspx). přenos po ruce je vzdělávací a výsledkem je lepší výsledky, pokud máte pouze několik projektů na port. Pokud ale přenášíte desítky nebo stovky souborů projektu, může se jednat o nástroj, jako je [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) .

Chcete-li vytvořit nový soubor projektu pro ukázku pro obchodní oddělení, `dotnet new wpf` spusťte příkaz v dočasném adresáři a přesuňte vygenerovaný soubor *. csproj* do složky *BeanTraderClient* a přejmenujte jej na **BeanTraderClient. Core. csproj**.

Vzhledem k tomu, že nový formát souboru projektu automaticky obsahuje soubory jazyka C#, soubory *RESX* a soubory XAML, které nalezne v nebo v jejím adresáři, je soubor projektu již skoro dokončen. Pro dokončení migrace otevřete staré a nové soubory projektu vedle sebe a Prohlédněte si starou a podívejte se, jestli je potřeba migrovat nějaké informace, které obsahuje. V ukázkovém případu pro hospodářský subjekt by měly být do nového projektu zkopírovány následující položky:

- Všechny `<RootNamespace>`vlastnosti `<AssemblyName>`, a `<ApplicationIcon>` by měly být kopírovány.

- Také je nutné přidat do nového `<GenerateAssemblyInfo>false</GenerateAssemblyInfo>` souboru projektu vlastnost, protože ukázka pro obchodníka v nástroji Bob zahrnuje atributy na úrovni sestavení ( `[AssemblyTitle]`například) v souboru AssemblyInfo.cs. Ve výchozím nastavení budou nové projekty ve stylu sady SDK tyto atributy generovat na základě vlastností v souboru csproj. Vzhledem k tomu, že v tomto případě nechcete, aby k tomu docházelo (automaticky vygenerovaný atribut by byl v konfliktu s hodnotami z AssemblyInfo.cs), zakážete `<GenerateAssemblyInfo>`automaticky generované atributy pomocí.

- I když soubory *RESX* jsou automaticky zahrnuty jako vložené prostředky, `<Resource>` jiné položky jako obrázky nejsou. Proto zkopírujte `<Resource>` prvky pro vkládání obrázků a souborů ikon. Můžete zjednodušit odkazy PNG na jeden řádek pomocí nového formátu souboru projektu, který je podporován pro vzory expanze názvů: `<Resource Include="**\*.png" />`.

- Podobně jsou `<None>` položky automaticky zahrnuty, ale ve výchozím nastavení nejsou zkopírovány do výstupního adresáře. Vzhledem k tomu, že projekt `<None>` fazolového účastníka obsahuje položku, která *je* zkopírována `PreserveNewest` do výstupního adresáře (pomocí chování), je `<None>` třeba aktualizovat automaticky vyplněnou položku pro tento soubor, například.

  ```xml
  <None Update="BeanTrader.pfx">
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </None>
  ```

- Ukázka pro obchodníka Bob zahrnuje soubor XAML (default. akcent. XAML) jako `Content` (nikoli jako `Page`), protože motivy a zvýraznění definované v tomto souboru jsou načteny z XAML souboru za běhu, místo aby se vložily do samotné aplikace. Nový projektový systém automaticky zahrne tento soubor jako `<Page>`, protože se jedná o soubor XAML. Proto je nutné soubor XAML odebrat jako stránku (`<Page Remove="**\Default.Accent.xaml" />`) a přidat jej jako obsah.

  ```xml
  <Content Include="Resources\Themes\Default.Accent.xaml">
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </Content>
  ```

- Nakonec přidejte odkazy na NuGet tím, že `<ItemGroup>` zkopírujete všechny `<PackageReference>` prvky. Pokud jste jste dříve upgradovali balíčky NuGet na verze kompatibilní se standardem .NET Core, můžete to udělat, pokud jsou odkazy na balíček v projektu specifickém pro .NET Core.

V tomto okamžiku by mělo být možné přidat nový projekt do řešení BeanTrader a otevřít ho v aplikaci Visual Studio. Projekt by měl vypadat správně v **Průzkumník řešení**a `dotnet restore BeanTraderClient.Core.csproj` měl by úspěšně obnovit balíčky (se dvěma očekávanými upozorněními souvisejícími s verzí MahApps. metro, kterou používáte cílení .NET Framework).

I když je možné uchovávat oba soubory projektu souběžně (a může to být žádoucí, pokud chcete zachovat původní projekt přesně tak, jak byl), ztěžuje proces migrace (tyto dva projekty se pokusí použít stejné složky bin a obj) a obvykle není nutné. Pokud chcete sestavovat pro cíle .NET Core i .NET Framework, můžete `<TargetFramework>netcoreapp3.0</TargetFramework>` `<TargetFrameworks>netcoreapp3.0;net472</TargetFrameworks>` místo toho nahradit vlastnost v novém souboru projektu. V případě ukázky pro obchodní oddělení odstraňte starý soubor projektu (BeanTraderClient. csproj), protože už není potřeba. Pokud chcete zachovat oba soubory projektu, nezapomeňte je nechat sestavit do různých výstupních a zprostředkujících výstupních cest.

## <a name="fix-build-issues"></a>Opravit problémy sestavení

Třetí krok procesu přenosu získává projekt, který se má sestavit. Některé aplikace budou po převedení souboru projektu na projekt ve stylu sady SDK již sestaveny úspěšně. Pokud je to váš případ pro vaši aplikaci, Blahopřejeme! Můžete přejít ke kroku 4. Ostatní aplikace budou potřebovat nějaké aktualizace, aby je mohli sestavit pro .NET Core. Pokud se pokusíte spustit `dotnet build` ukázkový projekt v programu Bob obchodník, například (nebo ho sestavit v aplikaci Visual Studio), dojde k velkému počtu chyb, ale budete je moct rychle opravit.

### <a name="systemservicemodel-references-and-microsoftwindowscompatibility"></a>Odkazy na System. ServiceModel a Microsoft. Windows. Compatibility

Ve společném zdroji chyb chybí odkazy pro rozhraní API, která jsou k dispozici pro .NET Core, ale nejsou automaticky zahrnutá do aplikace .NET Core Metapackage. Pokud to chcete vyřešit, měli byste se `Microsoft.Windows.Compatibility` na balíček odkazovat. Balíček kompatibility zahrnuje širokou škálu rozhraní API, která jsou společná pro desktopové aplikace pro Windows, jako je například klient WCF, adresářové služby, registr, konfigurace, rozhraní API seznamů ACL a další.

V případě ukázky v programu Bob obchodník je většina chyb sestavení způsobena chybějícími <xref:System.ServiceModel> typy. Ty je možné řešit pomocí odkazů na potřebné balíčky NuGet WCF. Klientská rozhraní API WCF jsou mezi systémy přítomnými v `Microsoft.Windows.Compatibility` balíčku, a to i tak, aby odkazovaly na balíček kompatibility ještě lepším řešením (protože taky řeší všechny problémy související s rozhraními API a také řešení problémů, ke kterým balíček kompatibility zpřístupňuje přístup). `Microsoft.Windows.Compatibility` Balíček pomáhá ve většině scénářů pro přenos rozhraní .net Core 3,0 WPF a WinForms. Po přidání odkazu na NuGet do `Microsoft.Windows.Compatibility`se zachová jenom jedna chyba buildu!

### <a name="cleaning-up-unused-files"></a>Čištění nepoužívaných souborů

Jeden typ problému migrace, který se často týká souborů C# a XAML, které nebyly dříve zahrnuty do sestavení, vybírají nové projekty ve stylu sady SDK, které zahrnují *všechny* zdroje automaticky.

Další chyba sestavení, kterou vidíte v ukázce pro obchodní vztah, odkazuje na chybnou implementaci rozhraní v *OldUnusedViewModel.cs*. Název souboru je pomocný parametr, ale při kontrole zjistíte, že tento zdrojový soubor není správný. Nezpůsobila problémy dříve, protože neobsahovala původní .NET Framework projekt. Zdrojové soubory, které byly přítomny na disku, ale nejsou zahrnuté do starého souboru *csproj* , jsou teď zahrnuté automaticky.

V případě nedostatku problému se dá snadno porovnat s předchozími *csproj* a potvrdit, že soubor není potřeba, a pak ho buď `<Compile Remove="" />` nebo, pokud už zdrojový soubor ještě není potřeba, odstranit. V tomto případě je bezpečné jenom odstranit *OldUnusedViewModel.cs*.

Pokud máte mnoho zdrojových souborů, které by musely být vyloučeny tímto způsobem, můžete zakázat automatické zahrnutí souborů jazyka C# nastavením `<EnableDefaultCompileItems>` vlastnosti na hodnotu false v souboru projektu. Pak můžete zkopírovat `<Compile Include>` položky ze starého souboru projektu do nového, aby bylo možné sestavit pouze zdroje, které mají být zahrnuty. Podobně `<EnableDefaultPageItems>` lze použít k vypnutí automatického zahrnutí stránek XAML a `<EnableDefaultItems>` může řídit jak jedinou vlastností.

### <a name="a-brief-aside-on-multi-pass-compilers"></a>Stručný výběr v kompilátorech s více průchody

Po odebrání problematického souboru z ukázky pro obchodníka z fazolového účastníka můžete znovu sestavit a zobrazí se čtyři chyby. Ještě nemáte nějaké předplatné? Proč počet chyb zachází? Kompilátor jazyka C# je [Vícenásobný předávací kompilátor](https://docs.microsoft.com/archive/blogs/ericlippert/how-many-passes). To znamená, že každý zdrojový soubor projde dvakrát. Za prvé kompilátor pouze prohlíží metadata a deklarace v každém zdrojovém souboru a identifikuje všechny problémy na úrovni deklarace. Jedná se o chyby, které jste opravili. Poté provede kód znovu a sestaví zdroj C# do IL; Ty jsou druhou sadou chyb, které vidíte nyní.

> [!NOTE]
> Kompilátor jazyka C# provede [více než pouze dva průchody](https://docs.microsoft.com/archive/blogs/ericlippert/how-many-passes), ale konečný výsledek je, že chyby kompilátoru pro velké změny kódu, jako by to vedlo k tomu, že jsou dva vlny.

### <a name="third-party-dependency-fixes-castlewindsor"></a>Opravy závislostí třetích stran (Castle. Windsor)

Další třídou problému, která se nachází v některých scénářích migrace, jsou rozdíly v rozhraní API mezi .NET Framework a verzemi závislostí .NET Core. I v případě, že balíček NuGet cílí na .NET Framework i .NET Standard nebo .NET Core, můžou existovat různé knihovny pro použití s různými cíli .NET. Díky tomu mohou balíčky podporovat mnoho různých platforem .NET, které mohou vyžadovat různé implementace. Také to znamená, že při cílení na různé platformy .NET můžou knihovny obsahovat malé rozdíly v rozhraní API.

Další sada chyb, které vidíte v ukázce obchodníka v programu Bob, se vztahuje `Castle.Windsor` na rozhraní API. Projekt .NET Core Bob používá stejnou verzi `Castle.Windsor` jako projekt cílený na .NET Framework (4.1.1), ale implementace těchto dvou platforem se mírně liší.

V takovém případě se zobrazí následující problémy, které je potřeba opravit:

1. `Castle.MicroKernel.Registration.Classes.FromThisAssembly`není k dispozici v .NET Core. K dispozici je však podobné rozhraní API `Classes.FromAssemblyContaining` , takže můžeme nahradit obě použití `Classes.FromThisAssembly()` voláním metody `Classes.FromAssemblyContaining(t)`, kde `t` je typ, který provádí volání.
1. Podobně v *Bootstrapper.cs* `Castle.Windsor.Installer.FromAssembly`. Tato technologie není v .NET Core dostupná. Místo toho lze toto volání nahradit pomocí `FromAssembly.Containing(typeof(Bootstrapper))`.

### <a name="updating-wcf-client-usage"></a>Aktualizace využití klienta WCF

V případě, `Castle.Windsor` že jsou rozdíly vyřešeny, poslední zbývající chyba sestavení v projektu .NET Core Bob obchodník `BeanTraderServiceClient` je, že (která `DuplexClientBase`je odvozena z `Open` ) nemá metodu. To není překvapivé, protože se jedná o rozhraní API, které na začátku tohoto procesu migrace zvýrazní analyzátor přenositelnosti .NET. Podíváme se na to, co `BeanTraderServiceClient` se věnuje pozornost většímu problému, ale. Tento klient WCF byl automaticky vygenerován nástrojem [Svcutil. exe](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) .

**Klienti WCF vygenerované službou Svcutil jsou určeny pro použití v .NET Framework.**

Řešení, která používají Svcutil klienty WCF, budou muset znovu vygenerovat klienty kompatibilní s .NET Standard pro použití s .NET Core. Jedním z hlavních důvodů, proč původní klienti nebudou fungovat, jsou závislé na konfiguraci aplikací pro definování vazeb a koncových bodů WCF. Protože .NET Standard rozhraní API WCF můžou pracovat na různých platformách (kde nejsou k dispozici rozhraní API pro System. Configuration), klienti WCF pro scénáře .NET Core a .NET Standard musí definovat vazby a koncové body programově místo v konfiguraci.

Ve skutečnosti bude nutné změnit použití všech klientů WCF, který `<system.serviceModel>` závisí na oddílu App. config (ať už vytvořené pomocí Svcutil nebo ručně), aby fungovalo na .NET Core.

Existují dva způsoby, jak automaticky generovat .NET Standard kompatibilních klientů WCF:

- Tento `dotnet-svcutil` nástroj je nástroj .NET, který GENERUJE klienty WCF způsobem, který je podobný tomu, jak Svcutil pracovali dříve.
- Visual Studio může generovat klienty WCF pomocí možnosti [reference webové služby WCF](../../core/additional-tools/wcf-web-service-reference-guide.md) funkce připojené služby.

Oba postupy fungují dobře. Můžete samozřejmě napsat kód klienta WCF sami. V této ukázce se používá funkce připojená služba sady Visual Studio. Provedete to tak, že kliknete pravým tlačítkem na projekt *BeanTraderClient. Core* v Průzkumníku řešení sady Visual Studio a vyberete **Přidat** > **připojenou službu**. Dále vyberte poskytovatele referencí webové služby WCF. Tím se zobrazí dialogové okno, kde můžete zadat adresu webové služby back-end účastníka (`localhost:8080` Pokud používáte server místně) a obor názvů, který mají generované typy použít (například**BeanTrader. Service**).

![Dialogová okna propojené služby odkazu webové služby WCF](./media/convert-project-from-net-framework/connected-service-dialog.png)

Po výběru tlačítka **Dokončit** je do projektu přidán nový uzel připojené služby a do tohoto uzlu bude přidán soubor reference.cs, který obsahuje .NET Standard nového klienta WCF pro přístup ke službě pro přístup k nástroji fazole. Pokud se podíváte `GetEndpointAddress` na `GetBindingForEndpoint` metody nebo v tomto souboru, uvidíte, že vazby a koncové body se nyní generují programově (místo pomocí konfigurace aplikace). Funkce přidat připojené služby může také přidat odkazy na některé balíčky System. ServiceModel v souboru projektu, které nejsou potřeba, protože všechny potřebné balíčky WCF jsou zahrnuté přes Microsoft. Windows. Compatibility. Zkontrolujte csproj a podívejte se, jestli se přidaly další `<PackageReference>` položky System. ServiceModel, a pokud ano, odeberte je.

Náš projekt teď má nové třídy klienta WCF (v *reference.cs*), ale zároveň má i staré (v BeanTrader.cs). V tuto chvíli jsou k dispozici dvě možnosti:

- Pokud chcete mít možnost sestavit původní .NET Framework projekt (společně s novým cílem rozhraní .NET Core), můžete použít `<Compile Remove="BeanTrader.cs" />` položku v souboru csproj projektu .NET Core tak, aby .NET Framework a verze .NET Core aplikace používaly různé klienty WCF. Tato výhoda má opustit stávající projekt .NET Framework beze změny, ale má nevýhodu, že kód pomocí generovaných klientů WCF může být v případě .NET Core v případě, že je v projektu .NET Framework, trochu odlišný, takže pravděpodobně budete muset použít `#if` direktivy k podmíněně zkompilování některých využití klientů WCF (vytváření klientů, například), aby fungovaly jedním ze způsobů, jak je sestaven pro .NET Core, a jiný způsob, jak je sestaven pro .NET Framework.

- Pokud je naopak některé změny kódu v existujícím projektu .NET Framework přijatelné, můžete *BeanTrader.cs* vše odebrat dohromady. Vzhledem k tomu, že nový klient služby WCF je sestaven pro .NET Standard, bude fungovat ve scénářích .NET Core i .NET Framework. Pokud sestavíte pro .NET Framework kromě .NET Core (buď pomocí cílení na více platforem, nebo se dvěma soubory csproj), můžete tento nový soubor *reference.cs* použít pro oba cíle. Tento přístup má výhodu, že kód nemusí bifurcate k podpoře dvou různých klientů WCF. stejný kód bude použit všude. Nevýhodou je, že zahrnuje změnu (PŘEDPOKLÁDANĚ stabilní) .NET Framework projektu.

V případě ukázky programu Bob obchodník můžete v původním projektu provést drobné změny, pokud to usnadňuje migraci, takže pomocí těchto kroků sjednotete použití klientů WCF:

01. Přidejte nový soubor Reference.cs do projektu .NET Framework *BeanTraderClient. csproj* pomocí kontextové nabídky Přidat existující položku z Průzkumníka řešení. Nezapomeňte přidat "as Link", aby oba projekty používaly stejný soubor (na rozdíl od kopírování souboru v jazyce C#). Pokud vytváříte rozhraní .NET Core i .NET Framework s jedním csproj (pomocí cílení na více platforem), tento krok není nezbytný.

01. Odstraňte *BeanTrader.cs*.

01. Nový klient služby WCF je podobný původnímu, ale několik oborů názvů v generovaném kódu se liší. Z tohoto důvodu je nutné aktualizovat projekt tak, aby se typy klientů WCF používaly ze služby BeanTrader. Service (nebo libovolného názvu oboru názvů, který jste zvolili) místo BeanTrader. model nebo bez oboru názvů. Sestavování *BeanTraderClient. Core. csproj* vám pomůže zjistit, kde se tyto změny musí provést. Opravy budou potřeba v C# i ve zdrojových souborech XAML.

01. Nakonec zjistíte, že v *BeanTraderServiceClientFactory.cs* dojde k chybě, protože se změnily dostupné konstruktory pro `BeanTraderServiceClient` daný typ. Slouží k zadání `InstanceContext` argumentu (který byl vytvořen pomocí `CallbackHandler` z kontejneru `Castle.Windsor` IOC). Nové konstruktory vytvoří nové `CallbackHandler`s. Existují však konstruktory v `BeanTraderServiceClient`základním typu, které odpovídají požadovaným požadavkům. Vzhledem k tomu, že automaticky generovaný kód klienta WCF existuje v dílčích třídách, je možné jej snadno zvětšit. Chcete-li to provést, vytvořte nový soubor s názvem *BeanTraderServiceClient.cs* a pak vytvořte částečnou třídu se stejným názvem (pomocí oboru názvů BeanTrader. Service). Pak přidejte jeden konstruktor na částečný typ, jak je znázorněno zde.

    ```csharp
    public BeanTraderServiceClient(System.ServiceModel.InstanceContext callbackInstance) :
        base(callbackInstance, EndpointConfiguration.NetTcpBinding_BeanTraderService)
            { }
    ```

V případě těchto změn nyní bude ukázka pro obchodníky v programu Bob používat nového klienta WCF kompatibilního s .NET Standard a můžete provést konečnou opravu změny `Open` volání v *TradingService.cs* . `await OpenAsync`

S vyřešenými problémy WCF se nyní sestavuje verze .NET Core ukázkového obchodníka v programu Bob.

## <a name="runtime-testing"></a>Testování za běhu

Je snadné se zapomenout, že migrace se neprovádí ihned po vyčištění sestavení projektu proti .NET Core. Je důležité, abyste ponechali čas při testování portu aplikace. Jakmile se všechno úspěšně sestaví, ujistěte se, že aplikace běží a funguje podle očekávání, zvlášť pokud používáte jakékoliv balíčky cílené .NET Framework.

Pojďme se pokusit spustit aplikaci s portem pro obchodní informování a zjistit, co se stane. Aplikace se před selháním nezdaří s následující výjimkou.

```output
System.Configuration.ConfigurationErrorsException: 'Configuration system failed to initialize'

Inner Exception
ConfigurationErrorsException: Unrecognized configuration section system.serviceModel.
```

To samozřejmě dává smysl. Pamatujte, že WCF už nepoužívá konfiguraci aplikací, takže je potřeba odebrat starý oddíl System. serviceModel souboru App. config. Aktualizovaný klient služby WCF zahrnuje všechny stejné informace ve svém kódu, takže konfigurační oddíl už není potřeba. Pokud jste chtěli nakonfigurovat koncový bod WCF v App. config, můžete ho přidat jako nastavení aplikace a aktualizovat kód klienta WCF pro načtení koncového bodu služby WCF z konfigurace.

Po odebrání oddílu System. serviceModel v *App. config*se aplikace spustí, ale když se uživatel přihlásí, dojde k chybě s jinou výjimkou.

```output
System.PlatformNotSupportedException: 'Operation is not supported on this platform.'
```

Nepodporované rozhraní API `Func<T>.BeginInvoke`je. Jak je vysvětleno v [dotnet/corefx # 5940](https://github.com/dotnet/corefx/issues/5940), .NET Core nepodporuje `BeginInvoke` metody `EndInvoke` a na typech delegátů z důvodu základních závislostí vzdálené komunikace. Tento problém a jeho opravu jsou podrobněji popsány v článku [migrace delegáta. BeginInvoke volání pro](https://devblogs.microsoft.com/dotnet/migrating-delegate-begininvoke-calls-for-net-core/) Blogový příspěvek .NET Core, ale v registru `BeginInvoke` je `EndInvoke` to, že pokud je `Task.Run` to možné, by volání měla být nahrazena (nebo asynchronními alternativami). Když použijete obecné řešení, `BeginInvoke` volání se dá nahradit `Invoke` voláním spuštěným v. `Task.Run`

```csharp
Task.Run(() =>
{
    return userInfoRetriever.Invoke();
}).ContinueWith(result =>
{
    // BeginInvoke's callback is replaced with ContinueWith
    var task = result.ConfigureAwait(false);
    CurrentTrader = task.GetAwaiter().GetResult();
}, TaskScheduler.Default);
```

Po odebrání `BeginInvoke` použití se aplikace Bob obchodník úspěšně spustí pro .NET Core.

![Obchodník pro fazole běžící v .NET Core](./media/convert-project-from-net-framework/running-on-core.png)

Všechny aplikace se liší, takže konkrétní kroky potřebné k migraci vlastních aplikací do .NET Core se budou lišit. Ale snad v ukázce Bob obchodník ukazuje obecný pracovní postup a typy problémů, které je možné očekávat. A i přes délku tohoto článku se skutečné změny potřebné v ukázce pro obchodníka v rámci nástroje Bob, aby fungovaly v .NET Core, byly poměrně omezené. Mnoho aplikací migruje do .NET Core stejným způsobem; s omezením nebo dokonce bez nutnosti změn kódu.
