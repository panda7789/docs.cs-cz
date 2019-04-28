---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 91eafa46aa73b5e6d359fcbe48f098f9f8a4d0f0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61644296"
---
# <a name="exposedmethod"></a><span data-ttu-id="3cf23-101">\<exposedMethod ></span><span class="sxs-lookup"><span data-stu-id="3cf23-101">\<exposedMethod></span></span>
<span data-ttu-id="3cf23-102">Představuje metodu COM +, která je vystavena při vystavení rozhraní komponenty COM + jako webovou službu.</span><span class="sxs-lookup"><span data-stu-id="3cf23-102">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
 <span data-ttu-id="3cf23-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3cf23-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="3cf23-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="3cf23-104">\<comContracts></span></span>  
<span data-ttu-id="3cf23-105">\<comContract></span><span class="sxs-lookup"><span data-stu-id="3cf23-105">\<comContract></span></span>  
<span data-ttu-id="3cf23-106">\<metody ></span><span class="sxs-lookup"><span data-stu-id="3cf23-106">\<methods></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cf23-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3cf23-107">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3cf23-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3cf23-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3cf23-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3cf23-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3cf23-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="3cf23-110">Attributes</span></span>  
  
|<span data-ttu-id="3cf23-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="3cf23-111">Attribute</span></span>|<span data-ttu-id="3cf23-112">Popis</span><span class="sxs-lookup"><span data-stu-id="3cf23-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3cf23-113">name</span><span class="sxs-lookup"><span data-stu-id="3cf23-113">name</span></span>|<span data-ttu-id="3cf23-114">Řetězec, který obsahuje metodu COM +, která je vystavena při vystavení rozhraní komponenty COM + jako webovou službu.</span><span class="sxs-lookup"><span data-stu-id="3cf23-114">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3cf23-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3cf23-115">Child Elements</span></span>  
 <span data-ttu-id="3cf23-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="3cf23-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3cf23-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3cf23-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3cf23-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="3cf23-118">Element</span></span>|<span data-ttu-id="3cf23-119">Popis</span><span class="sxs-lookup"><span data-stu-id="3cf23-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3cf23-120">\<exposedMethods ></span><span class="sxs-lookup"><span data-stu-id="3cf23-120">\<exposedMethods></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethods.md)|<span data-ttu-id="3cf23-121">Kolekce [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="3cf23-121">A collection of [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3cf23-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3cf23-122">Remarks</span></span>  
 <span data-ttu-id="3cf23-123">COM + integration nástroj pro konfiguraci (ComSvcConfig.exe) slouží k přidání specifických metod z rozhraní modelu COM, který se zobrazí na kontrakt generovaný služby.</span><span class="sxs-lookup"><span data-stu-id="3cf23-123">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="3cf23-124">Například slouží následující příkaz k přidání tří pojmenované metody ze `IFinances` rozhraní modelu COM na `ItemOrders`. Finanční součásti pro kontrakt generovaný služby.</span><span class="sxs-lookup"><span data-stu-id="3cf23-124">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="3cf23-125">Při spuštění také ComSvcConfig.exe, poté vygeneruje následující kontrakt služby výpis výše uvedených metod jako [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="3cf23-125">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 <span data-ttu-id="3cf23-126">Během inicializace služby, modul runtime pokusí vygenerovat kontraktu služby znázorňující v a přidáním pouze metody uvedené v seznamu [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="3cf23-126">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span> <span data-ttu-id="3cf23-127">Trasování je vytvořen pro každou metodu rozhraní, který není součástí kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="3cf23-127">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cf23-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3cf23-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [<span data-ttu-id="3cf23-129">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="3cf23-129">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [<span data-ttu-id="3cf23-130">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="3cf23-130">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="3cf23-131">Postupy: Konfigurace nastavení služby modelu COM +</span><span class="sxs-lookup"><span data-stu-id="3cf23-131">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
