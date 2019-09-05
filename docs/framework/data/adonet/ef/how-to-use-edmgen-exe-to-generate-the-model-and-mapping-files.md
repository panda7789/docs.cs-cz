---
title: 'Postupy: Použití EdmGen.exe pro generování modelu a souborů mapování'
ms.date: 03/30/2017
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
ms.openlocfilehash: 141b19c545360f92c2689252cf9aefd1ef156cf0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251412"
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>Postupy: Použití EdmGen.exe pro generování modelu a souborů mapování
V tomto tématu se dozvíte, jak pomocí nástroje generátoru EDM (EdmGen. exe) vygenerovat následující soubory založené na školní databázi:  
  
- Koncepční model (soubor. CSDL).  
  
- Model úložiště (soubor. ssdl).  
  
- Mapování mezi koncepční modely a modely úložiště (soubor. MSL).  
  
- Kód vrstvy objektu v Visual Basic nebo C#.  
  
- Zobrazit soubory.  
  
 Nástroj EdmGen. exe používá/Mode: FullGeneration k vygenerování souborů uvedených výše. Další informace o příkazech EdmGen. exe najdete v tématu [generátor EDM (EdmGen. exe)](edm-generator-edmgen-exe.md).  
  
 Použijete-li EdmGen. exe ke generování modelu a mapování souborů, je stále nutné nakonfigurovat projekt sady Visual Studio tak, aby používal [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Další informace najdete v tématu [jak: Ručně nakonfigurujte Entity Framework projekt](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).  
  
> [!NOTE]
> Koncepční model generovaný nástrojem EdmGen. exe obsahuje všechny objekty v databázi. Pokud chcete vygenerovat koncepční model, který obsahuje pouze konkrétní objekty, použijte Průvodce model EDM (Entity Data Model). Další informace najdete v tématu [jak: Použijte průvodce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))model EDM (Entity Data Model).  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Vygenerování školního modelu pro Visual Basic projekt pomocí nástroje EdmGen. exe  
  
1. Vytvořte školní databázi. Další informace najdete v tématu [vytvoření ukázkové školní databáze](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Na příkazovém řádku spusťte následující příkaz bez konců řádků:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>Vygenerování školního modelu pro C# projekt pomocí EdmGen. exe  
  
1. Vytvořte školní databázi. Další informace najdete v tématu [vytvoření ukázkové školní databáze](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Na příkazovém řádku spusťte následující příkaz bez konců řádků:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Modelování a mapování](modeling-and-mapping.md)
- [Postupy: Ruční konfigurace Entity Frameworkho projektu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [Postupy: Předem generovat zobrazení pro zlepšení výkonu dotazů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [ADO.NET model EDM (Entity Data Model) nástroje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Postupy: Použití EdmGen. exe k ověření modelu a souborů mapování](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)
