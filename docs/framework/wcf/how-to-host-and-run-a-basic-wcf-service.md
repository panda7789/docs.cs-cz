---
title: 'Kurz: Hostování a spuštění základní služby Windows Communication Foundation'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: ad9536b1f27ba3945bf76d0474de4825033a1e8b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197903"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a>Kurz: Hostování a spuštění základní služby Windows Communication Foundation

Tento kurz popisuje třetí pět úloh potřebných k vytvoření základní aplikace Windows Communication Foundation (WCF). Přehled v kurzech, naleznete v tématu [kurzu: Začínáme s aplikacemi Windows Communication Foundation](getting-started-tutorial.md).

Dalším úkolem pro vytvoření aplikace WCF je hostování služby WCF v konzolové aplikaci. Služby WCF zpřístupňuje jeden nebo více *koncové body*, každý z nich vystavuje jednu nebo víc operací služeb. Koncový bod služby určuje následující informace: 
- Adresa, kde najdete službu.
- Vazbu, která obsahuje informace, které popisuje, jak klient musí komunikovat se službou. 
- Kontrakt, který definuje funkci, která poskytuje služby svým klientům.

V tomto kurzu se naučíte:
> [!div class="checklist"]
> - Vytvořte a nakonfigurujte projekt konzolové aplikace pro hostování služby WCF.
> - Přidejte kód pro hostování služby WCF.
> - Aktualizujte konfigurační soubor.
> - Spusťte službu WCF a ověří, že je spuštěná.

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a>Vytvořte a nakonfigurujte projekt konzolové aplikace pro hostování služby

1. Vytvořte projekt konzolové aplikace v sadě Visual Studio: 
 
    1. Z **souboru** nabídce vyberte možnost **otevřít** > **projekt či řešení** a přejděte do **GettingStarted** řešení můžete vytvořené (*GettingStarted.sln*). Vyberte **Open** (Otevřít).

    2. Z **zobrazení** nabídce vyberte možnost **Průzkumníka řešení**.
    
    3. V **Průzkumníka řešení** okna, vyberte **GettingStarted** řešení (nejvyšší uzel) a pak vyberte **přidat** > **nový projekt** z místní nabídky. 

    4. V **přidat nový projekt** na levé straně vyberte okno **Windows Desktop** kategorie v části **Visual C#**  nebo **jazyka Visual Basic**. 

    5. Vyberte **Konzolová aplikace (.NET Framework)** šablony a zadejte *GettingStartedHost* pro **název**. Vyberte **OK**.

2. Přidat odkaz **GettingStartedHost** projektu **GettingStartedLib** projektu: 

    1. V **Průzkumníka řešení** okna, vyberte **odkazy** ve složce **GettingStartedHost** projektu a pak vyberte **přidat odkaz** z místní nabídky. 

    2. V **přidat odkaz** dialogového okna, v části **projekty** v levé části okna vyberte **řešení**. 
 
    3. Vyberte **GettingStartedLib** v System center části okna a pak vyberte **OK**. 

       Tato akce vytvoří typy definované v **GettingStartedLib** projektu, které jsou k dispozici na **GettingStartedHost** projektu.

3. Přidat odkaz **GettingStartedHost** projektu <xref:System.ServiceModel> sestavení: 

    1. V **Průzkumníka řešení** okna, vyberte **odkazy** ve složce **GettingStartedHost** projektu a pak vyberte **přidat odkaz** z místní nabídky.
    
    2. V **přidat odkaz** okně v části **sestavení** v levé části okna vyberte **Framework**. 

    3. Vyberte **System.ServiceModel**a pak vyberte **OK**. 
    
    4. Uložte řešení tak, že vyberete **souboru** > **Uložit vše**.

## <a name="add-code-to-host-the-service"></a>Přidejte kód pro hostování služby

K hostování služby, přidejte kód proveďte následující kroky: 
   1. Vytvořte identifikátor URI pro základní adresu.
   2. Vytvoření instance třídy, pro který je hostitelem služby.
   3. Vytvoření koncového bodu služby.
   4. Povolte výměny metadat.
   5. Otevření hostitele služby k naslouchání pro příchozí zprávy.
  
Proveďte následující změny kódu:

