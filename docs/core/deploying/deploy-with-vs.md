---
title: Nasazení aplikací .NET Core pomocí sady Visual Studio
description: Naučte se nasadit aplikaci .NET Core pomocí sady Visual Studio.
ms.date: 09/03/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 11a322278ce3ff38964fe2fa389e0b4a58897ec4
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449020"
---
# <a name="deploy-net-core-apps-with-visual-studio"></a>Nasazení aplikací .NET Core pomocí sady Visual Studio

Můžete nasadit aplikaci .NET Core buď jako *nasazení závislé na rozhraní*, které zahrnuje binární soubory aplikace, ale závisí na přítomnosti .NET Core v cílovém systému nebo jako *samostatné nasazení*, které zahrnuje jak vaše aplikace, tak binární soubory .NET Core. Přehled nasazení aplikace .NET Core najdete v tématu [nasazení aplikace .NET Core](index.md).

Následující části ukazují, jak pomocí Microsoft Visual Studio vytvořit následující typy nasazení:

- Nasazení závisí na architektuře
- Nasazení závislé na rozhraní se závislostmi třetích stran
- Samostatná nasazení
- Samostatné nasazení s závislostmi třetích stran

Informace o použití sady Visual Studio pro vývoj aplikací .NET Core najdete v tématu [závislosti a požadavky .NET Core](../install/dependencies.md?pivots=os-windows).

## <a name="framework-dependent-deployment"></a>Nasazení závisí na architektuře

Nasazení závislé na rozhraní bez závislostí třetí strany zahrnuje sestavování, testování a publikování aplikace. Jednoduchý příklad napsaný v C# tomto příkladu znázorňuje proces.

1. Vytvořte projekt.

   Vyberte **Soubor** > **Nový** > **Projekt**. V dialogovém okně **Nový projekt** rozbalte v podokně **nainstalované** typy projektůC# kategorii projektu (nebo Visual Basic) vašeho jazyka, zvolte možnost **.NET Core**a potom v prostředním podokně vyberte šablonu **Konzolová aplikace (.NET Core)** . Do textového pole **název** zadejte název projektu, například "FDD". Vyberte tlačítko **OK**.

1. Přidejte zdrojový kód aplikace.

   V editoru otevřete soubor *program.cs* nebo *program. vb* a nahraďte automaticky generovaný kód následujícím kódem. Vyzve uživatele, aby zadal text a zobrazil jednotlivá slova zadaná uživatelem. Používá regulární výraz `\w+` k oddělení slov ve vstupním textu.

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. Vytvořte ladicí sestavení vaší aplikace.

   Vyberte **sestavení** **řešení**Build > . Můžete také zkompilovat a **Spustit ladicí sestavení** vaší aplikace, a to tak, že vyberete ladění > **Spustit ladění**.

1. Nasaďte aplikaci.

   Po ladění a otestování programu vytvořte soubory, které mají být nasazeny s vaší aplikací. Chcete-li publikovat ze sady Visual Studio, postupujte následovně:

      1. Změňte konfiguraci řešení z **Debug** na **release** na panelu nástrojů a sestavte verzi (nikoli ladění) vaší aplikace.

      1. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt (ne řešení) a vyberte **publikovat**.

      1. Na kartě **publikovat** vyberte **publikovat**. Visual Studio zapisuje soubory, které tvoří vaši aplikaci, do místního systému souborů.

      1. Na kartě **publikovat** se teď zobrazí jeden profil, **FolderProfile**. Nastavení konfigurace profilu se zobrazí v části **Souhrn** na kartě.

   Výsledné soubory jsou umístěny v adresáři s názvem `Publish` v systému Windows a `publish` v systémech UNIX, které jsou v podadresáři podadresáře projektu *.\bin\release\netcoreapp2.1* .

Spolu se soubory vaší aplikace proces publikování generuje soubor databáze programu (PDB), který obsahuje informace o ladění vaší aplikace. Soubor je vhodný hlavně pro ladění výjimek. Můžete se rozhodnout, že ho nechcete zabalit do souborů vaší aplikace. Měli byste ji však uložit v případě, že chcete ladit sestavení pro vydání aplikace.

