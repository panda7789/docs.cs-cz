---
title: "Postupy: použití EdmGen.exe pro ověření modelu a soubory mapování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3ae17ceccf9d452951b1332525f3fa3536fd344c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a><span data-ttu-id="70bb8-102">Postupy: použití EdmGen.exe pro ověření modelu a soubory mapování</span><span class="sxs-lookup"><span data-stu-id="70bb8-102">How to: Use EdmGen.exe to Validate Model and Mapping Files</span></span>
<span data-ttu-id="70bb8-103">Toto téma ukazuje, jak používat [EDM generátor (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) nástroj k ověření modelu a mapování souborů.</span><span class="sxs-lookup"><span data-stu-id="70bb8-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) tool to validate the model and mapping files.</span></span> <span data-ttu-id="70bb8-104">Další informace najdete v tématu [datového modelu Entity](../../../../../docs/framework/data/adonet/entity-data-model.md).</span><span class="sxs-lookup"><span data-stu-id="70bb8-104">For more information, see [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md).</span></span>  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a><span data-ttu-id="70bb8-105">K ověření školní modelu s použitím EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="70bb8-105">To validate the School model using EdmGen.exe</span></span>  
  
1.  <span data-ttu-id="70bb8-106">Vytvořte databázi školy.</span><span class="sxs-lookup"><span data-stu-id="70bb8-106">Create the School database.</span></span> <span data-ttu-id="70bb8-107">Další informace najdete v tématu [vytváření ukázkovou databázi školy](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span><span class="sxs-lookup"><span data-stu-id="70bb8-107">For more information, see [Creating the School Sample Database](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span></span>  
  
2.  <span data-ttu-id="70bb8-108">Generování modelu školní.</span><span class="sxs-lookup"><span data-stu-id="70bb8-108">Generate the School model.</span></span> <span data-ttu-id="70bb8-109">Další informace najdete v tématu [postupy: použití EdmGen.exe pro generování modelu a mapování soubory](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="70bb8-109">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3.  <span data-ttu-id="70bb8-110">Na příkazovém řádku spusťte následující příkaz bez zalomení řádků:</span><span class="sxs-lookup"><span data-stu-id="70bb8-110">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="70bb8-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="70bb8-111">See Also</span></span>  
 [<span data-ttu-id="70bb8-112">Postupy: ruční konfigurace projektu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="70bb8-112">How to: Manually Configure an Entity Framework Project</span></span>](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [<span data-ttu-id="70bb8-113">Nástroje modelu ADO.NET Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="70bb8-113">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)  
 [<span data-ttu-id="70bb8-114">Postupy: předběžnému generování zobrazení pro zlepšení výkonu dotazů</span><span class="sxs-lookup"><span data-stu-id="70bb8-114">How to: Pre-Generate Views to Improve Query Performance</span></span>](http://msdn.microsoft.com/en-us/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [<span data-ttu-id="70bb8-115">Postupy: Použití EdmGen.exe pro generování kódu na objektové vrstvě</span><span class="sxs-lookup"><span data-stu-id="70bb8-115">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)
