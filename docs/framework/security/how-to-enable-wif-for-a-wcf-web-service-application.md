---
title: 'Postupy: Povolení WIF pro aplikaci webové služby WCF'
ms.date: 03/30/2017
ms.assetid: bfc64b3d-64e9-4093-a6a4-72e933917af7
author: BrucePerlerMS
ms.openlocfilehash: 6af0336e19df4ba2a99a52f8726e78ed92f5a79e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977428"
---
# <a name="how-to-enable-wif-for-a-wcf-web-service-application"></a><span data-ttu-id="c74bf-102">Postupy: Povolení WIF pro aplikaci webové služby WCF</span><span class="sxs-lookup"><span data-stu-id="c74bf-102">How To: Enable WIF for a WCF Web Service Application</span></span>
## <a name="applies-to"></a><span data-ttu-id="c74bf-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="c74bf-103">Applies To</span></span>  
  
-   <span data-ttu-id="c74bf-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="c74bf-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="c74bf-105">Microsoft® Windows® Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="c74bf-105">Microsoft® Windows® Communication Foundation (WCF)</span></span>  
  
## <a name="summary"></a><span data-ttu-id="c74bf-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="c74bf-106">Summary</span></span>  
 <span data-ttu-id="c74bf-107">Tento návod podrobně popisuje postupy pro povolení technologie WIF ve webové službě WCF.</span><span class="sxs-lookup"><span data-stu-id="c74bf-107">This How-To provides detailed step-by-step procedures for enabling WIF in a WCF web service.</span></span> <span data-ttu-id="c74bf-108">Obsahuje také pokyny, jak pomocí otestování aplikace ověřit, zda webová služba po spuštění aplikace správně předkládá deklarace.</span><span class="sxs-lookup"><span data-stu-id="c74bf-108">It also provides instructions for how to test the application to verify that the web service is correctly presenting claims when the application is run.</span></span> <span data-ttu-id="c74bf-109">Tento návod neobsahuje podrobné pokyny pro vytvoření služby tokenů zabezpečení (STS) a namísto toho používá službu STS určenou pro vývoj, která je součástí instalace nástroje Identity and Access Tool.</span><span class="sxs-lookup"><span data-stu-id="c74bf-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="c74bf-110">Služba STS pro vývoj neprovádí skutečné ověřování a je určena pouze pro testovací účely.</span><span class="sxs-lookup"><span data-stu-id="c74bf-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="c74bf-111">Abyste mohli dokončit postupy v tomto návodu, je třeba nainstalovat nástroj Identity and Access Tool.</span><span class="sxs-lookup"><span data-stu-id="c74bf-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="c74bf-112">Můžete ho stáhnout z následujícího umístění: [Nástroj identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)</span><span class="sxs-lookup"><span data-stu-id="c74bf-112">It can be downloaded from the following location: [Identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)</span></span>  
  
## <a name="contents"></a><span data-ttu-id="c74bf-113">Obsah</span><span class="sxs-lookup"><span data-stu-id="c74bf-113">Contents</span></span>  
  
-   <span data-ttu-id="c74bf-114">Cíle</span><span class="sxs-lookup"><span data-stu-id="c74bf-114">Objectives</span></span>  
  
-   <span data-ttu-id="c74bf-115">Přehled</span><span class="sxs-lookup"><span data-stu-id="c74bf-115">Overview</span></span>  
  
-   <span data-ttu-id="c74bf-116">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="c74bf-116">Summary of Steps</span></span>  
  
-   <span data-ttu-id="c74bf-117">Krok 1 – Vytvoření jednoduché služby WCF</span><span class="sxs-lookup"><span data-stu-id="c74bf-117">Step 1 – Create a Simple WCF Service</span></span>  
  
-   <span data-ttu-id="c74bf-118">Krok 2 – Vytvoření klientské aplikace pro službu WCF</span><span class="sxs-lookup"><span data-stu-id="c74bf-118">Step 2 – Create a Client Application for the WCF Service</span></span>  
  
-   <span data-ttu-id="c74bf-119">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="c74bf-119">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="c74bf-120">Cíle</span><span class="sxs-lookup"><span data-stu-id="c74bf-120">Objectives</span></span>  
  
