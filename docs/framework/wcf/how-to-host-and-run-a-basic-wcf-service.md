---
title: 'Kurz: Hostování a spuštění služby Windows Communication Foundation Basic'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 984c5e73a8efc4e9c2d487485267868ffa2f60f3
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928715"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a>Kurz: Hostování a spuštění služby Windows Communication Foundation Basic

Tento kurz popisuje třetí z pěti úloh potřebných k vytvoření aplikace Basic Windows Communication Foundation (WCF). Přehled kurzů najdete v tématu [kurz: Začněte s Windows Communication Foundation aplikacemi](getting-started-tutorial.md).

Další úlohou pro vytvoření aplikace WCF je hostování služby WCF v konzolové aplikaci. Služba WCF zveřejňuje jeden nebo více *koncových bodů*, z nichž každý zveřejňuje jednu nebo více operací služby. Koncový bod služby určuje následující informace:

- Adresa, kde můžete najít službu.
- Vazba obsahující informace, které popisují, jak klient musí komunikovat se službou. 
- Kontrakt definující funkce, které služba poskytuje svým klientům.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> - Vytvořte a nakonfigurujte projekt konzolové aplikace pro hostování služby WCF.
> - Přidejte kód pro hostování služby WCF.
> - Aktualizujte konfigurační soubor.
> - Spusťte službu WCF a ověřte, zda je spuštěná.

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a>Vytvoření a konfigurace projektu konzolové aplikace pro hostování služby

1. Vytvoření projektu konzolové aplikace v aplikaci Visual Studio: 
 
    1. V nabídce **soubor** vyberte **otevřít** > **projekt/řešení** a přejděte k **soubor GettingStarted** řešení, které jste dříve vytvořili (*soubor GettingStarted. sln*). Vyberte **Open** (Otevřít).

    2. V nabídce **zobrazení** vyberte **Průzkumník řešení**.
    
    3. V okně **Průzkumník řešení** vyberte řešení **soubor GettingStarted** (nejvyšší uzel) a pak v místní nabídce vyberte **Přidat** > **Nový projekt** . 

    4. V okně **Přidat nový projekt** na levé straně vyberte kategorii **Desktop systému Windows** pod položkou  **C# Visual** nebo **Visual Basic**. 

    5. Vyberte šablonu **Konzolová aplikace (.NET Framework)** a jako **název**zadejte *GettingStartedHost* . Vyberte **OK**.

2. Přidejte odkaz do projektu **GettingStartedHost** do projektu **GettingStartedLib** : 

    1. V okně **Průzkumník řešení** vyberte složku **odkazy** v projektu **GettingStartedHost** a pak vyberte **Přidat odkaz** z místní nabídky. 

    2. V dialogovém okně **Přidat odkaz** vyberte v části **projekty** na levé straně okna možnost **řešení**. 
 
    3. V okně střední části okna vyberte **GettingStartedLib** a pak vyberte **OK**. 

       Tato akce zpřístupňuje typy definované v projektu **GettingStartedLib** k projektu **GettingStartedHost** .

3. Přidejte odkaz do projektu **GettingStartedHost** do <xref:System.ServiceModel> sestavení: 

    1. V okně **Průzkumník řešení** vyberte složku **odkazy** v projektu **GettingStartedHost** a pak vyberte **Přidat odkaz** z místní nabídky.
    
    2. V okně **Přidat odkaz** v části **sestavení** na levé straně okna vyberte možnost **Architektura**. 

    3. Vyberte **System. ServiceModel**a pak vyberte **OK**. 
    
    4. Uložte řešení tak, že vyberete **soubor** > **Uložit vše**.

## <a name="add-code-to-host-the-service"></a>Přidat kód pro hostování služby

Chcete-li hostovat službu, přidejte kód, který provede následující kroky: 

1. Vytvořte identifikátor URI pro základní adresu.
2. Vytvořte instanci třídy pro hostování služby.
3. Vytvořte koncový bod služby.
4. Povolte výměnu metadat.
5. Otevřete hostitele služby pro příjem příchozích zpráv.
  
Proveďte následující změny kódu:

