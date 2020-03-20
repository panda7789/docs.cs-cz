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
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a><span data-ttu-id="f1883-102">Postupy: Použití EdmGen.exe pro generování kódu na objektové vrstvě</span><span class="sxs-lookup"><span data-stu-id="f1883-102">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>
<span data-ttu-id="f1883-103">Toto téma ukazuje, jak pomocí nástroje [EDMGen.exe](edm-generator-edmgen-exe.md) generátor u generovat kód objektové vrstvy na základě souboru .csdl.</span><span class="sxs-lookup"><span data-stu-id="f1883-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) tool to generate object-layer code  based on the .csdl file.</span></span>  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a><span data-ttu-id="f1883-104">Generování kódu objektové vrstvy pro školní model pro projekt jazyka Visual Basic pomocí edmgen.exe</span><span class="sxs-lookup"><span data-stu-id="f1883-104">To generate object-layer code for the School model for a Visual Basic project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="f1883-105">Vytvořte školní databázi.</span><span class="sxs-lookup"><span data-stu-id="f1883-105">Create the School database.</span></span> <span data-ttu-id="f1883-106">Další informace naleznete [v tématu Vytvoření ukázkové databáze školy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f1883-106">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="f1883-107">Vygenerujte model školy nebo získejte soubor School.csdl.</span><span class="sxs-lookup"><span data-stu-id="f1883-107">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="f1883-108">Další informace naleznete v [tématu How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="f1883-108">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="f1883-109">Na příkazovém řádku proveďte následující příkaz bez zakonců řádků:</span><span class="sxs-lookup"><span data-stu-id="f1883-109">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a><span data-ttu-id="f1883-110">Generování kódu objektové vrstvy pro školní model pro projekt Jazyka C# pomocí programu EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="f1883-110">To generate object-layer code for the School model for a C# project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="f1883-111">Vytvořte školní databázi.</span><span class="sxs-lookup"><span data-stu-id="f1883-111">Create the School database.</span></span> <span data-ttu-id="f1883-112">Další informace naleznete [v tématu Vytvoření ukázkové databáze školy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f1883-112">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="f1883-113">Vygenerujte model školy nebo získejte soubor School.csdl.</span><span class="sxs-lookup"><span data-stu-id="f1883-113">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="f1883-114">Další informace naleznete v [tématu How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="f1883-114">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="f1883-115">Na příkazovém řádku proveďte následující příkaz bez zakonců řádků:</span><span class="sxs-lookup"><span data-stu-id="f1883-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f1883-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1883-116">See also</span></span>

- [<span data-ttu-id="f1883-117">Modelování a mapování</span><span class="sxs-lookup"><span data-stu-id="f1883-117">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- <span data-ttu-id="f1883-118">[Postup: Ruční konfigurace projektu entity frameworku](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f1883-118">[How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="f1883-119">[nástroje datového modelu ADO.NET entity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f1883-119">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="f1883-120">[Postup: Předběžná generování zobrazení pro zlepšení výkonu dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f1883-120">[How to: Pre-Generate Views to Improve Query Performance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="f1883-121">Postupy: Použití EdmGen.exe pro generování modelu a souborů mapování</span><span class="sxs-lookup"><span data-stu-id="f1883-121">How to: Use EdmGen.exe to Generate the Model and Mapping Files</span></span>](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