Nasaďte kompletní sadu souborů aplikace jakýmkoli způsobem. Můžete je například zabalit do souboru zip, použít jednoduchý příkaz `copy`, nebo je nasadit s libovolným instalačním balíčkem podle vašeho výběru. Po instalaci pak uživatelé můžou aplikaci spustit pomocí příkazu `dotnet` a zadáním názvu souboru aplikace, jako je například `dotnet fdd.dll`.

Kromě binárních souborů aplikace by měl instalační program také buď seskupit rozhraní Shared Framework Installer, nebo ověřit, že je součástí instalace aplikace.  Instalace sdíleného rozhraní vyžaduje přístup správce nebo root, protože se jedná o počítač v rámci počítače.

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>Nasazení závislé na rozhraní se závislostmi třetích stran

Nasazení rozhraní závislého na rozhraní s jednou nebo více závislostmi třetí strany vyžaduje, aby byly všechny závislosti k dispozici pro váš projekt. Předtím, než budete moci sestavit aplikaci, jsou vyžadovány tyto další kroky:

1. Pomocí **Správce balíčků NuGet** přidejte do svého projektu odkaz na balíček NuGet; a pokud balíček ještě není ve vašem systému k dispozici, nainstalujte ho. Správce balíčků otevřete tak, že vyberete **nástroje** > **správce balíčků NuGet** > **Spravovat balíčky NuGet pro řešení**.

1. Ověřte, zda jsou v systému nainstalovány závislosti jiných výrobců (například `Newtonsoft.Json`), a pokud nejsou, nainstalujte je. Karta **Installed (instalovat** ) obsahuje seznam balíčků NuGet nainstalovaných ve vašem systému. Pokud zde `Newtonsoft.Json` není uveden, vyberte kartu **Procházet** a do vyhledávacího pole zadejte "Newtonsoft. JSON". Vyberte `Newtonsoft.Json` a v pravém podokně vyberte svůj projekt před výběrem možnosti **nainstalovat**.

1. Pokud je v systému už `Newtonsoft.Json` nainstalovaná, přidejte ho do svého projektu tak, že ho vyberete v pravém podokně na kartě **Spravovat balíčky pro řešení** .

Nasazení závislé na rozhraní se závislostmi třetích stran je stejně přenosné jako závislosti svých třetích stran. Pokud například knihovna třetí strany podporuje jenom macOS, aplikace není přenosná na systémy Windows. K tomu dojde v případě, že závislost třetí strany závisí na nativním kódu. Dobrým příkladem je [Kestrel Server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), který vyžaduje nativní závislost na [libuv](https://github.com/libuv/libuv). Pokud je vytvořen FDD pro aplikaci s tímto druhem závislosti třetí strany, publikovaný výstup obsahuje složku pro každý [identifikátor modulu runtime (RID)](../rid-catalog.md) , který nativní závislost podporuje (a který existuje v jeho balíčku NuGet).

## <a name="simpleSelf"></a>Samostatné nasazení bez závislostí třetích stran

Nasazení samostatného nasazení bez závislostí třetích stran zahrnuje vytvoření projektu, úpravu souboru *csproj* , sestavování, testování a publikování aplikace. Jednoduchý příklad napsaný v C# tomto příkladu znázorňuje proces. Začněte tím, že vytvoříte, zakódujete a otestujete projekt stejně jako nasazení závislé na rozhraní:

1. Vytvořte projekt.

   Vyberte **Soubor** > **Nový** > **Projekt**. V dialogovém okně **Nový projekt** rozbalte v podokně **nainstalované** typy projektůC# kategorii projektu (nebo Visual Basic) vašeho jazyka, zvolte možnost **.NET Core**a potom v prostředním podokně vyberte šablonu **Konzolová aplikace (.NET Core)** . Do textového pole **název** zadejte název projektu, například "SCD", a klikněte na tlačítko **OK** .

1. Přidejte zdrojový kód aplikace.

   V editoru otevřete soubor *program.cs* nebo *program. vb* a nahraďte automaticky generovaný kód následujícím kódem. Vyzve uživatele, aby zadal text a zobrazil jednotlivá slova zadaná uživatelem. Používá regulární výraz `\w+` k oddělení slov ve vstupním textu.

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. Určete, zda chcete použít invariantní režim globalizace.

   Zejména v případě, že je vaše aplikace cílena na Linux, můžete snížit celkovou velikost svého nasazení využitím [režimu invariantování globalizace](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md). Režim invariantní globalizace je vhodný pro aplikace, které nejsou globálně závislé a které mohou použít konvence formátování, konvence velikosti písmen a pořadí řazení [invariantní jazykové verze](xref:System.Globalization.CultureInfo.InvariantCulture).

   Chcete-li povolit režim invariant, klikněte pravým tlačítkem myši na projekt (ne řešení) v **Průzkumník řešení**a vyberte **Upravit SCD. csproj** nebo **upravte SCD. vbproj**. Pak přidejte do souboru následující zvýrazněné řádky:

   [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj?highlight=6-8)]

