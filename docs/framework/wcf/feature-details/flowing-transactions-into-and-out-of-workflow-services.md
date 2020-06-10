---
title: Tok transakcí do služeb pracovních postupů a mimo ně
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: 17c05139b5977c47e20e888e436a311ba145018a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597459"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a><span data-ttu-id="26d11-102">Tok transakcí do služeb pracovních postupů a mimo ně</span><span class="sxs-lookup"><span data-stu-id="26d11-102">Flowing Transactions into and out of Workflow Services</span></span>
<span data-ttu-id="26d11-103">Služby pracovních postupů a klienti se můžou zúčastnit transakcí.</span><span class="sxs-lookup"><span data-stu-id="26d11-103">Workflow services and clients can participate in transactions.</span></span>  <span data-ttu-id="26d11-104">Aby se operace služby stala součástí okolí transakce, umístěte <xref:System.ServiceModel.Activities.Receive> aktivitu do <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="26d11-104">For a service operation to become part of an ambient transaction, place a <xref:System.ServiceModel.Activities.Receive> activity within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="26d11-105">Všechna volání prováděná <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> aktivitou nebo v rámci <xref:System.ServiceModel.Activities.TransactedReceiveScope> budou také vytvořena v rámci okolí transakce.</span><span class="sxs-lookup"><span data-stu-id="26d11-105">Any calls made by a <xref:System.ServiceModel.Activities.Send> or a <xref:System.ServiceModel.Activities.SendReply> activity within the <xref:System.ServiceModel.Activities.TransactedReceiveScope> will also be made within the ambient transaction.</span></span> <span data-ttu-id="26d11-106">Klientská aplikace pracovního postupu může vytvořit okolí transakce pomocí <xref:System.Activities.Statements.TransactionScope> aktivity služby a volat operace služeb pomocí ambientní transakce.</span><span class="sxs-lookup"><span data-stu-id="26d11-106">A workflow client application can create an ambient transaction by using the <xref:System.Activities.Statements.TransactionScope> activity and call service operations using the ambient transaction.</span></span> <span data-ttu-id="26d11-107">Toto téma vás provede vytvořením služby pracovního postupu a klienta pracovního postupu, který se účastní transakcí.</span><span class="sxs-lookup"><span data-stu-id="26d11-107">This topic walks you through creating a workflow service and workflow client that participate in transactions.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="26d11-108">Pokud je instance služby pracovního postupu načtená v rámci transakce a pracovní postup obsahuje <xref:System.Activities.Statements.Persist> aktivitu, instance pracovního postupu se zablokuje, dokud nevyprší časový limit transakce.</span><span class="sxs-lookup"><span data-stu-id="26d11-108">If a workflow service instance is loaded within a transaction and the workflow contains a <xref:System.Activities.Statements.Persist> activity, the workflow instance will block until the transaction times out.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="26d11-109">Pokaždé, když použijete pracovní <xref:System.ServiceModel.Activities.TransactedReceiveScope> postup, se doporučuje umístit všechny přijaté aktivity do pracovního postupu v rámci <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivit.</span><span class="sxs-lookup"><span data-stu-id="26d11-109">Whenever you use a <xref:System.ServiceModel.Activities.TransactedReceiveScope> it is recommended to place all Receives in the workflow within <xref:System.ServiceModel.Activities.TransactedReceiveScope> activities.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="26d11-110">Při použití <xref:System.ServiceModel.Activities.TransactedReceiveScope> a doručení zpráv v nesprávném pořadí bude pracovní postup při pokusu o doručení první zprávy mimo pořadí přerušen.</span><span class="sxs-lookup"><span data-stu-id="26d11-110">When using <xref:System.ServiceModel.Activities.TransactedReceiveScope> and messages arrive in the incorrect order, the workflow will be aborted when trying to deliver the first out of order message.</span></span> <span data-ttu-id="26d11-111">Je nutné zajistit, aby byl pracovní postup vždy v konzistentním bodu zastavení v případě nečinnosti pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="26d11-111">You must make sure your workflow is always at a consistent stopping point when the workflow idles.</span></span> <span data-ttu-id="26d11-112">To vám umožní restartovat pracovní postup z předchozího bodu trvalosti, aby se pracovní postup přerušil.</span><span class="sxs-lookup"><span data-stu-id="26d11-112">This will allow you to restart the workflow from a previous persistence point should the workflow be aborted.</span></span>  
  
