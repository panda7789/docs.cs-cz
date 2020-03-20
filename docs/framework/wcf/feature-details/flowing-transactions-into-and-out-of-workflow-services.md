---
title: Tok transakcí do služeb pracovních postupů a mimo ně
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: fe03047dd931d25ec94bbc5e00c479d1b42397bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185269"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a><span data-ttu-id="a8458-102">Tok transakcí do služeb pracovních postupů a mimo ně</span><span class="sxs-lookup"><span data-stu-id="a8458-102">Flowing Transactions into and out of Workflow Services</span></span>
<span data-ttu-id="a8458-103">Služby pracovního postupu a klienti se mohou účastnit transakcí.</span><span class="sxs-lookup"><span data-stu-id="a8458-103">Workflow services and clients can participate in transactions.</span></span>  <span data-ttu-id="a8458-104">Chcete-li, aby se operace služby <xref:System.ServiceModel.Activities.Receive> stala součástí <xref:System.ServiceModel.Activities.TransactedReceiveScope> transakce okolí, umístěte aktivitu v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="a8458-104">For a service operation to become part of an ambient transaction, place a <xref:System.ServiceModel.Activities.Receive> activity within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="a8458-105">Jakékoli hovory provedené <xref:System.ServiceModel.Activities.Send> nebo <xref:System.ServiceModel.Activities.SendReply> aktivity <xref:System.ServiceModel.Activities.TransactedReceiveScope> v rámci bude také v rámci okolí transakce.</span><span class="sxs-lookup"><span data-stu-id="a8458-105">Any calls made by a <xref:System.ServiceModel.Activities.Send> or a <xref:System.ServiceModel.Activities.SendReply> activity within the <xref:System.ServiceModel.Activities.TransactedReceiveScope> will also be made within the ambient transaction.</span></span> <span data-ttu-id="a8458-106">Klientská aplikace pracovního postupu můžete <xref:System.Activities.Statements.TransactionScope> vytvořit okolní transakce pomocí operace aktivity a volání služby pomocí okolí transakce.</span><span class="sxs-lookup"><span data-stu-id="a8458-106">A workflow client application can create an ambient transaction by using the <xref:System.Activities.Statements.TransactionScope> activity and call service operations using the ambient transaction.</span></span> <span data-ttu-id="a8458-107">Toto téma vás provede vytvořením služby pracovního postupu a klienta pracovního postupu, kteří se účastní transakcí.</span><span class="sxs-lookup"><span data-stu-id="a8458-107">This topic walks you through creating a workflow service and workflow client that participate in transactions.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="a8458-108">Pokud je instance služby pracovního postupu načtena v rámci transakce a pracovní postup obsahuje aktivitu, <xref:System.Activities.Statements.Persist> instance pracovního postupu se zablokuje, dokud neskončí časový výplní transakce.</span><span class="sxs-lookup"><span data-stu-id="a8458-108">If a workflow service instance is loaded within a transaction and the workflow contains a <xref:System.Activities.Statements.Persist> activity, the workflow instance will block until the transaction times out.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a8458-109">Vždy, když <xref:System.ServiceModel.Activities.TransactedReceiveScope> používáte se doporučuje umístit všechny <xref:System.ServiceModel.Activities.TransactedReceiveScope> Příjem v pracovním postupu v rámci aktivit.</span><span class="sxs-lookup"><span data-stu-id="a8458-109">Whenever you use a <xref:System.ServiceModel.Activities.TransactedReceiveScope> it is recommended to place all Receives in the workflow within <xref:System.ServiceModel.Activities.TransactedReceiveScope> activities.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a8458-110">Při <xref:System.ServiceModel.Activities.TransactedReceiveScope> použití a zprávy dorazí v nesprávném pořadí, pracovní postup bude přerušena při pokusu o doručení první zprávy mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="a8458-110">When using <xref:System.ServiceModel.Activities.TransactedReceiveScope> and messages arrive in the incorrect order, the workflow will be aborted when trying to deliver the first out of order message.</span></span> <span data-ttu-id="a8458-111">Je nutné zajistit, aby byl pracovní postup vždy v konzistentním bodě zastavení při nečinnosti pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a8458-111">You must make sure your workflow is always at a consistent stopping point when the workflow idles.</span></span> <span data-ttu-id="a8458-112">To vám umožní restartovat pracovní postup z předchozího bodu trvalosti, pokud by byl pracovní postup přerušen.</span><span class="sxs-lookup"><span data-stu-id="a8458-112">This will allow you to restart the workflow from a previous persistence point should the workflow be aborted.</span></span>  
  
