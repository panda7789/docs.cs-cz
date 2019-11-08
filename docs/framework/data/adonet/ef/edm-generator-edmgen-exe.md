---
title: EDM Generator (EdmGen.exe)
ms.date: 03/30/2017
ms.assetid: fe8297a1-1fc3-48ce-8eeb-f70f63f857aa
ms.openlocfilehash: 858525a81e7779e7631ee8ac959110ba946cf652
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738529"
---
# <a name="edm-generator-edmgenexe"></a>EDM Generator (EdmGen.exe)

EdmGen. exe je nástroj příkazového řádku, který se používá pro práci s modelem Entity Framework a mapováním souborů. Pomocí nástroje EdmGen. exe můžete provést následující akce:

- Připojte se ke zdroji dat pomocí zdroje dat .NET Framework konkrétního poskytovatele dat a vygenerujte soubory koncepčního modelu (. CSDL), modelu úložiště (. ssdl) a mapování (. MSL), které jsou používány Entity Framework. Další informace naleznete v tématu [How to: use EdmGen. exe ke generování modelu a mapování souborů](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).

- Ověří existující model. Další informace naleznete v tématu [How to: use EdmGen. exe pro ověření modelu a mapování souborů](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md).

- Vygeneruje C# soubor kódu nebo Visual Basic, který obsahuje třídy objektů vygenerované ze souboru koncepčního modelu (. CSDL). Další informace naleznete v tématu [How to: use EdmGen. exe pro generování kódu objektové vrstvy](how-to-use-edmgen-exe-to-generate-object-layer-code.md).

- Vygeneruje C# soubor kódu nebo Visual Basic, který obsahuje předem vygenerovaná zobrazení pro existující model. Další informace najdete v tématu [Postup: předběžné generování zobrazení pro zlepšení výkonu dotazů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100)).

Nástroj EdmGen. exe je nainstalován v adresáři .NET Framework. V mnoha případech se nachází v C:\windows\Microsoft.NET\Framework\v4.0. Pro 64 systémy se nachází v C:\windows\Microsoft.NET\Framework64\v4.0. K nástroji EdmGen. exe můžete také přistupovat z příkazového řádku sady Visual Studio (klikněte na tlačítko **Start**, přejděte na příkaz **všechny programy**, přejděte na **Microsoft Visual Studio 2010**, přejděte na **Visual Studio Tools**a pak klikněte na **Visual Studio 2010 Příkazový řádek**).

## <a name="syntax"></a>Syntaxe

```console
EdmGen /mode:choice [options]
```

## <a name="mode"></a>Režim

Při použití nástroje EdmGen. exe je nutné zadat jeden z následujících režimů.

|Režim|Popis|
|----------|-----------------|
|`/mode:ValidateArtifacts`|Ověří soubory. csdl,. ssdl a. MSL a zobrazí všechny chyby nebo upozornění.<br /><br /> Tato možnost vyžaduje alespoň jeden z argumentů `/inssdl` nebo `/incsdl`. Je-li zadán parametr `/inmsl`, jsou také požadovány argumenty `/inssdl` a `/incsdl`.|
|`/mode:FullGeneration`|Používá informace o připojení databáze zadané v možnosti `/connectionstring` a generuje soubory. csdl,. ssdl,. MSL, objektové vrstvy a zobrazení souborů.<br /><br /> Tato možnost vyžaduje `/connectionstring` argument a buď argument `/project` nebo `/outssdl`, `/outcsdl`, `/outmsdl`, `/outobjectlayer`, `/outviews`, `/namespace`a `/entitycontainer` argumenty.|
|`/mode:FromSSDLGeneration`|Generuje soubory. csdl a. MSL, zdrojový kód a zobrazení ze zadaného souboru. ssdl.<br /><br /> Tato možnost vyžaduje `/inssdl` argument a buď argument `/project`, nebo argumenty `/outcsdl`, `/outmsl`, `/outobjectlayer`, `/outviews`, `/namespace,` a `/entitycontainer`.|
|`/mode:EntityClassGeneration`|Vytvoří soubor zdrojového kódu, který obsahuje třídy vygenerované ze souboru. csdl.<br /><br /> Tato možnost vyžaduje argument `/incsdl` a buď argument `/project`, nebo argument `/outobjectlayer`. Argument `/language` je nepovinný.|
|`/mode:ViewGeneration`|Vytvoří soubor zdrojového kódu, který obsahuje zobrazení generovaná ze souborů. csdl,. ssdl a. MSL.<br /><br /> Tato možnost vyžaduje `/inssdl`, `/incsdl`, `/inmsl,` a buď argumenty `/project` nebo `/outviews`. Argument `/language` je nepovinný.|

## <a name="options"></a>Možnosti

