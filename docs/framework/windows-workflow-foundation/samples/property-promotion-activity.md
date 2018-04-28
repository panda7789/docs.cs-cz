---
title: Vlastnost povýšení aktivity
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 802196b7-1159-4c05-b41b-d3bfdfcc88d9
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 12f7aa4bd10a22a3cd3ea361e32016b95e41e46b
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="property-promotion-activity"></a><span data-ttu-id="93e66-102">Vlastnost povýšení aktivity</span><span class="sxs-lookup"><span data-stu-id="93e66-102">Property Promotion Activity</span></span>
<span data-ttu-id="93e66-103">Tato ukázka poskytuje-komplexní řešení, která integruje <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkci povýšení přímo do pracovního postupu pro tvorbu prostředí.</span><span class="sxs-lookup"><span data-stu-id="93e66-103">This sample provides an end-to-end solution that integrates the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Promotion feature directly into the workflow authoring experience.</span></span> <span data-ttu-id="93e66-104">Soubor konfigurace – elementy, aktivity pracovního postupu a pracovní postup rozšíření, které usnadňují používání funkce povýšení jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="93e66-104">A collection of configuration elements, workflow activities, and workflow extensions that simplify the use of the Promotion feature are provided.</span></span> <span data-ttu-id="93e66-105">Kromě toho vzorek obsahuje jednoduché pracovní postup, který ukazuje, jak lze pomocí této kolekce.</span><span class="sxs-lookup"><span data-stu-id="93e66-105">Additionally, the sample contains a simple workflow that demonstrates how to use this collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93e66-106">Ukázky jsou uvedeny pouze pro vzdělávací účely.</span><span class="sxs-lookup"><span data-stu-id="93e66-106">Samples are provided for educational purposes only.</span></span> <span data-ttu-id="93e66-107">Nejsou určeny pro produkční prostředí a nebyly testovány v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="93e66-107">They are not intended for a production environment, and have not been tested in a production environment.</span></span> <span data-ttu-id="93e66-108">Společnost Microsoft neposkytuje pro tyto ukázky technickou podporu.</span><span class="sxs-lookup"><span data-stu-id="93e66-108">Microsoft does not provide technical support for these samples.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="93e66-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="93e66-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="93e66-110">Inicializovali <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> databáze</span><span class="sxs-lookup"><span data-stu-id="93e66-110">An initialized <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> database</span></span>  
  
-   [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]  
  
## <a name="sample-projects"></a><span data-ttu-id="93e66-111">Ukázkové projekty</span><span class="sxs-lookup"><span data-stu-id="93e66-111">Sample Projects</span></span>  
  
-   <span data-ttu-id="93e66-112">**PropertyPromotionActivity** projekt obsahuje soubory vztahující se k povýšení konkrétní konfigurační prvky, aktivity pracovního postupu a pracovní postup rozšíření.</span><span class="sxs-lookup"><span data-stu-id="93e66-112">The **PropertyPromotionActivity** project contains files pertaining to the promotion-specific configuration elements, workflow activities, and workflow extensions.</span></span>  
  
-   <span data-ttu-id="93e66-113">**CounterServiceApplication** projekt obsahuje ukázkový pracovní postup, který používá **SqlWorkflowInstanceStorePromotion** projektu.</span><span class="sxs-lookup"><span data-stu-id="93e66-113">The **CounterServiceApplication** project contains a sample workflow that uses the **SqlWorkflowInstanceStorePromotion** project.</span></span>  
  
-   <span data-ttu-id="93e66-114">Skript SQL (PropertyPromotionActivitySQLSample.sql), který musí být spuštěn proti <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> databáze.</span><span class="sxs-lookup"><span data-stu-id="93e66-114">A SQL script (PropertyPromotionActivitySQLSample.sql) that must be run against the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> database.</span></span>  
  
-   <span data-ttu-id="93e66-115">Soubor řešení, který odkazuje dva [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] projekty (`PropertyPromotionActivity.sln`)</span><span class="sxs-lookup"><span data-stu-id="93e66-115">A solution file that links the two [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] projects (`PropertyPromotionActivity.sln`)</span></span>  
  
## <a name="to-set-up-and-run-the-sample"></a><span data-ttu-id="93e66-116">Jak nastavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="93e66-116">To set up and run the sample</span></span>  
  
