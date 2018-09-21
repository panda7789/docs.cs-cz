---
title: 'Postupy: Hostování a spuštění základní služby Windows Communication Foundation Service'
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: b79c3246b7c12a3a99a5c68586387fc30573dcb6
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46562291"
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a>Postupy: Hostování a spuštění základní služby Windows Communication Foundation Service

Toto je třetí webinář z šesti úkolů potřebný k vytvoření aplikace Windows Communication Foundation (WCF). Přehled všech šesti úkoly, naleznete v tématu [kurz Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md) tématu.

Toto téma popisuje, jak k hostování služby Windows Communication Foundation (WCF) v konzolové aplikaci. Tento postup se skládá z následujících kroků:

- Vytvořte projekt konzolové aplikace pro hostování služby.

- Vytvořte hostitelskou služby pro službu.

- Povolte výměny metadat.

- Otevření hostitele služby.

Úplný kód napsaný v této úloze je najdete v příkladu za postupem.

## <a name="create-a-new-console-application-to-host-the-service"></a>Vytvořte novou konzolovou aplikaci pro hostování služby

1. Vytvořte nový projekt konzolové aplikace v sadě Visual Studio tak, že kliknete pravým tlačítkem na řešení Začínáme a vyberete **přidat** > **nový projekt**. V **přidat nový projekt** dialogového okna na levé straně, vyberte **Windows Desktop** kategorie v části **Visual C#** nebo **jazyka Visual Basic**. Vyberte **Konzolová aplikace (.NET Framework)** šablony a poté pojmenujte projekt **GettingStartedHost**.

2. Přidáte odkaz na projekt GettingStartedLib GettingStartedHost projektu. Klikněte pravým tlačítkem na **odkazy** ve složce projektu GettingStartedHost v **Průzkumníka řešení**a pak vyberte **přidat odkaz**. V **přidat odkaz** dialogového okna, vyberte **řešení** na levé straně dialogového okna, vyberte GettingStartedLib v System center části dialogového okna a pak zvolte **přidat**. Díky tomu typy definované v GettingStartedLib GettingStartedHost projektu k dispozici.

3. Přidáte odkaz na System.ServiceModel GettingStartedHost projektu. Klikněte pravým tlačítkem myši **odkazy** ve složce projektu GettingStartedHost v **Průzkumníku řešení** a vyberte **přidat odkaz**. V **přidat odkaz** dialogového okna, vyberte **Framework** na levé straně dialogového okna v části **sestavení**. Vyhledejte a vyberte **System.ServiceModel**a klikněte na tlačítko **OK**. Uložte řešení tak, že vyberete **souboru** > **Uložit vše**.

## <a name="host-the-service"></a>Hostitel služby

Otevřete soubor Program.cs nebo Module.vb a zadejte následující kód:

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
            // Step 1 Create a URI to serve as the base address.
            Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");

            // Step 2 Create a ServiceHost instance
            ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);

            try
            {
                // Step 3 Add a service endpoint.
                selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");

                // Step 4 Enable metadata exchange.
                ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
                smb.HttpGetEnabled = true;
                selfHost.Description.Behaviors.Add(smb);

                // Step 5 Start the service.
                selfHost.Open();
                Console.WriteLine("The service is ready.");
                Console.WriteLine("Press <ENTER> to terminate service.");
                Console.WriteLine();
                Console.ReadLine();

                // Close the ServiceHostBase to shutdown the service.
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
Imports GettingStartedLibVB.GettingStartedLib

Module Service

    Class Program
        Shared Sub Main()
            ' Step 1 Create a URI to serve as the base address
            Dim baseAddress As New Uri("http://localhost:8000/ServiceModelSamples/Service")

            ' Step 2 Create a ServiceHost instance
            Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)
           Try

                ' Step 3 Add a service endpoint
                ' Add a service endpoint
                selfHost.AddServiceEndpoint( _
                    GetType(ICalculator), _
                    New WSHttpBinding(), _
                    "CalculatorService")

                ' Step 4 Enable metadata exchange.
                Dim smb As New ServiceMetadataBehavior()
                smb.HttpGetEnabled = True
                selfHost.Description.Behaviors.Add(smb)

                ' Step 5 Start the service
                selfHost.Open()
                Console.WriteLine("The service is ready.")
                Console.WriteLine("Press <ENTER> to terminate service.")
                Console.WriteLine()
                Console.ReadLine()

                ' Close the ServiceHostBase to shutdown the service.
                selfHost.Close()
            Catch ce As CommunicationException
                Console.WriteLine("An exception occurred: {0}", ce.Message)
                selfHost.Abort()
            End Try
        End Sub
    End Class

