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
ms.openlocfilehash: 30eb86987b83427b94c6fff22755cde3d73dd9f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184073"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a>Kurz: Hostování a spuštění základní služby Windows Communication Foundation

Tento kurz popisuje třetí z pěti úloh potřebných k vytvoření základní aplikace Windows Communication Foundation (WCF). Přehled výukových programů najdete v [tématu Výuka: Začínáme s aplikacemi Windows Communication Foundation](getting-started-tutorial.md).

Dalším úkolem pro vytvoření aplikace WCF je hostování služby WCF v konzolové aplikaci. Služba WCF zpřístupňuje jeden nebo více *koncových bodů*, z nichž každý zpřístupňuje jednu nebo více operací služby. Koncový bod služby určuje následující informace:

- Adresa, na které můžete najít službu.
- Vazba, která obsahuje informace, které popisují, jak klient musí komunikovat se službou.
- Smlouva, která definuje funkce, které služba poskytuje svým klientům.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> - Vytvořte a nakonfigurujte projekt konzolové aplikace pro hostování služby WCF.
> - Přidejte kód pro hostování služby WCF.
> - Aktualizujte konfigurační soubor.
> - Spusťte službu WCF a ověřte, zda je spuštěná.

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a>Vytvoření a konfigurace projektu konzolové aplikace pro hostování služby

1. Vytvoření projektu konzolové aplikace v Sadě Visual Studio:

    1. V nabídce **Soubor** vyberte **Otevřít** > **projekt/řešení** a přejděte k řešení **GettingStarted,** které jste dříve vytvořili (*GettingStarted.sln*). Vyberte **Open** (Otevřít).

    2. V nabídce **Zobrazení** vyberte **Průzkumník řešení**.

    3. V okně **Průzkumník řešení** vyberte řešení **GettingStarted** (horní uzel) a pak v místní nabídce vyberte **Přidat** > **nový projekt.**

    4. V okně **Přidat nový projekt** na levé straně vyberte kategorii Plocha **systému Windows** v části Visual **C#** nebo **Visual Basic**.

    5. Vyberte šablonu **Konzolové aplikace (.NET Framework)** a zadejte *GettingStartedHost* pro **název**. Vyberte **OK**.

2. Přidejte odkaz v projektu **GettingStartedHost** do projektu **GettingStartedLib:**

    1. V okně **Průzkumník řešení** vyberte složku **Reference v** projektu **GettingStartedHost** a pak v místní nabídce vyberte **Přidat odkaz.**

    2. V dialogovém okně **Přidat odkaz** vyberte v části **Projekty** na levé straně okna **možnost Řešení**.

    3. Vprostřední části okna vyberte **GettingStartedLib** a pak vyberte **OK**.

       Tato akce zpřístupní typy definované v projektu **GettingStartedLib** projektu **GettingStartedHost pro projekt GettingStartedHost.**

3. Přidejte odkaz v projektu **GettingStartedHost** do <xref:System.ServiceModel> sestavení:

    1. V okně **Průzkumník řešení** vyberte složku **Reference v** projektu **GettingStartedHost** a pak v místní nabídce vyberte **Přidat odkaz.**

    2. V okně **Přidat odkaz** vyberte v části **Sestavení** na levé straně okna **možnost Framework**.

    3. Vyberte **Položku System.ServiceModel**a pak vyberte **OK**.

    4. Uložte řešení výběrem **možnosti Uložit** > **vše**.

## <a name="add-code-to-host-the-service"></a>Přidání kódu pro hostování služby

Chcete-li službu hostovat, přidejte kód, který provede následující kroky:

1. Vytvořte identifikátor URI pro základní adresu.
2. Vytvořte instanci třídy pro hostování služby.
3. Vytvořte koncový bod služby.
4. Povolte výměnu metadat.
5. Otevřete hostitele služby a poslouchejte příchozí zprávy.
  
Proveďte následující změny kódu:

