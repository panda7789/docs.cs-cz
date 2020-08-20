---
title: Příklad migrace na .NET Core 3.1
description: Ukazuje, jak migrovat ukázkové aplikace, které cílí na .NET Framework .NET Core 3,1.
ms.date: 05/12/2020
ms.openlocfilehash: 6a0311e9aaeb25ac39f3394d3a62e17046fe03d8
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656764"
---
# <a name="example-of-migrating-to-net-core-31"></a>Příklad migrace na .NET Core 3.1

V této kapitole máme praktické pokyny, které vám pomohou s migrací vaší stávající aplikace z .NET Framework do .NET Core.

Máme dobře strukturovaný proces, který můžete dodržovat, a nejdůležitější věci, které je potřeba vzít v úvahu pro každý krok.

Pak povedeme podrobný postup migrace pro ukázkovou desktopovou aplikaci, od verze WinForms a WPF.

## <a name="migration-process-overview"></a>Přehled procesu migrace

Proces migrace se skládá ze čtyř sekvenčních kroků:

1. **Příprava**: Seznámení se závislostmi, které projekt musí mít představu o tom, co je předem. V tomto kroku převezmete aktuální projekt do stavu, který zjednodušuje spouštěcí bod migrace.

2. **Migrace souboru projektu:** projekty .NET Core používají nový formát projektu ve stylu sady SDK. Vytvořte nový soubor projektu s tímto formátem, nebo aktualizujte ten, který budete muset použít ve stylu sady SDK.

3. **Opravit kód a sestavit:** Sestavte kód v části .NET Core Addressing – rozdíly na úrovni rozhraní API mezi .NET Framework a .NET Core. V případě potřeby aktualizujte balíčky třetích stran na ty, které podporují .NET Core.

4. **Spustit a otestovat:** Mohou existovat rozdíly, které se nezobrazí až do doby běhu. Nezapomeňte ale aplikaci spustit a otestovat, jestli všechno funguje podle očekávání.

### <a name="preparation"></a>Příprava

#### <a name="migrate-packagesconfig-file"></a>Migrovat soubor packages.config

V .NET Framework aplikaci jsou všechny odkazy na externí balíčky deklarované v souboru *packages.config* . V rozhraní .NET Core již není nutné používat soubor *packages.config* . Místo toho použijte vlastnost [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) v souboru projektu k určení balíčků NuGet pro vaši aplikaci.

Takže je potřeba přejít z jednoho formátu do druhého. Aktualizaci můžete provést ručně a přitom přebírat závislosti obsažené v souboru *packages.config* a migrovat je do souboru projektu ve `PackageReference` formátu. Nebo můžete nechat aplikaci Visual Studio pracovat za vás: klikněte pravým tlačítkem na soubor *packages.config* a vyberte možnost **migrovat packages.config na PackageReference** .

#### <a name="verify-every-dependency-compatibility-in-net-core"></a>Ověřit všechny kompatibility závislostí v .NET Core