End Module
```

**Krok 1** -vytvoří instanci třídy Uri k umístění základní adresu služby. Služby jsou označeny adresu URL, která obsahuje základní adresu a volitelné identifikátoru URI. Základní adresa naformátován takto: [přenosu] :// [název počítače nebo domény] [: volitelné port č] / [volitelný segment identifikátoru URI] základní adresa pro službu kalkulačky používá přenos pomocí protokolu HTTP, místního hostitele, port 8000 a identifikátor URI segmentovat "GettingStarted"

**Krok 2** – vytvoří instanci <xref:System.ServiceModel.ServiceHost> třídy pro hostování služby. Konstruktor přijímá dva parametry typu třídy, která implementuje kontrakt služby a základní adresu služby.

**Krok 3** – vytvoří <xref:System.ServiceModel.Description.ServiceEndpoint> instance. Koncový bod služby se skládá z adresy, vazby a smlouvy o poskytování služeb. <xref:System.ServiceModel.Description.ServiceEndpoint> Konstruktor proto přebírá typ rozhraní kontraktu služby, vazbu a adresu. Kontrakt služby je `ICalculator`, která definované a implementaci v typu služby. Vazba použitá v tomto příkladu je <xref:System.ServiceModel.WSHttpBinding> což je integrované vazbu, která se používá pro připojení ke koncovým bodům, které odpovídají WS-* specifikace. Další informace o vazbách WCF najdete v tématu [vazby WCF – přehled](../../../docs/framework/wcf/bindings-overview.md). Adresa se připojí k základní adrese k identifikaci koncového bodu. Adresa zadaná v tomto kódu je "CalculatorService", takže je plně kvalifikovanou adresu pro koncový bod `"http://localhost:8000/GettingStarted/CalculatorService"`.

    > [!IMPORTANT]
    > Adding a service endpoint is optional when using .NET Framework 4 or later. In these versions, if no endpoints are added in code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service. For more information about default endpoints see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md). For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).

**Krok 4** – povolit výměny metadat. Klienti použijí ke generování proxy servery, které se použije k volání operací služby metadata exchange. Umožňuje vytvořit výměny metadat <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, nastavte ho na <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> vlastnost `true`a přidat chování při <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  --> `System.ServiceModel.ServiceHost.Behaviors%2A` kolekce <xref:System.ServiceModel.ServiceHost> instance.

**Krok 5** – otevře <xref:System.ServiceModel.ServiceHost> k naslouchání pro příchozí zprávy. Všimněte si, že kód čeká uživatelem zadejte. Pokud to neprovedete, bude aplikace okamžitě ukončena a služby se vypne. Všimněte si také bloku try/catch použít. Po <xref:System.ServiceModel.ServiceHost> byla vytvořena instance, jiný kód je umístěn v bloku try/catch. Další informace o bezpečně zachycování výjimek vyvolaných <xref:System.ServiceModel.ServiceHost>, naleznete v tématu [vyhnout problémům s příkazem Using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)

> [!IMPORTANT]
> Úpravy souboru App.config v GettingStartedLib tak, aby odrážely změny provedené v kódu:
> 1. Změňte na řádek 14 `<service name="GettingStartedLib.CalculatorService">`
> 2. Změňte řádek 17 `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
> 3. Změňte řádek 22 na `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`

## <a name="verify-the-service-is-working"></a>Ověřte, že služba funguje

1. Spustit konzolu GettingStartedHost z aplikace v sadě Visual Studio.

   Služba musí běžet s oprávněními správce. Vzhledem k tomu, že Visual Studio otevřené s oprávněními správce, GettingStartedHost také spouštět s oprávněními správce. Můžete také otevřít nový příkazový řádek pomocí **spustit jako správce** a spusťte service.exe v něm.

2. Otevřete webový prohlížeč a přejděte na stránku služby ladění na `http://localhost:8000/GettingStarted/CalculatorService`.

## <a name="example"></a>Příklad

Následující příklad obsahuje kontrakt a implementaci služby z předchozích kroků tohoto kurzu a hostuje službu v konzolové aplikaci.

Chcete-li zkompilovat pomocí příkazového řádku kompilátoru, kompilace IService1.cs a Service1.cs do knihovny tříd, který odkazuje na `System.ServiceModel.dll`. Soubor Program.cs zkompiluje kód jako konzolové aplikace.

