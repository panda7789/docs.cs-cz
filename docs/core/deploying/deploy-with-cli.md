---
title: Nasazení aplikace .NET core pomocí nástrojů CLI
description: Zjistěte, nasazení aplikace .NET Core pomocí nástrojů rozhraní příkazového řádku (CLI)
author: rpetrusha
ms.author: ronpet
ms.date: 09/05/2018
dev_langs:
- csharp
- vb
ms.openlocfilehash: a7e810372d831699eae777186385e45fe65cdf45
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48046497"
---
# <a name="deploying-net-core-apps-with-command-line-interface-cli-tools"></a>Nasazení aplikace .NET Core pomocí nástrojů rozhraní příkazového řádku (CLI)

Můžete nasadit aplikaci .NET Core buď jako *nasazení závisí na architektuře*, který obsahuje binární soubory vaší aplikace, ale závisí na přítomnosti .NET Core v cílovém systému, nebo jako *samostatná nasazení*, což zahrnuje aplikace a binární soubory .NET Core. Přehled najdete v tématu [nasazení aplikace .NET Core](index.md).

Následující části vysvětlují, jak používat [nástroje rozhraní příkazového řádku .NET Core](../tools/index.md) vytvořit následující typy nasazení:

- Nasazení závisí na architektuře
- Nasazení závisí na architektuře s závislostí třetích stran
- Samostatná nasazení
- Samostatná nasazení s závislostí třetích stran

