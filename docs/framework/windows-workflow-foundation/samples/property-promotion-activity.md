---
title: Aktivita propagace vlastnosti
ms.date: 03/30/2017
ms.assetid: 802196b7-1159-4c05-b41b-d3bfdfcc88d9
ms.openlocfilehash: 6e059a0d344e6c62833feaa890c459c141a49673
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43870081"
---
# <a name="property-promotion-activity"></a><span data-ttu-id="4daef-102">Aktivita propagace vlastnosti</span><span class="sxs-lookup"><span data-stu-id="4daef-102">Property Promotion Activity</span></span>
<span data-ttu-id="4daef-103">Tato ukázka poskytuje-ucelené řešení, která se integruje <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkci povýšení přímo do prostředí pro tvorbu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4daef-103">This sample provides an end-to-end solution that integrates the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Promotion feature directly into the workflow authoring experience.</span></span> <span data-ttu-id="4daef-104">Kolekce elementů konfigurace, aktivity pracovního postupu a pracovní postup rozšíření, která zjednodušuje použití funkce povýšení jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="4daef-104">A collection of configuration elements, workflow activities, and workflow extensions that simplify the use of the Promotion feature are provided.</span></span> <span data-ttu-id="4daef-105">Kromě toho vzorek obsahuje jednoduchý pracovní postup, který ukazuje, jak tuto kolekci použít.</span><span class="sxs-lookup"><span data-stu-id="4daef-105">Additionally, the sample contains a simple workflow that demonstrates how to use this collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4daef-106">Ukázky jsou k dispozici pouze pro vzdělávací účely.</span><span class="sxs-lookup"><span data-stu-id="4daef-106">Samples are provided for educational purposes only.</span></span> <span data-ttu-id="4daef-107">Nejsou určeny pro produkční prostředí a nebyly testovány v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="4daef-107">They are not intended for a production environment, and have not been tested in a production environment.</span></span> <span data-ttu-id="4daef-108">Společnost Microsoft neposkytuje pro tyto ukázky technickou podporu.</span><span class="sxs-lookup"><span data-stu-id="4daef-108">Microsoft does not provide technical support for these samples.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4daef-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4daef-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="4daef-110">Inicializovali <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> databáze</span><span class="sxs-lookup"><span data-stu-id="4daef-110">An initialized <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> database</span></span>  
  
-   [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]  
  
## <a name="sample-projects"></a><span data-ttu-id="4daef-111">Ukázkové projekty</span><span class="sxs-lookup"><span data-stu-id="4daef-111">Sample Projects</span></span>  
  
-   <span data-ttu-id="4daef-112">**PropertyPromotionActivity** projekt obsahuje soubory vztahující se na podporu konkrétní konfigurační prvky, aktivity pracovního postupu a rozšíření pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4daef-112">The **PropertyPromotionActivity** project contains files pertaining to the promotion-specific configuration elements, workflow activities, and workflow extensions.</span></span>  
  
-   <span data-ttu-id="4daef-113">**CounterServiceApplication** projekt obsahuje ukázkový pracovní postup, který používá **SqlWorkflowInstanceStorePromotion** projektu.</span><span class="sxs-lookup"><span data-stu-id="4daef-113">The **CounterServiceApplication** project contains a sample workflow that uses the **SqlWorkflowInstanceStorePromotion** project.</span></span>  
  
-   <span data-ttu-id="4daef-114">Skript SQL (PropertyPromotionActivitySQLSample.sql), který musí být spuštěn proti <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> databáze.</span><span class="sxs-lookup"><span data-stu-id="4daef-114">A SQL script (PropertyPromotionActivitySQLSample.sql) that must be run against the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> database.</span></span>  
  
-   <span data-ttu-id="4daef-115">Soubor řešení, která propojuje dvě [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] projekty (`PropertyPromotionActivity.sln`)</span><span class="sxs-lookup"><span data-stu-id="4daef-115">A solution file that links the two [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] projects (`PropertyPromotionActivity.sln`)</span></span>  
  
## <a name="to-set-up-and-run-the-sample"></a><span data-ttu-id="4daef-116">K nastavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="4daef-116">To set up and run the sample</span></span>  
  
