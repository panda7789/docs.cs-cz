---
title: Nasazení aplikace .NET core pomocí sady Visual Studio
description: Další nasazení aplikace .NET Core pomocí sady Visual Studio
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 238e43149eebb59ecbb25dfc3976f912e0ae8b01
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="deploying-net-core-apps-with-visual-studio"></a>Nasazení .NET základní aplikace pomocí sady Visual Studio

Můžete nasadit aplikaci .NET Core buď jako *nasazení závislé na framework*, který obsahuje binární soubory vaší aplikace, ale závisí na přítomnost .NET Core v cílovém systému, nebo jako *samostatný nasazení*, což zahrnuje aplikace a binární soubory .NET Core. Přehled nasazení aplikace .NET Core najdete v tématu [nasazení aplikace .NET Core](index.md).

Následující části vysvětlují, jak pomocí sady Microsoft Visual Studio vytvořit následující typy nasazení:

- Nasazení závislé na Framework
- Nasazení závislé na Framework se závislostmi třetích stran
- Samostatná nasazení
- Samostatná nasazení se závislostmi třetích stran

Informace o vývoji aplikací .NET Core pomocí sady Visual Studio najdete v tématu [požadavky pro .NET Core v systému Windows](../windows-prerequisites.md#prerequisites-with-visual-studio-2017).

## <a name="framework-dependent-deployment"></a>Nasazení závislé na Framework

Nasazení závislé na framework nasazení nemá žádné závislosti třetích stran zahrnuje vytváření, testování a publikování aplikace. Jednoduchý příklad napsané v C# znázorňuje proces.  

1. Vytvoření projektu.

   Select **File** > **New** > **Project**. V **nový projekt** dialogovém okně, vyberte **.NET Core** v **nainstalovaná** typy podokně projektu a vyberte **konzolové aplikace (.NET Core)** Šablona v prostředním podokně. Zadejte název projektu, například "Chyba" v **název** textové pole. Vyberte **OK** tlačítko.

1. Přidejte zdrojový kód aplikace.

   Otevřete *Program.cs* souboru v editoru a automaticky vygenerovaný kód nahraďte následujícím kódem. Se zobrazí výzvu k zadání textu a zobrazí jednotlivých slov zadané uživatelem. Používá regulární výraz `\w+` slov v vstupního textu.

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. Vytvořte sestavení ladicí verze vaší aplikace.

   Vyberte **sestavení** > **sestavení řešení**. Můžete také zkompilování a spuštění ladění sestavení aplikace tak, že vyberete **ladění** > **spustit ladění**.

1. Nasazení aplikace.

   Po ladit a testovat program, vytvoření souborů k nasazení s vaší aplikací. Pokud chcete publikovat ze sady Visual Studio, postupujte takto:

      1. Změňte konfiguraci řešení z **ladění** k **verze** na panelu nástrojů na verzi sestavení a verze (nikoli a ladění) vaší aplikace.

      1. Klikněte pravým tlačítkem na projekt (ne řešení) v **Průzkumníku řešení**a vyberte **publikovat**.

      1. V **publikovat** vyberte **publikovat**. Visual Studio zapíše soubory, které tvoří vaši aplikaci do místního systému souborů.

      1. **Publikovat** kartě se teď zobrazují jediného profilu, **FolderProfile**. Nastavení profilu konfigurace se zobrazují v **Souhrn** části karty.

   Výsledné soubory jsou umístěny v adresáři s názvem `PublishOutput` , je v podadresáři vašeho projektu *.\bin\release* podadresáři.

Proces publikování společně se soubory aplikace vysílá soubor databáze (.pdb) program, který obsahuje ladicí informace o vaší aplikaci. Soubor je užitečné především pro ladění výjimek. Je možné, není-li vytvořit balíček s soubory aplikace. Ale uložte jej v případě, že chcete ladit sestavení pro vydání vaší aplikace.

Kompletní sadu souborů aplikace žádným způsobem, který chcete nasaďte. Například můžete balíček je v souboru Zip, pomocí jednoduché `copy` příkaz nebo nasadit pomocí jakékoli instalačního balíčku podle svého výběru. Po instalaci uživatelů můžete pak spouštět aplikace pomocí `dotnet` příkaz a poskytnutí názvu souboru, jako například `dotnet fdd.dll`.

Kromě binární soubory aplikace instalačním programem vaší by také buď vytvořit balíček instalačního programu sdílený framework nebo kontrolovat předpokladem je jako součást instalace aplikace.  Instalace sdílený framework vyžaduje přístup správce nebo nejnižší vzhledem k tomu, že je celého systému.

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>Nasazení závislé na Framework se závislostmi třetích stran

Nasazení nasazení framework závislé na jeden nebo více třetích stran závislosti vyžaduje, aby všechny závislosti projektu k dispozici. Následující kroky jsou požadovány, než můžete sestavit aplikaci:

1. Použití **Správce balíčků NuGet** přidat odkaz na balíček NuGet do projektu; a pokud balíček již není k dispozici v systému, nainstalujte ji. Chcete-li otevřít správce balíčku, vyberte **nástroje** > **Správce balíčků NuGet** > **spravovat balíčky NuGet pro řešení**.

1. Potvrďte, že `Newtonsoft.Json` na vašem systému je nainstalovaná a pokud není, nainstalujte ji. **Nainstalovaná** karta Vypíše seznam balíčků NuGet v systému nainstalována. Pokud `Newtonsoft.Json` není uveden, vyberte **Procházet** kartě a do vyhledávacího pole zadejte "Newtonsoft.Json". Vyberte `Newtonsoft.Json` a v pravém podokně vyberte projektu před výběrem **nainstalovat**.

1. Pokud `Newtonsoft.Json` je již nainstalován ve vašem systému, přidejte ji do projektu výběrem projektu v pravém podokně **spravovat balíčky pro řešení** kartě.

Upozorňujeme, že nasazení závislé na framework se závislostmi třetí strany se pouze jako přenosný jeho závislé součásti třetích stran. Například pokud knihovnu třetích stran podporuje pouze systému macOS, aplikace není přenosné pro systémy Windows. To se stane, když závislost třetích stran, samotné závisí na nativního kódu. Dobrým příkladem tohoto objektu je [Kestrel server](http://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), který vyžaduje nativní závislost na [libuv](https://github.com/libuv/libuv). Když disketové jednotky se vytvoří pro aplikace s tímto typem závislosti třetích stran, publikované výstup obsahuje složku pro každý [identifikátor Runtime (RID)](../rid-catalog.md) podporující nativní závislost (a která existuje v jeho balíčku NuGet).

## <a name="simpleSelf"></a> Samostatná nasazení bez závislosti na třetích stran

Nasazení samostatná nasazení nemá žádné závislosti třetích stran zahrnuje vytvoření projektu, úprava *csproj* souborů, vytváření, testování a publikování aplikace. Jednoduchý příklad napsané v C# znázorňuje proces. 

1. Vytvoření projektu.

   Select **File** > **New** > **Project**. V **přidat nový projekt** dialogovém okně, vyberte **.NET Core** v **nainstalovaná** typy podokně projektu a vyberte **konzolové aplikace (.NET Core)** Šablona v prostředním podokně. Zadejte název projektu, například "SCD" **název** textového pole a vyberte **OK** tlačítko.

1. Přidejte zdrojový kód aplikace.

   Otevřete *Program.cs* souboru ve svém editoru a automaticky vygenerovaný kód nahraďte následujícím kódem. Se zobrazí výzvu k zadání textu a zobrazí jednotlivých slov zadané uživatelem. Používá regulární výraz `\w+` slov v vstupního textu.

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. Definujte platformy, které se zaměří na vaši aplikaci.

   1. Klikněte pravým tlačítkem na projekt (ne řešení) v **Průzkumníku řešení**a vyberte **upravit SCD.csproj**.

   1. Vytvoření `<RuntimeIdentifiers>` značky v `<PropertyGroup>` část vaší *csproj* soubor, který definuje platformy cíle vaší aplikace, a zadejte runtime identifikátorů (RID) pro každou platformu, která cílí. Všimněte si, že je také nutné přidat středníkem k oddělení identifikátorů RID. V tématu [Runtime identifikátor katalogu](../rid-catalog.md) seznam identifikátorů modulu runtime. 

   Následující příklad například označuje, že aplikace běží na 64bitové verze Windows 10 operační systémy a operační systém 10.11 verze OS X 64-bit.

```xml
<PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
</PropertyGroup>
```
   Všimněte si, že `<RuntimeIdentifiers>` element můžete přejít do jakéhokoli `<PropertyGroup>` , ke které máte vaší *csproj* souboru. Ucelenou ukázku *csproj* souboru se zobrazí později v této části.

1. Vytvořte sestavení ladicí verze vaší aplikace.

   Vyberte **sestavení** > **sestavení řešení**. Můžete také zkompilování a spuštění ladění sestavení aplikace tak, že vyberete **ladění** > **spustit ladění**.

1. Publikování aplikace.

   Po ladit a testovat program, vytvoření souborů k nasazení s vaší aplikací pro každou platformu, cílem.

   K publikování aplikace ze sady Visual Studio, postupujte takto:

      1. Změňte konfiguraci řešení z **ladění** k **verze** na panelu nástrojů na verzi sestavení a verze (nikoli a ladění) vaší aplikace.

      1. Klikněte pravým tlačítkem na projekt (ne řešení) v **Průzkumníku řešení** a vyberte **publikovat**. 

      1. V **publikovat** vyberte **publikovat**. Visual Studio zapíše soubory, které tvoří vaši aplikaci do místního systému souborů.

      1. **Publikovat** kartě se teď zobrazují jediného profilu, **FolderProfile**. Nastavení profilu konfigurace se zobrazují v **Souhrn** části karty. **Cíl Runtime** identifikuje publikovali které runtime a **cílové umístění** identifikuje, kde byly napsány souborů pro samostatný nasazení.

      1. Visual Studio ve výchozím nastavení zapíše že všechny publikované soubory do jednoho adresáře. Pro usnadnění práce je nejvhodnější vytvořit samostatný profil pro každý cílový modul runtime a publikovaná soubory umístit do adresáře specifické pro platformu. To zahrnuje vytváření samostatný profil publikování pro každou cílovou platformu. Proto nyní znovu sestavte aplikaci pro každou platformu následujícím způsobem:

         1. Vyberte **vytvořit nový profil** v **publikovat** dialogové okno.

         1. V **vyberte cíl publikování** dialogové okno, změny **vyberte složku,** umístění pro *bin\Release\PublishOutput\win10 x64*. Vyberte **OK**.

         1. Vyberte profil, nové (**FolderProfile1**) v seznamu profilů a ujistěte se, že **cílový modul Runtime** je `win10-x64`. Pokud tomu tak není, vyberte **nastavení**. V **nastavení profilu** dialogové okno, změny **cílový modul Runtime** k `win10-x64` a vyberte **Uložit**. Jinak vyberte možnost **zrušit**.

         1. Vyberte **publikovat** k publikování aplikace pro 64bitové platformy Windows 10.

         1. Postupujte podle předchozích kroků znovu a vytvořit profil pro `osx.10.11-x64` platformy. **Cílové umístění** je *bin\Release\PublishOutput\osx.10.11-x64*a **cílový modul Runtime** je `osx.10.11-x64`. Název sady Visual Studio přiřadí k tomuto profilu je **FolderProfile2**.

      Všimněte si, že každé cílové umístění obsahuje kompletní sadu souborů (soubory aplikace a všechny soubory .NET Core) potřebné ke spuštění aplikace.

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

Nasazení samostatná nasazení s jeden nebo více závislostí třetí strany vyžaduje přidání závislosti. Následující kroky jsou požadovány, než můžete sestavit aplikaci:

1. Použití **Správce balíčků NuGet** přidat odkaz na balíček NuGet do projektu; a pokud balíček již není k dispozici v systému, nainstalujte ji. Chcete-li otevřít správce balíčku, vyberte **nástroje** > **Správce balíčků NuGet** > **spravovat balíčky NuGet pro řešení**.

1. Potvrďte, že `Newtonsoft.Json` na vašem systému je nainstalovaná a pokud není, nainstalujte ji. **Nainstalovaná** karta Vypíše seznam balíčků NuGet v systému nainstalována. Pokud `Newtonsoft.Json` není uveden, vyberte **Procházet** kartě a do vyhledávacího pole zadejte "Newtonsoft.Json". Vyberte `Newtonsoft.Json` a v pravém podokně vyberte projektu před výběrem **nainstalovat**.

1. Pokud `Newtonsoft.Json` je již nainstalován ve vašem systému, přidejte ji do projektu výběrem projektu v pravém podokně **spravovat balíčky pro řešení** kartě.

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

Všimněte si, že lze nasadit pouze samostatná nasazení s knihovnou třetích stran na platformách podporovaných aplikací této knihovny. Toto je podobná s závislosti třetích stran s nativní závislosti ve vašem nasazení závislé na framework, kde neexistují nativní závislosti na cílové platformy, pokud byly dříve nainstalovány existuje.

# <a name="see-also"></a>Viz také
[Nasazení aplikace .NET core](index.md)   
[Katalog .NET core Runtime identifikátor (RID)](../rid-catalog.md)   
