---
title: '&lt;comContracts&gt;'
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: 297a28181de8ce6ed658afad950f25cced9f9cb7
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46540801"
---
# <a name="ltcomcontractsgt"></a><span data-ttu-id="3d239-102">&lt;comContracts&gt;</span><span class="sxs-lookup"><span data-stu-id="3d239-102">&lt;comContracts&gt;</span></span>
<span data-ttu-id="3d239-103">`comContracts` Oddíl konfigurace obsahuje prvky, které vám umožňují určit různé vlastnosti kontraktu služby integrace modelu COM +.</span><span class="sxs-lookup"><span data-stu-id="3d239-103">The `comContracts` configuration section contains elements that allow you to specify various properties of a COM+ integration service contract.</span></span>  
  
## <a name="specifying-namespace-and-contract"></a><span data-ttu-id="3d239-104">Určení Namespace a smlouvy</span><span class="sxs-lookup"><span data-stu-id="3d239-104">Specifying Namespace and Contract</span></span>  
 <span data-ttu-id="3d239-105">Kontrakty služby integrace modelu COM + jsou momentálně omezené jenom na `http://tempuri.org` oboru názvů a název smlouvy je odvozen z rozhraní COM podpůrné.</span><span class="sxs-lookup"><span data-stu-id="3d239-105">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="3d239-106">Můžete však určit alternativy pomocí `comContracts` oddílu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="3d239-106">You can, however, specify alternatives by using the `comContracts` section in the configuration file.</span></span>  
  
 <span data-ttu-id="3d239-107">Například můžete použít následující konfigurace k určení oboru názvů a kontrakt název kontraktu služby, stejně jako možnost vynutit použití vazby s relacemi.</span><span class="sxs-lookup"><span data-stu-id="3d239-107">For example, you can use the following configuration to specify the namespace and contract name of the service contract, as well as an option to enforce usage on sessionful bindings.</span></span>  
  
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
  
 <span data-ttu-id="3d239-108">Při inicializaci služby zadaných oborů názvů trasy a názvy kontraktů se použijí na popis generované služeb.</span><span class="sxs-lookup"><span data-stu-id="3d239-108">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
 <span data-ttu-id="3d239-109">Když tato část je prázdná, inicializace služby se uplatní výchozí obor názvů a kontrakt název z podpůrné ID modelu COM rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3d239-109">When this section is empty, the service initialization applies a default namespace and contract name taken from the supporting COM interface ID.</span></span>  
  
 <span data-ttu-id="3d239-110">Kromě toho můžete použít [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementu k určení modelu COM + metody, které jsou vystaveny při vystavení rozhraní komponenty COM + jako webovou službu.</span><span class="sxs-lookup"><span data-stu-id="3d239-110">In addition, you can use the [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) element to specify COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span> <span data-ttu-id="3d239-111">Můžete také použít [ \<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) k určení trvalé typy používané v integraci.</span><span class="sxs-lookup"><span data-stu-id="3d239-111">You can also use the [\<persistableTypes>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) to specify persistable types used in integration.</span></span> <span data-ttu-id="3d239-112">Nakonec můžete použít [ \<typu userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) element patří uživateli definované typy (UDT), které se mají být součástí kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="3d239-112">Finally, you can use the [\<userDefinedType>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) element to include User Defined Types (UDT) that are to be included in the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d239-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d239-113">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [<span data-ttu-id="3d239-114">\<exposedMethod ></span><span class="sxs-lookup"><span data-stu-id="3d239-114">\<exposedMethod></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)  
 [<span data-ttu-id="3d239-115">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="3d239-115">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)  
 [<span data-ttu-id="3d239-116">\<userDefinedType></span><span class="sxs-lookup"><span data-stu-id="3d239-116">\<userDefinedType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)  
 [<span data-ttu-id="3d239-117">\<comContract></span><span class="sxs-lookup"><span data-stu-id="3d239-117">\<comContract></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontract.md)  
 [<span data-ttu-id="3d239-118">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="3d239-118">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="3d239-119">Postupy: Konfigurace nastavení služby modelu COM+</span><span class="sxs-lookup"><span data-stu-id="3d239-119">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