1.  <span data-ttu-id="4daef-117">Inicializace databáze trvalosti pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4daef-117">Initialize a workflow persistence database.</span></span>  
  
    1.  <span data-ttu-id="4daef-118">Přejděte do adresáře vzorku (\WF\Basic\Persistence\PropertyPromotionActivity) a spusťte CreateInstanceStore.cmd.</span><span class="sxs-lookup"><span data-stu-id="4daef-118">Navigate to the sample directory (\WF\Basic\Persistence\PropertyPromotionActivity) and run CreateInstanceStore.cmd.</span></span>  
  
    2.  <span data-ttu-id="4daef-119">Pokud nejsou k dispozici oprávnění správce, vytvořte přihlášení systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4daef-119">If Administrator privileges are not available, create a SQL Server login.</span></span> <span data-ttu-id="4daef-120">V SQL Server Management Studio, přejděte na **zabezpečení**, **přihlášení**.</span><span class="sxs-lookup"><span data-stu-id="4daef-120">In SQL Server Management Studio, go to **Security**, **Logins**.</span></span> <span data-ttu-id="4daef-121">Klikněte pravým tlačítkem na **přihlášení** a vytvořte nové přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="4daef-121">Right-click **Logins** and create a new login.</span></span> <span data-ttu-id="4daef-122">Přidejte uživatele seznamu ACL k roli SQL tak, že otevřete **databází**, **třídy InstanceStore**, **zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="4daef-122">Add your ACL user to the SQL role by opening **Databases**, **InstanceStore**, **Security**.</span></span> <span data-ttu-id="4daef-123">Klikněte pravým tlačítkem na **uživatelé** a vyberte **nového uživatele**.</span><span class="sxs-lookup"><span data-stu-id="4daef-123">Right-click **Users** and select **New user**.</span></span> <span data-ttu-id="4daef-124">Nastavte **přihlašovací jméno** uživateli vytvořené výše.</span><span class="sxs-lookup"><span data-stu-id="4daef-124">Set the **Login name** to the user created above.</span></span> <span data-ttu-id="4daef-125">Přidáte uživatele k členství role databáze System.Activities.DurableInstancing.InstanceStoreUsers (a ostatní).</span><span class="sxs-lookup"><span data-stu-id="4daef-125">Add the user to the Database role membership System.Activities.DurableInstancing.InstanceStoreUsers (and others).</span></span> <span data-ttu-id="4daef-126">Všimněte si, že uživatel může existovat už (například objekt dbo uživatele).</span><span class="sxs-lookup"><span data-stu-id="4daef-126">Note that the user might exist already (for example, user dbo).</span></span>  
  
2.  <span data-ttu-id="4daef-127">Otevřete soubor řešení PropertyPromotionActivity.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4daef-127">Open the PropertyPromotionActivity.sln solution file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="4daef-128">Pokud jste vytvořili v úložišti instancí v jiné databáze než místní instalace systému SQL Server Express, je nutné aktualizovat připojovací řetězec databáze.</span><span class="sxs-lookup"><span data-stu-id="4daef-128">If you created the instance store in a database other than a local installation of SQL Server Express, then you must update the database connection string.</span></span> <span data-ttu-id="4daef-129">Příkaz ALTER souboru App.config v části **CounterServiceApplication** tak, že nastavíte hodnotu `connectionString` atribut na `sqlWorkflowInstanceStorePromotion` uzlu tak, aby odkazovala na databáze trvalosti, který byl inicializován v kroku 1.</span><span class="sxs-lookup"><span data-stu-id="4daef-129">Alter the App.config file under the **CounterServiceApplication** by setting the value of the `connectionString` attribute on the `sqlWorkflowInstanceStorePromotion` node so that it points to the persistence database that was initialized in step 1.</span></span>  
  
4.  <span data-ttu-id="4daef-130">Sestavte a spusťte řešení.</span><span class="sxs-lookup"><span data-stu-id="4daef-130">Build and run the solution.</span></span> <span data-ttu-id="4daef-131">Se spustit službu WF čítače a automaticky spustí instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4daef-131">This will start the Counter WF service and automatically start a workflow instance.</span></span>  
  
