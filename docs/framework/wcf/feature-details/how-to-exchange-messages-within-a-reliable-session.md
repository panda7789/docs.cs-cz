---
title: 'Postupy: Výměna zpráv ve spolehlivých relacích'
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: 5b01ddfd95db2f7e88f9481265c348f4f16fbbee
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579473"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a><span data-ttu-id="ef3e8-102">Postupy: Výměna zpráv ve spolehlivých relacích</span><span class="sxs-lookup"><span data-stu-id="ef3e8-102">How to: Exchange Messages Within a Reliable Session</span></span>

<span data-ttu-id="ef3e8-103">Toto téma popisuje kroky potřebné k povolení spolehlivé relace pomocí jedné z vazeb poskytovaných systémem, které podporují takovou relaci, ale nejsou ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="ef3e8-103">This topic outlines the steps required to enable a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="ef3e8-104">Spolehlivou relaci povolíte imperativně pomocí kódu nebo deklarativně v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="ef3e8-104">You enable a reliable session imperatively using code or declaratively in your configuration file.</span></span> <span data-ttu-id="ef3e8-105">Tento postup používá konfigurační soubory klienta a služby k povolení spolehlivé relace a k určení toho, že zprávy přicházejí ve stejném pořadí, v jakém byly odeslány.</span><span class="sxs-lookup"><span data-stu-id="ef3e8-105">This procedure uses the client and service configuration files to enable the reliable session and to stipulate that the messages arrive in the same order in which they were sent.</span></span>

<span data-ttu-id="ef3e8-106">Klíčovou částí tohoto postupu je, že element konfigurace koncového bodu obsahuje `bindingConfiguration` atribut, který odkazuje na konfiguraci vazby s názvem `Binding1` .</span><span class="sxs-lookup"><span data-stu-id="ef3e8-106">The key part of this procedure is that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="ef3e8-107">[**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)Element Configuration odkazuje na tento název, aby povoloval spolehlivé relace nastavením `enabled` atributu [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) elementu na `true` .</span><span class="sxs-lookup"><span data-stu-id="ef3e8-107">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) element to `true`.</span></span> <span data-ttu-id="ef3e8-108">Určete seřazené záruky doručení pro spolehlivou relaci nastavením `ordered` atributu na `true` .</span><span class="sxs-lookup"><span data-stu-id="ef3e8-108">You specify the ordered delivery assurances for the reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="ef3e8-109">Zdrojovou kopii tohoto příkladu najdete v tématu o [spolehlivé relaci WS](../samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="ef3e8-109">For the source copy of this example, see [WS Reliable Session](../samples/ws-reliable-session.md).</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="ef3e8-110">Konfigurace služby s WSHttpBinding pro použití spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="ef3e8-110">Configure the service with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="ef3e8-111">Definujte kontrakt služby pro typ služby.</span><span class="sxs-lookup"><span data-stu-id="ef3e8-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. <span data-ttu-id="ef3e8-112">Implementujte kontrakt služby ve třídě služby.</span><span class="sxs-lookup"><span data-stu-id="ef3e8-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="ef3e8-113">Všimněte si, že informace o adrese nebo vazbě nejsou určeny v rámci implementace služby.</span><span class="sxs-lookup"><span data-stu-id="ef3e8-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="ef3e8-114">Nemusíte psát kód, který načte adresu nebo informace o vazbě z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="ef3e8-114">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. <span data-ttu-id="ef3e8-115">Vytvořte soubor *Web. config* pro konfiguraci koncového bodu pro `CalculatorService` , který používá se <xref:System.ServiceModel.WSHttpBinding> zapnutou spolehlivou relací a objednání požadovaných zpráv.</span><span class="sxs-lookup"><span data-stu-id="ef3e8-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding> with reliable session enabled and ordered delivery of messages required.</span></span>

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. <span data-ttu-id="ef3e8-116">Vytvořte soubor *Service. svc* , který obsahuje řádek:</span><span class="sxs-lookup"><span data-stu-id="ef3e8-116">Create a *Service.svc* file that contains the line:</span></span>

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. <span data-ttu-id="ef3e8-117">Soubor *Service. svc* umístěte do virtuálního adresáře Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="ef3e8-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="ef3e8-118">Konfigurace klienta s WSHttpBinding pro použití spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="ef3e8-118">Configure the client with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="ef3e8-119">K vygenerování kódu z metadat služby použijte [Nástroj*Svcutil. exe*(ServiceModel Metadata Utility)](../servicemodel-metadata-utility-tool-svcutil-exe.md) z příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="ef3e8-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata:</span></span>

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="ef3e8-120">Vygenerovaný klient obsahuje `ICalculator` rozhraní, které definuje kontrakt služby, který musí implementace klienta splňovat.</span><span class="sxs-lookup"><span data-stu-id="ef3e8-120">The generated client contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. <span data-ttu-id="ef3e8-121">Vygenerovaná klientská aplikace také obsahuje implementaci `ClientCalculator` .</span><span class="sxs-lookup"><span data-stu-id="ef3e8-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="ef3e8-122">Všimněte si, že informace o adrese a vazbě nejsou určeny nikde v implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="ef3e8-122">Note that the address and binding information isn't specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="ef3e8-123">Nemusíte psát kód, který načte adresu nebo informace o vazbě z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="ef3e8-123">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. <span data-ttu-id="ef3e8-124">*Svcutil. exe* také generuje konfiguraci pro klienta, který používá <xref:System.ServiceModel.WSHttpBinding> třídu.</span><span class="sxs-lookup"><span data-stu-id="ef3e8-124">*Svcutil.exe* also generates the configuration for the client that uses the <xref:System.ServiceModel.WSHttpBinding> class.</span></span> <span data-ttu-id="ef3e8-125">Pojmenujte konfigurační soubor *App. config* při použití sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ef3e8-125">Name the configuration file *App.config* when using Visual Studio.</span></span>

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. <span data-ttu-id="ef3e8-126">Vytvořte instanci `ClientCalculator` v aplikaci a zavolejte operace služby.</span><span class="sxs-lookup"><span data-stu-id="ef3e8-126">Create an instance of the `ClientCalculator` in an application and call the service operations.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. <span data-ttu-id="ef3e8-127">Zkompilujte a spusťte klienta.</span><span class="sxs-lookup"><span data-stu-id="ef3e8-127">Compile and run the client.</span></span>

## <a name="example"></a><span data-ttu-id="ef3e8-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef3e8-128">Example</span></span>

<span data-ttu-id="ef3e8-129">Několik vazeb poskytovaných systémem podporuje ve výchozím nastavení spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="ef3e8-129">Several of the system-provided bindings support reliable sessions by default.</span></span> <span data-ttu-id="ef3e8-130">Zde jsou některé z nich:</span><span class="sxs-lookup"><span data-stu-id="ef3e8-130">These include:</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

<span data-ttu-id="ef3e8-131">Příklad vytvoření vlastní vazby, která podporuje spolehlivé relace, najdete v tématu [Postupy: Vytvoření vlastní vazby spolehlivé relace s protokolem HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md).</span><span class="sxs-lookup"><span data-stu-id="ef3e8-131">For an example of how to create a custom binding that supports reliable sessions, see [How to: Create a Custom Reliable Session Binding with HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ef3e8-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef3e8-132">See also</span></span>

- [<span data-ttu-id="ef3e8-133">Spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="ef3e8-133">Reliable Sessions</span></span>](reliable-sessions.md)
