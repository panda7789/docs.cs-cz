---
title: EDM Generator (EdmGen.exe)
ms.date: 03/30/2017
ms.assetid: fe8297a1-1fc3-48ce-8eeb-f70f63f857aa
ms.openlocfilehash: 82166782e25cb7a7ea23fe7faf7a30cb0e68d631
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854718"
---
# <a name="edm-generator-edmgenexe"></a>EDM Generator (EdmGen.exe)

EdmGen. exe je nástroj příkazového řádku, který se používá pro práci s modelem Entity Framework a mapováním souborů. Pomocí nástroje EdmGen. exe můžete provést následující akce:

- Připojte se ke zdroji dat pomocí zdroje dat .NET Framework konkrétního poskytovatele dat a vygenerujte soubory koncepčního modelu (. CSDL), modelu úložiště (. ssdl) a mapování (. MSL), které jsou používány Entity Framework. Další informace najdete v tématu [jak: K vygenerování modelu a mapování souborů](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)použijte EdmGen. exe.

- Ověří existující model. Další informace najdete v tématu [jak: K ověření modelu a souborů](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)mapování použijte EdmGen. exe.

- Vygeneruje C# soubor kódu nebo Visual Basic, který obsahuje třídy objektů vygenerované ze souboru koncepčního modelu (. CSDL). Další informace najdete v tématu [jak: Pomocí EdmGen. exe vygenerujte kód](how-to-use-edmgen-exe-to-generate-object-layer-code.md)objektové vrstvy.

- Vygeneruje C# soubor kódu nebo Visual Basic, který obsahuje předem vygenerovaná zobrazení pro existující model. Další informace najdete v [tématu: Předem vygenerujte zobrazení pro zlepšení výkonu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))dotazů.

Nástroj EdmGen. exe je nainstalován v adresáři .NET Framework. V mnoha případech se nachází v C:\windows\Microsoft.NET\Framework\v4.0. Pro 64 systémy se nachází v C:\windows\Microsoft.NET\Framework64\v4.0. K nástroji EdmGen. exe můžete také přistupovat z příkazového řádku sady Visual Studio (klikněte na tlačítko **Start**, přejděte na příkaz **všechny programy**, přejděte na **Microsoft Visual Studio 2010**, přejděte na **Visual Studio Tools**a pak klikněte na **Visual Studio 2010 Příkazový řádek**).

## <a name="syntax"></a>Syntaxe

```
EdmGen /mode:choice [options]
```

## <a name="mode"></a>Režim

Při použití nástroje EdmGen. exe je nutné zadat jeden z následujících režimů.

|Režim|Popis|
|----------|-----------------|
|`/mode:ValidateArtifacts`|Ověří soubory. csdl,. ssdl a. MSL a zobrazí všechny chyby nebo upozornění.<br /><br /> Tato možnost vyžaduje aspoň jeden z `/inssdl` argumentů nebo. `/incsdl` Je `/inmsl` -liparametrzadán`/incsdl` , jsou vyžadovány i argumenty a.`/inssdl`|
|`/mode:FullGeneration`|Používá informace o připojení databáze zadané v `/connectionstring` možnosti a generuje soubory. csdl,. ssdl,. MSL, objektové vrstvy a zobrazení souborů.<br /><br /> Tato možnost `/connectionstring` vyžaduje argument a `/outssdl` `/project` argumenty, `/outcsdl` ,,`/outmsdl`,,, a`/entitycontainer` . `/outviews` `/outobjectlayer` `/namespace`|
|`/mode:FromSSDLGeneration`|Generuje soubory. csdl a. MSL, zdrojový kód a zobrazení ze zadaného souboru. ssdl.<br /><br /> Tato možnost `/inssdl` vyžaduje argument a `/project` buď `/outcsdl` `/outmsl`argument, neboargumenty`/namespace,` ,`/entitycontainer` ,, a. `/outobjectlayer` `/outviews`|
|`/mode:EntityClassGeneration`|Vytvoří soubor zdrojového kódu, který obsahuje třídy vygenerované ze souboru. csdl.<br /><br /> Tato možnost vyžaduje `/incsdl` argument a `/project` buď argument, nebo `/outobjectlayer` argument. `/language` Argument je nepovinný.|
|`/mode:ViewGeneration`|Vytvoří soubor zdrojového kódu, který obsahuje zobrazení generovaná ze souborů. csdl,. ssdl a. MSL.<br /><br /> Tato `/inssdl`možnost vyžaduje `/inmsl,` argumenty nebo .`/outviews` `/incsdl` `/project` `/language` Argument je nepovinný.|

## <a name="options"></a>Možnosti

