---
title: 'Postupy: Použití EdmGen.exe pro generování kódu na objektové vrstvě'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: 1dbd2e25d5f9795af4f80e079c6a0b807666743d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150555"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a>Postupy: Použití EdmGen.exe pro generování kódu na objektové vrstvě
Toto téma ukazuje, jak pomocí nástroje [EDMGen.exe](edm-generator-edmgen-exe.md) generátor u generovat kód objektové vrstvy na základě souboru .csdl.  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Generování kódu objektové vrstvy pro školní model pro projekt jazyka Visual Basic pomocí edmgen.exe  
  
1. Vytvořte školní databázi. Další informace naleznete [v tématu Vytvoření ukázkové databáze školy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Vygenerujte model školy nebo získejte soubor School.csdl. Další informace naleznete v [tématu How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3. Na příkazovém řádku proveďte následující příkaz bez zakonců řádků:  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a>Generování kódu objektové vrstvy pro školní model pro projekt Jazyka C# pomocí programu EdmGen.exe  
  
1. Vytvořte školní databázi. Další informace naleznete [v tématu Vytvoření ukázkové databáze školy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Vygenerujte model školy nebo získejte soubor School.csdl. Další informace naleznete v [tématu How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3. Na příkazovém řádku proveďte následující příkaz bez zakonců řádků:  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a>Viz také

- [Modelování a mapování](modeling-and-mapping.md)
- [Postup: Ruční konfigurace projektu entity frameworku](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [nástroje datového modelu ADO.NET entity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Postup: Předběžná generování zobrazení pro zlepšení výkonu dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [Postupy: Použití EdmGen.exe pro generování modelu a souborů mapování](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
