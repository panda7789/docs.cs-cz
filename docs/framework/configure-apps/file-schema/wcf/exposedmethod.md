---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 46f2872fb289c2793c356ea179deb3ce52e6d65e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855307"
---
# <a name="exposedmethod"></a><span data-ttu-id="5e9f8-101">\<Prvků exposedMethod ></span><span class="sxs-lookup"><span data-stu-id="5e9f8-101">\<exposedMethod></span></span>
<span data-ttu-id="5e9f8-102">Představuje metodu COM+, která je vystavena v případě, že je rozhraní součásti modelu COM vystaveno jako webová služba.</span><span class="sxs-lookup"><span data-stu-id="5e9f8-102">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
<span data-ttu-id="5e9f8-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5e9f8-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5e9f8-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5e9f8-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5e9f8-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Konfigurační oddíl comContracts >** ](comcontracts.md)</span><span class="sxs-lookup"><span data-stu-id="5e9f8-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)</span></span>\
<span data-ttu-id="5e9f8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comContract >** ](comcontract.md)</span><span class="sxs-lookup"><span data-stu-id="5e9f8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)</span></span>\
<span data-ttu-id="5e9f8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<exposedMethods >** ](exposedmethods.md)</span><span class="sxs-lookup"><span data-stu-id="5e9f8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<exposedMethods>**](exposedmethods.md)</span></span>\
<span data-ttu-id="5e9f8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Prvků exposedMethod >**</span><span class="sxs-lookup"><span data-stu-id="5e9f8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<exposedMethod>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e9f8-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e9f8-109">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e9f8-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5e9f8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5e9f8-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5e9f8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e9f8-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="5e9f8-112">Attributes</span></span>  
  
|<span data-ttu-id="5e9f8-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="5e9f8-113">Attribute</span></span>|<span data-ttu-id="5e9f8-114">Popis</span><span class="sxs-lookup"><span data-stu-id="5e9f8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5e9f8-115">name</span><span class="sxs-lookup"><span data-stu-id="5e9f8-115">name</span></span>|<span data-ttu-id="5e9f8-116">Řetězec obsahující metodu modelu COM+, která je vystavena v případě, že je rozhraní součásti modelu COM vystaveno jako webová služba.</span><span class="sxs-lookup"><span data-stu-id="5e9f8-116">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e9f8-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5e9f8-117">Child Elements</span></span>  
 <span data-ttu-id="5e9f8-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="5e9f8-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5e9f8-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5e9f8-119">Parent Elements</span></span>  
  
|<span data-ttu-id="5e9f8-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="5e9f8-120">Element</span></span>|<span data-ttu-id="5e9f8-121">Popis</span><span class="sxs-lookup"><span data-stu-id="5e9f8-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e9f8-122">\<exposedMethods ></span><span class="sxs-lookup"><span data-stu-id="5e9f8-122">\<exposedMethods></span></span>](exposedmethods.md)|<span data-ttu-id="5e9f8-123">Kolekce prvků exposedMethod prvků >. [ \<](exposedmethod.md)</span><span class="sxs-lookup"><span data-stu-id="5e9f8-123">A collection of [\<exposedMethod>](exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e9f8-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5e9f8-124">Remarks</span></span>  
 <span data-ttu-id="5e9f8-125">Nástroj pro konfiguraci integrace COM+ (ComSvcConfig. exe) se dá použít k přidání specifických metod z rozhraní modelu COM, které se zobrazí na vygenerované kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="5e9f8-125">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="5e9f8-126">Například můžete použít následující příkaz a přidat tři pojmenované metody z `IFinances` rozhraní COM `ItemOrders`na. Finanční komponenta k vygenerované smlouvě služby.</span><span class="sxs-lookup"><span data-stu-id="5e9f8-126">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="5e9f8-127">Když spustíte také ComSvcConfig. exe, vygeneruje následující kontrakt služby, který uvádí dřív uvedené metody jako [ \<prvky prvků exposedMethod >](exposedmethod.md) .</span><span class="sxs-lookup"><span data-stu-id="5e9f8-127">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 <span data-ttu-id="5e9f8-128">V okamžiku inicializace služby se modul runtime pokusí vygenerovat kontrakt služby tím, že se odrážejí a přidá jenom metody, které jsou uvedené v seznamu [ \<prvků exposedmethodch prvků >](exposedmethod.md) .</span><span class="sxs-lookup"><span data-stu-id="5e9f8-128">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](exposedmethod.md) elements.</span></span> <span data-ttu-id="5e9f8-129">Trasování se vytvoří pro každou metodu rozhraní, která není zahrnutá v kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="5e9f8-129">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e9f8-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e9f8-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [<span data-ttu-id="5e9f8-131">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="5e9f8-131">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="5e9f8-132">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="5e9f8-132">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="5e9f8-133">Postupy: Konfigurace nastavení služby modelu COM+</span><span class="sxs-lookup"><span data-stu-id="5e9f8-133">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
