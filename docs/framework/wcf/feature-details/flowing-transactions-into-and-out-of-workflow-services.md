---
title: "Tok transakcí do služeb pracovních postupů a mimo ně"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d097068720bb937911316fdb29a83ba0e8e67713
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a><span data-ttu-id="fff72-102">Tok transakcí do služeb pracovních postupů a mimo ně</span><span class="sxs-lookup"><span data-stu-id="fff72-102">Flowing Transactions into and out of Workflow Services</span></span>
<span data-ttu-id="fff72-103">Pracovní postup služby a klienti mohou účastnit transakce.</span><span class="sxs-lookup"><span data-stu-id="fff72-103">Workflow services and clients can participate in transactions.</span></span>  <span data-ttu-id="fff72-104">Pro operaci služby, který se stane součástí vedlejším transakce, umístit <xref:System.ServiceModel.Activities.Receive> aktivita v rámci <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="fff72-104">For a service operation to become part of an ambient transaction, place a <xref:System.ServiceModel.Activities.Receive> activity within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="fff72-105">Volání pomocí <xref:System.ServiceModel.Activities.Send> nebo <xref:System.ServiceModel.Activities.SendReply> aktivita v rámci <xref:System.ServiceModel.Activities.TransactedReceiveScope> bude také provést v rámci vedlejším transakce.</span><span class="sxs-lookup"><span data-stu-id="fff72-105">Any calls made by a <xref:System.ServiceModel.Activities.Send> or a <xref:System.ServiceModel.Activities.SendReply> activity within the <xref:System.ServiceModel.Activities.TransactedReceiveScope> will also be made within the ambient transaction.</span></span> <span data-ttu-id="fff72-106">Klientská aplikace pracovního postupu můžete vytvořit pomocí vedlejším transakce <xref:System.Activities.Statements.TransactionScope> aktivity a volání operací služby pomocí vedlejším transakce.</span><span class="sxs-lookup"><span data-stu-id="fff72-106">A workflow client application can create an ambient transaction by using the <xref:System.Activities.Statements.TransactionScope> activity and call service operations using the ambient transaction.</span></span> <span data-ttu-id="fff72-107">Toto téma vás provede procesem vytvoření služby pracovního postupu a pracovní postup klienta, které se začlení transakcí.</span><span class="sxs-lookup"><span data-stu-id="fff72-107">This topic walks you through creating a workflow service and workflow client that participate in transactions.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="fff72-108">Pokud je v rámci transakce načíst instanci pracovního postupu služby a pracovní postup obsahuje <xref:System.Activities.Statements.Persist> aktivity, instance pracovního postupu se zablokuje, dokud transakce časového limitu.</span><span class="sxs-lookup"><span data-stu-id="fff72-108">If a workflow service instance is loaded within a transaction and the workflow contains a <xref:System.Activities.Statements.Persist> activity, the workflow instance will hang until the transaction times out.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fff72-109">Vždy, když používáte <xref:System.ServiceModel.Activities.TransactedReceiveScope> doporučujeme umístit všechny Receives v pracovním postupu v rámci <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="fff72-109">Whenever you use a <xref:System.ServiceModel.Activities.TransactedReceiveScope> it is recommended to place all Receives in the workflow within <xref:System.ServiceModel.Activities.TransactedReceiveScope> activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fff72-110">Při použití <xref:System.ServiceModel.Activities.TransactedReceiveScope> a doručování zpráv v nesprávném pořadí, pracovní postup bude přerušena při pokusu o doručení první zprávy mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="fff72-110">When using <xref:System.ServiceModel.Activities.TransactedReceiveScope> and messages arrive in the incorrect order, the workflow will be aborted when trying to deliver the first out of order message.</span></span> <span data-ttu-id="fff72-111">Je nutné zajistěte, aby že pracovní postup je vždy na jednotnou zastavování bod při pracovního postupu nečinné po dlouhou dobu.</span><span class="sxs-lookup"><span data-stu-id="fff72-111">You must make sure your workflow is always at a consistent stopping point when the workflow idles.</span></span> <span data-ttu-id="fff72-112">Bude možné restartovat pracovní postup z předchozího bodu trvalost přerušena pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="fff72-112">This will allow you to restart the workflow from a previous persistence point should the workflow be aborted.</span></span>  
  
### <a name="create-a-shared-library"></a><span data-ttu-id="fff72-113">Vytvoření sdílené knihovny</span><span class="sxs-lookup"><span data-stu-id="fff72-113">Create a shared library</span></span>  
  
1.  <span data-ttu-id="fff72-114">Vytvoření nové prázdné Visual Studio řešení.</span><span class="sxs-lookup"><span data-stu-id="fff72-114">Create a new empty Visual Studio Solution.</span></span>  
  