1. Otevřete soubor **program.cs** nebo **Module1. vb** v projektu **GettingStartedHost** a nahraďte jeho kód následujícím kódem:

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
    
    Informace o tom, jak tento kód funguje, najdete v tématu věnovaném [postupům hostujícím programům](#service-hosting-program-steps).

2. Aktualizujte vlastnosti projektu:

   1. V okně **Průzkumník řešení** vyberte složku **GettingStartedHost** a potom v místní nabídce vyberte možnost **vlastnosti** .

   2. Na stránce vlastnosti **GettingStartedHost** vyberte kartu **aplikace** :

      - V C# části projekty vyberte **GettingStartedHost. program** ze seznamu **spouštěcích objektů** .

      - U Visual Basic projektů vyberte ze seznamu **spouštěcí objekt** položku **Service. program** .

   3. V nabídce **soubor** vyberte **Uložit vše**.

## <a name="verify-the-service-is-working"></a>Ověření funkčnosti služby

1. Sestavte řešení a potom spusťte konzolovou aplikaci **GettingStartedHost** ze sady Visual Studio. 

    Služba musí být spuštěná s oprávněními správce. Vzhledem k tomu, že jste otevřeli aplikaci Visual Studio s oprávněními správce, při spuštění **GettingStartedHost** v aplikaci Visual Studio se aplikace spouští také s oprávněními správce. Jako alternativu můžete otevřít nový příkazový řádek jako správce (v místní nabídce vyberte **Další** > **Spustit jako správce** ) a v něm spustit **GettingStartedHost. exe** .

2. Otevřete webový prohlížeč a přejděte na stránku služby na adrese `http://localhost:8000/GettingStarted/CalculatorService`.
   
   > [!NOTE]
   > Služby, jako je tato jedna, vyžadují správné oprávnění k registraci adres HTTP na počítači pro naslouchání. Účty správců mají toto oprávnění, ale účty bez oprávnění správce musí mít udělené oprávnění pro obory názvů HTTP. Další informace o tom, jak nakonfigurovat rezervace oboru názvů, najdete v tématu [Konfigurace HTTP a HTTPS](feature-details/configuring-http-and-https.md). 

## <a name="service-hosting-program-steps"></a>Kroky hostujícího programu služby

Kroky v kódu, který jste přidali k hostování služby, jsou popsány takto:

- **Krok 1**: Vytvořte instanci `Uri` třídy, která bude uchovávat základní adresu služby. Adresa URL, která obsahuje základní adresu, má volitelný identifikátor URI, který identifikuje službu. Základní adresa je formátována takto: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`. Základní adresa služby kalkulačky používá přenos HTTP, localhost, port 8000 a segment identifikátoru URI soubor GettingStarted.

- **Krok 2**: Vytvořte instanci <xref:System.ServiceModel.ServiceHost> třídy, kterou použijete k hostování služby. Konstruktor přijímá dva parametry: typ třídy, která implementuje kontrakt služby a základní adresu služby.

- **Krok 3**: <xref:System.ServiceModel.Description.ServiceEndpoint> Vytvořte instanci. Koncový bod služby se skládá z adresy, vazby a kontraktu služby. <xref:System.ServiceModel.Description.ServiceEndpoint> Konstruktor se skládá z typu rozhraní kontraktu služby, vazby a adresy. Kontrakt služby je `ICalculator`, který jste definovali a implementovali v typu služby. Vazba pro tuto ukázku je <xref:System.ServiceModel.WSHttpBinding>, což je integrovaná vazba a připojuje se k koncovým bodům, které odpovídají specifikacím WS-*. Další informace o vazbách WCF najdete v tématu [Přehled vazeb WCF](bindings-overview.md). K identifikaci koncového bodu připojíte adresu k základní adrese. Kód určuje adresu jako CalculatorService a plně kvalifikovanou adresu koncového bodu jako `http://localhost:8000/GettingStarted/CalculatorService`.

    > [!IMPORTANT]
    > Pro .NET Framework verze 4 a novější je přidání koncového bodu služby volitelné. Pro tyto verze, pokud nepřidáte kód nebo konfiguraci, WCF přidá jeden výchozí koncový bod pro každou kombinaci základní adresy a smlouvy implementované službou. Další informace o výchozích koncových bodech najdete v tématu [určení adresy koncového bodu](specifying-an-endpoint-address.md). Další informace o výchozích koncových bodech, vazbách a chování najdete v tématu [zjednodušená konfigurace](simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](samples/simplified-configuration-for-wcf-services.md).

- **Krok 4**: Povolte výměnu metadat. Klienti používají výměnu metadat k vygenerování proxy serverů pro volání operací služby. Chcete-li povolit výměnu metadat, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> vytvořte instanci, nastavte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> její vlastnost `true` `ServiceMetadataBehavior` na a <xref:System.ServiceModel.ServiceHost> přidejte objekt do <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekce instance.

- **Krok 5**: Otevřete <xref:System.ServiceModel.ServiceHost> pro příjem příchozích zpráv. Aplikace čeká na stisknutí klávesy **ENTER**. Po vytvoření instance <xref:System.ServiceModel.ServiceHost>aplikace se spustí blok try/catch. Další informace o bezpečném zachycení výjimek vyvolaných <xref:System.ServiceModel.ServiceHost>naleznete v tématu [použití funkcí zavřít a přerušit k vydání prostředků klienta WCF](samples/use-close-abort-release-wcf-client-resources.md).

> [!IMPORTANT]
> Když přidáte knihovnu služby WCF, Visual Studio ji hostuje za vás, pokud ji ladíte spuštěním hostitele služby. Aby nedocházelo ke konfliktům, můžete aplikaci Visual Studio zabránit v hostování knihovny služby WCF. 
>
> 1. V **Průzkumník řešení** vyberte projekt **GettingStartedLib** a v místní nabídce vyberte **vlastnosti** .
> 2. Vyberte **možnost WCF možnosti** a zrušte zaškrtnutí políčka **spustit hostitele služby WCF při ladění jiného projektu ve stejném řešení**.

## <a name="next-steps"></a>Další postup

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> - Vytvořte a nakonfigurujte projekt konzolové aplikace pro hostování služby WCF.
> - Přidejte kód pro hostování služby WCF.
> - Aktualizujte konfigurační soubor.
> - Spusťte službu WCF a ověřte, zda je spuštěná.

Přejděte k dalšímu kurzu, kde se dozvíte, jak vytvořit klienta WCF.

> [!div class="nextstepaction"]
> [Kurz: Vytvoření klienta WCF](how-to-create-a-wcf-client.md)