### <a name="create-a-shared-library"></a><span data-ttu-id="26d11-113">Vytvoření sdílené knihovny</span><span class="sxs-lookup"><span data-stu-id="26d11-113">Create a shared library</span></span>  
  
1. <span data-ttu-id="26d11-114">Vytvořte nové prázdné řešení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="26d11-114">Create a new empty Visual Studio Solution.</span></span>  
  
2. <span data-ttu-id="26d11-115">Přidejte nový projekt knihovny tříd s názvem `Common` .</span><span class="sxs-lookup"><span data-stu-id="26d11-115">Add a new class library project called `Common`.</span></span> <span data-ttu-id="26d11-116">Přidejte odkazy na následující sestavení:</span><span class="sxs-lookup"><span data-stu-id="26d11-116">Add references to the following assemblies:</span></span>  
  
    - <span data-ttu-id="26d11-117">System. Activities. dll</span><span class="sxs-lookup"><span data-stu-id="26d11-117">System.Activities.dll</span></span>  
  
    - <span data-ttu-id="26d11-118">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="26d11-118">System.ServiceModel.dll</span></span>  
  
    - <span data-ttu-id="26d11-119">System. ServiceModel. Activities. dll</span><span class="sxs-lookup"><span data-stu-id="26d11-119">System.ServiceModel.Activities.dll</span></span>  
  
    - <span data-ttu-id="26d11-120">System.Transactions.dll</span><span class="sxs-lookup"><span data-stu-id="26d11-120">System.Transactions.dll</span></span>  
  
3. <span data-ttu-id="26d11-121">Přidejte do projektu novou třídu s názvem `PrintTransactionInfo` `Common` .</span><span class="sxs-lookup"><span data-stu-id="26d11-121">Add a new class called `PrintTransactionInfo` to the `Common` project.</span></span> <span data-ttu-id="26d11-122">Tato třída je odvozena z <xref:System.Activities.NativeActivity> a přetížení <xref:System.Activities.NativeActivity.Execute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="26d11-122">This class is derived from <xref:System.Activities.NativeActivity> and overloads the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
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
  
     <span data-ttu-id="26d11-123">Toto je nativní aktivita, která zobrazuje informace o okolí transakce a používá se v pracovních postupech služby i klienta, které jsou používány v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="26d11-123">This is a native activity that displays information about the ambient transaction and is used in both the service and client workflows used in this topic.</span></span> <span data-ttu-id="26d11-124">Sestavte řešení, aby tato aktivita byla k dispozici v části **společná** v **sadě nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="26d11-124">Build the solution to make this activity available in the **Common** section of the **Toolbox**.</span></span>  
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="26d11-125">Implementace služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="26d11-125">Implement the workflow service</span></span>  
  
