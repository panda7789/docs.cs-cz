---
title: Nasazení aplikací .NET Core pomocí Sady Visual Studio
description: Naučte se nasadit aplikaci .NET Core pomocí Sady Visual Studio.
ms.date: 09/03/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: f2299ac807c845dab482306cc4c710560bb7f1e7
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607859"
---
# <a name="deploy-net-core-apps-with-visual-studio"></a>Nasazení aplikací .NET Core pomocí Sady Visual Studio

Můžete nasadit aplikaci .NET Core buď jako *nasazení závislé na rámci*, která zahrnuje binární soubory aplikace, ale závisí na přítomnosti .NET Core v cílovém systému, nebo jako samostatné *nasazení*, které zahrnuje obě aplikace a binární soubory .NET Core. Přehled nasazení aplikace .NET Core naleznete v tématu [.NET Core Application Deployment](index.md).

Následující části ukazují, jak pomocí sady Microsoft Visual Studio vytvořit následující typy nasazení:

- Nasazení závislé na rámci
- Nasazení závislé na rámci se závislostmi třetích stran
- Samostatné nasazení
- Samostatné nasazení se závislostmi třetích stran

Informace o vývoji základních aplikací .NET pomocí sady Visual Studio naleznete v [tématu .NET Core závislostí a požadavků](../install/dependencies.md?pivots=os-windows).

## <a name="framework-dependent-deployment"></a>Nasazení závislé na rámci

Nasazení nasazení závislé na rámci bez závislostí třetích stran jednoduše zahrnuje vytváření, testování a publikování aplikace. Jednoduchý příklad napsaný v C# ilustruje proces.

