---
title: 'Postupy: použití EdmGen.exe pro ověření modelu a souborů mapování'
ms.date: 03/30/2017
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
ms.openlocfilehash: fda8698381e98c64318f1a26f77f0263e9085074
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512442"
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a>Postupy: použití EdmGen.exe pro ověření modelu a souborů mapování
Toto téma ukazuje, jak používat [generátor EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) nástroje pro ověření modelu a souborů mapování. Další informace najdete v tématu [modelu Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md).  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a>Ověření modelu School pomocí EdmGen.exe  
  
1.  Vytvoření databáze školy. Další informace najdete v tématu [vytvoření ukázkové databáze školy](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  Generování modelu školy. Další informace najdete v tématu [postupy: použití EdmGen.exe pro generování modelu a souborů mapování](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3.  Na příkazovém řádku spusťte následující příkaz bez konce řádků:  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Postupy: ruční konfigurace projektu v Entity Framework](https://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [Datový Model Entity ADO.NET nástroje](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)  
 [Postupy: předběžně generovat zobrazení pro zlepšení výkonu dotazů](https://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [Postupy: Použití EdmGen.exe pro generování kódu na objektové vrstvě](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)