### <a name="create-a-shared-library"></a><span data-ttu-id="a8458-113">Vytvoření sdílené knihovny</span><span class="sxs-lookup"><span data-stu-id="a8458-113">Create a shared library</span></span>  
  
1. <span data-ttu-id="a8458-114">Vytvořte nové prázdné řešení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a8458-114">Create a new empty Visual Studio Solution.</span></span>  
  
2. <span data-ttu-id="a8458-115">Přidejte nový projekt `Common`knihovny tříd s názvem .</span><span class="sxs-lookup"><span data-stu-id="a8458-115">Add a new class library project called `Common`.</span></span> <span data-ttu-id="a8458-116">Přidejte odkazy na následující sestavení:</span><span class="sxs-lookup"><span data-stu-id="a8458-116">Add references to the following assemblies:</span></span>  
  
    - <span data-ttu-id="a8458-117">Soubor System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="a8458-117">System.Activities.dll</span></span>  
  
    - <span data-ttu-id="a8458-118">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="a8458-118">System.ServiceModel.dll</span></span>  
  
    - <span data-ttu-id="a8458-119">Soubor System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="a8458-119">System.ServiceModel.Activities.dll</span></span>  
  
    - <span data-ttu-id="a8458-120">System.Transactions.dll</span><span class="sxs-lookup"><span data-stu-id="a8458-120">System.Transactions.dll</span></span>  
  
