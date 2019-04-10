---
title: 'Postupy: Použití EdmGen.exe pro generování modelu a souborů mapování'
ms.date: 03/30/2017
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
ms.openlocfilehash: 915a9f3c53dba355480a3869602f963b195d53fb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59323795"
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>Postupy: Použití EdmGen.exe pro generování modelu a souborů mapování
Toto téma ukazuje, jak používat nástroj Generátor EDM (EdmGen.exe) můžete vygenerovat následující soubory podle databáze školy:  
  
-   Koncepční model (soubor .csdl).  
  
-   Model úložiště (souboru ssdl).  
  
-   Mapování mezi modely koncepční a úložiště (soubor .msl).  
  
-   Objektové vrstvě kód v jazyce Visual Basic nebo C#.  
  
-   Zobrazit soubory.  
  
 Nástroje EdmGen.exe /mode:FullGeneration používá ke generování souborů uvedených výše. Další informace o příkazech EdmGen.exe najdete v tématu [generátor EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).  
  
 Pokud použití EdmGen.exe pro generování modelu a souborů mapování, je stále potřeba konfigurace projektu Visual Studio pro použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Další informace najdete v tématu [jak: Ruční konfigurace projektu v Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).  
  
> [!NOTE]
>  Koncepční model generovaných EdmGen.exe zahrnuje všechny objekty v databázi. Pokud chcete generovat Koncepční model, který obsahuje pouze konkrétní objekty, použijte Průvodce datovým modelem Entity. Další informace najdete v tématu [jak: Použijte Průvodce datovým modelem Entity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Generování modelu školní pro projekt jazyka Visual Basic pomocí EdmGen.exe  
  
1. Vytvoření databáze školy. Další informace najdete v tématu [vytvoření ukázkové databáze školy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Na příkazovém řádku spusťte následující příkaz bez konce řádků:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>Generování modelu School pomocí EdmGen.exe projektu C#  
  
1. Vytvoření databáze školy. Další informace najdete v tématu [vytvoření ukázkové databáze školy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Na příkazovém řádku spusťte následující příkaz bez konce řádků:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Modelování a mapování](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)
- [Postupy: Ruční konfigurace projektu v Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [Postupy: Předběžně generovat zobrazení pro zlepšení výkonu dotazů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [Nástroje modelu Entity Data Model ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Postupy: Použití EdmGen.exe pro ověření modelu a souborů mapování](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)
