---
title: 'Postupy: Vytvoření vložených prostředků modelu a souborů mapování'
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: 371f8f0317295ee39d543b5637afb93102036b62
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854591"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a><span data-ttu-id="b73c4-102">Postupy: Vytvoření vložených prostředků modelu a souborů mapování</span><span class="sxs-lookup"><span data-stu-id="b73c4-102">How to: Make Model and Mapping Files Embedded Resources</span></span>
<span data-ttu-id="b73c4-103">Entity Framework umožňuje nasadit model a mapování souborů jako vložené prostředky aplikace.</span><span class="sxs-lookup"><span data-stu-id="b73c4-103">The Entity Framework enables you to deploy model and mapping files as embedded resources of an application.</span></span> <span data-ttu-id="b73c4-104">Sestavení s vloženým modelem a soubory mapování musí být načteny ve stejné doméně aplikace jako připojení k entitě.</span><span class="sxs-lookup"><span data-stu-id="b73c4-104">The assembly with the embedded model and mapping files must be loaded in the same application domain as the entity connection.</span></span> <span data-ttu-id="b73c4-105">Další informace najdete v tématu [připojovací řetězce](connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="b73c4-105">For more information, see [Connection Strings](connection-strings.md).</span></span> <span data-ttu-id="b73c4-106">Ve výchozím nastavení nástroje model EDM (Entity Data Model) vkládají model a mapování souborů.</span><span class="sxs-lookup"><span data-stu-id="b73c4-106">By default, the Entity Data Model tools embed the model and mapping files.</span></span> <span data-ttu-id="b73c4-107">Při ručním definování modelu a mapování souborů použijte tento postup, chcete-li zajistit, aby byly soubory nasazeny jako integrované prostředky spolu s aplikací Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="b73c4-107">When you manually define the model and mapping files, use this procedure to ensure that the files are deployed as embedded resources together with an Entity Framework application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b73c4-108">Chcete-li zachovat vložené prostředky, je nutné tento postup opakovat vždy, když dojde ke změně modelu a souborů mapování.</span><span class="sxs-lookup"><span data-stu-id="b73c4-108">To maintain embedded resources, you must repeat this procedure whenever the model and mapping files are modified.</span></span>  
  
### <a name="to-embed-model-and-mapping-files"></a><span data-ttu-id="b73c4-109">Vložení modelu a souborů mapování</span><span class="sxs-lookup"><span data-stu-id="b73c4-109">To embed model and mapping files</span></span>  
  
1. <span data-ttu-id="b73c4-110">V **Průzkumník řešení**vyberte koncepční soubor (. CSDL).</span><span class="sxs-lookup"><span data-stu-id="b73c4-110">In **Solution Explorer**, select the conceptual (.csdl) file.</span></span>  
  
2. <span data-ttu-id="b73c4-111">V podokně **vlastnosti** nastavte **akci sestavení** na **Integrovaný prostředek**.</span><span class="sxs-lookup"><span data-stu-id="b73c4-111">In the **Properties** pane, set **Build Action** to **Embedded Resource**.</span></span>  
  
3. <span data-ttu-id="b73c4-112">Opakujte kroky 1 a 2 pro soubor úložiště (. ssdl) a soubor mapování (. MSL).</span><span class="sxs-lookup"><span data-stu-id="b73c4-112">Repeat steps 1 and 2 for the storage (.ssdl) file and the mapping (.msl) file.</span></span>  
  
4. <span data-ttu-id="b73c4-113">V **Průzkumník řešení**dvakrát klikněte na soubor App. config a pak změňte `Metadata` parametr v `connectionString` atributu na základě jednoho z následujících formátů:</span><span class="sxs-lookup"><span data-stu-id="b73c4-113">In **Solution Explorer**, double-click the App.config file and then modify the `Metadata` parameter in the `connectionString` attribute based on one of the following formats:</span></span>  
  
    - <span data-ttu-id="b73c4-114">`Metadata=``res://<assemblyFullName>/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="b73c4-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span></span>  
  
    - <span data-ttu-id="b73c4-115">`Metadata=``res://*/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="b73c4-115">`Metadata=` `res://*/<resourceName>;`</span></span>  
  
    - `Metadata=res://*;`  
  
     <span data-ttu-id="b73c4-116">Další informace najdete v tématu [připojovací řetězce](connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="b73c4-116">For more information, see [Connection Strings](connection-strings.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b73c4-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="b73c4-117">Example</span></span>  
 <span data-ttu-id="b73c4-118">Následující připojovací řetězec odkazuje na vložený model a soubory mapování pro [model prodeje AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span><span class="sxs-lookup"><span data-stu-id="b73c4-118">The following connection string references embedded model and mapping files for the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="b73c4-119">Tento připojovací řetězec je uložený v souboru App. config projektu.</span><span class="sxs-lookup"><span data-stu-id="b73c4-119">This connection string is stored in the project's App.config file.</span></span>  

## <a name="see-also"></a><span data-ttu-id="b73c4-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b73c4-120">See also</span></span>

- [<span data-ttu-id="b73c4-121">Modelování a mapování</span><span class="sxs-lookup"><span data-stu-id="b73c4-121">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- [<span data-ttu-id="b73c4-122">Postupy: Definování připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="b73c4-122">How to: Define the Connection String</span></span>](how-to-define-the-connection-string.md)
- [<span data-ttu-id="b73c4-123">Postupy: Vytvoření připojovacího řetězce EntityConnection</span><span class="sxs-lookup"><span data-stu-id="b73c4-123">How to: Build an EntityConnection Connection String</span></span>](how-to-build-an-entityconnection-connection-string.md)
- <span data-ttu-id="b73c4-124">[ADO.NET model EDM (Entity Data Model) nástroje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b73c4-124">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
