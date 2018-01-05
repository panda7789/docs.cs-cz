---
title: "Postupy: Povolení WIF pro webovou aplikaci služby WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bfc64b3d-64e9-4093-a6a4-72e933917af7
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 1af6fc1b7802fe69f0585011322e2485695a030c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-wif-for-a-wcf-web-service-application"></a>Postupy: Povolení WIF pro webovou aplikaci služby WCF
## <a name="applies-to"></a>Platí pro  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   Microsoft® Windows® Communication Foundation (WCF)  
  
## <a name="summary"></a>Souhrn  
 Tento návod podrobně popisuje postupy pro povolení technologie WIF ve webové službě WCF. Obsahuje také pokyny, jak pomocí otestování aplikace ověřit, zda webová služba po spuštění aplikace správně předkládá deklarace. Tento návod neobsahuje podrobné pokyny pro vytvoření služby tokenů zabezpečení (STS) a namísto toho používá službu STS určenou pro vývoj, která je součástí instalace nástroje Identity and Access Tool. Služba STS pro vývoj neprovádí skutečné ověřování a je určena pouze pro testovací účely. Abyste mohli dokončit postupy v tomto návodu, je třeba nainstalovat nástroj Identity and Access Tool. Ho můžete stáhnout z následujícího umístění: [identita a přístup](http://go.microsoft.com/fwlink/?LinkID=245849)  
  
## <a name="contents"></a>Obsah  
  
-   Cíle  
  
-   Přehled  
  
-   Přehled kroků  
  
-   Krok 1 – Vytvoření jednoduché služby WCF  
  
-   Krok 2 – Vytvoření klientské aplikace pro službu WCF  
  
-   Krok 3 – Otestování řešení  
  
## <a name="objectives"></a>Cíle  
  
-   Vytvořte službu WCF, která vyžaduje vydané tokeny.  
  
-   Vytvořte klienta WCF, který si vyžádá token od služby STS a předá jej službě WCF.  
  
## <a name="overview"></a>Přehled  
 Cílem tohoto návodu je ukázat, jak mohou vývojáři používat federované ověřování při vývoji služeb WCF. Mezi výhody použití federace ve službách WCF patří:  
  
1.  Přesunutí logiky ověřování mimo kód služby WCF  
  
2.  Opětovné využití stávajících řešení pro správu identit  
  
3.  Vzájemná funkční spolupráce s jinými řešeními pro správu identit  
  
4.  Flexibilita a odolnost vůči budoucím změnám  
  
 Technologie WIF a související nástroj Identity and Access Tool usnadňují vývoj a testování služeb WCF pomocí federovaného ověřování, jak ukazují následující kroky.  
  
## <a name="summary-of-steps"></a>Přehled kroků  
  
-   Krok 1 – Vytvoření jednoduché služby WCF  
  
-   Krok 2 – Vytvoření klientské aplikace pro službu WCF  
  
-   Krok 3 – Otestování řešení  
  
## <a name="step-1--create-a-simple-wcf-service"></a>Krok 1 – Vytvoření jednoduché služby WCF  
 V tomto kroku vytvoříte novou službu WCF používající službu STS pro vývoj, která je součástí nástroje Identity and Access Tool.  
  
#### <a name="to-create-a-simple-wcf-service"></a>Vytvoření jednoduché služby WCF  
  
1.  Spusťte sadu Visual Studio jako správce v režimu se zvýšenými oprávněními.  
  
2.  V sadě Visual Studio, klikněte na tlačítko **soubor**, klikněte na tlačítko **nový**a potom klikněte na **projektu**.  
  
3.  V **nový projekt** okně klikněte na tlačítko **aplikace služby WCF**.  
  
4.  V **název**, zadejte `TestService` a stiskněte klávesu **OK**.  
  
5.  Klikněte pravým tlačítkem myši **TestService** projektu v části **Průzkumníku řešení**, pak vyberte **identit a přístupu**.  
  
6.  **Identit a přístupu** se zobrazí v okně. V části **zprostředkovatelé**, vyberte **testování vaší aplikace pomocí místní služby tokenů zabezpečení vývoj**, pak klikněte na tlačítko **použít**. Identita a přístup Konfiguruje službu technologii WIF používají a externí ověřování pro místní vývoj služby tokenů zabezpečení (**LocalSTS**) přidáním konfigurace – elementy do *Web.config* souboru.  
  
7.  V *Service1.svc.cs* soubor, přidejte `using` direktivy pro **System.Security.Claims** obor názvů a nahraďte existující kód následující, pak soubor uložte:  
  
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
  
     `ComputeResponse` Metoda zobrazí vlastnosti různé deklarace identity, které jsou vydány **LocalSTS**.  
  
8.  V *IService1.cs* souboru, nahraďte existující kód následující a pak soubor uložte:  
  
    ```csharp  
    [ServiceContract]  
    public interface IService1  
    {  
        [OperationContract]  
        string ComputeResponse(string input);  
    }  
    ```  
  
9. Sestavte projekt.  
  
10. Stiskněte klávesu **Ctrl + F5** ke spouštění služby bez spuštění ladicího programu. Na webové stránce by měla otevřít služby a ověřte, že **LocalSTS** se službou a vyhledávání v oznamovací oblasti (hlavní panel).  
  
    > [!IMPORTANT]
    >  Obě **TestService** a **LocalSTS** musí být spuštěna, když přidáte odkaz na službu do klientské aplikace v dalším kroku.  
  
## <a name="step-2--create-a-client-application-for-the-wcf-service"></a>Krok 2 – Vytvoření klientské aplikace pro službu WCF  
 V tomto kroku vytvoříte konzolovou aplikaci, která se pomocí služby STS pro vývoj ověřuje ve službě WCF vytvořené v předchozím kroku.  
  
#### <a name="to-create-a-client-application"></a>Vytvoření klientské aplikace  
  
1.  V sadě Visual Studio, klikněte pravým tlačítkem na řešení, klikněte na tlačítko **přidat**a potom klikněte na **nový projekt**.  
  
2.  V **přidat nový projekt** vyberte **konzolové aplikace** z **Visual C#** šablony seznamu, zadejte `Client`a potom stiskněte klávesu **OK**. Vytvoří se nový projekt ve složce řešení.  
  
3.  Klikněte pravým tlačítkem na **odkazy** pod **klienta** projektu a pak klikněte na **přidat odkaz na službu**.  
  
4.  V **přidat odkaz na službu** okně klikněte na šipku rozevíracího seznamu **Discover** tlačítko a klikněte na tlačítko **služby v řešení**. **Adresu** bude automaticky naplnit u služby WCF, který jste vytvořili dříve, a **Namespace** bude nastavena pro **ServiceReference1**. Click **OK**.  
  
    > [!IMPORTANT]
    >  Obě **TestService** a **LocalSTS** musí být spuštěna, když přidáte odkaz na službu do klienta.  
  
5.  Sada Visual Studio vygeneruje třídy proxy pro službu WCF a přidá všechny nezbytné informace odkazu. Také přidá elementy, aby *App.config* soubor konfigurace klienta se získat token ze služby tokenů zabezpečení k ověření u služby. Po dokončení tohoto procesu **Program.cs** soubor se otevře. Přidat `using` direktivy pro **System.ServiceModel** a druhý pro **Client.ServiceReference1**, nahraďte **hlavní** následujícím kódem, pak – metoda uložení souboru:  
  
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
  
6.  Otevřete *App.config* souboru a přidejte následující kód XML jako první podřízený prvek v rámci `<system.serviceModel>` elementu, pak uložte soubor:  
  
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
  
     Tím se zakáže ověřování certifikátu.  
  
7.  Klikněte pravým tlačítkem myši **TestService** řešení a klikněte na **nastavit projekty po spuštění**. **Spouštěný projekt** otevře se stránka vlastností. V **spouštěný projekt** stránka vlastností, vyberte **více projektů po spuštění** klikněte v **akce** pole pro každý projekt a vyberte **spustit** z rozevírací nabídky. Klikněte na tlačítko **OK** uložte nastavení.  
  
8.  Sestavte řešení.  
  
## <a name="step-3--test-your-solution"></a>Krok 3 – Otestování řešení  
 V tomto kroku otestujete aplikaci WCF s podporou technologie WIF a ověříte, že jsou předkládány deklarace.  
  
#### <a name="to-test-your-wif-enabled-wcf-application-for-claims"></a>Otestování deklarací v aplikaci WCF s podporou technologie WIF  
  
1.  Stiskněte klávesu **F5** sestavení a spuštění aplikace. By se měla zobrazit okno konzoly a následující text: **stiskněte klávesu Enter klíč k vyvolání služby, další klíč ukončete aplikaci:**  
  
2.  Stiskněte klávesu **Enter**, a následující deklarace identity informace by měly zobrazovat v konzole:  
  
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
    >  Obě **TestService** a **LocalSTS** musí být spuštěna před stisknutím klávesy **Enter**. Na webové stránce by měla otevřít služby a ověřte, že **LocalSTS** se službou a vyhledávání v oznamovací oblasti (hlavní panel).  
  
3.  Pokud se v konzole zobrazí tyto deklarace, byli jste úspěšně ověřeni pomocí služby STS pro zobrazení deklarací ze služby WCF.
