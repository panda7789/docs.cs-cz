---
title: EDM Generator (EdmGen.exe)
ms.date: 03/30/2017
ms.assetid: fe8297a1-1fc3-48ce-8eeb-f70f63f857aa
ms.openlocfilehash: cd43b6ca31eea2cc4265c7f2e1a045f0f12a256c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722114"
---
# <a name="edm-generator-edmgenexe"></a>EDM Generator (EdmGen.exe)
EdmGen.exe je nástroj příkazového řádku pro práci s [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] modelování a mapování souborů. Nástroje EdmGen.exe můžete provádět následující akce:  
  
-   Připojení ke zdroji dat pomocí zprostředkovatele dat rozhraní .NET Framework specifické pro zdroj dat a generovat koncepčního modelu (.csdl), úložiště modelu (ssdl) a souborů mapování (.msl), které jsou používány [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Další informace najdete v tématu [jak: Použití EdmGen.exe pro generování modelu a souborů mapování](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
-   Ověřte existující model. Další informace najdete v tématu [jak: Použití EdmGen.exe pro ověření modelu a souborů mapování](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md).  
  
-   Generovat soubor jazyka C# nebo Visual Basic kódu, obsahuje objekt třídy vygenerované ze souboru koncepčního modelu (.csdl). Další informace najdete v tématu [jak: Použití EdmGen.exe pro generování kódu na objektové vrstvě](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md).  
  
-   Generovat soubor kódu jazyka C# nebo Visual Basic, který obsahuje předem vygenerovaných zobrazení pro existující model. Další informace najdete [jak: Předběžně generovat zobrazení pro zlepšení výkonu dotazů](https://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579).  
  
 Nástroj EdmGen.exe je nainstalován v [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] adresáře. V mnoha případech je umístěn v C:\windows\Microsoft.NET\Framework\v4.0. Pro 64bitové systémy je umístěn v C:\windows\Microsoft.NET\Framework64\v4.0. Nástroje EdmGen.exe dá dostat taky z příkazového řádku sady Visual Studio (klikněte na tlačítko **Start**, přejděte na **všechny programy**, přejděte na **sadu Microsoft Visual Studio 2010**, přejděte na **Visual Studio Tools**a potom klikněte na tlačítko **příkazový řádek sady Visual Studio 2010**).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
EdmGen /mode:choice [options]  
```  
  
## <a name="mode"></a>Režim  
 Při používání nástroje EdmGen.exe, musíte zadat jednu z následujících režimů.  
  
|Režim|Popis|  
|----------|-----------------|  
|`/mode:ValidateArtifacts`|Ověří soubory .csdl, .ssdl a .msl a zobrazí nějaké chyby nebo upozornění.<br /><br /> Tato možnost vyžaduje alespoň jeden z `/inssdl` nebo `/incsdl` argumenty. Pokud `/inmsl` není zadána, `/inssdl` a `/incsdl` argumenty jsou povinné.|  
|`/mode:FullGeneration`|Používá informace o připojení databáze podle `/connectionstring` možnost a generuje .csdl, .ssdl, .msl, objekt vrstvy a zobrazení souborů.<br /><br /> Tato možnost vyžaduje `/connectionstring` argument a buď `/project` argument nebo `/outssdl`, `/outcsdl`, `/outmsdl`, `/outobjectlayer`, `/outviews`, `/namespace`, a `/entitycontainer` argumenty.|  
|`/mode:FromSSDLGeneration`|Generuje soubory .csdl a .msl, zdrojový kód a zobrazení ze souboru zadaného ssdl.<br /><br /> Tato možnost vyžaduje `/inssdl` argument a buď `/project` argument nebo `/outcsdl`, `/outmsl`, `/outobjectlayer`, `/outviews`, `/namespace,` a `/entitycontainer` argumenty.|  
|`/mode:EntityClassGeneration`|Vytvoří soubor zdrojového kódu, který obsahuje prostor tříd vygenerovaných z soubor .csdl.<br /><br /> Tato možnost vyžaduje `/incsdl` argument a buď `/project` argument nebo `/outobjectlayer` argument. `/language` Argument je nepovinný.|  
|`/mode:ViewGeneration`|Vytvoří soubor zdrojového kódu, který obsahuje vzhled zobrazení vygenerovaných z .csdl, .ssdl a .msl soubory.<br /><br /> Tato možnost vyžaduje `/inssdl`, `/incsdl`, `/inmsl,` a buď `/project` nebo `/outviews` argumenty. `/language` Argument je nepovinný.|  
  
## <a name="options"></a>Možnosti  
  
|Možnost|Popis|  
|------------|-----------------|  
|`/p[roject]:`\<řetězec >|Určuje název projektu použít. Název projektu slouží jako výchozí pro obor názvů, název modelu a souborů mapování, název objektu zdrojového souboru a název souboru zdroje generování zobrazení nastavení. Název kontejneru entity je nastavený na \<Projekt > kontext.|  
|`/prov[ider]:`\<řetězec >|Název [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat, který se má použít ke generování souboru modelu (ssdl) úložiště. Výchozí zprostředkovatel je [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Data Provider pro SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>).|  
|`/c[onnectionstring]:`\<připojovací řetězec >|Určuje řetězec, který se používá k připojení ke zdroji dat.|  
|`/incsdl:`\<Soubor >|Určuje soubor .csdl nebo do adresáře, kde jsou uložené soubory .csdl. Tento argument lze zadat více než jednou, takže můžete zadat několik adresářů a souborů .csdl. Určení více adresářů, může být užitečné pro generování tříd (`/mode:EntityClassGeneration`) nebo zobrazení (`/mode:ViewGeneration`) Pokud je konceptuálního modelu rozdělit mezi několik souborů. To může být také užitečné, pokud chcete ověřit více modelů (`/mode:ValidateArtifacts`).|  
|`/refcsdl:`\<Soubor >|Určuje další .csdl soubor nebo soubory, které vyřešit všechny odkazy ve zdrojovém souboru .csdl. (Zdrojový soubor .csdl se soubor určený parametrem `/incsdl` možnost). `/refcsdl` Soubor obsahuje typy, které je závislý soubor .csdl zdroje. Tento argument můžete zadat více než jednou.|  
|`/inmsl:`\<Soubor >|Určuje .msl soubor nebo adresář, kde jsou uložené soubory .msl. Tento argument lze zadat více než jednou, takže můžete zadat několik adresářů nebo .msl souborů. Určení více adresářů, může být užitečné při generování zobrazení (`/mode:ViewGeneration`) Pokud je konceptuálního modelu rozdělit mezi několik souborů. To může být také užitečné, pokud chcete ověřit více modelů (`/mode:ValidateArtifacts`).|  
|`/inssdl:`\<Soubor >|Určuje soubor .ssdl nebo adresář, kde je umístěn soubor ssdl. Tento argument lze zadat více než jednou, takže můžete zadat několik adresářů a souborů ssdl. To může být užitečné, pokud chcete ověřit několik modelů `(/mode:ValidateArtifacts)`.|  
|`/outcsdl:`\<Soubor >|Určuje název, který se vytvoří soubor .csdl.|  
|`/outmsl:`\<Soubor >|Určuje název souboru .msl, která bude vytvořena.|  
|`/outssdl:`\<Soubor >|Určuje název souboru ssdl, který bude vytvořen.|  
|`/outobjectlayer:`\<Soubor >|Určuje název souboru se zdrojovým kódem, který obsahuje objekty nevygeneruje soubor .csdl.|  
|`/outviews:`\<Soubor >|Určuje název souboru se zdrojovým kódem, který obsahuje zobrazení, které byly vygenerovány.|  
|`/language:`[VB&#124;CSharp]|Určuje jazyk pro soubory generovaného zdrojového kódu. Výchozí nastavení jazyka C#.|  
|`/namespace:`\<řetězec >|Určuje obor názvů modelů použít. Obor názvů je nastavena v souboru .csdl při spuštění `/mode:FullGeneration` nebo `/mode:FromSSDLGeneration`. Obor názvů se nepoužívá při spuštění `/mode:EntityClassGeneration`.|  
|`/entitycontainer:`\<řetězec >|Určuje název, který chcete použít `<EntityContainer>` element v generované modelu a souborů mapování.|  
|`/pl[uralize]`|Použije pravidla angličtině singulars a množné číslo k `Entity`, `EntitySet`, a `NavigationProperty` názvy v konceptuálním modelu. Tato možnost provede následující akce:<br /><br /> – Nastavit všechny `EntityType` názvy singulární.<br />– Nastavit všechny `EntitySet` názvy v množném čísle.<br />– Pro každou `NavigationProperty` , která vrací maximálně jedna entita, ujistěte se, název singulární.<br />– Pro každou `NavigationProperty` , která vrací více než jednu entitu, zkontrolujte název v množném čísle.|  
|`/SupressForeignKeyProperties or /nofk`|Zabraňuje vystavení jako skalární vlastnosti na typy entit v konceptuálním modelu sloupce cizích klíčů.|  
|`/help` Nebo `?`|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|`/nologo`|Potlačí zprávu o autorských právech ze zobrazení.|  
|`/targetversion:` \<řetězec >|Verze rozhraní .NET Framework, který se použije pro kompilaci vygenerovaného kódu. Podporovány jsou verze 4 a 4.5. Výchozí hodnota je 4.|  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Použití EdmGen.exe pro generování modelu a souborů mapování](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)  
  
 [Postupy: Použití EdmGen.exe pro generování kódu na objektové vrstvě](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)  
  
 [Postupy: Použití EdmGen.exe pro ověření modelu a souborů mapování](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)  
  
## <a name="see-also"></a>Viz také:
- [Datový Model Entity ADO.NET nástroje](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
- [Model EDM (Entity Data Model)](../../../../../docs/framework/data/adonet/entity-data-model.md)
- [Specifikace CSDL, SSDL a MSL](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
