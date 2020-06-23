---
title: 'Postupy: Zadání vazby služby v konfiguraci'
description: Naučte se Konfigurovat koncový bod pro službu WCF v konfiguračním souboru. Kontrakt je definován pro službu a implementován ve třídě.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
ms.openlocfilehash: 92d0834091a1f243df6be214f606fbf0093dca54
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244553"
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a><span data-ttu-id="62ca7-104">Postupy: Zadání vazby služby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="62ca7-104">How to: Specify a Service Binding in Configuration</span></span>
<span data-ttu-id="62ca7-105">V tomto příkladu `ICalculator` je smlouva definovaná pro základní službu kalkulačky, služba je implementovaná ve `CalculatorService` třídě a pak její koncový bod je nakonfigurovaný v souboru Web.config, kde je zadaný, aby služba používala <xref:System.ServiceModel.BasicHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="62ca7-105">In this example, an `ICalculator` contract is defined for a basic calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is configured in the Web.config file, where it is specified that the service uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="62ca7-106">Popis postupu konfigurace této služby pomocí kódu namísto konfigurace najdete v tématu [How to: určení vazby služby v kódu](how-to-specify-a-service-binding-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="62ca7-106">For a description of how to configure this service using code instead of a configuration, see [How to: Specify a Service Binding in Code](how-to-specify-a-service-binding-in-code.md).</span></span>  
  
 <span data-ttu-id="62ca7-107">Obvykle je osvědčeným postupem zadat vazby a informace o adrese deklarativně v konfiguraci, nikoli imperativně v kódu.</span><span class="sxs-lookup"><span data-stu-id="62ca7-107">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="62ca7-108">Definování koncových bodů v kódu obvykle není praktické, protože vazby a adresy nasazené služby se obvykle liší od těch, které se použily při vývoji služby.</span><span class="sxs-lookup"><span data-stu-id="62ca7-108">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="62ca7-109">Obecně platí, že zachování vazby a adresování informací z kódu umožňuje jejich změnu bez nutnosti opětovné kompilace nebo opětovného nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="62ca7-109">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="62ca7-110">Pomocí [nástroje Editor konfigurací (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md)je možné provést všechny následující kroky konfigurace.</span><span class="sxs-lookup"><span data-stu-id="62ca7-110">All of the following configuration steps can be undertaken using the [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="62ca7-111">Zdrojovou kopii tohoto příkladu naleznete v tématu [BasicBinding](./samples/basicbinding.md).</span><span class="sxs-lookup"><span data-stu-id="62ca7-111">For the source copy of this example, see [BasicBinding](./samples/basicbinding.md).</span></span>  
  
## <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a><span data-ttu-id="62ca7-112">Určení BasicHttpBinding, který se má použít ke konfiguraci služby</span><span class="sxs-lookup"><span data-stu-id="62ca7-112">To specify the BasicHttpBinding to use to configure the service</span></span>  
  
1. <span data-ttu-id="62ca7-113">Definujte kontrakt služby pro typ služby.</span><span class="sxs-lookup"><span data-stu-id="62ca7-113">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2. <span data-ttu-id="62ca7-114">Implementujte kontrakt služby ve třídě služby.</span><span class="sxs-lookup"><span data-stu-id="62ca7-114">Implement the service contract in a service class.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    > <span data-ttu-id="62ca7-115">V rámci implementace služby nejsou zadány informace o adrese nebo vazbě.</span><span class="sxs-lookup"><span data-stu-id="62ca7-115">Address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="62ca7-116">Také není nutné zapisovat kód pro načtení těchto informací z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="62ca7-116">Also, code does not have to be written to fetch that information from the configuration file.</span></span>  
  
3. <span data-ttu-id="62ca7-117">Vytvořte soubor Web.config pro konfiguraci koncového bodu pro `CalculatorService` , který používá <xref:System.ServiceModel.WSHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="62ca7-117">Create a Web.config file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name=" CalculatorService" >  

            <!-- Leave the address blank to be populated by default -->
            <!-- from the hosting environment,in this case IIS, so -->
            <!-- the address will just be that of the IIS Virtual -->
            <!-- Directory. -->

            <!-- Specify the binding configuration name for that -->
            <!-- binding type. This is optional but useful if you -->
            <!-- want to modify the properties of the binding. -->
            <!-- The bindingConfiguration name Binding1 is defined -->
            <!-- below in the bindings element. -->
            <endpoint
                address=""
                binding="wsHttpBinding"  
                bindingConfiguration="Binding1"  
                contract="ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <wsHttpBinding>  
            <binding name="Binding1">  
              <!-- Binding property values can be modified here. -->  
              <!-- See the next procedure. -->  
            </binding>  
          </wsHttpBinding>  
       </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4. <span data-ttu-id="62ca7-118">Vytvořte soubor Service. svc, který obsahuje následující řádek, a umístěte ho do virtuálního adresáře Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="62ca7-118">Create a Service.svc file that contains the following line and place it in your Internet Information Services (IIS) virtual directory.</span></span>  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>
    ```  
  
## <a name="to-modify-the-default-values-of-the-binding-properties"></a><span data-ttu-id="62ca7-119">Úprava výchozích hodnot vlastností vazby</span><span class="sxs-lookup"><span data-stu-id="62ca7-119">To modify the default values of the binding properties</span></span>  
  
1. <span data-ttu-id="62ca7-120">Chcete-li upravit jednu z hodnot výchozích vlastností <xref:System.ServiceModel.WSHttpBinding> , vytvořte nový název konfigurace vazby `<binding name="Binding1">` v rámci [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) elementu a nastavte nové hodnoty atributů vazby v tomto elementu vazby.</span><span class="sxs-lookup"><span data-stu-id="62ca7-120">To modify one of the default property values of the <xref:System.ServiceModel.WSHttpBinding>, create a new binding configuration name - `<binding name="Binding1">` - within the [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element and set the new values for the attributes of the binding in this binding element.</span></span> <span data-ttu-id="62ca7-121">Chcete-li například změnit výchozí hodnoty časového limitu pro otevření a ukončení 1 minuty na 2 minuty, přidejte následující do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="62ca7-121">For example, to change the default open and close timeout values of 1 minute to 2 minutes, add the following to the configuration file.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="62ca7-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="62ca7-122">See also</span></span>

- [<span data-ttu-id="62ca7-123">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="62ca7-123">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="62ca7-124">Zadání adresy koncového bodu</span><span class="sxs-lookup"><span data-stu-id="62ca7-124">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)