1.  <span data-ttu-id="93e66-117">Inicializuje databázi trvalost pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="93e66-117">Initialize a workflow persistence database.</span></span>  
  
    1.  <span data-ttu-id="93e66-118">Přejděte do adresáře ukázkové (\WF\Basic\Persistence\PropertyPromotionActivity) a spusťte CreateInstanceStore.cmd.</span><span class="sxs-lookup"><span data-stu-id="93e66-118">Navigate to the sample directory (\WF\Basic\Persistence\PropertyPromotionActivity) and run CreateInstanceStore.cmd.</span></span>  
  
    2.  <span data-ttu-id="93e66-119">Pokud nejsou k dispozici oprávnění správce, vytvořte přihlášení systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="93e66-119">If Administrator privileges are not available, create a SQL Server login.</span></span> <span data-ttu-id="93e66-120">V systému SQL Server Management Studio přejděte do **zabezpečení**, **přihlášení**.</span><span class="sxs-lookup"><span data-stu-id="93e66-120">In SQL Server Management Studio, go to **Security**, **Logins**.</span></span> <span data-ttu-id="93e66-121">Klikněte pravým tlačítkem na **přihlášení** a vytvořte nové přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="93e66-121">Right-click **Logins** and create a new login.</span></span> <span data-ttu-id="93e66-122">Přidat seznamu ACL uživatele k roli SQL otevřením **databáze**, **InstanceStore**, **zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="93e66-122">Add your ACL user to the SQL role by opening **Databases**, **InstanceStore**, **Security**.</span></span> <span data-ttu-id="93e66-123">Klikněte pravým tlačítkem na **uživatelé** a vyberte **nového uživatele**.</span><span class="sxs-lookup"><span data-stu-id="93e66-123">Right-click **Users** and select **New user**.</span></span> <span data-ttu-id="93e66-124">Nastavte **přihlašovací jméno** uživateli vytvořili výše.</span><span class="sxs-lookup"><span data-stu-id="93e66-124">Set the **Login name** to the user created above.</span></span> <span data-ttu-id="93e66-125">Přidejte uživatele k členství role databáze System.Activities.DurableInstancing.InstanceStoreUsers (a dalších).</span><span class="sxs-lookup"><span data-stu-id="93e66-125">Add the user to the Database role membership System.Activities.DurableInstancing.InstanceStoreUsers (and others).</span></span> <span data-ttu-id="93e66-126">Všimněte si, že tento uživatel může existovat již (například dbo uživatele).</span><span class="sxs-lookup"><span data-stu-id="93e66-126">Note that the user might exist already (for example, user dbo).</span></span>  
  
2.  <span data-ttu-id="93e66-127">Otevřete soubor řešení PropertyPromotionActivity.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="93e66-127">Open the PropertyPromotionActivity.sln solution file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="93e66-128">Pokud jste vytvořili instanci úložiště do jiné databáze než místní instalace systému SQL Server Express, je nutné aktualizovat připojovací řetězec databáze.</span><span class="sxs-lookup"><span data-stu-id="93e66-128">If you created the instance store in a database other than a local installation of SQL Server Express, then you must update the database connection string.</span></span> <span data-ttu-id="93e66-129">Příkaz ALTER souboru App.config v části **CounterServiceApplication** nastavením hodnotu `connectionString` atributu u `sqlWorkflowInstanceStorePromotion` uzlu tak, aby odkazoval na databázi trvalost, který byl inicializován v kroku 1.</span><span class="sxs-lookup"><span data-stu-id="93e66-129">Alter the App.config file under the **CounterServiceApplication** by setting the value of the `connectionString` attribute on the `sqlWorkflowInstanceStorePromotion` node so that it points to the persistence database that was initialized in step 1.</span></span>  
  
4.  <span data-ttu-id="93e66-130">Sestavení a spuštění řešení.</span><span class="sxs-lookup"><span data-stu-id="93e66-130">Build and run the solution.</span></span> <span data-ttu-id="93e66-131">To se spustit službu čítač WF a automaticky spustí instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="93e66-131">This will start the Counter WF service and automatically start a workflow instance.</span></span>  
  