1. Otevřít **Program.cs** nebo **Module1.vb** soubor **GettingStartedHost** projektu a nahraďte jeho kód následujícím kódem:

    ```csharp
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Description;
    using GettingStartedLib;

    namespace GettingStartedHost
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Step 1: Create a URI to serve as the base address.
                Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");

                // Step 2: Create a ServiceHost instance.
                ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);

                try
                {
                    // Step 3: Add a service endpoint.
                    selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");

                    // Step 4: Enable metadata exchange.
                    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
                    smb.HttpGetEnabled = true;
                    selfHost.Description.Behaviors.Add(smb)    ;

                    // Step 5: Start the service.
                    selfHost.Open();
                    Console.WriteLine("The service is ready.");

                    // Close the ServiceHost to stop the service.
                    Console.WriteLine("Press <Enter> to terminate the service.");
                    Console.WriteLine();
                    Console.ReadLine();
                    selfHost.Close();
                }
                catch (CommunicationException ce)
                {
                    Console.WriteLine("An exception occurred: {0}", ce.Message);
                    selfHost.Abort();
                }
            }
        }
    }
    ```

    ```vb
    Imports System.ServiceModel
    Imports System.ServiceModel.Description
    Imports GettingStartedLib.GettingStartedLib

    Module Service

        Class Program
            Shared Sub Main()
                ' Step 1: Create a URI to serve as the base address.
                Dim baseAddress As New Uri("http://localhost:8000/GettingStarted/")

                ' Step 2: Create a ServiceHost instance.
                Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)
               Try

                    ' Step 3: Add a service endpoint.
                    selfHost.AddServiceEndpoint( _
                        GetType(ICalculator), _
                        New WSHttpBinding(), _
                        "CalculatorService")

                    ' Step 4: Enable metadata exchange.
                    Dim smb As New ServiceMetadataBehavior()
                    smb.HttpGetEnabled = True
                    selfHost.Description.Behaviors.Add(smb)

                    ' Step 5: Start the service.
                    selfHost.Open()
                    Console.WriteLine("The service is ready.")

                    ' Close the ServiceHost to stop the service.
                    Console.WriteLine("Press <Enter> to terminate the service.")
                    Console.WriteLine()
                    Console.ReadLine()
                    selfHost.Close()

                Catch ce As CommunicationException
                    Console.WriteLine("An exception occurred: {0}", ce.Message)
                    selfHost.Abort()
                End Try
            End Sub
        End Class

    End Module
    ```
    
    Informace o tom, jak tento kód funguje, najdete v tématu [služby hostování program kroky](#service-hosting-program-steps).

2. Aktualizace vlastností projektu:

   1. V **Průzkumníka řešení** okna, vyberte **GettingStartedHost** složku a pak vyberte **vlastnosti** z místní nabídky.

   2. Na **GettingStartedHost** stránku vlastností, vyberte **aplikace** kartu:

      - Pro C# projektů, vyberte **GettingStartedHost.Program** z **spouštěcí objekt** seznamu.

      - Pro projekty jazyka Visual Basic, vyberte **Service.Program** z **spouštěcí objekt** seznamu.

   3. Z **souboru** nabídce vyberte možnost **Uložit vše**.

## <a name="verify-the-service-is-working"></a>Ověřte, že služba funguje

1. Sestavte řešení a pak spusťte **GettingStartedHost** konzoly z aplikace v sadě Visual Studio. 

    Služba musí běžet s oprávněními správce. Protože jste spustili sady Visual Studio s oprávněními správce, když spustíte **GettingStartedHost** v sadě Visual Studio, při spuštění aplikace se také oprávnění správce. Alternativně můžete otevřít nový příkazový řádek jako správce (vyberte **Další** > **spustit jako správce** z místní nabídky) a spusťte **GettingStartedHost.exe**  v něm.

2. Otevřete webový prohlížeč a přejděte na stránku služby na `http://localhost:8000/GettingStarted/CalculatorService`.
   
   > [!NOTE]
   > Služby, jako je ten vyžadují správné oprávnění k registraci adresami protokolu HTTP na počítači pro naslouchání. Účty správců mají toto oprávnění, ale účty bez oprávnění správce musí být uděleno oprávnění pro obory názvů HTTP. Další informace o tom, jak konfigurace rezervace oboru názvů najdete v tématu [konfigurace HTTP a HTTPS](feature-details/configuring-http-and-https.md). 

## <a name="service-hosting-program-steps"></a>Služby hostování program kroky

Kroky v kódu, který jste přidali do hostitele služby jsou popsány v následujícím způsobem:

- **Krok 1**: Vytvoření instance `Uri` třídy pro uložení základní adresu služby. Adresa URL, která obsahuje základní adresa má volitelný identifikátor URI, který identifikuje službu. Základní adresa naformátován takto: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`. Základní adresa pro službu kalkulačky používá přenos pomocí protokolu HTTP, místního hostitele, port 8000 a segment identifikátoru URI GettingStarted.

- **Krok 2**: Vytvoření instance <xref:System.ServiceModel.ServiceHost> třídy, který použijete k hostování služby. Konstruktor používá dva parametry: typ třídy, která implementuje kontrakt služby a základní adresu služby.

- **Krok 3**: Vytvoření <xref:System.ServiceModel.Description.ServiceEndpoint> instance. Koncový bod služby se skládá z adresy, vazby a smlouvy o poskytování služeb. <xref:System.ServiceModel.Description.ServiceEndpoint> Konstruktoru se skládá z typu rozhraní kontraktu služby, vazbu a adresu. Kontrakt služby je `ICalculator`, která definované a implementaci v typu služby. Vazba pro tuto ukázku je <xref:System.ServiceModel.WSHttpBinding>, které jsou integrované vazby a připojení ke koncovým bodům, které odpovídají WS-* specifikace. Další informace o vazbách WCF najdete v tématu [vazby WCF – přehled](bindings-overview.md). Adresa se připojí k základní adresu, abyste identifikovali koncový bod. Kód určuje adresu jako CalculatorService a plně kvalifikovanou adresu pro koncový bod jako `http://localhost:8000/GettingStarted/CalculatorService`.

    > [!IMPORTANT]
    > Pro rozhraní .NET Framework verze 4 a novější přidává se koncový bod služby je volitelný. Pro tyto verze pokud nepřidáte kódu nebo konfigurace WCF přidá jeden výchozí koncový bod pro každou kombinaci základní adresu a kontraktů implementovaných službou. Další informace o výchozí koncové body, naleznete v tématu [zadání adresy koncového bodu](specifying-an-endpoint-address.md). Další informace o výchozí koncové body, vazby a chování najdete v tématu [zjednodušené konfigurace](simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](samples/simplified-configuration-for-wcf-services.md).

- **Krok 4**: Povolte výměny metadat. Klienti používají ke generování proxy serverů k volání operací služby výměny metadat. Povolit výměny metadat, vytvořte <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, nastavte jeho <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> vlastnost `true`a přidejte `ServiceMetadataBehavior` objektu <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekce <xref:System.ServiceModel.ServiceHost> instance.

- **Krok 5**: Otevřít <xref:System.ServiceModel.ServiceHost> k naslouchání pro příchozí zprávy. Aplikace čeká, až stisknete **Enter**. Jakmile aplikace vytvoří instanci <xref:System.ServiceModel.ServiceHost>, provede blok try/catch. Další informace o bezpečně zachycování výjimek vyvolaných <xref:System.ServiceModel.ServiceHost>, naleznete v tématu [použití zavřít a Abort k uvolnění prostředků klienta WCF](samples/use-close-abort-release-wcf-client-resources.md).

> [!IMPORTANT]
> Když přidáte knihovny služby WCF, Visual Studio hostuje za vás při ladění pomocí spuštění hostitele služby. Aby nedocházelo ke konfliktům, můžete zabránit sady Visual Studio hostování knihovny služby WCF. 
> 1. Vyberte **GettingStartedLib** projekt **Průzkumníka řešení** a zvolte **vlastnosti** z místní nabídky.
> 2. Vyberte **možnosti WCF** a zrušte zaškrtnutí políčka **spuštění hostitele služby WCF při ladění jiného projektu ve stejném řešení**.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
> - Vytvořte a nakonfigurujte projekt konzolové aplikace pro hostování služby WCF.
> - Přidejte kód pro hostování služby WCF.
> - Aktualizujte konfigurační soubor.
> - Spusťte službu WCF a ověří, že je spuštěná.

Přejděte k dalšímu kurzu se naučíte, jak vytvořit klienta WCF.

> [!div class="nextstepaction"]
> [Kurz: Vytvořte klienta WCF](how-to-create-a-wcf-client.md)
