---
title: <comContracts>
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: 3e3e4bf18b204db5a4068cc3f6cbb1337d5f611d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254311"
---
# <a name="comcontracts"></a><span data-ttu-id="53f26-101">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="53f26-101">\<comContracts></span></span>
<span data-ttu-id="53f26-102">`comContracts` Oddíl konfigurace obsahuje prvky, které vám umožňují určit různé vlastnosti kontraktu služby integrace modelu COM +.</span><span class="sxs-lookup"><span data-stu-id="53f26-102">The `comContracts` configuration section contains elements that allow you to specify various properties of a COM+ integration service contract.</span></span>  
  
## <a name="specifying-namespace-and-contract"></a><span data-ttu-id="53f26-103">Určení Namespace a smlouvy</span><span class="sxs-lookup"><span data-stu-id="53f26-103">Specifying Namespace and Contract</span></span>  
 <span data-ttu-id="53f26-104">Kontrakty služby integrace modelu COM + jsou momentálně omezené jenom na `http://tempuri.org` oboru názvů a název smlouvy je odvozen z rozhraní COM podpůrné.</span><span class="sxs-lookup"><span data-stu-id="53f26-104">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="53f26-105">Můžete však určit alternativy pomocí `comContracts` oddílu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="53f26-105">You can, however, specify alternatives by using the `comContracts` section in the configuration file.</span></span>  
  
 <span data-ttu-id="53f26-106">Například můžete použít následující konfigurace k určení oboru názvů a kontrakt název kontraktu služby, stejně jako možnost vynutit použití vazby s relacemi.</span><span class="sxs-lookup"><span data-stu-id="53f26-106">For example, you can use the following configuration to specify the namespace and contract name of the service contract, as well as an option to enforce usage on sessionful bindings.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="53f26-107">Při inicializaci služby zadaných oborů názvů trasy a názvy kontraktů se použijí na popis generované služeb.</span><span class="sxs-lookup"><span data-stu-id="53f26-107">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
 <span data-ttu-id="53f26-108">Když tato část je prázdná, inicializace služby se uplatní výchozí obor názvů a kontrakt název z podpůrné ID modelu COM rozhraní.</span><span class="sxs-lookup"><span data-stu-id="53f26-108">When this section is empty, the service initialization applies a default namespace and contract name taken from the supporting COM interface ID.</span></span>  
  
 <span data-ttu-id="53f26-109">Kromě toho můžete použít [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementu k určení modelu COM + metody, které jsou vystaveny při vystavení rozhraní komponenty COM + jako webovou službu.</span><span class="sxs-lookup"><span data-stu-id="53f26-109">In addition, you can use the [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) element to specify COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span> <span data-ttu-id="53f26-110">Můžete také použít [ \<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) k určení trvalé typy používané v integraci.</span><span class="sxs-lookup"><span data-stu-id="53f26-110">You can also use the [\<persistableTypes>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) to specify persistable types used in integration.</span></span> <span data-ttu-id="53f26-111">Nakonec můžete použít [ \<typu userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) element patří uživateli definované typy (UDT), které se mají být součástí kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="53f26-111">Finally, you can use the [\<userDefinedType>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) element to include User Defined Types (UDT) that are to be included in the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53f26-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53f26-112">See also</span></span>
- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [<span data-ttu-id="53f26-113">\<exposedMethod></span><span class="sxs-lookup"><span data-stu-id="53f26-113">\<exposedMethod></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)
- [<span data-ttu-id="53f26-114">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="53f26-114">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)
- [<span data-ttu-id="53f26-115">\<userDefinedType></span><span class="sxs-lookup"><span data-stu-id="53f26-115">\<userDefinedType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)
- [<span data-ttu-id="53f26-116">\<comContract></span><span class="sxs-lookup"><span data-stu-id="53f26-116">\<comContract></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontract.md)
- [<span data-ttu-id="53f26-117">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="53f26-117">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="53f26-118">Postupy: Konfigurace nastavení služby modelu COM +</span><span class="sxs-lookup"><span data-stu-id="53f26-118">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
