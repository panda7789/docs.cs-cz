---
title: "Postupy: použití EdmGen.exe pro generování modelu a soubory mapování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ebff53126b808f679855b43fd8e1d2461b516e66
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>Postupy: použití EdmGen.exe pro generování modelu a soubory mapování
Toto téma ukazuje, jak pomocí nástroje Generátor EDM (EdmGen.exe) ke generování založena na databázi školní následující soubory:  
  
-   Koncepční model (soubor .csdl).  
  
-   Model úložiště (ssdl soubor).  
  
-   Mapování mezi modely koncepční a úložiště (soubor .msl).  
  
-   Objektové vrstvě kód v jazyce Visual Basic nebo C#.  
  
-   Zobrazit soubory.  
  
 Nástroj EdmGen.exe /mode:FullGeneration používá ke generování souborů uvedených výše. Další informace o příkazech EdmGen.exe najdete v tématu [EDM generátor (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).  
  
 Pokud používáte EdmGen.exe pro generování modelu a mapování souborů, musíte ještě nakonfigurovat vaše [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] projektu pro použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Další informace najdete v tématu [postupy: ruční konfigurace projektu Entity Framework](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).  
  
> [!NOTE]
>  Koncepční model generované EdmGen.exe zahrnuje všechny objekty v databázi. Pokud chcete generovat Koncepční model, který obsahuje pouze konkrétní objekty, použijte průvodce Entity Data Model. Další informace najdete v tématu [postupy: použití průvodce Entity Data Model](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Generování modelu školní pro použití EdmGen.exe projektu Visual Basic  
  
1.  Vytvořte databázi školy. Další informace najdete v tématu [vytváření ukázkovou databázi školy](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  Na příkazovém řádku spusťte následující příkaz bez zalomení řádků:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>Generování modelu školní pro projekt C# pomocí EdmGen.exe  
  
1.  Vytvořte databázi školy. Další informace najdete v tématu [vytváření ukázkovou databázi školy](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  Na příkazovém řádku spusťte následující příkaz bez zalomení řádků:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Modelování a mapování](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [Postupy: ruční konfigurace projektu Entity Framework](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [Postupy: předběžnému generování zobrazení pro zlepšení výkonu dotazů](http://msdn.microsoft.com/en-us/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [Nástroje modelu ADO.NET Entity Data Model](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)  
 [Postupy: Použití EdmGen.exe pro ověření modelu a souborů mapování](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)