5.  <span data-ttu-id="93e66-132">Rychle vyberte všechny řádky v [dbo]. Zobrazení [counterService] v databázi trvalost (v tomto zobrazení byl přidán spuštěním CreateInstanceStore.cmd v kroku 1).</span><span class="sxs-lookup"><span data-stu-id="93e66-132">Quickly select all the rows in the [dbo].[CounterService] view in your persistence database (this view was added by running CreateInstanceStore.cmd in step 1).</span></span> <span data-ttu-id="93e66-133">Zobrazí se podobné následujícímu sadě výsledků dotazu:</span><span class="sxs-lookup"><span data-stu-id="93e66-133">You will see a result set similar to the following:</span></span>  
  
    |<span data-ttu-id="93e66-134">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="93e66-134">InstanceId</span></span>|<span data-ttu-id="93e66-135">Přepočtené</span><span class="sxs-lookup"><span data-stu-id="93e66-135">CounterValue</span></span>|<span data-ttu-id="93e66-136">CounterValueLastUpdated</span><span class="sxs-lookup"><span data-stu-id="93e66-136">CounterValueLastUpdated</span></span>|  
    |----------------|------------------|-----------------------------|  
    |<span data-ttu-id="93e66-137">2FA2C302-929E-4C0D-8C25-768A3DA20CE5</span><span class="sxs-lookup"><span data-stu-id="93e66-137">2FA2C302-929E-4C0D-8C25-768A3DA20CE5</span></span>|<span data-ttu-id="93e66-138">12</span><span class="sxs-lookup"><span data-stu-id="93e66-138">12</span></span>|<span data-ttu-id="93e66-139">2010-02-18 22:48:01.740</span><span class="sxs-lookup"><span data-stu-id="93e66-139">2010-02-18 22:48:01.740</span></span>|  
  
     <span data-ttu-id="93e66-140">Jak můžete pokračovat v obnovování zobrazení, si všimnete, že přepočtené a CounterValueLastUpdated změnit každé dvě sekundy.</span><span class="sxs-lookup"><span data-stu-id="93e66-140">As you keep refreshing the view, you will notice that CounterValue and CounterValueLastUpdated change every two seconds.</span></span> <span data-ttu-id="93e66-141">Toto je interval, ve kterém čítač se aktualizuje sám.</span><span class="sxs-lookup"><span data-stu-id="93e66-141">This is the interval at which the counter updates itself.</span></span> <span data-ttu-id="93e66-142">Přepočtené a CounterValueLastUpdated představují propagovaných vlastnosti pro tento pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="93e66-142">CounterValue and CounterValueLastUpdated represent promoted properties for this workflow.</span></span>  
  
## <a name="to-remove-the-sample"></a><span data-ttu-id="93e66-143">Chcete-li odebrat vzorku</span><span class="sxs-lookup"><span data-stu-id="93e66-143">To remove the sample</span></span>  
  
-   <span data-ttu-id="93e66-144">Spusťte RemoveInstanceStore.cmd v adresáři ukázkové (\WF\Basic\Persistence\PropertyPromotionActivity).</span><span class="sxs-lookup"><span data-stu-id="93e66-144">Run RemoveInstanceStore.cmd in the sample directory (\WF\Basic\Persistence\PropertyPromotionActivity).</span></span>  
  
## <a name="understanding-this-sample"></a><span data-ttu-id="93e66-145">Vysvětlení této ukázky</span><span class="sxs-lookup"><span data-stu-id="93e66-145">Understanding This Sample</span></span>  
 <span data-ttu-id="93e66-146">Ukázka obsahuje dva projekty a soubor SQL:</span><span class="sxs-lookup"><span data-stu-id="93e66-146">The sample contains two projects and an SQL file:</span></span>  
  
-   <span data-ttu-id="93e66-147">**CounterServiceApplication** je konzolová aplikace, který je hostitelem služby jednoduchý čítač WF.</span><span class="sxs-lookup"><span data-stu-id="93e66-147">**CounterServiceApplication** is a console application that hosts a simple Counter WF service.</span></span> <span data-ttu-id="93e66-148">Po přijetí jednosměrný zprávy prostřednictvím `Start` koncový bod, pracovní postup počty od 0 do 29, zvyšování proměnnou čítač každé dvě sekundy.</span><span class="sxs-lookup"><span data-stu-id="93e66-148">Upon receiving a one-way message through the `Start` endpoint, the workflow counts from 0 to 29, incrementing a counter variable every two seconds.</span></span> <span data-ttu-id="93e66-149">Po každé přírůstek čítač potrvají pracovního postupu a propagovaných vlastnosti jsou aktualizovány v [dbo]. [CounterService] zobrazení.</span><span class="sxs-lookup"><span data-stu-id="93e66-149">After every counter increment, the workflow persists, and the promoted properties are updated in the [dbo].[CounterService] view.</span></span> <span data-ttu-id="93e66-150">Při spuštění konzolové aplikace hostuje službu WF a odešle zprávu, která `Start` koncový bod, vytvoření instance čítače WF.</span><span class="sxs-lookup"><span data-stu-id="93e66-150">When the console application is run, it hosts the WF service and sends a message to the `Start` endpoint, creating a Counter WF instance.</span></span>  
  