1. <span data-ttu-id="26d11-126">Přidejte do projektu novou službu pracovního postupu WCF volanou `WorkflowService` `Common` .</span><span class="sxs-lookup"><span data-stu-id="26d11-126">Add a new WCF Workflow Service, called `WorkflowService` to the `Common` project.</span></span> <span data-ttu-id="26d11-127">Provedete to tak, že kliknete pravým tlačítkem na `Common` projekt, vyberte **Přidat**, **Nová položka...**, vyberte **pracovní postup** v části **Nainstalované šablony** a vyberte **Služba pracovního postupu WCF**.</span><span class="sxs-lookup"><span data-stu-id="26d11-127">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **WCF Workflow Service**.</span></span>  
  
     ![Přidání služby pracovního postupu](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. <span data-ttu-id="26d11-129">Odstraňte výchozí `ReceiveRequest` aktivity a `SendResponse` .</span><span class="sxs-lookup"><span data-stu-id="26d11-129">Delete the default `ReceiveRequest` and `SendResponse` activities.</span></span>  
  
3. <span data-ttu-id="26d11-130">Přetáhněte <xref:System.Activities.Statements.WriteLine> aktivitu do `Sequential Service` aktivity.</span><span class="sxs-lookup"><span data-stu-id="26d11-130">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity into the `Sequential Service` activity.</span></span> <span data-ttu-id="26d11-131">Nastavte vlastnost text na `"Workflow Service starting ..."` , jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="26d11-131">Set the text property to `"Workflow Service starting ..."` as shown in the following example.</span></span>  
  
     <span data-ttu-id="26d11-132">! [Přidání aktivity WriteLine do aktivity sekvenční služby (./Media/Flowing-Transactions-into-and-out-of-Workflow-Services/Add-WriteLine-Sequential-Service.jpg)</span><span class="sxs-lookup"><span data-stu-id="26d11-132">![Adding a WriteLine activity to the Sequential Service activity(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg)</span></span>  
  
4. <span data-ttu-id="26d11-133">Přetáhněte <xref:System.ServiceModel.Activities.TransactedReceiveScope> za <xref:System.Activities.Statements.WriteLine> aktivitu.</span><span class="sxs-lookup"><span data-stu-id="26d11-133">Drag and drop a <xref:System.ServiceModel.Activities.TransactedReceiveScope> after the <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="26d11-134"><xref:System.ServiceModel.Activities.TransactedReceiveScope>Aktivitu najdete v části pro **zasílání zpráv** v **sadě nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="26d11-134">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity can be found in the **Messaging** section of the **Toolbox**.</span></span> <span data-ttu-id="26d11-135"><xref:System.ServiceModel.Activities.TransactedReceiveScope>Aktivita se skládá ze dvou částí **žádosti** a **textu**.</span><span class="sxs-lookup"><span data-stu-id="26d11-135">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity is composed of two sections **Request** and **Body**.</span></span> <span data-ttu-id="26d11-136">Část **žádosti** obsahuje <xref:System.ServiceModel.Activities.Receive> aktivitu.</span><span class="sxs-lookup"><span data-stu-id="26d11-136">The **Request** section contains the <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="26d11-137">Oddíl **text** obsahuje aktivity, které se mají provést v rámci transakce po přijetí zprávy.</span><span class="sxs-lookup"><span data-stu-id="26d11-137">The **Body** section contains the activities to execute within a transaction after a message has been received.</span></span>  
  
     ![Přidání aktivity TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. <span data-ttu-id="26d11-139">Vyberte <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivitu a klikněte na tlačítko **proměnné** .</span><span class="sxs-lookup"><span data-stu-id="26d11-139">Select the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity and click the **Variables** button.</span></span> <span data-ttu-id="26d11-140">Přidejte následující proměnné.</span><span class="sxs-lookup"><span data-stu-id="26d11-140">Add the following variables.</span></span>  
  
     ![Přidávání proměnných do TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > <span data-ttu-id="26d11-142">Můžete odstranit datovou proměnnou, která je ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="26d11-142">You can delete the data variable that is there by default.</span></span> <span data-ttu-id="26d11-143">Můžete také použít existující proměnnou popisovače.</span><span class="sxs-lookup"><span data-stu-id="26d11-143">You can also use the existing handle variable.</span></span>  
  
6. <span data-ttu-id="26d11-144">Přetáhněte <xref:System.ServiceModel.Activities.Receive> aktivitu v části **žádosti** <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="26d11-144">Drag and drop a <xref:System.ServiceModel.Activities.Receive> activity within the **Request** section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="26d11-145">Nastavte následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="26d11-145">Set the following properties:</span></span>  
  
    |<span data-ttu-id="26d11-146">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="26d11-146">Property</span></span>|<span data-ttu-id="26d11-147">Hodnota</span><span class="sxs-lookup"><span data-stu-id="26d11-147">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="26d11-148">CanCreateInstance</span><span class="sxs-lookup"><span data-stu-id="26d11-148">CanCreateInstance</span></span>|<span data-ttu-id="26d11-149">Pravda (zaškrtněte políčko)</span><span class="sxs-lookup"><span data-stu-id="26d11-149">True (check the checkbox)</span></span>|  
    |<span data-ttu-id="26d11-150">OperationName</span><span class="sxs-lookup"><span data-stu-id="26d11-150">OperationName</span></span>|<span data-ttu-id="26d11-151">StartSample</span><span class="sxs-lookup"><span data-stu-id="26d11-151">StartSample</span></span>|  
    |<span data-ttu-id="26d11-152">Stejnými ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="26d11-152">ServiceContractName</span></span>|<span data-ttu-id="26d11-153">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="26d11-153">ITransactionSample</span></span>|  
  
     <span data-ttu-id="26d11-154">Pracovní postup by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="26d11-154">The workflow should look like this:</span></span>  
  
     ![Přidání aktivity Receive](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. <span data-ttu-id="26d11-156">V aktivitě klikněte na odkaz **definovat...** <xref:System.ServiceModel.Activities.Receive> a proveďte následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="26d11-156">Click the **Define...** link in the <xref:System.ServiceModel.Activities.Receive> activity and make the following settings:</span></span>  
  
     ![Nastavení nastavení zpráv pro aktivitu Receive](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. <span data-ttu-id="26d11-158">Přetáhněte <xref:System.Activities.Statements.Sequence> aktivitu do části text v <xref:System.ServiceModel.Activities.TransactedReceiveScope> .</span><span class="sxs-lookup"><span data-stu-id="26d11-158">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the Body section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="26d11-159">V rámci <xref:System.Activities.Statements.Sequence> aktivity přetahujte a přetáhněte dvě <xref:System.Activities.Statements.WriteLine> aktivity a nastavte <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnosti, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="26d11-159">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop two <xref:System.Activities.Statements.WriteLine> activities and set the <xref:System.Activities.Statements.WriteLine.Text%2A> properties as shown in the following table.</span></span>  
  
    |<span data-ttu-id="26d11-160">Aktivita</span><span class="sxs-lookup"><span data-stu-id="26d11-160">Activity</span></span>|<span data-ttu-id="26d11-161">Hodnota</span><span class="sxs-lookup"><span data-stu-id="26d11-161">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="26d11-162">1. WriteLine</span><span class="sxs-lookup"><span data-stu-id="26d11-162">1st WriteLine</span></span>|<span data-ttu-id="26d11-163">"Služba: přijímání dokončeno"</span><span class="sxs-lookup"><span data-stu-id="26d11-163">"Service: Receive Completed"</span></span>|  
    |<span data-ttu-id="26d11-164">druhý WriteLine</span><span class="sxs-lookup"><span data-stu-id="26d11-164">2nd WriteLine</span></span>|<span data-ttu-id="26d11-165">"Service: Received =" + requestMessage</span><span class="sxs-lookup"><span data-stu-id="26d11-165">"Service: Received = " + requestMessage</span></span>|  
  
     <span data-ttu-id="26d11-166">Pracovní postup by teď měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="26d11-166">The workflow should now look like this:</span></span>  
  
     ![Sekvence po přidání aktivit WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. <span data-ttu-id="26d11-168">Přetáhněte `PrintTransactionInfo` aktivitu za druhou <xref:System.Activities.Statements.WriteLine> aktivitu v **těle** <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="26d11-168">Drag and drop the `PrintTransactionInfo` activity after the second <xref:System.Activities.Statements.WriteLine> activity in the **Body** in the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span>  
  
     ![Sekvence po přidání PrintTransactionInfo](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. <span data-ttu-id="26d11-170">Přetáhněte <xref:System.Activities.Statements.Assign> aktivitu za `PrintTransactionInfo` aktivitu a nastavte její vlastnosti podle následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="26d11-170">Drag and drop an <xref:System.Activities.Statements.Assign> activity after the `PrintTransactionInfo` activity and set its properties according to the following table.</span></span>  
  
    |<span data-ttu-id="26d11-171">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="26d11-171">Property</span></span>|<span data-ttu-id="26d11-172">Hodnota</span><span class="sxs-lookup"><span data-stu-id="26d11-172">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="26d11-173">Akce</span><span class="sxs-lookup"><span data-stu-id="26d11-173">To</span></span>|<span data-ttu-id="26d11-174">replyMessage</span><span class="sxs-lookup"><span data-stu-id="26d11-174">replyMessage</span></span>|  
    |<span data-ttu-id="26d11-175">Hodnota</span><span class="sxs-lookup"><span data-stu-id="26d11-175">Value</span></span>|<span data-ttu-id="26d11-176">"Služba: odesílá se odpověď."</span><span class="sxs-lookup"><span data-stu-id="26d11-176">"Service: Sending reply."</span></span>|  
  
11. <span data-ttu-id="26d11-177">Přetáhněte <xref:System.Activities.Statements.WriteLine> aktivitu za <xref:System.Activities.Statements.Assign> aktivitou a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na "služba: zahájit odpověď".</span><span class="sxs-lookup"><span data-stu-id="26d11-177">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.Activities.Statements.Assign> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Begin reply."</span></span>  
  
     <span data-ttu-id="26d11-178">Pracovní postup by teď měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="26d11-178">The workflow should now look like this:</span></span>  
  
     ![Po přidání přiřadit a odwriteline](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. <span data-ttu-id="26d11-180">Klikněte pravým tlačítkem na <xref:System.ServiceModel.Activities.Receive> aktivitu a vyberte **vytvořit aktivitu SendReply** a vložte ji za poslední <xref:System.Activities.Statements.WriteLine> aktivitu.</span><span class="sxs-lookup"><span data-stu-id="26d11-180">Right click the <xref:System.ServiceModel.Activities.Receive> activity and select **Create SendReply** and paste it after the last <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="26d11-181">V aktivitě klikněte na odkaz **definovat...** `SendReplyToReceive` a proveďte následující nastavení.</span><span class="sxs-lookup"><span data-stu-id="26d11-181">Click the **Define...** link in the `SendReplyToReceive` activity and make the following settings.</span></span>  
  
     ![Nastavení zprávy s odpovědí](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. <span data-ttu-id="26d11-183">Přetáhněte <xref:System.Activities.Statements.WriteLine> aktivitu za `SendReplyToReceive` aktivitou a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na "služba: odpověď poslána".</span><span class="sxs-lookup"><span data-stu-id="26d11-183">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `SendReplyToReceive` activity and set it’s <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Reply sent."</span></span>  
  
14. <span data-ttu-id="26d11-184">Přetáhněte <xref:System.Activities.Statements.WriteLine> aktivitu do dolní části pracovního postupu a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na "služba: pracovní postup končí, stiskněte klávesu ENTER pro ukončení."</span><span class="sxs-lookup"><span data-stu-id="26d11-184">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the bottom of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Workflow ends, press ENTER to exit."</span></span>  
  
     <span data-ttu-id="26d11-185">Dokončený pracovní postup služby by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="26d11-185">The completed service workflow should look like this:</span></span>  
  
     ![Dokončení pracovního postupu služby](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a><span data-ttu-id="26d11-187">Implementace klienta pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="26d11-187">Implement the workflow client</span></span>  
  
1. <span data-ttu-id="26d11-188">Přidejte novou aplikaci pracovního postupu WCF, která se volá `WorkflowClient` do `Common` projektu.</span><span class="sxs-lookup"><span data-stu-id="26d11-188">Add a new WCF Workflow application, called `WorkflowClient` to the `Common` project.</span></span> <span data-ttu-id="26d11-189">Chcete-li to provést, klikněte pravým tlačítkem myši na `Common` projekt, vyberte možnost **Přidat**, **Nová položka...**, vyberte možnost **pracovní postup** v části **Nainstalované šablony** a vyberte **aktivita**.</span><span class="sxs-lookup"><span data-stu-id="26d11-189">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **Activity**.</span></span>  
  
     ![Přidat projekt aktivity](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. <span data-ttu-id="26d11-191">Přetáhněte <xref:System.Activities.Statements.Sequence> aktivitu na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="26d11-191">Drag and drop a <xref:System.Activities.Statements.Sequence> activity onto the design surface.</span></span>  
  
3. <span data-ttu-id="26d11-192">V rámci <xref:System.Activities.Statements.Sequence> aktivity přetáhněte <xref:System.Activities.Statements.WriteLine> aktivitu a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na `"Client: Workflow starting"` .</span><span class="sxs-lookup"><span data-stu-id="26d11-192">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop a <xref:System.Activities.Statements.WriteLine> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to `"Client: Workflow starting"`.</span></span> <span data-ttu-id="26d11-193">Pracovní postup by teď měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="26d11-193">The workflow should now look like this:</span></span>  
  
     ![Přidání aktivity WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. <span data-ttu-id="26d11-195">Přetáhněte <xref:System.Activities.Statements.TransactionScope> aktivitu za <xref:System.Activities.Statements.WriteLine> aktivitou.</span><span class="sxs-lookup"><span data-stu-id="26d11-195">Drag and drop a <xref:System.Activities.Statements.TransactionScope> activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  <span data-ttu-id="26d11-196">Vyberte <xref:System.Activities.Statements.TransactionScope> aktivitu, klikněte na tlačítko proměnné a přidejte následující proměnné.</span><span class="sxs-lookup"><span data-stu-id="26d11-196">Select the <xref:System.Activities.Statements.TransactionScope> activity, click the Variables button and add the following variables.</span></span>  
  
     ![Přidat proměnné do objektu TransactionScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. <span data-ttu-id="26d11-198">Přetáhněte <xref:System.Activities.Statements.Sequence> aktivitu do těla <xref:System.Activities.Statements.TransactionScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="26d11-198">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the body of the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
6. <span data-ttu-id="26d11-199">Přetáhněte `PrintTransactionInfo` aktivitu v rámci<xref:System.Activities.Statements.Sequence></span><span class="sxs-lookup"><span data-stu-id="26d11-199">Drag and drop a `PrintTransactionInfo` activity within the <xref:System.Activities.Statements.Sequence></span></span>  
  
7. <span data-ttu-id="26d11-200">Přetáhněte <xref:System.Activities.Statements.WriteLine> aktivitu za `PrintTransactionInfo` aktivitu a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na "klient: začátek odeslání".</span><span class="sxs-lookup"><span data-stu-id="26d11-200">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `PrintTransactionInfo` activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Beginning Send".</span></span> <span data-ttu-id="26d11-201">Pracovní postup by teď měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="26d11-201">The workflow should now look like this:</span></span>  
  
     ![Přidávání klienta: zahájení aktivit odeslání](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. <span data-ttu-id="26d11-203">Přetáhněte <xref:System.ServiceModel.Activities.Send> aktivitu za <xref:System.Activities.Statements.Assign> aktivitu a nastavte následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="26d11-203">Drag and drop a <xref:System.ServiceModel.Activities.Send> activity after the <xref:System.Activities.Statements.Assign> activity and set the following properties:</span></span>  
  
    |<span data-ttu-id="26d11-204">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="26d11-204">Property</span></span>|<span data-ttu-id="26d11-205">Hodnota</span><span class="sxs-lookup"><span data-stu-id="26d11-205">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="26d11-206">EndpointConfigurationName</span><span class="sxs-lookup"><span data-stu-id="26d11-206">EndpointConfigurationName</span></span>|<span data-ttu-id="26d11-207">workflowServiceEndpoint</span><span class="sxs-lookup"><span data-stu-id="26d11-207">workflowServiceEndpoint</span></span>|  
    |<span data-ttu-id="26d11-208">OperationName</span><span class="sxs-lookup"><span data-stu-id="26d11-208">OperationName</span></span>|<span data-ttu-id="26d11-209">StartSample</span><span class="sxs-lookup"><span data-stu-id="26d11-209">StartSample</span></span>|  
    |<span data-ttu-id="26d11-210">Stejnými ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="26d11-210">ServiceContractName</span></span>|<span data-ttu-id="26d11-211">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="26d11-211">ITransactionSample</span></span>|  
  
     <span data-ttu-id="26d11-212">Pracovní postup by teď měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="26d11-212">The workflow should now look like this:</span></span>  
  
     ![Nastavení vlastností aktivity odeslání](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. <span data-ttu-id="26d11-214">Klikněte na odkaz **definovat...** a proveďte následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="26d11-214">Click the **Define...** link and make the following settings:</span></span>  
  
     ![Odeslat nastavení zprávy o aktivitě](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. <span data-ttu-id="26d11-216">Klikněte pravým tlačítkem na <xref:System.ServiceModel.Activities.Send> aktivitu a vyberte **vytvořit ReceiveReply**.</span><span class="sxs-lookup"><span data-stu-id="26d11-216">Right click the <xref:System.ServiceModel.Activities.Send> activity and select **Create ReceiveReply**.</span></span> <span data-ttu-id="26d11-217"><xref:System.ServiceModel.Activities.ReceiveReply>Aktivita se automaticky umístí za <xref:System.ServiceModel.Activities.Send> aktivitu.</span><span class="sxs-lookup"><span data-stu-id="26d11-217">The <xref:System.ServiceModel.Activities.ReceiveReply> activity will be automatically placed after the <xref:System.ServiceModel.Activities.Send> activity.</span></span>  
  
11. <span data-ttu-id="26d11-218">Klikněte na definovat... Propojte aktivitu ReceiveReplyForSend a proveďte následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="26d11-218">Click the Define... link on the ReceiveReplyForSend activity and make the following settings:</span></span>  
  
     ![Nastavení zprávy ReceiveForSend](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. <span data-ttu-id="26d11-220">Přetáhněte <xref:System.Activities.Statements.WriteLine> aktivitu mezi <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> aktivitami a a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na "klient: Odeslat dokončeno".</span><span class="sxs-lookup"><span data-stu-id="26d11-220">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity between the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> activities and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Send complete."</span></span>  
  
13. <span data-ttu-id="26d11-221">Přetáhněte <xref:System.Activities.Statements.WriteLine> aktivitu za <xref:System.ServiceModel.Activities.ReceiveReply> aktivitu a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na stranu klienta: odpověď přijata = "+ replyMessage</span><span class="sxs-lookup"><span data-stu-id="26d11-221">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.ServiceModel.Activities.ReceiveReply> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client side: Reply received = " + replyMessage</span></span>  
  
14. <span data-ttu-id="26d11-222">Přetáhněte `PrintTransactionInfo` aktivitu za <xref:System.Activities.Statements.WriteLine> aktivitou.</span><span class="sxs-lookup"><span data-stu-id="26d11-222">Drag and drop a `PrintTransactionInfo` activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
15. <span data-ttu-id="26d11-223">Přetáhněte <xref:System.Activities.Statements.WriteLine> aktivitu na konci pracovního postupu a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na "pracovní postup klienta končí."</span><span class="sxs-lookup"><span data-stu-id="26d11-223">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the end of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client workflow ends."</span></span> <span data-ttu-id="26d11-224">Dokončený pracovní postup klienta by měl vypadat jako v následujícím diagramu.</span><span class="sxs-lookup"><span data-stu-id="26d11-224">The completed client workflow should look like the following diagram.</span></span>  
  
     ![Dokončený pracovní postup klienta](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. <span data-ttu-id="26d11-226">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="26d11-226">Build the solution.</span></span>  
  
### <a name="create-the-service-application"></a><span data-ttu-id="26d11-227">Vytvoření aplikace služby</span><span class="sxs-lookup"><span data-stu-id="26d11-227">Create the Service application</span></span>  
  
1. <span data-ttu-id="26d11-228">Přidejte do řešení nový projekt konzolové aplikace s názvem `Service` .</span><span class="sxs-lookup"><span data-stu-id="26d11-228">Add a new Console Application project called `Service` to the solution.</span></span> <span data-ttu-id="26d11-229">Přidejte odkazy na následující sestavení:</span><span class="sxs-lookup"><span data-stu-id="26d11-229">Add references to the following assemblies:</span></span>  
  
    1. <span data-ttu-id="26d11-230">System. Activities. dll</span><span class="sxs-lookup"><span data-stu-id="26d11-230">System.Activities.dll</span></span>  
  
    2. <span data-ttu-id="26d11-231">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="26d11-231">System.ServiceModel.dll</span></span>  
  
    3. <span data-ttu-id="26d11-232">System. ServiceModel. Activities. dll</span><span class="sxs-lookup"><span data-stu-id="26d11-232">System.ServiceModel.Activities.dll</span></span>  
  
2. <span data-ttu-id="26d11-233">Otevřete vygenerovaný soubor Program.cs a následující kód:</span><span class="sxs-lookup"><span data-stu-id="26d11-233">Open the generated Program.cs file and the following code:</span></span>  
  
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
  
3. <span data-ttu-id="26d11-234">Do projektu přidejte následující soubor App. config.</span><span class="sxs-lookup"><span data-stu-id="26d11-234">Add the following app.config file to the project.</span></span>  
  
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
  
### <a name="create-the-client-application"></a><span data-ttu-id="26d11-235">Vytvoření klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="26d11-235">Create the client application</span></span>  
  
1. <span data-ttu-id="26d11-236">Přidejte do řešení nový projekt konzolové aplikace s názvem `Client` .</span><span class="sxs-lookup"><span data-stu-id="26d11-236">Add a new Console Application project called `Client` to the solution.</span></span> <span data-ttu-id="26d11-237">Přidejte odkaz na System. Activities. dll.</span><span class="sxs-lookup"><span data-stu-id="26d11-237">Add a reference to System.Activities.dll.</span></span>  
  
2. <span data-ttu-id="26d11-238">Otevřete soubor program.cs a přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="26d11-238">Open the program.cs file and add the following code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="26d11-239">Viz také</span><span class="sxs-lookup"><span data-stu-id="26d11-239">See also</span></span>

- [<span data-ttu-id="26d11-240">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="26d11-240">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="26d11-241">Transakce ve Windows Communication Foundation – přehled</span><span class="sxs-lookup"><span data-stu-id="26d11-241">Windows Communication Foundation Transactions Overview</span></span>](transactions-overview.md)
