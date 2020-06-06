---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 46f2872fb289c2793c356ea179deb3ce52e6d65e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855307"
---
# \<exposedMethod>
<span data-ttu-id="5006a-101">Představuje metodu COM+, která je vystavena v případě, že je rozhraní součásti modelu COM vystaveno jako webová služba.</span><span class="sxs-lookup"><span data-stu-id="5006a-101">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<exposedMethods>**](exposedmethods.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<exposedMethod>**  
  
## <a name="syntax"></a><span data-ttu-id="5006a-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5006a-102">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5006a-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5006a-103">Attributes and Elements</span></span>  
 <span data-ttu-id="5006a-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5006a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5006a-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="5006a-105">Attributes</span></span>  
  
|<span data-ttu-id="5006a-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="5006a-106">Attribute</span></span>|<span data-ttu-id="5006a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5006a-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5006a-108">name</span><span class="sxs-lookup"><span data-stu-id="5006a-108">name</span></span>|<span data-ttu-id="5006a-109">Řetězec obsahující metodu modelu COM+, která je vystavena v případě, že je rozhraní součásti modelu COM vystaveno jako webová služba.</span><span class="sxs-lookup"><span data-stu-id="5006a-109">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5006a-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5006a-110">Child Elements</span></span>  
 <span data-ttu-id="5006a-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="5006a-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5006a-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5006a-112">Parent Elements</span></span>  
  
|<span data-ttu-id="5006a-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="5006a-113">Element</span></span>|<span data-ttu-id="5006a-114">Description</span><span class="sxs-lookup"><span data-stu-id="5006a-114">Description</span></span>|  
|-------------|-----------------|  
|[\<exposedMethods>](exposedmethods.md)|<span data-ttu-id="5006a-115">Kolekce [\<exposedMethod>](exposedmethod.md) prvků.</span><span class="sxs-lookup"><span data-stu-id="5006a-115">A collection of [\<exposedMethod>](exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5006a-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5006a-116">Remarks</span></span>  
 <span data-ttu-id="5006a-117">Nástroj pro konfiguraci integrace COM+ (ComSvcConfig. exe) se dá použít k přidání specifických metod z rozhraní modelu COM, které se zobrazí na vygenerované kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="5006a-117">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="5006a-118">Například můžete použít následující příkaz a přidat tři pojmenované metody z `IFinances` rozhraní COM na `ItemOrders` . Finanční komponenta k vygenerované smlouvě služby.</span><span class="sxs-lookup"><span data-stu-id="5006a-118">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="5006a-119">Při spuštění nástroje ComSvcConfig. exe pak vygeneruje následující kontrakt služby, který obsahuje výše zmíněné metody jako [\<exposedMethod>](exposedmethod.md) prvky.</span><span class="sxs-lookup"><span data-stu-id="5006a-119">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 <span data-ttu-id="5006a-120">V okamžiku inicializace služby se modul runtime pokusí vygenerovat kontrakt služby tím, že se odrážejí a přidá pouze metody, které jsou obsaženy v seznamu [\<exposedMethod>](exposedmethod.md) prvků.</span><span class="sxs-lookup"><span data-stu-id="5006a-120">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](exposedmethod.md) elements.</span></span> <span data-ttu-id="5006a-121">Trasování se vytvoří pro každou metodu rozhraní, která není zahrnutá v kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="5006a-121">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5006a-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="5006a-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="5006a-123">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="5006a-123">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="5006a-124">Postupy: Konfigurace nastavení služby modelu COM+</span><span class="sxs-lookup"><span data-stu-id="5006a-124">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
