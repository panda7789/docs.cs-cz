---
title: Proces schválení dokumentu
ms.date: 03/30/2017
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
ms.openlocfilehash: cee43aff991f9482de7b3172174eb0e786ec1fe6
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74710845"
---
# <a name="document-approval-process"></a><span data-ttu-id="eb2c5-102">Proces schválení dokumentu</span><span class="sxs-lookup"><span data-stu-id="eb2c5-102">Document Approval Process</span></span>

<span data-ttu-id="eb2c5-103">Tato ukázka předvádí použití mnoha funkcí programovací model Windows Workflow Foundation (WF) a Windows Communication Foundation (WCF) společně.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-103">This sample demonstrates the use of many Windows Workflow Foundation (WF) and Windows Communication Foundation (WCF) features together.</span></span> <span data-ttu-id="eb2c5-104">Společně implementují scénář procesu schvalování dokumentů.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-104">Together they implement a document approval process scenario.</span></span> <span data-ttu-id="eb2c5-105">Klientská aplikace může odesílat dokumenty ke schválení a schvalování dokumentů.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-105">A client application can submit documents for approval and approve documents.</span></span> <span data-ttu-id="eb2c5-106">K dispozici je aplikace Správce schválení, která usnadňuje komunikaci mezi klienty a vynucuje pravidla schvalovacího procesu.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-106">An approval manager application exists to facilitate communications between clients and to enforce the rules of the approval process.</span></span> <span data-ttu-id="eb2c5-107">Proces schvalování je pracovní postup, který může provést několik typů schválení.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-107">The approval process is a workflow that can execute several types of approval.</span></span> <span data-ttu-id="eb2c5-108">Aktivity existují pro získání jediného schválení, schválení kvora (procento sady schvalovatelů) a složitý proces schvalování, který se skládá z kvora a jednoho schválení v rámci sekvence.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-108">Activities exist to get a single approval, a quorum approval (a percentage of set of approvers), and a complex approval process that consists of a quorum and single approval in a sequence.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eb2c5-109">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="eb2c5-110">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-110">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="eb2c5-111">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="eb2c5-112">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-112">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`

## <a name="sample-details"></a><span data-ttu-id="eb2c5-113">Podrobnosti ukázky</span><span class="sxs-lookup"><span data-stu-id="eb2c5-113">Sample Details</span></span>

<span data-ttu-id="eb2c5-114">Následující obrázek znázorňuje pracovní postup procesu schvalování dokumentů:</span><span class="sxs-lookup"><span data-stu-id="eb2c5-114">The following graphic demonstrates the document approval process workflow:</span></span>

![Pracovní postup procesu schválení dokumentu](./media/document-approval-process/document-approval-process.jpg)

<span data-ttu-id="eb2c5-116">V perspektivě klienta funkce procesu schvalování funguje takto:</span><span class="sxs-lookup"><span data-stu-id="eb2c5-116">From the client's perspective, the approval process functions as follows:</span></span>

1. <span data-ttu-id="eb2c5-117">Klient se přihlásí jako uživatel v systému schvalovacích procesů.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-117">A client subscribes to be a user in the approval process system.</span></span>

2. <span data-ttu-id="eb2c5-118">Klient WCF odesílá do služby WCF hostované aplikací Správce schvalování.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-118">A WCF client sends to a WCF service hosted by the approval manager application.</span></span>

3. <span data-ttu-id="eb2c5-119">Klientovi se vrátí jedinečné ID uživatele.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-119">A unique user ID is returned to the client.</span></span> <span data-ttu-id="eb2c5-120">Klient se teď může zúčastnit procesů schvalování.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-120">The client can now participate in approval processes.</span></span>

4. <span data-ttu-id="eb2c5-121">Po připojení může klient odeslat dokument ke schválení pomocí jednoho, kvora nebo složitých procesů schvalování.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-121">Once joined, a client can send a document for approval using single, quorum or complex approval processes.</span></span>

5. <span data-ttu-id="eb2c5-122">Klikne na tlačítko v rozhraní klienta a spustí se instance pracovního postupu na hostiteli služby pracovního postupu klienta.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-122">A button in the client’s interface is clicked, starting a workflow instance in a client Workflow Service Host.</span></span>

6. <span data-ttu-id="eb2c5-123">Pracovní postup odešle žádost o schválení aplikaci Správce schvalování.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-123">The workflow sends an approval request to the approval manager application.</span></span>

