---
title: Konfigurace hodnot časových limitů u vazby
description: Naučte se spravovat nastavení časových limitů pro vazby WCF za účelem zvýšení výkonu, použitelnosti a zabezpečení vaší služby.
ms.date: 03/30/2017
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
ms.openlocfilehash: c41824a242d9b42290183cd70b9acf5b8ee59e6b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245112"
---
# <a name="configuring-timeout-values-on-a-binding"></a><span data-ttu-id="8e22f-103">Konfigurace hodnot časových limitů u vazby</span><span class="sxs-lookup"><span data-stu-id="8e22f-103">Configuring Timeout Values on a Binding</span></span>
<span data-ttu-id="8e22f-104">V vazbách WCF je dostupných několik nastavení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="8e22f-104">There are a number of timeout settings available in WCF bindings.</span></span> <span data-ttu-id="8e22f-105">Nastavení těchto nastavení časového limitu může správně zlepšit nejen výkon služby, ale také hrát roli v oblasti použitelnosti a zabezpečení vaší služby.</span><span class="sxs-lookup"><span data-stu-id="8e22f-105">Setting these timeout settings correctly can improve not only your service’s performance but also play a role in the usability and security of your service.</span></span> <span data-ttu-id="8e22f-106">V vazbách WCF jsou k dispozici následující časové limity:</span><span class="sxs-lookup"><span data-stu-id="8e22f-106">The following timeouts are available on WCF bindings:</span></span>  
  
1. <span data-ttu-id="8e22f-107">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="8e22f-107">OpenTimeout</span></span>  
  
2. <span data-ttu-id="8e22f-108">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="8e22f-108">CloseTimeout</span></span>  
  
3. <span data-ttu-id="8e22f-109">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="8e22f-109">SendTimeout</span></span>  
  
4. <span data-ttu-id="8e22f-110">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="8e22f-110">ReceiveTimeout</span></span>  
  
## <a name="wcf-binding-timeouts"></a><span data-ttu-id="8e22f-111">Vypršení časových limitů vazeb WCF</span><span class="sxs-lookup"><span data-stu-id="8e22f-111">WCF Binding Timeouts</span></span>  
 <span data-ttu-id="8e22f-112">Každé nastavení popsané v tomto tématu se provádí na samotné vazbě, a to buď v kódu, nebo v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="8e22f-112">Each of the settings discussed in this topic are made on the binding itself, either in code or configuration.</span></span> <span data-ttu-id="8e22f-113">Následující kód ukazuje, jak programově nastavit vypršení časových limitů u vazby WCF v kontextu samoobslužné služby.</span><span class="sxs-lookup"><span data-stu-id="8e22f-113">The following code shows how to programmatically set timeouts on a WCF binding in the context of a self-hosted service.</span></span>  
  
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
  
 <span data-ttu-id="8e22f-114">Následující příklad ukazuje způsob konfigurace časových limitů u vazby v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="8e22f-114">The following example shows how to configure timeouts on a binding in a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="8e22f-115">Další informace o těchto nastaveních najdete v dokumentaci pro <xref:System.ServiceModel.Channels.Binding> třídu.</span><span class="sxs-lookup"><span data-stu-id="8e22f-115">More information about these settings can be found in the documentation for the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
### <a name="client-side-timeouts"></a><span data-ttu-id="8e22f-116">Vypršení časových limitů na straně klienta</span><span class="sxs-lookup"><span data-stu-id="8e22f-116">Client-side Timeouts</span></span>  
 <span data-ttu-id="8e22f-117">Na straně klienta:</span><span class="sxs-lookup"><span data-stu-id="8e22f-117">On the client side:</span></span>  
  
1. <span data-ttu-id="8e22f-118">SendTimeout – slouží k inicializaci OperationTimeout, který řídí celý proces odeslání zprávy, včetně přijetí zprávy odpovědi pro operaci služby žádosti a odpověď.</span><span class="sxs-lookup"><span data-stu-id="8e22f-118">SendTimeout – used to initialize the OperationTimeout, which governs the whole process of sending a message, including receiving a reply message for a request/reply service operation.</span></span> <span data-ttu-id="8e22f-119">Tento časový limit platí i při posílání odpovědí na zprávy z metody kontraktu zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="8e22f-119">This timeout also applies when sending reply messages from a callback contract method.</span></span>  
  
2. <span data-ttu-id="8e22f-120">OpenTimeout – používá se při otevírání kanálů, když není zadaná žádná explicitní hodnota časového limitu.</span><span class="sxs-lookup"><span data-stu-id="8e22f-120">OpenTimeout – used when opening channels when no explicit timeout value is specified.</span></span>  
  
3. <span data-ttu-id="8e22f-121">CloseTimeout – používá se při zavírání kanálů, když není zadaná žádná explicitní hodnota časového limitu.</span><span class="sxs-lookup"><span data-stu-id="8e22f-121">CloseTimeout – used when closing channels when no explicit timeout value is specified.</span></span>  
  
4. <span data-ttu-id="8e22f-122">ReceiveTimeout – se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="8e22f-122">ReceiveTimeout – is not used.</span></span>  
  
### <a name="service-side-timeouts"></a><span data-ttu-id="8e22f-123">Vypršení časových limitů na straně služby</span><span class="sxs-lookup"><span data-stu-id="8e22f-123">Service-side Timeouts</span></span>  
 <span data-ttu-id="8e22f-124">Na straně služby:</span><span class="sxs-lookup"><span data-stu-id="8e22f-124">On the service side:</span></span>  
  
1. <span data-ttu-id="8e22f-125">SendTimeout, OpenTimeout, CloseTimeout jsou stejné jako u klienta.</span><span class="sxs-lookup"><span data-stu-id="8e22f-125">SendTimeout, OpenTimeout, CloseTimeout are the same as on the client.</span></span>  
  
2. <span data-ttu-id="8e22f-126">ReceiveTimeout – používá se vrstvou rozhraní služby k inicializaci časového limitu nečinnosti relace, který určuje, jak dlouho může být relace nečinná, než vyprší časový limit.</span><span class="sxs-lookup"><span data-stu-id="8e22f-126">ReceiveTimeout – used by the Service Framework Layer to initialize the session-idle timeout which controls how long a session can be idle before timing out.</span></span>
