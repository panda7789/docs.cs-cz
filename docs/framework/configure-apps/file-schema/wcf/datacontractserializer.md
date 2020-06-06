---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: e6524c18780c062c3b5b7dfc2509449cb208e270
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400434"
---
# <a name="datacontractserializer"></a><span data-ttu-id="99d11-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="99d11-102">dataContractSerializer</span></span>
<span data-ttu-id="99d11-103">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="99d11-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="99d11-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99d11-104">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99d11-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="99d11-105">Attributes and Elements</span></span>  
 <span data-ttu-id="99d11-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="99d11-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99d11-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="99d11-107">Attributes</span></span>  
  
|<span data-ttu-id="99d11-108">Prvek</span><span class="sxs-lookup"><span data-stu-id="99d11-108">Element</span></span>|<span data-ttu-id="99d11-109">Description</span><span class="sxs-lookup"><span data-stu-id="99d11-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="99d11-110">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="99d11-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="99d11-111">Logická hodnota, která určuje, zda se mají ignorovat data poskytnutá koncovým bodem při jeho serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="99d11-111">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="99d11-112">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="99d11-112">maxItemsInObjectGraph</span></span>|<span data-ttu-id="99d11-113">Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="99d11-113">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99d11-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="99d11-114">Child Elements</span></span>  
 <span data-ttu-id="99d11-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="99d11-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="99d11-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="99d11-116">Parent Elements</span></span>  
  
|<span data-ttu-id="99d11-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="99d11-117">Element</span></span>|<span data-ttu-id="99d11-118">Description</span><span class="sxs-lookup"><span data-stu-id="99d11-118">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="99d11-119">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="99d11-119">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99d11-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="99d11-120">Remarks</span></span>  
 <span data-ttu-id="99d11-121"><xref:System.Runtime.Serialization.DataContractSerializer>Další informace o známých typech naleznete v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="99d11-121">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="99d11-122">`<dataContractSerializer>`Prvek chování (je-li k dispozici) by se měl vždy zobrazit před `<enableWebScript>` prvkem chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="99d11-122">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="99d11-123">V opačném případě není výsledné chování definováno.</span><span class="sxs-lookup"><span data-stu-id="99d11-123">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99d11-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="99d11-124">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="99d11-125">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="99d11-125">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="99d11-126">Přenos a serializace dat</span><span class="sxs-lookup"><span data-stu-id="99d11-126">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
