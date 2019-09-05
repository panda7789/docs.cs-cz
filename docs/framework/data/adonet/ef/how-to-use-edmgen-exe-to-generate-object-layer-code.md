---
title: 'Postupy: Použití EdmGen.exe pro generování kódu na objektové vrstvě'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: b85bacff093c268cd35dca2ede36e6ceb74ca4d1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251410"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a>Postupy: Použití EdmGen.exe pro generování kódu na objektové vrstvě
V tomto tématu se dozvíte, jak pomocí nástroje [generátoru EDM (EdmGen. exe)](edm-generator-edmgen-exe.md) vygenerovat kód objektové vrstvy založený na souboru. csdl.  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Generování kódu objektové vrstvy pro školní model pro projekt Visual Basic pomocí nástroje EdmGen. exe  
  
1. Vytvořte školní databázi. Další informace najdete v tématu [vytvoření ukázkové školní databáze](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Vygenerujte školní model nebo získejte soubor School. csdl. Další informace najdete v tématu [jak: K vygenerování modelu a mapování souborů](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)použijte EdmGen. exe.  
  
3. Na příkazovém řádku spusťte následující příkaz bez konců řádků:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a>Generování kódu vrstvy objektu pro školní model pro C# projekt pomocí EdmGen. exe  
  
1. Vytvořte školní databázi. Další informace najdete v tématu [vytvoření ukázkové školní databáze](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Vygenerujte školní model nebo získejte soubor School. csdl. Další informace najdete v tématu [jak: K vygenerování modelu a mapování souborů](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)použijte EdmGen. exe.  
  
3. Na příkazovém řádku spusťte následující příkaz bez konců řádků:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Modelování a mapování](modeling-and-mapping.md)
- [Postupy: Ruční konfigurace Entity Frameworkho projektu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [ADO.NET model EDM (Entity Data Model) nástroje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Postupy: Předem generovat zobrazení pro zlepšení výkonu dotazů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [Postupy: Použití EdmGen. exe ke generování modelu a souborů mapování](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
