---
title: Proces schválení dokumentu
description: Tato ukázka předvádí mnoho funkcí programovací model Windows Workflow Foundation a Windows Communication Foundation ve scénáři procesu schválení dokumentu.
ms.date: 03/30/2017
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
ms.openlocfilehash: 18b4f978e9234daf22395f0d2f6f0889d0edf966
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421407"
---
# <a name="document-approval-process"></a><span data-ttu-id="ce23e-103">Proces schválení dokumentu</span><span class="sxs-lookup"><span data-stu-id="ce23e-103">Document Approval Process</span></span>

<span data-ttu-id="ce23e-104">Tato ukázka předvádí použití mnoha funkcí programovací model Windows Workflow Foundation (WF) a Windows Communication Foundation (WCF) společně.</span><span class="sxs-lookup"><span data-stu-id="ce23e-104">This sample demonstrates the use of many Windows Workflow Foundation (WF) and Windows Communication Foundation (WCF) features together.</span></span> <span data-ttu-id="ce23e-105">Společně implementují scénář procesu schvalování dokumentů.</span><span class="sxs-lookup"><span data-stu-id="ce23e-105">Together they implement a document approval process scenario.</span></span> <span data-ttu-id="ce23e-106">Klientská aplikace může odesílat dokumenty ke schválení a schvalování dokumentů.</span><span class="sxs-lookup"><span data-stu-id="ce23e-106">A client application can submit documents for approval and approve documents.</span></span> <span data-ttu-id="ce23e-107">K dispozici je aplikace Správce schválení, která usnadňuje komunikaci mezi klienty a vynucuje pravidla schvalovacího procesu.</span><span class="sxs-lookup"><span data-stu-id="ce23e-107">An approval manager application exists to facilitate communications between clients and to enforce the rules of the approval process.</span></span> <span data-ttu-id="ce23e-108">Proces schvalování je pracovní postup, který může provést několik typů schválení.</span><span class="sxs-lookup"><span data-stu-id="ce23e-108">The approval process is a workflow that can execute several types of approval.</span></span> <span data-ttu-id="ce23e-109">Aktivity existují pro získání jediného schválení, schválení kvora (procento sady schvalovatelů) a složitý proces schvalování, který se skládá z kvora a jednoho schválení v rámci sekvence.</span><span class="sxs-lookup"><span data-stu-id="ce23e-109">Activities exist to get a single approval, a quorum approval (a percentage of set of approvers), and a complex approval process that consists of a quorum and single approval in a sequence.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ce23e-110">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="ce23e-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ce23e-111">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="ce23e-111">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="ce23e-112">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="ce23e-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ce23e-113">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ce23e-113">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`

## <a name="sample-details"></a><span data-ttu-id="ce23e-114">Podrobnosti ukázky</span><span class="sxs-lookup"><span data-stu-id="ce23e-114">Sample Details</span></span>

<span data-ttu-id="ce23e-115">Následující obrázek znázorňuje pracovní postup procesu schvalování dokumentů:</span><span class="sxs-lookup"><span data-stu-id="ce23e-115">The following graphic demonstrates the document approval process workflow:</span></span>

![Pracovní postup procesu schválení dokumentu](./media/document-approval-process/document-approval-process.jpg)

<span data-ttu-id="ce23e-117">V perspektivě klienta funkce procesu schvalování funguje takto:</span><span class="sxs-lookup"><span data-stu-id="ce23e-117">From the client's perspective, the approval process functions as follows:</span></span>

1. <span data-ttu-id="ce23e-118">Klient se přihlásí jako uživatel v systému schvalovacích procesů.</span><span class="sxs-lookup"><span data-stu-id="ce23e-118">A client subscribes to be a user in the approval process system.</span></span>

2. <span data-ttu-id="ce23e-119">Klient WCF odesílá do služby WCF hostované aplikací Správce schvalování.</span><span class="sxs-lookup"><span data-stu-id="ce23e-119">A WCF client sends to a WCF service hosted by the approval manager application.</span></span>

3. <span data-ttu-id="ce23e-120">Klientovi se vrátí jedinečné ID uživatele.</span><span class="sxs-lookup"><span data-stu-id="ce23e-120">A unique user ID is returned to the client.</span></span> <span data-ttu-id="ce23e-121">Klient se teď může zúčastnit procesů schvalování.</span><span class="sxs-lookup"><span data-stu-id="ce23e-121">The client can now participate in approval processes.</span></span>

4. <span data-ttu-id="ce23e-122">Po připojení může klient odeslat dokument ke schválení pomocí jednoho, kvora nebo složitých procesů schvalování.</span><span class="sxs-lookup"><span data-stu-id="ce23e-122">Once joined, a client can send a document for approval using single, quorum or complex approval processes.</span></span>

5. <span data-ttu-id="ce23e-123">Klikne na tlačítko v rozhraní klienta a spustí se instance pracovního postupu na hostiteli služby pracovního postupu klienta.</span><span class="sxs-lookup"><span data-stu-id="ce23e-123">A button in the client’s interface is clicked, starting a workflow instance in a client Workflow Service Host.</span></span>

6. <span data-ttu-id="ce23e-124">Pracovní postup odešle žádost o schválení aplikaci Správce schvalování.</span><span class="sxs-lookup"><span data-stu-id="ce23e-124">The workflow sends an approval request to the approval manager application.</span></span>

7. <span data-ttu-id="ce23e-125">Správce pracovních postupů spustí pracovní postup na vlastní straně, který bude reprezentovat schvalovací proces.</span><span class="sxs-lookup"><span data-stu-id="ce23e-125">The workflow manager starts a workflow on its own side to represent an approval process.</span></span>

8. <span data-ttu-id="ce23e-126">Po spuštění pracovního postupu schválení správce se výsledky odešlou zpátky klientovi.</span><span class="sxs-lookup"><span data-stu-id="ce23e-126">Once the manager approval workflow executes, the results are sent back to the client.</span></span>

9. <span data-ttu-id="ce23e-127">Klient zobrazí výsledky.</span><span class="sxs-lookup"><span data-stu-id="ce23e-127">The client displays the results.</span></span>

10. <span data-ttu-id="ce23e-128">Klient může obdržet žádost o schválení a odpovědět na žádost v jakémkoli okamžiku.</span><span class="sxs-lookup"><span data-stu-id="ce23e-128">A client may receive an approval request and respond to the request at any point in time.</span></span>

11. <span data-ttu-id="ce23e-129">Služba WCF hostovaná v klientovi může obdržet žádost o schválení z aplikace Správce schvalování.</span><span class="sxs-lookup"><span data-stu-id="ce23e-129">A WCF service hosted on the client can receive an approval request from the approval manager application.</span></span>

12. <span data-ttu-id="ce23e-130">Informace o dokumentu se zobrazí na klientovi ke kontrole.</span><span class="sxs-lookup"><span data-stu-id="ce23e-130">The document information is presented on the client for review.</span></span>

13. <span data-ttu-id="ce23e-131">Uživatel může dokument schválit nebo odmítnout.</span><span class="sxs-lookup"><span data-stu-id="ce23e-131">The user can approve or reject the document.</span></span>

14. <span data-ttu-id="ce23e-132">Klient WCF slouží k odeslání odpovědi na schválení zpět do aplikace Správce schvalování.</span><span class="sxs-lookup"><span data-stu-id="ce23e-132">A WCF client is used to send an approval response back to the approval manager application.</span></span>

<span data-ttu-id="ce23e-133">Proces schvalování vychází z pohledu aplikace schvalování Manager v zobrazení následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ce23e-133">From the approval manager application’s point of view, the approval process functions as follows:</span></span>

1. <span data-ttu-id="ce23e-134">Klient žádá o účast do systému procesu schvalování.</span><span class="sxs-lookup"><span data-stu-id="ce23e-134">A client requests to participate to the approval process system.</span></span>

2. <span data-ttu-id="ce23e-135">Služba WCF ve Správci schvalování obdrží požadavek, aby byl součástí systému schvalování procesů.</span><span class="sxs-lookup"><span data-stu-id="ce23e-135">A WCF service on the approval manager receives a request to be part of the approval process system.</span></span>

3. <span data-ttu-id="ce23e-136">Pro klienta je vygenerováno jedinečné ID.</span><span class="sxs-lookup"><span data-stu-id="ce23e-136">A unique ID is generated for the client.</span></span> <span data-ttu-id="ce23e-137">Informace o uživateli jsou uloženy v databázi aplikace.</span><span class="sxs-lookup"><span data-stu-id="ce23e-137">The user information is stored in a database.</span></span>

4. <span data-ttu-id="ce23e-138">Jedinečné ID se pošle zpátky uživateli.</span><span class="sxs-lookup"><span data-stu-id="ce23e-138">The unique ID is sent back to the user.</span></span>

5. <span data-ttu-id="ce23e-139">Obdrží se žádost o schválení.</span><span class="sxs-lookup"><span data-stu-id="ce23e-139">An approval request is receive.</span></span> <span data-ttu-id="ce23e-140">Správce schvalování provede schvalovací proces.</span><span class="sxs-lookup"><span data-stu-id="ce23e-140">The approval manager executes an approval process.</span></span>

6. <span data-ttu-id="ce23e-141">Správce schvalování obdrží žádost o schválení a spustí nový pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="ce23e-141">An approval request is received by the approval manager, starting a new workflow.</span></span>

7. <span data-ttu-id="ce23e-142">V závislosti na typu požadavku (jednoduché, kvorum nebo složité) se spustí jiná aktivita.</span><span class="sxs-lookup"><span data-stu-id="ce23e-142">Depending on the type of request (simple, quorum, or complex) a different activity is executed.</span></span>

8. <span data-ttu-id="ce23e-143">Aktivity Send a Receive se službou Correlation slouží k odeslání žádosti o schválení klientovi ke kontrole a přijetí odpovědi.</span><span class="sxs-lookup"><span data-stu-id="ce23e-143">Send and Receive activities with correlation are used to send the approval request to the client for review and receive the response.</span></span>

9. <span data-ttu-id="ce23e-144">Výsledek pracovního postupu procesu schválení je odeslán klientovi.</span><span class="sxs-lookup"><span data-stu-id="ce23e-144">The result of the approval process workflow is sent to the client.</span></span>

## <a name="using-the-sample"></a><span data-ttu-id="ce23e-145">Použití ukázky</span><span class="sxs-lookup"><span data-stu-id="ce23e-145">Using the Sample</span></span>

##### <a name="to-set-up-the-database"></a><span data-ttu-id="ce23e-146">Nastavení databáze</span><span class="sxs-lookup"><span data-stu-id="ce23e-146">To set up the database</span></span>

1. <span data-ttu-id="ce23e-147">Z příkazového řádku sady Visual Studio 2010 otevřeného s oprávněními správce přejděte do této složky DocumentApprovalProcess a spusťte Setup. cmd.</span><span class="sxs-lookup"><span data-stu-id="ce23e-147">From a Visual Studio 2010 command prompt opened with Administrator privileges, navigate to this DocumentApprovalProcess folder and run Setup.cmd.</span></span>

##### <a name="to-set-up-the-application"></a><span data-ttu-id="ce23e-148">Nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="ce23e-148">To set up the application</span></span>

1. <span data-ttu-id="ce23e-149">Pomocí sady Visual Studio 2010 otevřete soubor řešení DocumentApprovalProcess. sln.</span><span class="sxs-lookup"><span data-stu-id="ce23e-149">Using Visual Studio 2010, open the DocumentApprovalProcess.sln solution file.</span></span>

2. <span data-ttu-id="ce23e-150">Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="ce23e-150">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="ce23e-151">Chcete-li spustit řešení, spusťte aplikaci Správce schvalování kliknutím pravým tlačítkem na projekt ApprovalManager v **Průzkumník řešení** a kliknutím na položku **ladit** -> **Spustit** novou instanci z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="ce23e-151">To run the solution, launch the Approval Manager Application by right-clicking the ApprovalManager project in the **Solution Explorer** and clicking **Debug**->**Start** new instance from the right-click menu.</span></span>

    <span data-ttu-id="ce23e-152">Počkejte, až bude výstup správce, a dejte vám jistotu, že je připravený.</span><span class="sxs-lookup"><span data-stu-id="ce23e-152">Wait for the manager’s output to let you know that it is ready.</span></span>

##### <a name="to-run-the-single-approval-scenario"></a><span data-ttu-id="ce23e-153">Spuštění jediného scénáře schválení</span><span class="sxs-lookup"><span data-stu-id="ce23e-153">To run the single approval scenario</span></span>

1. <span data-ttu-id="ce23e-154">Otevřete příkazový řádek s oprávněním správce.</span><span class="sxs-lookup"><span data-stu-id="ce23e-154">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="ce23e-155">Přejděte do adresáře, který obsahuje řešení.</span><span class="sxs-lookup"><span data-stu-id="ce23e-155">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="ce23e-156">Přejděte do složky ApprovalClient\Bin\Debug a spusťte dvě instance nástroje ApprovalClient. exe.</span><span class="sxs-lookup"><span data-stu-id="ce23e-156">Navigate to the ApprovalClient\Bin\Debug folder and execute two instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="ce23e-157">Klikněte na **Vyhledat**a počkejte, než se aktivuje tlačítko **přihlášení k odběru** .</span><span class="sxs-lookup"><span data-stu-id="ce23e-157">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="ce23e-158">Zadejte libovolné uživatelské jméno a klikněte na **přihlásit k odběru**.</span><span class="sxs-lookup"><span data-stu-id="ce23e-158">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="ce23e-159">Pro jednoho klienta použijte `UserType1` a druhý typ `UserType2` .</span><span class="sxs-lookup"><span data-stu-id="ce23e-159">For one client, use `UserType1` and the other type `UserType2`.</span></span>

6. <span data-ttu-id="ce23e-160">V `UserType1` klientovi vyberte typ jednoho schválení z rozevírací nabídky a zadejte název a obsah dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ce23e-160">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="ce23e-161">Klikněte na **žádost o schválení**.</span><span class="sxs-lookup"><span data-stu-id="ce23e-161">Click **Request Approval**.</span></span>

7. <span data-ttu-id="ce23e-162">V `UserType2` klientovi se zobrazí dokument, který čeká na schválení.</span><span class="sxs-lookup"><span data-stu-id="ce23e-162">In the `UserType2` client, a document awaiting approval appears.</span></span> <span data-ttu-id="ce23e-163">Vyberte ji a stiskněte **schválit** nebo **zamítnout**.</span><span class="sxs-lookup"><span data-stu-id="ce23e-163">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="ce23e-164">Výsledky by se měly zobrazit v `UserType1` klientovi.</span><span class="sxs-lookup"><span data-stu-id="ce23e-164">The results should show in the `UserType1` client.</span></span>

##### <a name="to-run-the-quorum-approval-scenario"></a><span data-ttu-id="ce23e-165">Spuštění scénáře schválení kvora</span><span class="sxs-lookup"><span data-stu-id="ce23e-165">To run the quorum approval scenario</span></span>

1. <span data-ttu-id="ce23e-166">Otevřete příkazový řádek s oprávněním správce.</span><span class="sxs-lookup"><span data-stu-id="ce23e-166">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="ce23e-167">Přejděte do adresáře, který obsahuje řešení.</span><span class="sxs-lookup"><span data-stu-id="ce23e-167">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="ce23e-168">Přejděte do složky ApprovalClient\Bin\Debug a spusťte tři instance nástroje ApprovalClient. exe.</span><span class="sxs-lookup"><span data-stu-id="ce23e-168">Navigate to the ApprovalClient\Bin\Debug folder and execute three instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="ce23e-169">Klikněte na **Vyhledat**a počkejte, než se aktivuje tlačítko **přihlášení k odběru** .</span><span class="sxs-lookup"><span data-stu-id="ce23e-169">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="ce23e-170">Zadejte libovolné uživatelské jméno a klikněte na **přihlásit k odběru**.</span><span class="sxs-lookup"><span data-stu-id="ce23e-170">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="ce23e-171">Pro jedno použití klienta `UserType1` a druhý dva typy `UserType2` .</span><span class="sxs-lookup"><span data-stu-id="ce23e-171">For one client use `UserType1` and the other two type `UserType2`.</span></span>

6. <span data-ttu-id="ce23e-172">V `UserType1` klientovi vyberte typ schválení kvora z rozevírací nabídky a zadejte název a obsah dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ce23e-172">In the `UserType1` client, select the quorum approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="ce23e-173">Klikněte na **žádost o schválení**.</span><span class="sxs-lookup"><span data-stu-id="ce23e-173">Click **Request Approval**.</span></span> <span data-ttu-id="ce23e-174">To vyžaduje, aby dva `UserType2` klienti schválili nebo odmítli dokument.</span><span class="sxs-lookup"><span data-stu-id="ce23e-174">This requests that the two `UserType2` clients approve or reject the document.</span></span> <span data-ttu-id="ce23e-175">I když `UserType2` musí oba klienti reagovat, musí schválit dokument, jenom jeden klient, aby ho schválil.</span><span class="sxs-lookup"><span data-stu-id="ce23e-175">While both `UserType2` clients must respond, only one client must approve the document for it to be approved.</span></span>

7. <span data-ttu-id="ce23e-176">V `UserType2` klientech se zobrazí dokument čeká na schválení.</span><span class="sxs-lookup"><span data-stu-id="ce23e-176">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="ce23e-177">Vyberte ji a stiskněte **schválit** nebo **zamítnout**.</span><span class="sxs-lookup"><span data-stu-id="ce23e-177">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="ce23e-178">Výsledky by se měly zobrazit v `UserType1` klientovi.</span><span class="sxs-lookup"><span data-stu-id="ce23e-178">The results should show in the `UserType1` client.</span></span>

##### <a name="to-run-the-complex-approval-scenario"></a><span data-ttu-id="ce23e-179">Spuštění scénáře komplexního schválení</span><span class="sxs-lookup"><span data-stu-id="ce23e-179">To run the complex approval scenario</span></span>

1. <span data-ttu-id="ce23e-180">Otevřete příkazový řádek s oprávněním správce.</span><span class="sxs-lookup"><span data-stu-id="ce23e-180">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="ce23e-181">Přejděte do adresáře, který obsahuje řešení.</span><span class="sxs-lookup"><span data-stu-id="ce23e-181">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="ce23e-182">Přejděte do složky ApprovalClient\Bin\Debug a spusťte čtyři instance nástroje ApprovalClient. exe.</span><span class="sxs-lookup"><span data-stu-id="ce23e-182">Navigate to the ApprovalClient\Bin\Debug folder and execute four instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="ce23e-183">Klikněte na **Vyhledat**a počkejte, než se aktivuje tlačítko **přihlášení k odběru** .</span><span class="sxs-lookup"><span data-stu-id="ce23e-183">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="ce23e-184">Zadejte libovolné uživatelské jméno a klikněte na **přihlásit k odběru**.</span><span class="sxs-lookup"><span data-stu-id="ce23e-184">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="ce23e-185">Pro jednoho klienta používá nástroj `UserType1` ve dvou typech `UserType2` a při posledním použití `UserType3` .</span><span class="sxs-lookup"><span data-stu-id="ce23e-185">For one client use `UserType1`, in two uses type `UserType2`, and in the last use `UserType3`.</span></span>

6. <span data-ttu-id="ce23e-186">V `UserType1` klientovi vyberte typ jednoho schválení z rozevírací nabídky a zadejte název a obsah dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ce23e-186">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="ce23e-187">Klikněte na **žádost o schválení**.</span><span class="sxs-lookup"><span data-stu-id="ce23e-187">Click **Request Approval**.</span></span>

7. <span data-ttu-id="ce23e-188">V `UserType2` klientech se zobrazí dokument čeká na schválení.</span><span class="sxs-lookup"><span data-stu-id="ce23e-188">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="ce23e-189">Vyberte ji a stiskněte **schválit**, dokument se předává `UserType3` klientovi.</span><span class="sxs-lookup"><span data-stu-id="ce23e-189">Select it and press **approve**, the document is passed to the `UserType3` client.</span></span>

    <span data-ttu-id="ce23e-190">Pokud dokument schválí první `UserType2` kvorum, dokument se předává `UserType3` klientovi.</span><span class="sxs-lookup"><span data-stu-id="ce23e-190">If the document is approved by the first `UserType2` quorum, the document is passed to the `UserType3` client.</span></span>

8. <span data-ttu-id="ce23e-191">Schvalte nebo odmítněte dokument z `UserType3` klienta.</span><span class="sxs-lookup"><span data-stu-id="ce23e-191">Approve or reject the document from the `UserType3` client.</span></span> <span data-ttu-id="ce23e-192">Výsledky by se měly zobrazit v `UserType1` klientovi.</span><span class="sxs-lookup"><span data-stu-id="ce23e-192">The results should show in the `UserType1` client.</span></span>

##### <a name="to-clean-up"></a><span data-ttu-id="ce23e-193">Vyčištění</span><span class="sxs-lookup"><span data-stu-id="ce23e-193">To clean up</span></span>

1. <span data-ttu-id="ce23e-194">Z příkazového řádku sady Visual Studio 2010 přejděte do složky DocumentApprovalProcess a spusťte Cleanup. cmd.</span><span class="sxs-lookup"><span data-stu-id="ce23e-194">From a Visual Studio 2010 command prompt, navigate to the DocumentApprovalProcess folder and run Cleanup.cmd.</span></span>
