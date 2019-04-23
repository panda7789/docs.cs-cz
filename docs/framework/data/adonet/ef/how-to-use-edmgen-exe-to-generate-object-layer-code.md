---
title: 'Postupy: Použití EdmGen.exe pro generování kódu na objektové vrstvě'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: 8a39027ee6a5647bbd645f5a38e35d61f7ebbd8e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59333402"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a><span data-ttu-id="87f2a-102">Postupy: Použití EdmGen.exe pro generování kódu na objektové vrstvě</span><span class="sxs-lookup"><span data-stu-id="87f2a-102">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>
<span data-ttu-id="87f2a-103">Toto téma ukazuje, jak používat [generátor EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) nástroj pro generování kódu na objektové vrstvě podle soubor .csdl.</span><span class="sxs-lookup"><span data-stu-id="87f2a-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) tool to generate object-layer code  based on the .csdl file.</span></span>  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a><span data-ttu-id="87f2a-104">Pro generování kódu objektové vrstvě pro školy model pro projekt jazyka Visual Basic pomocí EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="87f2a-104">To generate object-layer code for the School model for a Visual Basic project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="87f2a-105">Vytvoření databáze školy.</span><span class="sxs-lookup"><span data-stu-id="87f2a-105">Create the School database.</span></span> <span data-ttu-id="87f2a-106">Další informace najdete v tématu [vytvoření ukázkové databáze školy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="87f2a-106">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="87f2a-107">Generování modelu školní nebo získání School.csdl souboru.</span><span class="sxs-lookup"><span data-stu-id="87f2a-107">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="87f2a-108">Další informace najdete v tématu [jak: Použití EdmGen.exe pro generování modelu a souborů mapování](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="87f2a-108">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="87f2a-109">Na příkazovém řádku spusťte následující příkaz bez konce řádků:</span><span class="sxs-lookup"><span data-stu-id="87f2a-109">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a><span data-ttu-id="87f2a-110">Pro generování kódu objektové vrstvě pro školy model pro použití EdmGen.exe projektu C#</span><span class="sxs-lookup"><span data-stu-id="87f2a-110">To generate object-layer code for the School model for a C# project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="87f2a-111">Vytvoření databáze školy.</span><span class="sxs-lookup"><span data-stu-id="87f2a-111">Create the School database.</span></span> <span data-ttu-id="87f2a-112">Další informace najdete v tématu [vytvoření ukázkové databáze školy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="87f2a-112">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="87f2a-113">Generování modelu školní nebo získání School.csdl souboru.</span><span class="sxs-lookup"><span data-stu-id="87f2a-113">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="87f2a-114">Další informace najdete v tématu [jak: Použití EdmGen.exe pro generování modelu a souborů mapování](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="87f2a-114">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="87f2a-115">Na příkazovém řádku spusťte následující příkaz bez konce řádků:</span><span class="sxs-lookup"><span data-stu-id="87f2a-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="87f2a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87f2a-116">See also</span></span>

- [<span data-ttu-id="87f2a-117">Modelování a mapování</span><span class="sxs-lookup"><span data-stu-id="87f2a-117">Modeling and Mapping</span></span>](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)
- <span data-ttu-id="87f2a-118">[Postupy: Ruční konfigurace projektu v Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="87f2a-118">[How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="87f2a-119">[Datový Model Entity ADO.NET nástroje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="87f2a-119">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="87f2a-120">[Postupy: Předběžně generovat zobrazení pro zlepšení výkonu dotazů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="87f2a-120">[How to: Pre-Generate Views to Improve Query Performance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="87f2a-121">Postupy: Použití EdmGen.exe pro generování modelu a souborů mapování</span><span class="sxs-lookup"><span data-stu-id="87f2a-121">How to: Use EdmGen.exe to Generate the Model and Mapping Files</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