5.  <span data-ttu-id="4daef-132">Rychle vyberte všechny řádky v [dbo]. Zobrazení [counterService] databáze trvalosti (Toto zobrazení byl přidán spuštěním CreateInstanceStore.cmd v kroku 1).</span><span class="sxs-lookup"><span data-stu-id="4daef-132">Quickly select all the rows in the [dbo].[CounterService] view in your persistence database (this view was added by running CreateInstanceStore.cmd in step 1).</span></span> <span data-ttu-id="4daef-133">Zobrazí se výsledek podobný následujícímu nastavení:</span><span class="sxs-lookup"><span data-stu-id="4daef-133">You will see a result set similar to the following:</span></span>  
  
    |<span data-ttu-id="4daef-134">instanceId</span><span class="sxs-lookup"><span data-stu-id="4daef-134">InstanceId</span></span>|<span data-ttu-id="4daef-135">CounterValue</span><span class="sxs-lookup"><span data-stu-id="4daef-135">CounterValue</span></span>|<span data-ttu-id="4daef-136">CounterValueLastUpdated</span><span class="sxs-lookup"><span data-stu-id="4daef-136">CounterValueLastUpdated</span></span>|  
    |----------------|------------------|-----------------------------|  
    |<span data-ttu-id="4daef-137">2FA2C302-929E-4C0D-8C25-768A3DA20CE5</span><span class="sxs-lookup"><span data-stu-id="4daef-137">2FA2C302-929E-4C0D-8C25-768A3DA20CE5</span></span>|<span data-ttu-id="4daef-138">12</span><span class="sxs-lookup"><span data-stu-id="4daef-138">12</span></span>|<span data-ttu-id="4daef-139">2010-02-18 22:48:01.740</span><span class="sxs-lookup"><span data-stu-id="4daef-139">2010-02-18 22:48:01.740</span></span>|  
  
     <span data-ttu-id="4daef-140">Jak zachovat aktualizace zobrazení, můžete si všimnout, že CounterValue a CounterValueLastUpdated změnit každé dvě sekundy.</span><span class="sxs-lookup"><span data-stu-id="4daef-140">As you keep refreshing the view, you will notice that CounterValue and CounterValueLastUpdated change every two seconds.</span></span> <span data-ttu-id="4daef-141">Jedná se o interval, ve kterém se čítač aktualizuje sám.</span><span class="sxs-lookup"><span data-stu-id="4daef-141">This is the interval at which the counter updates itself.</span></span> <span data-ttu-id="4daef-142">CounterValue a CounterValueLastUpdated představují propagované vlastnosti pro tento pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="4daef-142">CounterValue and CounterValueLastUpdated represent promoted properties for this workflow.</span></span>  
  
## <a name="to-remove-the-sample"></a><span data-ttu-id="4daef-143">Chcete-li odebrat vzorku</span><span class="sxs-lookup"><span data-stu-id="4daef-143">To remove the sample</span></span>  
  
-   <span data-ttu-id="4daef-144">Spusťte RemoveInstanceStore.cmd v adresáři ukázkové (\WF\Basic\Persistence\PropertyPromotionActivity).</span><span class="sxs-lookup"><span data-stu-id="4daef-144">Run RemoveInstanceStore.cmd in the sample directory (\WF\Basic\Persistence\PropertyPromotionActivity).</span></span>  
  
## <a name="understanding-this-sample"></a><span data-ttu-id="4daef-145">Principy tuto ukázku</span><span class="sxs-lookup"><span data-stu-id="4daef-145">Understanding This Sample</span></span>  
 <span data-ttu-id="4daef-146">Ukázka obsahuje dva projekty a soubor SQL:</span><span class="sxs-lookup"><span data-stu-id="4daef-146">The sample contains two projects and an SQL file:</span></span>  
  
