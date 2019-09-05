---
title: 'Postupy: Vytvoření vložených prostředků modelu a souborů mapování'
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: c88e0c09742d76c7508d7d782eabbe46035d3501
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251447"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a>Postupy: Vytvoření vložených prostředků modelu a souborů mapování
[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Umožňuje nasadit model a mapování souborů jako vložené prostředky aplikace. Sestavení s vloženým modelem a soubory mapování musí být načteny ve stejné doméně aplikace jako připojení k entitě. Další informace najdete v tématu [připojovací řetězce](connection-strings.md). Ve výchozím nastavení nástroje model EDM (Entity Data Model) vkládají model a mapování souborů. Při ručním definování modelu a mapování souborů použijte tento postup, chcete-li zajistit, aby byly soubory nasazeny jako integrované prostředky spolu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] s aplikací.  
  
> [!NOTE]
> Chcete-li zachovat vložené prostředky, je nutné tento postup opakovat vždy, když dojde ke změně modelu a souborů mapování.  
  
### <a name="to-embed-model-and-mapping-files"></a>Vložení modelu a souborů mapování  
  
1. V **Průzkumník řešení**vyberte koncepční soubor (. CSDL).  
  
2. V podokně **vlastnosti** nastavte **akci sestavení** na **Integrovaný prostředek**.  
  
3. Opakujte kroky 1 a 2 pro soubor úložiště (. ssdl) a soubor mapování (. MSL).  
  
4. V **Průzkumník řešení**dvakrát klikněte na soubor App. config a pak změňte `Metadata` parametr v `connectionString` atributu na základě jednoho z následujících formátů:  
  
    - `Metadata=``res://<assemblyFullName>/<resourceName>;`  
  
    - `Metadata=``res://*/<resourceName>;`  
  
    - `Metadata=res://*;`  
  
     Další informace najdete v tématu [připojovací řetězce](connection-strings.md).  
  
## <a name="example"></a>Příklad  
 Následující připojovací řetězec odkazuje na vložený model a soubory mapování pro [model prodeje AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). Tento připojovací řetězec je uložený v souboru App. config projektu.  

## <a name="see-also"></a>Viz také:

- [Modelování a mapování](modeling-and-mapping.md)
- [Postupy: Definování připojovacího řetězce](how-to-define-the-connection-string.md)
- [Postupy: Vytvoření připojovacího řetězce EntityConnection](how-to-build-an-entityconnection-connection-string.md)
- [ADO.NET model EDM (Entity Data Model) nástroje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
