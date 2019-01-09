---
title: '&lt;exposedMethod&gt;'
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: c63689224e3bba69816f5904599425a235a51bae
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145228"
---
# <a name="ltexposedmethodgt"></a><span data-ttu-id="a7b2d-102">&lt;exposedMethod&gt;</span><span class="sxs-lookup"><span data-stu-id="a7b2d-102">&lt;exposedMethod&gt;</span></span>
<span data-ttu-id="a7b2d-103">Představuje metodu COM +, která je vystavena při vystavení rozhraní komponenty COM + jako webovou službu.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-103">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
 <span data-ttu-id="a7b2d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a7b2d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a7b2d-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="a7b2d-105">\<comContracts></span></span>  
<span data-ttu-id="a7b2d-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="a7b2d-106">\<comContract></span></span>  
<span data-ttu-id="a7b2d-107">\<metody ></span><span class="sxs-lookup"><span data-stu-id="a7b2d-107">\<methods></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7b2d-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7b2d-108">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7b2d-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a7b2d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a7b2d-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7b2d-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="a7b2d-111">Attributes</span></span>  
  
|<span data-ttu-id="a7b2d-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="a7b2d-112">Attribute</span></span>|<span data-ttu-id="a7b2d-113">Popis</span><span class="sxs-lookup"><span data-stu-id="a7b2d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7b2d-114">name</span><span class="sxs-lookup"><span data-stu-id="a7b2d-114">name</span></span>|<span data-ttu-id="a7b2d-115">Řetězec, který obsahuje metodu COM +, která je vystavena při vystavení rozhraní komponenty COM + jako webovou službu.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-115">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7b2d-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a7b2d-116">Child Elements</span></span>  
 <span data-ttu-id="a7b2d-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="a7b2d-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a7b2d-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a7b2d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a7b2d-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="a7b2d-119">Element</span></span>|<span data-ttu-id="a7b2d-120">Popis</span><span class="sxs-lookup"><span data-stu-id="a7b2d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7b2d-121">\<exposedMethods ></span><span class="sxs-lookup"><span data-stu-id="a7b2d-121">\<exposedMethods></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethods.md)|<span data-ttu-id="a7b2d-122">Kolekce [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-122">A collection of [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7b2d-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a7b2d-123">Remarks</span></span>  
 <span data-ttu-id="a7b2d-124">COM + integration nástroj pro konfiguraci (ComSvcConfig.exe) slouží k přidání specifických metod z rozhraní modelu COM, který se zobrazí na kontrakt generovaný služby.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-124">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="a7b2d-125">Například slouží následující příkaz k přidání tří pojmenované metody ze `IFinances` rozhraní modelu COM na `ItemOrders`. Finanční součásti pro kontrakt generovaný služby.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-125">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="a7b2d-126">Při spuštění také ComSvcConfig.exe, poté vygeneruje následující kontrakt služby výpis výše uvedených metod jako [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-126">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 <span data-ttu-id="a7b2d-127">Během inicializace služby, modul runtime pokusí vygenerovat kontraktu služby znázorňující v a přidáním pouze metody uvedené v seznamu [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-127">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span> <span data-ttu-id="a7b2d-128">Trasování je vytvořen pro každou metodu rozhraní, který není součástí kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-128">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7b2d-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7b2d-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComMethodElementCollection>  
 <xref:System.ServiceModel.Configuration.ComMethodElement>  
 [<span data-ttu-id="a7b2d-130">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="a7b2d-130">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="a7b2d-131">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="a7b2d-131">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="a7b2d-132">Postupy: Konfigurace nastavení služby modelu COM +</span><span class="sxs-lookup"><span data-stu-id="a7b2d-132">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
