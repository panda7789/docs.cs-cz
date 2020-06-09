---
title: 'Postupy: Vytvoření vlastní vazby pro spolehlivou relaci s HTTPS'
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: 70f8f4f33626ab0d1705e03750bfd9baa324e60a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598993"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a><span data-ttu-id="c3177-102">Postupy: Vytvoření vlastní vazby pro spolehlivou relaci s HTTPS</span><span class="sxs-lookup"><span data-stu-id="c3177-102">How to: Create a Custom Reliable Session Binding with HTTPS</span></span>

<span data-ttu-id="c3177-103">Toto téma ukazuje použití zabezpečení přenosu SSL (Secure Sockets Layer) (SSL) u spolehlivých relací.</span><span class="sxs-lookup"><span data-stu-id="c3177-103">This topic demonstrates the use of Secure Sockets Layer (SSL) transport security with reliable sessions.</span></span> <span data-ttu-id="c3177-104">Pokud chcete používat spolehlivou relaci přes protokol HTTPS, musíte vytvořit vlastní vazbu, která používá spolehlivou relaci a přenos HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c3177-104">To use a reliable session over HTTPS, you must create a custom binding that uses a reliable session and the HTTPS transport.</span></span> <span data-ttu-id="c3177-105">Spolehlivou relaci povolíte buď imperativně, a to pomocí kódu nebo deklarativního v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="c3177-105">You enable the reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="c3177-106">Tento postup používá konfigurační soubory klienta a služby k povolení spolehlivé relace a [**\<httpsTransport>**](../../configure-apps/file-schema/wcf/httpstransport.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="c3177-106">This procedure uses the client and service configuration files to enable the reliable session and the [**\<httpsTransport>**](../../configure-apps/file-schema/wcf/httpstransport.md) element.</span></span>

<span data-ttu-id="c3177-107">Klíčovou částí tohoto postupu je, že **\<endpoint>** element Configuration obsahuje `bindingConfiguration` atribut, který odkazuje na vlastní konfiguraci vazby s názvem `reliableSessionOverHttps` .</span><span class="sxs-lookup"><span data-stu-id="c3177-107">The key part of this procedure is that the **\<endpoint>** configuration element contain a `bindingConfiguration` attribute that references a custom binding configuration named `reliableSessionOverHttps`.</span></span> <span data-ttu-id="c3177-108">[**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)Element Configuration odkazuje na tento název a určí, že se bude používat Spolehlivá relace a přenos HTTPS, a to včetně **\<reliableSession>** **\<httpsTransport>** prvků a.</span><span class="sxs-lookup"><span data-stu-id="c3177-108">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element references this name to specify that a reliable session and the HTTPS transport are used by including **\<reliableSession>** and **\<httpsTransport>** elements.</span></span>

<span data-ttu-id="c3177-109">Pro zdrojovou kopii tohoto příkladu si přečtěte téma [vlastní vázání spolehlivé relace přes HTTPS](../samples/custom-binding-reliable-session-over-https.md).</span><span class="sxs-lookup"><span data-stu-id="c3177-109">For the source copy of this example, see [Custom Binding Reliable Session over HTTPS](../samples/custom-binding-reliable-session-over-https.md).</span></span>

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="c3177-110">Konfigurace služby s CustomBinding pro použití spolehlivé relace s protokolem HTTPS</span><span class="sxs-lookup"><span data-stu-id="c3177-110">Configure the service with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="c3177-111">Definujte kontrakt služby pro typ služby.</span><span class="sxs-lookup"><span data-stu-id="c3177-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. <span data-ttu-id="c3177-112">Implementujte kontrakt služby ve třídě služby.</span><span class="sxs-lookup"><span data-stu-id="c3177-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="c3177-113">Všimněte si, že informace o adrese nebo vazbě nejsou určeny v rámci implementace služby.</span><span class="sxs-lookup"><span data-stu-id="c3177-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="c3177-114">Nemusíte psát kód, který načte adresu nebo informace o vazbě z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="c3177-114">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. <span data-ttu-id="c3177-115">Vytvořte soubor *Web. config* pro konfiguraci koncového bodu `CalculatorService` s vlastní vazbou s názvem `reliableSessionOverHttps` , který používá spolehlivou relaci a přenos HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c3177-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` with a custom binding named `reliableSessionOverHttps` that uses a reliable session and the HTTPS transport.</span></span>

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. <span data-ttu-id="c3177-116">Vytvořte soubor *Service. svc* , který obsahuje řádek:</span><span class="sxs-lookup"><span data-stu-id="c3177-116">Create a *Service.svc* file that contains the line:</span></span>

   `<%@ServiceHost language=c# Service="CalculatorService" %>`

1. <span data-ttu-id="c3177-117">Soubor *Service. svc* umístěte do virtuálního adresáře Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="c3177-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="c3177-118">Konfigurace klienta s CustomBinding pro použití spolehlivé relace s protokolem HTTPS</span><span class="sxs-lookup"><span data-stu-id="c3177-118">Configure the client with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="c3177-119">K vygenerování kódu z metadat služby použijte [Nástroj*Svcutil. exe*(ServiceModel Metadata Utility)](../servicemodel-metadata-utility-tool-svcutil-exe.md) z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="c3177-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="c3177-120">Generovaný klient obsahuje `ICalculator` rozhraní, které definuje kontrakt služby, který musí implementace klienta splňovat.</span><span class="sxs-lookup"><span data-stu-id="c3177-120">The client that's generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. <span data-ttu-id="c3177-121">Vygenerovaná klientská aplikace také obsahuje implementaci `ClientCalculator` .</span><span class="sxs-lookup"><span data-stu-id="c3177-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="c3177-122">Všimněte si, že informace o adrese a vazbě nejsou určeny v rámci implementace služby.</span><span class="sxs-lookup"><span data-stu-id="c3177-122">Note that the address and binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="c3177-123">Nemusíte psát kód, který načte adresu a informace o vazbě z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="c3177-123">You aren't required to write code to retrieve the address and binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. <span data-ttu-id="c3177-124">Nakonfigurujte vlastní vazbu s názvem `reliableSessionOverHttps` tak, aby používala přenos HTTPS a spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="c3177-124">Configure a custom binding named `reliableSessionOverHttps` to use the HTTPS transport and reliable sessions.</span></span>

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. <span data-ttu-id="c3177-125">Vytvořte instanci `ClientCalculator` v aplikaci a potom zavolejte operace služby.</span><span class="sxs-lookup"><span data-stu-id="c3177-125">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. <span data-ttu-id="c3177-126">Zkompilujte a spusťte klienta.</span><span class="sxs-lookup"><span data-stu-id="c3177-126">Compile and run the client.</span></span>  

## <a name="net-framework-security"></a><span data-ttu-id="c3177-127">zabezpečení v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c3177-127">.NET Framework security</span></span>

<span data-ttu-id="c3177-128">Vzhledem k tomu, že certifikát použitý v této ukázce je testovací certifikát vytvořený pomocí nástroje *Makecert. exe*, zobrazí se výstraha zabezpečení při pokusu o přístup k adrese https, jako `https://localhost/servicemodelsamples/service.svc` je například, z prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="c3177-128">Because the certificate used in this sample is a test certificate created with *Makecert.exe*, a security alert appears when you try to access an HTTPS address, such as `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3177-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3177-129">See also</span></span>

- [<span data-ttu-id="c3177-130">Spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="c3177-130">Reliable Sessions</span></span>](reliable-sessions.md)