-   <span data-ttu-id="c74bf-121">Vytvořte službu WCF, která vyžaduje vydané tokeny.</span><span class="sxs-lookup"><span data-stu-id="c74bf-121">Create a WCF service that requires issued tokens</span></span>  
  
-   <span data-ttu-id="c74bf-122">Vytvořte klienta WCF, který si vyžádá token od služby STS a předá jej službě WCF.</span><span class="sxs-lookup"><span data-stu-id="c74bf-122">Create a WCF client that requests a token from an STS and passes it to the WCF service</span></span>  
  
## <a name="overview"></a><span data-ttu-id="c74bf-123">Přehled</span><span class="sxs-lookup"><span data-stu-id="c74bf-123">Overview</span></span>  
 <span data-ttu-id="c74bf-124">Cílem tohoto návodu je ukázat, jak mohou vývojáři používat federované ověřování při vývoji služeb WCF.</span><span class="sxs-lookup"><span data-stu-id="c74bf-124">This How-To is intended to demonstrate how a developer can use federated authentication when developing WCF services.</span></span> <span data-ttu-id="c74bf-125">Mezi výhody použití federace ve službách WCF patří:</span><span class="sxs-lookup"><span data-stu-id="c74bf-125">Some of the benefits of using federation in WCF services include:</span></span>  
  
1. <span data-ttu-id="c74bf-126">Přesunutí logiky ověřování mimo kód služby WCF</span><span class="sxs-lookup"><span data-stu-id="c74bf-126">Factoring authentication logic out of WCF service code</span></span>  
  
2. <span data-ttu-id="c74bf-127">Opětovné využití stávajících řešení pro správu identit</span><span class="sxs-lookup"><span data-stu-id="c74bf-127">Re-using existing identity management solutions</span></span>  
  
3. <span data-ttu-id="c74bf-128">Vzájemná funkční spolupráce s jinými řešeními pro správu identit</span><span class="sxs-lookup"><span data-stu-id="c74bf-128">Interoperability with other identity solutions</span></span>  
  
4. <span data-ttu-id="c74bf-129">Flexibilita a odolnost vůči budoucím změnám</span><span class="sxs-lookup"><span data-stu-id="c74bf-129">Flexibility and resilience to future changes</span></span>  
  
 <span data-ttu-id="c74bf-130">Technologie WIF a související nástroj Identity and Access Tool usnadňují vývoj a testování služeb WCF pomocí federovaného ověřování, jak ukazují následující kroky.</span><span class="sxs-lookup"><span data-stu-id="c74bf-130">WIF and the associated Identity and Access tool make it easier to develop and test a WCF service using federated authentication, as the following steps demonstrate.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="c74bf-131">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="c74bf-131">Summary of Steps</span></span>  
  
-   <span data-ttu-id="c74bf-132">Krok 1 – Vytvoření jednoduché služby WCF</span><span class="sxs-lookup"><span data-stu-id="c74bf-132">Step 1 – Create a Simple WCF Service</span></span>  
  
-   <span data-ttu-id="c74bf-133">Krok 2 – Vytvoření klientské aplikace pro službu WCF</span><span class="sxs-lookup"><span data-stu-id="c74bf-133">Step 2 – Create a Client Application for the WCF Service</span></span>  
  
-   <span data-ttu-id="c74bf-134">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="c74bf-134">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-wcf-service"></a><span data-ttu-id="c74bf-135">Krok 1 – Vytvoření jednoduché služby WCF</span><span class="sxs-lookup"><span data-stu-id="c74bf-135">Step 1 – Create a Simple WCF Service</span></span>  
 <span data-ttu-id="c74bf-136">V tomto kroku vytvoříte novou službu WCF používající službu STS pro vývoj, která je součástí nástroje Identity and Access Tool.</span><span class="sxs-lookup"><span data-stu-id="c74bf-136">In this step, you will create a new WCF service that uses the Development STS that is included with the Identity and Access tool.</span></span>  
  
#### <a name="to-create-a-simple-wcf-service"></a><span data-ttu-id="c74bf-137">Vytvoření jednoduché služby WCF</span><span class="sxs-lookup"><span data-stu-id="c74bf-137">To create a simple WCF service</span></span>  
  
