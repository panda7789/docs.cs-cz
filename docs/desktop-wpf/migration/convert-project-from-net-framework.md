---
title: Migrace aplikací WPF do rozhraní .NET Core 3.0
description: Přečtěte si, jak migrovat aplikaci WPF (Windows Presentation Foundation) do rozhraní .NET Core 3.0.
author: mjrousos
ms.date: 09/12/2019
ms.author: mikerou
ms.openlocfilehash: f52005e7c8a6312b8c4e09a950f1f635af1894e4
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "82071309"
---
# <a name="migrating-wpf-apps-to-net-core"></a>Migrace aplikací WPF do jádra rozhraní .NET Core

Tento článek popisuje kroky potřebné k migraci aplikace WPF (Windows Presentation Foundation) z rozhraní .NET Framework do .NET Core 3.0. Pokud nemáte aplikaci WPF po ruce k portu, ale chtěli byste vyzkoušet proces, můžete použít ukázkovou aplikaci **Bean Trader,** která je k dispozici na [GitHubu](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader). Původní aplikace (cílení na rozhraní .NET Framework 4.7.2) je k dispozici ve složce NetFx\BeanTraderClient. Nejprve vysvětlíme kroky nezbytné k portování aplikací obecně a pak projdeme konkrétní změny, které se vztahují na ukázku **Bean Trader.**

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

Chcete-li migrovat do jádra .NET, musíte nejprve:

01. Pochopit a aktualizovat závislosti NuGet:

    01. Upgrade NuGet závislosti používat `<PackageReference>` formát.
    01. Zkontrolujte závislosti NuGet nejvyšší úrovně pro kompatibilitu s jádrem .NET nebo .NET Standard.
    01. Upgradujte balíčky NuGet na novější verze.
    01. Pomocí [analyzátoru přenositelnosti rozhraní .NET](../../standard/analyzers/portability-analyzer.md) porozumíte závislostem rozhraní .NET.

01. Migrujte soubor projektu do nového formátu ve stylu sady SDK:

    01. Zvolte, zda chcete cílit na rozhraní .NET Core i .NET Framework nebo pouze na .NET Core.
    01. Zkopírujte příslušné vlastnosti a položky souboru projektu do nového souboru projektu.

