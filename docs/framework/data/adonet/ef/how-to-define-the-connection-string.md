---
title: 'Postupy: Definování připojovacího řetězce'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: a78158c7553c0b479b935e3b94931313df912c2f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854655"
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="6bbf1-102">Postupy: Definování připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="6bbf1-102">How to: Define the Connection String</span></span>

<span data-ttu-id="6bbf1-103">Toto téma ukazuje, jak definovat připojovací řetězec, který se používá při připojování k koncepčnímu modelu.</span><span class="sxs-lookup"><span data-stu-id="6bbf1-103">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="6bbf1-104">Toto téma je založené na modelu [AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) koncepční model.</span><span class="sxs-lookup"><span data-stu-id="6bbf1-104">This topic is based on the [AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) conceptual model.</span></span> <span data-ttu-id="6bbf1-105">Model prodeje společnosti AdventureWorks se používá v různých tématech souvisejících s úlohami v dokumentaci k Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="6bbf1-105">The AdventureWorks Sales Model is used throughout the task-related topics in the Entity Framework documentation.</span></span> <span data-ttu-id="6bbf1-106">Toto téma předpokládá, že jste již nakonfigurovali Entity Framework a definovali prodejní model AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="6bbf1-106">This topic assumes that you have already configured the Entity Framework and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6bbf1-107">Další informace najdete v tématu [jak: Ručně definujte model a mapovací soubory](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="6bbf1-107">For more information, see [How to: Manually Define the Model and Mapping Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span></span> <span data-ttu-id="6bbf1-108">Postupy v tomto tématu jsou také zahrnuty v [tématu Postupy: Ručně nakonfigurujte Entity Framework projekt](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="6bbf1-108">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span></span>

> [!NOTE]
> <span data-ttu-id="6bbf1-109">Použijete-li průvodce model EDM (Entity Data Model) v projektu sady Visual Studio, automaticky vygeneruje soubor. edmx a nakonfiguruje projekt tak, aby používal Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="6bbf1-109">If you use the Entity Data Model Wizard in a Visual Studio project, it automatically generates an .edmx file and configures the project to use the Entity Framework.</span></span> <span data-ttu-id="6bbf1-110">Další informace najdete v tématu [jak: Použití Průvodce model EDM (Entity Data Model)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6bbf1-110">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))</span></span>

## <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="6bbf1-111">Definování připojovacího řetězce Entity Framework</span><span class="sxs-lookup"><span data-stu-id="6bbf1-111">To define the Entity Framework connection string</span></span>

- <span data-ttu-id="6bbf1-112">Otevřete konfigurační soubor aplikace projektu (App. config) a přidejte následující připojovací řetězec:</span><span class="sxs-lookup"><span data-stu-id="6bbf1-112">Open the project's application configuration file (app.config) and add the following connection string:</span></span>

```xml
<connectionStrings>
    <add name="AdventureWorksEntities" 
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

<span data-ttu-id="6bbf1-113">Pokud projekt nemá konfigurační soubor aplikace, můžete jej přidat výběrem možnosti **Přidat novou položku** z nabídky **projekt** , výběrem kategorie **Obecné** , výběrem **konfiguračního souboru aplikace**a následným kliknutím na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="6bbf1-113">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>

## <a name="see-also"></a><span data-ttu-id="6bbf1-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6bbf1-114">See also</span></span>

- <span data-ttu-id="6bbf1-115">[Rychlý start](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6bbf1-115">[Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span></span>
- <span data-ttu-id="6bbf1-116">[Postupy: Vytvořit nový soubor. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6bbf1-116">[How to: Create a New .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span></span>
- <span data-ttu-id="6bbf1-117">[ADO.NET model EDM (Entity Data Model) nástroje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6bbf1-117">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
