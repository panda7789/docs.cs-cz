---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 151929cd99df08b705bee94eb6fd6f10c254a660
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259849"
---
# <a name="exposedmethod"></a><span data-ttu-id="a7d02-101">\<exposedMethod ></span><span class="sxs-lookup"><span data-stu-id="a7d02-101">\<exposedMethod></span></span>
<span data-ttu-id="a7d02-102">Představuje metodu COM +, která je vystavena při vystavení rozhraní komponenty COM + jako webovou službu.</span><span class="sxs-lookup"><span data-stu-id="a7d02-102">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
 <span data-ttu-id="a7d02-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a7d02-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a7d02-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="a7d02-104">\<comContracts></span></span>  
<span data-ttu-id="a7d02-105">\<comContract></span><span class="sxs-lookup"><span data-stu-id="a7d02-105">\<comContract></span></span>  
<span data-ttu-id="a7d02-106">\<metody ></span><span class="sxs-lookup"><span data-stu-id="a7d02-106">\<methods></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7d02-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7d02-107">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7d02-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a7d02-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a7d02-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a7d02-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7d02-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="a7d02-110">Attributes</span></span>  
  
|<span data-ttu-id="a7d02-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="a7d02-111">Attribute</span></span>|<span data-ttu-id="a7d02-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a7d02-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7d02-113">name</span><span class="sxs-lookup"><span data-stu-id="a7d02-113">name</span></span>|<span data-ttu-id="a7d02-114">Řetězec, který obsahuje metodu COM +, která je vystavena při vystavení rozhraní komponenty COM + jako webovou službu.</span><span class="sxs-lookup"><span data-stu-id="a7d02-114">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7d02-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a7d02-115">Child Elements</span></span>  
 <span data-ttu-id="a7d02-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="a7d02-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a7d02-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a7d02-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a7d02-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="a7d02-118">Element</span></span>|<span data-ttu-id="a7d02-119">Popis</span><span class="sxs-lookup"><span data-stu-id="a7d02-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7d02-120">\<exposedMethods ></span><span class="sxs-lookup"><span data-stu-id="a7d02-120">\<exposedMethods></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethods.md)|<span data-ttu-id="a7d02-121">Kolekce [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="a7d02-121">A collection of [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7d02-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a7d02-122">Remarks</span></span>  
 <span data-ttu-id="a7d02-123">COM + integration nástroj pro konfiguraci (ComSvcConfig.exe) slouží k přidání specifických metod z rozhraní modelu COM, který se zobrazí na kontrakt generovaný služby.</span><span class="sxs-lookup"><span data-stu-id="a7d02-123">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="a7d02-124">Například slouží následující příkaz k přidání tří pojmenované metody ze `IFinances` rozhraní modelu COM na `ItemOrders`. Finanční součásti pro kontrakt generovaný služby.</span><span class="sxs-lookup"><span data-stu-id="a7d02-124">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="a7d02-125">Při spuštění také ComSvcConfig.exe, poté vygeneruje následující kontrakt služby výpis výše uvedených metod jako [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="a7d02-125">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 <span data-ttu-id="a7d02-126">Během inicializace služby, modul runtime pokusí vygenerovat kontraktu služby znázorňující v a přidáním pouze metody uvedené v seznamu [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="a7d02-126">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span> <span data-ttu-id="a7d02-127">Trasování je vytvořen pro každou metodu rozhraní, který není součástí kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="a7d02-127">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7d02-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7d02-128">See also</span></span>
- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [<span data-ttu-id="a7d02-129">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="a7d02-129">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [<span data-ttu-id="a7d02-130">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="a7d02-130">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="a7d02-131">Postupy: Konfigurace nastavení služby modelu COM +</span><span class="sxs-lookup"><span data-stu-id="a7d02-131">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
