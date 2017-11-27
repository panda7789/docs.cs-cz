---
title: "Postupy: dotaz pro netrvalé instance"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 294019b1-c1a7-4b81-a14f-b47c106cd723
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7c83e9364fa599d4356b69fe93ae3eaaa618c2f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-query-for-non-persisted-instances"></a><span data-ttu-id="bda45-102">Postupy: dotaz pro netrvalé instance</span><span class="sxs-lookup"><span data-stu-id="bda45-102">How to: Query for Non-persisted Instances</span></span>
<span data-ttu-id="bda45-103">Když je vytvořena nová instance služby a služby má chování ukládání Instance pracovního postupu SQL definovaný, hostitel služby vytvoří počáteční záznam pro tuto instanci služby v úložišti instance.</span><span class="sxs-lookup"><span data-stu-id="bda45-103">When a new instance of a service is created and the service has the SQL Workflow Instance Store behavior defined, the service host creates a initial entry for that service instance in the instance store.</span></span> <span data-ttu-id="bda45-104">Následně při prvním potrvají instance služby, chování ukládání Instance pracovního postupu SQL uloží aktuální stav instance společně s další data, která je požadována pro aktivaci, obnovení a řízení.</span><span class="sxs-lookup"><span data-stu-id="bda45-104">Subsequently when the service instance persists for the first time, the SQL Workflow Instance Store behavior stores the current instance state together with additional data that is required for activation, recovery, and control.</span></span>  
  
 <span data-ttu-id="bda45-105">Pokud instance není trvalý po vytvoření počáteční položka pro instanci, instance služby se říká, že v netrvalého stavu.</span><span class="sxs-lookup"><span data-stu-id="bda45-105">If an instance is not persisted after the initial entry for the instance is created, the service instance is said to be in the non-persisted state.</span></span> <span data-ttu-id="bda45-106">Všechny instance trvalou služby můžete dotaz a řídí.</span><span class="sxs-lookup"><span data-stu-id="bda45-106">All the persisted service instances can be queried and controlled.</span></span> <span data-ttu-id="bda45-107">Instance služby netrvalé může být dotazována ani řídí.</span><span class="sxs-lookup"><span data-stu-id="bda45-107">Non-persisted service instances can neither be queried nor controlled.</span></span> <span data-ttu-id="bda45-108">Pokud je instance netrvalé je pozastavená kvůli neošetřené výjimce můžete dotaz ale ovládaná nejsou.</span><span class="sxs-lookup"><span data-stu-id="bda45-108">If a non-persisted instance is suspended due to an unhandled exception it can be queried but not controlled.</span></span>  
  
 <span data-ttu-id="bda45-109">Instance trvanlivý služby, které ještě nejsou trvalé zůstanou v netrvalého stavu v následujících scénářích:</span><span class="sxs-lookup"><span data-stu-id="bda45-109">Durable service instances that are not yet persisted remain in a non-persisted state in the following scenarios:</span></span>  
  
-   <span data-ttu-id="bda45-110">Hostitel služby spadne, než se instance trvalé poprvé.</span><span class="sxs-lookup"><span data-stu-id="bda45-110">The service host crashes before the instance persisted for the first time.</span></span> <span data-ttu-id="bda45-111">Původní položka pro instanci zůstává v úložišti instance.</span><span class="sxs-lookup"><span data-stu-id="bda45-111">The initial entry for the instance remains in the instance store.</span></span> <span data-ttu-id="bda45-112">Tato instance není použitelná pro obnovení.</span><span class="sxs-lookup"><span data-stu-id="bda45-112">The instance is not recoverable.</span></span> <span data-ttu-id="bda45-113">Pokud je korelační zpráva doručena, instance zase aktivní.</span><span class="sxs-lookup"><span data-stu-id="bda45-113">If a correlated message arrives, the instance becomes active again.</span></span>  
  
