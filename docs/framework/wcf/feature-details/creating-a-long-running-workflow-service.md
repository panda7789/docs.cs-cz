---
title: "Vytvoření dlouhodobé služby pracovního postupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4c39bd04-5b8a-4562-a343-2c63c2821345
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f4204de8c113c2ff553afec934b68f0beeb89580
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="creating-a-long-running-workflow-service"></a><span data-ttu-id="cca69-102">Vytvoření dlouhodobé služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="cca69-102">Creating a Long-running Workflow Service</span></span>
<span data-ttu-id="cca69-103">Toto téma popisuje postup vytvoření dlouhodobé služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="cca69-103">This topic describes how to create a long-running workflow service.</span></span> <span data-ttu-id="cca69-104">Dlouho běžící služeb pracovních postupů mohou spustit pro dlouhou dobu.</span><span class="sxs-lookup"><span data-stu-id="cca69-104">Long running workflow services may run for long periods of time.</span></span> <span data-ttu-id="cca69-105">V určitém okamžiku pracovní postup může se stát, nečinnosti čeká se na některé další informace.</span><span class="sxs-lookup"><span data-stu-id="cca69-105">At some point the workflow may go idle waiting for some additional information.</span></span> <span data-ttu-id="cca69-106">V takovém případě pracovního postupu uložena v databázi SQL a bude odebrán z paměti.</span><span class="sxs-lookup"><span data-stu-id="cca69-106">When this occurs the workflow is persisted to a SQL database and is removed from memory.</span></span> <span data-ttu-id="cca69-107">Jakmile bude k dispozici další informace k instanci pracovního postupu je načteno zpět do paměti a pokračuje v provádění.</span><span class="sxs-lookup"><span data-stu-id="cca69-107">When the additional information becomes available the workflow instance is loaded back into memory and continues executing.</span></span>  <span data-ttu-id="cca69-108">V tomto scénáři jsou implementace velmi zjednodušené řazení systému.</span><span class="sxs-lookup"><span data-stu-id="cca69-108">In this scenario you are implementing a very simplified ordering system.</span></span>  <span data-ttu-id="cca69-109">Klient odešle zprávu počáteční služby pracovního postupu spustit pořadí.</span><span class="sxs-lookup"><span data-stu-id="cca69-109">The client sends an initial message to the workflow service to start the order.</span></span> <span data-ttu-id="cca69-110">Vrátí pořadí ID klienta.</span><span class="sxs-lookup"><span data-stu-id="cca69-110">It returns an order ID to the client.</span></span> <span data-ttu-id="cca69-111">V tomto okamžiku služby pracovního postupu se čeká na další zprávu od klienta a klient se přepne do stavu nečinnosti a uložena v databázi systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cca69-111">At this point the workflow service is waiting for another message from the client and goes into the idle state and is persisted to a SQL Server database.</span></span>  <span data-ttu-id="cca69-112">Když klient odešle na další zprávu pořadí položku, služby pracovního postupu je načteno zpět do paměti a dokončí zpracování pořadí.</span><span class="sxs-lookup"><span data-stu-id="cca69-112">When the client sends the next message to order an item, the workflow service is loaded back into memory and finishes processing the order.</span></span> <span data-ttu-id="cca69-113">V ukázce kódu vrátí řetězec s informacemi o tom, že položka se přidal do pořadí.</span><span class="sxs-lookup"><span data-stu-id="cca69-113">In the code sample it returns a string stating the item has been added to the order.</span></span> <span data-ttu-id="cca69-114">Ukázka kódu není určené jako aplikace skutečných technologie, ale spíš jednoduchý příklad, který znázorňuje dlouhotrvající služeb pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="cca69-114">The code sample is not meant to be a real world application of the technology, but rather a simple sample that illustrates long running workflow services.</span></span> <span data-ttu-id="cca69-115">Toto téma předpokládá, že víte, jak vytvořit [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] projekty a řešení.</span><span class="sxs-lookup"><span data-stu-id="cca69-115">This topic assumes you know how to create [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] projects and solutions.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cca69-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cca69-116">Prerequisites</span></span>  
 <span data-ttu-id="cca69-117">Musíte mít nainstalovaný pomocí tohoto průvodce použijte následující software:</span><span class="sxs-lookup"><span data-stu-id="cca69-117">You must have the following software installed to use this walkthrough:</span></span>  
  
1.  <span data-ttu-id="cca69-118">Microsoft SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="cca69-118">Microsoft SQL Server 2008</span></span>  
  