|Možnost|Popis|
|------------|-----------------|
|`/p[roject]:`\<> řetězců|Určuje název projektu, který se má použít. Název projektu je použit jako výchozí pro nastavení oboru názvů, název modelu a mapování souborů, název zdrojového souboru objektu a název zdrojového souboru generování zobrazení. Název kontejneru entity je nastaven na \<> kontext projektu.|
|`/prov[ider]:`\<> řetězců|Název poskytovatele dat .NET Framework, který se má použít k vygenerování souboru modelu úložiště (. ssdl). Výchozím poskytovatelem je .NET Framework Zprostředkovatel dat pro SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>).|
|`/c[onnectionstring]:`\<> připojovacího řetězce|Určuje řetězec, který se používá pro připojení ke zdroji dat.|
|`/incsdl:`\<> souboru|Určuje soubor. csdl nebo adresář, kde jsou umístěny soubory. csdl. Tento argument lze zadat vícekrát, aby bylo možné zadat několik adresářů nebo souborů. csdl. Určení více adresářů může být užitečné pro vygenerování tříd`/mode:EntityClassGeneration`() nebo zobrazení`/mode:ViewGeneration`(), pokud je koncepční model rozdělen mezi několik souborů. To může být užitečné také v případě, že chcete ověřit více modelů`/mode:ValidateArtifacts`().|
|`/refcsdl:`\<> souboru|Určuje další soubor. csdl nebo soubory, které se používají k překladu všech odkazů ve zdrojovém souboru. csdl. (Zdrojový soubor. csdl je, soubor určený `/incsdl` možností). `/refcsdl` Soubor obsahuje typy, na kterých je zdrojový soubor. csdl závislý. Tento argument lze zadat vícekrát.|
|`/inmsl:`\<> souboru|Určuje soubor. MSL nebo adresář, kde jsou umístěny soubory. MSL. Tento argument lze zadat vícekrát, aby bylo možné zadat několik adresářů nebo souborů. MSL. Určení více adresářů může být užitečné při generování zobrazení (`/mode:ViewGeneration`), když je koncepční model rozdělen mezi několik souborů. To může být užitečné také v případě, že chcete ověřit více modelů`/mode:ValidateArtifacts`().|
|`/inssdl:`\<> souboru|Určuje soubor. ssdl nebo adresář, kde se nachází soubor. ssdl. Tento argument lze zadat vícekrát, abyste mohli zadat několik adresářů nebo souborů. ssdl. To může být užitečné, když chcete ověřit více modelů `(/mode:ValidateArtifacts)`.|
|`/outcsdl:`\<> souboru|Určuje název souboru. csdl, který se vytvoří.|
|`/outmsl:`\<> souboru|Určuje název souboru. MSL, který se vytvoří.|
|`/outssdl:`\<> souboru|Určuje název souboru. ssdl, který se vytvoří.|
|`/outobjectlayer:`\<> souboru|Určuje název souboru se zdrojovým kódem, který obsahuje objekty generované ze souboru. csdl.|
|`/outviews:`\<> souboru|Určuje název souboru se zdrojovým kódem obsahujícího zobrazení, která byla vygenerována.|
|`/language:`[VB&#124;CSharp]|Určuje jazyk pro vygenerované soubory zdrojového kódu. Výchozí jazyk je C#.|
|`/namespace:`\<> řetězců|Určuje obor názvů modelu, který se má použít. Obor názvů je nastaven v souboru. csdl při spuštění `/mode:FullGeneration` nebo. `/mode:FromSSDLGeneration` Obor názvů se nepoužívá, pokud `/mode:EntityClassGeneration`je spuštěný.|
|`/entitycontainer:`\<> řetězců|Určuje název, který se má použít `<EntityContainer>` pro element ve vygenerovaném modelu a mapování souborů.|
|`/pl[uralize]`|Aplikuje pravidla anglické jazykové verze pro čísla v číslech a `Entity`v `EntitySet`konceptuálním `NavigationProperty` modelu na čísla, a. Tato možnost provede následující akce:<br /><br /> – Zajistěte, aby všechny `EntityType` názvy byly jednotné.<br />– Zajistěte, aby všechny `EntitySet` názvy byly plural.<br />– Pro každý `NavigationProperty` , který vrací jenom jednu entitu, udělejte název na jednotném místě.<br />– Pro každý `NavigationProperty` , který vrací více než jednu entitu, udělejte název plural.|
|`/SuppressForeignKeyProperties or /nofk`|Zabraňuje zveřejnění sloupce cizího klíče jako skalárních vlastností u typů entit v koncepčním modelu.|
|`/help` Nebo `?`|Zobrazí syntaxi příkazu a možnosti nástroje.|
|`/nologo`|Potlačí zobrazení zprávy o autorských právech.|
|`/targetversion:`\<> řetězců|Verze .NET Framework, která bude použita ke kompilaci generovaného kódu. Podporované verze jsou 4 a 4,5. Výchozí hodnota je 4.|

## <a name="in-this-section"></a>V tomto oddílu

[Postupy: Použití EdmGen. exe ke generování modelu a souborů mapování](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)

[Postupy: Použití EdmGen. exe pro generování kódu objektové vrstvy](how-to-use-edmgen-exe-to-generate-object-layer-code.md)

[Postupy: Použití EdmGen. exe k ověření modelu a souborů mapování](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)

## <a name="see-also"></a>Viz také:

- [ADO.NET model EDM (Entity Data Model) nástroje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Model EDM (Entity Data Model)](../entity-data-model.md)
- [Specifikace CSDL, SSDL a MSL](./language-reference/csdl-ssdl-and-msl-specifications.md)
