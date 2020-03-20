---
title: 'Postupy: Použití EdmGen.exe pro generování modelu a souborů mapování'
ms.date: 03/30/2017
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
ms.openlocfilehash: ee8297c0833378b2b44800355b47db9caa2dc7fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150508"
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>Postupy: Použití EdmGen.exe pro generování modelu a souborů mapování
Toto téma ukazuje, jak používat edm generátor (EdmGen.exe) nástroj pro generování následujících souborů na základě databáze školy:  
  
- Koncepční model (soubor .csdl).  
  
- Model úložiště (soubor .ssdl).  
  
- Mapování mezi koncepčními a paměťovými modely (soubor MSL).  
  
- Kód objektové vrstvy v jazyce Visual Basic nebo C#.  
  
- Zobrazení souborů.  
  
 Nástroj EdmGen.exe používá /mode:FullGeneration ke generování výše uvedených souborů. Další informace o příkazech EdmGen.exe naleznete v tématu [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md).  
  
 Pokud ke generování souborů modelu a mapování používáte edmgen.exe, budete stále muset nakonfigurovat projekt sady Visual Studio tak, aby používal rozhraní Entity Framework. Další informace naleznete v [tématu How to: Manually Configure a Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).  
  
> [!NOTE]
> Koncepční model generovaný edmgen.exe zahrnuje všechny objekty v databázi. Pokud chcete generovat koncepční model, který obsahuje pouze určité objekty, použijte Průvodce datovým modelem entity. Další informace naleznete v [tématu How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Generování modelu školy pro projekt jazyka Pomocí edmGen.exe  
  
1. Vytvořte školní databázi. Další informace naleznete [v tématu Vytvoření ukázkové databáze školy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Na příkazovém řádku proveďte následující příkaz bez zakonců řádků:  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>Generování modelu školy pro projekt Jazyka C# pomocí programu EdmGen.exe  
  
1. Vytvořte školní databázi. Další informace naleznete [v tématu Vytvoření ukázkové databáze školy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Na příkazovém řádku proveďte následující příkaz bez zakonců řádků:  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>Viz také

- [Modelování a mapování](modeling-and-mapping.md)
- [Postup: Ruční konfigurace projektu entity frameworku](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [Postup: Předběžná generování zobrazení pro zlepšení výkonu dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [nástroje datového modelu ADO.NET entity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Postupy: Použití EdmGen.exe pro ověření modelu a souborů mapování](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)