|Možnost|Popis|
|------------|-----------------|
|řetězec \<`/p[roject]:`|Určuje název projektu, který se má použít. Název projektu je použit jako výchozí pro nastavení oboru názvů, název modelu a mapování souborů, název zdrojového souboru objektu a název zdrojového souboru generování zobrazení. Název kontejneru entit je nastaven na \<>m kontextu projektu.|
|řetězec \<`/prov[ider]:`|Název poskytovatele dat .NET Framework, který se má použít k vygenerování souboru modelu úložiště (. ssdl). Výchozím poskytovatelem je .NET Framework Zprostředkovatel dat pro SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>).|
|připojovací řetězec \<`/c[onnectionstring]:`|Určuje řetězec, který se používá pro připojení ke zdroji dat.|
|soubor\<`/incsdl:`|Určuje soubor. csdl nebo adresář, kde jsou umístěny soubory. csdl. Tento argument lze zadat vícekrát, aby bylo možné zadat několik adresářů nebo souborů. csdl. Určení více adresářů může být užitečné pro vygenerování tříd (`/mode:EntityClassGeneration`) nebo zobrazení (`/mode:ViewGeneration`), když je koncepční model rozdělen mezi několik souborů. To může být užitečné také v případě, že chcete ověřit více modelů (`/mode:ValidateArtifacts`).|
|soubor\<`/refcsdl:`|Určuje další soubor. csdl nebo soubory, které se používají k překladu všech odkazů ve zdrojovém souboru. csdl. (Zdrojový soubor. csdl je soubor určený možností `/incsdl`). Soubor `/refcsdl` obsahuje typy, na kterých je zdrojový soubor. csdl závislý. Tento argument lze zadat vícekrát.|
|soubor\<`/inmsl:`|Určuje soubor. MSL nebo adresář, kde jsou umístěny soubory. MSL. Tento argument lze zadat vícekrát, aby bylo možné zadat několik adresářů nebo souborů. MSL. Určení více adresářů může být užitečné pro generování zobrazení (`/mode:ViewGeneration`), když je koncepční model rozdělen mezi několik souborů. To může být užitečné také v případě, že chcete ověřit více modelů (`/mode:ValidateArtifacts`).|
|soubor\<`/inssdl:`|Určuje soubor. ssdl nebo adresář, kde se nachází soubor. ssdl. Tento argument lze zadat vícekrát, abyste mohli zadat několik adresářů nebo souborů. ssdl. To může být užitečné, když chcete ověřit více modelů `(/mode:ValidateArtifacts)`.|
|soubor\<`/outcsdl:`|Určuje název souboru. csdl, který se vytvoří.|
|soubor\<`/outmsl:`|Určuje název souboru. MSL, který se vytvoří.|
|soubor\<`/outssdl:`|Určuje název souboru. ssdl, který se vytvoří.|
|soubor\<`/outobjectlayer:`|Určuje název souboru se zdrojovým kódem, který obsahuje objekty generované ze souboru. csdl.|
|soubor\<`/outviews:`|Určuje název souboru se zdrojovým kódem obsahujícího zobrazení, která byla vygenerována.|
|`/language:`[VB&#124;CSharp]|Určuje jazyk pro vygenerované soubory zdrojového kódu. Výchozí jazyk je C#.|
|řetězec\<`/namespace:`|Určuje obor názvů modelu, který se má použít. Obor názvů je nastaven v souboru. csdl při spuštění `/mode:FullGeneration` nebo `/mode:FromSSDLGeneration`. Obor názvů se nepoužívá při spuštění `/mode:EntityClassGeneration`.|
|řetězec\<`/entitycontainer:`|Určuje název, který se má použít pro `<EntityContainer>` element ve vygenerovaném modelu a mapování souborů.|
|`/pl[uralize]`|Aplikuje pravidla anglické abecedy pro čísla v číslech a v množném číslech na `Entity`, `EntitySet`a `NavigationProperty` názvy v koncepčním modelu. Tato možnost provede následující akce:<br /><br /> -Nastavit všechny názvy `EntityType` jednotném.<br />– Zajistěte, aby všechny názvy `EntitySet` plural.<br />– Pro každý `NavigationProperty`, který vrací maximálně jednu entitu, vytvořte název v jednotném čísle.<br />– Pro každý `NavigationProperty`, který vrací více než jednu entitu, udělejte název plural.|
|`/SuppressForeignKeyProperties or /nofk`|Zabraňuje zveřejnění sloupce cizího klíče jako skalárních vlastností u typů entit v koncepčním modelu.|
|`/help` nebo `?`|Zobrazí syntaxi příkazu a možnosti nástroje.|
|`/nologo`|Potlačí zobrazení zprávy o autorských právech.|
|řetězec \<`/targetversion:` >|Verze .NET Framework, která bude použita ke kompilaci generovaného kódu. Podporované verze jsou 4 a 4,5. Výchozí hodnota je 4.|

## <a name="in-this-section"></a>V tomto oddílu

[Postupy: Použití EdmGen.exe pro generování modelu a souborů mapování](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)

[Postupy: Použití EdmGen.exe pro generování kódu na objektové vrstvě](how-to-use-edmgen-exe-to-generate-object-layer-code.md)

[Postupy: Použití EdmGen.exe pro ověření modelu a souborů mapování](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)

## <a name="see-also"></a>Viz také:

- [ADO.NET model EDM (Entity Data Model) nástroje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Model EDM (Entity Data Model)](../entity-data-model.md)
- [Specifikace CSDL, SSDL a MSL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