3. <span data-ttu-id="a8458-121">Přidejte novou `PrintTransactionInfo` třídu `Common` volanou do projektu.</span><span class="sxs-lookup"><span data-stu-id="a8458-121">Add a new class called `PrintTransactionInfo` to the `Common` project.</span></span> <span data-ttu-id="a8458-122">Tato třída je <xref:System.Activities.NativeActivity> odvozen a <xref:System.Activities.NativeActivity.Execute%2A> přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="a8458-122">This class is derived from <xref:System.Activities.NativeActivity> and overloads the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
    ```csharp
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
  
     <span data-ttu-id="a8458-123">Toto je nativní aktivita, která zobrazuje informace o okolí transakce a používá se v pracovních postupech služby i klienta použitých v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="a8458-123">This is a native activity that displays information about the ambient transaction and is used in both the service and client workflows used in this topic.</span></span> <span data-ttu-id="a8458-124">Vytvořte řešení, které tuto aktivitu zpřístupní v **části Společné** v **panelu nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="a8458-124">Build the solution to make this activity available in the **Common** section of the **Toolbox**.</span></span>  
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="a8458-125">Implementace služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="a8458-125">Implement the workflow service</span></span>  
  
1. <span data-ttu-id="a8458-126">Přidejte novou službu pracovního postupu WCF, která je volána `WorkflowService` do `Common` projektu.</span><span class="sxs-lookup"><span data-stu-id="a8458-126">Add a new WCF Workflow Service, called `WorkflowService` to the `Common` project.</span></span> <span data-ttu-id="a8458-127">Chcete-li to `Common` provést pravým tlačítkem myši na projekt, vyberte **přidat**, **nová položka ...**, vybrat pracovní **postup** v části **Nainstalované šablony** a vyberte **službu pracovního postupu WCF**.</span><span class="sxs-lookup"><span data-stu-id="a8458-127">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **WCF Workflow Service**.</span></span>  
  
     ![Přidání služby pracovního postupu](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. <span data-ttu-id="a8458-129">Odstraňte `ReceiveRequest` výchozí `SendResponse` nastavení a aktivity.</span><span class="sxs-lookup"><span data-stu-id="a8458-129">Delete the default `ReceiveRequest` and `SendResponse` activities.</span></span>  
  
3. <span data-ttu-id="a8458-130">Přetáhněte aktivitu <xref:System.Activities.Statements.WriteLine> do `Sequential Service` aktivity.</span><span class="sxs-lookup"><span data-stu-id="a8458-130">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity into the `Sequential Service` activity.</span></span> <span data-ttu-id="a8458-131">Nastavte vlastnost text `"Workflow Service starting ..."` tak, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a8458-131">Set the text property to `"Workflow Service starting ..."` as shown in the following example.</span></span>  
  
     <span data-ttu-id="a8458-132">! [Přidání aktivity WriteLine do aktivity sekvenční služby(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg)</span><span class="sxs-lookup"><span data-stu-id="a8458-132">![Adding a WriteLine activity to the Sequential Service activity(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg)</span></span>  
  
4. <span data-ttu-id="a8458-133">Za aktivitou <xref:System.ServiceModel.Activities.TransactedReceiveScope> <xref:System.Activities.Statements.WriteLine> přetáhněte a.</span><span class="sxs-lookup"><span data-stu-id="a8458-133">Drag and drop a <xref:System.ServiceModel.Activities.TransactedReceiveScope> after the <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="a8458-134">Aktivitu <xref:System.ServiceModel.Activities.TransactedReceiveScope> naleznete v části **Zasílání zpráv** v **panelu nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="a8458-134">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity can be found in the **Messaging** section of the **Toolbox**.</span></span> <span data-ttu-id="a8458-135">Aktivita <xref:System.ServiceModel.Activities.TransactedReceiveScope> se skládá ze dvou částí **Request** a **Body**.</span><span class="sxs-lookup"><span data-stu-id="a8458-135">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity is composed of two sections **Request** and **Body**.</span></span> <span data-ttu-id="a8458-136">Část **Požadavek** <xref:System.ServiceModel.Activities.Receive> obsahuje aktivitu.</span><span class="sxs-lookup"><span data-stu-id="a8458-136">The **Request** section contains the <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="a8458-137">Část **Body** obsahuje aktivity, které mají být provedeny v rámci transakce po přijetí zprávy.</span><span class="sxs-lookup"><span data-stu-id="a8458-137">The **Body** section contains the activities to execute within a transaction after a message has been received.</span></span>  
  
     ![Přidání aktivity TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. <span data-ttu-id="a8458-139">Vyberte <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivitu a klepněte na tlačítko **Proměnné.**</span><span class="sxs-lookup"><span data-stu-id="a8458-139">Select the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity and click the **Variables** button.</span></span> <span data-ttu-id="a8458-140">Přidejte následující proměnné.</span><span class="sxs-lookup"><span data-stu-id="a8458-140">Add the following variables.</span></span>  
  
     ![Přidání proměnných do transactedreceivescope](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > <span data-ttu-id="a8458-142">Můžete odstranit datovou proměnnou, která je k dispozici ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="a8458-142">You can delete the data variable that is there by default.</span></span> <span data-ttu-id="a8458-143">Můžete také použít existující proměnnou popisovače.</span><span class="sxs-lookup"><span data-stu-id="a8458-143">You can also use the existing handle variable.</span></span>  
  
6. <span data-ttu-id="a8458-144">Přetáhněte aktivitu <xref:System.ServiceModel.Activities.Receive> v části **Požadavek** aktivity. <xref:System.ServiceModel.Activities.TransactedReceiveScope></span><span class="sxs-lookup"><span data-stu-id="a8458-144">Drag and drop a <xref:System.ServiceModel.Activities.Receive> activity within the **Request** section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="a8458-145">Nastavte následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="a8458-145">Set the following properties:</span></span>  
  
    |<span data-ttu-id="a8458-146">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="a8458-146">Property</span></span>|<span data-ttu-id="a8458-147">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a8458-147">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="a8458-148">Cancreateinstance</span><span class="sxs-lookup"><span data-stu-id="a8458-148">CanCreateInstance</span></span>|<span data-ttu-id="a8458-149">True (zaškrtněte políčko)</span><span class="sxs-lookup"><span data-stu-id="a8458-149">True (check the checkbox)</span></span>|  
    |<span data-ttu-id="a8458-150">OperationName</span><span class="sxs-lookup"><span data-stu-id="a8458-150">OperationName</span></span>|<span data-ttu-id="a8458-151">StartSample</span><span class="sxs-lookup"><span data-stu-id="a8458-151">StartSample</span></span>|  
    |<span data-ttu-id="a8458-152">Název_kontraktu_service_kontraktu</span><span class="sxs-lookup"><span data-stu-id="a8458-152">ServiceContractName</span></span>|<span data-ttu-id="a8458-153">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="a8458-153">ITransactionSample</span></span>|  
  
     <span data-ttu-id="a8458-154">Pracovní postup by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="a8458-154">The workflow should look like this:</span></span>  
  
     ![Přidání aktivity příjmu](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. <span data-ttu-id="a8458-156">Klikněte na odkaz <xref:System.ServiceModel.Activities.Receive> **Definovat...** v aktivitě a proveďte následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="a8458-156">Click the **Define...** link in the <xref:System.ServiceModel.Activities.Receive> activity and make the following settings:</span></span>  
  
     ![Nastavení nastavení zprávy pro aktivitu příjmu](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. <span data-ttu-id="a8458-158">Přetáhněte aktivitu <xref:System.Activities.Statements.Sequence> do části Tělo <xref:System.ServiceModel.Activities.TransactedReceiveScope>v .</span><span class="sxs-lookup"><span data-stu-id="a8458-158">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the Body section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="a8458-159">V <xref:System.Activities.Statements.Sequence> rámci aktivity <xref:System.Activities.Statements.WriteLine> přetáhněte dvě <xref:System.Activities.Statements.WriteLine.Text%2A> aktivity a nastavte vlastnosti, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="a8458-159">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop two <xref:System.Activities.Statements.WriteLine> activities and set the <xref:System.Activities.Statements.WriteLine.Text%2A> properties as shown in the following table.</span></span>  
  
    |<span data-ttu-id="a8458-160">Aktivita</span><span class="sxs-lookup"><span data-stu-id="a8458-160">Activity</span></span>|<span data-ttu-id="a8458-161">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a8458-161">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="a8458-162">1. WriteLine</span><span class="sxs-lookup"><span data-stu-id="a8458-162">1st WriteLine</span></span>|<span data-ttu-id="a8458-163">"Služba: Příjem dokončen"</span><span class="sxs-lookup"><span data-stu-id="a8458-163">"Service: Receive Completed"</span></span>|  
    |<span data-ttu-id="a8458-164">2. WriteLine</span><span class="sxs-lookup"><span data-stu-id="a8458-164">2nd WriteLine</span></span>|<span data-ttu-id="a8458-165">"Služba: Přijato = " + requestMessage</span><span class="sxs-lookup"><span data-stu-id="a8458-165">"Service: Received = " + requestMessage</span></span>|  
  
     <span data-ttu-id="a8458-166">Pracovní postup by nyní měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="a8458-166">The workflow should now look like this:</span></span>  
  
     ![Posloupnost po přidání aktivit WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. <span data-ttu-id="a8458-168">`PrintTransactionInfo` Přetáhněte aktivitu po <xref:System.Activities.Statements.WriteLine> druhé aktivitě v <xref:System.ServiceModel.Activities.TransactedReceiveScope> **těle** v aktivitě.</span><span class="sxs-lookup"><span data-stu-id="a8458-168">Drag and drop the `PrintTransactionInfo` activity after the second <xref:System.Activities.Statements.WriteLine> activity in the **Body** in the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span>  
  
     ![Sekvence po přidání PrintTransactionInfo](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. <span data-ttu-id="a8458-170">Přetáhněte aktivitu <xref:System.Activities.Statements.Assign> za `PrintTransactionInfo` aktivitou a nastavte její vlastnosti podle následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="a8458-170">Drag and drop an <xref:System.Activities.Statements.Assign> activity after the `PrintTransactionInfo` activity and set its properties according to the following table.</span></span>  
  
    |<span data-ttu-id="a8458-171">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="a8458-171">Property</span></span>|<span data-ttu-id="a8458-172">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a8458-172">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="a8458-173">Akce</span><span class="sxs-lookup"><span data-stu-id="a8458-173">To</span></span>|<span data-ttu-id="a8458-174">replyMessage</span><span class="sxs-lookup"><span data-stu-id="a8458-174">replyMessage</span></span>|  
    |<span data-ttu-id="a8458-175">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a8458-175">Value</span></span>|<span data-ttu-id="a8458-176">"Služba: Odeslání odpovědi."</span><span class="sxs-lookup"><span data-stu-id="a8458-176">"Service: Sending reply."</span></span>|  
  
11. <span data-ttu-id="a8458-177">Po aktivitě <xref:System.Activities.Statements.WriteLine> přetáhněte <xref:System.Activities.Statements.Assign> aktivitu <xref:System.Activities.Statements.WriteLine.Text%2A> a nastavte její vlastnost na "Služba: Zahájit odpověď".</span><span class="sxs-lookup"><span data-stu-id="a8458-177">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.Activities.Statements.Assign> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Begin reply."</span></span>  
  
     <span data-ttu-id="a8458-178">Pracovní postup by nyní měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="a8458-178">The workflow should now look like this:</span></span>  
  
     ![Po přidání přiřadit a writeline](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. <span data-ttu-id="a8458-180">Klikněte <xref:System.ServiceModel.Activities.Receive> pravým tlačítkem myši na aktivitu <xref:System.Activities.Statements.WriteLine> a vyberte **Vytvořit odeslanou odpověď** a vložte ji po poslední aktivitě.</span><span class="sxs-lookup"><span data-stu-id="a8458-180">Right click the <xref:System.ServiceModel.Activities.Receive> activity and select **Create SendReply** and paste it after the last <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="a8458-181">Klikněte na odkaz `SendReplyToReceive` **Definovat...** v aktivitě a proveďte následující nastavení.</span><span class="sxs-lookup"><span data-stu-id="a8458-181">Click the **Define...** link in the `SendReplyToReceive` activity and make the following settings.</span></span>  
  
     ![Nastavení odpovědi na zprávu](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. <span data-ttu-id="a8458-183">Po aktivitě <xref:System.Activities.Statements.WriteLine> přetáhněte `SendReplyToReceive` aktivitu a <xref:System.Activities.Statements.WriteLine.Text%2A> nastavte její vlastnost na "Služba: Odeslaná odpověď".</span><span class="sxs-lookup"><span data-stu-id="a8458-183">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `SendReplyToReceive` activity and set it’s <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Reply sent."</span></span>  
  
14. <span data-ttu-id="a8458-184">Přetáhněte aktivitu <xref:System.Activities.Statements.WriteLine> v dolní části pracovního <xref:System.Activities.Statements.WriteLine.Text%2A> postupu a nastavte její vlastnost na "Služba: Ukončení pracovního postupu, ukončení stisknutím klávesy ENTER".</span><span class="sxs-lookup"><span data-stu-id="a8458-184">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the bottom of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Workflow ends, press ENTER to exit."</span></span>  
  
     <span data-ttu-id="a8458-185">Pracovní postup dokončené služby by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="a8458-185">The completed service workflow should look like this:</span></span>  
  
     ![Dokončení pracovního postupu služby](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a><span data-ttu-id="a8458-187">Implementace klienta pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="a8458-187">Implement the workflow client</span></span>  
  
1. <span data-ttu-id="a8458-188">Přidejte novou aplikaci wcf workflow, volána `WorkflowClient` do `Common` projektu.</span><span class="sxs-lookup"><span data-stu-id="a8458-188">Add a new WCF Workflow application, called `WorkflowClient` to the `Common` project.</span></span> <span data-ttu-id="a8458-189">Chcete-li to `Common` provést pravým tlačítkem myši na projekt, vyberte **přidat**, **nová položka ...**, vybrat pracovní **postup** v části **Nainstalované šablony** a vyberte **aktivita**.</span><span class="sxs-lookup"><span data-stu-id="a8458-189">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **Activity**.</span></span>  
  
     ![Přidání projektu aktivity](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. <span data-ttu-id="a8458-191">Přetáhněte aktivitu <xref:System.Activities.Statements.Sequence> na plochu návrhu.</span><span class="sxs-lookup"><span data-stu-id="a8458-191">Drag and drop a <xref:System.Activities.Statements.Sequence> activity onto the design surface.</span></span>  
  
3. <span data-ttu-id="a8458-192">V <xref:System.Activities.Statements.Sequence> rámci aktivity <xref:System.Activities.Statements.WriteLine> přetáhněte aktivitu a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na `"Client: Workflow starting"`.</span><span class="sxs-lookup"><span data-stu-id="a8458-192">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop a <xref:System.Activities.Statements.WriteLine> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to `"Client: Workflow starting"`.</span></span> <span data-ttu-id="a8458-193">Pracovní postup by nyní měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="a8458-193">The workflow should now look like this:</span></span>  
  
     ![Přidání aktivity WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. <span data-ttu-id="a8458-195">Po aktivitě <xref:System.Activities.Statements.TransactionScope> přetáhněte <xref:System.Activities.Statements.WriteLine> aktivitu.</span><span class="sxs-lookup"><span data-stu-id="a8458-195">Drag and drop a <xref:System.Activities.Statements.TransactionScope> activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  <span data-ttu-id="a8458-196">Vyberte <xref:System.Activities.Statements.TransactionScope> aktivitu, klepněte na tlačítko Proměnné a přidejte následující proměnné.</span><span class="sxs-lookup"><span data-stu-id="a8458-196">Select the <xref:System.Activities.Statements.TransactionScope> activity, click the Variables button and add the following variables.</span></span>  
  
     ![Přidání proměnných do oboru transakce](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. <span data-ttu-id="a8458-198">Přetáhněte aktivitu <xref:System.Activities.Statements.Sequence> do těla <xref:System.Activities.Statements.TransactionScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="a8458-198">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the body of the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
6. <span data-ttu-id="a8458-199">Přetáhněte aktivitu `PrintTransactionInfo` v rámci<xref:System.Activities.Statements.Sequence></span><span class="sxs-lookup"><span data-stu-id="a8458-199">Drag and drop a `PrintTransactionInfo` activity within the <xref:System.Activities.Statements.Sequence></span></span>  
  
7. <span data-ttu-id="a8458-200">Přetáhněte aktivitu <xref:System.Activities.Statements.WriteLine> za `PrintTransactionInfo` aktivitou <xref:System.Activities.Statements.WriteLine.Text%2A> a nastavte její vlastnost na "Klient: Počáteční odeslání".</span><span class="sxs-lookup"><span data-stu-id="a8458-200">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `PrintTransactionInfo` activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Beginning Send".</span></span> <span data-ttu-id="a8458-201">Pracovní postup by nyní měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="a8458-201">The workflow should now look like this:</span></span>  
  
     ![Přidání klienta: Zahájení odesílání aktivit](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. <span data-ttu-id="a8458-203">Přetáhněte aktivitu <xref:System.ServiceModel.Activities.Send> za <xref:System.Activities.Statements.Assign> aktivitou a nastavte následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="a8458-203">Drag and drop a <xref:System.ServiceModel.Activities.Send> activity after the <xref:System.Activities.Statements.Assign> activity and set the following properties:</span></span>  
  
    |<span data-ttu-id="a8458-204">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="a8458-204">Property</span></span>|<span data-ttu-id="a8458-205">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a8458-205">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="a8458-206">Název konfigurace koncového bodu</span><span class="sxs-lookup"><span data-stu-id="a8458-206">EndpointConfigurationName</span></span>|<span data-ttu-id="a8458-207">workflowServiceEndpoint</span><span class="sxs-lookup"><span data-stu-id="a8458-207">workflowServiceEndpoint</span></span>|  
    |<span data-ttu-id="a8458-208">OperationName</span><span class="sxs-lookup"><span data-stu-id="a8458-208">OperationName</span></span>|<span data-ttu-id="a8458-209">StartSample</span><span class="sxs-lookup"><span data-stu-id="a8458-209">StartSample</span></span>|  
    |<span data-ttu-id="a8458-210">Název_kontraktu_service_kontraktu</span><span class="sxs-lookup"><span data-stu-id="a8458-210">ServiceContractName</span></span>|<span data-ttu-id="a8458-211">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="a8458-211">ITransactionSample</span></span>|  
  
     <span data-ttu-id="a8458-212">Pracovní postup by nyní měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="a8458-212">The workflow should now look like this:</span></span>  
  
     ![Nastavení vlastností aktivity Odeslat](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. <span data-ttu-id="a8458-214">Klikněte na odkaz **Definovat...** a proveďte následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="a8458-214">Click the **Define...** link and make the following settings:</span></span>  
  
     ![Odeslat nastavení zprávy o aktivitě](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. <span data-ttu-id="a8458-216">Klepněte <xref:System.ServiceModel.Activities.Send> pravým tlačítkem myši na aktivitu a vyberte **příkaz Vytvořit receivereply**.</span><span class="sxs-lookup"><span data-stu-id="a8458-216">Right click the <xref:System.ServiceModel.Activities.Send> activity and select **Create ReceiveReply**.</span></span> <span data-ttu-id="a8458-217">Aktivita <xref:System.ServiceModel.Activities.ReceiveReply> bude automaticky umístěna po aktivitě. <xref:System.ServiceModel.Activities.Send></span><span class="sxs-lookup"><span data-stu-id="a8458-217">The <xref:System.ServiceModel.Activities.ReceiveReply> activity will be automatically placed after the <xref:System.ServiceModel.Activities.Send> activity.</span></span>  
  
11. <span data-ttu-id="a8458-218">Klikněte na definovat... na aktivitu ReceiveReplyForSend a proveďte následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="a8458-218">Click the Define... link on the ReceiveReplyForSend activity and make the following settings:</span></span>  
  
     ![Nastavení zprávy ReceiveForSend](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. <span data-ttu-id="a8458-220"><xref:System.Activities.Statements.WriteLine> Přetáhněte aktivitu mezi <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> aktivitami <xref:System.Activities.Statements.WriteLine.Text%2A> a nastavte její vlastnost na "Klient: Odeslat dokončeno".</span><span class="sxs-lookup"><span data-stu-id="a8458-220">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity between the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> activities and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Send complete."</span></span>  
  
13. <span data-ttu-id="a8458-221">Přetáhněte aktivitu <xref:System.Activities.Statements.WriteLine> po <xref:System.ServiceModel.Activities.ReceiveReply> aktivitě <xref:System.Activities.Statements.WriteLine.Text%2A> a nastavte její vlastnost na "Strana klienta: Odpověď přijata = " + replyMessage</span><span class="sxs-lookup"><span data-stu-id="a8458-221">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.ServiceModel.Activities.ReceiveReply> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client side: Reply received = " + replyMessage</span></span>  
  
14. <span data-ttu-id="a8458-222">Po aktivitě `PrintTransactionInfo` přetáhněte <xref:System.Activities.Statements.WriteLine> aktivitu.</span><span class="sxs-lookup"><span data-stu-id="a8458-222">Drag and drop a `PrintTransactionInfo` activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
15. <span data-ttu-id="a8458-223">Přetáhněte aktivitu <xref:System.Activities.Statements.WriteLine> na konci pracovního postupu <xref:System.Activities.Statements.WriteLine.Text%2A> a nastavte její vlastnost na "Ukončení pracovního postupu klienta".</span><span class="sxs-lookup"><span data-stu-id="a8458-223">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the end of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client workflow ends."</span></span> <span data-ttu-id="a8458-224">Dokončený pracovní postup klienta by měl vypadat jako následující diagram.</span><span class="sxs-lookup"><span data-stu-id="a8458-224">The completed client workflow should look like the following diagram.</span></span>  
  
     ![Dokončený pracovní postup klienta](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. <span data-ttu-id="a8458-226">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="a8458-226">Build the solution.</span></span>  
  
### <a name="create-the-service-application"></a><span data-ttu-id="a8458-227">Vytvořit aplikaci Service</span><span class="sxs-lookup"><span data-stu-id="a8458-227">Create the Service application</span></span>  
  
1. <span data-ttu-id="a8458-228">Přidejte do řešení `Service` nový projekt konzolové aplikace svolaný do řešení.</span><span class="sxs-lookup"><span data-stu-id="a8458-228">Add a new Console Application project called `Service` to the solution.</span></span> <span data-ttu-id="a8458-229">Přidejte odkazy na následující sestavení:</span><span class="sxs-lookup"><span data-stu-id="a8458-229">Add references to the following assemblies:</span></span>  
  
    1. <span data-ttu-id="a8458-230">Soubor System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="a8458-230">System.Activities.dll</span></span>  
  
    2. <span data-ttu-id="a8458-231">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="a8458-231">System.ServiceModel.dll</span></span>  
  
    3. <span data-ttu-id="a8458-232">Soubor System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="a8458-232">System.ServiceModel.Activities.dll</span></span>  
  
2. <span data-ttu-id="a8458-233">Otevřete vygenerovaný soubor Program.cs a následující kód:</span><span class="sxs-lookup"><span data-stu-id="a8458-233">Open the generated Program.cs file and the following code:</span></span>  
  
    ```csharp
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
  
