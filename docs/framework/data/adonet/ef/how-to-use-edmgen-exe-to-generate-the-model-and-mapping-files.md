---
title: 'Postupy: použití EdmGen. exe ke generování modelu a souborů mapování'
ms.date: 03/30/2017
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
ms.openlocfilehash: c74f9344891d43f21034a48ac51723fa7441744d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040309"
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>Postupy: použití EdmGen. exe ke generování modelu a souborů mapování
V tomto tématu se dozvíte, jak pomocí nástroje generátoru EDM (EdmGen. exe) vygenerovat následující soubory založené na školní databázi:  
  
- Koncepční model (soubor. CSDL).  
  
- Model úložiště (soubor. ssdl).  
  
- Mapování mezi koncepční modely a modely úložiště (soubor. MSL).  
  
- Kód vrstvy objektu v Visual Basic nebo C#.  
  
- Zobrazit soubory.  
  
 Nástroj EdmGen. exe používá/Mode: FullGeneration k vygenerování souborů uvedených výše. Další informace o příkazech EdmGen. exe najdete v tématu [generátor EDM (EdmGen. exe)](edm-generator-edmgen-exe.md).  
  
 Použijete-li EdmGen. exe ke generování modelu a mapování souborů, je stále nutné nakonfigurovat projekt sady Visual Studio tak, aby používal Entity Framework. Další informace naleznete v tématu [How to: ručně configure Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).  
  
> [!NOTE]
> Koncepční model generovaný nástrojem EdmGen. exe obsahuje všechny objekty v databázi. Pokud chcete vygenerovat koncepční model, který obsahuje pouze konkrétní objekty, použijte Průvodce model EDM (Entity Data Model). Další informace naleznete v tématu [How to: use the model EDM (Entity Data Model) Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Vygenerování školního modelu pro Visual Basic projekt pomocí nástroje EdmGen. exe  
  
1. Vytvořte školní databázi. Další informace najdete v tématu [vytvoření ukázkové školní databáze](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Na příkazovém řádku spusťte následující příkaz bez konců řádků:  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>Vygenerování školního modelu pro C# projekt pomocí EdmGen. exe  
  
1. Vytvořte školní databázi. Další informace najdete v tématu [vytvoření ukázkové školní databáze](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Na příkazovém řádku spusťte následující příkaz bez konců řádků:  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Modelování a mapování](modeling-and-mapping.md)
- [Postupy: ruční konfigurace Entity Frameworkho projektu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [Postupy: předběžné generování zobrazení pro zlepšení výkonu dotazů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [ADO.NET model EDM (Entity Data Model) nástroje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Postupy: Použití EdmGen.exe pro ověření modelu a souborů mapování](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)
