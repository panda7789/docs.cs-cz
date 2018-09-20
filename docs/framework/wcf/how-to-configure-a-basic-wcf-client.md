---
title: 'Postupy: Konfigurace klienta základní Windows Communication Foundation'
ms.date: 09/14/2018
helpviewer_keywords:
- WCF clients [WCF], configuring
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
ms.openlocfilehash: 3f267edf87711de8a5969e3e0b577648008c5a75
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46323636"
---
# <a name="how-to-configure-a-basic-windows-communication-foundation-client"></a><span data-ttu-id="7025d-102">Postupy: Konfigurace klienta základní Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="7025d-102">How to: Configure a Basic Windows Communication Foundation Client</span></span>

<span data-ttu-id="7025d-103">Toto je pátý šesti úkolů, muset vytvořit základní aplikaci Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7025d-103">This is the fifth of six tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="7025d-104">Přehled všech šesti úkoly, naleznete v tématu [kurz Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="7025d-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>

<span data-ttu-id="7025d-105">Toto téma popisuje klientské konfigurační soubor, který se vygeneroval pomocí **přidat odkaz na službu** funkce sady Visual Studio nebo [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="7025d-105">This topic discusses the client configuration file that was generated using the **Add Service Reference** functionality of Visual Studio or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="7025d-106">Konfigurace klienta se skládá z zadání koncového bodu, který klient používá pro přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="7025d-106">Configuring the client consists of specifying the endpoint that the client uses to access the service.</span></span> <span data-ttu-id="7025d-107">Koncový bod má adresa, vazba a kontrakt a každý z nich musí být zadán právě konfigurace klienta.</span><span class="sxs-lookup"><span data-stu-id="7025d-107">An endpoint has an address, a binding, and a contract, and each of these must be specified in the process of configuring the client.</span></span>

## <a name="configure-a-windows-communication-foundation-client"></a><span data-ttu-id="7025d-108">Konfigurace klienta Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="7025d-108">Configure a Windows Communication Foundation client</span></span>

<span data-ttu-id="7025d-109">Z projektu GettingStartedClient otevřete vygenerovaný konfigurační soubor (App.config).</span><span class="sxs-lookup"><span data-stu-id="7025d-109">Open the generated configuration file (App.config) from the GettingStartedClient project.</span></span> <span data-ttu-id="7025d-110">V následujícím příkladu je zobrazení generovaného konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="7025d-110">The following example is a view of the generated configuration file.</span></span> <span data-ttu-id="7025d-111">V části [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) části, vyhledejte [ \<koncový bod >](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) elementu.</span><span class="sxs-lookup"><span data-stu-id="7025d-111">Under the [\<system.serviceModel>](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, find the [\<endpoint>](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element.</span></span>

```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup>
          <!-- specifies the version of WCF to use-->
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5,Profile=Client" />
        </startup>
        <system.serviceModel>
            <bindings>
                <!-- Uses wsHttpBinding-->
                <wsHttpBinding>
                    <binding name="WSHttpBinding_ICalculator" />
                </wsHttpBinding>
            </bindings>
            <client>
                <!-- specifies the endpoint to use when calling the service -->
                <endpoint address="http://localhost:8000/ServiceModelSamples/Service/CalculatorService"
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">
                    <identity>
                        <userPrincipalName value="migree@redmond.corp.microsoft.com" />
                    </identity>
                </endpoint>
            </client>
        </system.serviceModel>
    </configuration>
```

<span data-ttu-id="7025d-112">Tento příklad konfiguruje koncového bodu, který klient používá pro přístup ke službě, která se nachází na následující adrese: `http://localhost:8000/ServiceModelSamples/Service/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="7025d-112">This example configures the endpoint that the client uses to access the service that is located at the following address: `http://localhost:8000/ServiceModelSamples/Service/CalculatorService`.</span></span>

<span data-ttu-id="7025d-113">Určuje element koncového bodu, který `ServiceReference1.ICalculator` kontraktu služby se používá ke komunikaci mezi klienta WCF a službou.</span><span class="sxs-lookup"><span data-stu-id="7025d-113">The endpoint element specifies that the `ServiceReference1.ICalculator` service contract is used for communication between the WCF client and service.</span></span> <span data-ttu-id="7025d-114">Kanál WCF se nakonfigurují poskytovaných systémem <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="7025d-114">The WCF channel is configured with the system-provided <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="7025d-115">Tato smlouva byl vytvořen pomocí **přidat odkaz na službu** v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7025d-115">This contract was generated by using **Add Service Reference** in Visual Studio.</span></span> <span data-ttu-id="7025d-116">Je v podstatě kopií, která byla definována v projektu GettingStartedLib kontrakt.</span><span class="sxs-lookup"><span data-stu-id="7025d-116">It is essentially a copy of the contract that was defined in the GettingStartedLib project.</span></span> <span data-ttu-id="7025d-117"><xref:System.ServiceModel.WSHttpBinding> Vazbu určuje HTTP jako přenosu, interoperabilní zabezpečení a další podrobnosti o konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="7025d-117">The <xref:System.ServiceModel.WSHttpBinding> binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

<span data-ttu-id="7025d-118">Další informace o tom, jak pomocí generovaného klienta s touto konfigurací najdete v tématu [postupy: používání klienta](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="7025d-118">For more information about how to use the generated client with this configuration, see [How to: Use a Client](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="7025d-119">Další kroky</span><span class="sxs-lookup"><span data-stu-id="7025d-119">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7025d-120">Postupy: používání klienta WCF</span><span class="sxs-lookup"><span data-stu-id="7025d-120">How to: Use a WCF client</span></span>](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)

## <a name="see-also"></a><span data-ttu-id="7025d-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7025d-121">See also</span></span>

- [<span data-ttu-id="7025d-122">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="7025d-122">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="7025d-123">Nástroj metadat modelu služby (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="7025d-123">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="7025d-124">Postupy: Vytvoření klienta</span><span class="sxs-lookup"><span data-stu-id="7025d-124">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [<span data-ttu-id="7025d-125">Začínáme</span><span class="sxs-lookup"><span data-stu-id="7025d-125">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="7025d-126">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="7025d-126">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)