3. <span data-ttu-id="a8458-234">Přidejte do projektu následující soubor app.config.</span><span class="sxs-lookup"><span data-stu-id="a8458-234">Add the following app.config file to the project.</span></span>  
  
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
  
### <a name="create-the-client-application"></a><span data-ttu-id="a8458-235">Vytvoření klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="a8458-235">Create the client application</span></span>  
  
1. <span data-ttu-id="a8458-236">Přidejte do řešení `Client` nový projekt konzolové aplikace svolaný do řešení.</span><span class="sxs-lookup"><span data-stu-id="a8458-236">Add a new Console Application project called `Client` to the solution.</span></span> <span data-ttu-id="a8458-237">Přidejte odkaz na soubor System.Activities.dll.</span><span class="sxs-lookup"><span data-stu-id="a8458-237">Add a reference to System.Activities.dll.</span></span>  
  
2. <span data-ttu-id="a8458-238">Otevřete soubor program.cs a přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="a8458-238">Open the program.cs file and add the following code.</span></span>  
  
    ```csharp
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
  
## <a name="see-also"></a><span data-ttu-id="a8458-239">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8458-239">See also</span></span>

- [<span data-ttu-id="a8458-240">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="a8458-240">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="a8458-241">Transakce ve Windows Communication Foundation – přehled</span><span class="sxs-lookup"><span data-stu-id="a8458-241">Windows Communication Foundation Transactions Overview</span></span>](../../../../docs/framework/wcf/feature-details/transactions-overview.md)
