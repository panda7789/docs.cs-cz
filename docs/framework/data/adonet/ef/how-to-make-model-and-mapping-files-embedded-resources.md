---
title: 'Postupy: Vytvoření vložených prostředků modelu a souborů mapování'
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: eae3681664ab1fd095487a7b7ed395302faf2588
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607437"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a><span data-ttu-id="cee9d-102">Postupy: Vytvoření vložených prostředků modelu a souborů mapování</span><span class="sxs-lookup"><span data-stu-id="cee9d-102">How to: Make Model and Mapping Files Embedded Resources</span></span>
<span data-ttu-id="cee9d-103">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Umožňuje nasadit modelu a souborů mapování jako vložené prostředky aplikace.</span><span class="sxs-lookup"><span data-stu-id="cee9d-103">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] enables you to deploy model and mapping files as embedded resources of an application.</span></span> <span data-ttu-id="cee9d-104">Sestavení s vloženým modelem a souborů mapování musí být ve stejné doméně aplikace jako připojení entity načíst.</span><span class="sxs-lookup"><span data-stu-id="cee9d-104">The assembly with the embedded model and mapping files must be loaded in the same application domain as the entity connection.</span></span> <span data-ttu-id="cee9d-105">Další informace najdete v tématu [připojovací řetězce](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="cee9d-105">For more information, see [Connection Strings](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span></span> <span data-ttu-id="cee9d-106">Ve výchozím nastavení [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] nástroje vložení modelu a souborů mapování.</span><span class="sxs-lookup"><span data-stu-id="cee9d-106">By default, the [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] tools embed the model and mapping files.</span></span> <span data-ttu-id="cee9d-107">Když definujete modelu a souborů mapování ručně, pomocí tohoto postupu můžete zajistit, že jsou soubory nasazeny jako vložené prostředky spolu s [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="cee9d-107">When you manually define the model and mapping files, use this procedure to ensure that the files are deployed as embedded resources together with an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cee9d-108">Pokud chcete zachovat vložené prostředky, musíte tento postup zopakovat vždy, když se mění modelu a souborů mapování.</span><span class="sxs-lookup"><span data-stu-id="cee9d-108">To maintain embedded resources, you must repeat this procedure whenever the model and mapping files are modified.</span></span>  
  
### <a name="to-embed-model-and-mapping-files"></a><span data-ttu-id="cee9d-109">Chcete-li vložit modelu a souborů mapování</span><span class="sxs-lookup"><span data-stu-id="cee9d-109">To embed model and mapping files</span></span>  
  
1. <span data-ttu-id="cee9d-110">V **Průzkumníka řešení**, vyberte soubor koncepční (.csdl).</span><span class="sxs-lookup"><span data-stu-id="cee9d-110">In **Solution Explorer**, select the conceptual (.csdl) file.</span></span>  
  
2. <span data-ttu-id="cee9d-111">V **vlastnosti** podokně nastavte **akce sestavení** k **integrovaný prostředek**.</span><span class="sxs-lookup"><span data-stu-id="cee9d-111">In the **Properties** pane, set **Build Action** to **Embedded Resource**.</span></span>  
  
3. <span data-ttu-id="cee9d-112">Opakujte kroky 1 a 2 pro soubor úložiště (ssdl) a soubor mapování (.msl).</span><span class="sxs-lookup"><span data-stu-id="cee9d-112">Repeat steps 1 and 2 for the storage (.ssdl) file and the mapping (.msl) file.</span></span>  
  
4. <span data-ttu-id="cee9d-113">V **Průzkumníka řešení**, poklikejte na soubor App.config a potom změňte `Metadata` parametr `connectionString` atributů na základě jedné z následujících formátů:</span><span class="sxs-lookup"><span data-stu-id="cee9d-113">In **Solution Explorer**, double-click the App.config file and then modify the `Metadata` parameter in the `connectionString` attribute based on one of the following formats:</span></span>  
  
    - <span data-ttu-id="cee9d-114">`Metadata=``res://<assemblyFullName>/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="cee9d-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span></span>  
  
    - <span data-ttu-id="cee9d-115">`Metadata=``res://*/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="cee9d-115">`Metadata=` `res://*/<resourceName>;`</span></span>  
  
    - `Metadata=res://*;`  
  
     <span data-ttu-id="cee9d-116">Další informace najdete v tématu [připojovací řetězce](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="cee9d-116">For more information, see [Connection Strings](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cee9d-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="cee9d-117">Example</span></span>  
 <span data-ttu-id="cee9d-118">Vložený modelu a souborů mapování pro odkazuje na následující připojovací řetězec [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span><span class="sxs-lookup"><span data-stu-id="cee9d-118">The following connection string references embedded model and mapping files for the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="cee9d-119">Tento připojovací řetězec je uložen v souboru App.config projektu.</span><span class="sxs-lookup"><span data-stu-id="cee9d-119">This connection string is stored in the project's App.config file.</span></span>  

## <a name="see-also"></a><span data-ttu-id="cee9d-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cee9d-120">See also</span></span>

- [<span data-ttu-id="cee9d-121">Modelování a mapování</span><span class="sxs-lookup"><span data-stu-id="cee9d-121">Modeling and Mapping</span></span>](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)
- [<span data-ttu-id="cee9d-122">Postupy: Definování připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="cee9d-122">How to: Define the Connection String</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)
- [<span data-ttu-id="cee9d-123">Postupy: Vytvoření připojovacího řetězce EntityConnection</span><span class="sxs-lookup"><span data-stu-id="cee9d-123">How to: Build an EntityConnection Connection String</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)
- <span data-ttu-id="cee9d-124">[Datový Model Entity ADO.NET nástroje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="cee9d-124">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
