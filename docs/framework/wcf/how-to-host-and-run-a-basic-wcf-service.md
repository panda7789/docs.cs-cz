---
title: "Postupy: Hostování a spuštění základní služby Windows Communication Foundation Service"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 92aa512a12911913c1d4d7ca1587bb04df0a501d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a>Postupy: Hostování a spuštění základní služby Windows Communication Foundation Service
Toto je třetí šesti úlohy, které jsou nutné k vytváření [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikace. Přehled všech šest úloh najdete v tématu [kurzu Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md) tématu.  
  
 Toto téma popisuje, jak hostovat [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] službu v konzolové aplikaci. Tento postup se skládá z následujících kroků:  
  
-   Vytvoření projektu konzolové aplikace k hostování služby.  
  
-   Vytvořte hostitele služby pro službu.  
  
-   Povolte metadata exchange.  
  
-   Otevření hostitele služby.  
  
 Úplný kód napsaný v této úloze najdete v příkladu za postupem.  
  
## <a name="to-create-a-new-console-application-to-host-the-service"></a>Chcete-li vytvořit novou konzolovou aplikaci k hostování služby  
  
1.  Vytvořte nový projekt konzolové aplikace kliknutím pravým tlačítkem na řešení Začínáme vyberete, **přidat**, **nový projekt**. V **přidat nový projekt** dialog v dialogovém okně vyberte na levé straně **Windows** pod **C#** nebo **VB**. V části center dialogového okna Vybrat **konzolové aplikace**. Název projektu GettingStartedHost.  
  
2.  Nastavte cílový framework projektu GettingStartedHost na rozhraní .NET Framework 4.5 kliknutím pravým tlačítkem na **GettingStartedHost** v Průzkumníku řešení a výběrem **vlastnosti**. Rozevírací pole s popiskem **cílové rozhraní** vyberte **rozhraní .NET Framework 4.5**. Nastavení cílové rozhraní projektu jazyka Visual Basic je mírně liší v dialogovém okně Vlastnosti projektu GettingStartedHost, klikněte na tlačítko **zkompilovat** na levé straně obrazovky a pak klikněte **Advanced kompilace Možnosti** tlačítko v levém dolním rohu dialogu. Potom vyberte **rozhraní .NET Framework 4.5** rozevírací pole s popiskem **cílové rozhraní**.  
  
     Nastavení způsobí, že cílový framework [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] Pokud chcete znovu načíst řešení, stiskněte **OK** po zobrazení výzvy.  
  
3.  Přidat odkaz na projekt GettingStartedLib do projektu GettingStartedHost kliknutím pravým tlačítkem na **odkazy** ve složce projektu GettingStartedHost v Průzkumníku řešení a vyberte **přidání odkazu** . V **přidat odkaz na** dialogovém okně, vyberte **řešení** na levé straně dialogové okno a vyberte GettingStartedLib v části center dialogové okno a klikněte na tlačítko **přidat**. Díky tomu typy definované v GettingStartedLib GettingStartedHost projektu k dispozici.  
  
4.  Přidat odkaz na System.ServiceModel do projektu GettingStartedHost kliknutím pravým tlačítkem myši **odkaz** ve složce projektu GettingStartedHost v Průzkumníku řešení a vyberte **přidat** Odkaz. V **přidat odkaz na** dialogovém okně vyberte **Framework** na levé straně dialogového okna. Zadejte do textového pole hledání sestavení v `System.ServiceModel`. V části center dialogového okna Vybrat **System.ServiceModel**, klikněte na tlačítko **přidat** tlačítko a klikněte na tlačítko **Zavřít** tlačítko. Řešení uložte kliknutím na tlačítko Uložit vše v hlavní nabídce.  
  
### <a name="to-host-the-service"></a>K hostování služby  
  
-   Otevřete soubor Program.cs nebo Module.vb a zadejte následující kód:  
  
    ```csharp
    // program.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.ServiceModel;  
    using GettingStartedLib;  
    using System.ServiceModel.Description;   
  
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
    'Module1.vb  
    Imports System  
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
  
    1.  Krok 1 – vytvoří instanci třídy identifikátor Uri pro uložení základní adresa služby. Služby jsou označeny adresy URL, která obsahuje základní adresu a volitelné identifikátor URI. Základní adresa je naformátován takto: [přenosu] :// [název počítače nebo domény] [: volitelný port #] nebo [volitelné segment identifikátoru URI] přenos HTTP používá základní adresu pro službu kalkulačky, localhost, port 8000 a identifikátor URI segmentovat "GettingStarted"  
  
    2.  Krok 2 – vytvoří instanci <xref:System.ServiceModel.ServiceHost> třída k hostování služby. Konstruktor přebírá dva parametry, typu třídy, která implementuje kontrakt služby a základní adresa služby.  
  
    3.  Krok 3 – vytvoří <!--zz <xref:System.ServiceModel.ServiceEndpoint>--> ` System.ServiceModel.ServiceEndpoint` instance. Koncový bod služby se skládá z adresy, vazby a kontraktu služby. <!--zz <xref:System.ServiceModel.ServiceEndpoint>--> ` System.ServiceModel.ServiceEndpoint` Konstruktor proto trvá typ rozhraní kontraktu služby, vazbu a adresu. Kontrakt služby je `ICalculator`, která definované a implementovat typ služby. Vazba použitá v této ukázce je <xref:System.ServiceModel.WSHttpBinding> tedy předdefinované vazbu, která se používá pro připojení ke koncovým bodům, které odpovídají WS-* specifikace. Další informace o vazby WCF najdete v tématu [vazby WCF – přehled](../../../docs/framework/wcf/bindings-overview.md). Adresa se připojuje k základní adresu k identifikaci koncového bodu. Zadaná adresa v tento kód je "CalculatorService" plně kvalifikovanou adresu pro koncový bod je `"http://localhost:8000/GettingStarted/CalculatorService"` přidání koncového bodu služby je volitelný při použití rozhraní .NET Framework 4.0 nebo novější. V těchto verzích Pokud žádné koncové body se přidají kódu nebo konfigurace, WCF přidá jeden výchozí koncový bod pro každou kombinaci základní adresa a kontrakt implementované službu. Další informace o výchozím nastavení najdete v části koncové body [zadání adresy koncového bodu](../../../docs/framework/wcf/specifying-an-endpoint-address.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)]výchozí koncové body, vazby a chování, viz [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
        > [!IMPORTANT]
        >  Přidání koncového bodu služby je volitelný při použití rozhraní .NET Framework 4 nebo novější. V těchto verzích Pokud žádné koncové body se přidají kódu nebo konfigurace, WCF přidá jeden výchozí koncový bod pro každou kombinaci základní adresa a kontrakt implementované službu. Další informace o výchozím nastavení najdete v části koncové body [zadání adresy koncového bodu](../../../docs/framework/wcf/specifying-an-endpoint-address.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)]výchozí koncové body, vazby a chování, viz [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
    4.  Krok 4 – povolení metadata exchange. Metadata exchange budou klienti používat ke generování proxy servery, které se použije k volání operací služby. Povolit vytvořit metadata exchange <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, nastavte ji na <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> vlastnost `true`a přidejte požadované chování, <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  --> `System.ServiceModel.ServiceHost.Behaviors%2A` kolekce <xref:System.ServiceModel.ServiceHost> instance.  
  
    5.  Krok 5 – otevřete <xref:System.ServiceModel.ServiceHost> přijímat příchozí zprávy. Zadejte oznámení, které kód čeká uživatelem. Pokud není to uděláte, aplikace bude okamžitě ukončena a služba bude vypnuta. Také oznámení používá blok try/catch. Po <xref:System.ServiceModel.ServiceHost> byla vytvořena instance, jiný kód je umístěn v bloku try/catch. Další informace o bezpečně zachytávání výjimek vyvolaných <xref:System.ServiceModel.ServiceHost>, najdete v části [vyhnout problémům s příkazem Using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)  
  
### <a name="to-verify-the-service-is-working"></a>Chcete-li ověřit, že služba funguje  
  
1.  Spusťte konzolovou aplikaci GettingStartedHost z uvnitř [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]. Při spuštění [!INCLUDE[wv](../../../includes/wv-md.md)] a novějších operačních systémech, služba musí být spuštěn s oprávněními správce. Protože [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] byl spuštěn s oprávněním správce, GettingStartedHost je také spustit s oprávněním správce. Můžete také otevřete nový příkazový řádek s oprávněními správce a spusťte service.exe v něm.  
  
2.  Otevřete Internet Explorer a přejděte k ladění služby stránky v `http://localhost:8000/GettingStarted/CalculatorService`.  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje kontrakt služby a implementaci z předchozích kroků tohoto kurzu a hostuje službu v konzolové aplikaci.  
  
 To zkompilovat pomocí příkazového řádku kompilátoru, kompilována IService1.cs a Service1.cs knihovny tříd odkazující na `System.ServiceModel.dll`. A kompilaci souboru Program.cs do konzolové aplikace.  
  
```csharp
// IService1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
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
// Service1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
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
//Program.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel;  
using GettingStartedLib;  
using System.ServiceModel.Description;   
  
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
'IService1.vb  
Imports System  
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
'Service1.vb  
Imports System  
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
'Module1.vb  
Imports System  
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
>  Služby, jako je tento vyžadují oprávnění k registraci adresy protokolu HTTP na počítači pro naslouchání. Toto oprávnění mají účty správců, ale není správcem účty je potřeba udělit oprávnění pro obory názvů HTTP. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Postup konfigurace oboru názvů rezervace najdete v tématu [konfigurace HTTP a HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md). Při spuštění v [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], service.exe musí být spuštěn s oprávněními správce.  
  
 Nyní je služba spuštěná. Pokračujte [postupy: vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md). Informace o odstraňování potíží, najdete v části [řešení potíží s kurzu Začínáme](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).  
  
## <a name="see-also"></a>Viz také  
 [Začínáme](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Vlastní hostování](../../../docs/framework/wcf/samples/self-host.md)
