---
title: Proces schválení dokumentu
ms.date: 03/30/2017
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
ms.openlocfilehash: c28dafd3b0a1cb6dbee37fed2b3df8923ccd82c8
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="document-approval-process"></a><span data-ttu-id="9578b-102">Proces schválení dokumentu</span><span class="sxs-lookup"><span data-stu-id="9578b-102">Document Approval Process</span></span>
<span data-ttu-id="9578b-103">Tento příklad znázorňuje použití mnoha funkcí Windows Workflow Foundation (WF) a Windows Communication Foundation (WCF) společně.</span><span class="sxs-lookup"><span data-stu-id="9578b-103">This sample demonstrates the use of many Windows Workflow Foundation (WF) and Windows Communication Foundation (WCF) features together.</span></span> <span data-ttu-id="9578b-104">Společně se implementaci procesu scénáře schválení dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9578b-104">Together they implement a document approval process scenario.</span></span> <span data-ttu-id="9578b-105">Klientská aplikace může odesílat dokumenty k schválení a schválit dokumenty.</span><span class="sxs-lookup"><span data-stu-id="9578b-105">A client application can submit documents for approval and approve documents.</span></span> <span data-ttu-id="9578b-106">Aplikace Správce schválení existuje pro usnadnění komunikace mezi klienty a vynucování pravidel procesu schvalování.</span><span class="sxs-lookup"><span data-stu-id="9578b-106">An approval manager application exists to facilitate communications between clients and to enforce the rules of the approval process.</span></span> <span data-ttu-id="9578b-107">Proces schválení je pracovní postup, který můžete spustit několik typů schválení.</span><span class="sxs-lookup"><span data-stu-id="9578b-107">The approval process is a workflow that can execute several types of approval.</span></span> <span data-ttu-id="9578b-108">Aktivity existovat získat jeden schválení, schválení kvora (procento sadu schvalovatelů) a komplexní schválení proces, který se skládá z jedné schválení v pořadí a kvora.</span><span class="sxs-lookup"><span data-stu-id="9578b-108">Activities exist to get a single approval, a quorum approval (a percentage of set of approvers), and a complex approval process that consists of a quorum and single approval in a sequence.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9578b-109">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="9578b-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9578b-110">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="9578b-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9578b-111">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="9578b-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9578b-112">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="9578b-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`  
  
## <a name="sample-details"></a><span data-ttu-id="9578b-113">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="9578b-113">Sample Details</span></span>  
 <span data-ttu-id="9578b-114">Následující obrázek ukazuje pracovní postup procesu schvalování dokumentů.</span><span class="sxs-lookup"><span data-stu-id="9578b-114">The following graphic demonstrates the document approval process workflow.</span></span>  
  
 <span data-ttu-id="9578b-115">![Pracovní postup procesu schvalování dokumentů](../../../../docs/framework/windows-workflow-foundation/samples/media/approvalprocess.jpg "ApprovalProcess")</span><span class="sxs-lookup"><span data-stu-id="9578b-115">![A document approval process workflow](../../../../docs/framework/windows-workflow-foundation/samples/media/approvalprocess.jpg "ApprovalProcess")</span></span>  
  
 <span data-ttu-id="9578b-116">Z pohledu klienta schválení procesu funkce následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9578b-116">From the client's perspective, the approval process functions as follows:</span></span>  
  
1.  <span data-ttu-id="9578b-117">Klient jako odběratel u být uživatelem v systému procesu schvalování.</span><span class="sxs-lookup"><span data-stu-id="9578b-117">A client subscribes to be a user in the approval process system.</span></span>  
  
2.  <span data-ttu-id="9578b-118">Klienta WCF odešle do služby WCF hostované aplikace schválení správce.</span><span class="sxs-lookup"><span data-stu-id="9578b-118">A WCF client sends to a WCF service hosted by the approval manager application.</span></span>  
  
3.  <span data-ttu-id="9578b-119">Jedinečné ID uživatele je vrácen do klienta.</span><span class="sxs-lookup"><span data-stu-id="9578b-119">A unique user ID is returned to the client.</span></span> <span data-ttu-id="9578b-120">Klienta můžete nyní účastnit schvalovací procesy.</span><span class="sxs-lookup"><span data-stu-id="9578b-120">The client can now participate in approval processes.</span></span>  
  