1. Vytvořte sestavení pro ladění aplikace.

   Vyberte **sestavení** **řešení**Build > . Můžete také zkompilovat a **Spustit ladicí sestavení** vaší aplikace, a to tak, že vyberete ladění > **Spustit ladění**. Tento krok ladění vám umožní identifikovat problémy s vaší aplikací, když běží na hostitelské platformě. Pořád ho budete muset otestovat na každé cílové platformě.

   Pokud jste povolili režim invariantní globalizace, měli byste se zejména ujistit, zda neexistují data citlivá na jazykovou verzi vhodná pro vaši aplikaci.

Po dokončení ladění můžete publikovat samostatně zahrnuté nasazení:

<!-- markdownlint-disable MD025 -->

# <a name="visual-studio-156-and-earlier"></a>[Visual Studio 15,6 a starší](#tab/vs156)

Po ladění a otestování programu vytvořte soubory, které mají být nasazeny s vaší aplikací pro každou platformu, na kterou cílíte.

Pokud chcete svou aplikaci publikovat ze sady Visual Studio, udělejte toto:

1. Definujte platformy, na které bude vaše aplikace cílit.

   1. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt (ne řešení) a vyberte **Upravit SCD. csproj**.

   1. Vytvořte značku `<RuntimeIdentifiers>` v oddílu `<PropertyGroup>` souboru *csproj* , který definuje platformy, na které vaše aplikace cílí, a určete identifikátor modulu runtime (RID) pro každou cílovou platformu. Je také nutné přidat středník pro oddělení identifikátorů RID. Seznam identifikátorů modulu runtime najdete v tématu [katalog identifikátorů modulu runtime](../rid-catalog.md) .

   Například následující příklad označuje, že aplikace běží na 64 operačních systémech Windows 10 a 64 operačním systému OS X verze 10,11.

   ```xml
   <PropertyGroup>
      <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
   </PropertyGroup>
   ```

   Element `<RuntimeIdentifiers>` může přejít do jakékoli `<PropertyGroup>`, kterou máte v souboru *csproj* . V této části se zobrazí kompletní vzorový soubor *csproj* .

1. Publikujte svoji aplikaci.

   Po ladění a otestování programu vytvořte soubory, které mají být nasazeny s vaší aplikací pro každou platformu, na kterou cílíte.

   Pokud chcete svou aplikaci publikovat ze sady Visual Studio, udělejte toto:

      1. Změňte konfiguraci řešení z **Debug** na **release** na panelu nástrojů a sestavte verzi (nikoli ladění) vaší aplikace.

      1. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt (ne řešení) a vyberte **publikovat**.

      1. Na kartě **publikovat** vyberte **publikovat**. Visual Studio zapisuje soubory, které tvoří vaši aplikaci, do místního systému souborů.

      1. Na kartě **publikovat** se teď zobrazí jeden profil, **FolderProfile**. Nastavení konfigurace profilu se zobrazí v části **Souhrn** na kartě. **cílový modul runtime** určuje, který modul runtime byl publikován a **cílové umístění** identifikuje, kde byly zapsány soubory pro nasazení, které jsou samostatně obsaženy.

      1. Visual Studio ve výchozím nastavení zapisuje všechny publikované soubory do jednoho adresáře. Pro usnadnění práce je nejlepší vytvořit samostatné profily pro každý cílový modul runtime a umístit publikované soubory do adresáře specifického pro platformu. To zahrnuje vytvoření samostatného profilu publikování pro každou cílovou platformu. Takže teď aplikaci pro každou platformu znovu sestavíte následujícím způsobem:

         1. V dialogovém okně **publikovat** vyberte **vytvořit nový profil** .

         1. V dialogovém okně **vybrat cíl publikování** změňte umístění **složky** na *bin\Release\PublishOutput\win10-x64*. Vyberte **OK**.

         1. V seznamu profilů vyberte nový profil (**FolderProfile1**) a ujistěte se, že je **cílový modul runtime** `win10-x64`. Pokud není, vyberte **Nastavení**. V dialogovém okně **nastavení profilu** změňte **cílový modul runtime** na `win10-x64` a vyberte **Uložit**. V opačném případě vyberte **Zrušit**.

         1. Vyberte **publikovat** a publikujte svou aplikaci pro 64 platformy Windows 10.

         1. Pomocí předchozích kroků znovu vytvořte profil pro `osx.10.11-x64` platformu. **Cílové umístění** je *Bin\Release\PublishOutput\osx.10.11-x64*a **cílový modul runtime** je `osx.10.11-x64`. Název, který Visual Studio přiřadí k tomuto profilu, je **FolderProfile2**.

      Každé cílové umístění obsahuje kompletní sadu souborů (jak soubory aplikace, tak všechny soubory .NET Core) potřebné ke spuštění vaší aplikace.