1. Vytvořte projekt.

   Vyberte **Soubor** > **nový** > **projekt**. V dialogovém okně **Nový projekt** rozbalte kategorie projektu jazyka (C# nebo Visual Basic) v podokně **Nainstalované** typy projektů, zvolte **.NET Core**a v prostředním podokně vyberte šablonu **Konzola Aplikace (.NET Core).** Do textového pole **Název** zadejte název projektu, například FDD. Vyberte tlačítko **OK**.

1. Přidejte zdrojový kód aplikace.

   Otevřete soubor *Program.cs* nebo *Program.vb* v editoru a nahraďte automaticky generovaný kód následujícím kódem. Vyzve uživatele k zadání textu a zobrazí jednotlivá slova zadaná uživatelem. Používá regulární `\w+` výraz k oddělení slov ve vstupním textu.

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. Vytvořte sestavení ladění aplikace.

   Vyberte **sestavení** > **sestavení řešení**. Můžete také zkompilovat a spustit sestavení ladění aplikace výběrem ladění **ladění** > **start**.

1. Nasaďte aplikaci.

   Po odladění a testování programu vytvořte soubory, které se mají nasadit s vaší aplikací. Chcete-li publikovat z visual studia, postupujte takto:

      1. Změňte konfiguraci řešení z **Ladění** na **uvolnění** na panelu nástrojů a vytvořte verzi aplikace release (namísto ladění).

      1. Klikněte pravým tlačítkem myši na projekt (ne na řešení) v **Průzkumníku řešení** a vyberte **publikovat**.

      1. Na kartě **Publikovat** vyberte **Publikovat**. Visual Studio zapisuje soubory, které tvoří vaši aplikaci do místního systému souborů.

      1. Na kartě **Publikovat** se nyní zobrazuje jeden profil **FolderProfile**. Nastavení konfigurace profilu se zobrazí v části **Souhrn** na kartě.

   Výsledné soubory jsou umístěny v `Publish` adresáři `publish` pojmenovaném v systému Windows a v systémech Unix, který je umístěn v podadresáři podadresáře projektu *.\bin\release\netcoreapp2.1.*

Spolu se soubory vaší aplikace vydává proces publikování soubor databáze programů (.pdb), který obsahuje informace o ladění o vaší aplikaci. Soubor je užitečný především pro ladění výjimek. Můžete se rozhodnout, že ji nezabalíte se soubory aplikace. Měli byste ji však uložit v případě, že chcete ladit sestavení verze aplikace.

Nasaďte celou sadu souborů aplikací jakýmkoli způsobem. Můžete je například zabalit do souboru `copy` ZIP, použít jednoduchý příkaz nebo je nasadit s libovolným instalačním balíčkem podle vašeho výběru. Po instalaci mohou uživatelé spustit aplikaci pomocí příkazu `dotnet` a poskytnutím názvu souboru aplikace, například `dotnet fdd.dll`.

Kromě binárních souborů aplikace by měl instalační program také sdružovat instalační program sdílené ho rozhraní nebo jej zkontrolovat jako předpoklad v rámci instalace aplikace.  Instalace sdílené ho rozhraní vyžaduje přístup správce/root, protože je celopočítačová.

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>Nasazení závislé na rámci se závislostmi třetích stran

Nasazení nasazení závislé na rozhraní s jednou nebo více závislostmi třetích stran vyžaduje, aby všechny závislosti být k dispozici pro váš projekt. Před vytvořením aplikace jsou vyžadovány následující další kroky:

1. Pomocí **Správce balíčků NuGet** přidat odkaz na balíček NuGet do projektu; a pokud balíček ještě není ve vašem systému k dispozici, nainstalujte jej. Chcete-li otevřít správce balíčků, vyberte **nástroje, které** > **spravují správce** > balíčků**NuGet, pro řešení**.

1. Zkontrolujte, zda jsou v systému `Newtonsoft.Json`nainstalovány vaše závislosti třetích stran (například) a pokud nejsou, nainstalujte je. Na kartě **Nainstalováno** jsou uvedeny balíčky NuGet nainstalované v systému. Pokud `Newtonsoft.Json` zde není uvedena, vyberte kartu **Procházet** a do vyhledávacího pole zadejte "Newtonsoft.Json". Vyberte `Newtonsoft.Json` a v pravém podokně vyberte projekt před výběrem **možnosti Instalovat**.

1. Pokud `Newtonsoft.Json` je již v systému nainstalován, přidejte jej do projektu výběrem projektu v pravém podokně na kartě **Spravovat balíčky pro řešení.**

Nasazení závislé na rámci se závislostmi třetích stran je pouze tak přenosné jako jeho závislosti třetích stran. Pokud například knihovna jiného výrobce podporuje jenom macOS, aplikace není přenosná do systémů Windows. K tomu dochází, pokud závislost jiného výrobce sama o sobě závisí na nativním kódu. Dobrým příkladem je [Kestrel server](/aspnet/core/fundamentals/servers/kestrel), který vyžaduje nativní závislost na [libuv](https://github.com/libuv/libuv). Při vytvoření FDD pro aplikaci s tímto druhem závislosti třetí strany, publikovaný výstup obsahuje složku pro každý [identifikátor runtime (RID),](../rid-catalog.md) který podporuje nativní závislost (a která existuje v jeho balíčku NuGet).

## <a name="self-contained-deployment-without-third-party-dependencies"></a><a name="simpleSelf"></a>Samostatné nasazení bez závislostí třetích stran

Nasazení samostatného nasazení bez závislostí třetích stran zahrnuje vytvoření projektu, úpravu souboru *csproj,* sestavení, testování a publikování aplikace. Jednoduchý příklad napsaný v C# ilustruje proces. Začnete vytvořením, kódováním a testováním projektu stejně jako nasazení závislé na rámci:

1. Vytvořte projekt.

   Vyberte **Soubor** > **nový** > **projekt**. V dialogovém okně **Nový projekt** rozbalte kategorie projektu jazyka (C# nebo Visual Basic) v podokně **Nainstalované** typy projektů, zvolte **.NET Core**a v prostředním podokně vyberte šablonu **Konzola Aplikace (.NET Core).** Do textového pole **Název** zadejte název projektu, například "SCD", a vyberte tlačítko **OK.**

1. Přidejte zdrojový kód aplikace.

   Otevřete soubor *Program.cs* nebo *Program.vb* v editoru a nahraďte automaticky generovaný kód následujícím kódem. Vyzve uživatele k zadání textu a zobrazí jednotlivá slova zadaná uživatelem. Používá regulární `\w+` výraz k oddělení slov ve vstupním textu.

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. Určete, zda chcete použít režim globalizace invariantní.

   Zejména v případě, že vaše aplikace cíle Linux, můžete snížit celkovou velikost vašeho nasazení s využitím [globalizace invariantní režim](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md). Režim invariantizace je užitečné pro aplikace, které nejsou globálně vědomi a které můžete použít konvence formátování, konvencí caseing a porovnání řetězců a pořadí řazení [invariantní jazykové verze](xref:System.Globalization.CultureInfo.InvariantCulture).

   Chcete-li povolit invariantní režim, klepněte pravým tlačítkem myši na projekt (nikoli na řešení) v **Průzkumníku řešení**a vyberte **možnost Upravit Soubor SCD.csproj** nebo **Upravit Soubor SCD.vbproj**. Pak do souboru přidejte následující zvýrazněné řádky:

   [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj?highlight=6-8)]

1. Vytvořte sestavení ladění aplikace.

   Vyberte **sestavení** > **sestavení řešení**. Můžete také zkompilovat a spustit sestavení ladění aplikace výběrem ladění **ladění** > **start**. Tento krok ladění umožňuje identifikovat problémy s vaší aplikací, když je spuštěna na hostitelské platformě. Stále budete muset vyzkoušet na každé z vašich cílových platforem.

   Pokud jste povolili globalizace invariantní režim, nezapomeňte zejména otestovat, zda absence dat citlivých na jazykovou verzi je vhodný pro vaši aplikaci.

Po dokončení ladění můžete publikovat samostatné nasazení:

<!-- markdownlint-disable MD025 -->

# <a name="visual-studio-156-and-earlier"></a>[Visual Studio 15.6 a starší](#tab/vs156)

Po odladění a testování programu vytvořte soubory, které se mají nasadit s vaší aplikací pro každou platformu, na kterou cílí.

Pokud chcete aplikaci publikovat z Visual Studia, postupujte takto:

1. Definujte platformy, na které bude vaše aplikace cílit.

   1. Klikněte pravým tlačítkem myši na projekt (ne na řešení) v **Průzkumníku řešení** a vyberte **upravit Soubor SCD.csproj**.

   1. Vytvořte `<RuntimeIdentifiers>` značku `<PropertyGroup>` v části souboru *csproj,* která definuje platformy, na které vaše aplikace cílí, a zadejte identifikátor runtime (RID) každé platformy, na kterou cílíte. Musíte také přidat středník oddělit RIDs. Seznam identifikátorů modulu [runtime IDentifier](../rid-catalog.md) naleznete v části Katalog runtime iDentifier.

   Například následující příklad označuje, že aplikace běží na 64bitových operačních systémech Windows 10 a 64bitovém operačním systému OS X verze 10.11.

   ```xml
   <PropertyGroup>
      <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
   </PropertyGroup>
   ```

   Prvek `<RuntimeIdentifiers>` může jít `<PropertyGroup>` do jakéhokoli, které máte ve vašem *souboru csproj.* Kompletní ukázkový *soubor csproj* se zobrazí dále v této části.

1. Publikujte aplikaci.

   Po odladění a testování programu vytvořte soubory, které se mají nasadit s vaší aplikací pro každou platformu, na kterou cílí.

   Pokud chcete aplikaci publikovat z Visual Studia, postupujte takto:

      1. Změňte konfiguraci řešení z **Ladění** na **uvolnění** na panelu nástrojů a vytvořte verzi aplikace release (namísto ladění).

      1. Klikněte pravým tlačítkem myši na projekt (ne na řešení) v **Průzkumníku řešení** a vyberte **publikovat**.

      1. Na kartě **Publikovat** vyberte **Publikovat**. Visual Studio zapisuje soubory, které tvoří vaši aplikaci do místního systému souborů.

      1. Na kartě **Publikovat** se nyní zobrazuje jeden profil **FolderProfile**. Nastavení konfigurace profilu jsou zobrazeny v části **Souhrn** na **Target Location** kartě. **Target Runtime**

      1. Visual Studio ve výchozím nastavení zapíše všechny publikované soubory do jednoho adresáře. Pro větší pohodlí je nejlepší vytvořit samostatné profily pro každý cílový běh a umístit publikované soubory do adresáře specifického pro platformu. To zahrnuje vytvoření samostatného profilu publikování pro každou cílovou platformu. Takže nyní znovu aplikaci pro každou platformu tímto způsobem postupujte takto:

         1. V dialogovém okně **Publikovat** vyberte **Vytvořit nový profil.**

         1. V **dialogovém** okně Vybrat cíl publikování změňte možnost Vybrat umístění **složky** do *přihrádky\Release\PublishOutput\win10-x64*. Vyberte **OK**.

         1. Vyberte nový profil **(FolderProfile1**) v seznamu profilů a ujistěte se, že **cílový runtime** je `win10-x64`. Pokud tomu tak není, vyberte **Nastavení**. V dialogovém okně **Nastavení profilu** změňte **cílovou dobu běhu** na `win10-x64` položku **Uložit**. V opačném případě vyberte **zrušit**.

         1. Vyberte **Publikovat,** abyste publikovali aplikaci pro 64bitové platformy Windows 10.

         1. Chcete-li vytvořit profil pro platformu, postupujte znovu podle předchozích `osx.10.11-x64` kroků. **Cílové umístění** je *bin\Release\PublishOutput\osx.10.11-x64*a cílový `osx.10.11-x64`běh **runtime** je . Název, který Visual Studio přiřadí tomuto profilu, je **FolderProfile2**.

      Každé cílové umístění obsahuje úplnou sadu souborů (soubory aplikace i všechny soubory .NET Core), které jsou potřeba ke spuštění aplikace.

Spolu se soubory vaší aplikace vydává proces publikování soubor databáze programů (.pdb), který obsahuje informace o ladění o vaší aplikaci. Soubor je užitečný především pro ladění výjimek. Můžete se rozhodnout, že ji nezabalíte se soubory aplikace. Měli byste ji však uložit v případě, že chcete ladit sestavení verze aplikace.

Nasadit publikované soubory jakýmkoli způsobem se vám líbí. Můžete je například zabalit do souboru `copy` ZIP, použít jednoduchý příkaz nebo je nasadit s libovolným instalačním balíčkem podle vašeho výběru.

Následuje kompletní *csproj* soubor pro tento projekt.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

# <a name="visual-studio-157-and-later"></a>[Visual Studio 15.7 a novější](#tab/vs157)

Po odladění a testování programu vytvořte soubory, které se mají nasadit s vaší aplikací pro každou platformu, na kterou cílí. To zahrnuje vytvoření samostatného profilu pro každou cílovou platformu.

Pro každou platformu, na kterou vaše aplikace cílí, postupujte takto:

1. Vytvořte profil pro cílovou platformu.

   Pokud se jedná o první profil, který jste vytvořili, klikněte pravým tlačítkem myši na projekt (ne na řešení) v **Průzkumníku řešení** a vyberte **Publikovat**.

   Pokud jste profil už vytvořili, klikněte pravým tlačítkem myši na projekt a otevřete dialogové okno **Publikovat,** pokud ještě není otevřený. Pak vyberte **Nový profil**.

   Otevře se dialogové okno **Vybrat cíl publikování.**

1. Vyberte umístění, kde Visual Studio publikuje vaši aplikaci.

   Pokud publikujete jenom na jedné platformě, můžete přijmout výchozí hodnotu v textovém poli **Zvolit složku.** To publikuje nasazení aplikace závislé na rámci do * \<adresáře>\bin\Release\netcoreapp2.1\publish.*

   Pokud publikujete na více než jedné platformě, připojujte řetězec, který identifikuje cílovou platformu. Pokud například připojíte řetězec "linux" k cestě k souboru, aplikace Visual Studio publikuje nasazení aplikace závislé na rámci do * \<adresáře projektu>\bin\Release\netcoreapp2.1\publish\linux.*

1. Profil vytvořte tak, že vedle tlačítka **Publikovat** vyberete ikonu rozevíracího seznamu a vyberete **Vytvořit profil**. Pak vyberte tlačítko **Vytvořit profil** a vytvořte profil.

1. Označte, že publikujete samostatné nasazení a definujte platformu, na kterou bude vaše aplikace cílit.

   1. V dialogovém okně **Publikovat** vyberte odkaz **Konfigurovat** a otevřete dialogové okno **Nastavení profilu.**

   1. V seznamu **Režim nasazení** vyberte **Samostatný.**

   1. V seznamu **Cílový běh ový čas** vyberte jednu z platforem, na které vaše aplikace cílí.

   1. Vyberte **Uložit,** chcete-li přijmout změny a zavřít dialogové okno.

1. Pojmenujte svůj profil.

   1. Vyberte **Akce** > **Přejmenovat profil,** abyste svůj profil pojmenovali.

   2. Přiřaďte svému profilu název, který identifikuje cílovou platformu, a pak vyberte **Uložit*.

Opakujte tyto kroky a definujte všechny další cílové platformy, na které vaše aplikace cílí.

Nakonfigurovali jste profily a jste připraveni publikovat aplikaci. Použijte následující postup:

   1. Pokud okno **Publikovat** není aktuálně otevřené, klikněte pravým tlačítkem myši na projekt (ne na řešení) v **Průzkumníku řešení** a vyberte **Publikovat**.

   2. Vyberte profil, který chcete publikovat, a pak vyberte **Publikovat**. Proveďte to pro každý profil, který má být publikován.

   Každé cílové umístění (v případě našeho příkladu bin\release\netcoreapp2.1\publish\\*profile-name* obsahuje úplnou sadu souborů (soubory aplikace i všechny soubory .NET Core) potřebné ke spuštění aplikace.

Spolu se soubory vaší aplikace vydává proces publikování soubor databáze programů (.pdb), který obsahuje informace o ladění o vaší aplikaci. Soubor je užitečný především pro ladění výjimek. Můžete se rozhodnout, že ji nezabalíte se soubory aplikace. Měli byste ji však uložit v případě, že chcete ladit sestavení verze aplikace.

Nasadit publikované soubory jakýmkoli způsobem se vám líbí. Můžete je například zabalit do souboru `copy` ZIP, použít jednoduchý příkaz nebo je nasadit s libovolným instalačním balíčkem podle vašeho výběru.

Následuje kompletní *csproj* soubor pro tento projekt.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
</Project>
```

Kromě toho Visual Studio vytvoří samostatný\*profil publikování ( .pubxml) pro každou platformu, na kterou cílíte. Například soubor pro náš linuxový profil (linux.pubxml) se zobrazí takto:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--
https://go.microsoft.com/fwlink/?LinkID=208121.
-->
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PublishProtocol>FileSystem</PublishProtocol>
    <Configuration>Release</Configuration>
    <Platform>Any CPU</Platform>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <PublishDir>bin\Release\netcoreapp2.1\publish\linux</PublishDir>
    <RuntimeIdentifier>win-x86</RuntimeIdentifier>
    <SelfContained>true</SelfContained>
    <_IsPortable>false</_IsPortable>
  </PropertyGroup>
</Project>
```

---

## <a name="self-contained-deployment-with-third-party-dependencies"></a>Samostatné nasazení se závislostmi třetích stran

Nasazení samostatného nasazení s jednou nebo více závislostmi třetích stran zahrnuje přidání závislostí. Před vytvořením aplikace jsou vyžadovány následující další kroky:

1. Pomocí **Správce balíčků NuGet** přidat odkaz na balíček NuGet do projektu; a pokud balíček ještě není ve vašem systému k dispozici, nainstalujte jej. Chcete-li otevřít správce balíčků, vyberte **nástroje, které** > **spravují správce** > balíčků**NuGet, pro řešení**.

1. Zkontrolujte, zda jsou v systému `Newtonsoft.Json`nainstalovány vaše závislosti třetích stran (například) a pokud nejsou, nainstalujte je. Na kartě **Nainstalováno** jsou uvedeny balíčky NuGet nainstalované v systému. Pokud `Newtonsoft.Json` zde není uvedena, vyberte kartu **Procházet** a do vyhledávacího pole zadejte "Newtonsoft.Json". Vyberte `Newtonsoft.Json` a v pravém podokně vyberte projekt před výběrem **možnosti Instalovat**.

1. Pokud `Newtonsoft.Json` je již v systému nainstalován, přidejte jej do projektu výběrem projektu v pravém podokně na kartě **Spravovat balíčky pro řešení.**

Následuje kompletní *csproj* soubor pro tento projekt:

# <a name="visual-studio-156-and-earlier"></a>[Visual Studio 15.6 a starší](#tab/vs156)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

# <a name="visual-studio-157-and-later"></a>[Visual Studio 15.7 a novější](#tab/vs157)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

---

Při nasazení aplikace jsou všechny závislosti třetích stran používané ve vaší aplikaci také obsaženy se soubory aplikace. Knihovny třetích stran nejsou vyžadovány v systému, ve kterém je aplikace spuštěna.

Samostatné nasazení můžete nasadit pouze s knihovnou třetí strany na platformy podporované tou knihovnou. To je podobné s závislostí třetích stran s nativní závislosti v nasazení závislé na rámci, kde nativní závislosti nebude existovat na cílové platformě, pokud byly dříve nainstalovány tam.

## <a name="see-also"></a>Viz také

- [Nasazení základní aplikace .NET](index.md)
- [Katalog IDentifier (RID) modulu .NET Core Runtime](../rid-catalog.md)
