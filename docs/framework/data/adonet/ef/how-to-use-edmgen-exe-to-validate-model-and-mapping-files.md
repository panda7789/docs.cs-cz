---
title: 'Postupy: Použití EdmGen.exe pro ověření modelu a souborů mapování'
ms.date: 03/30/2017
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
ms.openlocfilehash: 4495ff3c5d55779e9db113a2a59361b643841382
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251377"
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a>Postupy: Použití EdmGen.exe pro ověření modelu a souborů mapování
V tomto tématu se dozvíte, jak pomocí nástroje [generátoru EDM (EdmGen. exe)](edm-generator-edmgen-exe.md) ověřit model a soubory mapování. Další informace najdete v tématu [model EDM (Entity Data Model)](../entity-data-model.md).  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a>Ověření školního modelu pomocí nástroje EdmGen. exe  
  
1. Vytvořte školní databázi. Další informace najdete v tématu [vytvoření ukázkové školní databáze](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Vygenerujte školní model. Další informace najdete v tématu [jak: K vygenerování modelu a mapování souborů](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)použijte EdmGen. exe.  
  
3. Na příkazovém řádku spusťte následující příkaz bez konců řádků:  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Ruční konfigurace Entity Frameworkho projektu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [ADO.NET model EDM (Entity Data Model) nástroje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Postupy: Předem generovat zobrazení pro zlepšení výkonu dotazů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [Postupy: Použití EdmGen. exe pro generování kódu objektové vrstvy](how-to-use-edmgen-exe-to-generate-object-layer-code.md)
