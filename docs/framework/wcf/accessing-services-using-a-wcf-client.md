---
title: Přístup ke službám pomocí klienta WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
ms.openlocfilehash: 462d9a3923009f0124c2b90b6fa86dfa9869a3c5
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72316543"
---
# <a name="accessing-services-using-a-wcf-client"></a>Přístup ke službám pomocí klienta WCF

Po vytvoření služby je dalším krokem vytvoření proxy klienta WCF. Klientská aplikace používá ke komunikaci se službou klienta proxy serveru služby WCF. Klientské aplikace obvykle importují metadata služby pro generování kódu klienta WCF, který lze použít k vyvolání služby.

 Základní kroky pro vytvoření klienta WCF zahrnují následující:

1. Zkompilujte kód služby.

2. Vygenerujte proxy server klienta služby WCF.

3. Vytvořte instanci proxy serveru služby WCF.

Proxy klient služby WCF se dá vytvořit ručně pomocí nástroje Service model metadat (SvcUtil. exe), kde najdete další informace v tématu [Nástroj pro nástroj pro metadata typu ServiceModel (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md). Proxy klient služby WCF lze také vygenerovat v rámci sady Visual Studio pomocí funkce **Přidat odkaz na službu** . Pro vygenerování proxy serveru služby WCF pomocí obou metod, které musí služba běžet. Pokud je služba v místním prostředí hostována, musíte spustit hostitele. Pokud je služba hostovaná ve službě IIS/nemusíte dělat něco jiného.

## <a name="servicemodel-metadata-utility-tool"></a>Nástroj pro metadata ServiceModel
 Nástroj pro vytváření [metadat (Svcutil. exe) třídy ServiceModel](servicemodel-metadata-utility-tool-svcutil-exe.md) je nástroj příkazového řádku pro generování kódu z metadat. Následující použití je příkladem základního příkazu Svcutil. exe.

```console
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
```

 Alternativně můžete použít Svcutil. exe se soubory WSDL (Web Services Description Language) a XSD (XML Schema Definition Language) v systému souborů.

```console
Svcutil.exe <list of WSDL and XSD files on file system>
```

 Výsledkem je soubor kódu, který obsahuje kód klienta WCF, který může klientská aplikace použít k vyvolání služby.

 Můžete také použít nástroj pro generování konfiguračních souborů.

```console
Svcutil.exe <file1 [,file2]>
```

 Je-li zadán pouze jeden název souboru, jedná se o název výstupního souboru. Pokud jsou zadány dva názvy souborů, pak je prvním souborem vstupní konfigurační soubor, jehož obsah je sloučen s vygenerovanou konfigurací a napsaný do druhého souboru. Další informace o konfiguraci najdete v tématu [Konfigurace vazeb pro služby](configuring-bindings-for-wcf-services.md).

> [!IMPORTANT]
> Nezabezpečené žádosti o metadata představují určitá rizika stejným způsobem jako jakákoli nezabezpečená síťová žádost: Pokud si nejste jisti, že koncový bod, se kterým komunikujete, je ten, kdo je vyjadřuje, informace, které načítajíte, mohou být metadata ze škodlivé služby.

## <a name="add-service-reference-in-visual-studio"></a>Přidat odkaz na službu v aplikaci Visual Studio

 Po spuštění služby klikněte pravým tlačítkem myši na projekt, který bude obsahovat proxy klienta WCF, a vyberte **Přidat** **odkaz na službu** > . V **dialogovém okně Přidat odkaz na službu**zadejte adresu URL služby, kterou chcete zavolat, a klikněte na tlačítko **Přejít** . V dialogovém okně se zobrazí seznam služeb dostupných na adrese, kterou zadáte. Dvojím kliknutím na službu zobrazte dostupné kontrakty a operace, zadejte obor názvů pro vygenerovaný kód a klikněte na tlačítko **OK** .

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje kontrakt služby vytvořenou pro službu.

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

 Nástroj pro dodávání metadat ServiceModel a **Přidat odkaz na službu** v aplikaci Visual Studio generuje následující třídu klienta WCF. Třída dědí z obecné třídy <xref:System.ServiceModel.ClientBase%601> a implementuje rozhraní `ICalculator`. Nástroj také vygeneruje rozhraní `ICalculator` (zde není zobrazeno).

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

## <a name="using-the-wcf-client"></a>Použití klienta WCF
 Chcete-li použít klienta služby WCF, vytvořte instanci klienta WCF a pak zavolejte své metody, jak je znázorněno v následujícím kódu.

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

## <a name="debugging-exceptions-thrown-by-a-client"></a>Ladění výjimek vyvolaných klientem

Mnoho výjimek vyvolaných klientem WCF je způsobeno výjimkou ve službě. Mezi příklady patří:

- <xref:System.Net.Sockets.SocketException>: vzdálený hostitel nuceně zavřel existující připojení.

- <xref:System.ServiceModel.CommunicationException>: základní připojení bylo neočekávaně ukončeno.

- <xref:System.ServiceModel.CommunicationObjectAbortedException>: připojení soketu bylo přerušeno. To může být způsobeno chybou při zpracování vaší zprávy, překročením časového limitu příjmu vzdáleným hostitelem nebo problémem se síťovými prostředky.

Pokud dojde k těmto typům výjimek, nejlepším způsobem, jak problém vyřešit, je zapnout trasování na straně služby a určit, k jaké výjimce došlo. Další informace o trasování naleznete v tématu [trasování](./diagnostics/tracing/index.md) a [používání trasování pro řešení potíží s aplikací](./diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).

## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření klienta](how-to-create-a-wcf-client.md)
- [Postupy: Přístup ke službám pomocí duplexního kontraktu](./feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Postupy: Asynchronní volání operací služby](./feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [Postupy: Přístup ke službám pomocí jednosměrných kontraktů a kontraktů žádost-odpověď](./feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [Postupy: Přístup ke službě WSE 3.0](./feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [Principy generovaného klientského kódu](./feature-details/understanding-generated-client-code.md)
- [Postupy: Vylepšení doby spouštění klientských aplikací WCF pomocí XmlSerializer](./feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
- [Nastavení chování klienta za běhu](specifying-client-run-time-behavior.md)
- [Konfigurace chování klienta](configuring-client-behaviors.md)
