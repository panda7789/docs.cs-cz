---
title: 'Postupy: použití EdmGen.exe pro generování modelu a souborů mapování'
ms.date: 03/30/2017
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
ms.openlocfilehash: 8eb7e0c19d775e516765b0e88f61789a9136e6e1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530070"
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>Postupy: použití EdmGen.exe pro generování modelu a souborů mapování
Toto téma ukazuje, jak používat nástroj Generátor EDM (EdmGen.exe) můžete vygenerovat následující soubory podle databáze školy:  
  
-   Koncepční model (soubor .csdl).  
  
-   Model úložiště (souboru ssdl).  
  
-   Mapování mezi modely koncepční a úložiště (soubor .msl).  
  
-   Objektové vrstvě kód v jazyce Visual Basic nebo C#.  
  
-   Zobrazit soubory.  
  
 Nástroje EdmGen.exe /mode:FullGeneration používá ke generování souborů uvedených výše. Další informace o příkazech EdmGen.exe najdete v tématu [generátor EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).  
  
 Pokud použití EdmGen.exe pro generování modelu a souborů mapování, je stále potřeba konfigurace projektu Visual Studio pro použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Další informace najdete v tématu [postupy: ruční konfigurace projektu v Entity Framework](https://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).  
  
> [!NOTE]
>  Koncepční model generovaných EdmGen.exe zahrnuje všechny objekty v databázi. Pokud chcete generovat Koncepční model, který obsahuje pouze konkrétní objekty, použijte Průvodce datovým modelem Entity. Další informace najdete v tématu [postupy: použití Průvodce datovým modelem Entity](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Generování modelu školní pro projekt jazyka Visual Basic pomocí EdmGen.exe  
  
1.  Vytvoření databáze školy. Další informace najdete v tématu [vytvoření ukázkové databáze školy](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  Na příkazovém řádku spusťte následující příkaz bez konce řádků:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>Generování modelu School pomocí EdmGen.exe projektu C#  
  
1.  Vytvoření databáze školy. Další informace najdete v tématu [vytvoření ukázkové databáze školy](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  Na příkazovém řádku spusťte následující příkaz bez konce řádků:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Modelování a mapování](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [Postupy: ruční konfigurace projektu v Entity Framework](https://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [Postupy: předběžně generovat zobrazení pro zlepšení výkonu dotazů](https://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [Datový Model Entity ADO.NET nástroje](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)  
 [Postupy: Použití EdmGen.exe pro ověření modelu a souborů mapování](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)