-   <span data-ttu-id="93e66-151">**PropertyPromotionActivity** je knihovna tříd, který obsahuje konfigurační prvky, aktivity pracovního postupu a pracovní postup rozšíření, **CounterServiceApplication** používá.</span><span class="sxs-lookup"><span data-stu-id="93e66-151">**PropertyPromotionActivity** is a class library that contains the configuration elements, workflow activities, and workflow extensions that the **CounterServiceApplication** uses.</span></span>  
  
-   <span data-ttu-id="93e66-152">**PropertyPromotionActivitySQLSample.sql** vytvoří a přidá zobrazení [dbo]. [ CounterService] do databáze.</span><span class="sxs-lookup"><span data-stu-id="93e66-152">**PropertyPromotionActivitySQLSample.sql** creates and adds the view [dbo].[CounterService] to the database.</span></span>  
  
### <a name="counterserviceapplication"></a><span data-ttu-id="93e66-153">CounterServiceApplication</span><span class="sxs-lookup"><span data-stu-id="93e66-153">CounterServiceApplication</span></span>  
  
#### <a name="using-the-sqlworkflowinstancestorepromotion-configuration-element"></a><span data-ttu-id="93e66-154">Pomocí elementu SqlWorkflowInstanceStorePromotion konfigurace</span><span class="sxs-lookup"><span data-stu-id="93e66-154">Using the SqlWorkflowInstanceStorePromotion Configuration Element</span></span>  
 <span data-ttu-id="93e66-155">`SqlWorkflowInstanceStorePromotion` Konfigurace element dědí z `SqlWorkflowInstanceStore` konfigurace elementu, ale přidá další konfiguraci prvek s názvem `promotionSets`.</span><span class="sxs-lookup"><span data-stu-id="93e66-155">The `SqlWorkflowInstanceStorePromotion` configuration element inherits from the `SqlWorkflowInstanceStore` configuration element, but adds an additional configuration element called `promotionSets`.</span></span> <span data-ttu-id="93e66-156">`promotionSets` Prvek umožní uživateli zadat propagovaných vlastnosti prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="93e66-156">The `promotionSets` element enables the user to specify promoted properties through configuration.</span></span> <span data-ttu-id="93e66-157">Toto je konfigurační soubor, který je používán v ukázkovém:</span><span class="sxs-lookup"><span data-stu-id="93e66-157">This is the configuration file that is used by the sample:</span></span>  
  
```xml  
<sqlWorkflowInstanceStorePromotion connectionString ="Data Source=.;Initial Catalog=SqlWorkflowInstanceStoreTest;Integrated Security=True;">  
  <promotionSets>  
    <promotionSet name="CounterService">  
      <promotedValue propertyName="Count"/>  
      <promotedValue propertyName="LastIncrementedAt"/>  
    </promotionSet>  
  </promotionSets>  
</sqlWorkflowInstanceStorePromotion>  
```  
  
 <span data-ttu-id="93e66-158">Zkontrolujte definici [dbo]. [CounterService] zobrazení.</span><span class="sxs-lookup"><span data-stu-id="93e66-158">Examine the definition for the [dbo].[CounterService] view.</span></span>  
  
