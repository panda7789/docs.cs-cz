---
title: Tok transakcí do služeb pracovních postupů a mimo ně
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: a74a2a82e63ddd6c331dd90f9eb894ed5069da3d
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675715"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a><span data-ttu-id="1fa36-102">Tok transakcí do služeb pracovních postupů a mimo ně</span><span class="sxs-lookup"><span data-stu-id="1fa36-102">Flowing Transactions into and out of Workflow Services</span></span>
<span data-ttu-id="1fa36-103">Služby pracovních postupů a klienti mohou účastnit transakce.</span><span class="sxs-lookup"><span data-stu-id="1fa36-103">Workflow services and clients can participate in transactions.</span></span>  <span data-ttu-id="1fa36-104">Operace služeb se stanou součástí okolí transakce, umístěte <xref:System.ServiceModel.Activities.Receive> aktivitu v rámci <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="1fa36-104">For a service operation to become part of an ambient transaction, place a <xref:System.ServiceModel.Activities.Receive> activity within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="1fa36-105">Všechna volání prováděných <xref:System.ServiceModel.Activities.Send> nebo <xref:System.ServiceModel.Activities.SendReply> aktivitu v rámci <xref:System.ServiceModel.Activities.TransactedReceiveScope> bude také možné v rámci ambientní transakce.</span><span class="sxs-lookup"><span data-stu-id="1fa36-105">Any calls made by a <xref:System.ServiceModel.Activities.Send> or a <xref:System.ServiceModel.Activities.SendReply> activity within the <xref:System.ServiceModel.Activities.TransactedReceiveScope> will also be made within the ambient transaction.</span></span> <span data-ttu-id="1fa36-106">Klientská aplikace pracovního postupu můžete vytvořit pomocí okolí transakce <xref:System.Activities.Statements.TransactionScope> aktivity a volání operací služby pomocí okolí transakce.</span><span class="sxs-lookup"><span data-stu-id="1fa36-106">A workflow client application can create an ambient transaction by using the <xref:System.Activities.Statements.TransactionScope> activity and call service operations using the ambient transaction.</span></span> <span data-ttu-id="1fa36-107">Toto téma vás provede procesem vytvoření služby pracovních postupů a pracovních postupů klienta, který se podílet na transakcích.</span><span class="sxs-lookup"><span data-stu-id="1fa36-107">This topic walks you through creating a workflow service and workflow client that participate in transactions.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="1fa36-108">Pokud instance služby pracovního postupu je načten v rámci transakce a obsahuje pracovní postup <xref:System.Activities.Statements.Persist> aktivity, instance pracovního postupu se zablokuje, dokud nebude transakce vyprší časový limit.</span><span class="sxs-lookup"><span data-stu-id="1fa36-108">If a workflow service instance is loaded within a transaction and the workflow contains a <xref:System.Activities.Statements.Persist> activity, the workflow instance will hang until the transaction times out.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1fa36-109">Vždy, když použijete <xref:System.ServiceModel.Activities.TransactedReceiveScope> doporučujeme umístit všechny přijme v pracovním postupu v rámci <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="1fa36-109">Whenever you use a <xref:System.ServiceModel.Activities.TransactedReceiveScope> it is recommended to place all Receives in the workflow within <xref:System.ServiceModel.Activities.TransactedReceiveScope> activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1fa36-110">Při použití <xref:System.ServiceModel.Activities.TransactedReceiveScope> a doručování zpráv v nesprávném pořadí, pracovní postup přeruší se při pokusu doručit první zprávu mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="1fa36-110">When using <xref:System.ServiceModel.Activities.TransactedReceiveScope> and messages arrive in the incorrect order, the workflow will be aborted when trying to deliver the first out of order message.</span></span> <span data-ttu-id="1fa36-111">Můžete třeba Ujistěte se, že váš pracovní postup je vždy na konzistentního koncový bod při pracovního postupu nečinné po dlouhou dobu.</span><span class="sxs-lookup"><span data-stu-id="1fa36-111">You must make sure your workflow is always at a consistent stopping point when the workflow idles.</span></span> <span data-ttu-id="1fa36-112">To vám umožní restartovat pracovní postup z předchozího bodu trvalosti by měl pracovní postup přeruší.</span><span class="sxs-lookup"><span data-stu-id="1fa36-112">This will allow you to restart the workflow from a previous persistence point should the workflow be aborted.</span></span>  
  
