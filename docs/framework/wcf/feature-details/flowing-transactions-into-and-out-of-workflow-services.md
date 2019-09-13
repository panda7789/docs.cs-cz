---
title: Tok transakcí do služeb pracovních postupů a mimo ně
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: db1a1ef6bcf3f048584b39450c90fac3ff35646b
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70893381"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a><span data-ttu-id="7bd5a-102">Tok transakcí do služeb pracovních postupů a mimo ně</span><span class="sxs-lookup"><span data-stu-id="7bd5a-102">Flowing Transactions into and out of Workflow Services</span></span>
<span data-ttu-id="7bd5a-103">Služby pracovních postupů a klienti se můžou zúčastnit transakcí.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-103">Workflow services and clients can participate in transactions.</span></span>  <span data-ttu-id="7bd5a-104">Aby se operace služby stala součástí okolí transakce, umístěte <xref:System.ServiceModel.Activities.Receive> aktivitu <xref:System.ServiceModel.Activities.TransactedReceiveScope> do aktivity.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-104">For a service operation to become part of an ambient transaction, place a <xref:System.ServiceModel.Activities.Receive> activity within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="7bd5a-105">Všechna volání prováděná <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> aktivitou nebo v rámci <xref:System.ServiceModel.Activities.TransactedReceiveScope> budou také vytvořena v rámci okolí transakce.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-105">Any calls made by a <xref:System.ServiceModel.Activities.Send> or a <xref:System.ServiceModel.Activities.SendReply> activity within the <xref:System.ServiceModel.Activities.TransactedReceiveScope> will also be made within the ambient transaction.</span></span> <span data-ttu-id="7bd5a-106">Klientská aplikace pracovního postupu může vytvořit okolí transakce <xref:System.Activities.Statements.TransactionScope> pomocí aktivity služby a volat operace služeb pomocí ambientní transakce.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-106">A workflow client application can create an ambient transaction by using the <xref:System.Activities.Statements.TransactionScope> activity and call service operations using the ambient transaction.</span></span> <span data-ttu-id="7bd5a-107">Toto téma vás provede vytvořením služby pracovního postupu a klienta pracovního postupu, který se účastní transakcí.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-107">This topic walks you through creating a workflow service and workflow client that participate in transactions.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="7bd5a-108">Pokud je instance služby pracovního postupu načtená v rámci transakce a pracovní postup obsahuje <xref:System.Activities.Statements.Persist> aktivitu, instance pracovního postupu se zablokuje, dokud nevyprší časový limit transakce.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-108">If a workflow service instance is loaded within a transaction and the workflow contains a <xref:System.Activities.Statements.Persist> activity, the workflow instance will block until the transaction times out.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7bd5a-109">Pokaždé, když <xref:System.ServiceModel.Activities.TransactedReceiveScope> použijete pracovní postup, se doporučuje umístit všechny přijaté aktivity <xref:System.ServiceModel.Activities.TransactedReceiveScope> do pracovního postupu v rámci aktivit.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-109">Whenever you use a <xref:System.ServiceModel.Activities.TransactedReceiveScope> it is recommended to place all Receives in the workflow within <xref:System.ServiceModel.Activities.TransactedReceiveScope> activities.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7bd5a-110">Při použití <xref:System.ServiceModel.Activities.TransactedReceiveScope> a doručení zpráv v nesprávném pořadí bude pracovní postup při pokusu o doručení první zprávy mimo pořadí přerušen.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-110">When using <xref:System.ServiceModel.Activities.TransactedReceiveScope> and messages arrive in the incorrect order, the workflow will be aborted when trying to deliver the first out of order message.</span></span> <span data-ttu-id="7bd5a-111">Je nutné zajistit, aby byl pracovní postup vždy v konzistentním bodu zastavení v případě nečinnosti pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-111">You must make sure your workflow is always at a consistent stopping point when the workflow idles.</span></span> <span data-ttu-id="7bd5a-112">To vám umožní restartovat pracovní postup z předchozího bodu trvalosti, aby se pracovní postup přerušil.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-112">This will allow you to restart the workflow from a previous persistence point should the workflow be aborted.</span></span>  
  
### <a name="create-a-shared-library"></a><span data-ttu-id="7bd5a-113">Vytvoření sdílené knihovny</span><span class="sxs-lookup"><span data-stu-id="7bd5a-113">Create a shared library</span></span>  
  
