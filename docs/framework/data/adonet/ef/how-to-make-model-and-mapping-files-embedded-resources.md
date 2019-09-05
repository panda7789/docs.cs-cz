---
title: 'Postupy: Vytvoření vložených prostředků modelu a souborů mapování'
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: c88e0c09742d76c7508d7d782eabbe46035d3501
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251447"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a><span data-ttu-id="55544-102">Postupy: Vytvoření vložených prostředků modelu a souborů mapování</span><span class="sxs-lookup"><span data-stu-id="55544-102">How to: Make Model and Mapping Files Embedded Resources</span></span>
<span data-ttu-id="55544-103">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Umožňuje nasadit model a mapování souborů jako vložené prostředky aplikace.</span><span class="sxs-lookup"><span data-stu-id="55544-103">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] enables you to deploy model and mapping files as embedded resources of an application.</span></span> <span data-ttu-id="55544-104">Sestavení s vloženým modelem a soubory mapování musí být načteny ve stejné doméně aplikace jako připojení k entitě.</span><span class="sxs-lookup"><span data-stu-id="55544-104">The assembly with the embedded model and mapping files must be loaded in the same application domain as the entity connection.</span></span> <span data-ttu-id="55544-105">Další informace najdete v tématu [připojovací řetězce](connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="55544-105">For more information, see [Connection Strings](connection-strings.md).</span></span> <span data-ttu-id="55544-106">Ve výchozím nastavení nástroje model EDM (Entity Data Model) vkládají model a mapování souborů.</span><span class="sxs-lookup"><span data-stu-id="55544-106">By default, the Entity Data Model tools embed the model and mapping files.</span></span> <span data-ttu-id="55544-107">Při ručním definování modelu a mapování souborů použijte tento postup, chcete-li zajistit, aby byly soubory nasazeny jako integrované prostředky spolu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] s aplikací.</span><span class="sxs-lookup"><span data-stu-id="55544-107">When you manually define the model and mapping files, use this procedure to ensure that the files are deployed as embedded resources together with an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55544-108">Chcete-li zachovat vložené prostředky, je nutné tento postup opakovat vždy, když dojde ke změně modelu a souborů mapování.</span><span class="sxs-lookup"><span data-stu-id="55544-108">To maintain embedded resources, you must repeat this procedure whenever the model and mapping files are modified.</span></span>  
  
### <a name="to-embed-model-and-mapping-files"></a><span data-ttu-id="55544-109">Vložení modelu a souborů mapování</span><span class="sxs-lookup"><span data-stu-id="55544-109">To embed model and mapping files</span></span>  
  
1. <span data-ttu-id="55544-110">V **Průzkumník řešení**vyberte koncepční soubor (. CSDL).</span><span class="sxs-lookup"><span data-stu-id="55544-110">In **Solution Explorer**, select the conceptual (.csdl) file.</span></span>  
  
2. <span data-ttu-id="55544-111">V podokně **vlastnosti** nastavte **akci sestavení** na **Integrovaný prostředek**.</span><span class="sxs-lookup"><span data-stu-id="55544-111">In the **Properties** pane, set **Build Action** to **Embedded Resource**.</span></span>  
  
3. <span data-ttu-id="55544-112">Opakujte kroky 1 a 2 pro soubor úložiště (. ssdl) a soubor mapování (. MSL).</span><span class="sxs-lookup"><span data-stu-id="55544-112">Repeat steps 1 and 2 for the storage (.ssdl) file and the mapping (.msl) file.</span></span>  
  
4. <span data-ttu-id="55544-113">V **Průzkumník řešení**dvakrát klikněte na soubor App. config a pak změňte `Metadata` parametr v `connectionString` atributu na základě jednoho z následujících formátů:</span><span class="sxs-lookup"><span data-stu-id="55544-113">In **Solution Explorer**, double-click the App.config file and then modify the `Metadata` parameter in the `connectionString` attribute based on one of the following formats:</span></span>  
  
    - <span data-ttu-id="55544-114">`Metadata=``res://<assemblyFullName>/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="55544-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span></span>  
  
    - <span data-ttu-id="55544-115">`Metadata=``res://*/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="55544-115">`Metadata=` `res://*/<resourceName>;`</span></span>  
  
    - `Metadata=res://*;`  
  
     <span data-ttu-id="55544-116">Další informace najdete v tématu [připojovací řetězce](connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="55544-116">For more information, see [Connection Strings](connection-strings.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="55544-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="55544-117">Example</span></span>  
 <span data-ttu-id="55544-118">Následující připojovací řetězec odkazuje na vložený model a soubory mapování pro [model prodeje AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span><span class="sxs-lookup"><span data-stu-id="55544-118">The following connection string references embedded model and mapping files for the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="55544-119">Tento připojovací řetězec je uložený v souboru App. config projektu.</span><span class="sxs-lookup"><span data-stu-id="55544-119">This connection string is stored in the project's App.config file.</span></span>  

## <a name="see-also"></a><span data-ttu-id="55544-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55544-120">See also</span></span>

- [<span data-ttu-id="55544-121">Modelování a mapování</span><span class="sxs-lookup"><span data-stu-id="55544-121">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- [<span data-ttu-id="55544-122">Postupy: Definování připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="55544-122">How to: Define the Connection String</span></span>](how-to-define-the-connection-string.md)
- [<span data-ttu-id="55544-123">Postupy: Vytvoření připojovacího řetězce EntityConnection</span><span class="sxs-lookup"><span data-stu-id="55544-123">How to: Build an EntityConnection Connection String</span></span>](how-to-build-an-entityconnection-connection-string.md)
- <span data-ttu-id="55544-124">[ADO.NET model EDM (Entity Data Model) nástroje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="55544-124">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
