---
title: 'Postupy: Výměna zpráv ve spolehlivých relacích'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ee558542eacede87ca29acf965491c965b6c4c63
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a><span data-ttu-id="43867-102">Postupy: Výměna zpráv ve spolehlivých relacích</span><span class="sxs-lookup"><span data-stu-id="43867-102">How to: Exchange Messages Within a Reliable Session</span></span>

<span data-ttu-id="43867-103">Toto téma popisuje kroky potřebné k povolení spolehlivé relace pomocí jedné vazby poskytované systémem, které podporují tyto relace, ale není ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="43867-103">This topic outlines the steps required to enable a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="43867-104">Povolit spolehlivé relace imperativní pomocí kódu nebo deklarativně v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="43867-104">You enable a reliable session imperatively using code or declaratively in your configuration file.</span></span> <span data-ttu-id="43867-105">Tento postup používá konfigurační soubory klienta a služby, povolte spolehlivé relace a stanovení, zda doručení zpráv ve stejném pořadí, ve které byly odeslány.</span><span class="sxs-lookup"><span data-stu-id="43867-105">This procedure uses the client and service configuration files to enable the reliable session and to stipulate that the messages arrive in the same order in which they were sent.</span></span>

<span data-ttu-id="43867-106">Část klíče tohoto postupu je, že element konfigurace koncového bodu obsahovat `bindingConfiguration` atribut, který odkazuje na vazbu konfigurace s názvem `Binding1`.</span><span class="sxs-lookup"><span data-stu-id="43867-106">The key part of this procedure is that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="43867-107">[  **\<Vazby >** ](../../../../docs/framework/misc/binding.md) konfigurační prvek odkazuje tento název pro nastavení Povolit spolehlivé relace `enabled` atribut [  **\<reliableSession >** ](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) element `true`.</span><span class="sxs-lookup"><span data-stu-id="43867-107">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) element to `true`.</span></span> <span data-ttu-id="43867-108">Zadejte záruky doručení pro spolehlivé relace nastavením `ordered` atribut `true`.</span><span class="sxs-lookup"><span data-stu-id="43867-108">You specify the ordered delivery assurances for the reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="43867-109">Zdroj kopírování tohoto příkladu, najdete v části [spolehlivá relace WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="43867-109">For the source copy of this example, see [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="43867-110">Konfigurovat službu s WSHttpBinding používat spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="43867-110">Configure the service with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="43867-111">Definování kontraktu služby pro typ služby.</span><span class="sxs-lookup"><span data-stu-id="43867-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. <span data-ttu-id="43867-112">Implementujte kontrakt služby v třídě služby.</span><span class="sxs-lookup"><span data-stu-id="43867-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="43867-113">Všimněte si, že není adresu nebo vazba informace zadat v rámci implementace služby.</span><span class="sxs-lookup"><span data-stu-id="43867-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="43867-114">Budete se muset napsat kód pro načtení informací informace adresu nebo vazbu z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="43867-114">You aren't required to write code to retrieve the address or binding information information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. <span data-ttu-id="43867-115">Vytvoření *Web.config* soubor konfigurace koncového bodu `CalculatorService` používající <xref:System.ServiceModel.WSHttpBinding> s spolehlivé relace povolen a seřazené doručení zpráv, které jsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="43867-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding> with reliable session enabled and ordered delivery of messages required.</span></span>

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. <span data-ttu-id="43867-116">Vytvoření *Service.svc* soubor, který obsahuje na řádku:</span><span class="sxs-lookup"><span data-stu-id="43867-116">Create a *Service.svc* file that contains the line:</span></span>

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1.  <span data-ttu-id="43867-117">Místo *Service.svc* souboru v virtuálního adresáře Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="43867-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="43867-118">Konfigurace klienta s WSHttpBinding používat spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="43867-118">Configure the client with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="43867-119">Použití [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z příkazového řádku pro generování kódu z metadat služby:</span><span class="sxs-lookup"><span data-stu-id="43867-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata:</span></span>

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="43867-120">Obsahuje generovaného klienta `ICalculator` rozhraní, které definuje kontrakt služby, které musí splňovat implementace klienta.</span><span class="sxs-lookup"><span data-stu-id="43867-120">The generated client contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. <span data-ttu-id="43867-121">Generovaného klienta aplikace také obsahuje implementace `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="43867-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="43867-122">Všimněte si, že informace o adrese a vazba není zadán kdekoli uvnitř implementace služby.</span><span class="sxs-lookup"><span data-stu-id="43867-122">Note that the address and binding information isn't specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="43867-123">Budete se muset napsat kód pro načtení informací informace adresu nebo vazbu z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="43867-123">You aren't required to write code to retrieve the address or binding information information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. <span data-ttu-id="43867-124">*Svcutil.exe* také generuje konfiguraci pro klienta, který používá <xref:System.ServiceModel.WSHttpBinding> třídy.</span><span class="sxs-lookup"><span data-stu-id="43867-124">*Svcutil.exe* also generates the configuration for the client that uses the <xref:System.ServiceModel.WSHttpBinding> class.</span></span> <span data-ttu-id="43867-125">Název konfiguračního souboru *App.config* když pomocí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="43867-125">Name the configuration file *App.config* when using Visual Studio.</span></span>

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. <span data-ttu-id="43867-126">Vytvoření instance `ClientCalculator` v aplikaci a volání operací služby.</span><span class="sxs-lookup"><span data-stu-id="43867-126">Create an instance of the `ClientCalculator` in an application and call the service operations.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. <span data-ttu-id="43867-127">Zkompilování a spuštění klienta.</span><span class="sxs-lookup"><span data-stu-id="43867-127">Compile and run the client.</span></span>

## <a name="example"></a><span data-ttu-id="43867-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="43867-128">Example</span></span>

<span data-ttu-id="43867-129">Několik vazeb poskytovaných systémem podporují spolehlivé relace ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="43867-129">Several of the system-provided bindings support reliable sessions by default.</span></span> <span data-ttu-id="43867-130">Mezi ně patří:</span><span class="sxs-lookup"><span data-stu-id="43867-130">These include:</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

<span data-ttu-id="43867-131">Příklad vytvoření vlastní vazby, která podporuje spolehlivé relace, naleznete v části [postupy: vytvoření vlastní vazby spolehlivé relace s protokolem HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).</span><span class="sxs-lookup"><span data-stu-id="43867-131">For an example of how to create a custom binding that supports reliable sessions, see [How to: Create a Custom Reliable Session Binding with HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="43867-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="43867-132">See also</span></span>

[<span data-ttu-id="43867-133">Spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="43867-133">Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