-   <span data-ttu-id="4daef-147">**CounterServiceApplication** je konzolová aplikace, který je hostitelem služby jednoduchý čítač WF.</span><span class="sxs-lookup"><span data-stu-id="4daef-147">**CounterServiceApplication** is a console application that hosts a simple Counter WF service.</span></span> <span data-ttu-id="4daef-148">Při přijetí jednosměrná zpráva prostřednictvím `Start` koncový bod, pracovní postup se počítá od 0 až 29 zvyšování hodnoty proměnné čítače každé dvě sekundy.</span><span class="sxs-lookup"><span data-stu-id="4daef-148">Upon receiving a one-way message through the `Start` endpoint, the workflow counts from 0 to 29, incrementing a counter variable every two seconds.</span></span> <span data-ttu-id="4daef-149">Po každý přírůstek čítače pracovní postup se opakuje a propagované vlastnosti jsou aktualizovány v [dbo]. Zobrazení [counterService].</span><span class="sxs-lookup"><span data-stu-id="4daef-149">After every counter increment, the workflow persists, and the promoted properties are updated in the [dbo].[CounterService] view.</span></span> <span data-ttu-id="4daef-150">Při spuštění aplikace konzoly hostitelem služby pracovního postupu a odešle zprávu `Start` koncového bodu, vytváří instanci čítače WF.</span><span class="sxs-lookup"><span data-stu-id="4daef-150">When the console application is run, it hosts the WF service and sends a message to the `Start` endpoint, creating a Counter WF instance.</span></span>  
  
-   <span data-ttu-id="4daef-151">**PropertyPromotionActivity** je knihovny tříd, který obsahuje konfigurační prvky, aktivity pracovního postupu a pracovní postup rozšíření, která **CounterServiceApplication** používá.</span><span class="sxs-lookup"><span data-stu-id="4daef-151">**PropertyPromotionActivity** is a class library that contains the configuration elements, workflow activities, and workflow extensions that the **CounterServiceApplication** uses.</span></span>  
  
-   <span data-ttu-id="4daef-152">**PropertyPromotionActivitySQLSample.sql** vytvoří a přidá zobrazení [dbo]. [ CounterService] do databáze.</span><span class="sxs-lookup"><span data-stu-id="4daef-152">**PropertyPromotionActivitySQLSample.sql** creates and adds the view [dbo].[CounterService] to the database.</span></span>  
  
### <a name="counterserviceapplication"></a><span data-ttu-id="4daef-153">CounterServiceApplication</span><span class="sxs-lookup"><span data-stu-id="4daef-153">CounterServiceApplication</span></span>  
  
#### <a name="using-the-sqlworkflowinstancestorepromotion-configuration-element"></a><span data-ttu-id="4daef-154">Pomocí konfiguračního elementu SqlWorkflowInstanceStorePromotion</span><span class="sxs-lookup"><span data-stu-id="4daef-154">Using the SqlWorkflowInstanceStorePromotion Configuration Element</span></span>  
 <span data-ttu-id="4daef-155">`SqlWorkflowInstanceStorePromotion` Element konfigurace dědí z `SqlWorkflowInstanceStore` prvek konfigurace, ale přidá další konfigurační prvek s názvem `promotionSets`.</span><span class="sxs-lookup"><span data-stu-id="4daef-155">The `SqlWorkflowInstanceStorePromotion` configuration element inherits from the `SqlWorkflowInstanceStore` configuration element, but adds an additional configuration element called `promotionSets`.</span></span> <span data-ttu-id="4daef-156">`promotionSets` Element umožňuje uživateli zadat propagované vlastnosti prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="4daef-156">The `promotionSets` element enables the user to specify promoted properties through configuration.</span></span> <span data-ttu-id="4daef-157">Toto je konfigurační soubor, který se používá v rámci ukázky:</span><span class="sxs-lookup"><span data-stu-id="4daef-157">This is the configuration file that is used by the sample:</span></span>  
  
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
  
 <span data-ttu-id="4daef-158">Zkontrolujte definici [dbo]. Zobrazení [counterService].</span><span class="sxs-lookup"><span data-stu-id="4daef-158">Examine the definition for the [dbo].[CounterService] view.</span></span>  
  
