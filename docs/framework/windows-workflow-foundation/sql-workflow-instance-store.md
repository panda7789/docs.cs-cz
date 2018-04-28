---
title: Ukládání Instance pracovního postupu SQL
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8cd2f8a5-4bf8-46ea-8909-c7fdb314fabc
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 11e61e1d702572af10cf4e46b9d1b284022fa56e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="sql-workflow-instance-store"></a><span data-ttu-id="7e1f6-102">Ukládání Instance pracovního postupu SQL</span><span class="sxs-lookup"><span data-stu-id="7e1f6-102">SQL Workflow Instance Store</span></span>
<span data-ttu-id="7e1f6-103">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Se dodává s SQL úložiště Instance pracovního postupu, která umožňuje pracovní postupy pro zachování stavu informace o instancí pracovních postupů v databázi systému SQL Server 2005 nebo SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="7e1f6-103">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ships with the SQL Workflow Instance Store, which allows workflows to persist state information about workflow instances in a SQL Server 2005 or SQL Server 2008 database.</span></span> <span data-ttu-id="7e1f6-104">Tato funkce je primárně implementována ve formě <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> třídy, která je odvozena z abstraktní <xref:System.Runtime.DurableInstancing.InstanceStore> třídu rozhraní trvalost.</span><span class="sxs-lookup"><span data-stu-id="7e1f6-104">This feature is primarily implemented in the form of the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> class, which derives from the abstract <xref:System.Runtime.DurableInstancing.InstanceStore> class of the persistence framework.</span></span> <span data-ttu-id="7e1f6-105">Funkci SQL ukládání Instance pracovního postupu se považuje za trvalost zprostředkovatele SQL, který je konkrétní implementaci trvalost rozhraní API, které hostitel používá k odesílání příkazů trvalost do úložiště.</span><span class="sxs-lookup"><span data-stu-id="7e1f6-105">The SQL Workflow Instance Store feature constitutes a SQL persistence provider, which is a concrete implementation of the persistence API that a host uses to send persistence commands to the store.</span></span>  
  
 <span data-ttu-id="7e1f6-106">Ukládání Instance pracovního postupu SQL podporuje vlastním hostováním pracovních nebo služeb pracovních postupů, které používají <xref:System.Activities.WorkflowApplication> nebo <xref:System.ServiceModel.WorkflowServiceHost> a také služby hostované v používal <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="7e1f6-106">The SQL Workflow Instance Store supports both self-hosted workflows or workflow services that use <xref:System.Activities.WorkflowApplication> or <xref:System.ServiceModel.WorkflowServiceHost> as well as services hosted in WAS using <xref:System.ServiceModel.WorkflowServiceHost>.</span></span> <span data-ttu-id="7e1f6-107">Funkci SQL ukládání Instance pracovního postupu pro samoobslužné hostované služby můžete nakonfigurovat programově pomocí objektového modelu, který je zveřejněný prostřednictvím funkce.</span><span class="sxs-lookup"><span data-stu-id="7e1f6-107">You can configure the SQL Workflow Instance Store feature for self-hosted services programmatically by using the object model exposed by the feature.</span></span> <span data-ttu-id="7e1f6-108">Můžete nakonfigurovat tuto funkci pro služby hostované <xref:System.ServiceModel.WorkflowServiceHost> programově pomocí objektového modelu i taky pomocí konfiguračního souboru XML.</span><span class="sxs-lookup"><span data-stu-id="7e1f6-108">You can configure this feature for services hosted by <xref:System.ServiceModel.WorkflowServiceHost> both programmatically by using the object model and also by using an XML configuration file.</span></span>  
  
 <span data-ttu-id="7e1f6-109">Funkci SQL ukládání Instance pracovního postupu (**SqlWorkflowInstanceStore** třída) neimplementuje <xref:System.ServiceModel.Persistence.PersistenceProviderFactory> a proto nenabízí podporu trvalosti pro trvalé služby WCF mimo pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="7e1f6-109">The SQL Workflow Instance Store feature (**SqlWorkflowInstanceStore** class) does not implement <xref:System.ServiceModel.Persistence.PersistenceProviderFactory> and hence does not offer persistence support for durable non-workflow WCF services.</span></span> <span data-ttu-id="7e1f6-110">Také neimplementuje <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> a proto nenabízí podporu trvalost 3.x pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="7e1f6-110">It also does not implement <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> and hence does not offer persistence support for 3.x workflows.</span></span> <span data-ttu-id="7e1f6-111">Tato funkce podporuje pracovních trvalosti pro pouze WF 4.0 (a novější) a služby pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="7e1f6-111">The feature supports persistence for only WF 4.0 (and later) workflows and workflow services.</span></span> <span data-ttu-id="7e1f6-112">Tato funkce taky nepodporuje žádné databáze než SQL Server 2005 a SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="7e1f6-112">The feature also does not support any databases other than SQL Server 2005 and SQL Server 2008.</span></span>  
  
 <span data-ttu-id="7e1f6-113">Témata v této části popisují vlastnosti a funkce ukládání Instance pracovního postupu SQL a poskytnout podrobné informace o konfiguraci úložiště.</span><span class="sxs-lookup"><span data-stu-id="7e1f6-113">The topics in this section describe properties and features of the SQL Workflow Instance Store and provide you with details on configuring the store.</span></span>  
  
 <span data-ttu-id="7e1f6-114">Windows Server App Fabric poskytuje svou vlastní instanci úložiště a nástrojů zjednodušit konfiguraci a použití instance úložiště.</span><span class="sxs-lookup"><span data-stu-id="7e1f6-114">Windows Server App Fabric provides its own instance store and tooling to simplify the configuration and use of the instance store.</span></span> <span data-ttu-id="7e1f6-115">Další informace najdete v tématu najdete v části [Windows Server App Fabric Instance Store](http://go.microsoft.com/fwlink/?LinkId=201201).</span><span class="sxs-lookup"><span data-stu-id="7e1f6-115">For more information, see see [Windows Server App Fabric Instance Store](http://go.microsoft.com/fwlink/?LinkId=201201).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="7e1f6-116"> Trvalost databáze systému SQL Server App Fabric najdete [trvalost databáze systému SQL Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201202)</span><span class="sxs-lookup"><span data-stu-id="7e1f6-116"> the App Fabric SQL Server Persistence Database see [App Fabric SQL Server Persistence Database](http://go.microsoft.com/fwlink/?LinkId=201202)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7e1f6-117">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="7e1f6-117">In This Section</span></span>  
  
-   [<span data-ttu-id="7e1f6-118">Vlastnosti úložiště instancí pracovních postupů SQL</span><span class="sxs-lookup"><span data-stu-id="7e1f6-118">Properties of SQL Workflow Instance Store</span></span>](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md)  
  
-   [<span data-ttu-id="7e1f6-119">Postupy: Povolení trvalosti SQL pro pracovní postupy a služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="7e1f6-119">How to: Enable SQL Persistence for Workflows and Workflow Services</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)  
  
-   [<span data-ttu-id="7e1f6-120">Aktivace instance</span><span class="sxs-lookup"><span data-stu-id="7e1f6-120">Instance Activation</span></span>](../../../docs/framework/windows-workflow-foundation/instance-activation.md)  
  
-   [<span data-ttu-id="7e1f6-121">Podpora pro dotazy</span><span class="sxs-lookup"><span data-stu-id="7e1f6-121">Support for Queries</span></span>](../../../docs/framework/windows-workflow-foundation/support-for-queries.md)  
  
-   [<span data-ttu-id="7e1f6-122">Rozšiřitelnost úložiště</span><span class="sxs-lookup"><span data-stu-id="7e1f6-122">Store Extensibility</span></span>](../../../docs/framework/windows-workflow-foundation/store-extensibility.md)  
  
-   [<span data-ttu-id="7e1f6-123">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7e1f6-123">Security</span></span>](../../../docs/framework/windows-workflow-foundation/security.md)  
  
-   [<span data-ttu-id="7e1f6-124">Databáze trvalosti SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="7e1f6-124">SQL Server Persistence Database</span></span>](../../../docs/framework/windows-workflow-foundation/sql-server-persistence-database.md)  
  
## <a name="see-also"></a><span data-ttu-id="7e1f6-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e1f6-125">See Also</span></span>  
 [<span data-ttu-id="7e1f6-126">Trvalost ukázky</span><span class="sxs-lookup"><span data-stu-id="7e1f6-126">Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkID=177735)