4.  <span data-ttu-id="9578b-121">Po připojený, klient může odesílat dokumentu pro schválení pomocí jednoho, kvora nebo komplexní schvalovací procesy.</span><span class="sxs-lookup"><span data-stu-id="9578b-121">Once joined, a client can send a document for approval using single, quorum or complex approval processes.</span></span>  
  
5.  <span data-ttu-id="9578b-122">Stisknutí tlačítka v rozhraní klienta od instance pracovního postupu v klientovi hostitele služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9578b-122">A button in the client’s interface is clicked, starting a workflow instance in a client Workflow Service Host.</span></span>  
  
6.  <span data-ttu-id="9578b-123">Pracovní postup odešle žádost o schválení aplikace schválení správce.</span><span class="sxs-lookup"><span data-stu-id="9578b-123">The workflow sends an approval request to the approval manager application.</span></span>  
  
7.  <span data-ttu-id="9578b-124">Pracovní postup správce spustí pracovní postup na vlastní straně představují proces schvalování.</span><span class="sxs-lookup"><span data-stu-id="9578b-124">The workflow manager starts a workflow on its own side to represent an approval process.</span></span>  
  
8.  <span data-ttu-id="9578b-125">Jakmile se spustí pracovní postup schválení správce, výsledky se odesílají zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="9578b-125">Once the manager approval workflow executes, the results are sent back to the client.</span></span>  
  
9. <span data-ttu-id="9578b-126">Klient se zobrazí výsledky.</span><span class="sxs-lookup"><span data-stu-id="9578b-126">The client displays the results.</span></span>  
  
10. <span data-ttu-id="9578b-127">Klient může obdrží žádost o schválení a odpovědět na požadavek v libovolném bodě v čase.</span><span class="sxs-lookup"><span data-stu-id="9578b-127">A client may receive an approval request and respond to the request at any point in time.</span></span>  
  
11. <span data-ttu-id="9578b-128">Služby WCF hostované na straně klienta může přijímat žádost o schválení od správce aplikace schválení.</span><span class="sxs-lookup"><span data-stu-id="9578b-128">A WCF service hosted on the client can receive an approval request from the approval manager application.</span></span>  
  
12. <span data-ttu-id="9578b-129">Dokument informace jsou poskytovány na straně klienta ke kontrole.</span><span class="sxs-lookup"><span data-stu-id="9578b-129">The document information is presented on the client for review.</span></span>  
  
13. <span data-ttu-id="9578b-130">Uživatele můžete schválit nebo odmítnout dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9578b-130">The user can approve or reject the document.</span></span>  
  
14. <span data-ttu-id="9578b-131">Klienta WCF se používá k odesílání odpověď na žádost o zpět do aplikace schválení správce.</span><span class="sxs-lookup"><span data-stu-id="9578b-131">A WCF client is used to send an approval response back to the approval manager application.</span></span>  
  
 <span data-ttu-id="9578b-132">Z aplikace schválení správce schválení procesu funkce následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9578b-132">From the approval manager application’s point of view, the approval process functions as follows:</span></span>  
  
1.  <span data-ttu-id="9578b-133">Klient požádá o zapojit do procesu systému schválení.</span><span class="sxs-lookup"><span data-stu-id="9578b-133">A client requests to participate to the approval process system.</span></span>  
  
2.  <span data-ttu-id="9578b-134">Služby WCF na schválení správce přijme požadavek jako součást procesu systému schválení.</span><span class="sxs-lookup"><span data-stu-id="9578b-134">A WCF service on the approval manager receives a request to be part of the approval process system.</span></span>  
  
3.  <span data-ttu-id="9578b-135">Jedinečné ID se generuje pro klienta.</span><span class="sxs-lookup"><span data-stu-id="9578b-135">A unique ID is generated for the client.</span></span> <span data-ttu-id="9578b-136">Uživatelské informace jsou uloženy v databázi.</span><span class="sxs-lookup"><span data-stu-id="9578b-136">The user information is stored in a database.</span></span>  
  
4.  <span data-ttu-id="9578b-137">Jedinečné ID budou odeslána zpět do uživatele.</span><span class="sxs-lookup"><span data-stu-id="9578b-137">The unique ID is sent back to the user.</span></span>  
  