1. <span data-ttu-id="c74bf-138">Spusťte sadu Visual Studio jako správce v režimu se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="c74bf-138">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2. <span data-ttu-id="c74bf-139">V sadě Visual Studio, klikněte na tlačítko **souboru**, klikněte na tlačítko **nový**a potom klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="c74bf-139">In Visual Studio, click **File**, click **New**, and then click **Project**.</span></span>  
  
3. <span data-ttu-id="c74bf-140">V **nový projekt** okna, klikněte na tlačítko **aplikace služby WCF**.</span><span class="sxs-lookup"><span data-stu-id="c74bf-140">In the **New Project** window, click **WCF Service Application**.</span></span>  
  
4. <span data-ttu-id="c74bf-141">V **název**, zadejte `TestService` a stiskněte klávesu **OK**.</span><span class="sxs-lookup"><span data-stu-id="c74bf-141">In **Name**, enter `TestService` and press **OK**.</span></span>  
  
5. <span data-ttu-id="c74bf-142">Klikněte pravým tlačítkem myši **TestService** projektu v rámci **Průzkumníku řešení**a pak vyberte **identit a přístupu**.</span><span class="sxs-lookup"><span data-stu-id="c74bf-142">Right-click the **TestService** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
6. <span data-ttu-id="c74bf-143">**Identit a přístupu** zobrazí se okno.</span><span class="sxs-lookup"><span data-stu-id="c74bf-143">The **Identity and Access** window appears.</span></span> <span data-ttu-id="c74bf-144">V části **poskytovatelé**vyberte **testování aplikace s místní službu STS pro vývoj**, pak klikněte na tlačítko **použít**.</span><span class="sxs-lookup"><span data-stu-id="c74bf-144">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span> <span data-ttu-id="c74bf-145">Nástroj Identity and Access Tool nakonfiguruje službu používat technologie WIF a externí ověřování místní služby STS pro vývoj pomocí (**LocalSTS**) přidáním konfiguračních elementů do *Web.config* souboru.</span><span class="sxs-lookup"><span data-stu-id="c74bf-145">The Identity and Access Tool configures the service to use WIF and to outsource authentication to the local development STS (**LocalSTS**) by adding configuration elements to the *Web.config* file.</span></span>  
  
7. <span data-ttu-id="c74bf-146">V *Service1.svc.cs* přidejte `using` směrnice pro **System.Security.Claims** obor názvů a nahraďte existující kód následujícím kódem a pak soubor uložte:</span><span class="sxs-lookup"><span data-stu-id="c74bf-146">In the *Service1.svc.cs* file, add a `using` directive for the **System.Security.Claims** namespace and replace the existing code with the following, then save the file:</span></span>  
  
    ```csharp  
    public class Service1 : IService1  
    {  
        public string ComputeResponse(string input)  
        {  
            // Get the caller's identity from ClaimsPrincipal.Current  
            ClaimsPrincipal claimsPrincipal = OperationContext.Current.ClaimsPrincipal;  
  
            // Start generating the output  
            StringBuilder builder = new StringBuilder();  
            builder.AppendLine("Computed by ClaimsAwareWebService");  
            builder.AppendLine("Input received from client:" + input);  
  
            if (claimsPrincipal != null)  
            {  
                // Display the claims from the caller. Do not use this code in a production application.  
                ClaimsIdentity identity = claimsPrincipal.Identity as ClaimsIdentity;  
                builder.AppendLine("Client Name:" + identity.Name);  
                builder.AppendLine("IsAuthenticated:" + identity.IsAuthenticated);  
                builder.AppendLine("The service received the following issued claims of the client:");  
  
                // Iterate over the caller’s claims and append to the output  
                foreach (Claim claim in claimsPrincipal.Claims)  
                {  
                    builder.AppendLine("ClaimType :" + claim.Type + "   ClaimValue:" + claim.Value);  
                }  
            }  
  
            return builder.ToString();  
        }  
    }  
    ```  
  
     <span data-ttu-id="c74bf-147">`ComputeResponse` Metoda zobrazuje vlastnosti různých deklarací, které jsou vystavované **LocalSTS**.</span><span class="sxs-lookup"><span data-stu-id="c74bf-147">The `ComputeResponse` method displays the properties of various claims that are issued by **LocalSTS**.</span></span>  
  
