---
title: "Postupy: vytvoření vazby vlastní spolehlivé relace s protokolem HTTPS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6e891f266a8159a6367a0a936d6ba11197484267
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a><span data-ttu-id="03442-102">Postupy: vytvoření vazby vlastní spolehlivé relace s protokolem HTTPS</span><span class="sxs-lookup"><span data-stu-id="03442-102">How to: Create a Custom Reliable Session Binding with HTTPS</span></span>

<span data-ttu-id="03442-103">Toto téma ukazuje použití Secure Sockets Layer (SSL) zabezpečení přenosu s spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="03442-103">This topic demonstrates the use of Secure Sockets Layer (SSL) transport security with reliable sessions.</span></span> <span data-ttu-id="03442-104">Pokud chcete používat spolehlivé relace přes protokol HTTPS, musíte vytvořit vlastní vazby, které používá spolehlivé relace a přenos HTTPS.</span><span class="sxs-lookup"><span data-stu-id="03442-104">To use a reliable session over HTTPS, you must create a custom binding that uses a reliable session and the HTTPS transport.</span></span> <span data-ttu-id="03442-105">Spolehlivá relace povolíte imperativní pomocí kódu nebo deklarativně v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="03442-105">You enable the reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="03442-106">Tento postup používá konfigurační soubory, které klient a služba umožňující spolehlivé relace a [  **\<httpsTransport >** ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) element.</span><span class="sxs-lookup"><span data-stu-id="03442-106">This procedure uses the client and service configuration files to enable the reliable session and the [**\<httpsTransport>**](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) element.</span></span>

<span data-ttu-id="03442-107">Část klíče tohoto postupu je, že  **\<endpoint >** konfigurace element obsahovat `bindingConfiguration` atribut, který odkazuje na vlastní vazby konfigurace s názvem `reliableSessionOverHttps`.</span><span class="sxs-lookup"><span data-stu-id="03442-107">The key part of this procedure is that the **\<endpoint>** configuration element contain a `bindingConfiguration` attribute that references a custom binding configuration named `reliableSessionOverHttps`.</span></span> <span data-ttu-id="03442-108">[  **\<Vazby >** ](../../../../docs/framework/misc/binding.md) konfigurační prvek odkazuje tento název zadat, že jsou používány spolehlivé relace a přenos HTTPS včetně  **\< reliableSession >** a  **\<httpsTransport >** elementy.</span><span class="sxs-lookup"><span data-stu-id="03442-108">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element references this name to specify that a reliable session and the HTTPS transport are used by including **\<reliableSession>** and **\<httpsTransport>** elements.</span></span>

<span data-ttu-id="03442-109">Zdroj kopírování tohoto příkladu, najdete v části [vlastní vazby spolehlivé relace HTTPS](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).</span><span class="sxs-lookup"><span data-stu-id="03442-109">For the source copy of this example, see [Custom Binding Reliable Session over HTTPS](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).</span></span>

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="03442-110">Konfigurovat službu s CustomBinding používat spolehlivé relace s protokolem HTTPS</span><span class="sxs-lookup"><span data-stu-id="03442-110">Configure the service with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="03442-111">Definování kontraktu služby pro typ služby.</span><span class="sxs-lookup"><span data-stu-id="03442-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. <span data-ttu-id="03442-112">Implementujte kontrakt služby v třídě služby.</span><span class="sxs-lookup"><span data-stu-id="03442-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="03442-113">Všimněte si, že není adresu nebo vazba informace zadat v rámci implementace služby.</span><span class="sxs-lookup"><span data-stu-id="03442-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="03442-114">Budete se muset napsat kód pro načtení informací adresu nebo vazbu z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="03442-114">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. <span data-ttu-id="03442-115">Vytvoření *Web.config* soubor konfigurace koncového bodu `CalculatorService` s vlastní vazby s názvem `reliableSessionOverHttps` používající spolehlivé relace a přenos HTTPS.</span><span class="sxs-lookup"><span data-stu-id="03442-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` with a custom binding named `reliableSessionOverHttps` that uses a reliable session and the HTTPS transport.</span></span>

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. <span data-ttu-id="03442-116">Vytvoření *Service.svc* soubor, který obsahuje na řádku:</span><span class="sxs-lookup"><span data-stu-id="03442-116">Create a *Service.svc* file that contains the line:</span></span>

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. <span data-ttu-id="03442-117">Místo *Service.svc* souboru v virtuálního adresáře Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="03442-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="03442-118">Konfigurace klienta s CustomBinding používat spolehlivé relace s protokolem HTTPS</span><span class="sxs-lookup"><span data-stu-id="03442-118">Configure the client with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="03442-119">Použití [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z příkazového řádku pro generování kódu z metadat služby.</span><span class="sxs-lookup"><span data-stu-id="03442-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="03442-120">Obsahuje klienta, který se generuje `ICalculator` rozhraní, které definuje kontrakt služby, které musí splňovat implementace klienta.</span><span class="sxs-lookup"><span data-stu-id="03442-120">The client that's generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. <span data-ttu-id="03442-121">Generovaného klienta aplikace také obsahuje implementace `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="03442-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="03442-122">Všimněte si, že není zadat informace o adrese a vazbu v rámci implementace služby.</span><span class="sxs-lookup"><span data-stu-id="03442-122">Note that the address and binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="03442-123">Budete se muset napsat kód pro načtení informací adresu a vazbu z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="03442-123">You aren't required to write code to retrieve the address and binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. <span data-ttu-id="03442-124">Konfigurace vlastní vazby s názvem `reliableSessionOverHttps` pro přenos HTTPS a spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="03442-124">Configure a custom binding named `reliableSessionOverHttps` to use the HTTPS transport and reliable sessions.</span></span>

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. <span data-ttu-id="03442-125">Vytvoření instance `ClientCalculator` v aplikaci a pak volání operací služby.</span><span class="sxs-lookup"><span data-stu-id="03442-125">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. <span data-ttu-id="03442-126">Zkompilování a spuštění klienta.</span><span class="sxs-lookup"><span data-stu-id="03442-126">Compile and run the client.</span></span>  

## <a name="net-framework-security"></a><span data-ttu-id="03442-127">zabezpečení v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="03442-127">.NET Framework security</span></span>

<span data-ttu-id="03442-128">Vzhledem k tomu, že certifikát použitý v této ukázce je testovací certifikát vytvořen s *Makecert.exe*, při pokusu o přístupu, jako například adresou protokolu HTTPS se zobrazí výstraha zabezpečení `https://localhost/servicemodelsamples/service.svc`, z prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="03442-128">Because the certificate used in this sample is a test certificate created with *Makecert.exe*, a security alert appears when you try to access an HTTPS address, such as `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="03442-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="03442-129">See also</span></span>

[<span data-ttu-id="03442-130">Spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="03442-130">Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