1. <span data-ttu-id="7bd5a-114">Vytvořte nové prázdné řešení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-114">Create a new empty Visual Studio Solution.</span></span>  
  
2. <span data-ttu-id="7bd5a-115">Přidejte nový projekt knihovny tříd s názvem `Common`.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-115">Add a new class library project called `Common`.</span></span> <span data-ttu-id="7bd5a-116">Přidejte odkazy na následující sestavení:</span><span class="sxs-lookup"><span data-stu-id="7bd5a-116">Add references to the following assemblies:</span></span>  
  
    - <span data-ttu-id="7bd5a-117">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="7bd5a-117">System.Activities.dll</span></span>  
  
    - <span data-ttu-id="7bd5a-118">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="7bd5a-118">System.ServiceModel.dll</span></span>  
  
    - <span data-ttu-id="7bd5a-119">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="7bd5a-119">System.ServiceModel.Activities.dll</span></span>  
  
    - <span data-ttu-id="7bd5a-120">System.Transactions.dll</span><span class="sxs-lookup"><span data-stu-id="7bd5a-120">System.Transactions.dll</span></span>  
  
3. <span data-ttu-id="7bd5a-121">`PrintTransactionInfo` Přidejte`Common` do projektu novou třídu s názvem.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-121">Add a new class called `PrintTransactionInfo` to the `Common` project.</span></span> <span data-ttu-id="7bd5a-122">Tato třída je odvozena <xref:System.Activities.NativeActivity> z a přetížení <xref:System.Activities.NativeActivity.Execute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-122">This class is derived from <xref:System.Activities.NativeActivity> and overloads the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
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
  
     <span data-ttu-id="7bd5a-123">Toto je nativní aktivita, která zobrazuje informace o okolí transakce a používá se v pracovních postupech služby i klienta, které jsou používány v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-123">This is a native activity that displays information about the ambient transaction and is used in both the service and client workflows used in this topic.</span></span> <span data-ttu-id="7bd5a-124">Sestavte řešení, aby tato aktivita byla k dispozici v části **společná** v **sadě nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-124">Build the solution to make this activity available in the **Common** section of the **Toolbox**.</span></span>  
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="7bd5a-125">Implementace služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="7bd5a-125">Implement the workflow service</span></span>  
  