```sql  
create view [dbo].[CounterService] as  
      select [InstanceId],  
 [Value1] as [CounterValue],  
 [Value2] as [CounterValueLastUpdated]  
      from [System.Activities.DurableInstancing].[InstancePromotedProperties]  
      where [PromotionName] = 'CounterService'  
go  
```  
  
 <span data-ttu-id="4daef-159">Pokud instance pracovního postupu budou dál problémy, vloží se řádek do `InstancePromotedProperties` zobrazení pro jednotlivé `PromotionSet` definované v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="4daef-159">When a workflow instance persists, a row is inserted into the `InstancePromotedProperties` view for each `PromotionSet` defined in the configuration.</span></span> <span data-ttu-id="4daef-160">Tento řádek obsahuje všechny propagované vlastnosti `PromotionSet` (přesunuté jednu vlastnost pro každý sloupec).</span><span class="sxs-lookup"><span data-stu-id="4daef-160">This row contains all the promoted properties of the `PromotionSet` (one promoted property per column).</span></span> <span data-ttu-id="4daef-161">To `PromotionSet` označenými pomocí řazené kolekce členů: `InstanceId, PromotionName`.</span><span class="sxs-lookup"><span data-stu-id="4daef-161">This `PromotionSet` is keyed by the tuple: `InstanceId, PromotionName`.</span></span> <span data-ttu-id="4daef-162">V tomto příkladu máme, jeden `PromotionSet` definované v konfiguraci, jehož název atributu je `CounterService`.</span><span class="sxs-lookup"><span data-stu-id="4daef-162">In this sample, we have one `PromotionSet` defined in configuration whose name attribute is `CounterService`.</span></span> <span data-ttu-id="4daef-163">Poznámka: Jak `PromotionName` hodnota sloupce je rovna hodnotě atribut name `PromotionSet` elementu.</span><span class="sxs-lookup"><span data-stu-id="4daef-163">Note how the `PromotionName` column value is equal to the name attribute of the `PromotionSet` element.</span></span>  
  
 <span data-ttu-id="4daef-164">Pořadí `promotedValue` prvky koreluje s umístění propagované vlastnosti `InstancePromotedProperties` zobrazení.</span><span class="sxs-lookup"><span data-stu-id="4daef-164">The order of the `promotedValue` elements correlates with the placement of the promoted properties in the `InstancePromotedProperties` view.</span></span> <span data-ttu-id="4daef-165">`Count` je první `promotedValue` elementu.</span><span class="sxs-lookup"><span data-stu-id="4daef-165">`Count` is the first `promotedValue` element.</span></span> <span data-ttu-id="4daef-166">V důsledku toho je namapována na `Value1` sloupec `InstancePromotedProperties` zobrazení.</span><span class="sxs-lookup"><span data-stu-id="4daef-166">As a result, it is mapped to the `Value1` column in the `InstancePromotedProperties` view.</span></span> <span data-ttu-id="4daef-167">`LastIncrementedAt` je druhý `promotedValue` elementu.</span><span class="sxs-lookup"><span data-stu-id="4daef-167">`LastIncrementedAt` is the second `promotedValue` element.</span></span> <span data-ttu-id="4daef-168">V důsledku toho je namapována na `Value2` sloupec `InstancePromotedProperties` zobrazení.</span><span class="sxs-lookup"><span data-stu-id="4daef-168">As a result, it is mapped to the `Value2` column in the `InstancePromotedProperties` view.</span></span>  
  
