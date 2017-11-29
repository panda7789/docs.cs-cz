---
title: '&lt;exposedMethod&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c89acb38678879f882d8bb2a2b5277b555a1eb26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltexposedmethodgt"></a><span data-ttu-id="4a5af-102">&lt;exposedMethod&gt;</span><span class="sxs-lookup"><span data-stu-id="4a5af-102">&lt;exposedMethod&gt;</span></span>
<span data-ttu-id="4a5af-103">Představuje metodu modelu COM +, který je zveřejněný, pokud je jako webovou službu vystavený rozhraní komponenty modelu COM +.</span><span class="sxs-lookup"><span data-stu-id="4a5af-103">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
 <span data-ttu-id="4a5af-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="4a5af-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4a5af-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="4a5af-105">\<comContracts></span></span>  
<span data-ttu-id="4a5af-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="4a5af-106">\<comContract></span></span>  
<span data-ttu-id="4a5af-107">\<metody ></span><span class="sxs-lookup"><span data-stu-id="4a5af-107">\<methods></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a5af-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a5af-108">Syntax</span></span>  
  
```xml  
<comContracts>  
  <comContract>  
      <exposedMethods>  
         <exposedMethod name="string" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a5af-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4a5af-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4a5af-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4a5af-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a5af-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="4a5af-111">Attributes</span></span>  
  
|<span data-ttu-id="4a5af-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="4a5af-112">Attribute</span></span>|<span data-ttu-id="4a5af-113">Popis</span><span class="sxs-lookup"><span data-stu-id="4a5af-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4a5af-114">name</span><span class="sxs-lookup"><span data-stu-id="4a5af-114">name</span></span>|<span data-ttu-id="4a5af-115">Řetězec, který obsahuje metodu modelu COM +, který je zveřejněný, pokud je jako webovou službu vystavený rozhraní komponenty modelu COM +.</span><span class="sxs-lookup"><span data-stu-id="4a5af-115">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4a5af-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4a5af-116">Child Elements</span></span>  
 <span data-ttu-id="4a5af-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="4a5af-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4a5af-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4a5af-118">Parent Elements</span></span>  
  
|<span data-ttu-id="4a5af-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="4a5af-119">Element</span></span>|<span data-ttu-id="4a5af-120">Popis</span><span class="sxs-lookup"><span data-stu-id="4a5af-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a5af-121">\<exposedMethods ></span><span class="sxs-lookup"><span data-stu-id="4a5af-121">\<exposedMethods></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethods.md)|<span data-ttu-id="4a5af-122">Kolekce [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="4a5af-122">A collection of [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a5af-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4a5af-123">Remarks</span></span>  
 <span data-ttu-id="4a5af-124">Modelu COM + integrace nástroje configuration (ComSvcConfig.exe) můžete použít k přidání konkrétních metod z rozhraní modelu COM se objevily na kontrakt generovaný služby.</span><span class="sxs-lookup"><span data-stu-id="4a5af-124">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="4a5af-125">Například následující příkaz můžete přidat tři metody s názvem z `IFinances` rozhraní modelu COM na `ItemOrders`. Finanční komponenta generovaného servisní smlouvou.</span><span class="sxs-lookup"><span data-stu-id="4a5af-125">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="4a5af-126">Když spustíte také ComSvcConfig.exe, pak generuje následující kontrakt služby výpis výše uvedených metod jako [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="4a5af-126">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" name="IFinances" namespace="http://contoso.com/services/financial">  
    <exposedMethod name="TransferFunds"/>  
    <exposedMethod name="AddFunds"/>  
    <exposedMethod name="RemoveFunds"/>  
</comContract>  
```  
  
 <span data-ttu-id="4a5af-127">Během inicializace služby modulu runtime pokusí generovat kontraktu služby odrážející přes a přidáním pouze metody, které jsou uvedené v seznamu [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="4a5af-127">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span> <span data-ttu-id="4a5af-128">Trasování se vytvoří pro každou metodu rozhraní, která není součástí kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="4a5af-128">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a5af-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="4a5af-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComMethodElementCollection>  
 <xref:System.ServiceModel.Configuration.ComMethodElement>  
 [<span data-ttu-id="4a5af-130">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="4a5af-130">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="4a5af-131">Integrace s aplikacemi modelu COM +</span><span class="sxs-lookup"><span data-stu-id="4a5af-131">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="4a5af-132">Postupy: Konfigurace nastavení služby COM +</span><span class="sxs-lookup"><span data-stu-id="4a5af-132">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