1. <span data-ttu-id="7bd5a-126">`WorkflowService` Přidejte`Common` do projektu novou službu pracovního postupu WCF volanou.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-126">Add a new WCF Workflow Service, called `WorkflowService` to the `Common` project.</span></span> <span data-ttu-id="7bd5a-127">Provedete to tak, `Common` že kliknete pravým tlačítkem na projekt, vyberte **Přidat**, **Nová položka...** , vyberte **pracovní postup** v části **Nainstalované šablony** a vyberte **Služba pracovního postupu WCF**.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-127">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **WCF Workflow Service**.</span></span>  
  
     ![Přidání služby pracovního postupu](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. <span data-ttu-id="7bd5a-129">Odstraňte výchozí `ReceiveRequest` aktivity a `SendResponse` .</span><span class="sxs-lookup"><span data-stu-id="7bd5a-129">Delete the default `ReceiveRequest` and `SendResponse` activities.</span></span>  
  
3. <span data-ttu-id="7bd5a-130"><xref:System.Activities.Statements.WriteLine> Přetáhněte aktivitu`Sequential Service` do aktivity.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-130">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity into the `Sequential Service` activity.</span></span> <span data-ttu-id="7bd5a-131">Nastavte vlastnost text na `"Workflow Service starting ..."` , jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-131">Set the text property to `"Workflow Service starting ..."` as shown in the following example.</span></span>  
  
     <span data-ttu-id="7bd5a-132">! [Přidání aktivity WriteLine do aktivity sekvenční služby (./Media/Flowing-Transactions-into-and-out-of-Workflow-Services/Add-WriteLine-Sequential-Service.jpg)</span><span class="sxs-lookup"><span data-stu-id="7bd5a-132">![Adding a WriteLine activity to the Sequential Service activity(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg)</span></span>  
  
4. <span data-ttu-id="7bd5a-133"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Přetáhněte<xref:System.Activities.Statements.WriteLine> za aktivitu.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-133">Drag and drop a <xref:System.ServiceModel.Activities.TransactedReceiveScope> after the <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="7bd5a-134">Aktivitu najdete v části pro **zasílání zpráv** v **sadě nástrojů.** <xref:System.ServiceModel.Activities.TransactedReceiveScope></span><span class="sxs-lookup"><span data-stu-id="7bd5a-134">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity can be found in the **Messaging** section of the **Toolbox**.</span></span> <span data-ttu-id="7bd5a-135">Aktivita se skládá ze dvou částí **žádosti** a **textu.** <xref:System.ServiceModel.Activities.TransactedReceiveScope></span><span class="sxs-lookup"><span data-stu-id="7bd5a-135">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity is composed of two sections **Request** and **Body**.</span></span> <span data-ttu-id="7bd5a-136">Část **žádosti** obsahuje <xref:System.ServiceModel.Activities.Receive> aktivitu.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-136">The **Request** section contains the <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="7bd5a-137">Oddíl **text** obsahuje aktivity, které se mají provést v rámci transakce po přijetí zprávy.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-137">The **Body** section contains the activities to execute within a transaction after a message has been received.</span></span>  
  
     ![Přidání aktivity TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. <span data-ttu-id="7bd5a-139">Vyberte aktivitu a klikněte na tlačítko **proměnné.** <xref:System.ServiceModel.Activities.TransactedReceiveScope></span><span class="sxs-lookup"><span data-stu-id="7bd5a-139">Select the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity and click the **Variables** button.</span></span> <span data-ttu-id="7bd5a-140">Přidejte následující proměnné.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-140">Add the following variables.</span></span>  
  
     ![Přidávání proměnných do TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > <span data-ttu-id="7bd5a-142">Můžete odstranit datovou proměnnou, která je ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-142">You can delete the data variable that is there by default.</span></span> <span data-ttu-id="7bd5a-143">Můžete také použít existující proměnnou popisovače.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-143">You can also use the existing handle variable.</span></span>  
  
6. <span data-ttu-id="7bd5a-144">Přetáhněte aktivitu v části <xref:System.ServiceModel.Activities.TransactedReceiveScope> žádosti aktivity. <xref:System.ServiceModel.Activities.Receive></span><span class="sxs-lookup"><span data-stu-id="7bd5a-144">Drag and drop a <xref:System.ServiceModel.Activities.Receive> activity within the **Request** section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="7bd5a-145">Nastavte následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="7bd5a-145">Set the following properties:</span></span>  
  
    |<span data-ttu-id="7bd5a-146">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="7bd5a-146">Property</span></span>|<span data-ttu-id="7bd5a-147">Value</span><span class="sxs-lookup"><span data-stu-id="7bd5a-147">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="7bd5a-148">CanCreateInstance</span><span class="sxs-lookup"><span data-stu-id="7bd5a-148">CanCreateInstance</span></span>|<span data-ttu-id="7bd5a-149">Pravda (zaškrtněte políčko)</span><span class="sxs-lookup"><span data-stu-id="7bd5a-149">True (check the checkbox)</span></span>|  
    |<span data-ttu-id="7bd5a-150">OperationName</span><span class="sxs-lookup"><span data-stu-id="7bd5a-150">OperationName</span></span>|<span data-ttu-id="7bd5a-151">StartSample</span><span class="sxs-lookup"><span data-stu-id="7bd5a-151">StartSample</span></span>|  
    |<span data-ttu-id="7bd5a-152">Stejnými ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="7bd5a-152">ServiceContractName</span></span>|<span data-ttu-id="7bd5a-153">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="7bd5a-153">ITransactionSample</span></span>|  
  
     <span data-ttu-id="7bd5a-154">Pracovní postup by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="7bd5a-154">The workflow should look like this:</span></span>  
  
     ![Přidání aktivity Receive](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. <span data-ttu-id="7bd5a-156">V<xref:System.ServiceModel.Activities.Receive> aktivitě klikněte na odkaz **definovat...** a proveďte následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="7bd5a-156">Click the **Define...** link in the <xref:System.ServiceModel.Activities.Receive> activity and make the following settings:</span></span>  
  
     ![Nastavení nastavení zpráv pro aktivitu Receive](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. <span data-ttu-id="7bd5a-158">Přetáhněte aktivitu do části text v <xref:System.ServiceModel.Activities.TransactedReceiveScope>. <xref:System.Activities.Statements.Sequence></span><span class="sxs-lookup"><span data-stu-id="7bd5a-158">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the Body section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="7bd5a-159">V rámci <xref:System.Activities.Statements.WriteLine> <xref:System.Activities.Statements.WriteLine.Text%2A> aktivity přetahujte a přetáhněte dvě aktivity a nastavte vlastnosti, jak je znázorněno v následující tabulce. <xref:System.Activities.Statements.Sequence></span><span class="sxs-lookup"><span data-stu-id="7bd5a-159">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop two <xref:System.Activities.Statements.WriteLine> activities and set the <xref:System.Activities.Statements.WriteLine.Text%2A> properties as shown in the following table.</span></span>  
  
    |<span data-ttu-id="7bd5a-160">Aktivita</span><span class="sxs-lookup"><span data-stu-id="7bd5a-160">Activity</span></span>|<span data-ttu-id="7bd5a-161">Value</span><span class="sxs-lookup"><span data-stu-id="7bd5a-161">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="7bd5a-162">1\. WriteLine</span><span class="sxs-lookup"><span data-stu-id="7bd5a-162">1st WriteLine</span></span>|<span data-ttu-id="7bd5a-163">Službám Přijetí dokončeno</span><span class="sxs-lookup"><span data-stu-id="7bd5a-163">"Service: Receive Completed"</span></span>|  
    |<span data-ttu-id="7bd5a-164">druhý WriteLine</span><span class="sxs-lookup"><span data-stu-id="7bd5a-164">2nd WriteLine</span></span>|<span data-ttu-id="7bd5a-165">Službám Přijato = "+ requestMessage</span><span class="sxs-lookup"><span data-stu-id="7bd5a-165">"Service: Received = " + requestMessage</span></span>|  
  
     <span data-ttu-id="7bd5a-166">Pracovní postup by teď měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="7bd5a-166">The workflow should now look like this:</span></span>  
  
     ![Sekvence po přidání aktivit WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. <span data-ttu-id="7bd5a-168">Přetáhněte aktivitu za druhou <xref:System.Activities.Statements.WriteLine> aktivitu <xref:System.ServiceModel.Activities.TransactedReceiveScope> v těle aktivity. `PrintTransactionInfo`</span><span class="sxs-lookup"><span data-stu-id="7bd5a-168">Drag and drop the `PrintTransactionInfo` activity after the second <xref:System.Activities.Statements.WriteLine> activity in the **Body** in the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span>  
  
     ![Sekvence po přidání PrintTransactionInfo](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. <span data-ttu-id="7bd5a-170"><xref:System.Activities.Statements.Assign> Přetáhněte aktivitu`PrintTransactionInfo` za aktivitu a nastavte její vlastnosti podle následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-170">Drag and drop an <xref:System.Activities.Statements.Assign> activity after the `PrintTransactionInfo` activity and set its properties according to the following table.</span></span>  
  
    |<span data-ttu-id="7bd5a-171">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="7bd5a-171">Property</span></span>|<span data-ttu-id="7bd5a-172">Value</span><span class="sxs-lookup"><span data-stu-id="7bd5a-172">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="7bd5a-173">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="7bd5a-173">To</span></span>|<span data-ttu-id="7bd5a-174">replyMessage</span><span class="sxs-lookup"><span data-stu-id="7bd5a-174">replyMessage</span></span>|  
    |<span data-ttu-id="7bd5a-175">Value</span><span class="sxs-lookup"><span data-stu-id="7bd5a-175">Value</span></span>|<span data-ttu-id="7bd5a-176">Službám Posílá se odpověď.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-176">"Service: Sending reply."</span></span>|  
  
11. <span data-ttu-id="7bd5a-177">Přetáhněte aktivitu za aktivitou a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na "Service: <xref:System.Activities.Statements.Assign> <xref:System.Activities.Statements.WriteLine> Zahajte odpověď.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-177">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.Activities.Statements.Assign> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Begin reply."</span></span>  
  
     <span data-ttu-id="7bd5a-178">Pracovní postup by teď měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="7bd5a-178">The workflow should now look like this:</span></span>  
  
     ![Po přidání přiřadit a odwriteline](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. <span data-ttu-id="7bd5a-180">Klikněte pravým <xref:System.ServiceModel.Activities.Receive> tlačítkem na aktivitu a vyberte **vytvořit aktivitu SendReply** a vložte ji <xref:System.Activities.Statements.WriteLine> za poslední aktivitu.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-180">Right click the <xref:System.ServiceModel.Activities.Receive> activity and select **Create SendReply** and paste it after the last <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="7bd5a-181">V`SendReplyToReceive` aktivitě klikněte na odkaz **definovat...** a proveďte následující nastavení.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-181">Click the **Define...** link in the `SendReplyToReceive` activity and make the following settings.</span></span>  
  
     ![Nastavení zprávy s odpovědí](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. <span data-ttu-id="7bd5a-183">Přetáhněte aktivitu za `SendReplyToReceive` aktivitou a nastavte její vlastnostna"služba:<xref:System.Activities.Statements.WriteLine.Text%2A> <xref:System.Activities.Statements.WriteLine> Odeslala se odpověď. "</span><span class="sxs-lookup"><span data-stu-id="7bd5a-183">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `SendReplyToReceive` activity and set it’s <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Reply sent."</span></span>  
  
14. <span data-ttu-id="7bd5a-184">Přetáhněte aktivitu do dolní části pracovního postupu a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na "Service: <xref:System.Activities.Statements.WriteLine> Pracovní postup skončí, stisknutím klávesy ENTER ukončete. "</span><span class="sxs-lookup"><span data-stu-id="7bd5a-184">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the bottom of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Workflow ends, press ENTER to exit."</span></span>  
  
     <span data-ttu-id="7bd5a-185">Dokončený pracovní postup služby by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="7bd5a-185">The completed service workflow should look like this:</span></span>  
  
     ![Dokončení pracovního postupu služby](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a><span data-ttu-id="7bd5a-187">Implementace klienta pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="7bd5a-187">Implement the workflow client</span></span>  
  
1. <span data-ttu-id="7bd5a-188">Přidejte novou aplikaci pracovního postupu WCF, `WorkflowClient` `Common` která se volá do projektu.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-188">Add a new WCF Workflow application, called `WorkflowClient` to the `Common` project.</span></span> <span data-ttu-id="7bd5a-189">Chcete-li to provést, `Common` klikněte pravým tlačítkem myši na projekt, vyberte možnost **Přidat**, **Nová položka...** , vyberte možnost **pracovní postup** v části **Nainstalované šablony** a vyberte **aktivita**.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-189">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **Activity**.</span></span>  
  
     ![Přidat projekt aktivity](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. <span data-ttu-id="7bd5a-191"><xref:System.Activities.Statements.Sequence> Přetáhněte aktivitu na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-191">Drag and drop a <xref:System.Activities.Statements.Sequence> activity onto the design surface.</span></span>  
  
3. <span data-ttu-id="7bd5a-192">V rámci <xref:System.Activities.Statements.WriteLine> <xref:System.Activities.Statements.WriteLine.Text%2A> aktivity přetáhněte aktivitu a nastavte její vlastnost na `"Client: Workflow starting"`. <xref:System.Activities.Statements.Sequence></span><span class="sxs-lookup"><span data-stu-id="7bd5a-192">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop a <xref:System.Activities.Statements.WriteLine> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to `"Client: Workflow starting"`.</span></span> <span data-ttu-id="7bd5a-193">Pracovní postup by teď měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="7bd5a-193">The workflow should now look like this:</span></span>  
  
     ![Přidání aktivity WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. <span data-ttu-id="7bd5a-195"><xref:System.Activities.Statements.TransactionScope> Přetáhněte aktivitu <xref:System.Activities.Statements.WriteLine> za aktivitou.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-195">Drag and drop a <xref:System.Activities.Statements.TransactionScope> activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  <span data-ttu-id="7bd5a-196"><xref:System.Activities.Statements.TransactionScope> Vyberte aktivitu, klikněte na tlačítko proměnné a přidejte následující proměnné.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-196">Select the <xref:System.Activities.Statements.TransactionScope> activity, click the Variables button and add the following variables.</span></span>  
  
     ![Přidat proměnné do objektu TransactionScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. <span data-ttu-id="7bd5a-198">Přetáhněte aktivitu do těla <xref:System.Activities.Statements.TransactionScope>aktivity. <xref:System.Activities.Statements.Sequence></span><span class="sxs-lookup"><span data-stu-id="7bd5a-198">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the body of the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
6. <span data-ttu-id="7bd5a-199">`PrintTransactionInfo` Přetáhněte aktivitu v rámci<xref:System.Activities.Statements.Sequence></span><span class="sxs-lookup"><span data-stu-id="7bd5a-199">Drag and drop a `PrintTransactionInfo` activity within the <xref:System.Activities.Statements.Sequence></span></span>  
  
7. <span data-ttu-id="7bd5a-200">Přetáhněte aktivitu za aktivitou a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na "klient: `PrintTransactionInfo` <xref:System.Activities.Statements.WriteLine> Začíná se odesílat.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-200">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `PrintTransactionInfo` activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Beginning Send".</span></span> <span data-ttu-id="7bd5a-201">Pracovní postup by teď měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="7bd5a-201">The workflow should now look like this:</span></span>  
  
     ![Přidávání klienta: Zahájení aktivit odeslání](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. <span data-ttu-id="7bd5a-203"><xref:System.ServiceModel.Activities.Send> Přetáhněte aktivitu<xref:System.Activities.Statements.Assign> za aktivitu a nastavte následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="7bd5a-203">Drag and drop a <xref:System.ServiceModel.Activities.Send> activity after the <xref:System.Activities.Statements.Assign> activity and set the following properties:</span></span>  
  
    |<span data-ttu-id="7bd5a-204">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="7bd5a-204">Property</span></span>|<span data-ttu-id="7bd5a-205">Value</span><span class="sxs-lookup"><span data-stu-id="7bd5a-205">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="7bd5a-206">EndpointConfigurationName</span><span class="sxs-lookup"><span data-stu-id="7bd5a-206">EndpointConfigurationName</span></span>|<span data-ttu-id="7bd5a-207">workflowServiceEndpoint</span><span class="sxs-lookup"><span data-stu-id="7bd5a-207">workflowServiceEndpoint</span></span>|  
    |<span data-ttu-id="7bd5a-208">OperationName</span><span class="sxs-lookup"><span data-stu-id="7bd5a-208">OperationName</span></span>|<span data-ttu-id="7bd5a-209">StartSample</span><span class="sxs-lookup"><span data-stu-id="7bd5a-209">StartSample</span></span>|  
    |<span data-ttu-id="7bd5a-210">Stejnými ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="7bd5a-210">ServiceContractName</span></span>|<span data-ttu-id="7bd5a-211">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="7bd5a-211">ITransactionSample</span></span>|  
  
     <span data-ttu-id="7bd5a-212">Pracovní postup by teď měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="7bd5a-212">The workflow should now look like this:</span></span>  
  
     ![Nastavení vlastností aktivity odeslání](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. <span data-ttu-id="7bd5a-214">Klikněte na odkaz **definovat...** a proveďte následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="7bd5a-214">Click the **Define...** link and make the following settings:</span></span>  
  
     ![Odeslat nastavení zprávy o aktivitě](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. <span data-ttu-id="7bd5a-216">Klikněte pravým <xref:System.ServiceModel.Activities.Send> tlačítkem na aktivitu a vyberte **vytvořit ReceiveReply**.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-216">Right click the <xref:System.ServiceModel.Activities.Send> activity and select **Create ReceiveReply**.</span></span> <span data-ttu-id="7bd5a-217">Aktivita se automaticky umístí <xref:System.ServiceModel.Activities.Send> za aktivitu. <xref:System.ServiceModel.Activities.ReceiveReply></span><span class="sxs-lookup"><span data-stu-id="7bd5a-217">The <xref:System.ServiceModel.Activities.ReceiveReply> activity will be automatically placed after the <xref:System.ServiceModel.Activities.Send> activity.</span></span>  
  
11. <span data-ttu-id="7bd5a-218">Klikněte na definovat... Propojte aktivitu ReceiveReplyForSend a proveďte následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="7bd5a-218">Click the Define... link on the ReceiveReplyForSend activity and make the following settings:</span></span>  
  
     ![Nastavení zprávy ReceiveForSend](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. <span data-ttu-id="7bd5a-220">Přetáhněte aktivitu mezi aktivitami <xref:System.ServiceModel.Activities.ReceiveReply>aa nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na Client: <xref:System.ServiceModel.Activities.Send> <xref:System.Activities.Statements.WriteLine> Odeslat dokončeno. "</span><span class="sxs-lookup"><span data-stu-id="7bd5a-220">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity between the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> activities and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Send complete."</span></span>  
  
13. <span data-ttu-id="7bd5a-221">Přetáhněte aktivitu za aktivitou a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na stranu klienta: <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.Activities.Statements.WriteLine> Přijatá odpověď = "+ replyMessage</span><span class="sxs-lookup"><span data-stu-id="7bd5a-221">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.ServiceModel.Activities.ReceiveReply> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client side: Reply received = " + replyMessage</span></span>  
  
14. <span data-ttu-id="7bd5a-222">`PrintTransactionInfo` Přetáhněte aktivitu <xref:System.Activities.Statements.WriteLine> za aktivitou.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-222">Drag and drop a `PrintTransactionInfo` activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
15. <span data-ttu-id="7bd5a-223">Přetáhněte aktivitu na konci pracovního postupu a nastavte její <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost na "pracovní postup klienta končí." <xref:System.Activities.Statements.WriteLine></span><span class="sxs-lookup"><span data-stu-id="7bd5a-223">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the end of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client workflow ends."</span></span> <span data-ttu-id="7bd5a-224">Dokončený pracovní postup klienta by měl vypadat jako v následujícím diagramu.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-224">The completed client workflow should look like the following diagram.</span></span>  
  
     ![Dokončený pracovní postup klienta](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. <span data-ttu-id="7bd5a-226">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-226">Build the solution.</span></span>  
  
### <a name="create-the-service-application"></a><span data-ttu-id="7bd5a-227">Vytvoření aplikace služby</span><span class="sxs-lookup"><span data-stu-id="7bd5a-227">Create the Service application</span></span>  
  
1. <span data-ttu-id="7bd5a-228">Přidejte do řešení nový projekt konzolové `Service` aplikace s názvem.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-228">Add a new Console Application project called `Service` to the solution.</span></span> <span data-ttu-id="7bd5a-229">Přidejte odkazy na následující sestavení:</span><span class="sxs-lookup"><span data-stu-id="7bd5a-229">Add references to the following assemblies:</span></span>  
  
    1. <span data-ttu-id="7bd5a-230">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="7bd5a-230">System.Activities.dll</span></span>  
  
    2. <span data-ttu-id="7bd5a-231">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="7bd5a-231">System.ServiceModel.dll</span></span>  
  
    3. <span data-ttu-id="7bd5a-232">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="7bd5a-232">System.ServiceModel.Activities.dll</span></span>  
  
2. <span data-ttu-id="7bd5a-233">Otevřete vygenerovaný soubor Program.cs a následující kód:</span><span class="sxs-lookup"><span data-stu-id="7bd5a-233">Open the generated Program.cs file and the following code:</span></span>  
  
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
  
3. <span data-ttu-id="7bd5a-234">Do projektu přidejte následující soubor App. config.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-234">Add the following app.config file to the project.</span></span>  
  
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
  
### <a name="create-the-client-application"></a><span data-ttu-id="7bd5a-235">Vytvoření klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="7bd5a-235">Create the client application</span></span>  
  
1. <span data-ttu-id="7bd5a-236">Přidejte do řešení nový projekt konzolové `Client` aplikace s názvem.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-236">Add a new Console Application project called `Client` to the solution.</span></span> <span data-ttu-id="7bd5a-237">Přidejte odkaz na System. Activities. dll.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-237">Add a reference to System.Activities.dll.</span></span>  
  
2. <span data-ttu-id="7bd5a-238">Otevřete soubor program.cs a přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="7bd5a-238">Open the program.cs file and add the following code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7bd5a-239">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7bd5a-239">See also</span></span>

- [<span data-ttu-id="7bd5a-240">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="7bd5a-240">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="7bd5a-241">Přehled transakcí ve Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="7bd5a-241">Windows Communication Foundation Transactions Overview</span></span>](../../../../docs/framework/wcf/feature-details/transactions-overview.md)