### <a name="create-a-shared-library"></a><span data-ttu-id="1fa36-113">Vytvořte sdílenou knihovnu</span><span class="sxs-lookup"><span data-stu-id="1fa36-113">Create a shared library</span></span>  
  
1.  <span data-ttu-id="1fa36-114">Vytvoření nové prázdné řešení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1fa36-114">Create a new empty Visual Studio Solution.</span></span>  
  
2.  <span data-ttu-id="1fa36-115">Přidat nový projekt knihovny tříd s názvem `Common`.</span><span class="sxs-lookup"><span data-stu-id="1fa36-115">Add a new class library project called `Common`.</span></span> <span data-ttu-id="1fa36-116">Přidejte odkazy na následující sestavení:</span><span class="sxs-lookup"><span data-stu-id="1fa36-116">Add references to the following assemblies:</span></span>  
  
    -   <span data-ttu-id="1fa36-117">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="1fa36-117">System.Activities.dll</span></span>  
  
    -   <span data-ttu-id="1fa36-118">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="1fa36-118">System.ServiceModel.dll</span></span>  
  
    -   <span data-ttu-id="1fa36-119">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="1fa36-119">System.ServiceModel.Activities.dll</span></span>  
  
    -   <span data-ttu-id="1fa36-120">System.Transactions.dll</span><span class="sxs-lookup"><span data-stu-id="1fa36-120">System.Transactions.dll</span></span>  
  
3.  <span data-ttu-id="1fa36-121">Přidejte novou třídu s názvem `PrintTransactionInfo` k `Common` projektu.</span><span class="sxs-lookup"><span data-stu-id="1fa36-121">Add a new class called `PrintTransactionInfo` to the `Common` project.</span></span> <span data-ttu-id="1fa36-122">Tato třída je odvozena z <xref:System.Activities.NativeActivity> a přetížení <xref:System.Activities.NativeActivity.Execute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1fa36-122">This class is derived from <xref:System.Activities.NativeActivity> and overloads the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
    ```  
    using System;  
    using System;  
    using System.Activities;  
    using System.Transactions;  
  
    namespace Common  
    {  
        public class PrintTransactionInfo : NativeActivity  
        {  
            protected override void Execute(NativeActivityContext context)  
            {  
                RuntimeTransactionHandle rth = context.Properties.Find(typeof(RuntimeTransactionHandle).FullName) as RuntimeTransactionHandle;  
  
                if (rth == null)  
                {  
                    Console.WriteLine("There is no ambient RuntimeTransactionHandle");  
                }  
  
                Transaction t = rth.GetCurrentTransaction(context);  
  
                if (t == null)  
                {  
                    Console.WriteLine("There is no ambient transaction");  
                }  
                else  
                {  
                    Console.WriteLine("Transaction: {0} is {1}", t.TransactionInformation.DistributedIdentifier, t.TransactionInformation.Status);  
                }  
            }  
        }  
  
    }  
    ```  
  
     <span data-ttu-id="1fa36-123">Toto je nativní aktivitu, která zobrazí informace o okolí transakce a používá se v pracovních postupech služby a klient používat v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="1fa36-123">This is a native activity that displays information about the ambient transaction and is used in both the service and client workflows used in this topic.</span></span> <span data-ttu-id="1fa36-124">Sestavte řešení, které chcete zpřístupnit tuto aktivitu v **běžné** část **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="1fa36-124">Build the solution to make this activity available in the **Common** section of the **Toolbox**.</span></span>  
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="1fa36-125">Implementace služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1fa36-125">Implement the workflow service</span></span>  
  