2.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
3.  <span data-ttu-id="cca69-119">Microsoft[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cca69-119">Microsoft  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]</span></span>  
  
4.  <span data-ttu-id="cca69-120">Jste obeznámeni s použitím technologie WCF a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] a vědět, jak vytvářet projekty nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="cca69-120">You are familiar with WCF and [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] and know how to create projects/solutions.</span></span>  
  
### <a name="to-setup-the-sql-database"></a><span data-ttu-id="cca69-121">K nastavení databáze SQL</span><span class="sxs-lookup"><span data-stu-id="cca69-121">To Setup the SQL Database</span></span>  
  
1.  <span data-ttu-id="cca69-122">V pořadí pro instance služby pracovního postupu na nastavit jako trvalý, musí mít nainstalovaný Microsoft SQL Server a je nutné nakonfigurovat databázi k ukládání instancí trvalou pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="cca69-122">In order for workflow service instances to be persisted you must have Microsoft SQL Server installed and you must configure a database to store the persisted workflow instances.</span></span> <span data-ttu-id="cca69-123">Spusťte Microsoft SQL Management Studio kliknutím **spustit** tlačítko výběru **všechny programy**, **Microsoft SQL Server 2008**, a **Microsoft SQL Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="cca69-123">Run Microsoft SQL Management Studio by clicking the **Start** button, selecting **All Programs**, **Microsoft SQL Server 2008**, and **Microsoft SQL Management Studio**.</span></span>  
  
2.  <span data-ttu-id="cca69-124">Klikněte **Connect** tlačítko a přihlaste se k instanci systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="cca69-124">Click the **Connect** button to log on to the SQL Server instance</span></span>  
  
3.  <span data-ttu-id="cca69-125">Klikněte pravým tlačítkem na **databáze** v zobrazení stromu a vyberte **nové databáze...**</span><span class="sxs-lookup"><span data-stu-id="cca69-125">Right click **Databases** in the tree view and select **New Database..**</span></span> <span data-ttu-id="cca69-126">Chcete-li vytvořit novou databázi názvem `SQLPersistenceStore`.</span><span class="sxs-lookup"><span data-stu-id="cca69-126">to create a new database called `SQLPersistenceStore`.</span></span>  
  
4.  <span data-ttu-id="cca69-127">Spusťte soubor skriptu SqlWorkflowInstanceStoreSchema.sql umístěný v adresáři C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en v databázi SQLPersistenceStore nastavit schémata potřebné databáze.</span><span class="sxs-lookup"><span data-stu-id="cca69-127">Run the SqlWorkflowInstanceStoreSchema.sql script file located in the C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en directory on the SQLPersistenceStore database to set up the needed database schemas.</span></span>  
  
5.  <span data-ttu-id="cca69-128">Spusťte soubor skriptu SqlWorkflowInstanceStoreLogic.sql umístěný v adresáři C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en v databázi SQLPersistenceStore nastavit logice potřebné databáze.</span><span class="sxs-lookup"><span data-stu-id="cca69-128">Run the SqlWorkflowInstanceStoreLogic.sql script file located in the C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en directory on the SQLPersistenceStore database to set up the needed database logic.</span></span>  
  
### <a name="to-create-the-web-hosted-workflow-service"></a><span data-ttu-id="cca69-129">Chcete-li vytvořit Web hostované služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="cca69-129">To Create the Web Hosted Workflow Service</span></span>  
  
1.  <span data-ttu-id="cca69-130">Vytvořte prázdnou [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] řešení, pojmenujte ji `OrderProcessing`.</span><span class="sxs-lookup"><span data-stu-id="cca69-130">Create an empty [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] solution, name it `OrderProcessing`.</span></span>  
  