#### <a name="using-the-promotevalue-activity"></a><span data-ttu-id="4daef-169">Použití aktivity PromoteValue</span><span class="sxs-lookup"><span data-stu-id="4daef-169">Using the PromoteValue Activity</span></span>  
 <span data-ttu-id="4daef-170">Zkontrolujte soubor CounterService.xamlx v Návrháři Windows Workflow Foundation.</span><span class="sxs-lookup"><span data-stu-id="4daef-170">Examine the CounterService.xamlx file in the Windows Workflow Foundation Designer.</span></span> <span data-ttu-id="4daef-171">Všimněte si, že existují dva speciální aktivity v definici pracovního postupu: `PromoteValue<DateTime>` a `PromoteValue<Int32>`.</span><span class="sxs-lookup"><span data-stu-id="4daef-171">Notice that there are two special activities in the WF definition: `PromoteValue<DateTime>` and `PromoteValue<Int32>`.</span></span>  
  
 <span data-ttu-id="4daef-172">`PromoteValue<Int32>` Aktivita má jeho `Name` člena definovaného jako `Count`.</span><span class="sxs-lookup"><span data-stu-id="4daef-172">The `PromoteValue<Int32>` activity has its `Name` member defined as `Count`.</span></span> <span data-ttu-id="4daef-173">Shoduje se s prvním `promotedValue` element v konfiguraci a má jeho `Value` definován jako `Counter` proměnné pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4daef-173">This matches with the first `promotedValue` element in the configuration, and has its `Value` defined as the `Counter` workflow variable.</span></span> <span data-ttu-id="4daef-174">Když pracovní postup budou dál problémy, `Counter` proměnné pracovního postupu je trvalý jako propagovanou vlastnost do `Value1` sloupec `InstancePromotedProperties` zobrazení.</span><span class="sxs-lookup"><span data-stu-id="4daef-174">When the workflow persists, the `Counter` workflow variable is persisted as a promoted property into the `Value1` column of the `InstancePromotedProperties` view.</span></span>  
  
 <span data-ttu-id="4daef-175">`PromoteValue<DateTime>` Aktivita má jeho `Name` člena definovaného jako `LastIncrementedAt`.</span><span class="sxs-lookup"><span data-stu-id="4daef-175">The `PromoteValue<DateTime>` activity has its `Name` member defined as `LastIncrementedAt`.</span></span> <span data-ttu-id="4daef-176">Shoduje se s druhým `promotedValue` element v konfiguraci a má jeho `Value` definován jako `TimeLastIncremented` proměnné pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4daef-176">This matches with the second `promotedValue` element in the configuration, and has its `Value` defined as the `TimeLastIncremented` workflow variable.</span></span> <span data-ttu-id="4daef-177">To znamená, že když pracovní postup budou dál problémy, hodnota `TimeLastIncremented` proměnné pracovního postupu se nastavit jako trvalý, jako propagovanou vlastnost do `Value2` sloupec `InstancePromotedProperties` zobrazení.</span><span class="sxs-lookup"><span data-stu-id="4daef-177">This means that when the workflow persists, the value for the `TimeLastIncremented` workflow variable will be persisted as a promoted property into the `Value2` column of the `InstancePromotedProperties` view.</span></span>  
  
 <span data-ttu-id="4daef-178">Všimněte si, že `PromotedValue` aktivity také obsahuje logický člena s názvem `ClearExistingPromotedData`.</span><span class="sxs-lookup"><span data-stu-id="4daef-178">Note that the `PromotedValue` activity also has a Boolean member called `ClearExistingPromotedData`.</span></span> <span data-ttu-id="4daef-179">Pokud je tento člen nastaven na `true`, tato akce smaže všechny hodnoty propagované vlastnosti až k danému bodu v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="4daef-179">When this member is set to `true`, this clears all the promoted property values up to that point in the workflow.</span></span> <span data-ttu-id="4daef-180">Například pokud sekvenční aktivity je definován jako následující:</span><span class="sxs-lookup"><span data-stu-id="4daef-180">For example, if a Sequence activity is defined as follows:</span></span>  
  
1.  <span data-ttu-id="4daef-181">PromoteValue {Name = "Count", hodnota = 3}</span><span class="sxs-lookup"><span data-stu-id="4daef-181">PromoteValue { Name = "Count", Value = 3}</span></span>  
  
2.  <span data-ttu-id="4daef-182">PromoteValue {Name = "LastIncrementedAt", hodnota = 1-1-2000}</span><span class="sxs-lookup"><span data-stu-id="4daef-182">PromoteValue {Name = "LastIncrementedAt", Value = 1-1-2000 }</span></span>  
  
3.  <span data-ttu-id="4daef-183">Zachovat</span><span class="sxs-lookup"><span data-stu-id="4daef-183">Persist</span></span>  
  
4.  <span data-ttu-id="4daef-184">PromoteValue {Name = "Count", hodnota = 4, ClearExistingPromotedData = true}</span><span class="sxs-lookup"><span data-stu-id="4daef-184">PromoteValue {Name = "Count", Value = 4, ClearExistingPromotedData = true}</span></span>  
  