7. <span data-ttu-id="eb2c5-124">Správce pracovních postupů spustí pracovní postup na vlastní straně, který bude reprezentovat schvalovací proces.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-124">The workflow manager starts a workflow on its own side to represent an approval process.</span></span>

8. <span data-ttu-id="eb2c5-125">Po spuštění pracovního postupu schválení správce se výsledky odešlou zpátky klientovi.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-125">Once the manager approval workflow executes, the results are sent back to the client.</span></span>

9. <span data-ttu-id="eb2c5-126">Klient zobrazí výsledky.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-126">The client displays the results.</span></span>

10. <span data-ttu-id="eb2c5-127">Klient může obdržet žádost o schválení a odpovědět na žádost v jakémkoli okamžiku.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-127">A client may receive an approval request and respond to the request at any point in time.</span></span>

11. <span data-ttu-id="eb2c5-128">Služba WCF hostovaná v klientovi může obdržet žádost o schválení z aplikace Správce schvalování.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-128">A WCF service hosted on the client can receive an approval request from the approval manager application.</span></span>

12. <span data-ttu-id="eb2c5-129">Informace o dokumentu se zobrazí na klientovi ke kontrole.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-129">The document information is presented on the client for review.</span></span>

13. <span data-ttu-id="eb2c5-130">Uživatel může dokument schválit nebo odmítnout.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-130">The user can approve or reject the document.</span></span>

14. <span data-ttu-id="eb2c5-131">Klient WCF slouží k odeslání odpovědi na schválení zpět do aplikace Správce schvalování.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-131">A WCF client is used to send an approval response back to the approval manager application.</span></span>

<span data-ttu-id="eb2c5-132">Proces schvalování vychází z pohledu aplikace schvalování Manager v zobrazení následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="eb2c5-132">From the approval manager application’s point of view, the approval process functions as follows:</span></span>

1. <span data-ttu-id="eb2c5-133">Klient žádá o účast do systému procesu schvalování.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-133">A client requests to participate to the approval process system.</span></span>

2. <span data-ttu-id="eb2c5-134">Služba WCF ve Správci schvalování obdrží požadavek, aby byl součástí systému schvalování procesů.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-134">A WCF service on the approval manager receives a request to be part of the approval process system.</span></span>

3. <span data-ttu-id="eb2c5-135">Pro klienta je vygenerováno jedinečné ID.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-135">A unique ID is generated for the client.</span></span> <span data-ttu-id="eb2c5-136">Informace o uživateli jsou uloženy v databázi aplikace.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-136">The user information is stored in a database.</span></span>

4. <span data-ttu-id="eb2c5-137">Jedinečné ID se pošle zpátky uživateli.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-137">The unique ID is sent back to the user.</span></span>

5. <span data-ttu-id="eb2c5-138">Obdrží se žádost o schválení.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-138">An approval request is receive.</span></span> <span data-ttu-id="eb2c5-139">Správce schvalování provede schvalovací proces.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-139">The approval manager executes an approval process.</span></span>

6. <span data-ttu-id="eb2c5-140">Správce schvalování obdrží žádost o schválení a spustí nový pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-140">An approval request is received by the approval manager, starting a new workflow.</span></span>

7. <span data-ttu-id="eb2c5-141">V závislosti na typu požadavku (jednoduché, kvorum nebo složité) se spustí jiná aktivita.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-141">Depending on the type of request (simple, quorum, or complex) a different activity is executed.</span></span>

8. <span data-ttu-id="eb2c5-142">Aktivity Send a Receive se službou Correlation slouží k odeslání žádosti o schválení klientovi ke kontrole a přijetí odpovědi.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-142">Send and Receive activities with correlation are used to send the approval request to the client for review and receive the response.</span></span>

9. <span data-ttu-id="eb2c5-143">Výsledek pracovního postupu procesu schválení je odeslán klientovi.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-143">The result of the approval process workflow is sent to the client.</span></span>

## <a name="using-the-sample"></a><span data-ttu-id="eb2c5-144">Použití ukázky</span><span class="sxs-lookup"><span data-stu-id="eb2c5-144">Using the Sample</span></span>

##### <a name="to-set-up-the-database"></a><span data-ttu-id="eb2c5-145">Nastavení databáze</span><span class="sxs-lookup"><span data-stu-id="eb2c5-145">To set up the database</span></span>

