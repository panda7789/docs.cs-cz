---
title: 'Postupy: Použití EdmGen.exe pro ověření modelu a souborů mapování'
ms.date: 03/30/2017
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
ms.openlocfilehash: 12258236c904c70d6d94490e3d1c6af2457bbe0c
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827884"
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a><span data-ttu-id="be75a-102">Postupy: Použití EdmGen.exe pro ověření modelu a souborů mapování</span><span class="sxs-lookup"><span data-stu-id="be75a-102">How to: Use EdmGen.exe to Validate Model and Mapping Files</span></span>
<span data-ttu-id="be75a-103">Toto téma ukazuje, jak používat [generátor EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) nástroje pro ověření modelu a souborů mapování.</span><span class="sxs-lookup"><span data-stu-id="be75a-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) tool to validate the model and mapping files.</span></span> <span data-ttu-id="be75a-104">Další informace najdete v tématu [modelu Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md).</span><span class="sxs-lookup"><span data-stu-id="be75a-104">For more information, see [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md).</span></span>  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a><span data-ttu-id="be75a-105">Ověření modelu School pomocí EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="be75a-105">To validate the School model using EdmGen.exe</span></span>  
  
1.  <span data-ttu-id="be75a-106">Vytvoření databáze školy.</span><span class="sxs-lookup"><span data-stu-id="be75a-106">Create the School database.</span></span> <span data-ttu-id="be75a-107">Další informace najdete v tématu [vytvoření ukázkové databáze školy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="be75a-107">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="be75a-108">Generování modelu školy.</span><span class="sxs-lookup"><span data-stu-id="be75a-108">Generate the School model.</span></span> <span data-ttu-id="be75a-109">Další informace najdete v tématu [jak: Použití EdmGen.exe pro generování modelu a souborů mapování](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="be75a-109">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3.  <span data-ttu-id="be75a-110">Na příkazovém řádku spusťte následující příkaz bez konce řádků:</span><span class="sxs-lookup"><span data-stu-id="be75a-110">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="be75a-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be75a-111">See also</span></span>
- <span data-ttu-id="be75a-112">[Postupy: Ruční konfigurace projektu v Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="be75a-112">[How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="be75a-113">[Datový Model Entity ADO.NET nástroje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="be75a-113">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="be75a-114">[Postupy: Předběžně generovat zobrazení pro zlepšení výkonu dotazů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="be75a-114">[How to: Pre-Generate Views to Improve Query Performance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="be75a-115">Postupy: Použití EdmGen.exe pro generování kódu na objektové vrstvě</span><span class="sxs-lookup"><span data-stu-id="be75a-115">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)
