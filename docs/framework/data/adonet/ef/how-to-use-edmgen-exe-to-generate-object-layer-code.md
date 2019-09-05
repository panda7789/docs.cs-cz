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
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a><span data-ttu-id="dd673-102">Postupy: Použití EdmGen.exe pro generování kódu na objektové vrstvě</span><span class="sxs-lookup"><span data-stu-id="dd673-102">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>
<span data-ttu-id="dd673-103">V tomto tématu se dozvíte, jak pomocí nástroje [generátoru EDM (EdmGen. exe)](edm-generator-edmgen-exe.md) vygenerovat kód objektové vrstvy založený na souboru. csdl.</span><span class="sxs-lookup"><span data-stu-id="dd673-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) tool to generate object-layer code  based on the .csdl file.</span></span>  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a><span data-ttu-id="dd673-104">Generování kódu objektové vrstvy pro školní model pro projekt Visual Basic pomocí nástroje EdmGen. exe</span><span class="sxs-lookup"><span data-stu-id="dd673-104">To generate object-layer code for the School model for a Visual Basic project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="dd673-105">Vytvořte školní databázi.</span><span class="sxs-lookup"><span data-stu-id="dd673-105">Create the School database.</span></span> <span data-ttu-id="dd673-106">Další informace najdete v tématu [vytvoření ukázkové školní databáze](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="dd673-106">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="dd673-107">Vygenerujte školní model nebo získejte soubor School. csdl.</span><span class="sxs-lookup"><span data-stu-id="dd673-107">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="dd673-108">Další informace najdete v tématu [jak: K vygenerování modelu a mapování souborů](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)použijte EdmGen. exe.</span><span class="sxs-lookup"><span data-stu-id="dd673-108">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="dd673-109">Na příkazovém řádku spusťte následující příkaz bez konců řádků:</span><span class="sxs-lookup"><span data-stu-id="dd673-109">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a><span data-ttu-id="dd673-110">Generování kódu vrstvy objektu pro školní model pro C# projekt pomocí EdmGen. exe</span><span class="sxs-lookup"><span data-stu-id="dd673-110">To generate object-layer code for the School model for a C# project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="dd673-111">Vytvořte školní databázi.</span><span class="sxs-lookup"><span data-stu-id="dd673-111">Create the School database.</span></span> <span data-ttu-id="dd673-112">Další informace najdete v tématu [vytvoření ukázkové školní databáze](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="dd673-112">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="dd673-113">Vygenerujte školní model nebo získejte soubor School. csdl.</span><span class="sxs-lookup"><span data-stu-id="dd673-113">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="dd673-114">Další informace najdete v tématu [jak: K vygenerování modelu a mapování souborů](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)použijte EdmGen. exe.</span><span class="sxs-lookup"><span data-stu-id="dd673-114">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="dd673-115">Na příkazovém řádku spusťte následující příkaz bez konců řádků:</span><span class="sxs-lookup"><span data-stu-id="dd673-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="dd673-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dd673-116">See also</span></span>

- [<span data-ttu-id="dd673-117">Modelování a mapování</span><span class="sxs-lookup"><span data-stu-id="dd673-117">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- <span data-ttu-id="dd673-118">[Postupy: Ruční konfigurace Entity Frameworkho projektu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dd673-118">[How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="dd673-119">[ADO.NET model EDM (Entity Data Model) nástroje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dd673-119">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="dd673-120">[Postupy: Předem generovat zobrazení pro zlepšení výkonu dotazů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dd673-120">[How to: Pre-Generate Views to Improve Query Performance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="dd673-121">Postupy: Použití EdmGen. exe ke generování modelu a souborů mapování</span><span class="sxs-lookup"><span data-stu-id="dd673-121">How to: Use EdmGen.exe to Generate the Model and Mapping Files</span></span>](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