Spolu se soubory vaší aplikace proces publikování generuje soubor databáze programu (PDB), který obsahuje informace o ladění vaší aplikace. Soubor je vhodný hlavně pro ladění výjimek. Můžete se rozhodnout, že ho nechcete zabalit do souborů vaší aplikace. Měli byste ji však uložit v případě, že chcete ladit sestavení pro vydání aplikace.

Nasaďte publikované soubory jakýmkoli způsobem. Můžete je například zabalit do souboru zip, použít jednoduchý příkaz `copy`, nebo je nasadit s libovolným instalačním balíčkem podle vašeho výběru.

Následuje úplný soubor *csproj* pro tento projekt.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

# <a name="visual-studio-157-and-later"></a>[Visual Studio 15,7 a novější](#tab/vs157)

Po ladění a otestování programu vytvořte soubory, které mají být nasazeny s vaší aplikací pro každou platformu, na kterou cílíte. To zahrnuje vytvoření samostatného profilu pro každou cílovou platformu.

Pro každou platformu, na kterou vaše aplikace cílí, udělejte toto:

1. Vytvořte profil pro cílovou platformu.

   Pokud se jedná o první profil, který jste vytvořili, klikněte pravým tlačítkem na projekt (ne řešení) v **Průzkumník řešení** a vyberte **publikovat**.

   Pokud jste už profil vytvořili, klikněte pravým tlačítkem na projekt a otevřete dialog **publikovat** , pokud už není otevřený. Pak vyberte **Nový profil**.

   Otevře se dialogové okno **vybrat cíl publikování** .

1. Vyberte umístění, kde aplikace Visual Studio publikuje vaši aplikaci.

   Pokud publikujete pouze na jednu platformu, můžete přijmout výchozí hodnotu v textovém poli **Zvolit složku** ; Tím se publikuje nasazení aplikace závislé na rozhraní do adresáře *\<projekt-adresář > \bin\Release\netcoreapp2.1\publish* .

   Pokud publikujete na více než jednu platformu, přidejte řetězec, který identifikuje cílovou platformu. Například pokud připojíte řetězec "Linux" k cestě k souboru, Visual Studio publikuje nasazení aplikace závislé na rozhraní do adresáře *\<Project-directory > \bin\Release\netcoreapp2.1\publish\linux* .

1. Vytvořte profil tak, že vyberete ikonu rozevíracího seznamu vedle tlačítka **publikovat** a vyberete **vytvořit profil**. Pak vyberte tlačítko **vytvořit profil** a vytvořte profil.

1. Uveďte, že publikujete samostatné nasazení a definujete platformu, na kterou bude vaše aplikace cílit.

   1. V dialogovém okně **publikovat** vyberte odkaz **Konfigurovat** a otevřete dialogové okno **nastavení profilu** .

   1. V seznamu **režim nasazení** vyberte možnost **samostatné – obsaženo** .

   1. V rozevíracím seznamu **cílový modul runtime** vyberte jednu z platforem, na kterou vaše aplikace cílí.

   1. Vyberte **Uložit** a potvrďte provedené změny a zavřete dialogové okno.

1. Pojmenujte profil.

   1. Vyberte **akce** > **Přejmenovat profil** pro pojmenování profilu.

   2. Přiřaďte profilu název, který identifikuje cílovou platformu, a pak vyberte **Uložit*.

