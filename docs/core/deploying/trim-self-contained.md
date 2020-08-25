---
title: Oříznout samostatně obsažené aplikace
description: Naučte se oříznout samostatné aplikace a zmenšit jejich velikost. .NET Core obsahuje modul runtime s aplikací, která je publikovaná samostatně a obecně zahrnuje více prostředí runtime, a je to nezbytné.
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: e3eb161b14f206723ad034af0a4a6ba8cd575578
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810609"
---
# <a name="trim-self-contained-deployments-and-executables"></a>Odebrání nechtěných součástí a zachování pouze samostatně nasaditelných součástí a spustitelných souborů

[Model nasazení závislý na rozhraní](index.md#publish-framework-dependent) byl nejaktivnějším modelem nasazení od okamžiku spuštění .NET. V tomto scénáři vývojář aplikace sady sestaví pouze aplikace a sestavení třetích stran s očekáváním, že v klientském počítači budou k dispozici knihovny .NET runtime a rozhraní. Tento model nasazení se v .NET Core i nadále považuje za dominantní, ale existují scénáře, kdy model závislý na rozhraní není optimální. Alternativou je publikování [samostatné aplikace](index.md#publish-self-contained), kde se modul runtime .NET Core a rozhraní seskupí spolu s aplikacemi a sestaveními třetích stran.

Model nasazení Trim – samostatně zahrnutý je specializovaná verze modelu nasazení, která je optimalizována pro snížení velikosti nasazení. Minimalizace velikosti nasazení je zásadním požadavkem pro některé scénáře na straně klienta, jako jsou Blazor aplikace. V závislosti na složitosti aplikace je pro spuštění aplikace nutná pouze podmnožina sestavení rozhraní. Tyto nepoužívané části knihovny jsou zbytečné a je možné je z zabalených aplikací oříznout. Nicméně existuje riziko, že analýza času sestavení aplikace může způsobit selhání za běhu, protože není schopná spolehlivě analyzovat různé problematické vzorce kódu (v podstatě na střed, na kterém je reflexe použito). Vzhledem k tomu, že spolehlivost nejde zaručit, tento model nasazení se nabízí jako funkce ve verzi Preview. Modul analýzy času sestavení poskytuje upozornění vývojářům vzorů kódu, které jsou problematické, a očekává se, že tyto vzory kódu budou opraveny. Pokud je to možné, doporučujeme, abyste přesunuli všechny závislosti na reflexi modulu runtime v aplikaci na čas sestavení pomocí kódu, který splňuje stejné požadavky.

Režim ořezávání pro aplikace lze konfigurovat prostřednictvím TrimMode a ve výchozím nastavení ( `copyused` ) pro sestavení sady prostředků, které se používají v aplikaci. Blazor aplikace WebAssembly budou používat účinnější režim ( `link` ), který ořízne nepoužitý kód v rámci sestavení. Upozornění analýzy střihu poskytují informace o vzorech kódu, u kterých není možné provést úplnou analýzu závislostí. Tato upozornění se ve výchozím nastavení potlačí a dají se zapnout nastavením příznaku `SuppressTrimAnalysisWarnings` na false. Další informace o dostupných možnostech ořezávání najdete na [stránce ILLinker](https://github.com/mono/linker/blob/master/docs/illink-options.md).

> [!NOTE]
> Ořezávání je experimentální funkce v rozhraní .NET Core 3,1, 5,0 a je dostupná _pouze_ pro aplikace, které jsou publikovány samostatně.

## <a name="prevent-assemblies-from-being-trimmed"></a>Zabránit oříznutí sestavení

Existují scénáře, ve kterých funkce ořezávání nedokáže detekovat odkazy. Například pokud se reflexe používá v sestavení modulu runtime, buď vaší aplikací, nebo knihovnou, na kterou odkazuje vaše aplikace, sestavení není přímo odkazováno. Ořezávání neví o těchto nepřímých odkazech a vyloučí knihovnu z publikované složky.

Pokud kód nepřímo odkazuje na sestavení prostřednictvím reflexe, můžete zabránit oříznutí sestavení s `<TrimmerRootAssembly>` nastavením. Následující příklad ukazuje, jak zabránit oříznutí sestavení nazývaného `System.Security` sestavení:

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="trim-your-app---cli"></a>Stříhání aplikace – CLI

Aplikaci ořízněte pomocí příkazu [dotnet Publish](../tools/dotnet-publish.md) . Při publikování aplikace nastavte následující vlastnosti:

- Publikovat jako samostatně uzavřenou aplikaci pro konkrétní modul runtime: `-r win-x64`
- Povolit oříznutí: `/p:PublishTrimmed=true`

Následující příklad publikuje aplikaci pro Windows jako samostatně obsaženou a ořízne výstup.

```xml
<PropertyGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

Následující příklad publikuje aplikaci v agresivním režimu střihu, kdy se nepoužívaný kód v sestaveních ořízne a jsou povolena upozornění ořezávání.

```xml
<PropertyGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <PublishTrimmed>true</PublishTrimmed>
    <TrimMode>link</TrimMode>
    <SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>
</PropertyGroup>
```

Další informace najdete v tématu [publikování aplikací .NET Core pomocí .NET Core CLI](deploy-with-cli.md).

## <a name="trim-your-app---visual-studio"></a>Střih aplikace – Visual Studio

Visual Studio vytvoří opakovaně použitelné publikační profily, které určují, jak je vaše aplikace publikovaná.

01. V podokně **Průzkumník řešení** klikněte pravým tlačítkem myši na projekt, který chcete publikovat. Vybrat **publikování...**.

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="Průzkumník řešení pomocí nabídky po kliknutí pravým tlačítkem myši zvýraznění možnosti Publikovat.":::

    Pokud ještě nemáte profil publikování, postupujte podle pokynů, abyste ho vytvořili, a vyberte cílový typ **složky** .

01. Klikněte na tlačítko **Upravit**.

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="Publikovat profil sady Visual Studio s tlačítkem Upravit":::

01. V dialogovém okně **nastavení profilu** nastavte následující možnosti:

    - Nastavte **režim nasazení** na **samostatné**.
    - Nastavte **cílový modul runtime** na platformu, do které chcete publikovat.
    - Vyberte **oříznout nepoužívaná sestavení (ve verzi Preview)**.

    Kliknutím na **Uložit** uložte nastavení a vraťte se do dialogového okna pro **publikování** .

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="Dialogové okno nastavení profilu s vybraným režimem nasazení, cílovým modulem runtime a oříznout nepoužité možnosti sestavení":::

01. Kliknutím na **publikovat** publikujte aplikaci oříznutou.

Další informace najdete v tématu [publikování aplikací .NET Core pomocí sady Visual Studio](deploy-with-vs.md).

## <a name="trim-your-app---visual-studio-for-mac"></a>Stříhání aplikace – Visual Studio pro Mac

Visual Studio pro Mac neposkytuje možnosti pro oříznutí vaší aplikace během publikování. Podle pokynů v oddílu [vystřihování rozhraní CLI aplikace](#trim-your-app---cli) budete muset publikovat ručně. Další informace najdete v tématu [publikování aplikací .NET Core pomocí .NET Core CLI](deploy-with-cli.md).

## <a name="see-also"></a>Viz také

- [Nasazení aplikace .NET Core](index.md)
- [Publikování aplikací .NET Core pomocí .NET Core CLI](deploy-with-cli.md).
- [Publikování aplikací .NET Core pomocí sady Visual Studio](deploy-with-vs.md)
- [dotnet Publish příkaz](../tools/dotnet-publish.md).
