---
title: '&lt;exposedMethod&gt;'
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 2a26ca90f6a66592c246cc9e5aef50cfa53b4bdd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltexposedmethodgt"></a><span data-ttu-id="4a831-102">&lt;exposedMethod&gt;</span><span class="sxs-lookup"><span data-stu-id="4a831-102">&lt;exposedMethod&gt;</span></span>
<span data-ttu-id="4a831-103">Představuje metodu modelu COM +, který je zveřejněný, pokud je jako webovou službu vystavený rozhraní komponenty modelu COM +.</span><span class="sxs-lookup"><span data-stu-id="4a831-103">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
 <span data-ttu-id="4a831-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4a831-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4a831-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="4a831-105">\<comContracts></span></span>  
<span data-ttu-id="4a831-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="4a831-106">\<comContract></span></span>  
<span data-ttu-id="4a831-107">\<metody ></span><span class="sxs-lookup"><span data-stu-id="4a831-107">\<methods></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a831-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a831-108">Syntax</span></span>  
  
```xml  
<comContracts>  
  <comContract>  
      <exposedMethods>  
         <exposedMethod name="string" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a831-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4a831-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4a831-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4a831-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a831-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="4a831-111">Attributes</span></span>  
  
|<span data-ttu-id="4a831-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="4a831-112">Attribute</span></span>|<span data-ttu-id="4a831-113">Popis</span><span class="sxs-lookup"><span data-stu-id="4a831-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4a831-114">name</span><span class="sxs-lookup"><span data-stu-id="4a831-114">name</span></span>|<span data-ttu-id="4a831-115">Řetězec, který obsahuje metodu modelu COM +, který je zveřejněný, pokud je jako webovou službu vystavený rozhraní komponenty modelu COM +.</span><span class="sxs-lookup"><span data-stu-id="4a831-115">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4a831-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4a831-116">Child Elements</span></span>  
 <span data-ttu-id="4a831-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="4a831-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4a831-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4a831-118">Parent Elements</span></span>  
  
|<span data-ttu-id="4a831-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="4a831-119">Element</span></span>|<span data-ttu-id="4a831-120">Popis</span><span class="sxs-lookup"><span data-stu-id="4a831-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a831-121">\<exposedMethods ></span><span class="sxs-lookup"><span data-stu-id="4a831-121">\<exposedMethods></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethods.md)|<span data-ttu-id="4a831-122">Kolekce [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="4a831-122">A collection of [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a831-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4a831-123">Remarks</span></span>  
 <span data-ttu-id="4a831-124">Modelu COM + integrace nástroje configuration (ComSvcConfig.exe) můžete použít k přidání konkrétních metod z rozhraní modelu COM se objevily na kontrakt generovaný služby.</span><span class="sxs-lookup"><span data-stu-id="4a831-124">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="4a831-125">Například následující příkaz můžete přidat tři metody s názvem z `IFinances` rozhraní modelu COM na `ItemOrders`. Finanční komponenta generovaného servisní smlouvou.</span><span class="sxs-lookup"><span data-stu-id="4a831-125">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="4a831-126">Když spustíte také ComSvcConfig.exe, pak generuje následující kontrakt služby výpis výše uvedených metod jako [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="4a831-126">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" name="IFinances" namespace="http://contoso.com/services/financial">  
    <exposedMethod name="TransferFunds"/>  
    <exposedMethod name="AddFunds"/>  
    <exposedMethod name="RemoveFunds"/>  
</comContract>  
```  
  
 <span data-ttu-id="4a831-127">Během inicializace služby modulu runtime pokusí generovat kontraktu služby odrážející přes a přidáním pouze metody, které jsou uvedené v seznamu [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="4a831-127">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span> <span data-ttu-id="4a831-128">Trasování se vytvoří pro každou metodu rozhraní, která není součástí kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="4a831-128">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a831-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="4a831-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComMethodElementCollection>  
 <xref:System.ServiceModel.Configuration.ComMethodElement>  
 [<span data-ttu-id="4a831-130">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="4a831-130">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="4a831-131">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="4a831-131">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="4a831-132">Postupy: Konfigurace nastavení služby modelu COM+</span><span class="sxs-lookup"><span data-stu-id="4a831-132">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