```csharp
using System;
using System.ServiceModel;

namespace GettingStartedLib
{
        [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
        public interface ICalculator
        {
            [OperationContract]
            double Add(double n1, double n2);
            [OperationContract]
            double Subtract(double n1, double n2);
            [OperationContract]
            double Multiply(double n1, double n2);
            [OperationContract]
            double Divide(double n1, double n2);
        }
}
```

```csharp
using System;
using System.ServiceModel;

namespace GettingStartedLib
{
    public class CalculatorService : ICalculator
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            // Code added to write output to the console window.
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
}
```

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
            // Step 1 of the address configuration procedure: Create a URI to serve as the base address.
            Uri baseAddress = new Uri("http://localhost:8000/ServiceModelSamples/Service");

            // Step 2 of the hosting procedure: Create ServiceHost
            ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);

            try
            {
                // Step 3 of the hosting procedure: Add a service endpoint.
                selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");

                // Step 4 of the hosting procedure: Enable metadata exchange.
                ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
                smb.HttpGetEnabled = true;
                selfHost.Description.Behaviors.Add(smb);

                // Step 5 of the hosting procedure: Start (and then stop) the service.
                selfHost.Open();
                Console.WriteLine("The service is ready.");
                Console.WriteLine("Press <ENTER> to terminate service.");
                Console.WriteLine();
                Console.ReadLine();

                // Close the ServiceHostBase to shutdown the service.
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

Namespace GettingStartedLib

    <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
    Public Interface ICalculator

        <OperationContract()> _
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
    End Interface
End Namespace
```

```vb
Imports System.ServiceModel

Namespace GettingStartedLib

    Public Class CalculatorService
        Implements ICalculator

        Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add
            Dim result As Double = n1 + n2
            ' Code added to write output to the console window.
            Console.WriteLine("Received Add({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result
        End Function

        Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract
            Dim result As Double = n1 - n2
            Console.WriteLine("Received Subtract({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply
            Dim result As Double = n1 * n2
            Console.WriteLine("Received Multiply({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide
            Dim result As Double = n1 / n2
            Console.WriteLine("Received Divide({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function
    End Class
End Namespace
```

```vb
Imports System.ServiceModel
Imports System.ServiceModel.Description
Imports GettingStartedLibVB.GettingStartedLib

Module Service

    Class Program
        Shared Sub Main()
            ' Step 1 of the address configuration procedure: Create a URI to serve as the base address.
            Dim baseAddress As New Uri("http://localhost:8000/ServiceModelSamples/Service")

            ' Step 2 of the hosting procedure: Create ServiceHost
            Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)
            Try

                ' Step 3 of the hosting procedure: Add a service endpoint.
                ' Add a service endpoint
                selfHost.AddServiceEndpoint( _
                    GetType(ICalculator), _
                    New WSHttpBinding(), _
                    "CalculatorService")

                ' Step 4 of the hosting procedure: Enable metadata exchange.
                ' Enable metadata exchange
                Dim smb As New ServiceMetadataBehavior()
                smb.HttpGetEnabled = True
                selfHost.Description.Behaviors.Add(smb)

                ' Step 5 of the hosting procedure: Start (and then stop) the service.
                selfHost.Open()
                Console.WriteLine("The service is ready.")
                Console.WriteLine("Press <ENTER> to terminate service.")
                Console.WriteLine()
                Console.ReadLine()

                ' Close the ServiceHostBase to shutdown the service.
                selfHost.Close()
            Catch ce As CommunicationException
                Console.WriteLine("An exception occurred: {0}", ce.Message)
                selfHost.Abort()
            End Try
        End Sub
    End Class

End Module
```

> [!NOTE]
> Služby, jako je ten vyžadují oprávnění k registraci adresami protokolu HTTP na počítači pro naslouchání. Účty správců mají toto oprávnění, ale účty bez oprávnění správce musí být uděleno oprávnění pro obory názvů HTTP. Další informace o tom, jak konfigurace rezervace oboru názvů najdete v tématu [konfigurace HTTP a HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md). Při spuštění v sadě Visual Studio, musí být spuštěn service.exe s oprávněními správce.

## <a name="next-steps"></a>Další kroky

Nyní je služba spuštěna. V dalším krokem vytvoření klienta WCF.

> [!div class="nextstepaction"]
> [Postupy: vytvoření klienta WCF](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)

Informace o odstraňování potíží naleznete v tématu [řešení potíží s kurzu Začínáme](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).

## <a name="see-also"></a>Viz také:

- [Začínáme](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [Vlastní hostování](../../../docs/framework/wcf/samples/self-host.md)