-   <span data-ttu-id="bda45-114">Instance dojde k neošetřené výjimce před nastavené jako trvalé, a poprvé.</span><span class="sxs-lookup"><span data-stu-id="bda45-114">The instance experiences an unhandled exception before it persisted for the first time.</span></span> <span data-ttu-id="bda45-115">Následující scénáře jsou vyvolány</span><span class="sxs-lookup"><span data-stu-id="bda45-115">The following scenarios arise</span></span>  
  
    -   <span data-ttu-id="bda45-116">Pokud hodnota **UnhandledExceptionAction** je nastavena na **Abandon**, informace o nasazení služby je zapsán do instance úložiště a instance je uvolněn z paměti.</span><span class="sxs-lookup"><span data-stu-id="bda45-116">If the value of the **UnhandledExceptionAction** property is set to **Abandon**, the service deployment information is written to the instance store and the instance is unloaded from memory.</span></span> <span data-ttu-id="bda45-117">Instance zůstane v netrvalého stavu v databázi trvalost.</span><span class="sxs-lookup"><span data-stu-id="bda45-117">The instance remains in non-persisted state in the persistence database.</span></span>  
  
    -   <span data-ttu-id="bda45-118">Pokud hodnota **UnhandledExceptionAction** je nastavena na **AbandonAndSuspsend**, informace o nasazení služby je zapsána do databáze trvalosti a stav instance je nastavena na  **Pozastaveno**.</span><span class="sxs-lookup"><span data-stu-id="bda45-118">If the value of the **UnhandledExceptionAction** property is set to **AbandonAndSuspsend**, the service deployment information is written to the persistence database and the instance state is set to **Suspended**.</span></span> <span data-ttu-id="bda45-119">Instance nelze obnovit, zrušena nebo byla ukončena.</span><span class="sxs-lookup"><span data-stu-id="bda45-119">The instance cannot be resumed, canceled, or terminated.</span></span> <span data-ttu-id="bda45-120">Hostitele služby nelze načíst instanci, protože instance není ještě jako trvalý, a proto není úplný záznam databáze pro instanci.</span><span class="sxs-lookup"><span data-stu-id="bda45-120">The service host cannot load the instance because the instance hasn't persisted yet and, hence the database entry for the instance is not complete.</span></span>  
  
    -   <span data-ttu-id="bda45-121">Pokud hodnota **UnhandledExceptionAction** je nastavena na **zrušit** nebo **ukončit**, informace o nasazení služby je zapsán do instance úložiště a stav instance je nastavený na **dokončeno**.</span><span class="sxs-lookup"><span data-stu-id="bda45-121">If the value of the **UnhandledExceptionAction** property is set to **Cancel** or **Terminate**, the service deployment information is written to the instance store and the instance state is set to **Completed**.</span></span>  
  
 <span data-ttu-id="bda45-122">Ukázkové dotazy nenalezl netrvalé instance v databázi SQL trvalosti a z databáze odstranit tyto instance v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="bda45-122">The following sections provide sample queries to find non-persisted instances in the SQL persistence database and to delete these instances from the database.</span></span>  
  
## <a name="to-find-all-instances-not-persisted-yet"></a><span data-ttu-id="bda45-123">Vyhledejte všechny instance není trvalý ještě</span><span class="sxs-lookup"><span data-stu-id="bda45-123">To find all instances not persisted yet</span></span>  
 <span data-ttu-id="bda45-124">Následující dotaz SQL vrátí ID a vytvoření času pro všechny instance, které nejsou trvalé v databázi trvalost ještě.</span><span class="sxs-lookup"><span data-stu-id="bda45-124">The following SQL query returns the ID and creation time for all instances that are not persisted in to the persistence database yet.</span></span>  
  
```  
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0;  
```  
  