```sql  
create view [dbo].[CounterService] as  
      select [InstanceId],  
 [Value1] as [CounterValue],  
 [Value2] as [CounterValueLastUpdated]  
      from [System.Activities.DurableInstancing].[InstancePromotedProperties]  
      where [PromotionName] = 'CounterService'  
go  
```  
  
 <span data-ttu-id="93e66-159">Když instanci pracovního postupu přetrvává, vloží se řádek do `InstancePromotedProperties` zobrazení pro každý `PromotionSet` definované v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="93e66-159">When a workflow instance persists, a row is inserted into the `InstancePromotedProperties` view for each `PromotionSet` defined in the configuration.</span></span> <span data-ttu-id="93e66-160">Tento řádek obsahuje všechny propagovaných vlastnosti `PromotionSet` (povýší jednu vlastnost pro každý sloupec).</span><span class="sxs-lookup"><span data-stu-id="93e66-160">This row contains all the promoted properties of the `PromotionSet` (one promoted property per column).</span></span> <span data-ttu-id="93e66-161">To `PromotionSet` je s klíči řazenou kolekci členů: `InstanceId, PromotionName`.</span><span class="sxs-lookup"><span data-stu-id="93e66-161">This `PromotionSet` is keyed by the tuple: `InstanceId, PromotionName`.</span></span> <span data-ttu-id="93e66-162">V této ukázce jsme mít jeden `PromotionSet` definované v konfiguraci, jehož název atributu je `CounterService`.</span><span class="sxs-lookup"><span data-stu-id="93e66-162">In this sample, we have one `PromotionSet` defined in configuration whose name attribute is `CounterService`.</span></span> <span data-ttu-id="93e66-163">Poznámka: Jak `PromotionName` hodnota sloupce je rovna atribut názvu `PromotionSet` elementu.</span><span class="sxs-lookup"><span data-stu-id="93e66-163">Note how the `PromotionName` column value is equal to the name attribute of the `PromotionSet` element.</span></span>  
  
 <span data-ttu-id="93e66-164">Pořadí `promotedValue` elementy koreluje s propagovaných vlastností v umístění `InstancePromotedProperties` zobrazení.</span><span class="sxs-lookup"><span data-stu-id="93e66-164">The order of the `promotedValue` elements correlates with the placement of the promoted properties in the `InstancePromotedProperties` view.</span></span> <span data-ttu-id="93e66-165">`Count` je první `promotedValue` elementu.</span><span class="sxs-lookup"><span data-stu-id="93e66-165">`Count` is the first `promotedValue` element.</span></span> <span data-ttu-id="93e66-166">V důsledku toho je namapovaný na `Value1` sloupec v `InstancePromotedProperties` zobrazení.</span><span class="sxs-lookup"><span data-stu-id="93e66-166">As a result, it is mapped to the `Value1` column in the `InstancePromotedProperties` view.</span></span> <span data-ttu-id="93e66-167">`LastIncrementedAt` je druhá `promotedValue` elementu.</span><span class="sxs-lookup"><span data-stu-id="93e66-167">`LastIncrementedAt` is the second `promotedValue` element.</span></span> <span data-ttu-id="93e66-168">V důsledku toho je namapovaný na `Value2` sloupec v `InstancePromotedProperties` zobrazení.</span><span class="sxs-lookup"><span data-stu-id="93e66-168">As a result, it is mapped to the `Value2` column in the `InstancePromotedProperties` view.</span></span>  
  