5.  <span data-ttu-id="9578b-138">Žádost o schválení je přijmout.</span><span class="sxs-lookup"><span data-stu-id="9578b-138">An approval request is receive.</span></span> <span data-ttu-id="9578b-139">Správce schvalování spustí proces schvalování.</span><span class="sxs-lookup"><span data-stu-id="9578b-139">The approval manager executes an approval process.</span></span>  
  
6.  <span data-ttu-id="9578b-140">Žádost o schválení byl přijat schválení správcem, spouštění nového pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9578b-140">An approval request is received by the approval manager, starting a new workflow.</span></span>  
  
7.  <span data-ttu-id="9578b-141">V závislosti na typu požadavku (jednoduchý, kvora nebo komplexní) se spustí jiné aktivitě.</span><span class="sxs-lookup"><span data-stu-id="9578b-141">Depending on the type of request (simple, quorum, or complex) a different activity is executed.</span></span>  
  
8.  <span data-ttu-id="9578b-142">Odesílání a příjmu aktivity s korelací se používají k poslat žádost o schválení klienta ke kontrole a přijímat odpovědi.</span><span class="sxs-lookup"><span data-stu-id="9578b-142">Send and Receive activities with correlation are used to send the approval request to the client for review and receive the response.</span></span>  
  
9. <span data-ttu-id="9578b-143">Výsledek procesu pracovního postupu schválení je odeslat klientovi.</span><span class="sxs-lookup"><span data-stu-id="9578b-143">The result of the approval process workflow is sent to the client.</span></span>  
  
## <a name="using-the-sample"></a><span data-ttu-id="9578b-144">Pomocí vzorku</span><span class="sxs-lookup"><span data-stu-id="9578b-144">Using the Sample</span></span>  
  
##### <a name="to-set-up-the-database"></a><span data-ttu-id="9578b-145">K nastavení databáze</span><span class="sxs-lookup"><span data-stu-id="9578b-145">To set up the database</span></span>  
  
1.  <span data-ttu-id="9578b-146">Z [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] otevřít příkazový řádek s oprávněními správce, přejděte do této složky DocumentApprovalProcess a spusťte Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="9578b-146">From a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt opened with Administrator privileges, navigate to this DocumentApprovalProcess folder and run Setup.cmd.</span></span>  
  
##### <a name="to-set-up-the-application"></a><span data-ttu-id="9578b-147">Nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="9578b-147">To set up the application</span></span>  
  
1.  <span data-ttu-id="9578b-148">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení DocumentApprovalProcess.sln.</span><span class="sxs-lookup"><span data-stu-id="9578b-148">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the DocumentApprovalProcess.sln solution file.</span></span>  
  
2.  <span data-ttu-id="9578b-149">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="9578b-149">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="9578b-150">Pokud chcete spustit řešení, Správce schvalování aplikaci spustit kliknutím pravým tlačítkem myši na projekt ApprovalManager **Průzkumníku řešení** a kliknutím na **ladění**->**Start**  nové instance z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="9578b-150">To run the solution, launch the Approval Manager Application by right-clicking the ApprovalManager project in the **Solution Explorer** and clicking **Debug**->**Start** new instance from the right-click menu.</span></span>  
  
     <span data-ttu-id="9578b-151">Počkejte manažera výstup do vám oznamuje, že je připravený.</span><span class="sxs-lookup"><span data-stu-id="9578b-151">Wait for the manager’s output to let you know that it is ready.</span></span>  
  
##### <a name="to-run-the-single-approval-scenario"></a><span data-ttu-id="9578b-152">Ke spuštění jedné schválení scénář</span><span class="sxs-lookup"><span data-stu-id="9578b-152">To run the single approval scenario</span></span>  
  
1.  <span data-ttu-id="9578b-153">Otevřete příkazový řádek s oprávněním správce.</span><span class="sxs-lookup"><span data-stu-id="9578b-153">Open a command prompt with administrator permission.</span></span>  
  
2.  <span data-ttu-id="9578b-154">Přejděte do adresáře, který obsahuje řešení.</span><span class="sxs-lookup"><span data-stu-id="9578b-154">Navigate to the directory that contains the solution.</span></span>  
  
3.  <span data-ttu-id="9578b-155">Přejděte do složky ApprovalClient\Bin\Debug a provést dvě instance ApprovalClient.exe.</span><span class="sxs-lookup"><span data-stu-id="9578b-155">Navigate to the ApprovalClient\Bin\Debug folder and execute two instances of ApprovalClient.exe.</span></span>  
  
