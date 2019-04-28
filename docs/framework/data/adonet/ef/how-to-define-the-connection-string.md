---
title: 'Postupy: Definování připojovacího řetězce'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: 7fb722acbb13b3502d004978581701cc70118ff8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606101"
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="6a268-102">Postupy: Definování připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="6a268-102">How to: Define the Connection String</span></span>

<span data-ttu-id="6a268-103">Toto téma ukazuje, jak definovat připojovací řetězec, který je použit při připojování ke konceptuálního modelu.</span><span class="sxs-lookup"><span data-stu-id="6a268-103">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="6a268-104">Toto téma vychází [AdventureWorks prodeje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) koncepčního modelu.</span><span class="sxs-lookup"><span data-stu-id="6a268-104">This topic is based on the [AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) conceptual model.</span></span> <span data-ttu-id="6a268-105">AdventureWorks Sales Model se používá v tématech souvisejících s úlohami v rámci [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="6a268-105">The AdventureWorks Sales Model is used throughout the task-related topics in the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] documentation.</span></span> <span data-ttu-id="6a268-106">Toto téma předpokládá, že jste již nakonfigurovali [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] a definovaný Model prodeje AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="6a268-106">This topic assumes that you have already configured the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6a268-107">Další informace najdete v tématu [jak: Ručně definovat modelu a mapování souborů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="6a268-107">For more information, see [How to: Manually Define the Model and Mapping Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span></span> <span data-ttu-id="6a268-108">Postupy v tomto tématu jsou taky součástí [jak: Ruční konfigurace projektu v Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="6a268-108">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span></span>

> [!NOTE]
> <span data-ttu-id="6a268-109">Pokud používáte [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] průvodce v projektu sady Visual Studio automaticky vygeneruje soubor .edmx a nakonfiguruje projekt na používání [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6a268-109">If you use the [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] Wizard in a Visual Studio project, it automatically generates an .edmx file and configures the project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="6a268-110">Další informace najdete v tématu [jak: Použití Průvodce datovým modelem Entity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6a268-110">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))</span></span>

## <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="6a268-111">K definování připojovacího řetězce Entity Framework</span><span class="sxs-lookup"><span data-stu-id="6a268-111">To define the Entity Framework connection string</span></span>

- <span data-ttu-id="6a268-112">Otevřete konfigurační soubor projektu aplikace (app.config) a přidejte následující připojovací řetězec:</span><span class="sxs-lookup"><span data-stu-id="6a268-112">Open the project's application configuration file (app.config) and add the following connection string:</span></span>

```xml
<connectionStrings>
    <add name="AdventureWorksEntities" 
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

<span data-ttu-id="6a268-113">Pokud váš projekt nemá konfiguračního souboru aplikace, můžete výběrem možnosti Přidat **přidat novou položku** z **projektu** nabídce vyberete **Obecné** kategorie, Výběr **konfiguračního souboru aplikace**a pak levým na **přidat**.</span><span class="sxs-lookup"><span data-stu-id="6a268-113">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a268-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a268-114">See also</span></span>

- <span data-ttu-id="6a268-115">[Rychlý start](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6a268-115">[Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span></span>
- <span data-ttu-id="6a268-116">[Postupy: Vytvoření nového souboru EDMX](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6a268-116">[How to: Create a New .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span></span>
- <span data-ttu-id="6a268-117">[Datový Model Entity ADO.NET nástroje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6a268-117">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
