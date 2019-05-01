---
title: Proces schválení dokumentu
ms.date: 03/30/2017
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
ms.openlocfilehash: dfc2e0a12d053733823427ac50066b1e4a0f97aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62005109"
---
# <a name="document-approval-process"></a><span data-ttu-id="a5322-102">Proces schválení dokumentu</span><span class="sxs-lookup"><span data-stu-id="a5322-102">Document Approval Process</span></span>
<span data-ttu-id="a5322-103">Tento příklad ukazuje použití mnoha funkcí Windows Workflow Foundation (WF) a Windows Communication Foundation (WCF) společně.</span><span class="sxs-lookup"><span data-stu-id="a5322-103">This sample demonstrates the use of many Windows Workflow Foundation (WF) and Windows Communication Foundation (WCF) features together.</span></span> <span data-ttu-id="a5322-104">Společně implementují scénář proces schválení dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a5322-104">Together they implement a document approval process scenario.</span></span> <span data-ttu-id="a5322-105">Klientská aplikace může odesílat dokumenty pro schválení a schválit dokumenty.</span><span class="sxs-lookup"><span data-stu-id="a5322-105">A client application can submit documents for approval and approve documents.</span></span> <span data-ttu-id="a5322-106">Aplikace Správce schválení existuje pro usnadnění komunikace mezi klienty a vynucení pravidel procesu schvalování.</span><span class="sxs-lookup"><span data-stu-id="a5322-106">An approval manager application exists to facilitate communications between clients and to enforce the rules of the approval process.</span></span> <span data-ttu-id="a5322-107">Proces schválení je pracovní postup, který můžete spustit několik typů schválení.</span><span class="sxs-lookup"><span data-stu-id="a5322-107">The approval process is a workflow that can execute several types of approval.</span></span> <span data-ttu-id="a5322-108">Aktivity slouží k získání jedné schválení, schválení kvora (procento sada schvalovatelů) a komplexní schválení proces, který se skládá z jedné schválení v pořadí a kvora.</span><span class="sxs-lookup"><span data-stu-id="a5322-108">Activities exist to get a single approval, a quorum approval (a percentage of set of approvers), and a complex approval process that consists of a quorum and single approval in a sequence.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="a5322-109">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="a5322-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a5322-110">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="a5322-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a5322-111">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="a5322-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a5322-112">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="a5322-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`  
  
## <a name="sample-details"></a><span data-ttu-id="a5322-113">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a5322-113">Sample Details</span></span>  
 <span data-ttu-id="a5322-114">Následující obrázek ukazuje pracovní postup procesu schvalování dokumentů:</span><span class="sxs-lookup"><span data-stu-id="a5322-114">The following graphic demonstrates the document approval process workflow:</span></span>  
  
 ![Pracovní postup procesu schvalování dokumentů](./media/document-approval-process/document-approval-process.jpg)  
  
 <span data-ttu-id="a5322-116">Z pohledu klienta schválení zpracování funkce takto:</span><span class="sxs-lookup"><span data-stu-id="a5322-116">From the client's perspective, the approval process functions as follows:</span></span>  
  
1. <span data-ttu-id="a5322-117">Klient přihlásí k odběru bude uživatel v systému proces schvalování.</span><span class="sxs-lookup"><span data-stu-id="a5322-117">A client subscribes to be a user in the approval process system.</span></span>  
  
2. <span data-ttu-id="a5322-118">Klienta WCF se odesílá do služby WCF hostované aplikace schválení správce.</span><span class="sxs-lookup"><span data-stu-id="a5322-118">A WCF client sends to a WCF service hosted by the approval manager application.</span></span>  
  
3. <span data-ttu-id="a5322-119">Jedinečné ID uživatele je vrácen do klienta.</span><span class="sxs-lookup"><span data-stu-id="a5322-119">A unique user ID is returned to the client.</span></span> <span data-ttu-id="a5322-120">Klienta můžete nyní účastnit schvalovací procesy.</span><span class="sxs-lookup"><span data-stu-id="a5322-120">The client can now participate in approval processes.</span></span>  
  
4. <span data-ttu-id="a5322-121">Po připojený, klient může odesílat dokument pro schválení pomocí jednoho, kvora nebo komplexní schvalovací procesy.</span><span class="sxs-lookup"><span data-stu-id="a5322-121">Once joined, a client can send a document for approval using single, quorum or complex approval processes.</span></span>  
  
5. <span data-ttu-id="a5322-122">Stisknutí tlačítka v rozhraní klienta spuštění instance pracovního postupu v klientovi hostitele služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a5322-122">A button in the client’s interface is clicked, starting a workflow instance in a client Workflow Service Host.</span></span>  
  
6. <span data-ttu-id="a5322-123">Pracovní postup odešle žádost o schválení aplikace schválení správce.</span><span class="sxs-lookup"><span data-stu-id="a5322-123">The workflow sends an approval request to the approval manager application.</span></span>  
  
7. <span data-ttu-id="a5322-124">Pracovní postup správce spustí pracovní postup na svůj vlastní straně k reprezentaci schvalovací proces.</span><span class="sxs-lookup"><span data-stu-id="a5322-124">The workflow manager starts a workflow on its own side to represent an approval process.</span></span>  
  
8. <span data-ttu-id="a5322-125">Jakmile se spustí pracovní postup schválení správce, se výsledky odesílají zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="a5322-125">Once the manager approval workflow executes, the results are sent back to the client.</span></span>  
  
9. <span data-ttu-id="a5322-126">Klient se zobrazí výsledky.</span><span class="sxs-lookup"><span data-stu-id="a5322-126">The client displays the results.</span></span>  
  
10. <span data-ttu-id="a5322-127">Klient může přijímat žádosti o schválení a reagovat na žádosti v libovolném bodě v čase.</span><span class="sxs-lookup"><span data-stu-id="a5322-127">A client may receive an approval request and respond to the request at any point in time.</span></span>  
  
11. <span data-ttu-id="a5322-128">Služby WCF hostované na straně klienta může přijímat žádosti o schválení aplikace pro správu schválení panelu.</span><span class="sxs-lookup"><span data-stu-id="a5322-128">A WCF service hosted on the client can receive an approval request from the approval manager application.</span></span>  
  
12. <span data-ttu-id="a5322-129">Informace o dokumentu se zobrazí na straně klienta pro kontrolu.</span><span class="sxs-lookup"><span data-stu-id="a5322-129">The document information is presented on the client for review.</span></span>  
  
13. <span data-ttu-id="a5322-130">Uživatel můžete schválit nebo odmítnout dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a5322-130">The user can approve or reject the document.</span></span>  
  
14. <span data-ttu-id="a5322-131">Klienta WCF se používá k odesílání odpovědi na schválení zpět do aplikace schválení správce.</span><span class="sxs-lookup"><span data-stu-id="a5322-131">A WCF client is used to send an approval response back to the approval manager application.</span></span>  
  
 <span data-ttu-id="a5322-132">Z aplikace schválení správce schválení zpracování funkce takto:</span><span class="sxs-lookup"><span data-stu-id="a5322-132">From the approval manager application’s point of view, the approval process functions as follows:</span></span>  
  
1. <span data-ttu-id="a5322-133">Klient požádá o se zapojit do systému proces schválení.</span><span class="sxs-lookup"><span data-stu-id="a5322-133">A client requests to participate to the approval process system.</span></span>  
  
2. <span data-ttu-id="a5322-134">Služby WCF na schválení správce obdrží žádost jako součást procesu systému schválení.</span><span class="sxs-lookup"><span data-stu-id="a5322-134">A WCF service on the approval manager receives a request to be part of the approval process system.</span></span>  
  
3. <span data-ttu-id="a5322-135">Jedinečné ID je generován pro klienta.</span><span class="sxs-lookup"><span data-stu-id="a5322-135">A unique ID is generated for the client.</span></span> <span data-ttu-id="a5322-136">Informace o uživateli je uložen v databázi.</span><span class="sxs-lookup"><span data-stu-id="a5322-136">The user information is stored in a database.</span></span>  
  
4. <span data-ttu-id="a5322-137">Jedinečné ID je odeslána zpět uživateli.</span><span class="sxs-lookup"><span data-stu-id="a5322-137">The unique ID is sent back to the user.</span></span>  
  
5. <span data-ttu-id="a5322-138">Žádost o schválení je přijímat.</span><span class="sxs-lookup"><span data-stu-id="a5322-138">An approval request is receive.</span></span> <span data-ttu-id="a5322-139">Správce schvalování spustí proces schvalování.</span><span class="sxs-lookup"><span data-stu-id="a5322-139">The approval manager executes an approval process.</span></span>  
  
6. <span data-ttu-id="a5322-140">Správce schvalování, spouští se nový pracovní postup přijme žádost o schválení.</span><span class="sxs-lookup"><span data-stu-id="a5322-140">An approval request is received by the approval manager, starting a new workflow.</span></span>  
  
7. <span data-ttu-id="a5322-141">V závislosti na typu požadavku (jednoduchý, kvora nebo komplexní) provádí jiné aktivitě.</span><span class="sxs-lookup"><span data-stu-id="a5322-141">Depending on the type of request (simple, quorum, or complex) a different activity is executed.</span></span>  
  
8. <span data-ttu-id="a5322-142">Odesílání a aktivity Receive s korelací slouží k odeslání žádosti o schválení klienta pro kontrolu a přijetí odpovědi.</span><span class="sxs-lookup"><span data-stu-id="a5322-142">Send and Receive activities with correlation are used to send the approval request to the client for review and receive the response.</span></span>  
  
9. <span data-ttu-id="a5322-143">Výsledek pracovního postupu schvalování procesu posílá do klienta.</span><span class="sxs-lookup"><span data-stu-id="a5322-143">The result of the approval process workflow is sent to the client.</span></span>  
  
## <a name="using-the-sample"></a><span data-ttu-id="a5322-144">Pomocí ukázky</span><span class="sxs-lookup"><span data-stu-id="a5322-144">Using the Sample</span></span>  
  
##### <a name="to-set-up-the-database"></a><span data-ttu-id="a5322-145">K nastavení databáze</span><span class="sxs-lookup"><span data-stu-id="a5322-145">To set up the database</span></span>  
  
1. <span data-ttu-id="a5322-146">Z příkazového řádku sady Visual Studio 2010 otevřeného s oprávněními správce přejděte na tuto složku DocumentApprovalProcess a spustit Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="a5322-146">From a Visual Studio 2010 command prompt opened with Administrator privileges, navigate to this DocumentApprovalProcess folder and run Setup.cmd.</span></span>  
  
##### <a name="to-set-up-the-application"></a><span data-ttu-id="a5322-147">Nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="a5322-147">To set up the application</span></span>  
  
1. <span data-ttu-id="a5322-148">Pomocí sady Visual Studio 2010, otevřete soubor řešení DocumentApprovalProcess.sln.</span><span class="sxs-lookup"><span data-stu-id="a5322-148">Using Visual Studio 2010, open the DocumentApprovalProcess.sln solution file.</span></span>  
  
2. <span data-ttu-id="a5322-149">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="a5322-149">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3. <span data-ttu-id="a5322-150">Spuštění řešení, schválení správce aplikaci spustit kliknutím pravým tlačítkem myši na projekt ApprovalManager v **Průzkumníka řešení** a kliknete na **ladění**->**Start**  novou instanci v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="a5322-150">To run the solution, launch the Approval Manager Application by right-clicking the ApprovalManager project in the **Solution Explorer** and clicking **Debug**->**Start** new instance from the right-click menu.</span></span>  
  
     <span data-ttu-id="a5322-151">Čekat správce výstup s oznámením, že je připravený.</span><span class="sxs-lookup"><span data-stu-id="a5322-151">Wait for the manager’s output to let you know that it is ready.</span></span>  
  
##### <a name="to-run-the-single-approval-scenario"></a><span data-ttu-id="a5322-152">Ke spuštění jedné schválení scénář</span><span class="sxs-lookup"><span data-stu-id="a5322-152">To run the single approval scenario</span></span>  
  
1. <span data-ttu-id="a5322-153">Otevřete příkazový řádek s oprávněním správce.</span><span class="sxs-lookup"><span data-stu-id="a5322-153">Open a command prompt with administrator permission.</span></span>  
  
2. <span data-ttu-id="a5322-154">Přejděte do adresáře, který obsahuje řešení.</span><span class="sxs-lookup"><span data-stu-id="a5322-154">Navigate to the directory that contains the solution.</span></span>  
  
3. <span data-ttu-id="a5322-155">Přejděte do složky ApprovalClient\Bin\Debug a spusťte dvě instance ApprovalClient.exe.</span><span class="sxs-lookup"><span data-stu-id="a5322-155">Navigate to the ApprovalClient\Bin\Debug folder and execute two instances of ApprovalClient.exe.</span></span>  
  
4. <span data-ttu-id="a5322-156">Klikněte na tlačítko **zjistit**, počkejte, dokud **odběru** tlačítko je povolené.</span><span class="sxs-lookup"><span data-stu-id="a5322-156">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5. <span data-ttu-id="a5322-157">Zadejte libovolné uživatelské jméno a klikněte na tlačítko **odběru**.</span><span class="sxs-lookup"><span data-stu-id="a5322-157">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="a5322-158">Pro jednoho klienta, použijte `UserType1` a jiný typ `UserType2`.</span><span class="sxs-lookup"><span data-stu-id="a5322-158">For one client, use `UserType1` and the other type `UserType2`.</span></span>  
  
6. <span data-ttu-id="a5322-159">V `UserType1` klienta, vyberte jeden schválení zadejte v rozevírací nabídce a zadejte název dokumentu a obsah.</span><span class="sxs-lookup"><span data-stu-id="a5322-159">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="a5322-160">Klikněte na tlačítko **žádost o schválení**.</span><span class="sxs-lookup"><span data-stu-id="a5322-160">Click **Request Approval**.</span></span>  
  
7. <span data-ttu-id="a5322-161">V `UserType2` klient, se zobrazí dokument čeká na schválení.</span><span class="sxs-lookup"><span data-stu-id="a5322-161">In the `UserType2` client, a document awaiting approval appears.</span></span> <span data-ttu-id="a5322-162">Vyberte ji a stiskněte klávesu **schválit** nebo **odmítnout**.</span><span class="sxs-lookup"><span data-stu-id="a5322-162">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="a5322-163">Výsledky by měly zobrazovat `UserType1` klienta.</span><span class="sxs-lookup"><span data-stu-id="a5322-163">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-run-the-quorum-approval-scenario"></a><span data-ttu-id="a5322-164">Chcete-li spustit scénář schválení kvora</span><span class="sxs-lookup"><span data-stu-id="a5322-164">To run the quorum approval scenario</span></span>  
  
1. <span data-ttu-id="a5322-165">Otevřete příkazový řádek s oprávněním správce.</span><span class="sxs-lookup"><span data-stu-id="a5322-165">Open a command prompt with administrator permission.</span></span>  
  
2. <span data-ttu-id="a5322-166">Přejděte do adresáře, který obsahuje řešení.</span><span class="sxs-lookup"><span data-stu-id="a5322-166">Navigate to the directory that contains the solution.</span></span>  
  
3. <span data-ttu-id="a5322-167">Přejděte do složky ApprovalClient\Bin\Debug a provést tři instance ApprovalClient.exe.</span><span class="sxs-lookup"><span data-stu-id="a5322-167">Navigate to the ApprovalClient\Bin\Debug folder and execute three instances of ApprovalClient.exe.</span></span>  
  
4. <span data-ttu-id="a5322-168">Klikněte na tlačítko **zjistit**, počkejte, dokud **odběru** tlačítko je povolené.</span><span class="sxs-lookup"><span data-stu-id="a5322-168">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5. <span data-ttu-id="a5322-169">Zadejte libovolné uživatelské jméno a klikněte na tlačítko **odběru**.</span><span class="sxs-lookup"><span data-stu-id="a5322-169">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="a5322-170">Pro jednoho klienta používat `UserType1` a další dva typy `UserType2`.</span><span class="sxs-lookup"><span data-stu-id="a5322-170">For one client use `UserType1` and the other two type `UserType2`.</span></span>  
  
6. <span data-ttu-id="a5322-171">V `UserType1` klienta, vyberte schválení kvora, zadejte v rozevírací nabídce a zadejte název dokumentu a obsah.</span><span class="sxs-lookup"><span data-stu-id="a5322-171">In the `UserType1` client, select the quorum approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="a5322-172">Klikněte na tlačítko **žádost o schválení**.</span><span class="sxs-lookup"><span data-stu-id="a5322-172">Click **Request Approval**.</span></span> <span data-ttu-id="a5322-173">To, který požaduje dva `UserType2` klienty schválit nebo odmítnout dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a5322-173">This requests that the two `UserType2` clients approve or reject the document.</span></span> <span data-ttu-id="a5322-174">Přestože obě `UserType2` klientů musí odpovědět, jen pro jednoho klienta musí schválit, aby se schválit.</span><span class="sxs-lookup"><span data-stu-id="a5322-174">While both `UserType2` clients must respond, only one client must approve the document for it to be approved.</span></span>  
  
7. <span data-ttu-id="a5322-175">V `UserType2` klientů, se zobrazí dokument čeká na schválení.</span><span class="sxs-lookup"><span data-stu-id="a5322-175">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="a5322-176">Vyberte ji a stiskněte klávesu **schválit** nebo **odmítnout**.</span><span class="sxs-lookup"><span data-stu-id="a5322-176">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="a5322-177">Výsledky by měly zobrazovat `UserType1` klienta.</span><span class="sxs-lookup"><span data-stu-id="a5322-177">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-run-the-complex-approval-scenario"></a><span data-ttu-id="a5322-178">Chcete-li spustit scénář komplexní schválení</span><span class="sxs-lookup"><span data-stu-id="a5322-178">To run the complex approval scenario</span></span>  
  
1. <span data-ttu-id="a5322-179">Otevřete příkazový řádek s oprávněním správce.</span><span class="sxs-lookup"><span data-stu-id="a5322-179">Open a command prompt with administrator permission.</span></span>  
  
2. <span data-ttu-id="a5322-180">Přejděte do adresáře, který obsahuje řešení.</span><span class="sxs-lookup"><span data-stu-id="a5322-180">Navigate to the directory that contains the solution.</span></span>  
  
3. <span data-ttu-id="a5322-181">Přejděte do složky ApprovalClient\Bin\Debug a spustit čtyři instancí ApprovalClient.exe.</span><span class="sxs-lookup"><span data-stu-id="a5322-181">Navigate to the ApprovalClient\Bin\Debug folder and execute four instances of ApprovalClient.exe.</span></span>  
  
4. <span data-ttu-id="a5322-182">Klikněte na tlačítko **zjistit**, počkejte, dokud **odběru** tlačítko je povolené.</span><span class="sxs-lookup"><span data-stu-id="a5322-182">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5. <span data-ttu-id="a5322-183">Zadejte libovolné uživatelské jméno a klikněte na tlačítko **odběru**.</span><span class="sxs-lookup"><span data-stu-id="a5322-183">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="a5322-184">Pro jednoho klienta používat `UserType1`ve dvou používá typ `UserType2`a v posledním `UserType3`.</span><span class="sxs-lookup"><span data-stu-id="a5322-184">For one client use `UserType1`, in two uses type `UserType2`, and in the last use `UserType3`.</span></span>  
  
6. <span data-ttu-id="a5322-185">V `UserType1` klienta, vyberte jeden schválení zadejte v rozevírací nabídce a zadejte název dokumentu a obsah.</span><span class="sxs-lookup"><span data-stu-id="a5322-185">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="a5322-186">Klikněte na tlačítko **žádost o schválení**.</span><span class="sxs-lookup"><span data-stu-id="a5322-186">Click **Request Approval**.</span></span>  
  
7. <span data-ttu-id="a5322-187">V `UserType2` klientů, se zobrazí dokument čeká na schválení.</span><span class="sxs-lookup"><span data-stu-id="a5322-187">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="a5322-188">Vyberte ji a stiskněte klávesu **schválit**, dokument je předán `UserType3` klienta.</span><span class="sxs-lookup"><span data-stu-id="a5322-188">Select it and press **approve**, the document is passed to the `UserType3` client.</span></span>  
  
     <span data-ttu-id="a5322-189">Po prvním schválení dokumentu `UserType2` kvora, dokument je předán `UserType3` klienta.</span><span class="sxs-lookup"><span data-stu-id="a5322-189">If the document is approved by the first `UserType2` quorum, the document is passed to the `UserType3` client.</span></span>  
  
8. <span data-ttu-id="a5322-190">Schválit nebo odmítnout dokumentu z `UserType3` klienta.</span><span class="sxs-lookup"><span data-stu-id="a5322-190">Approve or reject the document from the `UserType3` client.</span></span> <span data-ttu-id="a5322-191">Výsledky by měly zobrazovat `UserType1` klienta.</span><span class="sxs-lookup"><span data-stu-id="a5322-191">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-clean-up"></a><span data-ttu-id="a5322-192">Vyčistit</span><span class="sxs-lookup"><span data-stu-id="a5322-192">To clean up</span></span>  
  
1. <span data-ttu-id="a5322-193">Z příkazového řádku sady Visual Studio 2010 přejděte do složky DocumentApprovalProcess a spusťte Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="a5322-193">From a Visual Studio 2010 command prompt, navigate to the DocumentApprovalProcess folder and run Cleanup.cmd.</span></span>
