---
title: <add> z <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: 483ede53df13c896b88171910031dbe9793d66dc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920038"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="611e5-102">\<Přidat > \<> transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="611e5-102">\<add> of \<transportConfigurationType></span></span>
<span data-ttu-id="611e5-103">Tento prvek je dvojice klíč/hodnota, která určuje typ konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="611e5-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
 <span data-ttu-id="611e5-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="611e5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="611e5-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="611e5-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="611e5-106">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="611e5-106">\<transportConfigurationTypes></span></span>  
<span data-ttu-id="611e5-107">\<add></span><span class="sxs-lookup"><span data-stu-id="611e5-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="611e5-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="611e5-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="611e5-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="611e5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="611e5-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="611e5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="611e5-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="611e5-111">Attributes</span></span>  
  
|<span data-ttu-id="611e5-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="611e5-112">Attribute</span></span>|<span data-ttu-id="611e5-113">Popis</span><span class="sxs-lookup"><span data-stu-id="611e5-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="611e5-114">name</span><span class="sxs-lookup"><span data-stu-id="611e5-114">name</span></span>|<span data-ttu-id="611e5-115">Povinný atribut řetězce.</span><span class="sxs-lookup"><span data-stu-id="611e5-115">Required String attribute.</span></span><br /><br /> <span data-ttu-id="611e5-116">Obsahuje uživatelsky definovaný klíč, který jednoznačně identifikuje typ přenosu.</span><span class="sxs-lookup"><span data-stu-id="611e5-116">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="611e5-117">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="611e5-117">transportConfigurationType</span></span>|<span data-ttu-id="611e5-118">Řetězec obsahující typ, který implementuje konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="611e5-118">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="611e5-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="611e5-119">Child Elements</span></span>  
 <span data-ttu-id="611e5-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="611e5-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="611e5-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="611e5-121">Parent Elements</span></span>  
  
|<span data-ttu-id="611e5-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="611e5-122">Element</span></span>|<span data-ttu-id="611e5-123">Popis</span><span class="sxs-lookup"><span data-stu-id="611e5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="611e5-124">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="611e5-124">\<transportConfigurationTypes></span></span>](transportconfigurationtypes.md)|<span data-ttu-id="611e5-125">Kolekce typů, které implementují konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="611e5-125">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="611e5-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="611e5-126">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="611e5-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="611e5-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="611e5-128">Hostování</span><span class="sxs-lookup"><span data-stu-id="611e5-128">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
