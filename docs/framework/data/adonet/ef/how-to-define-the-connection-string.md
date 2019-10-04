---
title: 'Postupy: definování připojovacího řetězce'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: 9ce0b427cac17fc338877c5f85d3648d15d5ee14
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833955"
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="0db5e-102">Postupy: definování připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="0db5e-102">How to: Define the Connection String</span></span>

<span data-ttu-id="0db5e-103">Toto téma ukazuje, jak definovat připojovací řetězec, který se používá při připojování k koncepčnímu modelu.</span><span class="sxs-lookup"><span data-stu-id="0db5e-103">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="0db5e-104">Toto téma je založené na modelu [AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) koncepční model.</span><span class="sxs-lookup"><span data-stu-id="0db5e-104">This topic is based on the [AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) conceptual model.</span></span> <span data-ttu-id="0db5e-105">Model prodeje společnosti AdventureWorks se používá v různých tématech souvisejících s úlohami v dokumentaci k Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="0db5e-105">The AdventureWorks Sales Model is used throughout the task-related topics in the Entity Framework documentation.</span></span> <span data-ttu-id="0db5e-106">Toto téma předpokládá, že jste již nakonfigurovali Entity Framework a definovali prodejní model AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0db5e-106">This topic assumes that you have already configured the Entity Framework and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0db5e-107">Další informace naleznete v tématu [How to: Manual model and Mapping Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0db5e-107">For more information, see [How to: Manually Define the Model and Mapping Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span></span> <span data-ttu-id="0db5e-108">Postupy v tomto tématu jsou také zahrnuty v tématu [Postupy: ruční konfigurace entity Frameworkho projektu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0db5e-108">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span></span>

> [!NOTE]
> <span data-ttu-id="0db5e-109">Použijete-li průvodce model EDM (Entity Data Model) v projektu sady Visual Studio, automaticky vygeneruje soubor. edmx a nakonfiguruje projekt tak, aby používal Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="0db5e-109">If you use the Entity Data Model Wizard in a Visual Studio project, it automatically generates an .edmx file and configures the project to use the Entity Framework.</span></span> <span data-ttu-id="0db5e-110">Další informace naleznete v tématu [How to: use the model EDM (Entity Data Model) Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0db5e-110">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>

## <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="0db5e-111">Definování připojovacího řetězce Entity Framework</span><span class="sxs-lookup"><span data-stu-id="0db5e-111">To define the Entity Framework connection string</span></span>

- <span data-ttu-id="0db5e-112">Otevřete konfigurační soubor aplikace projektu (App. config) a přidejte následující připojovací řetězec:</span><span class="sxs-lookup"><span data-stu-id="0db5e-112">Open the project's application configuration file (app.config) and add the following connection string:</span></span>

```xml
<connectionStrings>
    <add name="AdventureWorksEntities" 
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

<span data-ttu-id="0db5e-113">Pokud projekt nemá konfigurační soubor aplikace, můžete jej přidat výběrem možnosti **Přidat novou položku** z nabídky **projekt** , výběrem kategorie **Obecné** , výběrem **konfiguračního souboru aplikace**a následným kliknutím na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="0db5e-113">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>

## <a name="see-also"></a><span data-ttu-id="0db5e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0db5e-114">See also</span></span>

- <span data-ttu-id="0db5e-115">[Rychlý start](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0db5e-115">[Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span></span>
- <span data-ttu-id="0db5e-116">[Postupy: vytvoření nového souboru EDMX](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0db5e-116">[How to: Create a New .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span></span>
- <span data-ttu-id="0db5e-117">[ADO.NET model EDM (Entity Data Model) nástroje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0db5e-117">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
