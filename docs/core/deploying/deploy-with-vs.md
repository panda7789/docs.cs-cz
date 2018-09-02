---
title: Nasazení aplikace .NET core pomocí sady Visual Studio
description: Zjistěte, nasazení aplikace .NET Core pomocí sady Visual Studio
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.openlocfilehash: 2829bb5a2f5857f6124e5c1f78f5247fe8d1f552
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43407446"
---
# <a name="deploying-net-core-apps-with-visual-studio"></a>Nasazení .NET Core aplikací pomocí sady Visual Studio

Můžete nasadit aplikaci .NET Core buď jako *nasazení závisí na architektuře*, který obsahuje binární soubory vaší aplikace, ale závisí na přítomnosti .NET Core v cílovém systému, nebo jako *samostatná nasazení*, což zahrnuje aplikace a .NET Core binární soubory. Přehled nasazení aplikace .NET Core, naleznete v tématu [nasazení aplikace .NET Core](index.md).

Následující části vysvětlují, jak pomocí sady Microsoft Visual Studio vytvořit následující typy nasazení:

- Nasazení závisí na architektuře
- Nasazení závisí na architektuře s závislostí třetích stran
- Samostatná nasazení
- Samostatná nasazení s závislostí třetích stran

Informace o používání sady Visual Studio pro vývoj aplikací .NET Core najdete v tématu [předpoklady pro .NET Core ve Windows](../windows-prerequisites.md#prerequisites-with-visual-studio-2017).

## <a name="framework-dependent-deployment"></a>Nasazení závisí na architektuře

Nasazení závisí na architektuře bez závislostí třetích stran zahrnuje vytváření, testování a publikování aplikace. Jednoduchý příklad napsané v jazyce C# znázorňuje proces.  

1. Vytvoření projektu.

   Vyberte **souboru** > **nové** > **projektu**. V **nový projekt** dialogového okna, vyberte **.NET Core** v **nainstalováno** podokně typů projektů a vyberte **Konzolová aplikace (.NET Core)** šablon v prostředním podokně. Zadejte název projektu, jako je například "Chyba" v **název** textového pole. Vyberte **OK** tlačítko.

1. Přidejte zdrojový kód aplikace.

   Otevřít *Program.cs* souboru v editoru a automaticky vygenerovaném kódu nahraďte následujícím kódem. Se zobrazí výzva k zadání textu a zobrazuje jednotlivá slova zadané uživatelem. Používá regulární výraz `\w+` k oddělení slov ve vstupním textu.

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. Vytvořte sestavení pro ladění vaší aplikace.

   Vyberte **sestavení** > **sestavit řešení**. Můžete také kompilace a spuštění sestavení pro ladění vaší aplikace tak, že vyberete **ladění** > **spustit ladění**.

1. Nasazení vaší aplikace.

   Po ladit a testovat program, vytvoření souborů k nasazení s vaší aplikací. Chcete-li publikovat ze sady Visual Studio, postupujte takto:

      1. Změňte konfiguraci řešení z **ladění** k **vydání** na panelu nástrojů k sestavení a vydání (tzn. Ne a ladění) verze vaší aplikace.

      1. Klikněte pravým tlačítkem na projekt (nikoli řešení) v **Průzkumníka řešení**a vyberte **publikovat**.

      1. V **publikovat** kartu, vyberte možnost **publikovat**. Visual Studio zapíše soubory, které tvoří vaši aplikaci do místního systému souborů.

      1. **Publikovat** karta nyní zobrazuje jeden profil, **FolderProfile**. Nastavení profilu konfigurace jsou uvedeny v **Souhrn** části karty.

   Výsledné soubory jsou umístěny v adresáři s názvem `PublishOutput` , který je v podadresáři vašeho projektu *.\bin\release* podadresáře.

Proces publikování spolu se soubory vaší aplikace, generuje soubor databáze (PDB) programu, který obsahuje ladicí informace o vaší aplikaci. Soubor je užitečné hlavně pro ladění výjimky. Můžete není balíček se soubory vaší aplikace. Měli byste, však uložit ho v případě, že chcete ladit sestavení pro vydání aplikace.

Nasaďte kompletní sadu souborů aplikace žádným způsobem, který vám vyhovuje. Například lze zabalit jako soubor Zip, použít jednoduchý `copy` příkazu, nebo je nasadit v balíčcích instalace podle vašeho výběru. Po instalaci se uživatelům může pak spustit vaši aplikaci s použitím `dotnet` příkazu a poskytuje název souboru aplikace, jako například `dotnet fdd.dll`.

Kromě binární soubory aplikace Instalační program by měl také vytvoření balíčku Instalační služby sdílené architektuře nebo vyhledat jako předpoklad jako součást instalace aplikace.  Instalace rozhraní sdílené vyžaduje přístup správce/root, protože jde o celý počítač.

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>Nasazení závisí na architektuře s závislostí třetích stran

Nasazení závisí na architektuře se jeden nebo více závislostí třetích stran vyžaduje, aby všechny závislosti k dispozici pro váš projekt. Následující kroky jsou požadovány, než můžete vytvářet aplikace:

1. Použití **Správce balíčků NuGet** přidejte odkaz na balíček NuGet do projektu, a pokud balíček už není k dispozici ve vašem systému, nainstalujte ho. Chcete-li spustit nástroj Správce balíčku, vyberte **nástroje** > **Správce balíčků NuGet** > **spravovat balíčky NuGet pro řešení**.

1. Ujistěte se, že `Newtonsoft.Json` je nainstalovaný ve vašem systému a pokud není, nainstalujte ho. **Nainstalováno** karta obsahuje balíčky NuGet ve vašem systému nainstalována. Pokud `Newtonsoft.Json` není uvedená, vyberte **Procházet** kartu a do vyhledávacího pole zadejte "Newtonsoft.Json". Vyberte `Newtonsoft.Json` a v pravém podokně vyberte svůj projekt před výběrem **nainstalovat**.

1. Pokud `Newtonsoft.Json` je už nainstalovaný ve vašem systému, přidejte ho do projektu výběrem projektu v pravém podokně **spravovat balíčky pro řešení** kartu.

Všimněte si, že nasazení závisí na architektuře závislostí třetích stran je pouze jako přenosný jeho závislostí třetích stran. Například pokud knihovny třetí strany pouze podporuje macOS, aplikace není přenosný do systémů Windows. To se stane, když závislostí třetích stran, samotný závisí na nativní kód. Dobrým příkladem tohoto je [Kestrel server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), což vyžaduje nativní závislost na [libuv](https://github.com/libuv/libuv). Po vytvoření disketové jednotky pro aplikace s tímto druhem závislostí třetích stran publikovaný výstup obsahuje složku pro každý [identifikátor modulu Runtime (RID)](../rid-catalog.md) podporující nativní závislostí (a, která existuje v jeho balíček NuGet).

## <a name="simpleSelf"></a> Samostatná nasazení bez závislostí třetích stran

Samostatná nasazení bez závislostí třetích stran zahrnuje vytvoření projektu, úpravy *csproj* souboru, sestavování, testování a publikování aplikace. Jednoduchý příklad napsané v jazyce C# znázorňuje proces.

1. Vytvoření projektu.

   Vyberte **souboru** > **nové** > **projektu**. V **přidat nový projekt** dialogového okna, vyberte **.NET Core** v **nainstalováno** podokně typů projektů a vyberte **Konzolová aplikace (.NET Core)** šablon v prostředním podokně. Zadejte název projektu, jako je například "SCD" **název** textového pole a vyberte **OK** tlačítko.

1. Přidejte zdrojový kód aplikace.

   Otevřít *Program.cs* souboru ve svém editoru a automaticky vygenerovaném kódu nahraďte následujícím kódem. Se zobrazí výzva k zadání textu a zobrazuje jednotlivá slova zadané uživatelem. Používá regulární výraz `\w+` k oddělení slov ve vstupním textu.

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. Definování platformy, které se zaměří na vaši aplikaci.

   1. Klikněte pravým tlačítkem na projekt (nikoli řešení) **Průzkumníka řešení**a vyberte **upravit SCD.csproj**.

   1. Vytvoření `<RuntimeIdentifiers>` značku `<PropertyGroup>` část vaší *csproj* soubor, který definuje vaše aplikace cílí platformy a zadejte identifikátor modulu runtime (RID) pro každou platformu, která je cílem. Všimněte si, že budete také muset přidat středníkem k oddělení identifikátory RID. Zobrazit [katalog identifikátorů modulu Runtime](../rid-catalog.md) seznam identifikátorů modulů runtime.

   Následující příklad například označuje, že aplikace běží na 64bitová verze Windows 10 operačních systémů a operačním systému OS 10.11 verze X 64-bit.

```xml
<PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
</PropertyGroup>
```

   Všimněte si, že `<RuntimeIdentifiers>` element můžete přejít do libovolného `<PropertyGroup>` , kterou máte vaše *csproj* souboru. Úplnou ukázku *csproj* souboru se zobrazí později v této části.

1. Vytvořte sestavení pro ladění vaší aplikace.

   Vyberte **sestavení** > **sestavit řešení**. Můžete také kompilace a spuštění sestavení pro ladění vaší aplikace tak, že vyberete **ladění** > **spustit ladění**.

1. Publikování aplikace.

   Po ladit a testovat program, vytvoření souborů k nasazení s vaší aplikací pro každou platformu, zaměřuje.

   K publikování aplikace ze sady Visual Studio, postupujte takto:

      1. Změňte konfiguraci řešení z **ladění** k **vydání** na panelu nástrojů k sestavení a vydání (tzn. Ne a ladění) verze vaší aplikace.

      1. Klikněte pravým tlačítkem na projekt (nikoli řešení) v **Průzkumníka řešení** a vyberte **publikovat**.

      1. V **publikovat** kartu, vyberte možnost **publikovat**. Visual Studio zapíše soubory, které tvoří vaši aplikaci do místního systému souborů.

      1. **Publikovat** karta nyní zobrazuje jeden profil, **FolderProfile**. Nastavení profilu konfigurace jsou uvedeny v **Souhrn** části karty. **Cílové prostředí Runtime** identifikuje, které modul runtime byla publikována, a **cílové umístění** identifikuje, ve kterém byly vytvořeny soubory pro samostatné nasazení.

      1. Visual Studio ve výchozím nastavení zapíše že všechny publikované soubory do jednoho adresáře. Pro usnadnění práce je nejlepší vytvořit samostatné profily pro každý cílový modul runtime a zadávat publikované soubory v adresáři pro konkrétní platformu. To zahrnuje vytvoření samostatný profil publikování pro každou cílovou platformu. Takže teď znovu sestavte aplikaci pro každou platformu následujícím způsobem:

         1. Vyberte **vytvořit nový profil** v **publikovat** dialogového okna.

         1. V **vyberte cíl publikování** dialogové okno Změnit **zvolte složku** umístění *bin\Release\PublishOutput\win10 x64*. Vyberte **OK**.

         1. Vyberte nový profil (**FolderProfile1**) v seznamu profilů a ujistěte se, že **cílový modul Runtime** je `win10-x64`. Pokud tomu tak není, vyberte **nastavení**. V **nastavení profilu** dialogové okno Změnit **cílový modul Runtime** k `win10-x64` a vyberte **Uložit**. V opačném případě vyberte **zrušit**.

         1. Vyberte **publikovat** a publikujte svou aplikaci pro 64bitové platformy Windows 10.

         1. Postupujte podle předchozích kroků znovu vytvořit profil `osx.10.11-x64` platformy. **Cílové umístění** je *bin\Release\PublishOutput\osx.10.11-x64*a **cílový modul Runtime** je `osx.10.11-x64`. Název sady Visual Studio přiřadí k tomuto profilu je **FolderProfile2**.

      Všimněte si, že každý cílové umístění obsahuje kompletní sadu souborů (soubory aplikace a všechny soubory .NET Core) potřebné pro spuštění vaší aplikace.

Proces publikování spolu se soubory vaší aplikace, generuje soubor databáze (PDB) programu, který obsahuje ladicí informace o vaší aplikaci. Soubor je užitečné hlavně pro ladění výjimky. Můžete není balíček se soubory vaší aplikace. Měli byste, však uložit ho v případě, že chcete ladit sestavení pro vydání aplikace.

Nasaďte publikované soubory žádným způsobem, který vám vyhovuje. Například lze zabalit jako soubor Zip, použít jednoduchý `copy` příkazu, nebo je nasadit v balíčcích instalace podle vašeho výběru.

Tady je úplný *csproj* souboru pro tento projekt.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a>Samostatná nasazení s závislostí třetích stran

Samostatná nasazení s jeden nebo více závislostí třetích stran, zahrnuje přidání závislosti. Následující kroky jsou požadovány, než můžete vytvářet aplikace:

1. Použití **Správce balíčků NuGet** přidejte odkaz na balíček NuGet do projektu, a pokud balíček už není k dispozici ve vašem systému, nainstalujte ho. Chcete-li spustit nástroj Správce balíčku, vyberte **nástroje** > **Správce balíčků NuGet** > **spravovat balíčky NuGet pro řešení**.

1. Ujistěte se, že `Newtonsoft.Json` je nainstalovaný ve vašem systému a pokud není, nainstalujte ho. **Nainstalováno** karta obsahuje balíčky NuGet ve vašem systému nainstalována. Pokud `Newtonsoft.Json` není uvedená, vyberte **Procházet** kartu a do vyhledávacího pole zadejte "Newtonsoft.Json". Vyberte `Newtonsoft.Json` a v pravém podokně vyberte svůj projekt před výběrem **nainstalovat**.

1. Pokud `Newtonsoft.Json` je už nainstalovaný ve vašem systému, přidejte ho do projektu výběrem projektu v pravém podokně **spravovat balíčky pro řešení** kartu.

Tady je úplný *csproj* souboru pro tento projekt:

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

Při nasazení vaší aplikace jsou také obsažena případných závislostí třetích stran používají ve vaší aplikaci se soubory aplikace. V systému, na kterém běží aplikace nejsou vyžadovány knihovny třetích stran.

Všimněte si, že lze nasadit pouze samostatná nasazení pomocí knihovny třetí strany na platformách podporovaných aplikací tuto knihovnu. Toto je podobný s tím, že závislostí třetích stran s nativní závislosti ve vašem nasazení závisí na architektuře, kde neexistují nativní závislosti na cílové platformě, pokud byly dříve nainstalovány existuje.

## <a name="see-also"></a>Viz také:

* [Nasazení aplikace .NET core](index.md)
* [.NET core Runtime identifikátor (RID) katalogu](../rid-catalog.md)
