---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 032139b714aa11079c7ee8610c332e404b3981ac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918997"
---
# <a name="exposedmethod"></a><span data-ttu-id="2ec6d-101">\<Prvků exposedMethod ></span><span class="sxs-lookup"><span data-stu-id="2ec6d-101">\<exposedMethod></span></span>
<span data-ttu-id="2ec6d-102">Představuje metodu COM+, která je vystavena v případě, že je rozhraní součásti modelu COM vystaveno jako webová služba.</span><span class="sxs-lookup"><span data-stu-id="2ec6d-102">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
 <span data-ttu-id="2ec6d-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2ec6d-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="2ec6d-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="2ec6d-104">\<comContracts></span></span>  
<span data-ttu-id="2ec6d-105">\<comContract></span><span class="sxs-lookup"><span data-stu-id="2ec6d-105">\<comContract></span></span>  
<span data-ttu-id="2ec6d-106">\<metody ></span><span class="sxs-lookup"><span data-stu-id="2ec6d-106">\<methods></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ec6d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ec6d-107">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ec6d-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2ec6d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2ec6d-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2ec6d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ec6d-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="2ec6d-110">Attributes</span></span>  
  
|<span data-ttu-id="2ec6d-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="2ec6d-111">Attribute</span></span>|<span data-ttu-id="2ec6d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2ec6d-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2ec6d-113">name</span><span class="sxs-lookup"><span data-stu-id="2ec6d-113">name</span></span>|<span data-ttu-id="2ec6d-114">Řetězec obsahující metodu modelu COM+, která je vystavena v případě, že je rozhraní součásti modelu COM vystaveno jako webová služba.</span><span class="sxs-lookup"><span data-stu-id="2ec6d-114">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2ec6d-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2ec6d-115">Child Elements</span></span>  
 <span data-ttu-id="2ec6d-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="2ec6d-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2ec6d-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2ec6d-117">Parent Elements</span></span>  
  
|<span data-ttu-id="2ec6d-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="2ec6d-118">Element</span></span>|<span data-ttu-id="2ec6d-119">Popis</span><span class="sxs-lookup"><span data-stu-id="2ec6d-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2ec6d-120">\<exposedMethods ></span><span class="sxs-lookup"><span data-stu-id="2ec6d-120">\<exposedMethods></span></span>](exposedmethods.md)|<span data-ttu-id="2ec6d-121">Kolekce prvků exposedMethod prvků >. [ \<](exposedmethod.md)</span><span class="sxs-lookup"><span data-stu-id="2ec6d-121">A collection of [\<exposedMethod>](exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ec6d-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2ec6d-122">Remarks</span></span>  
 <span data-ttu-id="2ec6d-123">Nástroj pro konfiguraci integrace COM+ (ComSvcConfig. exe) se dá použít k přidání specifických metod z rozhraní modelu COM, které se zobrazí na vygenerované kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="2ec6d-123">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="2ec6d-124">Například můžete použít následující příkaz a přidat tři pojmenované metody z `IFinances` rozhraní COM `ItemOrders`na. Finanční komponenta k vygenerované smlouvě služby.</span><span class="sxs-lookup"><span data-stu-id="2ec6d-124">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="2ec6d-125">Když spustíte také ComSvcConfig. exe, vygeneruje následující kontrakt služby, který uvádí dřív uvedené metody jako [ \<prvky prvků exposedMethod >](exposedmethod.md) .</span><span class="sxs-lookup"><span data-stu-id="2ec6d-125">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 <span data-ttu-id="2ec6d-126">V okamžiku inicializace služby se modul runtime pokusí vygenerovat kontrakt služby tím, že se odrážejí a přidá jenom metody, které jsou uvedené v [ \<](exposedmethod.md) seznamu prvků exposedmethodch prvků >.</span><span class="sxs-lookup"><span data-stu-id="2ec6d-126">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](exposedmethod.md) elements.</span></span> <span data-ttu-id="2ec6d-127">Trasování se vytvoří pro každou metodu rozhraní, která není zahrnutá v kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="2ec6d-127">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ec6d-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2ec6d-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [<span data-ttu-id="2ec6d-129">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="2ec6d-129">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="2ec6d-130">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="2ec6d-130">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="2ec6d-131">Postupy: Konfigurace nastavení služby modelu COM+</span><span class="sxs-lookup"><span data-stu-id="2ec6d-131">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