#### <a name="using-the-promotevalue-activity"></a><span data-ttu-id="93e66-169">Pomocí aktivity PromoteValue</span><span class="sxs-lookup"><span data-stu-id="93e66-169">Using the PromoteValue Activity</span></span>  
 <span data-ttu-id="93e66-170">Zkontrolujte v souboru CounterService.xamlx v Návrháři Windows Workflow Foundation.</span><span class="sxs-lookup"><span data-stu-id="93e66-170">Examine the CounterService.xamlx file in the Windows Workflow Foundation Designer.</span></span> <span data-ttu-id="93e66-171">Definice pracovního postupu jsou speciální dvě aktivity: `PromoteValue<DateTime>` a `PromoteValue<Int32>`.</span><span class="sxs-lookup"><span data-stu-id="93e66-171">Notice that there are two special activities in the WF definition: `PromoteValue<DateTime>` and `PromoteValue<Int32>`.</span></span>  
  
 <span data-ttu-id="93e66-172">`PromoteValue<Int32>` Aktivita má jeho `Name` člen definován jako `Count`.</span><span class="sxs-lookup"><span data-stu-id="93e66-172">The `PromoteValue<Int32>` activity has its `Name` member defined as `Count`.</span></span> <span data-ttu-id="93e66-173">To odpovídá s prvním `promotedValue` element v konfiguraci a má jeho `Value` definován jako `Counter` proměnné pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="93e66-173">This matches with the first `promotedValue` element in the configuration, and has its `Value` defined as the `Counter` workflow variable.</span></span> <span data-ttu-id="93e66-174">Když pracovní postup potrvají, `Counter` proměnné pracovního postupu je uchován jako propagovaných vlastnost do `Value1` sloupec `InstancePromotedProperties` zobrazení.</span><span class="sxs-lookup"><span data-stu-id="93e66-174">When the workflow persists, the `Counter` workflow variable is persisted as a promoted property into the `Value1` column of the `InstancePromotedProperties` view.</span></span>  
  
 <span data-ttu-id="93e66-175">`PromoteValue<DateTime>` Aktivita má jeho `Name` člen definován jako `LastIncrementedAt`.</span><span class="sxs-lookup"><span data-stu-id="93e66-175">The `PromoteValue<DateTime>` activity has its `Name` member defined as `LastIncrementedAt`.</span></span> <span data-ttu-id="93e66-176">To odpovídá s druhou `promotedValue` element v konfiguraci a má jeho `Value` definován jako `TimeLastIncremented` proměnné pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="93e66-176">This matches with the second `promotedValue` element in the configuration, and has its `Value` defined as the `TimeLastIncremented` workflow variable.</span></span> <span data-ttu-id="93e66-177">To znamená, že když pracovní postup přetrvává, hodnota `TimeLastIncremented` proměnné pracovního postupu bude natrvalo jako propagovaných vlastnost do `Value2` sloupec `InstancePromotedProperties` zobrazení.</span><span class="sxs-lookup"><span data-stu-id="93e66-177">This means that when the workflow persists, the value for the `TimeLastIncremented` workflow variable will be persisted as a promoted property into the `Value2` column of the `InstancePromotedProperties` view.</span></span>  
  
 <span data-ttu-id="93e66-178">Všimněte si, že `PromotedValue` aktivita má také Boolean člena s názvem `ClearExistingPromotedData`.</span><span class="sxs-lookup"><span data-stu-id="93e66-178">Note that the `PromotedValue` activity also has a Boolean member called `ClearExistingPromotedData`.</span></span> <span data-ttu-id="93e66-179">Když je tento člen nastavená na `true`, zruší všechny hodnoty vlastností propagovaných až tento bod v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="93e66-179">When this member is set to `true`, this clears all the promoted property values up to that point in the workflow.</span></span> <span data-ttu-id="93e66-180">Například pokud aktivitu pořadí je definován jako takto:</span><span class="sxs-lookup"><span data-stu-id="93e66-180">For example, if a Sequence activity is defined as follows:</span></span>  
  
1.  <span data-ttu-id="93e66-181">PromoteValue {Name = "Count", hodnota = 3}</span><span class="sxs-lookup"><span data-stu-id="93e66-181">PromoteValue { Name = "Count", Value = 3}</span></span>  
  
2.  <span data-ttu-id="93e66-182">PromoteValue {Name = "LastIncrementedAt", hodnota = 1-1-2000}</span><span class="sxs-lookup"><span data-stu-id="93e66-182">PromoteValue {Name = "LastIncrementedAt", Value = 1-1-2000 }</span></span>  
  
3.  <span data-ttu-id="93e66-183">Zachovat</span><span class="sxs-lookup"><span data-stu-id="93e66-183">Persist</span></span>  
  
4.  <span data-ttu-id="93e66-184">PromoteValue {Name = "Count", hodnota = 4, ClearExistingPromotedData = true}</span><span class="sxs-lookup"><span data-stu-id="93e66-184">PromoteValue {Name = "Count", Value = 4, ClearExistingPromotedData = true}</span></span>  
  
5.  <span data-ttu-id="93e66-185">Zachovat</span><span class="sxs-lookup"><span data-stu-id="93e66-185">Persist</span></span>  
  
 <span data-ttu-id="93e66-186">Na druhé zachovat povýšeného hodnota `Count` 4.</span><span class="sxs-lookup"><span data-stu-id="93e66-186">On the second persist, the promoted value for `Count` will be 4.</span></span> <span data-ttu-id="93e66-187">Ale propagovaných hodnota `LastIncrementedAt` bude `NULL`.</span><span class="sxs-lookup"><span data-stu-id="93e66-187">However, the promoted value for `LastIncrementedAt` will be `NULL`.</span></span> <span data-ttu-id="93e66-188">Pokud `ClearExistingPromotedData` nebyl nastaven na `true` kroku 4, pak po druhé zachovat povýšeného hodnotu pro počet by bylo 4.</span><span class="sxs-lookup"><span data-stu-id="93e66-188">If `ClearExistingPromotedData` was not set to `true` for step 4, then after the second persist, the promoted value for Count would be 4.</span></span> <span data-ttu-id="93e66-189">V důsledku toho propagovaných hodnota `LastIncrementedAt` by však bylo 1-1-2000.</span><span class="sxs-lookup"><span data-stu-id="93e66-189">As a result, the promoted value for `LastIncrementedAt` would still be 1-1-2000.</span></span>  
  
