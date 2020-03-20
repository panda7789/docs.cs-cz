---
title: 'Postupy: Definování připojovacího řetězce'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: e5b675a50f883825cce97275048447b79b64cc97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150568"
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="e29b3-102">Postupy: Definování připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="e29b3-102">How to: Define the Connection String</span></span>

<span data-ttu-id="e29b3-103">Toto téma ukazuje, jak definovat připojovací řetězec, který se používá při připojování ke konceptuálnímu modelu.</span><span class="sxs-lookup"><span data-stu-id="e29b3-103">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="e29b3-104">Toto téma je založeno na konceptuálním modelu [AdventureWorks Sales.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e29b3-104">This topic is based on the [AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) conceptual model.</span></span> <span data-ttu-id="e29b3-105">AdventureWorks Prodejní model se používá v celé témata související s úkoly v dokumentaci entity framework.</span><span class="sxs-lookup"><span data-stu-id="e29b3-105">The AdventureWorks Sales Model is used throughout the task-related topics in the Entity Framework documentation.</span></span> <span data-ttu-id="e29b3-106">Toto téma předpokládá, že jste již nakonfigurovali entity framework a definovali obchodní model AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e29b3-106">This topic assumes that you have already configured the Entity Framework and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e29b3-107">Další informace naleznete v [tématu How to: Manually Define the Model and Mapping Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e29b3-107">For more information, see [How to: Manually Define the Model and Mapping Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span></span> <span data-ttu-id="e29b3-108">Postupy v tomto tématu jsou také zahrnuty v [postupech: Ruční konfigurace projektu entity framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e29b3-108">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span></span>

> [!NOTE]
> <span data-ttu-id="e29b3-109">Pokud použijete Průvodce datovým modelem entity v projektu sady Visual Studio, automaticky vygeneruje soubor .edmx a nakonfiguruje projekt tak, aby používal rozhraní Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="e29b3-109">If you use the Entity Data Model Wizard in a Visual Studio project, it automatically generates an .edmx file and configures the project to use the Entity Framework.</span></span> <span data-ttu-id="e29b3-110">Další informace naleznete v [tématu How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e29b3-110">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>

## <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="e29b3-111">Definování připojovacího řetězce Entity Framework</span><span class="sxs-lookup"><span data-stu-id="e29b3-111">To define the Entity Framework connection string</span></span>

- <span data-ttu-id="e29b3-112">Otevřete konfigurační soubor aplikace projektu (app.config) a přidejte následující připojovací řetězec:</span><span class="sxs-lookup"><span data-stu-id="e29b3-112">Open the project's application configuration file (app.config) and add the following connection string:</span></span>

```xml
<connectionStrings>
    <add name="AdventureWorksEntities"
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

<span data-ttu-id="e29b3-113">Pokud projekt nemá konfigurační soubor aplikace, můžete jej přidat tak, že z nabídky **Projekt** vyberete **Přidat novou položku,** vyberete kategorii **Obecné,** vyberete **Konfigurační soubor aplikace**a potom klepnete na tlačítko **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="e29b3-113">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>

## <a name="see-also"></a><span data-ttu-id="e29b3-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="e29b3-114">See also</span></span>

- <span data-ttu-id="e29b3-115">[Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e29b3-115">[Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span></span>
- <span data-ttu-id="e29b3-116">[Postup: Vytvoření nového souboru .edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e29b3-116">[How to: Create a New .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span></span>
- <span data-ttu-id="e29b3-117">[nástroje datového modelu ADO.NET entity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e29b3-117">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