2.  <span data-ttu-id="fff72-115">Přidat nový projekt knihovny třídy s názvem `Common`.</span><span class="sxs-lookup"><span data-stu-id="fff72-115">Add a new class library project called `Common`.</span></span> <span data-ttu-id="fff72-116">Přidejte odkazy na následující sestavení:</span><span class="sxs-lookup"><span data-stu-id="fff72-116">Add references to the following assemblies:</span></span>  
  
    -   <span data-ttu-id="fff72-117">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="fff72-117">System.Activities.dll</span></span>  
  
    -   <span data-ttu-id="fff72-118">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="fff72-118">System.ServiceModel.dll</span></span>  
  
    -   <span data-ttu-id="fff72-119">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="fff72-119">System.ServiceModel.Activities.dll</span></span>  
  
    -   <span data-ttu-id="fff72-120">System.Transactions.dll</span><span class="sxs-lookup"><span data-stu-id="fff72-120">System.Transactions.dll</span></span>  
  
3.  <span data-ttu-id="fff72-121">Přidejte novou třídu s názvem `PrintTransactionInfo` k `Common` projektu.</span><span class="sxs-lookup"><span data-stu-id="fff72-121">Add a new class called `PrintTransactionInfo` to the `Common` project.</span></span> <span data-ttu-id="fff72-122">Tato třída je odvozený od <xref:System.Activities.NativeActivity> a přetížení <xref:System.Activities.NativeActivity.Execute%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="fff72-122">This class is derived from <xref:System.Activities.NativeActivity> and overloads the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
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
  
     <span data-ttu-id="fff72-123">Toto je nativní aktivity, která zobrazuje informace o vedlejším transakce a používá se v pracovních postupech služby i klient použitým v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="fff72-123">This is a native activity that displays information about the ambient transaction and is used in both the service and client workflows used in this topic.</span></span> <span data-ttu-id="fff72-124">Sestavte řešení Chcete-li k dispozici v této aktivity **běžné** části **sada nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="fff72-124">Build the solution to make this activity available in the **Common** section of the **Toolbox**.</span></span>  
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="fff72-125">Implementace služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="fff72-125">Implement the workflow service</span></span>  
  
