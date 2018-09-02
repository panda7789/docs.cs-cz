---
title: 'Postupy: použití EdmGen.exe pro generování kódu na objektové vrstvě'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: c15ceec66ad5b1c9ef414c3e57e3b6e49c372e7a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416261"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a><span data-ttu-id="f4527-102">Postupy: použití EdmGen.exe pro generování kódu na objektové vrstvě</span><span class="sxs-lookup"><span data-stu-id="f4527-102">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>
<span data-ttu-id="f4527-103">Toto téma ukazuje, jak používat [generátor EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) nástroj pro generování kódu na objektové vrstvě podle soubor .csdl.</span><span class="sxs-lookup"><span data-stu-id="f4527-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) tool to generate object-layer code  based on the .csdl file.</span></span>  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a><span data-ttu-id="f4527-104">Pro generování kódu objektové vrstvě pro školy model pro projekt jazyka Visual Basic pomocí EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="f4527-104">To generate object-layer code for the School model for a Visual Basic project using EdmGen.exe</span></span>  
  
1.  <span data-ttu-id="f4527-105">Vytvoření databáze školy.</span><span class="sxs-lookup"><span data-stu-id="f4527-105">Create the School database.</span></span> <span data-ttu-id="f4527-106">Další informace najdete v tématu [vytvoření ukázkové databáze školy](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span><span class="sxs-lookup"><span data-stu-id="f4527-106">For more information, see [Creating the School Sample Database](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span></span>  
  
2.  <span data-ttu-id="f4527-107">Generování modelu školní nebo získání School.csdl souboru.</span><span class="sxs-lookup"><span data-stu-id="f4527-107">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="f4527-108">Další informace najdete v tématu [postupy: použití EdmGen.exe pro generování modelu a souborů mapování](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="f4527-108">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3.  <span data-ttu-id="f4527-109">Na příkazovém řádku spusťte následující příkaz bez konce řádků:</span><span class="sxs-lookup"><span data-stu-id="f4527-109">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a><span data-ttu-id="f4527-110">Pro generování kódu objektové vrstvě pro školy model pro použití EdmGen.exe projektu C#</span><span class="sxs-lookup"><span data-stu-id="f4527-110">To generate object-layer code for the School model for a C# project using EdmGen.exe</span></span>  
  
1.  <span data-ttu-id="f4527-111">Vytvoření databáze školy.</span><span class="sxs-lookup"><span data-stu-id="f4527-111">Create the School database.</span></span> <span data-ttu-id="f4527-112">Další informace najdete v tématu [vytvoření ukázkové databáze školy](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span><span class="sxs-lookup"><span data-stu-id="f4527-112">For more information, see [Creating the School Sample Database](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span></span>  
  
2.  <span data-ttu-id="f4527-113">Generování modelu školní nebo získání School.csdl souboru.</span><span class="sxs-lookup"><span data-stu-id="f4527-113">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="f4527-114">Další informace najdete v tématu [postupy: použití EdmGen.exe pro generování modelu a souborů mapování](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="f4527-114">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3.  <span data-ttu-id="f4527-115">Na příkazovém řádku spusťte následující příkaz bez konce řádků:</span><span class="sxs-lookup"><span data-stu-id="f4527-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f4527-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4527-116">See Also</span></span>  
 [<span data-ttu-id="f4527-117">Modelování a mapování</span><span class="sxs-lookup"><span data-stu-id="f4527-117">Modeling and Mapping</span></span>](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [<span data-ttu-id="f4527-118">Postupy: ruční konfigurace projektu v Entity Framework</span><span class="sxs-lookup"><span data-stu-id="f4527-118">How to: Manually Configure an Entity Framework Project</span></span>](https://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [<span data-ttu-id="f4527-119">Datový Model Entity ADO.NET nástroje</span><span class="sxs-lookup"><span data-stu-id="f4527-119">ADO.NET Entity Data Model  Tools</span></span>](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)  
 [<span data-ttu-id="f4527-120">Postupy: předběžně generovat zobrazení pro zlepšení výkonu dotazů</span><span class="sxs-lookup"><span data-stu-id="f4527-120">How to: Pre-Generate Views to Improve Query Performance</span></span>](https://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [<span data-ttu-id="f4527-121">Postupy: Použití EdmGen.exe pro generování modelu a souborů mapování</span><span class="sxs-lookup"><span data-stu-id="f4527-121">How to: Use EdmGen.exe to Generate the Model and Mapping Files</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
