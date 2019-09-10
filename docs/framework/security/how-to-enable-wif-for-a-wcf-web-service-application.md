---
title: 'Postupy: Povolení WIF pro aplikaci webové služby WCF'
ms.date: 03/30/2017
ms.assetid: bfc64b3d-64e9-4093-a6a4-72e933917af7
author: BrucePerlerMS
ms.openlocfilehash: 809009642caf743f4f067591adfa63ccb154a577
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851530"
---
# <a name="how-to-enable-wif-for-a-wcf-web-service-application"></a>Postupy: Povolení WIF pro aplikaci webové služby WCF
## <a name="applies-to"></a>Platí pro

- Microsoft® Windows® Identity Foundation (WIF)

- Microsoft® Windows® Communication Foundation (WCF)

## <a name="summary"></a>Souhrn

Tento návod podrobně popisuje postupy pro povolení technologie WIF ve webové službě WCF. Obsahuje také pokyny, jak pomocí otestování aplikace ověřit, zda webová služba po spuštění aplikace správně předkládá deklarace. Tento návod neobsahuje podrobné pokyny pro vytvoření služby tokenů zabezpečení (STS) a namísto toho používá službu STS určenou pro vývoj, která je součástí instalace nástroje Identity and Access Tool. Služba STS pro vývoj neprovádí skutečné ověřování a je určena pouze pro testovací účely. Abyste mohli dokončit postupy v tomto návodu, je třeba nainstalovat nástroj Identity and Access Tool. Dá se stáhnout z následujícího umístění: [Nástroj identity and Access](https://go.microsoft.com/fwlink/?LinkID=245849)

## <a name="contents"></a>Obsah

- Cíle

- Přehled

- Přehled kroků

- Krok 1 – Vytvoření jednoduché služby WCF

- Krok 2 – Vytvoření klientské aplikace pro službu WCF

- Krok 3 – Otestování řešení

## <a name="objectives"></a>Cíle

- Vytvořte službu WCF, která vyžaduje vydané tokeny.

- Vytvořte klienta WCF, který si vyžádá token od služby STS a předá jej službě WCF.

## <a name="overview"></a>Přehled

Cílem tohoto návodu je ukázat, jak mohou vývojáři používat federované ověřování při vývoji služeb WCF. Mezi výhody použití federace ve službách WCF patří:

1. Přesunutí logiky ověřování mimo kód služby WCF

2. Opětovné využití stávajících řešení pro správu identit

3. Vzájemná funkční spolupráce s jinými řešeními pro správu identit

4. Flexibilita a odolnost vůči budoucím změnám

Technologie WIF a související nástroj Identity and Access Tool usnadňují vývoj a testování služeb WCF pomocí federovaného ověřování, jak ukazují následující kroky.

## <a name="summary-of-steps"></a>Přehled kroků

- Krok 1 – Vytvoření jednoduché služby WCF

- Krok 2 – Vytvoření klientské aplikace pro službu WCF

- Krok 3 – Otestování řešení

## <a name="step-1--create-a-simple-wcf-service"></a>Krok 1 – Vytvoření jednoduché služby WCF

V tomto kroku vytvoříte novou službu WCF používající službu STS pro vývoj, která je součástí nástroje Identity and Access Tool.

#### <a name="to-create-a-simple-wcf-service"></a>Vytvoření jednoduché služby WCF

1. Spusťte sadu Visual Studio jako správce v režimu se zvýšenými oprávněními.

2. V aplikaci Visual Studio klikněte na možnost **soubor**, klikněte na možnost **Nový**a poté klikněte na možnost **projekt**.

3. V okně **Nový projekt** klikněte na položku **aplikace služby WCF**.

4. Do **název**zadejte `TestService` a stiskněte **OK**.

5. V části **Průzkumník řešení**klikněte pravým tlačítkem na projekt **TestService** a pak vyberte **Identita a přístup**.

6. Zobrazí se okno **Identita a přístup** . V části **poskytovatelé**vyberte **test aplikace pomocí místní služby tokenů pro vývoj**a pak klikněte na **použít**. Nástroj identity and Access nakonfiguruje službu tak, aby používala WIF, a k místnímu ověřování STS (**LocalSTS**), a to přidáním elementů konfigurace do souboru *Web. config* .

7. V souboru *Service1.svc.cs* přidejte `using` direktivu pro obor názvů **System. Security. Claims** a nahraďte stávající kód následujícím kódem a poté soubor uložte:

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

    Metoda zobrazí vlastnosti různých deklarací identity vydaných nástrojem LocalSTS. `ComputeResponse`

8. V souboru *IService1.cs* nahraďte existující kód následujícím kódem a poté soubor uložte:

    ```csharp
    [ServiceContract]
    public interface IService1
    {
        [OperationContract]
        string ComputeResponse(string input);
    }
    ```

9. Sestavte projekt.

10. Stisknutím **kombinace kláves CTRL + F5** službu spusťte bez spuštění ladicího programu. Webová stránka by měla být otevřená pro službu a můžete ověřit, že je **LocalSTS** spuštěná, a to tak, že se vyhledají v oznamovací oblasti (hlavní panel systému).

    > [!IMPORTANT]
    > **TestService** i **LocalSTS** musí být spuštěny při přidání odkazu na službu do klientské aplikace v dalším kroku.

## <a name="step-2--create-a-client-application-for-the-wcf-service"></a>Krok 2 – Vytvoření klientské aplikace pro službu WCF

V tomto kroku vytvoříte konzolovou aplikaci, která se pomocí služby STS pro vývoj ověřuje ve službě WCF vytvořené v předchozím kroku.

#### <a name="to-create-a-client-application"></a>Vytvoření klientské aplikace

1. V aplikaci Visual Studio klikněte pravým tlačítkem myši na řešení, klikněte na tlačítko **Přidat**a poté klikněte na možnost **Nový projekt**.

2. V okně **Přidat nový projekt** vyberte v seznamu šablony **vizuálu C#**  položku **Konzolová aplikace** , zadejte `Client`a potom stiskněte **OK**. Vytvoří se nový projekt ve složce řešení.

3. Klikněte pravým tlačítkem na **odkazy** v rámci projektu **klienta** a pak klikněte na **Přidat odkaz na službu**.

4. V okně **Přidat odkaz na službu** klikněte na šipku rozevíracího seznamu na tlačítku **Vyhledat** a klikněte na **služby v řešení**. **Adresa** bude automaticky naplněna službou WCF, kterou jste vytvořili dříve, a **obor názvů** bude nastaven na **ServiceReference1**. Klikněte na **OK**.

    > [!IMPORTANT]
    > **TestService** i **LocalSTS** musí být spuštěny, když přidáte odkaz na službu do klienta.

5. Sada Visual Studio vygeneruje třídy proxy pro službu WCF a přidá všechny nezbytné informace odkazu. Přidá také prvky do souboru *App. config* ke konfiguraci klienta, aby získal token od služby STS, který bude moci ověřit pomocí služby. Po dokončení tohoto procesu se otevře soubor **program.cs** . Přidejte direktivu pro **System. ServiceModel** a jinou pro **Client. ServiceReference1**, nahraďte metodu Main následujícím kódem a pak soubor uložte: `using`

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

6. Otevřete soubor *App. config* a přidejte následující kód XML jako první podřízený prvek pod `<system.serviceModel>` prvkem a pak soubor uložte:

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

7. Klikněte pravým tlačítkem na řešení **TestService** a klikněte na **nastavit projekty po spuštění**. Otevře se stránka vlastností **projektu po spuštění** . Na stránce vlastnost **projektu po spuštění** vyberte **více projektů po spuštění** a potom klikněte v poli **Akce** pro každý projekt a v rozevírací nabídce vyberte možnost **Spustit** . Nastavení uložíte kliknutím na **OK** .

8. Sestavte řešení.

## <a name="step-3--test-your-solution"></a>Krok 3 – Otestování řešení

V tomto kroku otestujete aplikaci WCF s podporou technologie WIF a ověříte, že jsou předkládány deklarace.

#### <a name="to-test-your-wif-enabled-wcf-application-for-claims"></a>Otestování deklarací v aplikaci WCF s podporou technologie WIF

1. Stisknutím klávesy **F5** Sestavte a spusťte aplikaci. Měli byste se prezentovat oknem konzoly a následujícím textem: **Stiskněte klávesu ENTER pro vyvolání služby, jakýkoli další klíč k ukončení aplikace:**

2. Stiskněte klávesu **ENTER**a v konzole nástroje by se měly zobrazit následující informace o deklaracích:

    ```output
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
    > Před stiskem klávesy **ENTER**musí být spuštěny obě **TestService** i **LocalSTS** . Webová stránka by měla být otevřená pro službu a můžete ověřit, že je **LocalSTS** spuštěná, a to tak, že se vyhledají v oznamovací oblasti (hlavní panel systému).

3. Pokud se v konzole zobrazí tyto deklarace, byli jste úspěšně ověřeni pomocí služby STS pro zobrazení deklarací ze služby WCF.