8. <span data-ttu-id="c74bf-148">V *IService1.cs* souboru, nahraďte existující kód následujícím kódem a pak soubor uložte:</span><span class="sxs-lookup"><span data-stu-id="c74bf-148">In the *IService1.cs* file, replace the existing code with the following, then save the file:</span></span>  
  
    ```csharp  
    [ServiceContract]  
    public interface IService1  
    {  
        [OperationContract]  
        string ComputeResponse(string input);  
    }  
    ```  
  
9. <span data-ttu-id="c74bf-149">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="c74bf-149">Build the project.</span></span>  
  
10. <span data-ttu-id="c74bf-150">Stisknutím klávesy **Ctrl-F5** spusťte službu bez spuštění ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="c74bf-150">Press **Ctrl-F5** to run the service without starting the debugger.</span></span> <span data-ttu-id="c74bf-151">Na webové stránce by se otevřít pro služby a ověřte, zda **LocalSTS** spuštěna v oznamovací oblasti (na hlavním panelu systému).</span><span class="sxs-lookup"><span data-stu-id="c74bf-151">A Web page should open for the service and you can verify that **LocalSTS** is running by looking in the notification area (system tray).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="c74bf-152">Obě **TestService** a **LocalSTS** musí být spuštěna v dalším kroku přidáte odkaz na službu do klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="c74bf-152">Both **TestService** and **LocalSTS** must be running when you add the service reference to the client application in the next step.</span></span>  
  
## <a name="step-2--create-a-client-application-for-the-wcf-service"></a><span data-ttu-id="c74bf-153">Krok 2 – Vytvoření klientské aplikace pro službu WCF</span><span class="sxs-lookup"><span data-stu-id="c74bf-153">Step 2 – Create a Client Application for the WCF Service</span></span>  
 <span data-ttu-id="c74bf-154">V tomto kroku vytvoříte konzolovou aplikaci, která se pomocí služby STS pro vývoj ověřuje ve službě WCF vytvořené v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="c74bf-154">In this step, you will create a console application that uses the Development STS to authenticate with the WCF service you created in the previous step.</span></span>  
  
#### <a name="to-create-a-client-application"></a><span data-ttu-id="c74bf-155">Vytvoření klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="c74bf-155">To create a client application</span></span>  
  
1. <span data-ttu-id="c74bf-156">V sadě Visual Studio, klikněte pravým tlačítkem na řešení, klikněte na tlačítko **přidat**a potom klikněte na tlačítko **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="c74bf-156">In Visual Studio, right-click on the solution, click **Add**, and then click **New Project**.</span></span>  
  
2. <span data-ttu-id="c74bf-157">V **přidat nový projekt** okně **konzolovou aplikaci** z **Visual C#** šablony seznamu, zadejte `Client`a potom stiskněte klávesu **OK**.</span><span class="sxs-lookup"><span data-stu-id="c74bf-157">In the **Add New Project** window, select **Console Application** from the **Visual C#** templates list, enter `Client`, and then press **OK**.</span></span> <span data-ttu-id="c74bf-158">Vytvoří se nový projekt ve složce řešení.</span><span class="sxs-lookup"><span data-stu-id="c74bf-158">The new project will be created in your solution folder.</span></span>  
  
3. <span data-ttu-id="c74bf-159">Klikněte pravým tlačítkem na **odkazy** pod **klienta** projektu a pak klikněte na tlačítko **přidat odkaz na službu**.</span><span class="sxs-lookup"><span data-stu-id="c74bf-159">Right-click on **References** under the **Client** project, and then click **Add Service Reference**.</span></span>  
  
4. <span data-ttu-id="c74bf-160">V **přidat odkaz na službu** okna, klikněte na šipku rozevíracího seznamu **zjišťování** tlačítko a klikněte na tlačítko **služby v řešení**.</span><span class="sxs-lookup"><span data-stu-id="c74bf-160">In the **Add Service Reference** window, click the drop-down arrow on the **Discover** button and click **Services in Solution**.</span></span> <span data-ttu-id="c74bf-161">**Adresu** se automaticky vyplní služba WCF, který jste vytvořili dříve, a **Namespace** se nastaví na **ServiceReference1**.</span><span class="sxs-lookup"><span data-stu-id="c74bf-161">The **Address** will automatically populate with the WCF service you created earlier, and the **Namespace** will be set to **ServiceReference1**.</span></span> <span data-ttu-id="c74bf-162">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="c74bf-162">Click **OK**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="c74bf-163">Obě **TestService** a **LocalSTS** musí běžet, když přidáte odkaz na službu do klienta.</span><span class="sxs-lookup"><span data-stu-id="c74bf-163">Both **TestService** and **LocalSTS** must be running when you add the service reference to the client.</span></span>  
  