## <a name="to-find-all-instances-not-persisted-yet-and-also-not-loaded"></a><span data-ttu-id="bda45-125">Najít všechny instance ještě není trvalý a také není načtená.</span><span class="sxs-lookup"><span data-stu-id="bda45-125">To find all instances not persisted yet and also not loaded</span></span>  
 <span data-ttu-id="bda45-126">Následující dotaz SQL vrátí ID a vytvoření času pro všechny instance, které nejsou trvalé a také se nenačítají.</span><span class="sxs-lookup"><span data-stu-id="bda45-126">The following SQL query returns ID and creation time for all instances that are not persisted and also are not loaded.</span></span>  
  
```  
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and CurrentMachine is NULL;  
```  
  
## <a name="to-find-all-suspended-instances-not-persisted-yet"></a><span data-ttu-id="bda45-127">Najít všechny pozastavené instance není trvalý ještě</span><span class="sxs-lookup"><span data-stu-id="bda45-127">To find all suspended instances not persisted yet</span></span>  
 <span data-ttu-id="bda45-128">Následující dotaz SQL vrátí ID, vytváření, Důvod pozastavení a název pozastavení výjimky pro všechny instance, které nejsou trvalé a taky v pozastaveném stavu.</span><span class="sxs-lookup"><span data-stu-id="bda45-128">The following SQL query returns ID, creation time, suspension reason, and suspension exception name for all instances that are not persisted and also in a suspended state.</span></span>  
  
```  
select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and IsSuspended = 1;  
```  
  
## <a name="to-delete-non-persisted-instances-from-the-persistence-database"></a><span data-ttu-id="bda45-129">Chcete odstranit netrvalé instancí z databáze trvalost</span><span class="sxs-lookup"><span data-stu-id="bda45-129">To delete non-persisted instances from the persistence database</span></span>  
 <span data-ttu-id="bda45-130">Pravidelně zkontrolujte úložiště instance k netrvalé instancí a odeberte instancí z úložiště instance, pokud jste si jistí, že instance neobdrží zprávu korelační.</span><span class="sxs-lookup"><span data-stu-id="bda45-130">You should periodically check the instance store for non-persisted instances and remove instances from the instance store if you are sure that the instance will not receive a correlated message.</span></span> <span data-ttu-id="bda45-131">Například pokud instance byla v databázi několik měsíců a znáte pracovního postupu má obvykle životnost za několik dnů, je bezpečné předpokládají, že se jedná o instanci neinicializovaný, která měla došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="bda45-131">For example, if the instance has been in the database for several months and you know that the workflow typically has a lifetime of a few days, it would be safe to assume that this is an uninitialized instance that had crashed.</span></span>  
  
 <span data-ttu-id="bda45-132">Obecně je bezpečné odstranit netrvalé instancí, které není pozastaven nebo není načtená.</span><span class="sxs-lookup"><span data-stu-id="bda45-132">In general, it is safe to delete non-persisted instances that are not suspended or not loaded.</span></span> <span data-ttu-id="bda45-133">Nedoporučuje se mazat **všechny** netrvalé instance, protože tato instance sada obsahuje instance, které jsou právě vytvořili, ale nejsou nastavené jako trvalé ještě.</span><span class="sxs-lookup"><span data-stu-id="bda45-133">You should not delete **all** the non-persisted instances because this instance set includes instances that are just created but are not persisted yet.</span></span> <span data-ttu-id="bda45-134">Odstraňte pouze netrvalé instancí, které zbyly vzhledem k tomu, že hostitel služby pracovního postupu, který měl načíst instanci způsobila výjimku nebo instance samotného způsobila výjimku.</span><span class="sxs-lookup"><span data-stu-id="bda45-134">You should only delete non-persisted instances that are left over because the workflow service host that had the instance loaded caused an exception or the instance itself caused an exception.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="bda45-135">Odstraňování instancí netrvalé z obchodu instance snižuje velikost úložiště a může zvýšit výkon operací úložiště.</span><span class="sxs-lookup"><span data-stu-id="bda45-135">Deleting non-persisted instances from the instance store decreases the size of the store and may improve the performance of store operations.</span></span>
