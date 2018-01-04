---
title: "Konfigurace hodnot časových limitů u vazby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 164b4e3bff3e327b82c78c403a0e65ec8db744ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-timeout-values-on-a-binding"></a><span data-ttu-id="c206d-102">Konfigurace hodnot časových limitů u vazby</span><span class="sxs-lookup"><span data-stu-id="c206d-102">Configuring Timeout Values on a Binding</span></span>
<span data-ttu-id="c206d-103">Nejsou k dispozici v vazby WCF několik nastavení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="c206d-103">There are a number of timeout settings available in WCF bindings.</span></span> <span data-ttu-id="c206d-104">Nastavení těchto časový limit nastavení správně může zlepšit pouze vaší služby výkon, ale také play roli v použitelnost a zabezpečení vaší služby.</span><span class="sxs-lookup"><span data-stu-id="c206d-104">Setting these timeout settings correctly can improve not only your service’s performance but also play a role in the usability and security of your service.</span></span> <span data-ttu-id="c206d-105">Následující časové limity jsou k dispozici na vazby WCF:</span><span class="sxs-lookup"><span data-stu-id="c206d-105">The following timeouts are available on WCF bindings:</span></span>  
  
1.  <span data-ttu-id="c206d-106">openTimeout</span><span class="sxs-lookup"><span data-stu-id="c206d-106">OpenTimeout</span></span>  
  
2.  <span data-ttu-id="c206d-107">Intervalu</span><span class="sxs-lookup"><span data-stu-id="c206d-107">CloseTimeout</span></span>  
  
3.  <span data-ttu-id="c206d-108">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="c206d-108">SendTimeout</span></span>  
  
4.  <span data-ttu-id="c206d-109">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="c206d-109">ReceiveTimeout</span></span>  
  
## <a name="wcf-binding-timeouts"></a><span data-ttu-id="c206d-110">Časové limity vazby WCF</span><span class="sxs-lookup"><span data-stu-id="c206d-110">WCF Binding Timeouts</span></span>  
 <span data-ttu-id="c206d-111">Každé nastavení popsané v tomto tématu jsou probíhají vazby samostatně, buď v kódu nebo konfigurace.</span><span class="sxs-lookup"><span data-stu-id="c206d-111">Each of the settings discussed in this topic are made on the binding itself, either in code or configuration.</span></span> <span data-ttu-id="c206d-112">Následující kód ukazuje, jak programového nastavení časových limitů u vazby WCF v kontextu služba s vlastním hostováním.</span><span class="sxs-lookup"><span data-stu-id="c206d-112">The following code shows how to programmatically set timeouts on a WCF binding in the context of a self-hosted service.</span></span>  
  
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
  
 <span data-ttu-id="c206d-113">Následující příklad ukazuje, jak nakonfigurovat vypršení časových limitů u vazby v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="c206d-113">The following example shows how to configure timeouts on a binding in a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="c206d-114">Další informace o těchto nastaveních naleznete v dokumentaci k <xref:System.ServiceModel.Channels.Binding> třídy.</span><span class="sxs-lookup"><span data-stu-id="c206d-114">More information about these settings can be found in the documentation for the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
### <a name="client-side-timeouts"></a><span data-ttu-id="c206d-115">Časové limity straně klienta</span><span class="sxs-lookup"><span data-stu-id="c206d-115">Client-side Timeouts</span></span>  
 <span data-ttu-id="c206d-116">Na straně klienta:</span><span class="sxs-lookup"><span data-stu-id="c206d-116">On the client side:</span></span>  
  
1.  <span data-ttu-id="c206d-117">SendTimeout – použitý k inicializaci OperationTimeout, jimiž se řídí celý proces odesílání zprávy, včetně přijímání zprávy odpovědi pro požadavek nebo odpověď operace služby.</span><span class="sxs-lookup"><span data-stu-id="c206d-117">SendTimeout – used to initialize the OperationTimeout, which governs the whole process of sending a message, including receiving a reply message for a request/reply service operation.</span></span> <span data-ttu-id="c206d-118">Tento časový limit platí také při odesílání zprávy odpovědi z kontrakt metody zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="c206d-118">This timeout also applies when sending reply messages from a callback contract method.</span></span>  
  
2.  <span data-ttu-id="c206d-119">OpenTimeout – použít při otevírání kanály, když není zadaná žádná hodnota explicitní vypršení časového limitu</span><span class="sxs-lookup"><span data-stu-id="c206d-119">OpenTimeout – used when opening channels when no explicit timeout value is specified</span></span>  
  
3.  <span data-ttu-id="c206d-120">Intervalu – použít při zavření kanály, když není zadaná žádná hodnota explicitní vypršení časového limitu</span><span class="sxs-lookup"><span data-stu-id="c206d-120">CloseTimeout – used when closing channels when no explicit timeout value is specified</span></span>  
  
4.  <span data-ttu-id="c206d-121">ReceiveTimeout – se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="c206d-121">ReceiveTimeout – is not used</span></span>  
  
### <a name="service-side-timeouts"></a><span data-ttu-id="c206d-122">Časové limity straně služby</span><span class="sxs-lookup"><span data-stu-id="c206d-122">Service-side Timeouts</span></span>  
 <span data-ttu-id="c206d-123">Na straně služby:</span><span class="sxs-lookup"><span data-stu-id="c206d-123">On the service side:</span></span>  
  
1.  <span data-ttu-id="c206d-124">SendTimeout, OpentTimeout, intervalu jsou stejné jako na straně klienta</span><span class="sxs-lookup"><span data-stu-id="c206d-124">SendTimeout, OpentTimeout, CloseTimeout are the same as on the client</span></span>  
  
2.  <span data-ttu-id="c206d-125">ReceiveTimeout – vrstvou Framework služby použitý k inicializaci časový limit nečinnosti relace, který řídí, jak dlouho může být relace před vypršením časového limitu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="c206d-125">ReceiveTimeout – used by the Service Framework Layer to initialize the session-idle timeout which controls how long a session can be idle before timing out.</span></span>