Zopakováním těchto kroků definujte všechny další cílové platformy, na které vaše aplikace cílí.

Nakonfigurovali jste profily a teď jste připraveni publikovat svou aplikaci. Použijte následující postup:

   1. Pokud okno **publikovat** není momentálně otevřené, klikněte pravým tlačítkem myši na projekt (ne řešení) v **Průzkumník řešení** a vyberte **publikovat**.

   2. Vyberte profil, který chcete publikovat, a pak vyberte **publikovat**. Udělejte to pro každý profil, který se má publikovat.

   Každé cílové umístění (v případě našeho příkladu bin\release\netcoreapp2.1\publish\\*Profile-název* obsahuje úplnou sadu souborů (jak soubory aplikace, tak všechny soubory .NET Core) potřebné ke spuštění vaší aplikace.

Spolu se soubory vaší aplikace proces publikování generuje soubor databáze programu (PDB), který obsahuje informace o ladění vaší aplikace. Soubor je vhodný hlavně pro ladění výjimek. Můžete se rozhodnout, že ho nechcete zabalit do souborů vaší aplikace. Měli byste ji však uložit v případě, že chcete ladit sestavení pro vydání aplikace.

Nasaďte publikované soubory jakýmkoli způsobem. Můžete je například zabalit do souboru zip, použít jednoduchý příkaz `copy`, nebo je nasadit s libovolným instalačním balíčkem podle vašeho výběru.

Následuje úplný soubor *csproj* pro tento projekt.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
</Project>
```

Kromě toho Visual Studio vytvoří samostatný profil publikování (\*. pubxml) pro každou cílovou platformu. Například soubor pro náš profil Linux (Linux. pubxml) se zobrazí takto:

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

## <a name="self-contained-deployment-with-third-party-dependencies"></a>Samostatné nasazení s závislostmi třetích stran

Nasazení samostatně uzavřeného nasazení s jednou nebo více závislostmi třetích stran zahrnuje přidání závislostí. Předtím, než budete moci sestavit aplikaci, jsou vyžadovány tyto další kroky:

1. Pomocí **Správce balíčků NuGet** přidejte do svého projektu odkaz na balíček NuGet; a pokud balíček ještě není ve vašem systému k dispozici, nainstalujte ho. Správce balíčků otevřete tak, že vyberete **nástroje** > **správce balíčků NuGet** > **Spravovat balíčky NuGet pro řešení**.

1. Ověřte, zda jsou v systému nainstalovány závislosti jiných výrobců (například `Newtonsoft.Json`), a pokud nejsou, nainstalujte je. Karta **Installed (instalovat** ) obsahuje seznam balíčků NuGet nainstalovaných ve vašem systému. Pokud zde `Newtonsoft.Json` není uveden, vyberte kartu **Procházet** a do vyhledávacího pole zadejte "Newtonsoft. JSON". Vyberte `Newtonsoft.Json` a v pravém podokně vyberte svůj projekt před výběrem možnosti **nainstalovat**.

1. Pokud je v systému už `Newtonsoft.Json` nainstalovaná, přidejte ho do svého projektu tak, že ho vyberete v pravém podokně na kartě **Spravovat balíčky pro řešení** .

Následuje kompletní soubor *csproj* pro tento projekt:

# <a name="visual-studio-156-and-earlier"></a>[Visual Studio 15,6 a starší](#tab/vs156)

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

# <a name="visual-studio-157-and-later"></a>[Visual Studio 15,7 a novější](#tab/vs157)

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

Při nasazení aplikace jsou také součástí souborů aplikace všechny závislosti třetích stran používané ve vaší aplikaci. V systému, ve kterém je aplikace spuštěná, se nevyžadují knihovny třetích stran.

Samostatné nasazení můžete nasadit jenom pomocí knihovny třetích stran na platformy podporované touto knihovnou. To se podobá tomu, že se závislosti třetích stran s nativními závislostmi v nasazení závislém na rozhraní, kde nativní závislosti neexistují na cílové platformě, pokud se tam dříve nenainstalovaly.

## <a name="see-also"></a>Viz také

- [Nasazení aplikace .NET Core](index.md)
- [Katalog identifikátorů runtime .NET Core (RID)](../rid-catalog.md)
