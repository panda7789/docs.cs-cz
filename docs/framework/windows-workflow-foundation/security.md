---
title: "Zabezpečení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 461bc36fd85a158e67c29c3f4ad001997218c824
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="security"></a><span data-ttu-id="1ebcc-102">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="1ebcc-102">Security</span></span>
<span data-ttu-id="1ebcc-103">Ukládání Instance SQL pracovního postupu používá tyto role zabezpečení databáze zabezpečený přístup k informacím stavu instance v databázi trvalost.</span><span class="sxs-lookup"><span data-stu-id="1ebcc-103">The SQL Workflow Instance Store uses the following database security roles to secure access to instance state information in the persistence database.</span></span>  
  
-   <span data-ttu-id="1ebcc-104">**System.Activities.DurableInstancing.InstanceStoreUsers**.</span><span class="sxs-lookup"><span data-stu-id="1ebcc-104">**System.Activities.DurableInstancing.InstanceStoreUsers**.</span></span> <span data-ttu-id="1ebcc-105">Tato role má ke čtení a oprávnění k zápisu do veřejné zobrazení a provádění práva uložené procedury, které se podílejí vytváření, načítání a ukládání instancí.</span><span class="sxs-lookup"><span data-stu-id="1ebcc-105">This role has read and write access to public views and execution rights to stored procedures that are involved in creating, loading and saving instances.</span></span>  
  
-   <span data-ttu-id="1ebcc-106">**System.Activities.DurableInstancing.InstanceStoreObservers**.</span><span class="sxs-lookup"><span data-stu-id="1ebcc-106">**System.Activities.DurableInstancing.InstanceStoreObservers**.</span></span> <span data-ttu-id="1ebcc-107">Tato role má přístup jen pro čtení k veřejné zobrazení.</span><span class="sxs-lookup"><span data-stu-id="1ebcc-107">This role has read-only access to public views.</span></span>  
  
-   <span data-ttu-id="1ebcc-108">**System.Activities.DurableInstancing.WorkflowActivationUsers**.</span><span class="sxs-lookup"><span data-stu-id="1ebcc-108">**System.Activities.DurableInstancing.WorkflowActivationUsers**.</span></span> <span data-ttu-id="1ebcc-109">Tato role má práva provádění uložené procedury, které jsou součástí procesu aktivace instance.</span><span class="sxs-lookup"><span data-stu-id="1ebcc-109">This role has execution rights to stored procedures that are involved in the instance activation process.</span></span> <span data-ttu-id="1ebcc-110">Další informace o aktivaci instance najdete v tématu [Instance aktivace](../../../docs/framework/windows-workflow-foundation/instance-activation.md).</span><span class="sxs-lookup"><span data-stu-id="1ebcc-110">For more information about instance activation, see [Instance Activation](../../../docs/framework/windows-workflow-foundation/instance-activation.md).</span></span> <span data-ttu-id="1ebcc-111">Uživatelský účet, pod kterým obecné hostitele (například službu správy pracovního postupu [!INCLUDE[dublin](../../../includes/dublin-md.md)]) spustí musí být přidaní do této role databáze.</span><span class="sxs-lookup"><span data-stu-id="1ebcc-111">The user account under which a generic host (such as the Workflow Management Service of [!INCLUDE[dublin](../../../includes/dublin-md.md)]) runs should be added to this database role.</span></span>  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="1ebcc-112">zabezpečení pro trvalost úložiště s Windows Server App Fabric, najdete v části [konfigurace zabezpečení pro úložiště trvalosti v App Fabric](http://go.microsoft.com/fwlink/?LinkId=201208)</span><span class="sxs-lookup"><span data-stu-id="1ebcc-112"> security for persistence stores with Windows Server App Fabric, see [Security Configuration for Persistence Stores in App Fabric](http://go.microsoft.com/fwlink/?LinkId=201208)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="1ebcc-113">Klient, který má přístup k vlastní data instance v úložišti instance má přístup k další instance v úložišti stejné instanci.</span><span class="sxs-lookup"><span data-stu-id="1ebcc-113">A client that has access to its own instance data in the instance store has access to all other instances in the same instance store.</span></span> <span data-ttu-id="1ebcc-114">Instance úložiště nepodporuje zadání oprávnění zabezpečení na úrovni instance.</span><span class="sxs-lookup"><span data-stu-id="1ebcc-114">The instance store does not support specifying security permissions at the instance level.</span></span> <span data-ttu-id="1ebcc-115">Doporučujeme vytvořit samostatnou instanci úložiště a mapování různých skupin nebo uživatelů do mají přístup do různých úložišť.</span><span class="sxs-lookup"><span data-stu-id="1ebcc-115">You should create separate instance stores and map different groups/users to have access to different stores.</span></span>