### <a name="propertypromotionactivity"></a><span data-ttu-id="93e66-190">PropertyPromotionActivity</span><span class="sxs-lookup"><span data-stu-id="93e66-190">PropertyPromotionActivity</span></span>  
 <span data-ttu-id="93e66-191">Tato knihovna tříd obsahuje následující veřejné třídy ke zjednodušení použití <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkci povýšení.</span><span class="sxs-lookup"><span data-stu-id="93e66-191">This class library contains the following public classes to simplify use of the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Promotion feature.</span></span>  
  
#### <a name="promotevalue-class"></a><span data-ttu-id="93e66-192">PromoteValue – třída</span><span class="sxs-lookup"><span data-stu-id="93e66-192">PromoteValue Class</span></span>  
 <span data-ttu-id="93e66-193">Tato třída podporuje jednu vlastnost.</span><span class="sxs-lookup"><span data-stu-id="93e66-193">This class promotes one property.</span></span> <span data-ttu-id="93e66-194">Název propagovaných vlastnosti by měl odpovídat názvu atributu `promotedValue` element v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="93e66-194">The name of the promoted property should match a name attribute of a `promotedValue` element in the configuration.</span></span> <span data-ttu-id="93e66-195">Tato aktivita lze použít v Návrháři pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="93e66-195">This activity can be used in the Workflow Designer.</span></span> <span data-ttu-id="93e66-196">V tématu CounterServiceApplication pro příklad použití.</span><span class="sxs-lookup"><span data-stu-id="93e66-196">See the CounterServiceApplication for an example usage.</span></span>  
  
```csharp  
public class PromoteValue<T> : CodeActivity  
{  
    public PromoteValue()  
    {  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public string Name { get; set; }  
    public InArgument<T> Value { get; set; }  
}  
```  
  
 <span data-ttu-id="93e66-197">ClearExistingPromotedData (logická hodnota)</span><span class="sxs-lookup"><span data-stu-id="93e66-197">ClearExistingPromotedData (Bool)</span></span>  
 <span data-ttu-id="93e66-198">Vymaže všechny hodnoty, které byly povýší před této aktivity.</span><span class="sxs-lookup"><span data-stu-id="93e66-198">Clears all values that were promoted before this activity.</span></span>  
  
 <span data-ttu-id="93e66-199">název (string)</span><span class="sxs-lookup"><span data-stu-id="93e66-199">Name (string)</span></span>  
 <span data-ttu-id="93e66-200">Název, který představuje tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="93e66-200">The name that represents this property.</span></span> <span data-ttu-id="93e66-201">Mělo by to odpovídat atribut názvu \<promotedValue > element v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="93e66-201">This should match the name attribute of a \<promotedValue> element in the configuration.</span></span>  
  
 <span data-ttu-id="93e66-202">Hodnota (InArgument\<T >)</span><span class="sxs-lookup"><span data-stu-id="93e66-202">Value (InArgument\<T>)</span></span>  
 <span data-ttu-id="93e66-203">Proměnná / hodnota, které chcete uložit ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="93e66-203">The variable / value that you want to store in the column.</span></span>  
  
#### <a name="promotevalues-class"></a><span data-ttu-id="93e66-204">PromoteValues – třída</span><span class="sxs-lookup"><span data-stu-id="93e66-204">PromoteValues Class</span></span>  
 <span data-ttu-id="93e66-205">Zvýší úroveň více vlastností.</span><span class="sxs-lookup"><span data-stu-id="93e66-205">Promotes multiple properties.</span></span> <span data-ttu-id="93e66-206">Názvy vlastností propagovaných musí odpovídat všechny atributy názvu v `promotedValue` elementy v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="93e66-206">The names of the promoted properties should match all name attributes in the `promotedValue` elements in the configuration.</span></span> <span data-ttu-id="93e66-207">Využití je podobná `PromoteValue` aktivity, s výjimkou fakt, že můžete zvýšit úroveň více vlastností ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="93e66-207">Usage is similar to the `PromoteValue` activity, except for the fact that multiple properties can be promoted at the same time.</span></span> <span data-ttu-id="93e66-208">Tuto aktivitu nelze použít v Návrháři pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="93e66-208">This activity cannot be used in the Workflow Designer.</span></span>  
  