5.  <span data-ttu-id="4daef-185">Zachovat</span><span class="sxs-lookup"><span data-stu-id="4daef-185">Persist</span></span>  
  
 <span data-ttu-id="4daef-186">Na druhé trvalého přesunutá hodnota `Count` budou 4.</span><span class="sxs-lookup"><span data-stu-id="4daef-186">On the second persist, the promoted value for `Count` will be 4.</span></span> <span data-ttu-id="4daef-187">Ale přesunutá hodnota `LastIncrementedAt` bude `NULL`.</span><span class="sxs-lookup"><span data-stu-id="4daef-187">However, the promoted value for `LastIncrementedAt` will be `NULL`.</span></span> <span data-ttu-id="4daef-188">Pokud `ClearExistingPromotedData` nebyl nastaven na `true` kroku 4, pak po druhé trvalého přesunutá hodnotu Count by 4.</span><span class="sxs-lookup"><span data-stu-id="4daef-188">If `ClearExistingPromotedData` was not set to `true` for step 4, then after the second persist, the promoted value for Count would be 4.</span></span> <span data-ttu-id="4daef-189">V důsledku toho přesunutá hodnota `LastIncrementedAt` stále by šlo 1-1-2000.</span><span class="sxs-lookup"><span data-stu-id="4daef-189">As a result, the promoted value for `LastIncrementedAt` would still be 1-1-2000.</span></span>  
  
### <a name="propertypromotionactivity"></a><span data-ttu-id="4daef-190">PropertyPromotionActivity</span><span class="sxs-lookup"><span data-stu-id="4daef-190">PropertyPromotionActivity</span></span>  
 <span data-ttu-id="4daef-191">Tato knihovna tříd obsahuje následující veřejných tříd zjednodušení používání <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkci povýšení.</span><span class="sxs-lookup"><span data-stu-id="4daef-191">This class library contains the following public classes to simplify use of the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Promotion feature.</span></span>  
  
#### <a name="promotevalue-class"></a><span data-ttu-id="4daef-192">Třída PromoteValue</span><span class="sxs-lookup"><span data-stu-id="4daef-192">PromoteValue Class</span></span>  
 <span data-ttu-id="4daef-193">Tato třída podporuje jednu vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4daef-193">This class promotes one property.</span></span> <span data-ttu-id="4daef-194">Název propagované vlastnosti by měl odpovídat názvu atributu `promotedValue` element v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="4daef-194">The name of the promoted property should match a name attribute of a `promotedValue` element in the configuration.</span></span> <span data-ttu-id="4daef-195">Tato aktivita se dá použít v Návrháři pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="4daef-195">This activity can be used in the Workflow Designer.</span></span> <span data-ttu-id="4daef-196">Zobrazit CounterServiceApplication pro příklady použití.</span><span class="sxs-lookup"><span data-stu-id="4daef-196">See the CounterServiceApplication for an example usage.</span></span>  
  
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
  
 <span data-ttu-id="4daef-197">ClearExistingPromotedData (Bool)</span><span class="sxs-lookup"><span data-stu-id="4daef-197">ClearExistingPromotedData (Bool)</span></span>  
 <span data-ttu-id="4daef-198">Vymaže všechny hodnoty, které byly přesunuty před této aktivity.</span><span class="sxs-lookup"><span data-stu-id="4daef-198">Clears all values that were promoted before this activity.</span></span>  
  
 <span data-ttu-id="4daef-199">Název (řetězec)</span><span class="sxs-lookup"><span data-stu-id="4daef-199">Name (string)</span></span>  
 <span data-ttu-id="4daef-200">Název, který představuje tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4daef-200">The name that represents this property.</span></span> <span data-ttu-id="4daef-201">Ten by měl odpovídat názvu atributu \<promotedValue > element v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="4daef-201">This should match the name attribute of a \<promotedValue> element in the configuration.</span></span>  
  
 <span data-ttu-id="4daef-202">Hodnota (argument InArgument\<T >)</span><span class="sxs-lookup"><span data-stu-id="4daef-202">Value (InArgument\<T>)</span></span>  
 <span data-ttu-id="4daef-203">Proměnná / hodnota, které chcete uložit ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="4daef-203">The variable / value that you want to store in the column.</span></span>  
  
