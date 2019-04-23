---
title: Přístup ke službám pomocí klienta WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
ms.openlocfilehash: 6bf683cdd0a03a5d1dbc452c28e7b33911464f09
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59297249"
---
# <a name="accessing-services-using-a-wcf-client"></a>Přístup ke službám pomocí klienta WCF

Po vytvoření služby, dalším krokem je vytvoření proxy serveru klienta WCF. Klientská aplikace bude používat ke komunikaci se službou proxy klienta WCF. Klientské aplikace obvykle importovat metadata služby pro generování kódu klienta WCF, který můžete použít k vyvolání služby.

 Základní kroky pro vytvoření klienta WCF patří:

1. Kompilace kódu služby.

2. Generování proxy klienta WCF.

3. Vytvořit instanci proxy serveru klienta WCF.

Klient proxy WCF je vygenerovat ručně pomocí nástroje modelu služby Metadata Utility (SvcUtil.exe) pro další informace najdete [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Klient proxy WCF můžou být taky vygenerovaná v rámci sady Visual Studio pomocí **přidat odkaz na službu** funkce. Generování proxy klienta WCF pomocí některé z metod služby musí být spuštěna. Pokud je služba v místním prostředí je nutné spustit hostiteli. Pokud služba je hostována ve službě IIS nebo WAS, nemusíte dělat nic dalšího.

## <a name="servicemodel-metadata-utility-tool"></a>Nástroj ServiceModel Metadata Utility
 [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) je nástroj příkazového řádku pro generování kódu z metadat. Následující je příklad základní příkaz Svcutil.exe.

```
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
```

 Alternativně můžete použít Svcutil.exe webové služby WSDL (Description Language) a schéma XML definice jazyk (XSD) soubory v systému souborů.

```
Svcutil.exe <list of WSDL and XSD files on file system>
```

 Výsledkem je soubor kódu, který obsahuje kód klienta WCF, který klientská aplikace můžete použít k vyvolání služby.

 Nástroj můžete použít také ke generování konfigurační soubory.

```
Svcutil.exe <file1 [,file2]>
```

 Pokud pouze jeden název souboru je uveden, to je název výstupního souboru. Dva názvy souborů směru, je-li první soubor je soubor vstupní konfigurace, jejichž obsah jsou sloučeny s vygenerovanou konfiguraci a zapsat do druhého souboru. Další informace o konfiguraci najdete v tématu [Konfigurace vazeb pro služby](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).

> [!IMPORTANT]
> Požadavky na nezabezpečenou metadata představovat určitá rizika stejným způsobem, který nemá žádné žádosti o nezabezpečené síti: Pokud si nejste jisti, že je koncový bod, které komunikují s který říká, že se že jedná, může být informace, které můžete načíst metadata ze škodlivých služby.

## <a name="add-service-reference-in-visual-studio"></a>Přidání odkazu na službu v sadě Visual Studio

 Služba spuštěná, klikněte pravým tlačítkem na projekt, který bude obsahovat proxy klienta WCF a zvolte **přidat** > **odkaz na službu**. V **dialogové okno Přidat odkaz na službu**, zadejte adresu URL služby, které chcete volat a klikněte na tlačítko **Přejít** tlačítko. Dialogové okno se zobrazí seznam služeb, které jsou k dispozici na adrese, kterou zadáte. Dvakrát klikněte na službu naleznete v tématu smluv a operace, které jsou k dispozici, zadejte obor názvů pro generovaný kód a klikněte na tlačítko **OK** tlačítko.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje kontraktu služby vytvořené pro službu.

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    // Other methods are not shown here.
}
```

```vb
' Define a service contract.
<ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
Public Interface ICalculator
    <OperationContract()>  _
    Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
    ' Other methods are not shown here.
End Interface
```

 Nástroj ServiceModel Metadata a **přidat odkaz na službu** v sadě Visual Studio generuje následující třídy klienta WCF. Třída dědí z obecného <xref:System.ServiceModel.ClientBase%601> třídy a implementuje `ICalculator` rozhraní. Nástroj také vytvoří `ICalculator` rozhraní (není tady zobrazené).

```csharp
public partial class CalculatorClient : System.ServiceModel.ClientBase<ICalculator>, ICalculator
{
    public CalculatorClient()
    {}

    public CalculatorClient(string endpointConfigurationName) :
            base(endpointConfigurationName)
    {}

    public CalculatorClient(string endpointConfigurationName, string remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(string endpointConfigurationName,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(System.ServiceModel.Channels.Binding binding,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(binding, remoteAddress)
    {}

    public double Add(double n1, double n2)
    {
        return base.Channel.Add(n1, n2);
    }
}
```

```vb
Partial Public Class CalculatorClient
    Inherits System.ServiceModel.ClientBase(Of ICalculator)
    Implements ICalculator

    Public Sub New()
        MyBase.New
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String)
        MyBase.New(endpointConfigurationName)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String, ByVal remoteAddress As String)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal binding As System.ServiceModel.Channels.Binding,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(binding, remoteAddress)
    End Sub

    Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        Implements ICalculator.Add
        Return MyBase.Channel.Add(n1, n2)
    End Function
End Class
```

## <a name="using-the-wcf-client"></a>Pomocí klienta WCF
 Použití klienta WCF, vytvořte instanci klienta WCF a potom volání obsažených metod, jak je znázorněno v následujícím kódu.

```csharp
// Create a client object with the given client endpoint configuration.
CalculatorClient calcClient = new CalculatorClient("CalculatorEndpoint"));
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = calcClient.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```

```vb
' Create a client object with the given client endpoint configuration.
Dim calcClient As CalculatorClient = _
New CalculatorClient("CalculatorEndpoint")

' Call the Add service operation.
Dim value1 As Double = 100.00D
Dim value2 As Double = 15.99D
Dim result As Double = calcClient.Add(value1, value2)
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)
```

## <a name="debugging-exceptions-thrown-by-a-client"></a>Ladění výjimky vyvolané klientem

Velký počet výjimek vyvolaných klienta WCF jsou způsobeny výjimku ve službě. Některé příklady jsou:

-   <xref:System.Net.Sockets.SocketException>: Stávající připojení vynuceně zavřel vzdálený hostitel.

-   <xref:System.ServiceModel.CommunicationException>: Základní připojení bylo neočekávaně ukončeno.

-   <xref:System.ServiceModel.CommunicationObjectAbortedException>: Připojení soketu bylo přerušeno. Může to být způsobeno chybou při zpracování zprávy, vypršení časového limitu příjmu, překročení vzdáleným hostitelem nebo problém prostředků základní sítě.

Pokud dojde k tyto typy výjimek, je nejlepší způsob, jak problém vyřešit zapnout trasování na straně služby a zjistit, jaké výjimky došlo k chybě došlo. Další informace o trasování najdete v tématu [trasování](../../../docs/framework/wcf/diagnostics/tracing/index.md) a [pomocí trasování řešení potíží s aplikace](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).

## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [Postupy: Přístup ke službám pomocí duplexního kontraktu](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Postupy: Asynchronní volání operací služby](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [Postupy: Přístup ke službám pomocí jednosměrných kontraktů a kontraktů požadavek odpověď](../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [Postupy: Přístup k WSE 3.0 Service](../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [Principy generovaného klientského kódu](../../../docs/framework/wcf/feature-details/understanding-generated-client-code.md)
- [Postupy: Vylepšení spuštění čas z klientských aplikací WCF pomocí třídy XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
- [Nastavení chování klienta za běhu](../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [Konfigurace chování klienta](../../../docs/framework/wcf/configuring-client-behaviors.md)