```  
public class PromoteValues : CodeActivity  
{  
    public PromoteValues()  
    {  
        this.ValuesToPromote = new Dictionary<string, InArgument>();  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public IDictionary<string, InArgument> ValuesToPromote { get; set; }  
}  
```  
  
#### <a name="sqlworkflowinstancestorepromotionbehavior"></a><span data-ttu-id="93e66-209">SqlWorkflowInstanceStorePromotionBehavior</span><span class="sxs-lookup"><span data-stu-id="93e66-209">SqlWorkflowInstanceStorePromotionBehavior</span></span>  
 <span data-ttu-id="93e66-210">Odvozená z `SqlWorkflowInstanceStoreBehavior`.</span><span class="sxs-lookup"><span data-stu-id="93e66-210">Derives from `SqlWorkflowInstanceStoreBehavior`.</span></span> <span data-ttu-id="93e66-211">Tato odvozená třída přidá vlastní trvalost účastník (také součástí této knihovny) jako rozšíření pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="93e66-211">This derived class adds a custom persistence participant (also a part of this library) as a workflow extension.</span></span> <span data-ttu-id="93e66-212">Implementace předchozích dvou aktivit pracovního postupu spoléhá na tento účastník vlastní trvalost.</span><span class="sxs-lookup"><span data-stu-id="93e66-212">The implementation of the previous two workflow activities relies on this custom persistence participant.</span></span>  
  
```  
public class SqlWorkflowInstanceStorePromotionBehavior :  
             SqlWorkflowInstanceStoreBehavior, IServiceBehavior  
{  
        public void Promote(string name, IEnumerable<string> promoteAsSqlVariant,  
                            IEnumerable<string> promoteAsBinary)  
  
}  
```  
  
 <span data-ttu-id="93e66-213">Tato knihovna třída také obsahuje `ConfigurationElement` implementace `SqlWorkflowInstanceStorePromotionElement` , která vlastní trvalost používá předchozí aktivity povýšení.</span><span class="sxs-lookup"><span data-stu-id="93e66-213">This class library also contains the `ConfigurationElement` implementation for the `SqlWorkflowInstanceStorePromotionElement` and a custom persistence participant used by the previous promotion activities.</span></span>  
  
### <a name="propertypromotionactivitysqlsample"></a><span data-ttu-id="93e66-214">PropertyPromotionActivitySQLSample</span><span class="sxs-lookup"><span data-stu-id="93e66-214">PropertyPromotionActivitySQLSample</span></span>  
 <span data-ttu-id="93e66-215">Vytvoří tento soubor SQL `[dbo].[CounterService]` zobrazení kromě `[InstancePromotedProperties]` zobrazení pro dotaz na všechny instance, které mají sadu CounterService povýšení.</span><span class="sxs-lookup"><span data-stu-id="93e66-215">This SQL file creates a `[dbo].[CounterService]` view in addition to the `[InstancePromotedProperties]` view for querying all instances that have a CounterService Promotion set.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="93e66-216">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="93e66-216">The samples may already be installed on your computer.</span></span> <span data-ttu-id="93e66-217">Před pokračováním zkontrolovat na následující adresář (výchozí):</span><span class="sxs-lookup"><span data-stu-id="93e66-217">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="93e66-218">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="93e66-218">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="93e66-219">Tato ukázka se nachází v následujícím adresáři:</span><span class="sxs-lookup"><span data-stu-id="93e66-219">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\PropertyPromotionActivity`  
  
## <a name="see-also"></a><span data-ttu-id="93e66-220">Viz také</span><span class="sxs-lookup"><span data-stu-id="93e66-220">See Also</span></span>  
 [<span data-ttu-id="93e66-221">Ukázky trvalosti a hostování AppFabric</span><span class="sxs-lookup"><span data-stu-id="93e66-221">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
