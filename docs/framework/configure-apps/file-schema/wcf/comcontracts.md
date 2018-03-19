---
title: '&lt;comContracts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 69fbce3f312833c374a4c2615a15359d9c2db3a7
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2018
---
# <a name="ltcomcontractsgt"></a><span data-ttu-id="48a0e-102">&lt;comContracts&gt;</span><span class="sxs-lookup"><span data-stu-id="48a0e-102">&lt;comContracts&gt;</span></span>
<span data-ttu-id="48a0e-103">`comContracts` Konfigurační oddíl obsahuje prvky, které umožňují určit různé vlastnosti modelu COM + integrace kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="48a0e-103">The `comContracts` configuration section contains elements that allow you to specify various properties of a COM+ integration service contract.</span></span>  
  
## <a name="specifying-namespace-and-contract"></a><span data-ttu-id="48a0e-104">Určení Namespace a kontraktu</span><span class="sxs-lookup"><span data-stu-id="48a0e-104">Specifying Namespace and Contract</span></span>  
 <span data-ttu-id="48a0e-105">Kontrakty služeb integrace COM + aktuálně omezeny na "http://tempuri.org" oboru názvů a název smlouvy je odvozený od podpůrné rozhraní modelu COM.</span><span class="sxs-lookup"><span data-stu-id="48a0e-105">COM+ integration service contracts are currently restricted to the "http://tempuri.org" namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="48a0e-106">Můžete však zadat alternativy pomocí `comContracts` oddíl v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="48a0e-106">You can, however, specify alternatives by using the `comContracts` section in the configuration file.</span></span>  
  
 <span data-ttu-id="48a0e-107">Například můžete použít následující konfigurace zadat obor názvů a kontrakt název kontraktu služby, stejně jako možnost vynutit využití na relacemi vazby.</span><span class="sxs-lookup"><span data-stu-id="48a0e-107">For example, you can use the following configuration to specify the namespace and contract name of the service contract, as well as an option to enforce usage on sessionful bindings.</span></span>  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
      namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"  
      name="_Broker"  
      requireSession="true">  
  </comContract>  
</comContracts>  
```  
  
 <span data-ttu-id="48a0e-108">Při inicializaci služby zadaných oborů názvů a názvy kontraktu platí pro popis generovaného služby.</span><span class="sxs-lookup"><span data-stu-id="48a0e-108">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
 <span data-ttu-id="48a0e-109">Když tato část je prázdná, inicializace služby se uplatní výchozí obor názvů a kontrakt název prováděné z podpůrné ID. rozhraní COM</span><span class="sxs-lookup"><span data-stu-id="48a0e-109">When this section is empty, the service initialization applies a default namespace and contract name taken from the supporting COM interface ID.</span></span>  
  
 <span data-ttu-id="48a0e-110">Kromě toho můžete použít [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) element k určení modelu COM + metody, které jsou zveřejněné, pokud je jako webovou službu vystavený rozhraní komponenty modelu COM +.</span><span class="sxs-lookup"><span data-stu-id="48a0e-110">In addition, you can use the [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) element to specify COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span> <span data-ttu-id="48a0e-111">Můžete také [ \<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) k určení trvalá typy používané v integrace.</span><span class="sxs-lookup"><span data-stu-id="48a0e-111">You can also use the [\<persistableTypes>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) to specify persistable types used in integration.</span></span> <span data-ttu-id="48a0e-112">Nakonec můžete použít [ \<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) elementu, který chcete zahrnout uživatele definované typy (UDT), které mají být zahrnuty do kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="48a0e-112">Finally, you can use the [\<userDefinedType>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) element to include User Defined Types (UDT) that are to be included in the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48a0e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="48a0e-113">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [<span data-ttu-id="48a0e-114">\<exposedMethod ></span><span class="sxs-lookup"><span data-stu-id="48a0e-114">\<exposedMethod></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)  
 [<span data-ttu-id="48a0e-115">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="48a0e-115">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)  
 [<span data-ttu-id="48a0e-116">\<userDefinedType></span><span class="sxs-lookup"><span data-stu-id="48a0e-116">\<userDefinedType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)  
 [<span data-ttu-id="48a0e-117">\<comContract></span><span class="sxs-lookup"><span data-stu-id="48a0e-117">\<comContract></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontract.md)  
 [<span data-ttu-id="48a0e-118">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="48a0e-118">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="48a0e-119">Postupy: Konfigurace nastavení služby modelu COM+</span><span class="sxs-lookup"><span data-stu-id="48a0e-119">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