1. <span data-ttu-id="eb2c5-146">Z příkazového řádku sady Visual Studio 2010 otevřeného s oprávněními správce přejděte do této složky DocumentApprovalProcess a spusťte Setup. cmd.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-146">From a Visual Studio 2010 command prompt opened with Administrator privileges, navigate to this DocumentApprovalProcess folder and run Setup.cmd.</span></span>

##### <a name="to-set-up-the-application"></a><span data-ttu-id="eb2c5-147">Nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="eb2c5-147">To set up the application</span></span>

1. <span data-ttu-id="eb2c5-148">Pomocí sady Visual Studio 2010 otevřete soubor řešení DocumentApprovalProcess. sln.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-148">Using Visual Studio 2010, open the DocumentApprovalProcess.sln solution file.</span></span>

2. <span data-ttu-id="eb2c5-149">Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-149">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="eb2c5-150">Chcete-li spustit řešení, spusťte aplikaci Správce schvalování kliknutím pravým tlačítkem myši na projekt ApprovalManager v **Průzkumník řešení** a kliknutím na položku **ladění**->**Spustit** novou instanci z nabídky klikněte pravým tlačítkem myši.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-150">To run the solution, launch the Approval Manager Application by right-clicking the ApprovalManager project in the **Solution Explorer** and clicking **Debug**->**Start** new instance from the right-click menu.</span></span>

    <span data-ttu-id="eb2c5-151">Počkejte, až bude výstup správce, a dejte vám jistotu, že je připravený.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-151">Wait for the manager’s output to let you know that it is ready.</span></span>

##### <a name="to-run-the-single-approval-scenario"></a><span data-ttu-id="eb2c5-152">Spuštění jediného scénáře schválení</span><span class="sxs-lookup"><span data-stu-id="eb2c5-152">To run the single approval scenario</span></span>

1. <span data-ttu-id="eb2c5-153">Otevřete příkazový řádek s oprávněním správce.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-153">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="eb2c5-154">Přejděte do adresáře, který obsahuje řešení.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-154">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="eb2c5-155">Přejděte do složky ApprovalClient\Bin\Debug a spusťte dvě instance nástroje ApprovalClient. exe.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-155">Navigate to the ApprovalClient\Bin\Debug folder and execute two instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="eb2c5-156">Klikněte na **Vyhledat**a počkejte, než se aktivuje tlačítko **přihlášení k odběru** .</span><span class="sxs-lookup"><span data-stu-id="eb2c5-156">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="eb2c5-157">Zadejte libovolné uživatelské jméno a klikněte na **přihlásit k odběru**.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-157">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="eb2c5-158">Pro jednoho klienta použijte `UserType1` a druhý typ `UserType2`.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-158">For one client, use `UserType1` and the other type `UserType2`.</span></span>

6. <span data-ttu-id="eb2c5-159">V klientovi `UserType1` v rozevírací nabídce vyberte typ jednoho schválení a zadejte název a obsah dokumentu.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-159">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="eb2c5-160">Klikněte na **žádost o schválení**.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-160">Click **Request Approval**.</span></span>

7. <span data-ttu-id="eb2c5-161">V klientovi `UserType2` se zobrazí dokument čeká na schválení.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-161">In the `UserType2` client, a document awaiting approval appears.</span></span> <span data-ttu-id="eb2c5-162">Vyberte ji a stiskněte **schválit** nebo **zamítnout**.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-162">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="eb2c5-163">Výsledky by se měly zobrazit ve `UserType1` klientovi.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-163">The results should show in the `UserType1` client.</span></span>

##### <a name="to-run-the-quorum-approval-scenario"></a><span data-ttu-id="eb2c5-164">Spuštění scénáře schválení kvora</span><span class="sxs-lookup"><span data-stu-id="eb2c5-164">To run the quorum approval scenario</span></span>

1. <span data-ttu-id="eb2c5-165">Otevřete příkazový řádek s oprávněním správce.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-165">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="eb2c5-166">Přejděte do adresáře, který obsahuje řešení.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-166">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="eb2c5-167">Přejděte do složky ApprovalClient\Bin\Debug a spusťte tři instance nástroje ApprovalClient. exe.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-167">Navigate to the ApprovalClient\Bin\Debug folder and execute three instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="eb2c5-168">Klikněte na **Vyhledat**a počkejte, než se aktivuje tlačítko **přihlášení k odběru** .</span><span class="sxs-lookup"><span data-stu-id="eb2c5-168">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="eb2c5-169">Zadejte libovolné uživatelské jméno a klikněte na **přihlásit k odběru**.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-169">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="eb2c5-170">Pro jednoho klienta použijte `UserType1` a druhý `UserType2`typu.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-170">For one client use `UserType1` and the other two type `UserType2`.</span></span>