#### <a name="promotevalues-class"></a><span data-ttu-id="4daef-204">Třída PromoteValues</span><span class="sxs-lookup"><span data-stu-id="4daef-204">PromoteValues Class</span></span>  
 <span data-ttu-id="4daef-205">Podporuje více vlastností.</span><span class="sxs-lookup"><span data-stu-id="4daef-205">Promotes multiple properties.</span></span> <span data-ttu-id="4daef-206">Názvy propagované vlastnosti by měla odpovídat všechny atributy názvu v `promotedValue` prvky v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="4daef-206">The names of the promoted properties should match all name attributes in the `promotedValue` elements in the configuration.</span></span> <span data-ttu-id="4daef-207">Využití je podobný `PromoteValue` aktivity, s výjimkou skutečnost, že ve stejnou dobu může být povýšen víc vlastností.</span><span class="sxs-lookup"><span data-stu-id="4daef-207">Usage is similar to the `PromoteValue` activity, except for the fact that multiple properties can be promoted at the same time.</span></span> <span data-ttu-id="4daef-208">Tuto aktivitu nelze použít v Návrháři pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="4daef-208">This activity cannot be used in the Workflow Designer.</span></span>  
  
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
  
#### <a name="sqlworkflowinstancestorepromotionbehavior"></a><span data-ttu-id="4daef-209">SqlWorkflowInstanceStorePromotionBehavior</span><span class="sxs-lookup"><span data-stu-id="4daef-209">SqlWorkflowInstanceStorePromotionBehavior</span></span>  
 <span data-ttu-id="4daef-210">Je odvozen od `SqlWorkflowInstanceStoreBehavior`.</span><span class="sxs-lookup"><span data-stu-id="4daef-210">Derives from `SqlWorkflowInstanceStoreBehavior`.</span></span> <span data-ttu-id="4daef-211">Tato odvozená třída přidá vlastního účastníka trvalosti (také součástí této knihovny) jako rozšíření pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4daef-211">This derived class adds a custom persistence participant (also a part of this library) as a workflow extension.</span></span> <span data-ttu-id="4daef-212">Implementace předchozích dvou aktivit pracovního postupu závisí na tomto vlastního účastníka trvalosti.</span><span class="sxs-lookup"><span data-stu-id="4daef-212">The implementation of the previous two workflow activities relies on this custom persistence participant.</span></span>  
  
```  
public class SqlWorkflowInstanceStorePromotionBehavior :  
             SqlWorkflowInstanceStoreBehavior, IServiceBehavior  
{  
        public void Promote(string name, IEnumerable<string> promoteAsSqlVariant,  
                            IEnumerable<string> promoteAsBinary)  
  
}  
```  
  
 <span data-ttu-id="4daef-213">Tato knihovna tříd obsahuje také `ConfigurationElement` implementace `SqlWorkflowInstanceStorePromotionElement` a vlastního účastníka trvalosti používají předchozí aktivity povýšení.</span><span class="sxs-lookup"><span data-stu-id="4daef-213">This class library also contains the `ConfigurationElement` implementation for the `SqlWorkflowInstanceStorePromotionElement` and a custom persistence participant used by the previous promotion activities.</span></span>  
  
### <a name="propertypromotionactivitysqlsample"></a><span data-ttu-id="4daef-214">PropertyPromotionActivitySQLSample</span><span class="sxs-lookup"><span data-stu-id="4daef-214">PropertyPromotionActivitySQLSample</span></span>  
 <span data-ttu-id="4daef-215">Tento soubor SQL vytvoří `[dbo].[CounterService]` zobrazení kromě `[InstancePromotedProperties]` zobrazení pro dotazování na všechny instance, které mají sadu CounterService povýšení.</span><span class="sxs-lookup"><span data-stu-id="4daef-215">This SQL file creates a `[dbo].[CounterService]` view in addition to the `[InstancePromotedProperties]` view for querying all instances that have a CounterService Promotion set.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4daef-216">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="4daef-216">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4daef-217">Před pokračováním zkontrolujte následující adresář (výchozí):</span><span class="sxs-lookup"><span data-stu-id="4daef-217">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4daef-218">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="4daef-218">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4daef-219">Tato ukázka se nachází v následujícím adresáři:</span><span class="sxs-lookup"><span data-stu-id="4daef-219">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\PropertyPromotionActivity`  
  
## <a name="see-also"></a><span data-ttu-id="4daef-220">Viz také</span><span class="sxs-lookup"><span data-stu-id="4daef-220">See Also</span></span>  
 [<span data-ttu-id="4daef-221">Hostování AppFabric a ukázky trvalosti</span><span class="sxs-lookup"><span data-stu-id="4daef-221">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