Při práci z příkazového řádku, můžete program editoru podle vašeho výběru. Pokud je váš program editor [Visual Studio Code](https://code.visualstudio.com), nástroje command console v prostředí Visual Studio Code můžete otevřít tak, že vyberete **zobrazení** > **integrovaný terminál**.

## <a name="framework-dependent-deployment"></a>Nasazení závisí na architektuře

Nasazení závisí na architektuře bez závislostí třetích stran zahrnuje vytváření, testování a publikování aplikace. Jednoduchý příklad napsané v jazyce C# znázorňuje proces.

1. Vytvořte adresář projektu.

   Vytvořte adresář pro váš projekt a nastavte ji váš aktuální adresář.

1. Vytvoření projektu.

   Z příkazového řádku, zadejte [dotnet nové konzoly](../tools/dotnet-new.md) vytvořte nový projekt konzoly C# nebo [dotnet nové konzoly - lang vb](../tools/dotnet-new.md) vytvoříte nový projekt konzoly jazyka Visual Basic v tomto adresáři.

1. Přidejte zdrojový kód aplikace.

   Otevřít *Program.cs* nebo *soubor Program.vb* souboru ve svém editoru a automaticky vygenerovaném kódu nahraďte následujícím kódem. Se zobrazí výzva k zadání textu a zobrazuje jednotlivá slova zadané uživatelem. Používá regulární výraz `\w+` k oddělení slov ve vstupním textu.

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. Aktualizujte závislosti projektu a nástroje.

   Spustit [dotnet restore](../tools/dotnet-restore.md) ([viz Poznámka](#dotnet-restore-note)) příkaz pro obnovení závislosti zadaný ve vašem projektu.

1. Vytvořte sestavení pro ladění vaší aplikace.

   Použití [dotnet sestavení](../tools/dotnet-build.md) příkazu k sestavení aplikace nebo [dotnet spustit](../tools/dotnet-run.md) příkazu sestavit a spustit ho.

1. Nasazení vaší aplikace.

   Po ladit a testovat program, vytvořte nasazení pomocí následujícího příkazu:

      ```console
      dotnet publish -f netcoreapp2.1 -c Release
      ```
   Tím se vytvoří vydanou verzi (místo ladění) verze vaší aplikace. Výsledné soubory jsou umístěny v adresáři s názvem *publikovat* , který je v podadresáři vašeho projektu *bin* adresáře.

   Proces publikování spolu se soubory vaší aplikace, generuje soubor databáze (PDB) programu, který obsahuje ladicí informace o vaší aplikaci. Soubor je užitečné hlavně pro ladění výjimky. Můžete nechcete distribuovat s vaší aplikace soubory. Měli byste, však uložit ho v případě, že chcete ladit sestavení pro vydání aplikace.

   Můžete nasadit kompletní sadu souborů aplikace žádným způsobem, který vám vyhovuje. Například lze zabalit jako soubor Zip, použít jednoduchý `copy` příkazu, nebo je nasadit v balíčcích instalace podle vašeho výběru.

1. Spuštění aplikace

   Po instalaci se uživatelé můžou spustit vaši aplikaci pomocí `dotnet` příkazu a poskytuje název souboru aplikace, jako například `dotnet fdd.dll`.

   Kromě binární soubory aplikace Instalační program by měl také vytvoření balíčku Instalační služby sdílené architektuře nebo vyhledat jako předpoklad jako součást instalace aplikace.  Instalace rozhraní sdílené vyžaduje přístup správce/root.

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>Nasazení závisí na architektuře s závislostí třetích stran

Nasazení závisí na architektuře se jeden nebo více závislostí třetích stran vyžaduje, aby tyto závislosti k dispozici pro váš projekt. Další dva kroky jsou požadovány, než můžete spustit `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) příkaz:

1. Přidat odkazy na požadované knihovny třetích stran `<ItemGroup>` část vaší *csproj* souboru. Následující `<ItemGroup>` oddíl obsahuje závislost na [Json.NET](http://www.newtonsoft.com/json) jako knihovny třetích stran:

      ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
      ```

1. Pokud jste tak dosud neučinili, stáhněte si balíček NuGet obsahující závislostí třetích stran. Pokud chcete stáhnout balíček, spusťte `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) příkaz po přidání závislosti. Protože závislost vyřeší z místní mezipaměti NuGet na čas publikování, musí být k dispozici ve vašem systému.

Všimněte si, že nasazení závisí na architektuře závislostí třetích stran je pouze jako přenosný jeho závislostí třetích stran. Například pokud knihovny třetí strany pouze podporuje macOS, aplikace není přenosný do systémů Windows. To se stane, když závislostí třetích stran, samotný závisí na nativní kód. Dobrým příkladem tohoto je [Kestrel server](/aspnet/core/fundamentals/servers/kestrel), což vyžaduje nativní závislost na [libuv](https://github.com/libuv/libuv). Po vytvoření disketové jednotky pro aplikace s tímto druhem závislostí třetích stran publikovaný výstup obsahuje složku pro každý [identifikátor modulu Runtime (RID)](../rid-catalog.md) podporující nativní závislostí (a, která existuje v jeho balíček NuGet).

## <a name="simpleSelf"></a> Samostatná nasazení bez závislostí třetích stran

Samostatná nasazení bez závislostí třetích stran zahrnuje vytvoření projektu, úpravy *csproj* souboru, sestavování, testování a publikování aplikace. Jednoduchý příklad napsané v jazyce C# znázorňuje proces. Tento příklad ukazuje, jak vytvořit samostatná nasazení pomocí [nástrojů dotnet](../tools/dotnet.md) z příkazového řádku.

1. Vytvořte adresář pro projekt.

   Vytvořte adresář pro váš projekt a nastavte ji váš aktuální adresář.

1. Vytvoření projektu.

   Z příkazového řádku, zadejte [nové konzoly dotnet](../tools/dotnet-new.md) v tomto adresáři vytvořte nový projekt konzoly C#.

1. Přidejte zdrojový kód aplikace.

   Otevřít *Program.cs* souboru ve svém editoru a automaticky vygenerovaném kódu nahraďte následujícím kódem. Se zobrazí výzva k zadání textu a zobrazuje jednotlivá slova zadané uživatelem. Používá regulární výraz `\w+` k oddělení slov ve vstupním textu.

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]
1. Definování platformy, které se zaměří na vaši aplikaci.

   Vytvoření `<RuntimeIdentifiers>` značku `<PropertyGroup>` část vaší *csproj* soubor, který definuje platformy, zaměřuje a zadejte identifikátor modulu runtime (RID) pro každou platformu, která je cílem vaší aplikace. Všimněte si, že budete také muset přidat středníkem k oddělení identifikátory RID. Zobrazit [katalog identifikátorů modulu Runtime](../rid-catalog.md) seznam identifikátorů modulů runtime.

   Například následující `<PropertyGroup>` části označuje, že aplikace běží na 64bitová verze Windows 10 operačních systémů a operačním systému OS 10.11 verze X 64-bit.

     ```xml
     <PropertyGroup>
         <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
     </PropertyGroup>
     ```

   Všimněte si, že `<RuntimeIdentifiers>` element lze použít v libovolném `<PropertyGroup>` ve vašich *csproj* souboru. Úplnou ukázku *csproj* souboru se zobrazí později v této části.

1. Aktualizujte závislosti projektu a nástroje.

   Spustit [dotnet restore](../tools/dotnet-restore.md) ([viz Poznámka](#dotnet-restore-note)) příkaz pro obnovení závislosti zadaný ve vašem projektu.

1. Určete, jestli chcete použít režim globalizace invariantní.

   Zejména v případě, že vaše aplikace cílí na Linux, můžete snížit celkovou velikost vašeho nasazení s využitím [invariantní režimu globalizace](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md). Globalizace invariantní režim je užitečný pro aplikace, které nejsou globální a které používají konvence formátování, konvence malých a velkých písmen a řetězec porovnání a řazení pořadí [invariantní jazyková verze](xref:System.Globalization.CultureInfo.InvariantCulture).

   Výchozí režim povolit, klikněte pravým tlačítkem na projekt (nikoli řešení) v **Průzkumníka řešení**a vyberte **upravit SCD.csproj** nebo **upravit SCD.vbproj**. Pak přidejte následující zvýrazněný řádky do souboru:

 [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj)]

1. Vytvořte sestavení pro ladění vaší aplikace.

   Z příkazového řádku, použijte [dotnet sestavení](../tools/dotnet-build.md) příkazu.

1. Po ladit a testovat program, vytvoření souborů k nasazení s vaší aplikací pro každou platformu, zaměřuje.

   Použití `dotnet publish` příkaz pro obě cílových platforem následujícím způsobem:

      ```console
      dotnet publish -c Release -r win10-x64
      dotnet publish -c Release -r osx.10.11-x64
      ```

   Tím se vytvoří vydanou verzi (místo ladění) verze vaší aplikace pro každou cílovou platformu. Výsledné soubory jsou umístěny v podadresáři s názvem *publikovat* , který je v podadresáři vašeho projektu *.\bin\Release\netcoreapp2.1\<runtime_identifier >* podadresáře. Všimněte si, že každý podadresář obsahuje kompletní sadu souborů (soubory aplikace a všechny soubory .NET Core) potřebné pro spuštění vaší aplikace.

Proces publikování spolu se soubory vaší aplikace, generuje soubor databáze (PDB) programu, který obsahuje ladicí informace o vaší aplikaci. Soubor je užitečné hlavně pro ladění výjimky. Můžete není balíček se soubory vaší aplikace. Měli byste, však uložit ho v případě, že chcete ladit sestavení pro vydání aplikace.

Nasaďte publikované soubory žádným způsobem, který vám vyhovuje. Například lze zabalit jako soubor Zip, použít jednoduchý `copy` příkazu, nebo je nasadit v balíčcích instalace podle vašeho výběru.

Tady je úplný *csproj* souboru pro tento projekt.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a>Samostatná nasazení s závislostí třetích stran

Samostatná nasazení s jeden nebo více závislostí třetích stran, zahrnuje přidání závislosti. Další dva kroky jsou požadovány, než můžete spustit `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) příkaz:

1. Přidat odkazy na žádné knihovny třetích stran `<ItemGroup>` část vaší *csproj* souboru. Následující `<ItemGroup>` části používá technologii Json.NET jako knihovny třetí strany.

    ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
    ```

1. Pokud jste tak dosud neučinili, stáhněte si balíček NuGet obsahující závislostí třetích stran do vašeho systému. Pokud chcete zpřístupnit závislost do aplikace, spusťte `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) příkaz po přidání závislosti. Protože závislost vyřeší z místní mezipaměti NuGet na čas publikování, musí být k dispozici ve vašem systému.

Tady je úplný *csproj* souboru pro tento projekt:

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

Při nasazení vaší aplikace jsou také obsažena případných závislostí třetích stran používají ve vaší aplikaci se soubory aplikace. V systému, na kterém běží aplikace nejsou vyžadovány knihovny třetích stran.

Všimněte si, že lze nasadit pouze samostatná nasazení pomocí knihovny třetí strany na platformách podporovaných aplikací tuto knihovnu. Toto je podobný s tím, že závislostí třetích stran s nativní závislosti v nasazení závisí na architektuře, kde musí být kompatibilní s platformou, do kterého byla nasazena aplikace, nativní závislosti.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

## <a name="see-also"></a>Viz také:

* [Nasazení aplikace .NET core](index.md)
* [.NET core Runtime identifikátor (RID) katalogu](../rid-catalog.md)