1.  <span data-ttu-id="fff72-126">Přidejte nový [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby pracovního postupu, nazývá `WorkflowService` k `Common` projektu.</span><span class="sxs-lookup"><span data-stu-id="fff72-126">Add a new [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Workflow Service, called `WorkflowService` to the `Common` project.</span></span> <span data-ttu-id="fff72-127">Na pravé tlačítko `Common` projekt, vyberte **přidat**, **novou položku...** , Vyberte **pracovního postupu** pod **nainstalovaných šablonách** a vyberte **pracovního postupu služby WCF**.</span><span class="sxs-lookup"><span data-stu-id="fff72-127">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **WCF Workflow Service**.</span></span>  
  
     <span data-ttu-id="fff72-128">![Přidání služby pracovního postupu](../../../../docs/framework/wcf/feature-details/media/addwfservice.JPG "AddWFService")</span><span class="sxs-lookup"><span data-stu-id="fff72-128">![Adding a Workflow Service](../../../../docs/framework/wcf/feature-details/media/addwfservice.JPG "AddWFService")</span></span>  
  
2.  <span data-ttu-id="fff72-129">Odstranit výchozí `ReceiveRequest` a `SendResponse` aktivity.</span><span class="sxs-lookup"><span data-stu-id="fff72-129">Delete the default `ReceiveRequest` and `SendResponse` activities.</span></span>  
  
3.  <span data-ttu-id="fff72-130">Přetáhnout myší <xref:System.Activities.Statements.WriteLine> aktivity do `Sequential Service` aktivity.</span><span class="sxs-lookup"><span data-stu-id="fff72-130">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity into the `Sequential Service` activity.</span></span> <span data-ttu-id="fff72-131">Nastavte vlastnost text na `"Workflow Service starting ..."` jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="fff72-131">Set the text property to `"Workflow Service starting ..."` as shown in the following example.</span></span>  
  
     <span data-ttu-id="fff72-132">![Přidání aktivity WriteLine](../../../../docs/framework/wcf/feature-details/media/addwriteline.JPG "AddWriteLine")</span><span class="sxs-lookup"><span data-stu-id="fff72-132">![Adding a WriteLine activity](../../../../docs/framework/wcf/feature-details/media/addwriteline.JPG "AddWriteLine")</span></span>  
  
4.  <span data-ttu-id="fff72-133">Přetáhnout myší <xref:System.ServiceModel.Activities.TransactedReceiveScope> po <xref:System.Activities.Statements.WriteLine> aktivity.</span><span class="sxs-lookup"><span data-stu-id="fff72-133">Drag and drop a <xref:System.ServiceModel.Activities.TransactedReceiveScope> after the <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="fff72-134"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Aktivity naleznete v **zasílání zpráv** části **sada nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="fff72-134">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity can be found in the **Messaging** section of the **Toolbox**.</span></span> <span data-ttu-id="fff72-135"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Aktivity se skládá ze dvou částech **požadavku** a **textu**.</span><span class="sxs-lookup"><span data-stu-id="fff72-135">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity is composed of two sections **Request** and **Body**.</span></span> <span data-ttu-id="fff72-136">**Požadavku** část obsahuje <xref:System.ServiceModel.Activities.Receive> aktivity.</span><span class="sxs-lookup"><span data-stu-id="fff72-136">The **Request** section contains the <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="fff72-137">**Textu** část obsahuje aktivity po byla přijata zpráva provést v transakci.</span><span class="sxs-lookup"><span data-stu-id="fff72-137">The **Body** section contains the activities to execute within a transaction after a message has been received.</span></span>  
  
     <span data-ttu-id="fff72-138">![Přidání aktivity TransactedReceiveScope](../../../../docs/framework/wcf/feature-details/media/trs.JPG "TRS")</span><span class="sxs-lookup"><span data-stu-id="fff72-138">![Adding a TransactedReceiveScope activity](../../../../docs/framework/wcf/feature-details/media/trs.JPG "TRS")</span></span>  
  
5.  <span data-ttu-id="fff72-139">Vyberte <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity a klikněte na **proměnné** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="fff72-139">Select the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity and click the **Variables** button.</span></span> <span data-ttu-id="fff72-140">Přidejte následující proměnné.</span><span class="sxs-lookup"><span data-stu-id="fff72-140">Add the following variables.</span></span>  
  
     <span data-ttu-id="fff72-141">![Přidání proměnné do TransactedReceiveScope](../../../../docs/framework/wcf/feature-details/media/trsvariables.JPG "TRSVariables")</span><span class="sxs-lookup"><span data-stu-id="fff72-141">![Adding Variables to the TransactedReceiveScope](../../../../docs/framework/wcf/feature-details/media/trsvariables.JPG "TRSVariables")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fff72-142">Proměnné data, která je k dispozici ve výchozím nastavení, můžete odstranit.</span><span class="sxs-lookup"><span data-stu-id="fff72-142">You can delete the data variable that is there by default.</span></span> <span data-ttu-id="fff72-143">Můžete také použít existující proměnnou popisovač.</span><span class="sxs-lookup"><span data-stu-id="fff72-143">You can also use the existing handle variable.</span></span>  
  
6.  <span data-ttu-id="fff72-144">Přetáhnout myší <xref:System.ServiceModel.Activities.Receive> aktivita v rámci **požadavku** části <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="fff72-144">Drag and drop a <xref:System.ServiceModel.Activities.Receive> activity within the **Request** section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="fff72-145">Nastavte následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="fff72-145">Set the following properties:</span></span>  
  
    |<span data-ttu-id="fff72-146">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="fff72-146">Property</span></span>|<span data-ttu-id="fff72-147">Hodnota</span><span class="sxs-lookup"><span data-stu-id="fff72-147">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="fff72-148">CanCreateInstance</span><span class="sxs-lookup"><span data-stu-id="fff72-148">CanCreateInstance</span></span>|<span data-ttu-id="fff72-149">Hodnotu true (zaškrtávací políčko)</span><span class="sxs-lookup"><span data-stu-id="fff72-149">True (check the checkbox)</span></span>|  
    |<span data-ttu-id="fff72-150">OperationName</span><span class="sxs-lookup"><span data-stu-id="fff72-150">OperationName</span></span>|<span data-ttu-id="fff72-151">StartSample</span><span class="sxs-lookup"><span data-stu-id="fff72-151">StartSample</span></span>|  
    |<span data-ttu-id="fff72-152">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="fff72-152">ServiceContractName</span></span>|<span data-ttu-id="fff72-153">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="fff72-153">ITransactionSample</span></span>|  
  
     <span data-ttu-id="fff72-154">Pracovní postup by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="fff72-154">The workflow should look like this:</span></span>  
  
     <span data-ttu-id="fff72-155">![Přidání aktivity Receive](../../../../docs/framework/wcf/feature-details/media/serviceaddreceive.JPG "ServiceAddReceive")</span><span class="sxs-lookup"><span data-stu-id="fff72-155">![Adding a Receive activity](../../../../docs/framework/wcf/feature-details/media/serviceaddreceive.JPG "ServiceAddReceive")</span></span>  
  
7.  <span data-ttu-id="fff72-156">Klikněte **definovat...**  odkaz <xref:System.ServiceModel.Activities.Receive> aktivity a proveďte následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="fff72-156">Click the **Define...** link in the <xref:System.ServiceModel.Activities.Receive> activity and make the following settings:</span></span>  
  
     <span data-ttu-id="fff72-157">![Nastavení zprávy pro aktivitu Receive](../../../../docs/framework/wcf/feature-details/media/receivemessagesettings.JPG "ReceiveMessageSettings")</span><span class="sxs-lookup"><span data-stu-id="fff72-157">![Setting message settings for the Recieve activity](../../../../docs/framework/wcf/feature-details/media/receivemessagesettings.JPG "ReceiveMessageSettings")</span></span>  
  
8.  <span data-ttu-id="fff72-158">Přetáhnout myší <xref:System.Activities.Statements.Sequence> aktivity do části textu <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="fff72-158">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the Body section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="fff72-159">V rámci <xref:System.Activities.Statements.Sequence> aktivity přetažení dva <xref:System.Activities.Statements.WriteLine> aktivity a sady <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnosti, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="fff72-159">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop two <xref:System.Activities.Statements.WriteLine> activities and set the <xref:System.Activities.Statements.WriteLine.Text%2A> properties as shown in the following table.</span></span>  
  
    |<span data-ttu-id="fff72-160">Aktivita</span><span class="sxs-lookup"><span data-stu-id="fff72-160">Activity</span></span>|<span data-ttu-id="fff72-161">Hodnota</span><span class="sxs-lookup"><span data-stu-id="fff72-161">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="fff72-162">WriteLine 1.</span><span class="sxs-lookup"><span data-stu-id="fff72-162">1st WriteLine</span></span>|<span data-ttu-id="fff72-163">"Service: přijímat dokončené"</span><span class="sxs-lookup"><span data-stu-id="fff72-163">"Service: Receive Completed"</span></span>|  
    |<span data-ttu-id="fff72-164">WriteLine 2.</span><span class="sxs-lookup"><span data-stu-id="fff72-164">2nd WriteLine</span></span>|<span data-ttu-id="fff72-165">"Service: přijaté =" + requestMessage</span><span class="sxs-lookup"><span data-stu-id="fff72-165">"Service: Received = " + requestMessage</span></span>|  
  
     <span data-ttu-id="fff72-166">Pracovní postup by měl nyní vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="fff72-166">The workflow should now look like this:</span></span>  
  
     <span data-ttu-id="fff72-167">![Přidání aktivity WriteLine](../../../../docs/framework/wcf/feature-details/media/afteraddingwritelines.JPG "AfterAddingWriteLines")</span><span class="sxs-lookup"><span data-stu-id="fff72-167">![Adding WriteLine activities](../../../../docs/framework/wcf/feature-details/media/afteraddingwritelines.JPG "AfterAddingWriteLines")</span></span>  
  
9. <span data-ttu-id="fff72-168">Přetáhnout myší `PrintTransactionInfo` aktivity po druhá <xref:System.Activities.Statements.WriteLine> aktivity v **textu** v <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="fff72-168">Drag and drop the `PrintTransactionInfo` activity after the second <xref:System.Activities.Statements.WriteLine> activity in the **Body** in the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span>  
  
     <span data-ttu-id="fff72-169">![Po přidání PrintTransactionInfo](../../../../docs/framework/wcf/feature-details/media/afteraddingprinttransactioninfo.JPG "AfterAddingPrintTransactionInfo")</span><span class="sxs-lookup"><span data-stu-id="fff72-169">![After adding PrintTransactionInfo](../../../../docs/framework/wcf/feature-details/media/afteraddingprinttransactioninfo.JPG "AfterAddingPrintTransactionInfo")</span></span>  
  
10. <span data-ttu-id="fff72-170">Přetáhnout myší <xref:System.Activities.Statements.Assign> aktivity po `PrintTransactionInfo` aktivity a nastavit jeho vlastnosti podle následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="fff72-170">Drag and drop an <xref:System.Activities.Statements.Assign> activity after the `PrintTransactionInfo` activity and set its properties according to the following table.</span></span>  
  
    |<span data-ttu-id="fff72-171">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="fff72-171">Property</span></span>|<span data-ttu-id="fff72-172">Hodnota</span><span class="sxs-lookup"><span data-stu-id="fff72-172">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="fff72-173">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="fff72-173">To</span></span>|<span data-ttu-id="fff72-174">replyMessage</span><span class="sxs-lookup"><span data-stu-id="fff72-174">replyMessage</span></span>|  
    |<span data-ttu-id="fff72-175">Hodnota</span><span class="sxs-lookup"><span data-stu-id="fff72-175">Value</span></span>|<span data-ttu-id="fff72-176">"Service: odeslání odpovědi."</span><span class="sxs-lookup"><span data-stu-id="fff72-176">"Service: Sending reply."</span></span>|  
  
11. <span data-ttu-id="fff72-177">Přetažení <xref:System.Activities.Statements.WriteLine> aktivity po <xref:System.Activities.Statements.Assign> aktivity a sady jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost "Service: začít odpovědi."</span><span class="sxs-lookup"><span data-stu-id="fff72-177">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.Activities.Statements.Assign> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Begin reply."</span></span>  
  
     <span data-ttu-id="fff72-178">Pracovní postup by měl nyní vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="fff72-178">The workflow should now look like this:</span></span>  
  
     <span data-ttu-id="fff72-179">![Po přidání přiřazení a WriteLine](../../../../docs/framework/wcf/feature-details/media/afteraddingsbrwriteline.JPG "AfterAddingSBRWriteLine")</span><span class="sxs-lookup"><span data-stu-id="fff72-179">![After adding Assign and WriteLine](../../../../docs/framework/wcf/feature-details/media/afteraddingsbrwriteline.JPG "AfterAddingSBRWriteLine")</span></span>  
  
12. <span data-ttu-id="fff72-180">Klikněte pravým tlačítkem <xref:System.ServiceModel.Activities.Receive> aktivitu a vyberte **vytvořit SendReply** a vložte ji za poslední <xref:System.Activities.Statements.WriteLine> aktivity.</span><span class="sxs-lookup"><span data-stu-id="fff72-180">Right click the <xref:System.ServiceModel.Activities.Receive> activity and select **Create SendReply** and paste it after the last <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="fff72-181">Klikněte **definovat...**  odkaz `SendReplyToReceive` aktivity a proveďte následující nastavení.</span><span class="sxs-lookup"><span data-stu-id="fff72-181">Click the **Define...** link in the `SendReplyToReceive` activity and make the following settings.</span></span>  
  
     <span data-ttu-id="fff72-182">![Odpovědět nastavení zpráv](../../../../docs/framework/wcf/feature-details/media/replymessagesettings.JPG "ReplyMessageSettings")</span><span class="sxs-lookup"><span data-stu-id="fff72-182">![Reply message settings](../../../../docs/framework/wcf/feature-details/media/replymessagesettings.JPG "ReplyMessageSettings")</span></span>  
  
13. <span data-ttu-id="fff72-183">Přetažení <xref:System.Activities.Statements.WriteLine> aktivity po `SendReplyToReceive` aktivity a sady má <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost "Service: odpověď odeslaná."</span><span class="sxs-lookup"><span data-stu-id="fff72-183">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `SendReplyToReceive` activity and set it’s <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Reply sent."</span></span>  
  
14. <span data-ttu-id="fff72-184">Přetažení <xref:System.Activities.Statements.WriteLine> aktivity na konci pracovního postupu a sadu jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost, která má "Service: ukončení pracovního postupu, stiskněte klávesu ENTER, chcete-li ukončit."</span><span class="sxs-lookup"><span data-stu-id="fff72-184">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the bottom of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Workflow ends, press ENTER to exit."</span></span>  
  
     <span data-ttu-id="fff72-185">Dokončené služby pracovního postupu by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="fff72-185">The completed service workflow should look like this:</span></span>  
  
     <span data-ttu-id="fff72-186">![Dokončení pracovního postupu služby](../../../../docs/framework/wcf/feature-details/media/servicecomplete.jpg "ServiceComplete")</span><span class="sxs-lookup"><span data-stu-id="fff72-186">![Complete Service Workflow](../../../../docs/framework/wcf/feature-details/media/servicecomplete.jpg "ServiceComplete")</span></span>  
  
### <a name="implement-the-workflow-client"></a><span data-ttu-id="fff72-187">Implementace klienta pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="fff72-187">Implement the workflow client</span></span>  
  
1.  <span data-ttu-id="fff72-188">Přidejte novou aplikaci WCF pracovního postupu, s názvem `WorkflowClient` k `Common` projektu.</span><span class="sxs-lookup"><span data-stu-id="fff72-188">Add a new WCF Workflow application, called `WorkflowClient` to the `Common` project.</span></span> <span data-ttu-id="fff72-189">Na pravé tlačítko `Common` projekt, vyberte **přidat**, **novou položku...** , Vyberte **pracovního postupu** pod **nainstalovaných šablonách** a vyberte **aktivity**.</span><span class="sxs-lookup"><span data-stu-id="fff72-189">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **Activity**.</span></span>  
  
     <span data-ttu-id="fff72-190">![Přidání aktivity projektu](../../../../docs/framework/wcf/feature-details/media/addactivity.JPG "AddActivity")</span><span class="sxs-lookup"><span data-stu-id="fff72-190">![Add an Activity project](../../../../docs/framework/wcf/feature-details/media/addactivity.JPG "AddActivity")</span></span>  
  
2.  <span data-ttu-id="fff72-191">Přetáhnout myší <xref:System.Activities.Statements.Sequence> aktivity na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="fff72-191">Drag and drop a <xref:System.Activities.Statements.Sequence> activity onto the design surface.</span></span>  
  
3.  <span data-ttu-id="fff72-192">V rámci <xref:System.Activities.Statements.Sequence> aktivity přetažení <xref:System.Activities.Statements.WriteLine> aktivity a sady jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost `"Client: Workflow starting"`.</span><span class="sxs-lookup"><span data-stu-id="fff72-192">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop a <xref:System.Activities.Statements.WriteLine> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to `"Client: Workflow starting"`.</span></span> <span data-ttu-id="fff72-193">Pracovní postup by měl nyní vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="fff72-193">The workflow should now look like this:</span></span>  
  
     <span data-ttu-id="fff72-194">![Přidat aktivitu WriteLine](../../../../docs/framework/wcf/feature-details/media/clientaddwriteline.JPG "ClientAddWriteLine")</span><span class="sxs-lookup"><span data-stu-id="fff72-194">![Add a WriteLine activity](../../../../docs/framework/wcf/feature-details/media/clientaddwriteline.JPG "ClientAddWriteLine")</span></span>  
  
4.  <span data-ttu-id="fff72-195">Přetáhnout myší <xref:System.Activities.Statements.TransactionScope> aktivity po <xref:System.Activities.Statements.WriteLine> aktivity.</span><span class="sxs-lookup"><span data-stu-id="fff72-195">Drag and drop a <xref:System.Activities.Statements.TransactionScope> activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  <span data-ttu-id="fff72-196">Vyberte <xref:System.Activities.Statements.TransactionScope> aktivity, klikněte na tlačítko proměnné a přidejte následující proměnné.</span><span class="sxs-lookup"><span data-stu-id="fff72-196">Select the <xref:System.Activities.Statements.TransactionScope> activity, click the Variables button and add the following variables.</span></span>  
  
     <span data-ttu-id="fff72-197">![Přidání proměnné do v objektu TransactionScope](../../../../docs/framework/wcf/feature-details/media/tsvariables.JPG "TSVariables")</span><span class="sxs-lookup"><span data-stu-id="fff72-197">![Add variables to the TransactionScope](../../../../docs/framework/wcf/feature-details/media/tsvariables.JPG "TSVariables")</span></span>  
  
5.  <span data-ttu-id="fff72-198">Přetáhnout myší <xref:System.Activities.Statements.Sequence> aktivity do textu <xref:System.Activities.Statements.TransactionScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="fff72-198">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the body of the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
6.  <span data-ttu-id="fff72-199">Přetáhnout myší `PrintTransactionInfo` aktivita v rámci<xref:System.Activities.Statements.Sequence></span><span class="sxs-lookup"><span data-stu-id="fff72-199">Drag and drop a `PrintTransactionInfo` activity within the <xref:System.Activities.Statements.Sequence></span></span>  
  
7.  <span data-ttu-id="fff72-200">Přetáhnout myší <xref:System.Activities.Statements.WriteLine> aktivity po `PrintTransactionInfo` aktivity a sady jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost "Klienta: začátku odeslat".</span><span class="sxs-lookup"><span data-stu-id="fff72-200">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `PrintTransactionInfo` activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Beginning Send".</span></span> <span data-ttu-id="fff72-201">Pracovní postup by měl nyní vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="fff72-201">The workflow should now look like this:</span></span>  
  
     <span data-ttu-id="fff72-202">![Přidání aktivity](../../../../docs/framework/wcf/feature-details/media/clientaddcbswriteline.JPG "ClientAddCBSWriteLine")</span><span class="sxs-lookup"><span data-stu-id="fff72-202">![Adding activities](../../../../docs/framework/wcf/feature-details/media/clientaddcbswriteline.JPG "ClientAddCBSWriteLine")</span></span>  
  
8.  <span data-ttu-id="fff72-203">Přetáhnout myší <xref:System.ServiceModel.Activities.Send> aktivity po <xref:System.Activities.Statements.Assign> aktivity a nastavte následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="fff72-203">Drag and drop a <xref:System.ServiceModel.Activities.Send> activity after the <xref:System.Activities.Statements.Assign> activity and set the following properties:</span></span>  
  
    |<span data-ttu-id="fff72-204">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="fff72-204">Property</span></span>|<span data-ttu-id="fff72-205">Hodnota</span><span class="sxs-lookup"><span data-stu-id="fff72-205">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="fff72-206">EndpointConfigurationName</span><span class="sxs-lookup"><span data-stu-id="fff72-206">EndpointConfigurationName</span></span>|<span data-ttu-id="fff72-207">workflowServiceEndpoint</span><span class="sxs-lookup"><span data-stu-id="fff72-207">workflowServiceEndpoint</span></span>|  
    |<span data-ttu-id="fff72-208">OperationName</span><span class="sxs-lookup"><span data-stu-id="fff72-208">OperationName</span></span>|<span data-ttu-id="fff72-209">StartSample</span><span class="sxs-lookup"><span data-stu-id="fff72-209">StartSample</span></span>|  
    |<span data-ttu-id="fff72-210">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="fff72-210">ServiceContractName</span></span>|<span data-ttu-id="fff72-211">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="fff72-211">ITransactionSample</span></span>|  
  
     <span data-ttu-id="fff72-212">Pracovní postup by měl nyní vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="fff72-212">The workflow should now look like this:</span></span>  
  
     <span data-ttu-id="fff72-213">![Nastavení vlastnosti Send aktivity](../../../../docs/framework/wcf/feature-details/media/clientsendsettings.JPG "ClientSendSettings")</span><span class="sxs-lookup"><span data-stu-id="fff72-213">![Setting the Send activity properties](../../../../docs/framework/wcf/feature-details/media/clientsendsettings.JPG "ClientSendSettings")</span></span>  
  
9. <span data-ttu-id="fff72-214">Klikněte **definovat...**  propojit a proveďte následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="fff72-214">Click the **Define...** link and make the following settings:</span></span>  
  
     <span data-ttu-id="fff72-215">![Odeslat zprávu nastavení aktivity](../../../../docs/framework/wcf/feature-details/media/sendmessagesettings.JPG "SendMessageSettings")</span><span class="sxs-lookup"><span data-stu-id="fff72-215">![Send activity message settings](../../../../docs/framework/wcf/feature-details/media/sendmessagesettings.JPG "SendMessageSettings")</span></span>  
  
10. <span data-ttu-id="fff72-216">Klikněte pravým tlačítkem <xref:System.ServiceModel.Activities.Send> aktivitu a vyberte **vytvořit ReceiveReply**.</span><span class="sxs-lookup"><span data-stu-id="fff72-216">Right click the <xref:System.ServiceModel.Activities.Send> activity and select **Create ReceiveReply**.</span></span> <span data-ttu-id="fff72-217"><xref:System.ServiceModel.Activities.ReceiveReply> Aktivity se po automaticky umístí <xref:System.ServiceModel.Activities.Send> aktivity.</span><span class="sxs-lookup"><span data-stu-id="fff72-217">The <xref:System.ServiceModel.Activities.ReceiveReply> activity will be automatically placed after the <xref:System.ServiceModel.Activities.Send> activity.</span></span>  
  
11. <span data-ttu-id="fff72-218">Klikněte na možnost definovat... odkaz na ReceiveReplyForSend aktivity a proveďte následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="fff72-218">Click the Define... link on the ReceiveReplyForSend activity and make the following settings:</span></span>  
  
     <span data-ttu-id="fff72-219">![Nastavení zpráv ReceiveForSend](../../../../docs/framework/wcf/feature-details/media/clientreplymessagesettings.JPG "ClientReplyMessageSettings")</span><span class="sxs-lookup"><span data-stu-id="fff72-219">![Setting the ReceiveForSend message settings](../../../../docs/framework/wcf/feature-details/media/clientreplymessagesettings.JPG "ClientReplyMessageSettings")</span></span>  
  
12. <span data-ttu-id="fff72-220">Přetažení <xref:System.Activities.Statements.WriteLine> aktivity mezi <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity a sady jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost "klienta: dokončení odesílání."</span><span class="sxs-lookup"><span data-stu-id="fff72-220">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity between the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> activities and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Send complete."</span></span>  
  
13. <span data-ttu-id="fff72-221">Přetáhnout myší <xref:System.Activities.Statements.WriteLine> aktivity po <xref:System.ServiceModel.Activities.ReceiveReply> aktivity a sady jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnosti "na straně klienta: odpověď přijata =" + replyMessage</span><span class="sxs-lookup"><span data-stu-id="fff72-221">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.ServiceModel.Activities.ReceiveReply> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client side: Reply received = " + replyMessage</span></span>  
  
14. <span data-ttu-id="fff72-222">Přetáhnout myší `PrintTransactionInfo` aktivity po <xref:System.Activities.Statements.WriteLine> aktivity.</span><span class="sxs-lookup"><span data-stu-id="fff72-222">Drag and drop a `PrintTransactionInfo` activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
15. <span data-ttu-id="fff72-223">Přetáhnout myší <xref:System.Activities.Statements.WriteLine> aktivity na konci pracovního postupu a sadu jeho <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost "Klienta pracovního postupu zakončením."</span><span class="sxs-lookup"><span data-stu-id="fff72-223">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the end of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client workflow ends."</span></span> <span data-ttu-id="fff72-224">Pracovní postup dokončené klienta by měl vypadat jako na následujícím diagramu.</span><span class="sxs-lookup"><span data-stu-id="fff72-224">The completed client workflow should look like the following diagram.</span></span>  
  
     <span data-ttu-id="fff72-225">![Dokončené klienta workfliow](../../../../docs/framework/wcf/feature-details/media/clientcompleteworkflow.jpg "ClientCompleteWorkflow")</span><span class="sxs-lookup"><span data-stu-id="fff72-225">![The completed client workfliow](../../../../docs/framework/wcf/feature-details/media/clientcompleteworkflow.jpg "ClientCompleteWorkflow")</span></span>  
  
16. <span data-ttu-id="fff72-226">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="fff72-226">Build the solution.</span></span>  
  
### <a name="create-the-service-application"></a><span data-ttu-id="fff72-227">Vytvořit aplikaci služby</span><span class="sxs-lookup"><span data-stu-id="fff72-227">Create the Service application</span></span>  
  
1.  <span data-ttu-id="fff72-228">Přidat nový projekt konzolové aplikace s názvem `Service` k řešení.</span><span class="sxs-lookup"><span data-stu-id="fff72-228">Add a new Console Application project called `Service` to the solution.</span></span> <span data-ttu-id="fff72-229">Přidejte odkazy na následující sestavení:</span><span class="sxs-lookup"><span data-stu-id="fff72-229">Add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="fff72-230">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="fff72-230">System.Activities.dll</span></span>  
  
    2.  <span data-ttu-id="fff72-231">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="fff72-231">System.ServiceModel.dll</span></span>  
  
    3.  <span data-ttu-id="fff72-232">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="fff72-232">System.ServiceModel.Activities.dll</span></span>  
  
2.  <span data-ttu-id="fff72-233">Otevřete generovaný soubor Program.cs a následující kód:</span><span class="sxs-lookup"><span data-stu-id="fff72-233">Open the generated Program.cs file and the following code:</span></span>  
  
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
  
3.  <span data-ttu-id="fff72-234">Následující soubor app.config přidejte do projektu.</span><span class="sxs-lookup"><span data-stu-id="fff72-234">Add the following app.config file to the project.</span></span>  
  
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
  
### <a name="create-the-client-application"></a><span data-ttu-id="fff72-235">Vytvoření aplikace klienta</span><span class="sxs-lookup"><span data-stu-id="fff72-235">Create the client application</span></span>  
  
1.  <span data-ttu-id="fff72-236">Přidat nový projekt konzolové aplikace s názvem `Client` k řešení.</span><span class="sxs-lookup"><span data-stu-id="fff72-236">Add a new Console Application project called `Client` to the solution.</span></span> <span data-ttu-id="fff72-237">Přidáte odkaz na System.Activities.dll.</span><span class="sxs-lookup"><span data-stu-id="fff72-237">Add a reference to System.Activities.dll.</span></span>  
  
2.  <span data-ttu-id="fff72-238">Otevřete soubor program.cs a přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="fff72-238">Open the program.cs file and add the following code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fff72-239">Viz také</span><span class="sxs-lookup"><span data-stu-id="fff72-239">See Also</span></span>  
 [<span data-ttu-id="fff72-240">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="fff72-240">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="fff72-241">Transakce Windows Communication Foundation – přehled</span><span class="sxs-lookup"><span data-stu-id="fff72-241">Windows Communication Foundation Transactions Overview</span></span>](../../../../docs/framework/wcf/feature-details/transactions-overview.md)  
 [<span data-ttu-id="fff72-242">Použití TransactedReceiveScope</span><span class="sxs-lookup"><span data-stu-id="fff72-242">Use of TransactedReceiveScope</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/use-of-transactedreceivescope.md)