01. Řešení problémů se sestavením:

    01. Přidejte odkaz na balíček [Microsoft.Windows.Compatibility.](https://www.nuget.org/packages/Microsoft.Windows.Compatibility/)
    01. Najděte a opravte rozdíly na úrovni rozhraní API.
    01. Odebrání jiných oddílů *app.config* než `appSettings` nebo `connectionStrings`.
    01. V případě potřeby vygenerujte generovaný kód.

01. Testování za běhu:

    01. Potvrďte, že přenesená aplikace funguje podle očekávání.
    01. Dejte si <xref:System.NotSupportedException> pozor na výjimky.

## <a name="about-the-sample"></a>O vzorku

Tento článek odkazuje na [ukázkovou aplikaci Bean Trader,](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader) protože používá různé závislosti podobné těm, které mohou mít skutečné aplikace WPF. Aplikace není velká, ale má být krok nahoru od "Hello World" z hlediska složitosti. Aplikace ukazuje některé problémy, se kterými se uživatelé mohou setkat při přenosu skutečných aplikací. Aplikace komunikuje se službou WCF, takže aby správně běžela, budete také muset spustit projekt BeanTraderServer (k dispozici ve stejném úložišti GitHub) a ujistěte se, že konfigurace BeanTraderClient odkazuje na správný koncový bod. (Ve výchozím nastavení ukázka předpokládá, že server *http://localhost:8090*běží na stejném počítači na , což bude pravda, pokud spustíte BeanTraderServer místně.)

Mějte na paměti, že tato ukázková aplikace je určena k předvedení rozhraní .NET Core výzvy a řešení. Není určen k prokázání WPF osvědčené postupy. Ve skutečnosti, to záměrně obsahuje některé anti-vzory, aby se ujistil, narazíte alespoň na pár zajímavých výzev při portování.

## <a name="getting-ready"></a>Příprava

Primární výzvou migrace aplikace rozhraní .NET Framework do služby .NET Core je, že její závislosti mohou fungovat jinak nebo vůbec. Migrace je mnohem jednodušší, než bývala; mnoho balíčků NuGet nyní cílí na standard .NET. Počínaje rozhraním .NET Core 2.0 se oblasti .NET Framework a .NET Core staly podobnými. I tak zůstávají některé rozdíly (jak v podpoře z balíčků NuGet, tak v dostupných rozhraních API .NET). Prvním krokem při migraci je kontrola závislostí aplikace a ujistěte se, že odkazy jsou ve formátu, který se snadno migruje do jádra .NET Core.

### <a name="upgrade-to-packagereference-nuget-references"></a>Upgrade `<PackageReference>` na odkazy NuGet

Starší projekty rozhraní .NET Framework obvykle uvádějí své závislosti NuGet v souboru *packages.config.* Nový formát souboru projektu ve stylu sady SDK odkazuje na balíčky NuGet jako [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) na prvky v samotném souboru csproj, nikoli v samostatném konfiguračním souboru.

Při migraci existují dvě výhody `<PackageReference>`použití odkazů ve stylu:

- Toto je styl odkazu NuGet, který je vyžadován pro nový soubor projektu .NET Core. Pokud již používáte `<PackageReference>`, tyto prvky souboru projektu lze zkopírovat a vložit přímo do nového projektu.
- Na rozdíl od souboru `<PackageReference>` packages.config elementy odkazují pouze na závislosti nejvyšší úrovně, na kterých projekt přímo závisí. Všechny ostatní přenosité balíčky NuGet budou určeny v době obnovení a zaznamenány v automaticky generovaném souboru obj\project.assets.json. To usnadňuje určení, jaké závislosti má váš projekt, což je užitečné při určování, zda nezbytné závislosti bude fungovat na .NET Core nebo ne.

Prvním krokem migrace aplikace rozhraní .NET Framework do jádra .NET `<PackageReference>` je aktualizace tak, aby používala odkazy NuGet. Visual Studio je to jednoduché. Stačí klepnout pravým tlačítkem myši na soubor *packages.config* projektu v **Průzkumníku řešení**sady Visual Studio a potom vybrat **příkaz Migrovat packages.config na PackageReference**.

![Upgrade na odkaz na balíček](./media/convert-project-from-net-framework/package-reference-migration.png)

Zobrazí se dialogové okno zobrazující vypočtené závislosti NuGet nejvyšší úrovně a dotaz, které další balíčky NuGet by měly být povýšeny na nejvyšší úroveň. Žádný z těchto dalších balíčků nemusí být nejvyšší úroveň pro ukázku Bean Trader, takže můžete zrušit zaškrtnutí všech těchto políček. Potom klepněte na tlačítko **Ok** a soubor `<PackageReference>` *packages.config* je odebrán a prvky jsou přidány do souboru projektu.

`<PackageReference>`-style odkazy neukládají balíčky NuGet místně ve složce balíčky. Místo toho jsou uloženy globálně jako optimalizace. Po dokončení migrace upravte soubor csproj `<Analyzer>` a odstraňte všechny prvky odkazující na analyzátory, které dříve pocházely z *.. \packages* adresáře. Nebojte se; vzhledem k tomu, že stále máte odkazy na balíček NuGet, analyzátory budou zahrnuty do projektu. Stačí vyčistit staré elementy packages.config `<Analyzer>` stylu.

### <a name="review-nuget-packages"></a>Projděte si balíčky NuGet

Teď, když můžete vidět balíčky NuGet nejvyšší úrovně, na kterých projekt závisí, můžete zkontrolovat, zda jsou tyto balíčky k dispozici na .NET Core. Můžete určit, zda balíček podporuje .NET Core při pohledu na jeho závislosti na [nuget.org](https://www.nuget.org/). Fuget.org [web](https://www.fuget.org/) vytvořený komunitou zobrazuje tyto informace výrazně v horní části informační stránky balíčku.

Při cílení na rozhraní .NET Core 3.0 by měly fungovat všechny balíčky zaměřené na rozhraní .NET Core nebo .NET Standard (protože rozhraní .NET Core implementuje plochu .NET Standard). V některých případech konkrétní verze balíčku, který se používá nebude cílit .NET Core nebo .NET Standard, ale novější verze bude. V takovém případě byste měli zvážit upgrade na nejnovější verzi balíčku.

Můžete také použít balíčky zaměřené na rozhraní .NET Framework, ale to představuje určité riziko. Závislosti rozhraní .NET Core to .NET Framework jsou povoleny, protože oblasti povrchu rozhraní .NET Core a .NET Framework jsou natolik podobné, že tyto závislosti *často* fungují. Pokud se však balíček pokusí použít rozhraní .NET API, které není v jádru .NET, dojde k výjimce za běhu. Z tohoto důvodu byste měli odkazovat pouze na balíčky rozhraní .NET Framework, pokud nejsou k dispozici žádné jiné možnosti, a pochopit, že tím se ukládá zkušební zátěž.

Pokud existují odkazy na balíčky, které necílí na .NET Core nebo .NET Standard, budete muset přemýšlet o dalších alternativách:

- Existují jiné podobné balíčky, které lze použít místo? Někdy NuGet autoři publikovat samostatné '. Core' verze jejich knihoven specificky zaměřené na .NET Core. Balíčky enterprise knihovny jsou příkladem publikování komunity ". NetCore" alternativy. V ostatních případech jsou pro soubor .NET Standard k dispozici novější sady SDK pro určitou službu (někdy s různými názvy balíčků). Pokud nejsou k dispozici žádné alternativy, můžete pokračovat pomocí balíčků cílených na rozhraní .NET Framework, s ohledem na to, že je budete muset důkladně otestovat po spuštění v .NET Core.

Ukázka Bean Trader má následující závislosti NuGet nejvyšší úrovně:

- [**Castle.Windsor, verze 4.1.1**](https://www.castleproject.org/projects/windsor/)  

  Tento balíček se zaměřuje na standard .NET Standard 1.6, takže funguje na .NET Core.

- [**Microsoft.CodeAnalysis.FxCopAnalyzers, verze 2.6.3**](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3)  
  Toto je meta balíček, takže není okamžitě zřejmé, které platformy podporuje, ale [dokumentace](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisfxcopanalyzers) znamená, že jeho nejnovější verze (2.9.2) bude fungovat jak pro rozhraní .NET Framework, tak pro .NET Core.

- [**Nito.AsyncEx, verze 4.0.1**](https://www.nuget.org/packages/Nito.AsyncEx/4.0.1)  

  Tento balíček necílí na .NET Core, ale novější verze 5.0 ano. To je běžné při migraci, protože mnoho balíčků NuGet nedávno přidalo podporu .NET Standard, ale starší verze projektu se zaměří pouze na rozhraní .NET Framework. Pokud je rozdíl verzí pouze menší verze rozdíl, je to často snadné upgradovat na novější verzi. Vzhledem k tomu, že se jedná o hlavní změnu verze, musíte být opatrní při upgradu, protože v balíčku může dojít k porušení změn. Existuje však cesta vpřed, což je dobré.

- [**MahApps.Metro, verze 1.6.5**](https://www.nuget.org/packages/MahApps.Metro/1.6.5)  

  Tento balíček také necílí na .NET Core, ale má novější předběžnou verzi (2.0-alpha), která ano. Opět platí, že budete muset dávat pozor na lámání změny, ale novější balíček je povzbudivý.

Bean Trader ukázkové nuget závislosti všechny cíl .NET Standard/.NET Core nebo novější verze, které dělají, takže je nepravděpodobné, že žádné problémy blokování zde.

### <a name="upgrade-nuget-packages"></a>Upgrade balíčků NuGet

Pokud je to možné, bylo by vhodné inovovat verze všech balíčků, které se zaměřují pouze na rozhraní .NET Core nebo .NET Standard s novějšími verzemi v tomto okamžiku (s projektem stále zaměřeným na rozhraní .NET Framework) za účelem včasného zjištění a řešení všech narušujících změn.

Pokud byste raději neprováděli žádné podstatné změny v existující verzi aplikace rozhraní .NET Framework, může to počkat, dokud nebudete mít nový soubor projektu zaměřený na .NET Core. Upgrade balíčků NuGet na verze kompatibilní s rozhraním .NET Core však po vytvoření nového souboru projektu proces migrace ještě více zjednoduší a sníží počet rozdílů mezi verzemi rozhraní .NET Framework a .NET Core aplikace.

S ukázkou Bean Trader lze všechny potřebné upgrady snadno provést (pomocí správce balíčků NuGet sady Visual Studio) s jednou výjimkou: upgrade z **MahApps.Metro 1.6.5** na **2.0** odhalí nejnovější změny související s tématem a nastaveními pro správu zvýraznění.

V ideálním případě by aplikace být aktualizovány použít novější verzi balíčku (vzhledem k tomu, že je pravděpodobnější, že pracovat na .NET Core). V některých případech to však nemusí být proveditelné. V těchto případech neupgradujte **MahApps.Metro,** protože nezbytné změny nejsou triviální a tento kurz se zaměřuje na migraci na .NET Core 3, nikoli na **MahApps.Metro 2.** Také se jedná o závislost na rozhraní .NET Framework s nízkým rizikem, protože aplikace Bean Trader používá pouze malou část **mahapps.metro**. Bude to samozřejmě vyžadovat testování, aby se ujistil, že vše funguje, jakmile je migrace dokončena. Pokud by se jednalo o skutečný scénář, bylo by dobré podat problém sledovat práci přesunout do **MahApps.Metro** verze 2.0, protože nedělá migrace nyní zanechává některé technické dluhy.

Jakmile jsou balíčky NuGet aktualizovány `<PackageReference>` na nejnovější verze, skupina položek v souboru projektu ukázkového souboru Bean Trader by měla vypadat takto.

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

### <a name="net-framework-portability-analysis"></a>Analýza přenositelnosti rozhraní .NET Framework

Jakmile porozumíte stavu závislostí NuGet vašeho projektu, další věc, kterou je třeba zvážit, je .NET Framework API závislosti. Nástroj [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) je užitečný pro pochopení toho, která rozhraní API .NET, která projekt používá, jsou k dispozici na jiných platformách .NET.

Nástroj je dodáván jako [plugin Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), nástroj [příkazového řádku](https://github.com/Microsoft/dotnet-apiport/releases)nebo zabalený do [jednoduchého grafického uživatelského rozhraní](https://github.com/Microsoft/dotnet-apiport-ui), které zjednodušuje jeho možnosti. Další informace o použití nástroje .NET Portability Analyzer (PORT Port Port) pomocí grafického uživatelského rozhraní v příspěvku blogu [Porting desktopových aplikací na .NET Core.](https://devblogs.microsoft.com/dotnet/porting-desktop-apps-to-net-core/) Pokud dáváte přednost použití příkazového řádku, jsou nezbytné kroky:

1. Stáhněte si [analyzátor přenositelnosti .NET,](https://github.com/Microsoft/dotnet-apiport/releases) pokud ho ještě nemáte.
1. Ujistěte se, že aplikace .NET Framework, která má být portována sestavení úspěšně (to je dobrý nápad před migrací bez ohledu na to).
1. Spusťte port rozhraní API s příkazovým řádkem, jako je tento.

    ```console
    ApiPort.exe analyze -f <PathToBeanTraderBinaries> -r html -r excel -t ".NET Core"
    ```

    Argument `-f` určuje cestu obsahující binární soubory k analýze. Argument `-r` určuje, který formát výstupního souboru chcete. Argument `-t` určuje, proti které platformě .NET má být analyzovat využití rozhraní API. V tomto případě chcete .NET Core.

Když otevřete sestavu HTML, první část zobrazí všechny analyzované binární soubory a jaké procento rozhraní API .NET, které používají, jsou k dispozici na cílové platformě. Procento není smysluplné samo o sobě. Co je užitečnější je vidět konkrétní api, které chybí. Chcete-li to provést, vyberte název sestavy nebo posuňte dolů k sestavám pro jednotlivá sestavení.

Zaměřte se na sestavení, pro která vlastníte zdrojový kód. V sestavě ApiPort Bean Trader je například mnoho binárních souborů, ale většina z nich patří do balíčků NuGet. `Castle.Windsor`ukazuje, že závisí na některých rozhraních API System.Web, které chybí v rozhraní .NET Core. To není problém, protože jste `Castle.Windsor` dříve ověřili, že podporuje .NET Core. Je běžné, že balíčky NuGet mají různé binární soubory pro použití s různými `Castle.Windsor` platformami .NET, takže zda je verze rozhraní .NET Framework používá rozhraní API System.Web nebo ne, irelevantní, pokud balíček také cílí na standard .NET nebo .NET Core (což ano).

S ukázkou Bean Trader je jediným binárním souborem, který je třeba **zvážit, BeanTraderClient** a sestava ukazuje, že chybí pouze dvě rozhraní API .NET: `System.ServiceModel.ClientBase<T>.Close` a `System.ServiceModel.ClientBase<T>.Open`.

![Sestava přenositelnosti klienta BeanTrader](./media/convert-project-from-net-framework/portability-report.png)

Ty pravděpodobně neblokují problémy, protože rozhraní API klientů WCF jsou (většinou) podporována v jádru .NET, takže pro tato centrální rozhraní API musí být k dispozici alternativy. Ve skutečnosti při `System.ServiceModel`pohledu na 's <https://apisof.net>.NET Core plochy (pomocí ), uvidíte, že existují asynchronní alternativy v .NET Core místo.

Na základě této sestavy a předchozí analýzy závislostí NuGet, vypadá to, že by měly být žádné hlavní problémy migrace bean Trader vzorku .NET Core. Jste připraveni na další krok, ve kterém skutečně zahájíte migraci.

## <a name="migrating-the-project-file"></a>Migrace souboru projektu

Pokud vaše aplikace nepoužívá nový [formát souboru projektu ve stylu sady SDK](../../core/tools/csproj.md), budete k cílení na jádro .NET potřebovat nový soubor projektu. Můžete nahradit existující soubor csproj, nebo pokud dáváte přednost tomu, aby byl existující projekt v aktuálním stavu nedotčený, můžete přidat nový soubor csproj zaměřený na .NET Core. Můžete vytvořit verze aplikace pro rozhraní .NET Framework a .NET Core s jedním souborem projektu ve `<TargetFrameworks>` stylu sady SDK s [více cíleními](../../standard/library-guidance/cross-platform-targeting.md) (určením více cílů).

Chcete-li vytvořit nový soubor projektu, můžete vytvořit nový projekt `dotnet new wpf` WPF v sadě Visual Studio nebo pomocí příkazu v dočasném adresáři vygenerovat soubor projektu a potom jej zkopírovat nebo přejmenovat do správného umístění. K dispozici je také nástroj vytvořený [komunitou, CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017), který může automatizovat některé migrace souboru projektu. Nástroj je užitečný, ale stále potřebuje člověka, aby přezkoumal výsledky, aby se ujistil, že všechny podrobnosti o migraci jsou správné. Jednou z konkrétních oblastí, které nástroj nezpracovává optimálně je migrace balíčků NuGet ze souborů *packages.config.* Pokud nástroj běží na soubor projektu, který stále používá *soubor packages.config* odkazovat NuGet balíčky, bude migrovat na `<PackageReference>` prvky automaticky, ale přidá `<PackageReference>` prvky pro *všechny* balíčky namísto pouze ty nejvyšší úrovně. Pokud jste již migrovali na`<PackageReference>` prvky s Visual Studio (jako jste to udělali v této ukázce), pak nástroj může pomoci se zbytkem převodu. Stejně jako Scott Hanselman doporučuje ve [svém blogu o migraci csproj soubory](https://www.hanselman.com/blog/UpgradingAnExistingNETProjectFilesToTheLeanNewCSPROJFormatFromNETCore.aspx), portování ručně je vzdělávací a dá lepší výsledky, pokud máte jen několik projektů na port. Ale pokud portujete desítky nebo stovky projektových souborů, pak nástroj jako [CsprojToVs2017] může být nápovědou.

Chcete-li vytvořit nový soubor projektu pro `dotnet new wpf` ukázku Bean Trader, spusťte v dočasném adresáři a přesuňte generovaný soubor *.csproj* do složky *BeanTraderClient* a přejmenujte jej **na BeanTraderClient.Core.csproj**.

Vzhledem k tomu, že nový formát souboru projektu automaticky obsahuje soubory Jazyka C#, *soubory resx* a soubory XAML, které najde v adresáři nebo pod ním, je soubor projektu již téměř dokončen! Chcete-li migraci dokončit, otevřete staré a nové soubory projektu vedle sebe a prohlédněte si staré soubory a zjistěte, zda je třeba migrovat nějaké informace, které obsahuje. V případě vzorku Bean Trader by měly být do nového projektu zkopírovány následující položky:

- Všechny `<RootNamespace>` `<AssemblyName>`vlastnosti `<ApplicationIcon>` , a by měly být zkopírovány.

- Také je třeba `<GenerateAssemblyInfo>false</GenerateAssemblyInfo>` přidat vlastnost do nového souboru projektu, protože ukázka `[AssemblyTitle]`Bean Trader obsahuje atributy na úrovni sestavení (například ) v souboru AssemblyInfo.cs. Ve výchozím nastavení budou nové projekty ve stylu sady SDK automaticky generovat tyto atributy na základě vlastností v souboru csproj. Protože nechcete, aby se tak stalo v tomto případě (automaticky generované atributy by v konfliktu s `<GenerateAssemblyInfo>`těmi z AssemblyInfo.cs), můžete zakázat automaticky generované atributy s .

- Přestože *resx* soubory jsou automaticky zahrnuty jako vložené prostředky, jiné `<Resource>` položky, jako jsou obrázky nejsou. Takže zkopírujte `<Resource>` prvky pro vkládání souborů obrázků a ikon. Odkazy png na jeden řádek můžete zjednodušit pomocí podpory nového formátu souboru `<Resource Include="**\*.png" />`projektu pro globbing patterns: .

- Podobně `<None>` jsou položky zahrnuty automaticky, ale ve výchozím nastavení nejsou zkopírovány do výstupního adresáře. Vzhledem k tomu, `<None>` že projekt Bean Trader obsahuje `PreserveNewest` položku, která *je* zkopírována do výstupního adresáře (pomocí chování), je třeba aktualizovat automaticky vyplněnou `<None>` položku pro tento soubor, takto.

  ```xml
  <None Update="BeanTrader.pfx">
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </None>
  ```

- Ukázka Bean Trader obsahuje soubor XAML (Default.Accent.xaml) `Content` `Page`jako (spíše než jako ) protože motivy a akcenty definované v tomto souboru jsou načteny z XAML souboru za běhu, spíše než vložené do samotné aplikace. Nový projektový systém automaticky zahrnuje `<Page>`tento soubor jako , nicméně, protože je to soubor XAML. Takže musíte odstranit soubor XAML jako stránku`<Page Remove="**\Default.Accent.xaml" />`( ) a přidat jej jako obsah.

  ```xml
  <Content Include="Resources\Themes\Default.Accent.xaml">
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </Content>
  ```

- Nakonec přidejte odkazy NuGet zkopírováním `<ItemGroup>` `<PackageReference>` se všemi prvky. Pokud jste dříve upgradovali balíčky NuGet na verze kompatibilní s jádrem .NET, můžete to udělat nyní, když jsou odkazy na balíček v projektu specifickém pro jádro .NET.

V tomto okamžiku by mělo být možné přidat nový projekt do řešení BeanTrader a otevřít jej v sadě Visual Studio. Projekt by měl vypadat správně `dotnet restore BeanTraderClient.Core.csproj` v **Průzkumníku řešení**a měl by úspěšně obnovit balíčky (se dvěma očekávanými upozorněními souvisejícími s verzí MahApps.Metro, kterou používáte cílení .NET Framework).

I když je možné zachovat oba soubory projektu vedle sebe (a může být dokonce žádoucí, pokud chcete zachovat vytváření starého projektu přesně tak, jak byl), komplikuje proces migrace (dva projekty se pokusí použít stejné bin a obj složky) a obvykle není nutné. Pokud chcete vytvořit pro cíle .NET Core a .NET `<TargetFramework>netcoreapp3.0</TargetFramework>` Framework, můžete `<TargetFrameworks>netcoreapp3.0;net472</TargetFrameworks>` místo toho nahradit vlastnost v novém souboru projektu. Pro ukázku Bean Trader odstraňte starý soubor projektu (BeanTraderClient.csproj), protože již není potřeba. Pokud dáváte přednost zachovat oba soubory projektu, ujistěte se, že je sestavení na jiný výstup a zprostředkující výstupní cesty.

## <a name="fix-build-issues"></a>Řešení problémů se sestavením

Třetím krokem procesu přenosu je získání projektu k sestavení. Některé aplikace se již úspěšně vytvoří, jakmile je soubor projektu převeden na projekt ve stylu sady SDK. Pokud je to váš případ pro vaši aplikaci, gratulujeme! Můžete přejít na krok 4. Ostatní aplikace budou potřebovat některé aktualizace, aby je získaly pro .NET Core. Pokud se pokusíte spustit `dotnet build` na ukázkový projekt Bean Trader nyní, například (nebo jej sestavit v sadě Visual Studio), bude mnoho chyb, ale dostanete je rychle opravit.

### <a name="systemservicemodel-references-and-microsoftwindowscompatibility"></a>Reference System.ServiceModel a Microsoft.Windows.Compatibility

Běžným zdrojem chyb chybí odkazy na rozhraní API, které jsou k dispozici pro rozhraní .NET Core, ale nejsou automaticky zahrnuty do metabalíčku aplikace .NET Core. Chcete-li tento problém `Microsoft.Windows.Compatibility` vyřešit, měli byste odkazovat na balíček. Balíček kompatibility obsahuje širokou sadu rozhraní API, která jsou běžná v aplikacích klasické pracovní plochy systému Windows, jako je klient WCF, adresářové služby, registr, konfigurace, rozhraní API ACA a další.

U ukázky Bean Trader je většina chyb sestavení <xref:System.ServiceModel> způsobena chybějícími typy. Ty by mohly být vyřešeny odkazem na nezbytné balíčky WCF NuGet. WCF klientská rozhraní API patří `Microsoft.Windows.Compatibility` mezi ty, které jsou k dispozici v balíčku, i když, takže odkazování na balíček kompatibility je ještě lepší řešení (protože také řeší všechny problémy související s rozhraní api, stejně jako řešení problémů WCF, že balíček kompatibility zpřístupní). Balíček `Microsoft.Windows.Compatibility` pomáhá ve většině scénářů přenosu .NET Core 3.0 WPF a WinForms. Po přidání odkazu NuGet do `Microsoft.Windows.Compatibility`, zůstane pouze jedna chyba sestavení!

### <a name="cleaning-up-unused-files"></a>Čištění nepoužívaných souborů

Jeden typ problému migrace, který přichází často se týká C# a XAML soubory, které nebyly dříve zahrnuty v sestavení získání zvedl nové projekty ve stylu Sady SDK, které obsahují *všechny* zdroje automaticky.

Další chyba sestavení, kterou vidíte v ukázce Bean Trader, odkazuje na chybné implementaci rozhraní v *OldUnusedViewModel.cs*. Název souboru je nápověda, ale při kontrole zjistíte, že tento zdrojový soubor je nesprávný. Dříve nezpůsobila problémy, protože nebyla zahrnuta v původním projektu rozhraní .NET Framework. Zdrojové soubory, které byly přítomny na disku, ale nebyly zahrnuty do starého *csproj* jsou zahrnuty automaticky nyní.

U jednorázových problémů, jako je tento, je snadné porovnat s předchozím *csproj* potvrdit, že `<Compile Remove="" />` soubor není potřeba, a pak buď to, nebo, pokud zdrojový soubor není potřeba nikde už, odstranit. V tomto případě je bezpečné jen odstranit *OldUnusedViewModel.cs*.

Pokud máte mnoho zdrojových souborů, které by bylo nutné vyloučit tímto způsobem, můžete `<EnableDefaultCompileItems>` zakázat automatické zahrnutí souborů Jazyka C# nastavením vlastnosti false v souboru projektu. Potom můžete zkopírovat `<Compile Include>` položky ze starého souboru projektu do nového, abyste mohli vytvářet pouze zdroje, které jste chtěli zahrnout. Podobně `<EnableDefaultPageItems>` lze vypnout automatické zahrnutí stránek XAML `<EnableDefaultItems>` a můžete řídit jak s jednou vlastností.

### <a name="a-brief-aside-on-multi-pass-compilers"></a>Stručný stranou na multi-pass kompilátory

Po odstranění problematického souboru z ukázky Bean Trader můžete znovu sestavit a získáte čtyři chyby. Neměl jsi ho předtím? Proč se počet chyb zvýšil? Kompilátor Jazyka C# je [víceprůchodový kompilátor](https://docs.microsoft.com/archive/blogs/ericlippert/how-many-passes). To znamená, že prochází každý zdrojový soubor dvakrát. Nejprve kompilátor pouze vyhledá metadata a deklarace v každém zdrojovém souboru a identifikuje všechny problémy na úrovni deklarace. To jsou chyby, které jste opravili. Pak znovu projde kódem k sestavení zdroje C# do IL; to jsou druhá sada chyb, které vidíte nyní.

> [!NOTE]
> Kompilátor Jazyka C# provádí [více než jen dva průchody](https://docs.microsoft.com/archive/blogs/ericlippert/how-many-passes), ale konečným výsledkem je, že chyby kompilátoru pro velké změny kódu, jako je tento, mají tendenci přijít ve dvou vlnách.

### <a name="third-party-dependency-fixes-castlewindsor"></a>Opravy závislostí třetích stran (Castle.Windsor)

Další třídou problému, která se objevuje v některých scénářích migrace, jsou rozdíly rozhraní API mezi rozhraním .NET Framework a .NET Core verzemi závislostí. I v případě, že balíček NuGet cílí na rozhraní .NET Framework i na rozhraní .NET Standard nebo .NET Core, mohou existovat různé knihovny pro použití s různými cíli .NET. To umožňuje balíčky pro podporu mnoha různých platforem .NET, které mohou vyžadovat různé implementace. To také znamená, že může být malé rozdíly rozhraní API v knihovnách při cílení různých platformách .NET.

Další sada chyb, které se zobrazí ve vzorku Bean Trader, souvisí `Castle.Windsor` s api. Projekt .NET Core Bean Trader používá `Castle.Windsor` stejnou verzi jako projekt cílený na rozhraní .NET Framework (4.1.1), ale implementace pro tyto dvě platformy se mírně liší.

V takovém případě se zobrazí následující problémy, které je třeba opravit:

1. `Castle.MicroKernel.Registration.Classes.FromThisAssembly`není k dispozici na .NET Core. Existuje však podobné rozhraní `Classes.FromAssemblyContaining` API k dispozici, takže `Classes.FromThisAssembly()` můžeme `Classes.FromAssemblyContaining(t)`nahradit `t` obě použití s voláním , kde je typ volání.
1. Podobně v *Bootstrapper.cs* `Castle.Windsor.Installer.FromAssembly`. . To to není k dispozici na .NET Core. Místo toho může být toto volání nahrazeno . `FromAssembly.Containing(typeof(Bootstrapper))`

### <a name="updating-wcf-client-usage"></a>Aktualizace využití klienta WCF

`Castle.Windsor` Po opevnění rozdílů je poslední zbývající chyba sestavení v projektu .NET Core Bean Trader ta `Open` `BeanTraderServiceClient` (která je odvozena z) `DuplexClientBase`nemá metodu. To není překvapující, protože se jedná o rozhraní API, které bylo zvýrazněno analyzátorem přenosové schopnosti .NET na začátku tohoto procesu migrace. Při `BeanTraderServiceClient` pohledu na upozorňuje me na větší problém, ačkoli. Tento klient WCF byl automaticky generován nástrojem [Svcutil.exe.](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)

**WCF klienti generované Svcutil jsou určeny pro použití na rozhraní .NET Framework.**

Řešení, která používají klienty WCF generované svcutil, budou muset znovu vygenerovat klienty kompatibilní se standardem .NET pro použití s rozhraním .NET Core. Jedním z hlavních důvodů, proč staří klienti nebudou fungovat, je, že závisí na konfiguraci aplikace pro definování vazby WCF a koncových bodů. Vzhledem k tomu, že rozhraní API WCF standardu .NET mohou fungovat napříč platformami (kde rozhraní API System.Configuration NEJSOU k dispozici), musí klienti WCF pro scénáře .NET Core a .NET Standard definovat vazby a koncové body programově namísto v konfiguraci.

Ve skutečnosti jakékoli wcf využití klienta, který závisí na `<system.serviceModel>` app.config části (zda vytvořené s Svcutil nebo ručně) bude muset být změněn a pracovat na .NET Core.

Existují dva způsoby automatického generování klientů WCF kompatibilních se standardem .NET:

- Nástroj `dotnet-svcutil` je nástroj .NET, který generuje wcf klienty způsobem, který je podobný tomu, jak Svcutil pracoval dříve.
- Visual Studio může generovat klienty WCF pomocí [možnosti WCF Web Service Reference](../../core/additional-tools/wcf-web-service-reference-guide.md) jeho funkce Připojené služby.

Oba přístup funguje dobře. Případně, samozřejmě, můžete napsat kód klienta WCF sami. V této ukázce jsem se rozhodl použít funkci Visual Studio Connected Service. Chcete-li to provést, klikněte pravým tlačítkem myši na projekt *BeanTraderClient.Core* v průzkumníku řešení sady Visual Studio a vyberte **přidat** > **připojenou službu**. Dále zvolte wcf webové služby referenčního zprostředkovatele. Tím se zobrazí dialogové okno, kde můžete zadat adresu webové služby back-end Bean Trader (pokud`localhost:8080` používáte server místně) a obor názvů, který by měl ygenerovat typy ( například**BeanTrader.Service).**

![Dialogové okno Připojené služby wcf webové služby](./media/convert-project-from-net-framework/connected-service-dialog.png)

Po výběru tlačítka **Dokončit** je do projektu přidán nový uzel Připojené služby a pod tento uzel, který obsahuje nového klienta WCF standardu .NET pro přístup ke službě Bean Trader, je přidán soubor Reference.cs. Pokud se podíváte na `GetEndpointAddress` metody nebo `GetBindingForEndpoint` v tomto souboru, uvidíte, že vazby a koncové body jsou nyní generovány programově (namísto prostřednictvím konfigurace aplikace). Funkce Přidat připojené služby může také přidat odkazy na některé balíčky System.ServiceModel v souboru projektu, které nejsou potřeba, protože všechny potřebné balíčky WCF jsou zahrnuty prostřednictvím Microsoft.Windows.Compatibility. Zkontrolujte csproj, zda byly přidány `<PackageReference>` nějaké další položky System.ServiceModel, a pokud ano, odstraňte je.

Náš projekt má nyní nové třídy klientů WCF (v *Reference.cs),* ale stále má i ty staré (v BeanTrader.cs). V tomto okamžiku existují dvě možnosti:

- Pokud chcete mít možnost sestavit původní projekt rozhraní .NET Framework (vedle nového projektu cíleného na jádro .NET), můžete použít položku `<Compile Remove="BeanTrader.cs" />` v souboru csproj projektu .NET Core tak, aby verze .NET Framework a .NET Core aplikace používaly různé klienty WCF. To má tu výhodu, že ponechává existující projekt rozhraní .NET Framework beze změny, ale má nevýhodu, že kód pomocí generované wcf klienty může být nutné mírně `#if` lišit v případě .NET Core, než tomu bylo v projektu rozhraní .NET Framework, takže budete pravděpodobně muset použít direktivy podmíněně zkompilovat některé wcf klienta použití (vytváření klientů, například) pracovat jedním způsobem při sestavení pro .NET Core a jiným způsobem při sestavení pro rozhraní .NET Framework.

- Pokud na druhé straně některé změny kódu v existujícím projektu rozhraní .NET Framework je přijatelné, můžete odebrat *BeanTrader.cs* všechny dohromady. Vzhledem k tomu, že nový klient WCF je vytvořen pro standard .NET, bude fungovat ve scénářích .NET Core i .NET Framework. Pokud vytváříte rozhraní .NET Framework navíc k rozhraní .NET Core (buď pomocí více násobného cílení, nebo dvěma soubory csproj), můžete tento nový *soubor Reference.cs* použít pro oba cíle. Tento přístup má výhodu, že kód nebude muset rozdvojit pro podporu dvou různých klientů WCF; stejný kód bude použit všude. Nevýhodou je, že zahrnuje změnu (pravděpodobně stabilní) .NET Framework projektu.

V případě ukázky Bean Trader můžete provést malé změny původního projektu, pokud usnadňuje migraci, postupujte takto a odsouhlasete využití klienta WCF:

01. Přidejte nový soubor Reference.cs do projektu .NET Framework *BeanTraderClient.csproj* pomocí kontextové nabídky "Přidat existující položku" z průzkumníka řešení. Nezapomeňte přidat "jako odkaz", takže stejný soubor je používán oběma projekty (na rozdíl od kopírování souboru C#). Pokud vytváříte pro rozhraní .NET Core i .NET Framework pomocí jednoho csproj (pomocí vícenásobného cílení), není tento krok nutný.

01. Odstranit *BeanTrader.cs*.

01. Nový klient WCF je podobný starému, ale počet oborů názvů ve generovaném kódu se liší. Z tohoto důvodu je nutné aktualizovat projekt tak, aby wcf typy klientů jsou používány z BeanTrader.Service (nebo bez ohledu na název oboru názvů, který jste zvolili) namísto BeanTrader.Model nebo bez oboru názvů. Budování *BeanTraderClient.Core.csproj* pomůže určit, kde je třeba tyto změny provést. Opravy budou potřebné jak v C# a ve zdrojových souborech XAML.

01. Nakonec zjistíte, že je chyba v *BeanTraderServiceClientFactory.cs* protože dostupné konstruktory pro `BeanTraderServiceClient` typ se změnily. Dříve bylo možné zadat `InstanceContext` argument (který byl `CallbackHandler` vytvořen `Castle.Windsor` pomocí kontejneru IoC). Nové konstruktory vytvořit `CallbackHandler`nové s. Existují však konstruktory `BeanTraderServiceClient`v základním typu společnosti , které odpovídají tomu, co chcete. Vzhledem k tomu, že automaticky vygenerovaný kód klienta WCF existuje všechny existují v částečné třídy, můžete jej snadno rozšířit. Chcete-li to provést, vytvořte nový soubor s názvem *BeanTraderServiceClient.cs* a potom vytvořte částečnou třídu se stejným názvem (pomocí oboru názvů BeanTrader.Service). Potom přidejte jeden konstruktor k částečnému typu, jak je znázorněno zde.

    ```csharp
    public BeanTraderServiceClient(System.ServiceModel.InstanceContext callbackInstance) :
        base(callbackInstance, EndpointConfiguration.NetTcpBinding_BeanTraderService)
            { }
    ```

S těmito změnami provedené, bude Bean Trader ukázka nyní používat nový klient WCF kompatibilní `Open` se standardem `await OpenAsync` .NET a můžete provést konečnou opravu změny volání v *TradingService.cs* použít místo.

S problémy WCF vyřešeny , .NET Core verze ukázky Bean Trader nyní staví čistě!

## <a name="runtime-testing"></a>Testování za běhu

Je snadné zapomenout, že migrace práce není provedeno, jakmile projekt vytvoří čistě proti .NET Core. Je důležité ponechat čas na testování portované aplikace. Jakmile se věci úspěšně vytvoří, ujistěte se, že aplikace běží a funguje podle očekávání, zejména pokud používáte všechny balíčky zaměřené na rozhraní .NET Framework.

Zkusme spustit portovnu Bean Trader app a uvidíme, co se stane. Aplikace se nedostane daleko před selháním s následující výjimkou.

```output
System.Configuration.ConfigurationErrorsException: 'Configuration system failed to initialize'

Inner Exception
ConfigurationErrorsException: Unrecognized configuration section system.serviceModel.
```

To dává smysl, samozřejmě. Nezapomeňte, že WCF již nepoužívá konfiguraci aplikace, takže je třeba odebrat starou část system.serviceModel souboru app.config. Aktualizovaný klient WCF obsahuje všechny stejné informace ve svém kódu, takže konfigurační část již není potřeba. Pokud jste chtěli, aby koncový bod WCF byl konfigurovatelný v souboru app.config, můžete jej přidat jako nastavení aplikace a aktualizovat kód klienta WCF, abyste načetli koncový bod služby WCF z konfigurace.

Po odebrání system.serviceModel části *app.config*, aplikace spustí, ale selže s jinou výjimkou při přihlášení uživatele.

```output
System.PlatformNotSupportedException: 'Operation is not supported on this platform.'
```

Nepodporované rozhraní `Func<T>.BeginInvoke`API je . Jak je vysvětleno v [dotnet/corefx#5940](https://github.com/dotnet/corefx/issues/5940), `BeginInvoke` .NET Core nepodporuje metody a `EndInvoke` na typy delegátů z důvodu základních závislostí vzdálené komunikace. Tento problém a jeho oprava jsou podrobněji vysvětleny v [migrující Delegate.BeginInvoke volání pro .NET Core](https://devblogs.microsoft.com/dotnet/migrating-delegate-begininvoke-calls-for-net-core/) blogu, ale podstata je, že `BeginInvoke` a `EndInvoke` volání by měla být nahrazena `Task.Run` (nebo asynchronní alternativy, pokud je to možné). Použití obecné řešení zde `BeginInvoke` volání může být `Invoke` nahrazen o `Task.Run`volání zahájené .

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

Po odebrání `BeginInvoke` využití se aplikace Bean Trader úspěšně spustí na .NET Core!

![Obchodník s beanem běžící na jádru .NET](./media/convert-project-from-net-framework/running-on-core.png)

Všechny aplikace se liší, takže konkrétní kroky potřebné k migraci vlastních aplikací do .NET Core se budou lišit. Ale doufejme, že ukázka Bean Trader demonstruje obecný pracovní postup a typy problémů, které lze očekávat. A navzdory délce tohoto článku byly skutečné změny potřebné ve vzorku Bean Trader, aby fungovaly na .NET Core, poměrně omezené. Mnoho aplikací migruje do .NET Core stejným způsobem; s omezenými nebo dokonce žádnými potřebnými změnami kódu.