6. <span data-ttu-id="eb2c5-171">V klientovi `UserType1` v rozevírací nabídce vyberte typ schválení kvora a zadejte název a obsah dokumentu.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-171">In the `UserType1` client, select the quorum approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="eb2c5-172">Klikněte na **žádost o schválení**.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-172">Click **Request Approval**.</span></span> <span data-ttu-id="eb2c5-173">Tím se vyžádá, že dva klienti `UserType2` schvalují nebo odmítnou dokument.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-173">This requests that the two `UserType2` clients approve or reject the document.</span></span> <span data-ttu-id="eb2c5-174">I když musí oba klienti `UserType2` reagovat, musí dokument schválit jenom jeden klient, aby ho bylo možné schválit.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-174">While both `UserType2` clients must respond, only one client must approve the document for it to be approved.</span></span>

7. <span data-ttu-id="eb2c5-175">V klientech `UserType2` se zobrazí dokument čeká na schválení.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-175">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="eb2c5-176">Vyberte ji a stiskněte **schválit** nebo **zamítnout**.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-176">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="eb2c5-177">Výsledky by se měly zobrazit ve `UserType1` klientovi.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-177">The results should show in the `UserType1` client.</span></span>

##### <a name="to-run-the-complex-approval-scenario"></a><span data-ttu-id="eb2c5-178">Spuštění scénáře komplexního schválení</span><span class="sxs-lookup"><span data-stu-id="eb2c5-178">To run the complex approval scenario</span></span>

1. <span data-ttu-id="eb2c5-179">Otevřete příkazový řádek s oprávněním správce.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-179">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="eb2c5-180">Přejděte do adresáře, který obsahuje řešení.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-180">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="eb2c5-181">Přejděte do složky ApprovalClient\Bin\Debug a spusťte čtyři instance nástroje ApprovalClient. exe.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-181">Navigate to the ApprovalClient\Bin\Debug folder and execute four instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="eb2c5-182">Klikněte na **Vyhledat**a počkejte, než se aktivuje tlačítko **přihlášení k odběru** .</span><span class="sxs-lookup"><span data-stu-id="eb2c5-182">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="eb2c5-183">Zadejte libovolné uživatelské jméno a klikněte na **přihlásit k odběru**.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-183">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="eb2c5-184">Pro jednoho klienta použijte `UserType1`, ve dvou případech používá typ `UserType2`a při posledním `UserType3`použití.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-184">For one client use `UserType1`, in two uses type `UserType2`, and in the last use `UserType3`.</span></span>

6. <span data-ttu-id="eb2c5-185">V klientovi `UserType1` v rozevírací nabídce vyberte typ jednoho schválení a zadejte název a obsah dokumentu.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-185">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="eb2c5-186">Klikněte na **žádost o schválení**.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-186">Click **Request Approval**.</span></span>

7. <span data-ttu-id="eb2c5-187">V klientech `UserType2` se zobrazí dokument čeká na schválení.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-187">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="eb2c5-188">Vyberte ji a stiskněte **schválit**, dokument se předává klientovi `UserType3`.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-188">Select it and press **approve**, the document is passed to the `UserType3` client.</span></span>

    <span data-ttu-id="eb2c5-189">Pokud je dokument schválený prvním `UserType2` kvora, dokument se předává klientovi `UserType3`.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-189">If the document is approved by the first `UserType2` quorum, the document is passed to the `UserType3` client.</span></span>

8. <span data-ttu-id="eb2c5-190">Umožňuje schválit nebo odmítnout dokument z klienta `UserType3`.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-190">Approve or reject the document from the `UserType3` client.</span></span> <span data-ttu-id="eb2c5-191">Výsledky by se měly zobrazit ve `UserType1` klientovi.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-191">The results should show in the `UserType1` client.</span></span>

##### <a name="to-clean-up"></a><span data-ttu-id="eb2c5-192">Vyčištění</span><span class="sxs-lookup"><span data-stu-id="eb2c5-192">To clean up</span></span>

1. <span data-ttu-id="eb2c5-193">Z příkazového řádku sady Visual Studio 2010 přejděte do složky DocumentApprovalProcess a spusťte Cleanup. cmd.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-193">From a Visual Studio 2010 command prompt, navigate to the DocumentApprovalProcess folder and run Cleanup.cmd.</span></span>