1. Otevřete soubor **Program.cs** nebo **Module1.vb** v projektu **GettingStartedHost** a nahraďte jeho kód následujícím kódem:

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

    Informace o tom, jak tento kód funguje, naleznete [v tématu Service hosting program steps](#service-hosting-program-steps).

2. Aktualizace vlastností projektu:

   1. V okně **Průzkumník řešení** vyberte složku **GettingStartedHost** a pak v místní nabídce vyberte **Vlastnosti.**

   2. Na stránce **Vlastností GettingStartedHost** vyberte kartu **Aplikace:**

      - U projektů jazyka C# vyberte **gettingstartedhost.program** ze seznamu **spouštěcích objektů.**

      - U projektů jazyka Visual Basic vyberte **service.program** ze seznamu **spouštěcích objektů.**

   3. V nabídce **Soubor** vyberte **Uložit vše**.

## <a name="verify-the-service-is-working"></a>Ověřte, zda služba funguje

1. Sestavte řešení a spusťte konzolovou aplikaci **GettingStartedHost** z aplikace Visual Studio.

    Služba musí být spuštěna s oprávněními správce. Vzhledem k tomu, že jste otevřeli Visual Studio s oprávněními správce, při spuštění **GettingStartedHost** v sadě Visual Studio je aplikace spuštěna také s oprávněními správce. Jako alternativu můžete otevřít nový příkazový řádek jako správce (v místní nabídce vyberte **možnost Další** > **spuštění jako správce)** a spustit v něm soubor **GettingStartedHost.exe.**

2. Otevřete webový prohlížeč a přejděte na `http://localhost:8000/GettingStarted/CalculatorService`stránku služby na adrese .

   > [!NOTE]
   > Služby, jako je tento, vyžadují řádné oprávnění k registraci adres HTTP v počítači pro naslouchání. Účty správce mají toto oprávnění, ale účty bez oprávnění správce musí být uděleno oprávnění pro obory názvů HTTP. Další informace o konfiguraci rezervací oboru názvů naleznete v [tématu Konfigurace protokolů HTTP a HTTPS](feature-details/configuring-http-and-https.md).

## <a name="service-hosting-program-steps"></a>Kroky programu hostování služeb

Kroky v kódu, který jste přidali k hostiteli služby jsou popsány takto:

- **Krok 1**: Vytvořte `Uri` instanci třídy pro uložení základní adresy služby. Adresa URL, která obsahuje základní adresu, má volitelný identifikátor URI, který identifikuje službu. Základní adresa je formátována `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`takto: . Základní adresa pro službu kalkulačky používá přenos HTTP, localhost, port 8000 a segment URI GettingStarted.

- **Krok 2**: Vytvořte <xref:System.ServiceModel.ServiceHost> instanci třídy, kterou používáte k hostování služby. Konstruktor má dva parametry: typ třídy, která implementuje servisní smlouvu a základní adresu služby.

- **Krok 3**: <xref:System.ServiceModel.Description.ServiceEndpoint> Vytvoření instance. Koncový bod služby se skládá z adresy, vazby a smlouvy o poskytování služeb. Konstruktor <xref:System.ServiceModel.Description.ServiceEndpoint> se skládá z typu rozhraní servisní smlouvy, vazby a adresy. Servisní smlouva `ICalculator`je , kterou jste definovali a implementovali v typu služby. Vazba pro tuto <xref:System.ServiceModel.WSHttpBinding>ukázku je , což je vestavěná vazba a připojuje se ke koncovým bodům, které odpovídají specifikacím WS-*. Další informace o vazby WCF naleznete v tématu [Přehled vazby WCF](bindings-overview.md). Připojíte adresu k základní adrese k identifikaci koncového bodu. Kód určuje adresu jako CalculatorService a plně kvalifikovanou adresu `http://localhost:8000/GettingStarted/CalculatorService`pro koncový bod jako .

    > [!IMPORTANT]
    > Pro rozhraní .NET Framework verze 4 a novější je přidání koncového bodu služby volitelné. Pro tyto verze, pokud nepřidáte kód nebo konfiguraci, WCF přidá jeden výchozí koncový bod pro každou kombinaci základní adresy a smlouvy implementované službou. Další informace o výchozích koncových bodech naleznete [v tématu Určení adresy koncového bodu](specifying-an-endpoint-address.md). Další informace o výchozích koncových bodech, vazbách a chování naleznete v [tématu Zjednodušená konfigurace](simplified-configuration.md) a [Zjednodušená konfigurace pro služby WCF](samples/simplified-configuration-for-wcf-services.md).

- **Krok 4**: Povolit výměnu metadat. Klienti používají výměnu metadat ke generování proxy serverů pro volání operací služby. Chcete-li povolit výměnu <xref:System.ServiceModel.Description.ServiceMetadataBehavior> metadat, <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> vytvořte `true`instanci, nastavte její vlastnost na a přidejte `ServiceMetadataBehavior` objekt do <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekce <xref:System.ServiceModel.ServiceHost> instance.

- **Krok 5** <xref:System.ServiceModel.ServiceHost> : Otevřete pro poslech příchozích zpráv. Aplikace čeká, až stisknete **klávesu Enter**. Poté, co aplikace <xref:System.ServiceModel.ServiceHost>instance , provede try/catch bloku. Další informace o bezpečném zachycení <xref:System.ServiceModel.ServiceHost>výjimek vyvolaných aplikacemi naleznete [v tématu Použití zavřít a přerušit uvolnění klientských prostředků WCF](samples/use-close-abort-release-wcf-client-resources.md).

> [!IMPORTANT]
> Když přidáte knihovnu služeb WCF, Visual Studio ji hostuje za vás, pokud ji ladíte spuštěním hostitele služby. Chcete-li se vyhnout konfliktům, můžete zabránit visual studio hostování knihovny služeb WCF.
>
> 1. V průzkumníku **řešení** vyberte projekt **GettingStartedLib** a z místní nabídky zvolte **Vlastnosti.**
> 2. Vyberte **možnosti WCF** a zrušte zaškrtnutí **políčka Spustit hostitele služby WCF při ladění jiného projektu ve stejném řešení**.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> - Vytvořte a nakonfigurujte projekt konzolové aplikace pro hostování služby WCF.
> - Přidejte kód pro hostování služby WCF.
> - Aktualizujte konfigurační soubor.
> - Spusťte službu WCF a ověřte, zda je spuštěná.

Přejdete k dalšímu kurzu, který se dozvíte, jak vytvořit klienta WCF.

> [!div class="nextstepaction"]
> [Kurz: Vytvoření klienta WCF](how-to-create-a-wcf-client.md)
