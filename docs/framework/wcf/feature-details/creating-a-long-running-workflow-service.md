---
title: Vytvoření dlouhodobé služby pracovního postupu
ms.date: 03/30/2017
ms.assetid: 4c39bd04-5b8a-4562-a343-2c63c2821345
ms.openlocfilehash: 4ae01201230bf848c045158424db60097d8dd767
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599344"
---
# <a name="create-a-long-running-workflow-service"></a><span data-ttu-id="2248b-102">Vytvoření dlouhodobě spuštěné služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="2248b-102">Create a Long-running Workflow Service</span></span>

<span data-ttu-id="2248b-103">Toto téma popisuje, jak vytvořit dlouhodobě běžící službu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2248b-103">This topic describes how to create a long-running workflow service.</span></span> <span data-ttu-id="2248b-104">Dlouhodobě běžící služby pracovních postupů můžou běžet dlouhou dobu.</span><span class="sxs-lookup"><span data-stu-id="2248b-104">Long running workflow services may run for long periods of time.</span></span> <span data-ttu-id="2248b-105">V určitém okamžiku může pracovní postup při čekání na některé další informace přejít na nečinné.</span><span class="sxs-lookup"><span data-stu-id="2248b-105">At some point the workflow may go idle waiting for some additional information.</span></span> <span data-ttu-id="2248b-106">V takovém případě je pracovní postup trvale uložen v databázi SQL a je odebrán z paměti.</span><span class="sxs-lookup"><span data-stu-id="2248b-106">When this occurs the workflow is persisted to a SQL database and is removed from memory.</span></span> <span data-ttu-id="2248b-107">Když budou další informace k dispozici, instance pracovního postupu se načte zpátky do paměti a pokračuje v provádění.</span><span class="sxs-lookup"><span data-stu-id="2248b-107">When the additional information becomes available the workflow instance is loaded back into memory and continues executing.</span></span>  <span data-ttu-id="2248b-108">V tomto scénáři implementujete velmi zjednodušený systém řazení.</span><span class="sxs-lookup"><span data-stu-id="2248b-108">In this scenario you are implementing a very simplified ordering system.</span></span>  <span data-ttu-id="2248b-109">Klient odešle počáteční zprávu službě pracovního postupu, aby zahájí objednávku.</span><span class="sxs-lookup"><span data-stu-id="2248b-109">The client sends an initial message to the workflow service to start the order.</span></span> <span data-ttu-id="2248b-110">Vrátí klientovi ID objednávky.</span><span class="sxs-lookup"><span data-stu-id="2248b-110">It returns an order ID to the client.</span></span> <span data-ttu-id="2248b-111">V tomto okamžiku služba pracovního postupu čeká na jinou zprávu od klienta a přejde do stavu nečinnosti a bude trvale uložena do databáze SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2248b-111">At this point the workflow service is waiting for another message from the client and goes into the idle state and is persisted to a SQL Server database.</span></span>  <span data-ttu-id="2248b-112">Když klient pošle další zprávu pro objednání položky, služba pracovního postupu se načte zpátky do paměti a dokončí zpracování objednávky.</span><span class="sxs-lookup"><span data-stu-id="2248b-112">When the client sends the next message to order an item, the workflow service is loaded back into memory and finishes processing the order.</span></span> <span data-ttu-id="2248b-113">V ukázce kódu vrátí řetězec oznamující, že položka byla přidána do objednávky.</span><span class="sxs-lookup"><span data-stu-id="2248b-113">In the code sample it returns a string stating the item has been added to the order.</span></span> <span data-ttu-id="2248b-114">Ukázka kódu se nepovažuje za reálné použití technologie, ale spíše na jednoduchou ukázku, která znázorňuje dlouhodobě běžící služby pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="2248b-114">The code sample is not meant to be a real world application of the technology, but rather a simple sample that illustrates long running workflow services.</span></span> <span data-ttu-id="2248b-115">Toto téma předpokládá, že máte v úmyslu vytvořit projekty a řešení sady Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="2248b-115">This topic assumes you know how to create Visual Studio 2012 projects and solutions.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2248b-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2248b-116">Prerequisites</span></span>

<span data-ttu-id="2248b-117">Pro použití tohoto Názorného postupu musíte mít nainstalovaný následující software:</span><span class="sxs-lookup"><span data-stu-id="2248b-117">You must have the following software installed to use this walkthrough:</span></span>

1. <span data-ttu-id="2248b-118">Microsoft SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="2248b-118">Microsoft SQL Server 2008</span></span>

2. <span data-ttu-id="2248b-119">Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="2248b-119">Visual Studio 2012</span></span>

