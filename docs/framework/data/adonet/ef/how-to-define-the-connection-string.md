---
title: "Postupy: definování připojovací řetězec"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e42fba03b50c0ffd765bbe25ef60b3317ed1b307
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="7a7f9-102">Postupy: definování připojovací řetězec</span><span class="sxs-lookup"><span data-stu-id="7a7f9-102">How to: Define the Connection String</span></span>
<span data-ttu-id="7a7f9-103">Toto téma ukazuje, jak zadat připojovací řetězec, který se používá při připojování k konceptuálního modelu.</span><span class="sxs-lookup"><span data-stu-id="7a7f9-103">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="7a7f9-104">Toto téma je založena na [AdventureWorks prodej](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) konceptuálního modelu.</span><span class="sxs-lookup"><span data-stu-id="7a7f9-104">This topic is based on the [AdventureWorks Sales](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) conceptual model.</span></span> <span data-ttu-id="7a7f9-105">Model organizační jednotky prodej AdventureWorks se používá v rámci úlohy související témata v [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="7a7f9-105">The AdventureWorks Sales Model is used throughout the task-related topics in the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] documentation.</span></span> <span data-ttu-id="7a7f9-106">Toto téma předpokládá, že jste již nakonfigurovali [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] a definované Model prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="7a7f9-106">This topic assumes that you have already configured the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="7a7f9-107">Další informace najdete v tématu [postupy: ruční definování modelu a mapování souborů](http://msdn.microsoft.com/en-us/d4fd6864-f2a1-48f0-aa32-1e318775a99a).</span><span class="sxs-lookup"><span data-stu-id="7a7f9-107">For more information, see [How to: Manually Define the Model and Mapping Files](http://msdn.microsoft.com/en-us/d4fd6864-f2a1-48f0-aa32-1e318775a99a).</span></span> <span data-ttu-id="7a7f9-108">Postupy v tomto tématu jsou také obsaženy v [postupy: ruční konfigurace projektu Entity Framework](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).</span><span class="sxs-lookup"><span data-stu-id="7a7f9-108">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a7f9-109">Pokud použijete [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] průvodce v nástroji [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] projektu, automaticky vygeneruje soubor EDMX a nakonfiguruje projektu pro použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7a7f9-109">If you use the [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] Wizard in a [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] project, it automatically generates an .edmx file and configures the project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="7a7f9-110">Další informace najdete v tématu [postupy: použití průvodce Entity Data Model](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d)</span><span class="sxs-lookup"><span data-stu-id="7a7f9-110">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d)</span></span>  
  
### <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="7a7f9-111">Chcete-li definovat připojovací řetězec Entity Framework</span><span class="sxs-lookup"><span data-stu-id="7a7f9-111">To define the Entity Framework connection string</span></span>  
  
-   <span data-ttu-id="7a7f9-112">Otevřete konfigurační soubor projektu aplikace (app.config) a přidejte následující připojovací řetězec:</span><span class="sxs-lookup"><span data-stu-id="7a7f9-112">Open the project's application configuration file (app.config) and add the following connection string:</span></span>  
  
  
  
     <span data-ttu-id="7a7f9-113">Pokud projekt nemá konfiguračního souboru aplikace, můžete přidat výběrem možnosti **přidat novou položku** z **projektu** nabídce vyberete **Obecné** kategorie, Výběr **konfigurační soubor aplikace**a pak levým na **přidat**.</span><span class="sxs-lookup"><span data-stu-id="7a7f9-113">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a7f9-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a7f9-114">See Also</span></span>  
 [<span data-ttu-id="7a7f9-115">Rychlý start</span><span class="sxs-lookup"><span data-stu-id="7a7f9-115">Quickstart</span></span>](http://msdn.microsoft.com/en-us/0bc534be-789f-4819-b9f6-76e51d961675)  
 [<span data-ttu-id="7a7f9-116">Postupy: vytvoření nového souboru EDMX</span><span class="sxs-lookup"><span data-stu-id="7a7f9-116">How to: Create a New .edmx File</span></span>](http://msdn.microsoft.com/en-us/beb8189e-e51c-4051-839c-9902c224abf2)  
 [<span data-ttu-id="7a7f9-117">Nástroje modelu ADO.NET Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="7a7f9-117">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)
