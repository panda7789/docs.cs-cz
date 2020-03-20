---
title: Konfigurace hodnot časových limitů u vazby
ms.date: 03/30/2017
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
ms.openlocfilehash: 968e80bbd4b50d72d089a325f8e3fe498de2eac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185289"
---
# <a name="configuring-timeout-values-on-a-binding"></a><span data-ttu-id="f2648-102">Konfigurace hodnot časových limitů u vazby</span><span class="sxs-lookup"><span data-stu-id="f2648-102">Configuring Timeout Values on a Binding</span></span>
<span data-ttu-id="f2648-103">Existuje několik nastavení časového času k dispozici ve vazbách WCF.</span><span class="sxs-lookup"><span data-stu-id="f2648-103">There are a number of timeout settings available in WCF bindings.</span></span> <span data-ttu-id="f2648-104">Správné nastavení časového času může zlepšit nejen výkon služby, ale také hrát roli v použitelnosti a zabezpečení vaší služby.</span><span class="sxs-lookup"><span data-stu-id="f2648-104">Setting these timeout settings correctly can improve not only your service’s performance but also play a role in the usability and security of your service.</span></span> <span data-ttu-id="f2648-105">Následující časové osy jsou k dispozici na WCF vazby:</span><span class="sxs-lookup"><span data-stu-id="f2648-105">The following timeouts are available on WCF bindings:</span></span>  
  
1. <span data-ttu-id="f2648-106">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="f2648-106">OpenTimeout</span></span>  
  
2. <span data-ttu-id="f2648-107">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="f2648-107">CloseTimeout</span></span>  
  
3. <span data-ttu-id="f2648-108">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="f2648-108">SendTimeout</span></span>  
  
4. <span data-ttu-id="f2648-109">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="f2648-109">ReceiveTimeout</span></span>  
  
## <a name="wcf-binding-timeouts"></a><span data-ttu-id="f2648-110">Časové osy vazby WCF</span><span class="sxs-lookup"><span data-stu-id="f2648-110">WCF Binding Timeouts</span></span>  
 <span data-ttu-id="f2648-111">Každé z nastavení popsaných v tomto tématu jsou provedeny na vazbě sám, a to buď v kódu nebo konfigurace.</span><span class="sxs-lookup"><span data-stu-id="f2648-111">Each of the settings discussed in this topic are made on the binding itself, either in code or configuration.</span></span> <span data-ttu-id="f2648-112">Následující kód ukazuje, jak programově nastavit časové toky na vazbě WCF v kontextu samoobslužné služby.</span><span class="sxs-lookup"><span data-stu-id="f2648-112">The following code shows how to programmatically set timeouts on a WCF binding in the context of a self-hosted service.</span></span>  
  
```csharp  
public static void Main()
{
    Uri baseAddress = new Uri("http://localhost/MyServer/MyService");

    try
    {
        ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService));

        WSHttpBinding binding = new WSHttpBinding();
        binding.OpenTimeout = new TimeSpan(0, 10, 0);
        binding.CloseTimeout = new TimeSpan(0, 10, 0);
        binding.SendTimeout = new TimeSpan(0, 10, 0);
        binding.ReceiveTimeout = new TimeSpan(0, 10, 0);

        serviceHost.AddServiceEndpoint("ICalculator", binding, baseAddress);
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();
    }
    catch (CommunicationException ex)
    {
        // Handle exception ...
    }
}
```  
  
 <span data-ttu-id="f2648-113">Následující příklad ukazuje, jak nakonfigurovat časové toky na vazbě v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="f2648-113">The following example shows how to configure timeouts on a binding in a configuration file.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding openTimeout="00:10:00"
                 closeTimeout="00:10:00"
                 sendTimeout="00:10:00"
                 receiveTimeout="00:10:00">
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```  
  
 <span data-ttu-id="f2648-114">Další informace o těchto nastaveních naleznete <xref:System.ServiceModel.Channels.Binding> v dokumentaci pro třídu.</span><span class="sxs-lookup"><span data-stu-id="f2648-114">More information about these settings can be found in the documentation for the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
### <a name="client-side-timeouts"></a><span data-ttu-id="f2648-115">Časové opozí na straně klienta</span><span class="sxs-lookup"><span data-stu-id="f2648-115">Client-side Timeouts</span></span>  
 <span data-ttu-id="f2648-116">Na straně klienta:</span><span class="sxs-lookup"><span data-stu-id="f2648-116">On the client side:</span></span>  
  
1. <span data-ttu-id="f2648-117">SendTimeout – slouží k inicializaci OperationTimeout, který řídí celý proces odesílání zprávy, včetně přijetí odpovědi na operaci služby požadavek/odpověď.</span><span class="sxs-lookup"><span data-stu-id="f2648-117">SendTimeout – used to initialize the OperationTimeout, which governs the whole process of sending a message, including receiving a reply message for a request/reply service operation.</span></span> <span data-ttu-id="f2648-118">Tento časový opova platí také při odesílání odpovědí z metody smlouvy zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="f2648-118">This timeout also applies when sending reply messages from a callback contract method.</span></span>  
  
2. <span data-ttu-id="f2648-119">OpenTimeout – používá se při otevírání kanálů, když není zadána žádná explicitní hodnota časového času.</span><span class="sxs-lookup"><span data-stu-id="f2648-119">OpenTimeout – used when opening channels when no explicit timeout value is specified.</span></span>  
  
3. <span data-ttu-id="f2648-120">CloseTimeout – používá se při zavírání kanálů, když není zadána žádná explicitní hodnota časového času.</span><span class="sxs-lookup"><span data-stu-id="f2648-120">CloseTimeout – used when closing channels when no explicit timeout value is specified.</span></span>  
  
4. <span data-ttu-id="f2648-121">ReceiveTimeout – se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="f2648-121">ReceiveTimeout – is not used.</span></span>  
  
### <a name="service-side-timeouts"></a><span data-ttu-id="f2648-122">Časové výtažky na straně služby</span><span class="sxs-lookup"><span data-stu-id="f2648-122">Service-side Timeouts</span></span>  
 <span data-ttu-id="f2648-123">Na straně služby:</span><span class="sxs-lookup"><span data-stu-id="f2648-123">On the service side:</span></span>  
  
1. <span data-ttu-id="f2648-124">SendTimeout, OpenTimeout, CloseTimeout jsou stejné jako na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="f2648-124">SendTimeout, OpenTimeout, CloseTimeout are the same as on the client.</span></span>  
  
2. <span data-ttu-id="f2648-125">ReceiveTimeout – používá vrstva rozhraní služby k inicializaci relace nečinnosti časový limit, který určuje, jak dlouho relace může být nečinný před vypršením časového limitu.</span><span class="sxs-lookup"><span data-stu-id="f2648-125">ReceiveTimeout – used by the Service Framework Layer to initialize the session-idle timeout which controls how long a session can be idle before timing out.</span></span>