4.  <span data-ttu-id="9578b-156">Klikněte na tlačítko **zjistit**, počkejte **přihlášení k odběru** tlačítko je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="9578b-156">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5.  <span data-ttu-id="9578b-157">Zadejte libovolné uživatelské jméno a klikněte na **přihlášení k odběru**.</span><span class="sxs-lookup"><span data-stu-id="9578b-157">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="9578b-158">Pro jednoho klienta, použijte `UserType1` a v případě druhého typu `UserType2`.</span><span class="sxs-lookup"><span data-stu-id="9578b-158">For one client, use `UserType1` and the other type `UserType2`.</span></span>  
  
6.  <span data-ttu-id="9578b-159">V `UserType1` klienta, vyberte jeden schválení typu z rozevírací nabídky a zadejte název dokumentu a obsahu.</span><span class="sxs-lookup"><span data-stu-id="9578b-159">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="9578b-160">Klikněte na tlačítko **požádat o schválení**.</span><span class="sxs-lookup"><span data-stu-id="9578b-160">Click **Request Approval**.</span></span>  
  
7.  <span data-ttu-id="9578b-161">V `UserType2` se zobrazí dokument čeká na schválení klienta.</span><span class="sxs-lookup"><span data-stu-id="9578b-161">In the `UserType2` client, a document awaiting approval appears.</span></span> <span data-ttu-id="9578b-162">Vyberte ho a stiskněte klávesu **schválit** nebo **odmítnout**.</span><span class="sxs-lookup"><span data-stu-id="9578b-162">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="9578b-163">Výsledky by měl zobrazit v `UserType1` klienta.</span><span class="sxs-lookup"><span data-stu-id="9578b-163">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-run-the-quorum-approval-scenario"></a><span data-ttu-id="9578b-164">Ke spuštění scénáře schválení kvora</span><span class="sxs-lookup"><span data-stu-id="9578b-164">To run the quorum approval scenario</span></span>  
  
1.  <span data-ttu-id="9578b-165">Otevřete příkazový řádek s oprávněním správce.</span><span class="sxs-lookup"><span data-stu-id="9578b-165">Open a command prompt with administrator permission.</span></span>  
  
2.  <span data-ttu-id="9578b-166">Přejděte do adresáře, který obsahuje řešení.</span><span class="sxs-lookup"><span data-stu-id="9578b-166">Navigate to the directory that contains the solution.</span></span>  
  
3.  <span data-ttu-id="9578b-167">Přejděte do složky ApprovalClient\Bin\Debug a provést tři instance ApprovalClient.exe.</span><span class="sxs-lookup"><span data-stu-id="9578b-167">Navigate to the ApprovalClient\Bin\Debug folder and execute three instances of ApprovalClient.exe.</span></span>  
  
4.  <span data-ttu-id="9578b-168">Klikněte na tlačítko **zjistit**, počkejte **přihlášení k odběru** tlačítko je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="9578b-168">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5.  <span data-ttu-id="9578b-169">Zadejte libovolné uživatelské jméno a klikněte na **přihlášení k odběru**.</span><span class="sxs-lookup"><span data-stu-id="9578b-169">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="9578b-170">Pro jednoho klienta používat `UserType1` a další dva typy `UserType2`.</span><span class="sxs-lookup"><span data-stu-id="9578b-170">For one client use `UserType1` and the other two type `UserType2`.</span></span>  
  
6.  <span data-ttu-id="9578b-171">V `UserType1` klienta, vyberte schválení kvora typu z rozevírací nabídky a zadejte název dokumentu a obsahu.</span><span class="sxs-lookup"><span data-stu-id="9578b-171">In the `UserType1` client, select the quorum approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="9578b-172">Klikněte na tlačítko **požádat o schválení**.</span><span class="sxs-lookup"><span data-stu-id="9578b-172">Click **Request Approval**.</span></span> <span data-ttu-id="9578b-173">To požadavky, které dva `UserType2` klienty schválit nebo odmítnout dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9578b-173">This requests that the two `UserType2` clients approve or reject the document.</span></span> <span data-ttu-id="9578b-174">Při obě `UserType2` klienti musí odpovědět, jen jeden klientský musí schválit v dokumentu ji ke schválení.</span><span class="sxs-lookup"><span data-stu-id="9578b-174">While both `UserType2` clients must respond, only one client must approve the document for it to be approved.</span></span>  
  