3. <span data-ttu-id="2248b-120">Microsoft[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2248b-120">Microsoft  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]</span></span>

4. <span data-ttu-id="2248b-121">Jste obeznámeni s WCF a sadou Visual Studio 2012 a víte, jak vytvářet projekty a řešení.</span><span class="sxs-lookup"><span data-stu-id="2248b-121">You are familiar with WCF and Visual Studio 2012 and know how to create projects/solutions.</span></span>

## <a name="set-up-the-sql-database"></a><span data-ttu-id="2248b-122">Nastavení SQL Database</span><span class="sxs-lookup"><span data-stu-id="2248b-122">Set up the SQL Database</span></span>

1. <span data-ttu-id="2248b-123">Aby se instance služby pracovních postupů zachovaly, musíte mít nainstalovanou Microsoft SQL Server a musíte nakonfigurovat databázi tak, aby ukládala trvalé instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2248b-123">In order for workflow service instances to be persisted you must have Microsoft SQL Server installed and you must configure a database to store the persisted workflow instances.</span></span> <span data-ttu-id="2248b-124">Spusťte Microsoft SQL Management Studio kliknutím na tlačítko **Start** , výběrem možnosti **všechny programy**, **Microsoft SQL Server 2008**a **Microsoft SQL Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="2248b-124">Run Microsoft SQL Management Studio by clicking the **Start** button, selecting **All Programs**, **Microsoft SQL Server 2008**, and **Microsoft SQL Management Studio**.</span></span>

2. <span data-ttu-id="2248b-125">Kliknutím na tlačítko **připojit** se přihlaste k instanci SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2248b-125">Click the **Connect** button to log on to the SQL Server instance</span></span>

3. <span data-ttu-id="2248b-126">Ve stromovém zobrazení klikněte pravým tlačítkem na **databáze** a vyberte **Nová databáze.**</span><span class="sxs-lookup"><span data-stu-id="2248b-126">Right click **Databases** in the tree view and select **New Database..**</span></span> <span data-ttu-id="2248b-127">Vytvoří se nová databáze s názvem `SQLPersistenceStore` .</span><span class="sxs-lookup"><span data-stu-id="2248b-127">to create a new database called `SQLPersistenceStore`.</span></span>

4. <span data-ttu-id="2248b-128">Spuštěním souboru skriptu SqlWorkflowInstanceStoreSchema. SQL umístěného v adresáři C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en v databázi SQLPersistenceStore nastavte potřebná schémata databáze.</span><span class="sxs-lookup"><span data-stu-id="2248b-128">Run the SqlWorkflowInstanceStoreSchema.sql script file located in the C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en directory on the SQLPersistenceStore database to set up the needed database schemas.</span></span>

5. <span data-ttu-id="2248b-129">Spusťte soubor skriptu SqlWorkflowInstanceStoreLogic. SQL umístěný v adresáři C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en v databázi SQLPersistenceStore a nastavte tak potřebnou databázovou logiku.</span><span class="sxs-lookup"><span data-stu-id="2248b-129">Run the SqlWorkflowInstanceStoreLogic.sql script file located in the C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en directory on the SQLPersistenceStore database to set up the needed database logic.</span></span>

## <a name="create-the-web-hosted-workflow-service"></a><span data-ttu-id="2248b-130">Vytvořit službu Web Hosted Workflow Service</span><span class="sxs-lookup"><span data-stu-id="2248b-130">Create the Web Hosted Workflow Service</span></span>

1. <span data-ttu-id="2248b-131">Vytvořte prázdné řešení sady Visual Studio 2012 a pojmenujte ho `OrderProcessing` .</span><span class="sxs-lookup"><span data-stu-id="2248b-131">Create an empty Visual Studio 2012 solution, name it `OrderProcessing`.</span></span>

2. <span data-ttu-id="2248b-132">Přidejte do řešení nový projekt aplikace služby pracovního postupu WCF s názvem `OrderService` .</span><span class="sxs-lookup"><span data-stu-id="2248b-132">Add a new WCF Workflow Service Application project called `OrderService` to the solution.</span></span>

3. <span data-ttu-id="2248b-133">V dialogovém okně Vlastnosti projektu vyberte kartu **Web** .</span><span class="sxs-lookup"><span data-stu-id="2248b-133">In the project properties dialog, select the **Web** tab.</span></span>

    1. <span data-ttu-id="2248b-134">V části **Spustit akci** vyberte **konkrétní stránka** a zadejte `Service1.xamlx` .</span><span class="sxs-lookup"><span data-stu-id="2248b-134">Under **Start Action** select **Specific Page** and specify `Service1.xamlx`.</span></span>

        <span data-ttu-id="2248b-135">![Webové vlastnosti projektu služby pracovního postupu](./media/creating-a-long-running-workflow-service/start-action-specific-page-option.png "Vytvořit možnost stránky pro web hostovaný pracovní postup – konkrétní služba")</span><span class="sxs-lookup"><span data-stu-id="2248b-135">![Workflow Service Project Web Properties](./media/creating-a-long-running-workflow-service/start-action-specific-page-option.png "Create the web hosted workflow service - Specific Page option")</span></span>

    2. <span data-ttu-id="2248b-136">V části **servery** vyberte **použít místní webový server služby IIS**.</span><span class="sxs-lookup"><span data-stu-id="2248b-136">Under **Servers** select **Use Local IIS Web server**.</span></span>

        <span data-ttu-id="2248b-137">![Nastavení místního webového serveru](./media/creating-a-long-running-workflow-service/use-local-web-server.png "Vytvoření služby Web Hosted Workflow Service – použijte možnost místní webový server služby IIS")</span><span class="sxs-lookup"><span data-stu-id="2248b-137">![Local Web Server Settings](./media/creating-a-long-running-workflow-service/use-local-web-server.png "Create the web hosted workflow service - Use Local IIS Web Server option")</span></span>

        > [!WARNING]
        > <span data-ttu-id="2248b-138">Chcete-li nastavit toto nastavení, je nutné spustit aplikaci Visual Studio 2012 v režimu správce.</span><span class="sxs-lookup"><span data-stu-id="2248b-138">You must run Visual Studio 2012 in administrator mode to make this setting.</span></span>

        <span data-ttu-id="2248b-139">Tyto dva kroky nakonfigurují projekt služby pracovního postupu tak, aby byl hostovaný službou IIS.</span><span class="sxs-lookup"><span data-stu-id="2248b-139">These two steps configure the workflow service project to be hosted by IIS.</span></span>

4. <span data-ttu-id="2248b-140">Otevřete, `Service1.xamlx` Pokud už není otevřený, a odstraňte existující aktivity **ReceiveRequest** a **SendResponse** .</span><span class="sxs-lookup"><span data-stu-id="2248b-140">Open `Service1.xamlx` if it is not open already and delete the existing **ReceiveRequest** and **SendResponse** activities.</span></span>

5. <span data-ttu-id="2248b-141">Vyberte aktivitu **sekvenční služby** a klikněte na odkaz **proměnné** a přidejte proměnné zobrazené na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="2248b-141">Select the **Sequential Service** activity and click the **Variables** link and add the variables shown in the following illustration.</span></span> <span data-ttu-id="2248b-142">Tím se přidají některé proměnné, které se použijí později ve službě pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2248b-142">Doing this adds some variables that will be used later on in the workflow service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2248b-143">Pokud popisovač CorrelationHandle není v rozevíracím seznamu typ proměnné, vyberte **Vyhledat typy** z rozevírací nabídky.</span><span class="sxs-lookup"><span data-stu-id="2248b-143">If CorrelationHandle is not in the Variable Type drop-down, select **Browse for types** from the drop-down.</span></span> <span data-ttu-id="2248b-144">Do pole **název typu** zadejte popisovač CorrelationHandle, v seznamu vyberte popisovač CorrelationHandle a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="2248b-144">Type CorrelationHandle in the **Type name** box, select CorrelationHandle from the listbox and click **OK**.</span></span>

    <span data-ttu-id="2248b-145">![Přidat proměnné](./media/creating-a-long-running-workflow-service/add-variables-sequential-service-activity.gif "Přidejte proměnné do aktivity sekvenční služby.")</span><span class="sxs-lookup"><span data-stu-id="2248b-145">![Add Variables](./media/creating-a-long-running-workflow-service/add-variables-sequential-service-activity.gif "Add variables to the Sequential Service activity.")</span></span>

6. <span data-ttu-id="2248b-146">Přetáhněte šablonu aktivity **ReceiveAndSendReply** do aktivity **sekvenční služby** .</span><span class="sxs-lookup"><span data-stu-id="2248b-146">Drag and drop a **ReceiveAndSendReply** activity template into the **Sequential Service** activity.</span></span> <span data-ttu-id="2248b-147">Tato sada aktivit obdrží zprávu od klienta a pošle odpověď zpátky.</span><span class="sxs-lookup"><span data-stu-id="2248b-147">This set of activities will receive a message from a client and send a reply back.</span></span>

    1. <span data-ttu-id="2248b-148">Vyberte aktivitu **přijmout** a nastavte vlastnosti zvýrazněné na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="2248b-148">Select the **Receive** activity and set the properties highlighted in the following illustration.</span></span>

        <span data-ttu-id="2248b-149">![Nastavit vlastnosti aktivity Receive](./media/creating-a-long-running-workflow-service/set-receive-activity-properties.png "Nastavte vlastnosti aktivity Receive.")</span><span class="sxs-lookup"><span data-stu-id="2248b-149">![Set Receive Activity Properties](./media/creating-a-long-running-workflow-service/set-receive-activity-properties.png "Set the Receive activity properties.")</span></span>

        <span data-ttu-id="2248b-150">Vlastnost DisplayName nastaví název zobrazený pro aktivitu Receive v návrháři.</span><span class="sxs-lookup"><span data-stu-id="2248b-150">The DisplayName property sets the name displayed for the Receive activity in the designer.</span></span> <span data-ttu-id="2248b-151">Vlastnosti ServiceContractName a OperationName určují název kontraktu služby a operace, které jsou implementované aktivitou Receive.</span><span class="sxs-lookup"><span data-stu-id="2248b-151">The ServiceContractName and OperationName properties specify the name of the service contract and operation that are implemented by the Receive activity.</span></span> <span data-ttu-id="2248b-152">Další informace o tom, jak se ve službách pracovních postupů používají kontrakty, najdete v tématu [Použití kontraktů v pracovním postupu](using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="2248b-152">For more information about how contracts are used in Workflow services see [Using Contracts in Workflow](using-contracts-in-workflow.md).</span></span>

    2. <span data-ttu-id="2248b-153">Klikněte na odkaz **definovat...** v aktivitě **ReceiveStartOrder** a nastavte vlastnosti zobrazené na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="2248b-153">Click the **Define...** link in the **ReceiveStartOrder** activity and set the properties shown in the following illustration.</span></span>  <span data-ttu-id="2248b-154">Všimněte si, že přepínač **Parameters** je vybrán, parametr s názvem `p_customerName` je vázán na `customerName` proměnnou.</span><span class="sxs-lookup"><span data-stu-id="2248b-154">Notice that the **Parameters** radio button is selected, a parameter named `p_customerName` is bound to the `customerName` variable.</span></span> <span data-ttu-id="2248b-155">Tím se nakonfiguruje aktivita **příjmu** pro příjem některých dat a vazba těchto dat na lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="2248b-155">This configures the **Receive** activity to receive some data and bind that data to local variables.</span></span>

        <span data-ttu-id="2248b-156">![Nastavení dat přijatých aktivitou Receive](./media/creating-a-long-running-workflow-service/set-properties-for-receive-content.png "Nastavte vlastnosti pro data přijatá aktivitou Receive.")</span><span class="sxs-lookup"><span data-stu-id="2248b-156">![Setting the data received by the Receive activity](./media/creating-a-long-running-workflow-service/set-properties-for-receive-content.png "Set the properties for data received by the Receive activity.")</span></span>

    3. <span data-ttu-id="2248b-157">Vyberte aktivitu **SendReplyToReceive** a nastavte zvýrazněnou vlastnost, která je znázorněna na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="2248b-157">Select The **SendReplyToReceive** activity and set the highlighted property shown in the following illustration.</span></span>

        <span data-ttu-id="2248b-158">![Nastavení vlastností aktivity SendReply](./media/creating-a-long-running-workflow-service/set-properties-for-reply-activities.png "SetReplyProperties")</span><span class="sxs-lookup"><span data-stu-id="2248b-158">![Setting the properties of the SendReply activity](./media/creating-a-long-running-workflow-service/set-properties-for-reply-activities.png "SetReplyProperties")</span></span>

    4. <span data-ttu-id="2248b-159">Klikněte na odkaz **definovat...** v aktivitě **SendReplyToStartOrder** a nastavte vlastnosti zobrazené na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="2248b-159">Click the **Define...** link in the **SendReplyToStartOrder** activity and set the properties shown in the following illustration.</span></span> <span data-ttu-id="2248b-160">Všimněte si, že přepínač **Parameters** je vybrán; parametr s názvem `p_orderId` je vázán na `orderId` proměnnou.</span><span class="sxs-lookup"><span data-stu-id="2248b-160">Notice that the **Parameters** radio button is selected; a parameter named `p_orderId` is bound to the `orderId` variable.</span></span> <span data-ttu-id="2248b-161">Toto nastavení určuje, že aktivita SendReplyToStartOrder vrátí hodnotu typu String volajícímu.</span><span class="sxs-lookup"><span data-stu-id="2248b-161">This setting specifies that the SendReplyToStartOrder activity will return a value of type string to the caller.</span></span>

        <span data-ttu-id="2248b-162">![Konfigurace dat obsahu aktivity SendReply](./media/creating-a-long-running-workflow-service/setreplycontent-for-sendreplytostartorder-activity.png "Nakonfigurujte nastavení pro aktivitu SetReplyToStartOrder.")</span><span class="sxs-lookup"><span data-stu-id="2248b-162">![Configuring the SendReply activity content data](./media/creating-a-long-running-workflow-service/setreplycontent-for-sendreplytostartorder-activity.png "Configure setting for SetReplyToStartOrder activity.")</span></span>

    5. <span data-ttu-id="2248b-163">Přetáhněte aktivitu přiřadit mezi aktivitami **Receive** a **SendReply** a nastavte vlastnosti tak, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="2248b-163">Drag and drop an Assign activity in between the **Receive** and **SendReply** activities and set the properties as shown in the following illustration:</span></span>

        <span data-ttu-id="2248b-164">![Přidání aktivity přiřazení](./media/creating-a-long-running-workflow-service/add-an-assign-activity.png "Přidejte aktivitu přiřazení.")</span><span class="sxs-lookup"><span data-stu-id="2248b-164">![Adding an assign activity](./media/creating-a-long-running-workflow-service/add-an-assign-activity.png "Add an assign activity.")</span></span>

        <span data-ttu-id="2248b-165">Tím se vytvoří nové ID objednávky a hodnota se umístí do proměnné ČísloObjednávky.</span><span class="sxs-lookup"><span data-stu-id="2248b-165">This creates a new order ID and places the value in the orderId variable.</span></span>

    6. <span data-ttu-id="2248b-166">Vyberte aktivitu **ReplyToStartOrder** .</span><span class="sxs-lookup"><span data-stu-id="2248b-166">Select the **ReplyToStartOrder** activity.</span></span> <span data-ttu-id="2248b-167">V okně Vlastnosti klikněte na tlačítko se třemi tečkami pro **inicializátoři CorrelationInitializers**.</span><span class="sxs-lookup"><span data-stu-id="2248b-167">In the properties window click the ellipsis button for **CorrelationInitializers**.</span></span> <span data-ttu-id="2248b-168">Vyberte odkaz **Přidat inicializátor** , `orderIdHandle` do textového pole inicializátor zadejte, pro typ korelace vyberte inicializátor korelace a v rozevíracím seznamu dotazy XPath vyberte p_orderId.</span><span class="sxs-lookup"><span data-stu-id="2248b-168">Select the **Add initializer** link, enter `orderIdHandle` in the Initializer text box, select Query correlation initializer for the Correlation type, and select p_orderId under the XPATH Queries dropdown box.</span></span> <span data-ttu-id="2248b-169">Tato nastavení znázorňuje následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="2248b-169">These settings are shown in the following illustration.</span></span> <span data-ttu-id="2248b-170">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="2248b-170">Click **OK**.</span></span>  <span data-ttu-id="2248b-171">Tím se inicializuje korelace mezi klientem a touto instancí služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2248b-171">This initializes a correlation between the client and this instance of the workflow service.</span></span> <span data-ttu-id="2248b-172">Když se přijme zpráva obsahující toto ID objednávky, je směrována do této instance služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2248b-172">When a message containing this order ID is received it is routed to this instance of the workflow service.</span></span>

        <span data-ttu-id="2248b-173">![Přidání inicializátoru korelace](./media/creating-a-long-running-workflow-service/add-correlationinitializers.png "Přidejte inicializátor korelace.")</span><span class="sxs-lookup"><span data-stu-id="2248b-173">![Adding a correlation initializer](./media/creating-a-long-running-workflow-service/add-correlationinitializers.png "Add a correlation initializer.")</span></span>

7. <span data-ttu-id="2248b-174">Přetáhněte další aktivitu **ReceiveAndSendReply** na konec pracovního postupu (mimo **sekvenci** obsahující první aktivity **Receive** a **SendReply** ).</span><span class="sxs-lookup"><span data-stu-id="2248b-174">Drag and drop another **ReceiveAndSendReply** activity to the end of the workflow (outside the **Sequence** containing the first **Receive** and **SendReply** activities).</span></span> <span data-ttu-id="2248b-175">Tím přijde druhá zpráva odeslaná klientem a reaguje na ni.</span><span class="sxs-lookup"><span data-stu-id="2248b-175">This will receive the second message sent by the client and respond to it.</span></span>

    1. <span data-ttu-id="2248b-176">Vyberte **sekvenci** , která obsahuje nově přidané aktivity **Receive** a **SendReply** a klikněte na tlačítko **proměnné** .</span><span class="sxs-lookup"><span data-stu-id="2248b-176">Select the **Sequence** that contains the newly added **Receive** and **SendReply** activities and click the **Variables** button.</span></span> <span data-ttu-id="2248b-177">Přidejte proměnnou zvýrazněnou na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="2248b-177">Add the variable highlighted in the following illustration:</span></span>

        <span data-ttu-id="2248b-178">![Přidávání nových proměnných](./media/creating-a-long-running-workflow-service/add-the-itemid-variable.png "Přidejte proměnnou ItemId.")</span><span class="sxs-lookup"><span data-stu-id="2248b-178">![Adding new variables](./media/creating-a-long-running-workflow-service/add-the-itemid-variable.png "Add the ItemId variable.")</span></span>

        <span data-ttu-id="2248b-179">`orderResult`Do oboru přidejte také **řetězec** as `Sequence` .</span><span class="sxs-lookup"><span data-stu-id="2248b-179">Also add `orderResult` as **String** in the `Sequence` scope.</span></span>

    2. <span data-ttu-id="2248b-180">Vyberte aktivitu **Receive** a nastavte vlastnosti zobrazené na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="2248b-180">Select the **Receive** activity and set the properties shown in the following illustration:</span></span>

        <span data-ttu-id="2248b-181">![Nastavit vlastnosti aktivity Receive](./media/creating-a-long-running-workflow-service/set-receive-activities-properties.png "Nastavte vlastnosti aktivity Receive.")</span><span class="sxs-lookup"><span data-stu-id="2248b-181">![Set the Receive activity properties](./media/creating-a-long-running-workflow-service/set-receive-activities-properties.png "Set the Receive activities properties.")</span></span>

        > [!NOTE]
        > <span data-ttu-id="2248b-182">Nezapomeňte změnit pole **ServiceContractName** pomocí `../IAddItem` .</span><span class="sxs-lookup"><span data-stu-id="2248b-182">Don't forget to change **ServiceContractName** field with `../IAddItem`.</span></span>

    3. <span data-ttu-id="2248b-183">Klikněte na odkaz **definovat...** v aktivitě **ReceiveAddItem** a přidejte parametry zobrazené na následujícím obrázku: tím se nakonfiguruje aktivita Receive pro příjem dvou parametrů, ID objednávky a ID položky, která je seřazená.</span><span class="sxs-lookup"><span data-stu-id="2248b-183">Click the **Define...** link in the **ReceiveAddItem** activity and add the parameters shown in the following illustration:This configures the receive activity to accept two parameters, the order ID and the ID of the item being ordered.</span></span>

        <span data-ttu-id="2248b-184">![Určení parametrů pro druhý příjem](./media/creating-a-long-running-workflow-service/add-receive-two-parameters.png "Nakonfigurujte aktivitu Receive pro příjem dvou parametrů.")</span><span class="sxs-lookup"><span data-stu-id="2248b-184">![Specifying parameters for the second receive](./media/creating-a-long-running-workflow-service/add-receive-two-parameters.png "Configure the receive activity to receive two parameters.")</span></span>

    4. <span data-ttu-id="2248b-185">Klikněte na tlačítko se třemi tečkami **CorrelateOn** a zadejte `orderIdHandle` .</span><span class="sxs-lookup"><span data-stu-id="2248b-185">Click the **CorrelateOn** ellipsis button and enter `orderIdHandle`.</span></span> <span data-ttu-id="2248b-186">V části **dotazy XPath**klikněte na šipku rozevíracího seznamu a vyberte `p_orderId` .</span><span class="sxs-lookup"><span data-stu-id="2248b-186">Under **XPath Queries**, click the drop down arrow and select `p_orderId`.</span></span> <span data-ttu-id="2248b-187">Tím se nakonfiguruje korelace pro druhou aktivitu Receive.</span><span class="sxs-lookup"><span data-stu-id="2248b-187">This configures the correlation on the second receive activity.</span></span> <span data-ttu-id="2248b-188">Další informace o korelaci najdete v tématu [korelace](correlation.md).</span><span class="sxs-lookup"><span data-stu-id="2248b-188">For more information about correlation see [Correlation](correlation.md).</span></span>

        <span data-ttu-id="2248b-189">![Nastavení vlastnosti vlastnosti CorrelatesOn](./media/creating-a-long-running-workflow-service/correlateson-setting.png "Nastavte vlastnost vlastnosti CorrelatesOn.")</span><span class="sxs-lookup"><span data-stu-id="2248b-189">![Setting the CorrelatesOn property](./media/creating-a-long-running-workflow-service/correlateson-setting.png "Set the CorrelatesOn property.")</span></span>

    5. <span data-ttu-id="2248b-190">Přetáhněte aktivitu **if** hned za aktivitu **ReceiveAddItem** .</span><span class="sxs-lookup"><span data-stu-id="2248b-190">Drag and drop an **If** activity immediately after the **ReceiveAddItem** activity.</span></span> <span data-ttu-id="2248b-191">Tato aktivita funguje stejně jako příkaz if.</span><span class="sxs-lookup"><span data-stu-id="2248b-191">This activity acts just like an if statement.</span></span>

        1. <span data-ttu-id="2248b-192">Nastavte vlastnost **Condition** na`itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`</span><span class="sxs-lookup"><span data-stu-id="2248b-192">Set the **Condition** property to `itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`</span></span>

        2. <span data-ttu-id="2248b-193">Přetáhněte aktivitu **přiřadit** v části do oddílu **then** a jinou do části **Else** nastavte vlastnosti aktivity **přiřazení** , jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="2248b-193">Drag and drop an **Assign** activity in to the **Then** section and another into the **Else** section set the properties of the **Assign** activities as shown in the following illustration.</span></span>

            <span data-ttu-id="2248b-194">![Přiřazuje se výsledek volání služby.](./media/creating-a-long-running-workflow-service/assign-result-of-service-call.png "Přiřaďte výsledek volání služby.")</span><span class="sxs-lookup"><span data-stu-id="2248b-194">![Assigning the result of the service call](./media/creating-a-long-running-workflow-service/assign-result-of-service-call.png "Assign the result of the service call.")</span></span>

            <span data-ttu-id="2248b-195">Pokud je podmínka `true` , bude provedena v oddílu **then** .</span><span class="sxs-lookup"><span data-stu-id="2248b-195">If the condition is `true` the **Then** section will be executed.</span></span> <span data-ttu-id="2248b-196">Pokud je podmínka `false` v části **Else** , je provedena.</span><span class="sxs-lookup"><span data-stu-id="2248b-196">If the condition is `false` the **Else** section is executed.</span></span>

        3. <span data-ttu-id="2248b-197">Vyberte aktivitu **SendReplyToReceive** a nastavte vlastnost **DisplayName** znázorněnou na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="2248b-197">Select the **SendReplyToReceive** activity and set the **DisplayName** property shown in the following illustration.</span></span>

            <span data-ttu-id="2248b-198">![Nastavení vlastností aktivity SendReply](./media/creating-a-long-running-workflow-service/send-reply-activity-property.png "Nastavte vlastnost aktivity SendReply.")</span><span class="sxs-lookup"><span data-stu-id="2248b-198">![Setting the SendReply activity properties](./media/creating-a-long-running-workflow-service/send-reply-activity-property.png "Set the SendReply activity property.")</span></span>

        4. <span data-ttu-id="2248b-199">Klikněte na odkaz **definovat...** v aktivitě **SetReplyToAddItem** a nakonfigurujte ho tak, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="2248b-199">Click the **Define ...** link in the **SetReplyToAddItem** activity and configure it as shown in the following illustration.</span></span> <span data-ttu-id="2248b-200">Tím se nakonfiguruje aktivita **SendReplyToAddItem** , která vrátí hodnotu v `orderResult` proměnné.</span><span class="sxs-lookup"><span data-stu-id="2248b-200">This configures the **SendReplyToAddItem** activity to return the value in the `orderResult` variable.</span></span>

            <span data-ttu-id="2248b-201">![Nastavení datové vazby pro aktivitu SendReply](./media/creating-a-long-running-workflow-service/set-property-for-sendreplytoadditem.gif "Nastaví vlastnost pro aktivitu SendReplyToAddItem.")</span><span class="sxs-lookup"><span data-stu-id="2248b-201">![Setting the data binding for the SendReply activity](./media/creating-a-long-running-workflow-service/set-property-for-sendreplytoadditem.gif "Set property for SendReplyToAddItem activity.")</span></span>

8. <span data-ttu-id="2248b-202">Otevřete soubor Web. config a přidejte následující prvky do \<behavior> části pro povolení trvalosti pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2248b-202">Open the web.config file and add the following elements in the \<behavior> section to enable workflow persistence.</span></span>

    ```xml
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />
              <workflowIdle timeToUnload="0"/>
    ```

    > [!WARNING]
    > <span data-ttu-id="2248b-203">Nezapomeňte nahradit název hostitele a instance serveru SQL Server v předchozím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="2248b-203">Make sure to replace your host and SQL server instance name in the previous code snippet.</span></span>

9. <span data-ttu-id="2248b-204">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="2248b-204">Build the solution.</span></span>

## <a name="create-a-client-application-to-call-the-workflow-service"></a><span data-ttu-id="2248b-205">Vytvoření klientské aplikace pro volání služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="2248b-205">Create a Client Application to Call the Workflow Service</span></span>

1. <span data-ttu-id="2248b-206">Přidejte do řešení nový projekt konzolové aplikace s názvem `OrderClient` .</span><span class="sxs-lookup"><span data-stu-id="2248b-206">Add a new Console application project called `OrderClient` to the solution.</span></span>

2. <span data-ttu-id="2248b-207">Přidat do projektu odkazy na následující sestavení `OrderClient`</span><span class="sxs-lookup"><span data-stu-id="2248b-207">Add references to the following assemblies to the `OrderClient` project</span></span>

    1. <span data-ttu-id="2248b-208">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="2248b-208">System.ServiceModel.dll</span></span>

    2. <span data-ttu-id="2248b-209">System. ServiceModel. Activities. dll</span><span class="sxs-lookup"><span data-stu-id="2248b-209">System.ServiceModel.Activities.dll</span></span>

3. <span data-ttu-id="2248b-210">Přidejte do služby pracovního postupu odkaz na službu a `OrderService` jako obor názvů zadejte.</span><span class="sxs-lookup"><span data-stu-id="2248b-210">Add a service reference to the workflow service and specify `OrderService` as the namespace.</span></span>

4. <span data-ttu-id="2248b-211">V `Main()` metodě klientského projektu přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="2248b-211">In the `Main()` method of the client project add the following code:</span></span>

    ```csharp
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

5. <span data-ttu-id="2248b-212">Sestavte řešení a spusťte `OrderClient` aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2248b-212">Build the solution and run the `OrderClient` application.</span></span> <span data-ttu-id="2248b-213">Klient zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="2248b-213">The client will display the following text:</span></span>

    ```output
    Sending start messageWorkflow service is idle...Press [ENTER] to send an add item message to reactivate the workflow service...
    ```

6. <span data-ttu-id="2248b-214">Chcete-li ověřit, zda byla služba pracovního postupu trvalá, spusťte SQL Server Management Studio přejděte do nabídky **Start** a vyberte možnost **všechny programy** **Microsoft SQL Server 2008** **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="2248b-214">To verify that the workflow service has been persisted, start the SQL Server Management Studio by going to the **Start** menu, Selecting **All Programs**, **Microsoft SQL Server 2008**, **SQL Server Management Studio**.</span></span>

    1. <span data-ttu-id="2248b-215">V levém podokně rozbalte, **databáze**, **SQLPersistenceStore**, **zobrazení** a klikněte pravým tlačítkem na **System. Activities. DurableInstancing. Instances** a vyberte **Vybrat prvních 1000 řádků**.</span><span class="sxs-lookup"><span data-stu-id="2248b-215">In the left hand pane expand, **Databases**, **SQLPersistenceStore**, **Views** and right click **System.Activities.DurableInstancing.Instances** and select **Select Top 1000 Rows**.</span></span> <span data-ttu-id="2248b-216">V podokně **výsledků** ověřte, že je v seznamu uvedena alespoň jedna instance.</span><span class="sxs-lookup"><span data-stu-id="2248b-216">In the **Results** pane verify you see at least one instance listed.</span></span> <span data-ttu-id="2248b-217">Pokud při spuštění dojde k výjimce, může dojít k dalším instancím z předchozích spuštění.</span><span class="sxs-lookup"><span data-stu-id="2248b-217">There may be other instances from prior runs if an exception occurred while running.</span></span> <span data-ttu-id="2248b-218">Existující řádky můžete odstranit tak, že kliknete pravým tlačítkem na **System. Activities. DurableInstancing. Instances** a vyberete **Upravit horní 200 řádků**, stisknete tlačítko **Spustit** , vyberete všechny řádky v podokně výsledků a vyberete **Odstranit**.</span><span class="sxs-lookup"><span data-stu-id="2248b-218">You can delete existing rows by right clicking **System.Activities.DurableInstancing.Instances** and selecting **Edit Top 200 rows**, pressing the **Execute** button, selecting all rows in the results pane and selecting **delete**.</span></span>  <span data-ttu-id="2248b-219">Chcete-li ověřit, zda je instance zobrazená v databázi instancí aplikace vytvořená, ověřte, zda je zobrazení instance před spuštěním klienta prázdné.</span><span class="sxs-lookup"><span data-stu-id="2248b-219">To verify the instance displayed in the database is the instance your application created, verify the instances view is empty prior to running the client.</span></span> <span data-ttu-id="2248b-220">Po spuštění klienta znovu spusťte dotaz (vyberte horní 1000 řádků) a ověřte, zda byla přidána nová instance.</span><span class="sxs-lookup"><span data-stu-id="2248b-220">Once the client is running re-run the query (Select Top 1000 Rows) and verify a new instance has been added.</span></span>

7. <span data-ttu-id="2248b-221">Stisknutím klávesy ENTER odešlete zprávu přidat položku do služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2248b-221">Press enter to send the add item message to the workflow service.</span></span> <span data-ttu-id="2248b-222">Klient zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="2248b-222">The client will display the following text:</span></span>

    ```output
    Sending add item messageService returned: Item added to orderPress any key to continue . . .
    ```

## <a name="see-also"></a><span data-ttu-id="2248b-223">Viz také</span><span class="sxs-lookup"><span data-stu-id="2248b-223">See also</span></span>

- [<span data-ttu-id="2248b-224">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="2248b-224">Workflow Services</span></span>](workflow-services.md)
