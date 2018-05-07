---
title: Nasazení aplikace .NET core pomocí nástrojů příkazového řádku
description: Další nasazení aplikace .NET Core pomocí nástrojů rozhraní příkazového řádku (CLI)
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.openlocfilehash: 7b009068422686442ebff83b9400c365f34a3154
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="deploying-net-core-apps-with-command-line-interface-cli-tools"></a>Nasazení aplikací .NET Core pomocí nástrojů rozhraní příkazového řádku (CLI)

Můžete nasadit aplikaci .NET Core buď jako *nasazení závislé na framework*, který obsahuje binární soubory vaší aplikace, ale závisí na přítomnost .NET Core v cílovém systému, nebo jako *samostatný nasazení*, což zahrnuje aplikace a binární soubory .NET Core. Přehled najdete v tématu [nasazení aplikace .NET Core](index.md).

Následující části vysvětlují, jak používat [.NET Core rozhraní příkazového řádku nástroje](../tools/index.md) vytvořit následující typy nasazení:

- Nasazení závislé na Framework
- Nasazení závislé na Framework se závislostmi třetích stran
- Samostatná nasazení
- Samostatná nasazení se závislostmi třetích stran

Při práci z příkazového řádku, můžete použít program editor podle svého výběru. Pokud je váš program editor [Visual Studio Code](https://code.visualstudio.com), nástroje command console můžete otevřít v prostředí Visual Studio Code výběrem **zobrazení** > **integrované Terminálové**.

## <a name="framework-dependent-deployment"></a>Nasazení závislé na Framework

Nasazení závislé na framework nasazení nemá žádné závislosti třetích stran zahrnuje vytváření, testování a publikování aplikace. Jednoduchý příklad napsané v C# znázorňuje proces. 

1. Vytvořte adresář projektu.

   Vytvořte adresář pro svůj projekt a nastavit jej jako aktuální adresář.

1. Vytvoření projektu.

   Z příkazového řádku, zadejte [novou konzolu pro dotnet](../tools/dotnet-new.md) vytvořit nový projekt konzolové C# v tomto adresáři.

1. Přidejte zdrojový kód aplikace.

   Otevřete *Program.cs* souboru ve svém editoru a automaticky vygenerovaný kód nahraďte následujícím kódem. Se zobrazí výzvu k zadání textu a zobrazí jednotlivých slov zadané uživatelem. Používá regulární výraz `\w+` slov v vstupního textu.

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. Aktualizujte závislosti projektu a nástroje.
 
   Spustit [dotnet obnovení](../tools/dotnet-restore.md) ([viz Poznámka](#dotnet-restore-note)) příkazu obnovte závislosti zadaný ve vašem projektu.

1. Vytvořte sestavení ladicí verze vaší aplikace.

   Použití [dotnet sestavení](../tools/dotnet-build.md) k vytvoření aplikace nebo [dotnet. Spusťte](../tools/dotnet-run.md) příkazu sestavit a spustit ho.

1. Nasazení aplikace.

   Po ladit a testovat program, vytvořte nasazení pomocí následujícího příkazu:

      ```console
      dotnet publish -f netcoreapp1.1 -c Release
      ```
   Tím se vytvoří verze (a nikoli ladění) verzi aplikace. Výsledné soubory jsou umístěny v adresáři s názvem *publikování* , je v podadresáři vašeho projektu *bin* adresáře.

   Proces publikování společně se soubory aplikace vysílá soubor databáze (.pdb) program, který obsahuje ladicí informace o vaší aplikaci. Soubor je užitečné především pro ladění výjimek. Můžete se distribuovat soubory vaší aplikace. Ale uložte jej v případě, že chcete ladit sestavení pro vydání vaší aplikace.

   Můžete nasadit kompletní sadu aplikací, které chcete systém souborů. Například můžete balíček je v souboru Zip, pomocí jednoduché `copy` příkaz nebo nasadit pomocí jakékoli instalačního balíčku podle svého výběru.

1. Spuštění aplikace

   Po instalaci, mohou uživatelé provádět vaší aplikace pomocí `dotnet` příkaz a poskytnutí názvu souboru, jako například `dotnet fdd.dll`.

   Kromě binární soubory aplikace instalačním programem vaší by také buď vytvořit balíček instalačního programu sdílený framework nebo kontrolovat předpokladem je jako součást instalace aplikace.  Instalace sdílený framework vyžaduje správce nebo kořenový přístup.

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>Nasazení závislé na Framework se závislostmi třetích stran

Nasazení nasazení framework závislé na jeden nebo více třetích stran závislosti vyžaduje, aby tyto závislosti projektu k dispozici. Dva další kroky jsou požadovány, než můžete spustit `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) příkaz:

1. Přidejte odkazy na požadované knihovny třetích stran `<ItemGroup>` část vaší *csproj* souboru. Následující `<ItemGroup>` část obsahuje závislost na [Json.NET](http://www.newtonsoft.com/json) jako knihovnu třetí strany:

      ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
      ```

1. Pokud jste tak ještě neučinili, stáhněte si balíček NuGet obsahující závislost třetích stran. Chcete-li stáhnout balíček, spusťte `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) příkaz po přidání závislost. Protože závislost vyřešen z místní mezipaměti NuGet v publikovat čas, musí být k dispozici v systému.

Upozorňujeme, že nasazení závislé na framework se závislostmi třetí strany se pouze jako přenosný jeho závislé součásti třetích stran. Například pokud knihovnu třetích stran podporuje pouze systému macOS, aplikace není přenosné pro systémy Windows. To se stane, když závislost třetích stran, samotné závisí na nativního kódu. Dobrým příkladem tohoto objektu je [Kestrel server](/aspnet/core/fundamentals/servers/kestrel), který vyžaduje nativní závislost na [libuv](https://github.com/libuv/libuv). Když disketové jednotky se vytvoří pro aplikace s tímto typem závislosti třetích stran, publikované výstup obsahuje složku pro každý [identifikátor Runtime (RID)](../rid-catalog.md) podporující nativní závislost (a která existuje v jeho balíčku NuGet).

## <a name="simpleSelf"></a> Samostatná nasazení bez závislosti na třetích stran

Nasazení samostatná nasazení bez závislosti na třetích stran zahrnuje vytvoření projektu, úprava *csproj* souborů, vytváření, testování a publikování aplikace. Jednoduchý příklad napsané v C# znázorňuje proces. Tento příklad ukazuje, jak vytvořit samostatný nasazení pomocí [dotnet nástroj](../tools/dotnet.md) z příkazového řádku.

1. Vytvořte adresář pro projekt.

   Vytvořte adresář pro svůj projekt a nastavte jej aktuální adresář.

1. Vytvoření projektu.

   Z příkazového řádku, zadejte [novou konzolu pro dotnet](../tools/dotnet-new.md) vytvořit nový projekt konzolové C# v tomto adresáři.

1. Přidejte zdrojový kód aplikace.

   Otevřete *Program.cs* souboru ve svém editoru a automaticky vygenerovaný kód nahraďte následujícím kódem. Se zobrazí výzvu k zadání textu a zobrazí jednotlivých slov zadané uživatelem. Používá regulární výraz `\w+` slov v vstupního textu.

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. Definujte platformy, které se zaměří na vaši aplikaci.

   Vytvoření `<RuntimeIdentifiers>` značky v `<PropertyGroup>` část vaší *csproj* soubor, který definuje platformy vaší aplikace cílí a zadejte runtime identifikátorů (RID) pro každou platformu, která cílí. Všimněte si, že je také nutné přidat středníkem k oddělení identifikátorů RID. V tématu [Runtime identifikátor katalogu](../rid-catalog.md) seznam identifikátorů modulu runtime. 

   Například následující `<PropertyGroup>` části udává, že se aplikace spouští na 64bitové verze Windows 10 operační systémy a operační systém 10.11 verze OS X 64-bit.

     ```xml
     <PropertyGroup>
         <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
     </PropertyGroup>
     ```

   Všimněte si, že `<RuntimeIdentifiers>` element může vyskytovat v žádném `<PropertyGroup>` ve vaší *csproj* souboru. Ucelenou ukázku *csproj* souboru se zobrazí později v této části.

1. Aktualizujte závislosti projektu a nástroje.

   Spustit [dotnet obnovení](../tools/dotnet-restore.md) ([viz Poznámka](#dotnet-restore-note)) příkazu obnovte závislosti zadaný ve vašem projektu.

1. Vytvořte sestavení ladicí verze vaší aplikace.

   Z příkazového řádku, použijte [dotnet sestavení](../tools/dotnet-build.md) příkaz.

1. Po ladit a testovat program, vytvoření souborů k nasazení s vaší aplikací pro každou platformu, cílem.

   Použití `dotnet publish` příkaz pro obě platformy cílí následujícím způsobem:

      ```console
      dotnet publish -c Release -r win10-x64
      dotnet publish -c Release -r osx.10.11-x64
      ```

   Tím se vytvoří verze (a nikoli ladění) verzi aplikace pro každou cílovou platformu. Výsledné soubory jsou umístěny v podadresáři s názvem *publikování* , je v podadresáři vašeho projektu *.\bin\Release\netcoreapp1.1\<runtime_identifier >* podadresáři. Všimněte si, že každý podadresář obsahuje kompletní sadu souborů (soubory aplikace a všechny soubory .NET Core) potřebné ke spuštění aplikace.

Proces publikování společně se soubory aplikace vysílá soubor databáze (.pdb) program, který obsahuje ladicí informace o vaší aplikaci. Soubor je užitečné především pro ladění výjimek. Je možné, není-li vytvořit balíček s soubory aplikace. Ale uložte jej v případě, že chcete ladit sestavení pro vydání vaší aplikace.

Publikované soubory žádným způsobem, který chcete nasaďte. Například můžete balíček je v souboru Zip, pomocí jednoduché `copy` příkaz nebo nasadit pomocí jakékoli instalačního balíčku podle svého výběru.

Toto je kompletní *csproj* souboru pro tento projekt.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a>Samostatná nasazení se závislostmi třetích stran

Nasazení samostatná nasazení s jeden nebo více závislostí třetí strany vyžaduje přidání závislosti. Dva další kroky jsou požadovány, než můžete spustit `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) příkaz:

1. Přidejte odkazy na všechny knihovny třetích stran `<ItemGroup>` část vaší *csproj* souboru. Následující `<ItemGroup>` část používá technologii Json.NET jako knihovnu třetích stran.

    ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
    ```

1. Pokud jste tak ještě neučinili, stáhněte si balíček NuGet obsahující závislost třetích stran k vašemu systému. Chcete-li zpřístupnit závislost do vaší aplikace, spustit `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) příkaz po přidání závislost. Protože závislost vyřešen z místní mezipaměti NuGet v publikovat čas, musí být k dispozici v systému.

Toto je kompletní *csproj* souboru pro tento projekt:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

Když nasadíte aplikaci, všechny závislosti třetích stran používají ve vaší aplikaci jsou také obsažena s soubory aplikace. Knihovny jiných výrobců nemusí na serveru, na kterém aplikace běží.

Všimněte si, že lze nasadit pouze samostatná nasazení s knihovnou třetích stran na platformách podporovaných aplikací této knihovny. Toto je podobná s závislosti třetích stran s nativní závislosti v nasazení závislé na framework, kde musí být kompatibilní s platformou, pro které je aplikace nasazená nativní závislosti.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

# <a name="see-also"></a>Viz také

[Nasazení aplikace .NET core](index.md)   
[Katalog .NET core Runtime identifikátor (RID)](../rid-catalog.md)   