Po dokončení migrace odkazů na balíčky je nutné ověřit všechny reference z hlediska kompatibility. Můžete prozkoumat závislosti jednotlivých balíčků NuGet, které vaše aplikace používá v [NuGet.org](https://www.nuget.org/). Pokud balíček obsahuje .NET Standard závislosti, pak bude fungovat na .NET Core, protože .NET Core 3,1 [podporuje](../../standard/net-standard.md#net-implementation-support) všechny verze .NET Standard. Následující obrázek ukazuje závislosti `Castle.Windsor` balíčku:

![Snímek obrazovky se závislostmi NuGet pro balíček Castle. Windsor](./media/example-migration-core/nuget-dependencies.png)

Chcete-li ověřit kompatibilitu balíčku, můžete použít nástroj <https://fuget.org> , který nabízí podrobnější informace o verzích a závislostech.

Projekt je pravděpodobně odkazován na starší verze balíčků, které nepodporují .NET Core, ale můžete najít novější verze, které ji podporují. Aktualizace balíčků do novějších verzí proto obecně představuje dobrou doporučení. Měli byste však vzít v úvahu, že aktualizace verze balíčku může vést k nějakým změnám, které by vynutily aktualizaci kódu.

Co se stane, když nenajdete kompatibilní verzi? Co když ale nechcete aktualizovat verzi balíčku z důvodu těchto nejnovějších změn? Nedělejte si starosti, protože je možné záviset na .NET Framework balíčky z aplikace .NET Core. Nezapomeňte ho testovat v rozsáhlých případech, protože může způsobit chyby za běhu, pokud externí balíček volá rozhraní API, které není k dispozici v rozhraní .NET Core. To je skvělé, když používáte starý balíček, který se nebude aktualizovat, a vy můžete změnit cílení na práci v .NET Core.

#### <a name="check-for-api-compatibility"></a>Ověřit kompatibilitu rozhraní API

Vzhledem k tomu, že je plocha rozhraní API v .NET Framework a .NET Core podobná, ale není identická, musíte ověřit, která rozhraní API jsou k dispozici v rozhraní .NET Core a nikoli. Nástroj Analyzátor přenositelnosti .NET můžete použít k Surface používaných rozhraní API, která nejsou přítomna v rozhraní .NET Core. Vypadá na binární úrovni vaší aplikace, extrahuje všechna rozhraní API, která jsou volána, a pak zobrazí seznam rozhraní API, která nejsou k dispozici v cílové verzi rozhraní (v tomto případě .NET Core 3,1).

Další informace o tomto nástroji najdete na adrese:

<https://docs.microsoft.com/dotnet/standard/analyzers/portability-analyzer>

Zajímavým aspektem tohoto nástroje je, že pouze rozsvítí rozdíly z vlastního kódu a nikoli z externích balíčků, které nelze změnit. Nezapomeňte, že byste měli aktualizovat většinu těchto balíčků, abyste je mohli pracovat s .NET Core.

### <a name="migrate-project-file"></a>Migrovat soubor projektu

#### <a name="create-the-new-net-core-project"></a>Vytvoření nového projektu .NET Core

Ve většině případů budete chtít aktualizovat existující projekt na nový formát .NET Core. Můžete ale také vytvořit nový projekt a zachovávat si ho starý. Hlavní nevýhodou aktualizace původního projektu je, že ztratíte podporu návrháře, což může být pro vás důležité. Chcete-li pokračovat v používání návrháře, je nutné vytvořit nový projekt .NET Core paralelně se starým a sdílet prostředky. Pokud potřebujete upravit prvky uživatelského rozhraní v návrháři, můžete k tomu přejít na původní projekt. A vzhledem k tomu, že prostředky jsou propojeny, budou aktualizovány také v projektu .NET Core.

[Projekt ve stylu sady SDK](../../core/project-sdk/msbuild-props.md) pro .NET Core je mnohem jednodušší než formát projektu .NET Framework. Kromě výše uvedených `PackageReference` položek nemusíte dělat spoustu dalších věcí. Nový formát projektu zahrnuje určité přípony souborů [ve výchozím nastavení](../../core/tools/csproj.md#default-compilation-includes-in-net-core-projects), například `.cs` soubory a `.xaml` , aniž by bylo nutné je explicitně zahrnout do souboru projektu.

#### <a name="assemblyinfo-considerations"></a>Assembly.info požadavky

Atributy se generují automaticky v projektech .NET Core. Pokud projekt obsahuje soubor *AssemblyInfo.cs* , definice budou duplikovány, což způsobí konflikty při kompilaci. Můžete odstranit starší soubor *AssemblyInfo.cs* nebo zakázat Autogeneration přidáním následujícího záznamu do souboru projektu .NET Core:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

#### <a name="resources"></a>Zdroje a prostředky

Integrované prostředky jsou zahrnuté automaticky, ale prostředky nejsou, takže je potřeba migrovat prostředky do nového souboru projektu.

#### <a name="package-references"></a>Odkazy na balíčky

Pomocí možnosti **migrovat packages.config do PackageReference** můžete snadno přesunout odkazy na externí balíčky do nového formátu, jak je uvedeno výše.

#### <a name="update-package-references"></a>Aktualizovat odkazy na balíček

Aktualizujte verze balíčků, které byly zjištěny jako kompatibilní, jak je znázorněno v předchozí části.

### <a name="fix-the-code-and-build"></a>Opravit kód a sestavit

#### <a name="microsoftwindowscompatibility"></a>Microsoft. Windows. Compatibility

Pokud vaše aplikace závisí na rozhraních API, která nejsou k dispozici v rozhraní .NET Core, jako je například registr, seznamy ACL nebo WCF, musíte do `Microsoft.Windows.Compatibility` balíčku přidat odkaz na tyto rozhraní API specifická pro systém Windows. Pracují v .NET Core, ale nejsou zahrnuté, protože nejsou součástí různých platforem.

K dispozici je nástroj, který se nazývá API Analyzer ( <https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer> ), který vám pomůže identifikovat rozhraní API, která nejsou kompatibilní s vaším kódem.

#### <a name="use-if-directives"></a>Použít \# direktivy if

Pokud při .NET Framework a .NET Core potřebujete jiné cesty spuštění, měli byste použít konstanty kompilace. Přidejte některé \# direktivy IF do kódu pro zachování stejné základny kódu pro oba cíle.

#### <a name="technologies-not-available-on-net-core"></a>Technologie, které nejsou dostupné v .NET Core

Některé technologie nejsou k dispozici v rozhraní .NET Core, například:

* Objektů třídy AppDomains
* Vzdálenou
* Zabezpečení přístupu kódu
* Server WCF
* Pracovní postup Windows

To je důvod, proč potřebujete najít náhradu za tyto technologie, pokud je používáte ve své aplikaci. Další informace najdete v článku [věnovaném technologii .NET Framework nedostupné v rozhraní .NET Core](../../core/porting/net-framework-tech-unavailable.md) .

#### <a name="regenerate-autogenerated-clients"></a>Znovu vygenerovat automaticky generované klienty

Pokud vaše aplikace používá automaticky generovaný kód, jako je například klient WCF, bude pravděpodobně nutné znovu vygenerovat tento kód pro cílový .NET Core. Někdy můžete najít některé chybějící odkazy, protože nemusí být zahrnuty jako součást výchozích sad sestavení .NET Core. Pomocí nástroje, jako <https://apisof.net/> je, můžete snadno najít sestavení chybějící odkaz v a přidat ho z NuGet.

#### <a name="rolling-back-package-versions"></a>Vracení verzí balíčku zpět

Jako obecné pravidlo jsme dřív uvedli, že byste měli lépe aktualizovat všechny verze jednoho balíčku tak, aby byly kompatibilní s .NET Core. Můžete ale najít, že cílení na aktualizovanou a kompatibilní verzi sestavení pouze neplatí. Pokud náklady na změnu nejsou přijatelné, můžete uvažovat o vracení verzí balíčků, které budou používat .NET Framework. I když nemusí být cíleny na rozhraní .NET Core, měly by fungovat dobře, pokud nevolají některá nepodporovaná rozhraní API.

### <a name="run-and-test"></a>Spuštění a testování

Po sestavení vaší aplikace bez chyb můžete spustit poslední krok migrace otestováním všech funkcí.

V tomto posledním kroku můžete najít několik různých problémů v závislosti na složitosti vaší aplikace a závislostech a rozhraních API, které používáte.

Pokud například použijete konfigurační soubory (*app.config*), může dojít k chybám za běhu, jako jsou konfigurační oddíly, které nejsou k dispozici. `Microsoft.Extensions.Configuration`Tato chyba by se měla opravit pomocí balíčku NuGet.

Dalším důvodem pro chyby je použití `BeginInvoke` metod a, `EndInvoke` protože nejsou podporované v .NET Core. Nepodporují se v .NET Core, protože mají závislost na vzdálené komunikaci, která v .NET Core neexistuje. Chcete-li tento problém vyřešit, zkuste použít `await` klíčové slovo (je-li k dispozici) nebo <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metodu.

Pomocí analyzátorů kompatibility můžete identifikovat rozhraní API a vzory kódu v kódu, které mohou potenciálně způsobovat problémy v době běhu pomocí .NET Core. Přejít na <https://github.com/dotnet/platform-compat> a použít analyzátor rozhraní .NET API pro váš projekt.

## <a name="migrating-a-windows-forms-application"></a>Migrace aplikace model Windows Forms

Aby se dokončil proces migrace model Windows Forms aplikace, rozhodli jsme se migrovat ukázkovou aplikaci eShop, která je dostupná na adrese <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms> . Úplný výsledek migrace můžete najít na adrese <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms> .

Tato aplikace zobrazuje katalog produktů a umožňuje uživateli navigaci, filtrování a hledání produktů. Z hlediska architektury se aplikace spoléhá na externí službu WCF, která slouží jako fasáda do back-endové databáze.

Hlavní okno aplikace můžete zobrazit na následujícím obrázku:

![Hlavní okno aplikace](./media/example-migration-core/main-application-window.png)

Pokud otevřete soubor projektu *. csproj* , vidíte to přibližně takto:

![Snímek obrazovky s obsahem souboru csproj](./media/example-migration-core/csproj-file.png)

Jak už jsme uvedli, projekt .NET Core má kompaktnější styl a potřebujete migrovat strukturu projektu na nový styl .NET Core SDK.

V Průzkumník řešení klikněte pravým tlačítkem na projekt model Windows Forms a vyberte **Uvolnit projekt**  >  **Úpravy**.

Nyní můžete aktualizovat soubor. csproj. Odstraníte celý obsah a nahradíte ho následujícím kódem:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
    <PropertyGroup>
        <OutputType>WinExe</OutputType>
        <TargetFramework>netcoreapp3.1</TargetFramework>
        <UseWindowsForms>true</UseWindowsForms>
        <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    </PropertyGroup>
</Project>
```

Uložte a znovu načtěte projekt. Nyní jste dokončili aktualizaci souboru projektu a projekt cílí na .NET Core.

Pokud v tomto okamžiku zkompilujete projekt, zjistíte chyby související s odkazem na klienta WCF. Vzhledem k tomu, že se tento kód generuje automaticky, musíte ho znovu vygenerovat pro cílový .NET Core.

![Snímek obrazovky s chybami kompilace v aplikaci Visual Studio](./media/example-migration-core/winforms-compilation-errors.png)

Odstraňte soubor *reference.cs* a vygenerujte nového klienta služby.

Klikněte pravým tlačítkem na **připojené služby** a vyberte možnost **Přidat připojenou službu** .

![Snímek obrazovky s vybranou možností přidat připojenou službu v nabídce připojených služeb](./media/example-migration-core/add-connected-service.png)

Otevře se okno připojené služby. Vyberte možnost **webové služby Microsoft WCF** .

![Snímek obrazovky okna připojené služby](./media/example-migration-core/connected-services-window.png)

Pokud máte službu WCF ve stejném řešení jako v tomto příkladu, můžete místo zadání adresy URL služby vybrat možnost **zjišťování** .

![Snímek obrazovky s referenčním oknem konfigurace WCF webové služby](./media/example-migration-core/configure-wcf-reference.png)

Po umístění služby nástroj odráží kontrakt rozhraní API implementovaný službou. Změňte název oboru názvů tak `eShopServiceReference` , jak je znázorněno na následujícím obrázku:

![Snímek obrazovky se smlouvou API a oborem názvů se změnil](./media/example-migration-core/api-contract-namespace.png)

Vyberte tlačítko **Dokončit** . Po chvíli se zobrazí generovaný kód.

Měli byste vidět tři automaticky generované soubory:

1. *Začínáme*: odkaz na GitHub, který poskytuje některé informace o WCF.
2. *ConnectedService.js*: parametry konfigurace pro připojení ke službě.
3. *Reference.cs*: skutečný kód klienta WCF.

![Snímek obrazovky okna Průzkumník řešení se třemi automaticky generovanými soubory](./media/example-migration-core/autogenerated-files.png)

Pokud znovu zkompilujete, zobrazí se mnoho chyb ze souborů *. cs* ve složce *pomocníka* . Tato složka se objevila ve verzi .NET Framework, ale není zahrnutá v Old *. csproj*. Ale v novém projektu ve stylu sady SDK je každý soubor s kódem, který je přítomen pod umístěním souboru projektu, ve výchozím nastavení zahrnut. To znamená, že nový projekt .NET Core se pokusí kompilovat soubory uvnitř složky *pomocníka* . Vzhledem k tomu, že tato složka není potřeba, můžete ji bezpečně odstranit.

Pokud projekt zkompilujete znovu a spustíte, neuvidíte image produktu. Problémem je to, že se teď cesta k souborům mírně změnila. Chcete-li tento problém vyřešit, je třeba v cestě přidat další úroveň hloubky, aktualizovat v souboru `CatalogView.cs` řádek:

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

na

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

Po této změně můžete ověřit, že se aplikace spouští a běží podle očekávání v .NET Core.

## <a name="migrating-a-wpf-application"></a>Migrace aplikace WPF

`Shop.ClassicWPF`K provedení migrace použijeme ukázkovou aplikaci. Následující obrázek ukazuje snímek obrazovky aplikace před migrací:

![Ukázková aplikace před migrací](./media/example-migration-core/app-before-migration.png)

Tato aplikace používá k ukládání informací katalogu produktů místní databázi SQL Server Express. K této databázi se dostanete přímo z aplikace WPF.

Nejprve je třeba aktualizovat soubor *. csproj* na nový styl sady SDK používaný aplikacemi .NET Core. Budete postupovat podle stejných kroků popsaných v tématu Migrace model Windows Forms: projekt zrušíte, otevřete soubor *. csproj* , aktualizujete jeho obsah a znovu načtete projekt.

V takovém případě odstraňte veškerý obsah souboru *. csproj* a nahraďte ho následujícím kódem:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
    <PropertyGroup>
        <OutputType>WinExe</OutputType>
        <TargetFramework>netcoreapp3.1</TargetFramework>
        <UseWpf>true</UseWpf>
        <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    </PropertyGroup>
</Project>
```

Pokud projekt znovu načtete a zkompilujete, zobrazí se následující chyba:

![Snímek obrazovky s chybami kompilace v aplikaci Visual Studio](./media/example-migration-core/wpf-compilation-error.png)

Vzhledem k tomu, že jste odstranili všechen obsah *. csproj* , ztratili jste ve starém projektu specifikaci odkazů na projekt. Pouze potřebujete přidat tento řádek do souboru *. csproj* pro zahrnutí odkazu na projekt:

```xml
<ItemGroup>
    <ProjectReference Include="..\\eShop.SqlProvider\\eShop.SqlProvider.csproj" />
<ItemGroup>
```

Aplikaci Visual Studio můžete také nechat pomáhat kliknutím pravým tlačítkem na uzel **závislosti** a výběrem možnosti **Přidat odkaz na projekt**. Vyberte projekt z řešení a klikněte na **OK**:

![Snímek obrazovky dialogového okna Správce odkazů s vybraným projektem eShop. SqlProvider](./media/example-migration-core/reference-manager.png)

Po přidání chybějícího odkazu na projekt se aplikace zkompiluje a spustí podle očekávání v .NET Core.

>[!div class="step-by-step"]
>[Předchozí](windows-migration.md) 
> [Další](deploy-modern-applications.md)