2.  <span data-ttu-id="cca69-131">Přidejte nový [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] projekt aplikace služby pracovního postupu s názvem `OrderService` k řešení.</span><span class="sxs-lookup"><span data-stu-id="cca69-131">Add a new [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Workflow Service Application project called `OrderService` to the solution.</span></span>  
  
3.  <span data-ttu-id="cca69-132">V dialogovém okně Vlastnosti projektu, vyberte **webové** kartě.</span><span class="sxs-lookup"><span data-stu-id="cca69-132">In the project properties dialog, select the **Web** tab.</span></span>  
  
    1.  <span data-ttu-id="cca69-133">V části **spustit akci** vyberte **konkrétní stránky** a zadejte `Service1.xamlx`.</span><span class="sxs-lookup"><span data-stu-id="cca69-133">Under **Start Action** select **Specific Page** and specify `Service1.xamlx`.</span></span>  
  
         <span data-ttu-id="cca69-134">![Vlastnosti webového projektu služby pracovního postupu](../../../../docs/framework/wcf/feature-details/media/startaction.png "StartAction")</span><span class="sxs-lookup"><span data-stu-id="cca69-134">![Workflow Service Project Web Properties](../../../../docs/framework/wcf/feature-details/media/startaction.png "StartAction")</span></span>  
  
    2.  <span data-ttu-id="cca69-135">V části **servery** vyberte **použití místního webového serveru IIS**.</span><span class="sxs-lookup"><span data-stu-id="cca69-135">Under **Servers** select **Use Local IIS Web server**.</span></span>  
  
         <span data-ttu-id="cca69-136">![Nastavení místního webového serveru](../../../../docs/framework/wcf/feature-details/media/uselocalwebserver.png "UseLocalWebServer")</span><span class="sxs-lookup"><span data-stu-id="cca69-136">![Local Web Server Settings](../../../../docs/framework/wcf/feature-details/media/uselocalwebserver.png "UseLocalWebServer")</span></span>  
  
        > [!WARNING]
        >  <span data-ttu-id="cca69-137">Je nutné spustit [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] v režimu správce, aby se toto nastavení.</span><span class="sxs-lookup"><span data-stu-id="cca69-137">You must run [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] in administrator mode to make this setting.</span></span>  
  
         <span data-ttu-id="cca69-138">Tyto dva kroky konfigurace projekt služby pracovního postupu, který má být hostované službou IIS.</span><span class="sxs-lookup"><span data-stu-id="cca69-138">These two steps configure the workflow service project to be hosted by IIS.</span></span>  
  
4.  <span data-ttu-id="cca69-139">Otevřete `Service1.xamlx` Pokud není již otevřete a odstranit existující **ReceiveRequest** a **SendResponse** aktivity.</span><span class="sxs-lookup"><span data-stu-id="cca69-139">Open `Service1.xamlx` if it is not open already and delete the existing **ReceiveRequest** and **SendResponse** activities.</span></span>  
  
5.  <span data-ttu-id="cca69-140">Vyberte **sekvenční služby** aktivity a klikněte na tlačítko **proměnné** propojit a přidejte proměnné vidět na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="cca69-140">Select the **Sequential Service** activity and click the **Variables** link and add the variables shown in the following illustration.</span></span> <span data-ttu-id="cca69-141">Díky tomuto přidá některé proměnné, které se použijí později v rámci služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="cca69-141">Doing this adds some variables that will be used later on in the workflow service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cca69-142">Pokud CorrelationHandle v proměnné typu rozevíracího seznamu není, vyberte **Procházet pro typy** z rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="cca69-142">If CorrelationHandle is not in the Variable Type drop-down, select **Browse for types** from the drop-down.</span></span> <span data-ttu-id="cca69-143">Zadejte CorrelationHandle v **název typu** CorrelationHandle vyberte ze seznamu a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="cca69-143">Type CorrelationHandle in the **Type name** box, select CorrelationHandle from the listbox and click **OK**.</span></span>  
  
     <span data-ttu-id="cca69-144">![Přidání proměnné](../../../../docs/framework/wcf/feature-details/media/addvariables.gif "AddVariables")</span><span class="sxs-lookup"><span data-stu-id="cca69-144">![Add Variables](../../../../docs/framework/wcf/feature-details/media/addvariables.gif "AddVariables")</span></span>  
  
6.  <span data-ttu-id="cca69-145">Přetáhnout myší **ReceiveAndSendReply** šablony aktivit do **sekvenční služby** aktivity.</span><span class="sxs-lookup"><span data-stu-id="cca69-145">Drag and drop a **ReceiveAndSendReply** activity template into the **Sequential Service** activity.</span></span> <span data-ttu-id="cca69-146">Tuto sadu aktivit, bude přijímat zprávu od klienta a odesílání odpovědí zpět.</span><span class="sxs-lookup"><span data-stu-id="cca69-146">This set of activities will receive a message from a client and send a reply back.</span></span>  
  
    1.  <span data-ttu-id="cca69-147">Vyberte **Receive** aktivity a sadu vlastností zvýrazněná na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="cca69-147">Select the **Receive** activity and set the properties highlighted in the following illustration.</span></span>  
  
         <span data-ttu-id="cca69-148">![Sada přijímat vlastnosti aktivity](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties.png "SetReceiveProperties")</span><span class="sxs-lookup"><span data-stu-id="cca69-148">![Set Receive Activity Properties](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties.png "SetReceiveProperties")</span></span>  
  
         <span data-ttu-id="cca69-149">Vlastnost DisplayName nastaví název zobrazený Receive aktivity v návrháři.</span><span class="sxs-lookup"><span data-stu-id="cca69-149">The DisplayName property sets the name displayed for the Receive activity in the designer.</span></span> <span data-ttu-id="cca69-150">Vlastnosti ServiceContractName a OperationName zadejte název kontraktu služby a operace, které jsou implementované pomocí aktivity Receive.</span><span class="sxs-lookup"><span data-stu-id="cca69-150">The ServiceContractName and OperationName properties specify the name of the service contract and operation that are implemented by the Receive activity.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="cca69-151">použití kontraktů v pracovním postupu služeb najdete v tématu [použití kontraktů v pracovním postupu](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="cca69-151"> how contracts are used in Workflow services see [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>  
  
    2.  <span data-ttu-id="cca69-152">Klikněte **definovat...**  odkaz **ReceiveStartOrder** aktivity a nastavte vlastnosti zobrazené na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="cca69-152">Click the **Define...** link in the **ReceiveStartOrder** activity and set the properties shown in the following illustration.</span></span>  <span data-ttu-id="cca69-153">Všimněte si, že **parametry** přepínače, parametr s názvem `p_customerName` je vázána `customerName` proměnné.</span><span class="sxs-lookup"><span data-stu-id="cca69-153">Notice that the **Parameters** radio button is selected, a parameter named `p_customerName` is bound to the `customerName` variable.</span></span> <span data-ttu-id="cca69-154">Tím se nakonfiguruje **Receive** aktivity přijímat některá data a vytvoření vazby dat k lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="cca69-154">This configures the **Receive** activity to receive some data and bind that data to local variables.</span></span>  
  
         <span data-ttu-id="cca69-155">![Nastavení dat přijatých aktivitou Receive](../../../../docs/framework/wcf/feature-details/media/setreceivecontent.png "SetReceiveContent")</span><span class="sxs-lookup"><span data-stu-id="cca69-155">![Setting the data received by the Receive activity](../../../../docs/framework/wcf/feature-details/media/setreceivecontent.png "SetReceiveContent")</span></span>  
  
    3.  <span data-ttu-id="cca69-156">Vyberte **SendReplyToReceive** aktivity a nastavte vlastnost zvýrazněná vidět na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="cca69-156">Select The **SendReplyToReceive** activity and set the highlighted property shown in the following illustration.</span></span>  
  
         <span data-ttu-id="cca69-157">![Nastavení vlastností aktivity SendReply](../../../../docs/framework/wcf/feature-details/media/setreplyproperties.png "SetReplyProperties")</span><span class="sxs-lookup"><span data-stu-id="cca69-157">![Setting the properties of the SendReply activity](../../../../docs/framework/wcf/feature-details/media/setreplyproperties.png "SetReplyProperties")</span></span>  
  
    4.  <span data-ttu-id="cca69-158">Klikněte **definovat...**  odkaz **SendReplyToStartOrder** aktivity a nastavte vlastnosti zobrazené na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="cca69-158">Click the **Define...** link in the **SendReplyToStartOrder** activity and set the properties shown in the following illustration.</span></span> <span data-ttu-id="cca69-159">Všimněte si, že **parametry** přepínače; parametr s názvem `p_orderId` je vázána `orderId` proměnné.</span><span class="sxs-lookup"><span data-stu-id="cca69-159">Notice that the **Parameters** radio button is selected; a parameter named `p_orderId` is bound to the `orderId` variable.</span></span> <span data-ttu-id="cca69-160">Toto nastavení určuje, že aktivita SendReplyToStartOrder vrátí hodnotu typu řetězec na volajícího.</span><span class="sxs-lookup"><span data-stu-id="cca69-160">This setting specifies that the SendReplyToStartOrder activity will return a value of type string to the caller.</span></span>  
  
         <span data-ttu-id="cca69-161">![Konfigurace obsahu data aktivit SendReply](../../../../docs/framework/wcf/feature-details/media/setreplycontent.png "SetReplyContent")</span><span class="sxs-lookup"><span data-stu-id="cca69-161">![Configuring the SendReply activity content data](../../../../docs/framework/wcf/feature-details/media/setreplycontent.png "SetReplyContent")</span></span>  
  
    5.  <span data-ttu-id="cca69-162">Přetáhnout myší přiřadit aktivitu v rozmezí **Receive** a **SendReply** aktivity a nastavte vlastnosti, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="cca69-162">Drag and drop an Assign activity in between the **Receive** and **SendReply** activities and set the properties as shown in the following illustration:</span></span>  
  
         <span data-ttu-id="cca69-163">![Přidání aktivity přiřadit](../../../../docs/framework/wcf/feature-details/media/addassign.png "AddAssign")</span><span class="sxs-lookup"><span data-stu-id="cca69-163">![Adding an assign activity](../../../../docs/framework/wcf/feature-details/media/addassign.png "AddAssign")</span></span>  
  
         <span data-ttu-id="cca69-164">Tím se vytvoří nové ID pořadí a umístí hodnota proměnné orderId.</span><span class="sxs-lookup"><span data-stu-id="cca69-164">This creates a new order ID and places the value in the orderId variable.</span></span>  
  
    6.  <span data-ttu-id="cca69-165">Vyberte **ReplyToStartOrder** aktivity.</span><span class="sxs-lookup"><span data-stu-id="cca69-165">Select the **ReplyToStartOrder** activity.</span></span> <span data-ttu-id="cca69-166">V okně vlastností klikněte na tlačítko se třemi tečkami pro **CorrelationInitializers**.</span><span class="sxs-lookup"><span data-stu-id="cca69-166">In the properties window click the ellipsis button for **CorrelationInitializers**.</span></span> <span data-ttu-id="cca69-167">Vyberte **přidat inicializátoru** odkaz, zadejte `orderIdHandle` do textového pole inicializátoru vyberte inicializátoru korelace dotazu pro typ korelace a vyberte p_orderId pod rozevíracím dotazů XPATH.</span><span class="sxs-lookup"><span data-stu-id="cca69-167">Select the **Add initializer** link, enter `orderIdHandle` in the Initializer text box, select Query correlation initializer for the Correlation type, and select p_orderId under the XPATH Queries dropdown box.</span></span> <span data-ttu-id="cca69-168">Tato nastavení znázorňuje následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="cca69-168">These settings are shown in the following illustration.</span></span> <span data-ttu-id="cca69-169">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="cca69-169">Click **OK**.</span></span>  <span data-ttu-id="cca69-170">To inicializuje korelace mezi klientem a tuto instanci služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="cca69-170">This initializes a correlation between the client and this instance of the workflow service.</span></span> <span data-ttu-id="cca69-171">Když zprávu obsahující toto pořadí je přijata ID se směruje na tuto instanci služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="cca69-171">When a message containing this order ID is received it is routed to this instance of the workflow service.</span></span>  
  
         <span data-ttu-id="cca69-172">![Přidání inicializátoru korelace](../../../../docs/framework/wcf/feature-details/media/addcorrelationinitializers.png "AddCorrelationInitializers")</span><span class="sxs-lookup"><span data-stu-id="cca69-172">![Adding a correlation initializer](../../../../docs/framework/wcf/feature-details/media/addcorrelationinitializers.png "AddCorrelationInitializers")</span></span>  
  
7.  <span data-ttu-id="cca69-173">Přetáhnout myší jiné **ReceiveAndSendReply** aktivity na konci pracovního postupu (mimo **pořadí** obsahující první **Receive** a  **SendReply** aktivit).</span><span class="sxs-lookup"><span data-stu-id="cca69-173">Drag and drop another **ReceiveAndSendReply** activity to the end of the workflow (outside the **Sequence** containing the first **Receive** and **SendReply** activities).</span></span> <span data-ttu-id="cca69-174">To bude přijímat o druhou zprávu odesílaný klientem a reagovat na ni.</span><span class="sxs-lookup"><span data-stu-id="cca69-174">This will receive the second message sent by the client and respond to it.</span></span>  
  
    1.  <span data-ttu-id="cca69-175">Vyberte **pořadí** obsahující nově přidaný **Receive** a **SendReply** aktivit a klikněte na tlačítko **proměnné** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="cca69-175">Select the **Sequence** that contains the newly added **Receive** and **SendReply** activities and click the **Variables** button.</span></span> <span data-ttu-id="cca69-176">Přidejte proměnnou vyznačené na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="cca69-176">Add the variable highlighted in the following illustration:</span></span>  
  
         <span data-ttu-id="cca69-177">![Přidání nové proměnné](../../../../docs/framework/wcf/feature-details/media/addorderitemidvariable.png "AddOrderItemIdVariable")</span><span class="sxs-lookup"><span data-stu-id="cca69-177">![Adding new variables](../../../../docs/framework/wcf/feature-details/media/addorderitemidvariable.png "AddOrderItemIdVariable")</span></span>  
  
    2.  <span data-ttu-id="cca69-178">Vyberte **Receive** aktivity a nastavte vlastnosti zobrazené na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="cca69-178">Select the **Receive** activity and set the properties shown in the following illustration:</span></span>  
  
         <span data-ttu-id="cca69-179">![Nastavit vlastnosti jsou Receive](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties2.png "SetReceiveProperties2")</span><span class="sxs-lookup"><span data-stu-id="cca69-179">![Set the Receive acitivity properties](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties2.png "SetReceiveProperties2")</span></span>  
  
    3.  <span data-ttu-id="cca69-180">Klikněte **definovat...**  na odkaz v **ReceiveAddItem** aktivity a přidání parametrů vidět na následujícím obrázku: tím se nakonfiguruje tak, aby přijímal dva parametry, kód a ID položky řazen aktivitu příjmu.</span><span class="sxs-lookup"><span data-stu-id="cca69-180">Click the **Define...** link in the **ReceiveAddItem** activity and add the parameters shown in the following illustration:This configures the receive activity to accept two parameters, the order ID and the ID of the item being ordered.</span></span>  
  
         <span data-ttu-id="cca69-181">![Určení parametrů pro druhý přijímat](../../../../docs/framework/wcf/feature-details/media/addreceive2parameters.png "AddReceive2Parameters")</span><span class="sxs-lookup"><span data-stu-id="cca69-181">![Specifying parameters for the second receive](../../../../docs/framework/wcf/feature-details/media/addreceive2parameters.png "AddReceive2Parameters")</span></span>  
  
    4.  <span data-ttu-id="cca69-182">Klikněte **CorrelateOn** třemi tečkami tlačítko a zadejte `orderIdHandle`.</span><span class="sxs-lookup"><span data-stu-id="cca69-182">Click the **CorrelateOn** ellipsis button and enter `orderIdHandle`.</span></span> <span data-ttu-id="cca69-183">V části **dotazů XPath**, klikněte na šipku rozevíracího seznamu a vyberte `p_orderId`.</span><span class="sxs-lookup"><span data-stu-id="cca69-183">Under **XPath Queries**, click the drop down arrow and select `p_orderId`.</span></span> <span data-ttu-id="cca69-184">Tím se nakonfiguruje korelaci na druhé stránce přijímat aktivity.</span><span class="sxs-lookup"><span data-stu-id="cca69-184">This configures the correlation on the second receive activity.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="cca69-185">korelace najdete [korelace](../../../../docs/framework/wcf/feature-details/correlation.md).</span><span class="sxs-lookup"><span data-stu-id="cca69-185"> correlation see [Correlation](../../../../docs/framework/wcf/feature-details/correlation.md).</span></span>  
  
         <span data-ttu-id="cca69-186">![Nastavení vlastnosti CorrelatesOn](../../../../docs/framework/wcf/feature-details/media/correlateson.png "CorrelatesOn")</span><span class="sxs-lookup"><span data-stu-id="cca69-186">![Setting the CorrelatesOn property](../../../../docs/framework/wcf/feature-details/media/correlateson.png "CorrelatesOn")</span></span>  
  
    5.  <span data-ttu-id="cca69-187">Přetáhnout myší **Pokud** aktivity ihned po **ReceiveAddItem** aktivity.</span><span class="sxs-lookup"><span data-stu-id="cca69-187">Drag and drop an **If** activity immediately after the **ReceiveAddItem** activity.</span></span> <span data-ttu-id="cca69-188">Tato aktivita funguje stejně jako Pokud příkaz.</span><span class="sxs-lookup"><span data-stu-id="cca69-188">This activity acts just like an if statement.</span></span>  
  
        1.  <span data-ttu-id="cca69-189">Nastavte **podmínku** vlastnosti`itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`</span><span class="sxs-lookup"><span data-stu-id="cca69-189">Set the **Condition** property to `itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`</span></span>  
  
        2.  <span data-ttu-id="cca69-190">Přetáhnout myší **přiřadit** aktivitu v **pak** části a druhý do **Else** oddíl nastavit vlastnosti **přiřadit** aktivity, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="cca69-190">Drag and drop an **Assign** activity in to the **Then** section and another into the **Else** section set the properties of the **Assign** activities as shown in the following illustration.</span></span>  
  
             <span data-ttu-id="cca69-191">![Přiřazení výsledek volání služby](../../../../docs/framework/wcf/feature-details/media/resultassign.png "ResultAssign")</span><span class="sxs-lookup"><span data-stu-id="cca69-191">![Assigning the result of the service call](../../../../docs/framework/wcf/feature-details/media/resultassign.png "ResultAssign")</span></span>  
  
             <span data-ttu-id="cca69-192">Pokud je podmínka vyhodnocena `true` **pak** části bude proveden.</span><span class="sxs-lookup"><span data-stu-id="cca69-192">If the condition is `true` the **Then** section will be executed.</span></span> <span data-ttu-id="cca69-193">Pokud je podmínka vyhodnocena `false` **Else** části se spustí.</span><span class="sxs-lookup"><span data-stu-id="cca69-193">If the condition is `false` the **Else** section is executed.</span></span>  
  
        3.  <span data-ttu-id="cca69-194">Vyberte **SendReplyToReceive** aktivity a sady **DisplayName** vlastnost vidět na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="cca69-194">Select the **SendReplyToReceive** activity and set the **DisplayName** property shown in the following illustration.</span></span>  
  
             <span data-ttu-id="cca69-195">![Nastavení vlastnosti aktivity SendReply](../../../../docs/framework/wcf/feature-details/media/setreply2properties.png "SetReply2Properties")</span><span class="sxs-lookup"><span data-stu-id="cca69-195">![Setting the SendReply activity properties](../../../../docs/framework/wcf/feature-details/media/setreply2properties.png "SetReply2Properties")</span></span>  
  
        4.  <span data-ttu-id="cca69-196">Klikněte **definovat...**  odkaz **SetReplyToAddItem** aktivity a nakonfigurovat ji, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="cca69-196">Click the **Define ...** link in the **SetReplyToAddItem** activity and configure it as shown in the following illustration.</span></span> <span data-ttu-id="cca69-197">Tím se nakonfiguruje **SendReplyToAddItem** aktivitu pro vrácení hodnoty v `orderResult` proměnné.</span><span class="sxs-lookup"><span data-stu-id="cca69-197">This configures the **SendReplyToAddItem** activity to return the value in the `orderResult` variable.</span></span>  
  
             <span data-ttu-id="cca69-198">![Nastavení datové vazby pro aktivita SendReply](../../../../docs/framework/wcf/feature-details/media/replytoadditemcontent.gif "ReplyToAddItemContent")</span><span class="sxs-lookup"><span data-stu-id="cca69-198">![Setting the data binding for the SendReply activit](../../../../docs/framework/wcf/feature-details/media/replytoadditemcontent.gif "ReplyToAddItemContent")</span></span>  
  
8.  <span data-ttu-id="cca69-199">Otevřete soubor web.config a přidejte následující prvky \<chování > části zapnout stálost pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="cca69-199">Open the web.config file and add the following elements in the \<behavior> section to enable workflow persistence.</span></span>  
  
    ```xml  
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />  
              <workflowIdle timeToUnload="0"/>  
    ```  
  
    > [!WARNING]
    >  <span data-ttu-id="cca69-200">Nezapomeňte nahradit hostitele a název instance systému SQL server v předchozím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="cca69-200">Make sure to replace your host and SQL server instance name in the previous code snippet.</span></span>  
  
9. <span data-ttu-id="cca69-201">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="cca69-201">Build the solution.</span></span>  
  
### <a name="to-create-a-client-application-to-call-the-workflow-service"></a><span data-ttu-id="cca69-202">Chcete-li vytvořit klientskou aplikaci, aby volání služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="cca69-202">To Create a Client Application to Call the Workflow Service</span></span>  
  
1.  <span data-ttu-id="cca69-203">Přidat nový projekt konzolové aplikace volá `OrderClient` k řešení.</span><span class="sxs-lookup"><span data-stu-id="cca69-203">Add a new Console application project called `OrderClient` to the solution.</span></span>  
  
2.  <span data-ttu-id="cca69-204">Odkazy na následující sestavení, které chcete přidat `OrderClient` projektu</span><span class="sxs-lookup"><span data-stu-id="cca69-204">Add references to the following assemblies to the `OrderClient` project</span></span>  
  
    1.  <span data-ttu-id="cca69-205">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="cca69-205">System.ServiceModel.dll</span></span>  
  
    2.  <span data-ttu-id="cca69-206">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="cca69-206">System.ServiceModel.Activities.dll</span></span>  
  
3.  <span data-ttu-id="cca69-207">Přidat odkaz na službu ve službě pracovní postup a zadejte `OrderService` jako obor názvů.</span><span class="sxs-lookup"><span data-stu-id="cca69-207">Add a service reference to the workflow service and specify `OrderService` as the namespace.</span></span>  
  
4.  <span data-ttu-id="cca69-208">V `Main()` metoda klientského projektu přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="cca69-208">In the `Main()` method of the client project add the following code:</span></span>  
  
    ```  
    static void Main(string[] args)  
    {  
       // Send initial message to start the workflow service  
       Console.WriteLine("Sending start message");  
       StartOrderClient startProxy = new StartOrderClient();  
       string orderId = startProxy.StartOrder("Kim Abercrombie");  
  
       // The workflow service is now waiting for the second message to be sent  
       Console.WriteLine("Workflow service is idle...");  
       Console.WriteLine("Press [ENTER] to send an add item message to reactivate the workflow service...");  
       Console.ReadLine();  
  
       // Send the second message  
       Console.WriteLine("Sending add item message");  
       AddItemClient addProxy = new AddItemClient();  
       AddItem item = new AddItem();  
       item.p_itemId = "Zune HD";  
       item.p_orderId = orderId;  
  
       string orderResult = addProxy.AddItem(item);  
       Console.WriteLine("Service returned: " + orderResult);  
    }  
    ```  
  
5.  <span data-ttu-id="cca69-209">Sestavte řešení a spusťte `OrderClient` aplikace.</span><span class="sxs-lookup"><span data-stu-id="cca69-209">Build the solution and run the `OrderClient` application.</span></span> <span data-ttu-id="cca69-210">Klient se zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="cca69-210">The client will display the following text:</span></span>  
  
    ```Output  
    Sending start messageWorkflow service is idle...Press [ENTER] to send an add item message to reactivate the workflow service...  
    ```  
  
6.  <span data-ttu-id="cca69-211">Pokud chcete ověřit, že byl jako trvalý služby pracovního postupu, spustit SQL Server Management Studio přechodem na **spustit** nabídce zvolíte **všechny programy**, **Microsoft SQL Server 2008**, **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="cca69-211">To verify that the workflow service has been persisted, start the SQL Server Management Studio by going to the **Start** menu, Selecting **All Programs**, **Microsoft SQL Server 2008**, **SQL Server Management Studio**.</span></span>  
  
    1.  <span data-ttu-id="cca69-212">V levém podokně rozbalte, **databáze**, **SQLPersistenceStore**, **zobrazení** a klikněte pravým tlačítkem na **System.Activities.DurableInstancing.Instances**  a vyberte **vyberte Top 1000 řádky**.</span><span class="sxs-lookup"><span data-stu-id="cca69-212">In the left hand pane expand, **Databases**, **SQLPersistenceStore**, **Views** and right click **System.Activities.DurableInstancing.Instances** and select **Select Top 1000 Rows**.</span></span> <span data-ttu-id="cca69-213">V **výsledky** ověřte podokně se zobrazí alespoň jedna instance uvedené.</span><span class="sxs-lookup"><span data-stu-id="cca69-213">In the **Results** pane verify you see at least one instance listed.</span></span> <span data-ttu-id="cca69-214">Může mít další instance z předchozího spuštění během spuštění došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="cca69-214">There may be other instances from prior runs if an exception occurred while running.</span></span> <span data-ttu-id="cca69-215">Kliknutím pravým tlačítkem můžete odstranit stávající řádky **System.Activities.DurableInstancing.Instances** a výběrem **upravit Top 200 řádků**, stisknutí **Execute** tlačítko vyberete všechny řádky v podokně výsledků a vyberete **odstranit**.</span><span class="sxs-lookup"><span data-stu-id="cca69-215">You can delete existing rows by right clicking **System.Activities.DurableInstancing.Instances** and selecting **Edit Top 200 rows**, pressing the **Execute** button, selecting all rows in the results pane and selecting **delete**.</span></span>  <span data-ttu-id="cca69-216">Ověření instance, zobrazí se v databázi je instance aplikace vytvořena, ověřte zobrazení instance je prázdný před spuštěním klienta.</span><span class="sxs-lookup"><span data-stu-id="cca69-216">To verify the instance displayed in the database is the instance your application created, verify the instances view is empty prior to running the client.</span></span> <span data-ttu-id="cca69-217">Jakmile klient je spuštěné opětovným spuštěním dotazu (vyberte Top 1000 řádky) a ověřte přidaná novou instanci.</span><span class="sxs-lookup"><span data-stu-id="cca69-217">Once the client is running re-run the query (Select Top 1000 Rows) and verify a new instance has been added.</span></span>  
  
7.  <span data-ttu-id="cca69-218">Stiskněte klávesu enter k odeslání zprávy přidat položku do služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="cca69-218">Press enter to send the add item message to the workflow service.</span></span> <span data-ttu-id="cca69-219">Klient se zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="cca69-219">The client will display the following text:</span></span>  
  
    ```Output  
    Sending add item messageService returned: Item added to orderPress any key to continue . . .  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cca69-220">Viz také</span><span class="sxs-lookup"><span data-stu-id="cca69-220">See Also</span></span>  
 [<span data-ttu-id="cca69-221">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="cca69-221">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