7.  <span data-ttu-id="9578b-175">V `UserType2` klientů, se zobrazí dokument čeká na schválení.</span><span class="sxs-lookup"><span data-stu-id="9578b-175">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="9578b-176">Vyberte ho a stiskněte klávesu **schválit** nebo **odmítnout**.</span><span class="sxs-lookup"><span data-stu-id="9578b-176">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="9578b-177">Výsledky by měl zobrazit v `UserType1` klienta.</span><span class="sxs-lookup"><span data-stu-id="9578b-177">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-run-the-complex-approval-scenario"></a><span data-ttu-id="9578b-178">Ke spuštění scénář komplexní schválení</span><span class="sxs-lookup"><span data-stu-id="9578b-178">To run the complex approval scenario</span></span>  
  
1.  <span data-ttu-id="9578b-179">Otevřete příkazový řádek s oprávněním správce.</span><span class="sxs-lookup"><span data-stu-id="9578b-179">Open a command prompt with administrator permission.</span></span>  
  
2.  <span data-ttu-id="9578b-180">Přejděte do adresáře, který obsahuje řešení.</span><span class="sxs-lookup"><span data-stu-id="9578b-180">Navigate to the directory that contains the solution.</span></span>  
  
3.  <span data-ttu-id="9578b-181">Přejděte do složky ApprovalClient\Bin\Debug a provést čtyři instance ApprovalClient.exe.</span><span class="sxs-lookup"><span data-stu-id="9578b-181">Navigate to the ApprovalClient\Bin\Debug folder and execute four instances of ApprovalClient.exe.</span></span>  
  
4.  <span data-ttu-id="9578b-182">Klikněte na tlačítko **zjistit**, počkejte **přihlášení k odběru** tlačítko je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="9578b-182">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5.  <span data-ttu-id="9578b-183">Zadejte libovolné uživatelské jméno a klikněte na **přihlášení k odběru**.</span><span class="sxs-lookup"><span data-stu-id="9578b-183">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="9578b-184">Pro jednoho klienta používat `UserType1`v dva používá typ `UserType2`a v posledního použití `UserType3`.</span><span class="sxs-lookup"><span data-stu-id="9578b-184">For one client use `UserType1`, in two uses type `UserType2`, and in the last use `UserType3`.</span></span>  
  
6.  <span data-ttu-id="9578b-185">V `UserType1` klienta, vyberte jeden schválení typu z rozevírací nabídky a zadejte název dokumentu a obsahu.</span><span class="sxs-lookup"><span data-stu-id="9578b-185">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="9578b-186">Klikněte na tlačítko **požádat o schválení**.</span><span class="sxs-lookup"><span data-stu-id="9578b-186">Click **Request Approval**.</span></span>  
  
7.  <span data-ttu-id="9578b-187">V `UserType2` klientů, se zobrazí dokument čeká na schválení.</span><span class="sxs-lookup"><span data-stu-id="9578b-187">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="9578b-188">Vyberte ho a stiskněte klávesu **schválit**, dokument je předána `UserType3` klienta.</span><span class="sxs-lookup"><span data-stu-id="9578b-188">Select it and press **approve**, the document is passed to the `UserType3` client.</span></span>  
  
     <span data-ttu-id="9578b-189">Pokud dokument schválí první `UserType2` kvora, dokument je předána `UserType3` klienta.</span><span class="sxs-lookup"><span data-stu-id="9578b-189">If the document is approved by the first `UserType2` quorum, the document is passed to the `UserType3` client.</span></span>  
  
8.  <span data-ttu-id="9578b-190">Schválit nebo odmítnout dokumentu z `UserType3` klienta.</span><span class="sxs-lookup"><span data-stu-id="9578b-190">Approve or reject the document from the `UserType3` client.</span></span> <span data-ttu-id="9578b-191">Výsledky by měl zobrazit v `UserType1` klienta.</span><span class="sxs-lookup"><span data-stu-id="9578b-191">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-clean-up"></a><span data-ttu-id="9578b-192">Vyčistěte</span><span class="sxs-lookup"><span data-stu-id="9578b-192">To clean up</span></span>  
  
1.  <span data-ttu-id="9578b-193">Z [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazový řádek, přejděte do složky DocumentApprovalProcess a spusťte Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="9578b-193">From a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, navigate to the DocumentApprovalProcess folder and run Cleanup.cmd.</span></span>