---
title: 'Postupy: zpřístupnění modelu a souborů mapování vložené prostředky'
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: 35507f92d0ba9f434156773c8dc5621ed3c423c0
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864278"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a>Postupy: zpřístupnění modelu a souborů mapování vložené prostředky
[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Umožňuje nasadit modelu a souborů mapování jako vložené prostředky aplikace. Sestavení s vloženým modelem a souborů mapování musí být ve stejné doméně aplikace jako připojení entity načíst. Další informace najdete v tématu [připojovací řetězce](../../../../../docs/framework/data/adonet/ef/connection-strings.md). Ve výchozím nastavení [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] nástroje vložení modelu a souborů mapování. Když definujete modelu a souborů mapování ručně, pomocí tohoto postupu můžete zajistit, že jsou soubory nasazeny jako vložené prostředky spolu s [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikace.  
  
> [!NOTE]
>  Pokud chcete zachovat vložené prostředky, musíte tento postup zopakovat vždy, když se mění modelu a souborů mapování.  
  
### <a name="to-embed-model-and-mapping-files"></a>Chcete-li vložit modelu a souborů mapování  
  
1.  V **Průzkumníka řešení**, vyberte soubor koncepční (.csdl).  
  
2.  V **vlastnosti** podokně nastavte **akce sestavení** k **integrovaný prostředek**.  
  
3.  Opakujte kroky 1 a 2 pro soubor úložiště (ssdl) a soubor mapování (.msl).  
  
4.  V **Průzkumníka řešení**, poklikejte na soubor App.config a potom změňte `Metadata` parametr `connectionString` atributů na základě jedné z následujících formátů:  
  
    -   `Metadata=``res://<assemblyFullName>/<resourceName>;`  
  
    -   `Metadata=``res://*/<resourceName>;`  
  
    -   `Metadata=res://*;`  
  
     Další informace najdete v tématu [připojovací řetězce](../../../../../docs/framework/data/adonet/ef/connection-strings.md).  
  
## <a name="example"></a>Příklad  
 Vložený modelu a souborů mapování pro odkazuje na následující připojovací řetězec [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832). Tento připojovací řetězec je uložen v souboru App.config projektu.  
  
  
  
## <a name="see-also"></a>Viz také  
 [Modelování a mapování](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [Postupy: Definování připojovacího řetězce](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)  
 [Postupy: Sestavení připojovacího řetězce EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
 [Datový Model Entity ADO.NET nástroje](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
