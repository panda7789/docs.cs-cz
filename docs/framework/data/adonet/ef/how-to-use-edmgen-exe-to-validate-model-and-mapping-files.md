---
title: 'Postupy: použití EdmGen.exe pro ověření modelu a souborů mapování'
ms.date: 03/30/2017
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
ms.openlocfilehash: fda8698381e98c64318f1a26f77f0263e9085074
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43471923"
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a><span data-ttu-id="0bf96-102">Postupy: použití EdmGen.exe pro ověření modelu a souborů mapování</span><span class="sxs-lookup"><span data-stu-id="0bf96-102">How to: Use EdmGen.exe to Validate Model and Mapping Files</span></span>
<span data-ttu-id="0bf96-103">Toto téma ukazuje, jak používat [generátor EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) nástroje pro ověření modelu a souborů mapování.</span><span class="sxs-lookup"><span data-stu-id="0bf96-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) tool to validate the model and mapping files.</span></span> <span data-ttu-id="0bf96-104">Další informace najdete v tématu [modelu Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md).</span><span class="sxs-lookup"><span data-stu-id="0bf96-104">For more information, see [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md).</span></span>  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a><span data-ttu-id="0bf96-105">Ověření modelu School pomocí EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="0bf96-105">To validate the School model using EdmGen.exe</span></span>  
  
1.  <span data-ttu-id="0bf96-106">Vytvoření databáze školy.</span><span class="sxs-lookup"><span data-stu-id="0bf96-106">Create the School database.</span></span> <span data-ttu-id="0bf96-107">Další informace najdete v tématu [vytvoření ukázkové databáze školy](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span><span class="sxs-lookup"><span data-stu-id="0bf96-107">For more information, see [Creating the School Sample Database](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span></span>  
  
2.  <span data-ttu-id="0bf96-108">Generování modelu školy.</span><span class="sxs-lookup"><span data-stu-id="0bf96-108">Generate the School model.</span></span> <span data-ttu-id="0bf96-109">Další informace najdete v tématu [postupy: použití EdmGen.exe pro generování modelu a souborů mapování](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="0bf96-109">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3.  <span data-ttu-id="0bf96-110">Na příkazovém řádku spusťte následující příkaz bez konce řádků:</span><span class="sxs-lookup"><span data-stu-id="0bf96-110">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0bf96-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="0bf96-111">See Also</span></span>  
 [<span data-ttu-id="0bf96-112">Postupy: ruční konfigurace projektu v Entity Framework</span><span class="sxs-lookup"><span data-stu-id="0bf96-112">How to: Manually Configure an Entity Framework Project</span></span>](https://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [<span data-ttu-id="0bf96-113">Datový Model Entity ADO.NET nástroje</span><span class="sxs-lookup"><span data-stu-id="0bf96-113">ADO.NET Entity Data Model  Tools</span></span>](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)  
 [<span data-ttu-id="0bf96-114">Postupy: předběžně generovat zobrazení pro zlepšení výkonu dotazů</span><span class="sxs-lookup"><span data-stu-id="0bf96-114">How to: Pre-Generate Views to Improve Query Performance</span></span>](https://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [<span data-ttu-id="0bf96-115">Postupy: Použití EdmGen.exe pro generování kódu na objektové vrstvě</span><span class="sxs-lookup"><span data-stu-id="0bf96-115">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)