5. <span data-ttu-id="c74bf-164">Sada Visual Studio vygeneruje třídy proxy pro službu WCF a přidá všechny nezbytné informace odkazu.</span><span class="sxs-lookup"><span data-stu-id="c74bf-164">Visual Studio will generate proxy classes for the WCF service, and add all of the necessary reference information.</span></span> <span data-ttu-id="c74bf-165">Přidá také elementy do *App.config* souborů pro konfiguraci klienta získá token ze služby STS pro ověření ve službě.</span><span class="sxs-lookup"><span data-stu-id="c74bf-165">It will also add elements to the *App.config* file to configure the client to get a token from the STS to authenticate with the service.</span></span> <span data-ttu-id="c74bf-166">Po dokončení tohoto procesu **Program.cs** soubor se otevře.</span><span class="sxs-lookup"><span data-stu-id="c74bf-166">When this process is finished, the **Program.cs** file will open.</span></span> <span data-ttu-id="c74bf-167">Přidat `using` směrnice pro **System.ServiceModel** a druhý pro **Client.ServiceReference1**, nahraďte **hlavní** metodu s následujícím kódem, pak soubor uložte:</span><span class="sxs-lookup"><span data-stu-id="c74bf-167">Add a `using` directive for **System.ServiceModel** and another for **Client.ServiceReference1**, replace the **Main** method with the following code, then save the file:</span></span>  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        // Create the client for the service  
        Service1Client client = new Service1Client();  
        Console.WriteLine("-------------WCF Client Application--------------\n");  
  
        while (!ShouldQuitApplication())  
        {  
            try  
            {  
                Console.WriteLine(client.ComputeResponse("Hello World"));  
            }  
            catch (CommunicationException e)  
            {  
                Console.WriteLine(e.Message);  
                Console.WriteLine(e.StackTrace);  
                Exception ex = e.InnerException;  
                while (ex != null)  
                {  
                    Console.WriteLine("===========================");  
                    Console.WriteLine(ex.Message);  
                    Console.WriteLine(ex.StackTrace);  
                    ex = ex.InnerException;  
                }  
            }  
            catch (TimeoutException)  
            {  
                Console.WriteLine("Timed out...");  
            }  
            catch (Exception e)  
            {  
                Console.WriteLine("An unexpected exception occurred.");  
                Console.WriteLine(e.StackTrace);  
            }  
        }  
  
        client.Close();  
  
        if (client != null)  
        {  
            client.Abort();  
        }  
    }  
  
    static bool ShouldQuitApplication()  
    {  
        Console.WriteLine("---------------------------------------------------------------------");  
        Console.WriteLine("Press Enter key to invoke service, any other key to quit application:");  
        Console.WriteLine("----------------------------------------------------------------------");  
  
        ConsoleKeyInfo keyInfo = Console.ReadKey();  
        if (keyInfo.Key == ConsoleKey.Enter)  
            return false;  
        return true;  
    }  
    ```  
  
6. <span data-ttu-id="c74bf-168">Otevřít *App.config* a přidejte následující kód XML jako první podřízený element pod `<system.serviceModel>` element poté soubor uložte:</span><span class="sxs-lookup"><span data-stu-id="c74bf-168">Open the *App.config* file and add the following XML as the first child element under the `<system.serviceModel>` element, then save the file:</span></span>  
  
    ```xml  
    <behaviors>  
       <endpointBehaviors>  
         <behavior>  
           <clientCredentials>  
             <serviceCertificate>  
               <authentication certificateValidationMode="None"/>  
             </serviceCertificate>  
           </clientCredentials>  
         </behavior>  
       </endpointBehaviors>  
     </behaviors>  
    ```  
  
     <span data-ttu-id="c74bf-169">Tím se zakáže ověřování certifikátu.</span><span class="sxs-lookup"><span data-stu-id="c74bf-169">This disables certificate validation.</span></span>  
  
7. <span data-ttu-id="c74bf-170">Klikněte pravým tlačítkem myši **TestService** řešení a klikněte na kartu **nastavit projekty po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="c74bf-170">Right-click the **TestService** solution and click on **Set StartUp Projects**.</span></span> <span data-ttu-id="c74bf-171">**Spouštěný projekt** otevře se stránka Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c74bf-171">The **Startup Project** property page opens.</span></span> <span data-ttu-id="c74bf-172">V **spouštěný projekt** stránky vlastností, vyberte **více projektů po spuštění** klikněte v **akce** pole pro každý projekt a vyberte **Start** z rozevírací nabídky.</span><span class="sxs-lookup"><span data-stu-id="c74bf-172">In the **Startup Project** property page, select **Multiple startup projects** then click in the **Action** field for each project and select **Start** from the drop-down menu.</span></span> <span data-ttu-id="c74bf-173">Klikněte na tlačítko **OK** uložte nastavení.</span><span class="sxs-lookup"><span data-stu-id="c74bf-173">Click **OK** to save the settings.</span></span>  
  
8. <span data-ttu-id="c74bf-174">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="c74bf-174">Build the solution.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="c74bf-175">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="c74bf-175">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="c74bf-176">V tomto kroku otestujete aplikaci WCF s podporou technologie WIF a ověříte, že jsou předkládány deklarace.</span><span class="sxs-lookup"><span data-stu-id="c74bf-176">In this step you will test your WIF-enabled WCF application and verify that claims are presented.</span></span>  
  
#### <a name="to-test-your-wif-enabled-wcf-application-for-claims"></a><span data-ttu-id="c74bf-177">Otestování deklarací v aplikaci WCF s podporou technologie WIF</span><span class="sxs-lookup"><span data-stu-id="c74bf-177">To test your WIF-enabled WCF application for claims</span></span>  
  
1. <span data-ttu-id="c74bf-178">Stisknutím klávesy **F5** sestavíte a spustíte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c74bf-178">Press **F5** to build and run the application.</span></span> <span data-ttu-id="c74bf-179">Mělo by se zobrazit okno konzoly a následující text: **Stiskněte klávesu Enter, abyste mohli vyvolat službu, libovolné klávesy ukončete aplikaci:**</span><span class="sxs-lookup"><span data-stu-id="c74bf-179">You should be presented with a console window, and the following text: **Press Enter key to invoke service, any other key to quit application:**</span></span>  
  
2. <span data-ttu-id="c74bf-180">Stisknutím klávesy **Enter**, a následující informace o deklaracích by se měla zobrazit v konzole:</span><span class="sxs-lookup"><span data-stu-id="c74bf-180">Press **Enter**, and the following claims information should appear in the console:</span></span>  
  
    ```  
    Computed by Service1  
    Input received from client: Hello World  
    Client Name: Terry  
    IsAuthenticated: True  
    The service received the following issued claims of the client:  
    ClaimType :http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name    ClaimValue:Terry  
    ClaimType :http://schema.xmlsoap.org/ws/2005/05/identity/claims/surname    ClaimValue:Adams  
    ClaimType :http://schemas.microsoft.com/ws/2008/06/identity/claims/role    ClaimValue:developer  
    ClaimType :http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress    ClaimValue:terry@contoso.com  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="c74bf-181">Obě **TestService** a **LocalSTS** musí běžet před stisknutím **Enter**.</span><span class="sxs-lookup"><span data-stu-id="c74bf-181">Both **TestService** and **LocalSTS** must be running before you press **Enter**.</span></span> <span data-ttu-id="c74bf-182">Na webové stránce by se otevřít pro služby a ověřte, zda **LocalSTS** spuštěna v oznamovací oblasti (na hlavním panelu systému).</span><span class="sxs-lookup"><span data-stu-id="c74bf-182">A Web page should open for the service and you can verify that **LocalSTS** is running by looking in the notification area (system tray).</span></span>  
  
3. <span data-ttu-id="c74bf-183">Pokud se v konzole zobrazí tyto deklarace, byli jste úspěšně ověřeni pomocí služby STS pro zobrazení deklarací ze služby WCF.</span><span class="sxs-lookup"><span data-stu-id="c74bf-183">If these claims appear in the console, you have successfully authenticated with the STS to display claims from the WCF service.</span></span>
