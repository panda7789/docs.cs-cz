---
title: "Generátor EDM (EdmGen.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe8297a1-1fc3-48ce-8eeb-f70f63f857aa
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: da99c43d9142ee754b2b48db45ca070d1ab7c4e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="edm-generator-edmgenexe"></a>Generátor EDM (EdmGen.exe)
EdmGen.exe je nástroj příkazového řádku používané pro práci s [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] modelu a mapování souborů. Nástroj EdmGen.exe můžete provést následující akce:  
  
-   Připojení ke zdroji dat pomocí zprostředkovatele dat rozhraní .NET Framework specifické zdroje dat a ke generování konceptuálního modelu (.csdl), modelu úložiště (ssdl) a soubory mapování (.msl), které jsou používány [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Další informace najdete v tématu [postupy: použití EdmGen.exe pro generování modelu a mapování soubory](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
-   Ověřte existující model. Další informace najdete v tématu [postupy: použití EdmGen.exe ověření modelu a mapování soubory](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md).  
  
-   Vygenerujte C# nebo Visual Basic kód soubor, který obsahuje objekt třídy vygenerované ze souboru konceptuálního modelu (.csdl). Další informace najdete v tématu [postupy: použití EdmGen.exe ke generování kódu objektové vrstvě](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md).  
  
-   Generovat soubor kódu C# nebo Visual Basic, který obsahuje předem vygenerovaných zobrazení existujícího modelu. Další informace najdete [postupy: zobrazení Pre-Generate ke zlepšení výkonu dotazů](http://msdn.microsoft.com/en-us/b18a9d16-e10b-4043-ba91-b632f85a2579).  
  
 Nástroj EdmGen.exe se nainstaluje v [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] adresáře. V mnoha případech je umístěn v C:\windows\Microsoft.NET\Framework\v4.0. Pro 64bitové systémy je umístěný v C:\windows\Microsoft.NET\Framework64\v4.0. Můžete také využít nástroj EdmGen.exe z příkazového řádku Visual Studia (klikněte na tlačítko **spustit**, přejděte na příkaz **všechny programy**, přejděte na příkaz **Microsoft Visual Studio 2010**, přejděte na **Nástroje sady visual Studio**a potom klikněte na **příkazový řádek sady Visual Studio 2010**).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
EdmGen /mode:choice [options]  
```  
  
## <a name="mode"></a>Režim  
 Pokud používáte nástroj EdmGen.exe, musíte zadat jednu z následujících režimů.  
  
|Režim|Popis|  
|----------|-----------------|  
|`/mode:ValidateArtifacts`|Ověří soubory .csdl, .ssdl a .msl a zobrazí nějaké chyby nebo upozornění.<br /><br /> Tato možnost vyžaduje alespoň jeden z `/inssdl` nebo `/incsdl` argumenty. Pokud `/inmsl` je zadána, `/inssdl` a `/incsdl` argumenty jsou povinné.|  
|`/mode:FullGeneration`|Používá informace o připojení databáze zadaná v `/connectionstring` možnost a generuje .csdl, .ssdl, .msl, objekt vrstvy a zobrazit soubory.<br /><br /> Tato možnost vyžaduje `/connectionstring` argument a buď `/project` argument nebo `/outssdl`, `/outcsdl`, `/outmsdl`, `/outobjectlayer`, `/outviews`, `/namespace`, a `/entitycontainer` argumenty.|  
|`/mode:FromSSDLGeneration`|Generuje soubory .csdl a .msl, zdrojový kód a zobrazení ze souboru zadané ssdl.<br /><br /> Tato možnost vyžaduje `/inssdl` argument a buď `/project` argument nebo `/outcsdl`, `/outmsl`, `/outobjectlayer`, `/outviews`, `/namespace,` a `/entitycontainer` argumenty.|  
|`/mode:EntityClassGeneration`|Vytvoří soubor zdrojového kódu, který obsahuje třídy vygenerované ze souboru .csdl.<br /><br /> Tato možnost vyžaduje `/incsdl` argument a buď `/project` argument nebo `/outobjectlayer` argument. `/language` Argument je volitelný.|  
|`/mode:ViewGeneration`|Vytvoří soubor zdrojového kódu, který obsahuje zobrazení generují z .csdl, .ssdl a .msl soubory.<br /><br /> Tato možnost vyžaduje `/inssdl`, `/incsdl`, `/inmsl,` a buď `/project` nebo `/outviews` argumenty. `/language` Argument je volitelný.|  
  
## <a name="options"></a>Možnosti  
  
|Možnost|Popis|  
|------------|-----------------|  
|`/p[roject]:`\<řetězec >|Určuje název projektu se má použít. Název projektu se používá jako výchozí pro obor názvů, název modelu a mapování souborů, názvu souboru zdrojového objektu a název souboru zdroje generování zobrazení nastavení. Název kontejneru entit nastaven na \<Projekt > kontextu.|  
|`/prov[ider]:`\<řetězec >|Název [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat, který se má použít pro generování souboru modelu (ssdl) úložiště. Výchozí zprostředkovatel je [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Data Provider pro SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>).|  
|`/c[onnectionstring]:`\<připojovací řetězec >|Určuje řetězec, který se používá k připojení ke zdroji dat.|  
|`/incsdl:`\<Soubor >|Určuje .csdl soubor nebo adresář, kde jsou umístěny soubory .csdl. Tento argument může být zadána vícekrát, ve kterém můžete zadat několik adresářů a souborů .csdl. Zadání několik adresářů, může být užitečná pro generování tříd (`/mode:EntityClassGeneration`) a zobrazení (`/mode:ViewGeneration`) Pokud je konceptuální model rozdělit do několika souborů. To může být také užitečné, pokud chcete ověřit více modelů (`/mode:ValidateArtifacts`).|  
|`/refcsdl:`\<Soubor >|Určuje další .csdl soubor nebo soubory používané se vyřešit všechny odkazy na ve zdrojovém .csdl souboru. (Zdrojový soubor .csdl je soubor určený touto `/incsdl` možnost). `/refcsdl` Soubor obsahuje typy, které je závislá na zdrojový soubor .csdl. Tento argument může být zadána vícekrát.|  
|`/inmsl:`\<Soubor >|Určuje .msl soubor nebo adresář, kde jsou umístěny soubory .msl. Tento argument může být zadána vícekrát, ve kterém můžete zadat několik adresáře nebo .msl soubory. Určení několik adresářů, může být užitečná pro generování zobrazení (`/mode:ViewGeneration`) Pokud je konceptuální model rozdělit do několika souborů. To může být také užitečné, pokud chcete ověřit více modelů (`/mode:ValidateArtifacts`).|  
|`/inssdl:`\<Soubor >|Určuje .ssdl soubor nebo adresář, kde je umístěn soubor ssdl. Tento argument může být zadána vícekrát, ve kterém můžete zadat několik adresářů a souborů ssdl. To může být užitečné, pokud chcete ověřit více modelů `(/mode:ValidateArtifacts)`.|  
|`/outcsdl:`\<Soubor >|Určuje název souboru .csdl, který bude vytvořen.|  
|`/outmsl:`\<Soubor >|Určuje název souboru .msl, který bude vytvořen.|  
|`/outssdl:`\<Soubor >|Určuje název souboru ssdl, který bude vytvořen.|  
|`/outobjectlayer:`\<Soubor >|Určuje název souboru zdrojového kódu, který obsahuje objekty generované ze souboru .csdl.|  
|`/outviews:`\<Soubor >|Určuje název souboru zdrojového kódu, který obsahuje zobrazení, které byly vygenerovány.|  
|`/language:`[VB &#124; CSharp]|Určuje jazyk pro soubory generované zdrojového kódu. Výchozí hodnoty jazyka C#.|  
|`/namespace:`\<řetězec >|Určuje obor názvů modelu používat. Obor názvů je nastaveno v souboru .csdl, při spuštění `/mode:FullGeneration` nebo `/mode:FromSSDLGeneration`. Obor názvů se nepoužívá při spuštění `/mode:EntityClassGeneration`.|  
|`/entitycontainer:`\<řetězec >|Určuje název, který chcete použít `<EntityContainer>` element v souborech mapování a generovaný model.|  
|`/pl[uralize]`|Použije Anglická pravidla pro singulars a množné číslo na `Entity`, `EntitySet`, a `NavigationProperty` názvy v konceptuálním modelu. Tato možnost provede následující akce:<br /><br /> – Zkontrolujte všechny `EntityType` názvy singulární.<br />– Zkontrolujte všechny `EntitySet` názvy v množném čísle.<br />– Pro každou `NavigationProperty` , který vrací maximálně jedna entita, zkontrolujte název singulární.<br />– Pro každou `NavigationProperty` , který vrací více než jedna entita, zkontrolujte název množném čísle.|  
|`/SupressForeignKeyProperties or /nofk`|Zabraňuje vystavení jako skalární vlastnosti pro typy entity v konceptuálním modelu sloupce cizích klíčů.|  
|`/help`nebo`?`|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|`/nologo`|Potlačí zprávu o autorských právech ze zobrazení.|  
|`/targetversion:`\<řetězec >|Verze rozhraní .NET Framework, který se použije kompilace generovaného kódu. Podporované verze jsou 4 a 4.5. Výchozí hodnota je 4.|  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: použití EdmGen.exe pro generování modelu a soubory mapování](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)  
  
 [Postupy: použití EdmGen.exe ke generování kódu na objektové vrstvě](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)  
  
 [Postupy: použití EdmGen.exe pro ověření modelu a soubory mapování](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)  
  
## <a name="see-also"></a>Viz také  
 [Nástroje modelu ADO.NET Entity Data Model](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)  
 [Datového modelu entity](../../../../../docs/framework/data/adonet/entity-data-model.md)  
 [CSDL, SSDL a specifikace MSL](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
