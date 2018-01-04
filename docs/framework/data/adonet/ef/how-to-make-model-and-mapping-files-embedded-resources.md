---
title: "Postupy: zpřístupnění modelu a soubory mapování vložené prostředky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6b8439e81c9a77f15556c21c5e96add86265c4ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a>Postupy: zpřístupnění modelu a soubory mapování vložené prostředky
[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Umožňuje nasadit model a mapování soubory jako vložené prostředky aplikace. Toto sestavení s vložený model a mapování soubory musí být ve stejné doméně aplikace jako připojení entity načíst. Další informace najdete v tématu [připojovací řetězce](../../../../../docs/framework/data/adonet/ef/connection-strings.md). Ve výchozím nastavení [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] nástroje pro vložení modelu a mapování souborů. Když definujete ručně modelu a mapování souborů, pomocí tohoto postupu zkontrolujte, že soubory jsou nasazeny jako vložené prostředky společně s [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikace.  
  
> [!NOTE]
>  Pokud chcete zachovat vložené prostředky, musíte tento postup zopakovat vždy, když jsou upraveny modelu a mapování souborů.  
  
### <a name="to-embed-model-and-mapping-files"></a>Chcete-li vložit soubory mapování a modelu  
  
1.  V **Průzkumníku**, vyberte soubor koncepční (.csdl).  
  
2.  V **vlastnosti** podokně nastavit **akce sestavení** k **vložený prostředek**.  
  
3.  Opakujte kroky 1 a 2 pro soubor úložiště (ssdl) a souboru mapování (.msl).  
  
4.  V **Průzkumníku řešení**, poklikejte na soubor App.config a potom upravte `Metadata` parametr ve `connectionString` atributů na základě jedné z následujících formátů:  
  
    -   `Metadata=``res://<assemblyFullName>/<resourceName>;`  
  
    -   `Metadata=``res://*/<resourceName>;`  
  
    -   `Metadata=res://*;`  
  
     Další informace najdete v tématu [připojovací řetězce](../../../../../docs/framework/data/adonet/ef/connection-strings.md).  
  
## <a name="example"></a>Příklad  
 Následující připojovací řetězec odkazuje vložený model a mapování souborů [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832). Tento připojovací řetězec uložený v souboru App.config projektu.  
  
  
  
## <a name="see-also"></a>Viz také  
 [Modelování a mapování](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [Postupy: Definování připojovacího řetězce](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)  
 [Postupy: Sestavení připojovacího řetězce EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
 [Nástroje modelu ADO.NET Entity Data Model](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)