1.  <span data-ttu-id="1fa36-126">Přidejte novou službu pracovního postupu WCF volá `WorkflowService` k `Common` projektu.</span><span class="sxs-lookup"><span data-stu-id="1fa36-126">Add a new WCF Workflow Service, called `WorkflowService` to the `Common` project.</span></span> <span data-ttu-id="1fa36-127">Klikněte na tlačítko vpravo `Common` projekt, vyberte **přidat**, **novou položku...** Vyberte **pracovního postupu** pod **nainstalované šablony** a vyberte **služby pracovního postupu WCF**.</span><span class="sxs-lookup"><span data-stu-id="1fa36-127">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **WCF Workflow Service**.</span></span>  
  
     ![Přidání služby pracovních postupů](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2.  <span data-ttu-id="1fa36-129">Odstranit výchozí `ReceiveRequest` a `SendResponse` aktivity.</span><span class="sxs-lookup"><span data-stu-id="1fa36-129">Delete the default `ReceiveRequest` and `SendResponse` activities.</span></span>  
  
3.  <span data-ttu-id="1fa36-130">Přetáhnout myší <xref:System.Activities.Statements.WriteLine> aktivitu `Sequential Service` aktivity.</span><span class="sxs-lookup"><span data-stu-id="1fa36-130">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity into the `Sequential Service` activity.</span></span> <span data-ttu-id="1fa36-131">Nastavte vlastnost text na `"Workflow Service starting ..."` jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1fa36-131">Set the text property to `"Workflow Service starting ..."` as shown in the following example.</span></span>  
  
     <span data-ttu-id="1fa36-132">! [Přidání aktivity WriteLine activity(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg) sekvenční služba</span><span class="sxs-lookup"><span data-stu-id="1fa36-132">![Adding a WriteLine activity to the Sequential Service activity(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg)</span></span>  
  
4.  <span data-ttu-id="1fa36-133">Přetáhnout myší <xref:System.ServiceModel.Activities.TransactedReceiveScope> po <xref:System.Activities.Statements.WriteLine> aktivity.</span><span class="sxs-lookup"><span data-stu-id="1fa36-133">Drag and drop a <xref:System.ServiceModel.Activities.TransactedReceiveScope> after the <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="1fa36-134"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Aktivit najdete v **zasílání zpráv** část **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="1fa36-134">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity can be found in the **Messaging** section of the **Toolbox**.</span></span> <span data-ttu-id="1fa36-135"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Aktivity se skládá ze dvou částí **žádosti** a **tělo**.</span><span class="sxs-lookup"><span data-stu-id="1fa36-135">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity is composed of two sections **Request** and **Body**.</span></span> <span data-ttu-id="1fa36-136">**Žádosti** oddíl obsahuje <xref:System.ServiceModel.Activities.Receive> aktivity.</span><span class="sxs-lookup"><span data-stu-id="1fa36-136">The **Request** section contains the <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="1fa36-137">**Tělo** oddíl obsahuje aktivity ke spuštění v rámci transakce po byla přijata zpráva.</span><span class="sxs-lookup"><span data-stu-id="1fa36-137">The **Body** section contains the activities to execute within a transaction after a message has been received.</span></span>  
  
     ![Přidání aktivity TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5.  <span data-ttu-id="1fa36-139">Vyberte <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity a kliknutím **proměnné** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="1fa36-139">Select the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity and click the **Variables** button.</span></span> <span data-ttu-id="1fa36-140">Přidejte následující proměnné.</span><span class="sxs-lookup"><span data-stu-id="1fa36-140">Add the following variables.</span></span>  
  
     ![Přidávání proměnných do TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    >  <span data-ttu-id="1fa36-142">Můžete odstranit datovou proměnnou, která je k dispozici ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="1fa36-142">You can delete the data variable that is there by default.</span></span> <span data-ttu-id="1fa36-143">Můžete také použít existující proměnnou popisovač.</span><span class="sxs-lookup"><span data-stu-id="1fa36-143">You can also use the existing handle variable.</span></span>  
  
6.  <span data-ttu-id="1fa36-144">Přetáhnout myší <xref:System.ServiceModel.Activities.Receive> aktivitu v rámci **žádosti** část <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="1fa36-144">Drag and drop a <xref:System.ServiceModel.Activities.Receive> activity within the **Request** section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="1fa36-145">Nastavte následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="1fa36-145">Set the following properties:</span></span>  
  
    |<span data-ttu-id="1fa36-146">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="1fa36-146">Property</span></span>|<span data-ttu-id="1fa36-147">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1fa36-147">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="1fa36-148">CanCreateInstance</span><span class="sxs-lookup"><span data-stu-id="1fa36-148">CanCreateInstance</span></span>|<span data-ttu-id="1fa36-149">True (zaškrtávací políčko)</span><span class="sxs-lookup"><span data-stu-id="1fa36-149">True (check the checkbox)</span></span>|  
    |<span data-ttu-id="1fa36-150">OperationName</span><span class="sxs-lookup"><span data-stu-id="1fa36-150">OperationName</span></span>|<span data-ttu-id="1fa36-151">StartSample</span><span class="sxs-lookup"><span data-stu-id="1fa36-151">StartSample</span></span>|  
    |<span data-ttu-id="1fa36-152">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="1fa36-152">ServiceContractName</span></span>|<span data-ttu-id="1fa36-153">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="1fa36-153">ITransactionSample</span></span>|  
  
     <span data-ttu-id="1fa36-154">Pracovní postup by měl vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="1fa36-154">The workflow should look like this:</span></span>  
  
     ![Přidání aktivity Receive](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7.  <span data-ttu-id="1fa36-156">Klikněte na tlačítko **definovat...**  propojit <xref:System.ServiceModel.Activities.Receive> aktivity a proveďte následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="1fa36-156">Click the **Define...** link in the <xref:System.ServiceModel.Activities.Receive> activity and make the following settings:</span></span>  
  
     ![Nastavení zpráv aktivity Receive](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8.  <span data-ttu-id="1fa36-158">Přetáhnout myší <xref:System.Activities.Statements.Sequence> aktivity do těla oddílu <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="1fa36-158">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the Body section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="1fa36-159">V rámci <xref:System.Activities.Statements.Sequence> aktivity přetáhnout myší dvě <xref:System.Activities.Statements.WriteLine> aktivity a nastavte <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnosti, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="1fa36-159">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop two <xref:System.Activities.Statements.WriteLine> activities and set the <xref:System.Activities.Statements.WriteLine.Text%2A> properties as shown in the following table.</span></span>  
  
    |<span data-ttu-id="1fa36-160">Aktivita</span><span class="sxs-lookup"><span data-stu-id="1fa36-160">Activity</span></span>|<span data-ttu-id="1fa36-161">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1fa36-161">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="1fa36-162">1. WriteLine</span><span class="sxs-lookup"><span data-stu-id="1fa36-162">1st WriteLine</span></span>|<span data-ttu-id="1fa36-163">"Service: Zobrazit dokončené"</span><span class="sxs-lookup"><span data-stu-id="1fa36-163">"Service: Receive Completed"</span></span>|  
    |<span data-ttu-id="1fa36-164">2. WriteLine</span><span class="sxs-lookup"><span data-stu-id="1fa36-164">2nd WriteLine</span></span>|<span data-ttu-id="1fa36-165">"Service: Přijata = "+ requestMessage</span><span class="sxs-lookup"><span data-stu-id="1fa36-165">"Service: Received = " + requestMessage</span></span>|  
  
     <span data-ttu-id="1fa36-166">Pracovní postup by teď měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="1fa36-166">The workflow should now look like this:</span></span>  
  
     ![Pořadí po přidání aktivity WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. <span data-ttu-id="1fa36-168">Přetáhnout myší `PrintTransactionInfo` aktivitu po druhé <xref:System.Activities.Statements.WriteLine> aktivity v **tělo** v <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="1fa36-168">Drag and drop the `PrintTransactionInfo` activity after the second <xref:System.Activities.Statements.WriteLine> activity in the **Body** in the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span>  
  
     ![Po přidání PrintTransactionInfo pořadí](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. <span data-ttu-id="1fa36-170">Přetáhnout myší <xref:System.Activities.Statements.Assign> aktivity po `PrintTransactionInfo` aktivity a nastavte jeho vlastnosti podle následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="1fa36-170">Drag and drop an <xref:System.Activities.Statements.Assign> activity after the `PrintTransactionInfo` activity and set its properties according to the following table.</span></span>  
  
    |<span data-ttu-id="1fa36-171">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="1fa36-171">Property</span></span>|<span data-ttu-id="1fa36-172">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1fa36-172">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="1fa36-173">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="1fa36-173">To</span></span>|<span data-ttu-id="1fa36-174">replyMessage</span><span class="sxs-lookup"><span data-stu-id="1fa36-174">replyMessage</span></span>|  
    |<span data-ttu-id="1fa36-175">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1fa36-175">Value</span></span>|<span data-ttu-id="1fa36-176">"Service: Odeslání odpovědi."</span><span class="sxs-lookup"><span data-stu-id="1fa36-176">"Service: Sending reply."</span></span>|  
  
11. <span data-ttu-id="1fa36-177">Přetáhnout myší <xref:System.Activities.Statements.WriteLine> aktivity po <xref:System.Activities.Statements.Assign> aktivity a nastavte jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost "Service: Začněte odpověď."</span><span class="sxs-lookup"><span data-stu-id="1fa36-177">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.Activities.Statements.Assign> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Begin reply."</span></span>  
  
     <span data-ttu-id="1fa36-178">Pracovní postup by teď měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="1fa36-178">The workflow should now look like this:</span></span>  
  
     ![Po přidání přiřadit a WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. <span data-ttu-id="1fa36-180">Klikněte pravým tlačítkem myši <xref:System.ServiceModel.Activities.Receive> aktivitu a vyberte **vytvořit odeslání odpovědi SendReply** a vložte za poslední <xref:System.Activities.Statements.WriteLine> aktivity.</span><span class="sxs-lookup"><span data-stu-id="1fa36-180">Right click the <xref:System.ServiceModel.Activities.Receive> activity and select **Create SendReply** and paste it after the last <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="1fa36-181">Klikněte na tlačítko **definovat...**  propojit `SendReplyToReceive` aktivity a proveďte následující nastavení.</span><span class="sxs-lookup"><span data-stu-id="1fa36-181">Click the **Define...** link in the `SendReplyToReceive` activity and make the following settings.</span></span>  
  
     ![Nastavení zpráva odpovědi](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. <span data-ttu-id="1fa36-183">Přetáhnout myší <xref:System.Activities.Statements.WriteLine> aktivity po `SendReplyToReceive` aktivity a nastavte má <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost "Service: Byla odeslána odpověď."</span><span class="sxs-lookup"><span data-stu-id="1fa36-183">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `SendReplyToReceive` activity and set it’s <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Reply sent."</span></span>  
  
14. <span data-ttu-id="1fa36-184">Přetáhnout myší <xref:System.Activities.Statements.WriteLine> aktivity v dolní části pracovního postupu a nastavte jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost "Service: Pracovní postup skončí, stisknutím klávesy ENTER ukončete."</span><span class="sxs-lookup"><span data-stu-id="1fa36-184">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the bottom of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Workflow ends, press ENTER to exit."</span></span>  
  
     <span data-ttu-id="1fa36-185">Pracovní postup dokončený služby by měl vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="1fa36-185">The completed service workflow should look like this:</span></span>  
  
     ![Dokončení pracovního postupu služby](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a><span data-ttu-id="1fa36-187">Implementace klienta pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1fa36-187">Implement the workflow client</span></span>  
  
1.  <span data-ttu-id="1fa36-188">Přidat novou aplikaci pracovního postupu WCF, s názvem `WorkflowClient` k `Common` projektu.</span><span class="sxs-lookup"><span data-stu-id="1fa36-188">Add a new WCF Workflow application, called `WorkflowClient` to the `Common` project.</span></span> <span data-ttu-id="1fa36-189">Klikněte na tlačítko vpravo `Common` projekt, vyberte **přidat**, **novou položku...** Vyberte **pracovního postupu** pod **nainstalované šablony** a vyberte **aktivity**.</span><span class="sxs-lookup"><span data-stu-id="1fa36-189">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **Activity**.</span></span>  
  
     ![Přidání aktivity projektu](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2.  <span data-ttu-id="1fa36-191">Přetáhnout myší <xref:System.Activities.Statements.Sequence> aktivity na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="1fa36-191">Drag and drop a <xref:System.Activities.Statements.Sequence> activity onto the design surface.</span></span>  
  
3.  <span data-ttu-id="1fa36-192">V rámci <xref:System.Activities.Statements.Sequence> přetáhnout aktivity <xref:System.Activities.Statements.WriteLine> aktivity a nastavte jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost `"Client: Workflow starting"`.</span><span class="sxs-lookup"><span data-stu-id="1fa36-192">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop a <xref:System.Activities.Statements.WriteLine> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to `"Client: Workflow starting"`.</span></span> <span data-ttu-id="1fa36-193">Pracovní postup by teď měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="1fa36-193">The workflow should now look like this:</span></span>  
  
     ![Přidání aktivity WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4.  <span data-ttu-id="1fa36-195">Přetáhnout myší <xref:System.Activities.Statements.TransactionScope> aktivity po <xref:System.Activities.Statements.WriteLine> aktivity.</span><span class="sxs-lookup"><span data-stu-id="1fa36-195">Drag and drop a <xref:System.Activities.Statements.TransactionScope> activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  <span data-ttu-id="1fa36-196">Vyberte <xref:System.Activities.Statements.TransactionScope> aktivity, klikněte na tlačítko proměnné a přidejte následující proměnné.</span><span class="sxs-lookup"><span data-stu-id="1fa36-196">Select the <xref:System.Activities.Statements.TransactionScope> activity, click the Variables button and add the following variables.</span></span>  
  
     ![Přidejte proměnné do objektu TransactionScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5.  <span data-ttu-id="1fa36-198">Přetáhnout myší <xref:System.Activities.Statements.Sequence> aktivity do textu <xref:System.Activities.Statements.TransactionScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="1fa36-198">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the body of the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
6.  <span data-ttu-id="1fa36-199">Přetáhnout myší `PrintTransactionInfo` aktivitu v rámci <xref:System.Activities.Statements.Sequence></span><span class="sxs-lookup"><span data-stu-id="1fa36-199">Drag and drop a `PrintTransactionInfo` activity within the <xref:System.Activities.Statements.Sequence></span></span>  
  
7.  <span data-ttu-id="1fa36-200">Přetáhnout myší <xref:System.Activities.Statements.WriteLine> aktivity po `PrintTransactionInfo` aktivity a nastavte jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost "klienta: Od odeslání".</span><span class="sxs-lookup"><span data-stu-id="1fa36-200">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `PrintTransactionInfo` activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Beginning Send".</span></span> <span data-ttu-id="1fa36-201">Pracovní postup by teď měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="1fa36-201">The workflow should now look like this:</span></span>  
  
     ![Přidání klienta: Od aktivity odesílání](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8.  <span data-ttu-id="1fa36-203">Přetáhnout myší <xref:System.ServiceModel.Activities.Send> aktivity po <xref:System.Activities.Statements.Assign> aktivity a nastavte následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="1fa36-203">Drag and drop a <xref:System.ServiceModel.Activities.Send> activity after the <xref:System.Activities.Statements.Assign> activity and set the following properties:</span></span>  
  
    |<span data-ttu-id="1fa36-204">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="1fa36-204">Property</span></span>|<span data-ttu-id="1fa36-205">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1fa36-205">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="1fa36-206">EndpointConfigurationName</span><span class="sxs-lookup"><span data-stu-id="1fa36-206">EndpointConfigurationName</span></span>|<span data-ttu-id="1fa36-207">workflowServiceEndpoint</span><span class="sxs-lookup"><span data-stu-id="1fa36-207">workflowServiceEndpoint</span></span>|  
    |<span data-ttu-id="1fa36-208">OperationName</span><span class="sxs-lookup"><span data-stu-id="1fa36-208">OperationName</span></span>|<span data-ttu-id="1fa36-209">StartSample</span><span class="sxs-lookup"><span data-stu-id="1fa36-209">StartSample</span></span>|  
    |<span data-ttu-id="1fa36-210">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="1fa36-210">ServiceContractName</span></span>|<span data-ttu-id="1fa36-211">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="1fa36-211">ITransactionSample</span></span>|  
  
     <span data-ttu-id="1fa36-212">Pracovní postup by teď měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="1fa36-212">The workflow should now look like this:</span></span>  
  
     ![Nastavení vlastnosti aktivity Send](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. <span data-ttu-id="1fa36-214">Klikněte na tlačítko **definovat...**  odkaz a proveďte následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="1fa36-214">Click the **Define...** link and make the following settings:</span></span>  
  
     ![Odeslání zprávy nastavení aktivity](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. <span data-ttu-id="1fa36-216">Klikněte pravým tlačítkem myši <xref:System.ServiceModel.Activities.Send> aktivitu a vyberte **vytvořit ReceiveReply**.</span><span class="sxs-lookup"><span data-stu-id="1fa36-216">Right click the <xref:System.ServiceModel.Activities.Send> activity and select **Create ReceiveReply**.</span></span> <span data-ttu-id="1fa36-217"><xref:System.ServiceModel.Activities.ReceiveReply> Aktivity se automaticky umístí po <xref:System.ServiceModel.Activities.Send> aktivity.</span><span class="sxs-lookup"><span data-stu-id="1fa36-217">The <xref:System.ServiceModel.Activities.ReceiveReply> activity will be automatically placed after the <xref:System.ServiceModel.Activities.Send> activity.</span></span>  
  
11. <span data-ttu-id="1fa36-218">Klikněte na tlačítko... definovat odkaz na aktivitu ReceiveReplyForSend a proveďte následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="1fa36-218">Click the Define... link on the ReceiveReplyForSend activity and make the following settings:</span></span>  
  
     ![Nastavení ReceiveForSend zprávy](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. <span data-ttu-id="1fa36-220">Přetáhnout myší <xref:System.Activities.Statements.WriteLine> aktivity mezi <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity a nastavte jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost "klienta: Odeslat kompletní."</span><span class="sxs-lookup"><span data-stu-id="1fa36-220">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity between the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> activities and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Send complete."</span></span>  
  
13. <span data-ttu-id="1fa36-221">Přetáhnout myší <xref:System.Activities.Statements.WriteLine> aktivity po <xref:System.ServiceModel.Activities.ReceiveReply> aktivity a nastavte jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost "na straně klienta: Přijatá odpověď = "+ replyMessage</span><span class="sxs-lookup"><span data-stu-id="1fa36-221">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.ServiceModel.Activities.ReceiveReply> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client side: Reply received = " + replyMessage</span></span>  
  
14. <span data-ttu-id="1fa36-222">Přetáhnout myší `PrintTransactionInfo` aktivity po <xref:System.Activities.Statements.WriteLine> aktivity.</span><span class="sxs-lookup"><span data-stu-id="1fa36-222">Drag and drop a `PrintTransactionInfo` activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
15. <span data-ttu-id="1fa36-223">Přetáhnout myší <xref:System.Activities.Statements.WriteLine> aktivity na konci pracovního postupu a nastavte jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost "Klienta pracovní postup ukončen."</span><span class="sxs-lookup"><span data-stu-id="1fa36-223">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the end of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client workflow ends."</span></span> <span data-ttu-id="1fa36-224">Pracovní postup dokončený klienta by mělo vypadat jako na následujícím diagramu.</span><span class="sxs-lookup"><span data-stu-id="1fa36-224">The completed client workflow should look like the following diagram.</span></span>  
  
     ![Pracovní postup dokončený klienta](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. <span data-ttu-id="1fa36-226">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="1fa36-226">Build the solution.</span></span>  
  
### <a name="create-the-service-application"></a><span data-ttu-id="1fa36-227">Vytvoření aplikace služby</span><span class="sxs-lookup"><span data-stu-id="1fa36-227">Create the Service application</span></span>  
  
1.  <span data-ttu-id="1fa36-228">Přidat nový projekt konzolové aplikace s názvem `Service` do řešení.</span><span class="sxs-lookup"><span data-stu-id="1fa36-228">Add a new Console Application project called `Service` to the solution.</span></span> <span data-ttu-id="1fa36-229">Přidejte odkazy na následující sestavení:</span><span class="sxs-lookup"><span data-stu-id="1fa36-229">Add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="1fa36-230">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="1fa36-230">System.Activities.dll</span></span>  
  
    2.  <span data-ttu-id="1fa36-231">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="1fa36-231">System.ServiceModel.dll</span></span>  
  
    3.  <span data-ttu-id="1fa36-232">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="1fa36-232">System.ServiceModel.Activities.dll</span></span>  
  
2.  <span data-ttu-id="1fa36-233">Otevřete vygenerovaný soubor Program.cs a následující kód:</span><span class="sxs-lookup"><span data-stu-id="1fa36-233">Open the generated Program.cs file and the following code:</span></span>  
  
    ```  
    static void Main()  
          {  
              Console.WriteLine("Building the server.");  
              using (WorkflowServiceHost host = new WorkflowServiceHost(new DeclarativeServiceWorkflow(), new Uri("net.tcp://localhost:8000/TransactedReceiveService/Declarative")))  
              {                
                  //Start the server  
                  host.Open();  
                  Console.WriteLine("Service started.");  
  
                  Console.WriteLine();  
                  Console.ReadLine();  
                  //Shutdown  
                  host.Close();  
              };         
          }  
    ```  
  
3.  <span data-ttu-id="1fa36-234">Následující soubor app.config přidejte do projektu.</span><span class="sxs-lookup"><span data-stu-id="1fa36-234">Add the following app.config file to the project.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <!-- Copyright © Microsoft Corporation.  All rights reserved. -->  
    <configuration>  
        <system.serviceModel>  
            <bindings>  
                <netTcpBinding>  
                    <binding transactionFlow="true" />  
                </netTcpBinding>  
            </bindings>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="create-the-client-application"></a><span data-ttu-id="1fa36-235">Vytvoření klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="1fa36-235">Create the client application</span></span>  
  
1.  <span data-ttu-id="1fa36-236">Přidat nový projekt konzolové aplikace s názvem `Client` do řešení.</span><span class="sxs-lookup"><span data-stu-id="1fa36-236">Add a new Console Application project called `Client` to the solution.</span></span> <span data-ttu-id="1fa36-237">Přidejte odkaz na System.Activities.dll.</span><span class="sxs-lookup"><span data-stu-id="1fa36-237">Add a reference to System.Activities.dll.</span></span>  
  
2.  <span data-ttu-id="1fa36-238">Otevřete soubor program.cs a přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="1fa36-238">Open the program.cs file and add the following code.</span></span>  
  
    ```  
    class Program  
        {  
  
            private static AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
            static void Main(string[] args)  
            {  
                //Build client  
                Console.WriteLine("Building the client.");  
                WorkflowApplication client = new WorkflowApplication(new DeclarativeClientWorkflow());  
                client.Completed = Program.Completed;  
                client.Aborted = Program.Aborted;  
                client.OnUnhandledException = Program.OnUnhandledException;  
  
                //Wait for service to start  
                Console.WriteLine("Press ENTER once service is started.");  
                Console.ReadLine();  
  
                //Start the client              
                Console.WriteLine("Starting the client.");  
                client.Run();  
                syncEvent.WaitOne();  
  
                //Sample complete  
                Console.WriteLine();  
                Console.WriteLine("Client complete. Press ENTER to exit.");  
                Console.ReadLine();  
            }  
  
            private static void Completed(WorkflowApplicationCompletedEventArgs e)  
            {  
                Program.syncEvent.Set();  
            }  
  
            private static void Aborted(WorkflowApplicationAbortedEventArgs e)  
            {  
                Console.WriteLine("Client Aborted: {0}", e.Reason);  
                Program.syncEvent.Set();  
            }  
  
            private static UnhandledExceptionAction OnUnhandledException(WorkflowApplicationUnhandledExceptionEventArgs e)  
            {  
                Console.WriteLine("Client had an unhandled exception: {0}", e.UnhandledException);  
                return UnhandledExceptionAction.Cancel;  
            }  
        }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1fa36-239">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1fa36-239">See also</span></span>

- [<span data-ttu-id="1fa36-240">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="1fa36-240">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="1fa36-241">Přehled transakcí ve Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="1fa36-241">Windows Communication Foundation Transactions Overview</span></span>](../../../../docs/framework/wcf/feature-details/transactions-overview.md)
