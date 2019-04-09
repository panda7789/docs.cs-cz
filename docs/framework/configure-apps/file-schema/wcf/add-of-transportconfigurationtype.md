---
title: <add> of <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: c71a58b13e89bedb5eed24d784c82fb1525f7625
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126721"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="24adf-102">\<add> of \<transportConfigurationType></span><span class="sxs-lookup"><span data-stu-id="24adf-102">\<add> of \<transportConfigurationType></span></span>
<span data-ttu-id="24adf-103">Tento element je dvojice klíč/hodnota, která identifikuje typ konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="24adf-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
 <span data-ttu-id="24adf-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="24adf-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="24adf-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="24adf-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="24adf-106">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="24adf-106">\<transportConfigurationTypes></span></span>  
<span data-ttu-id="24adf-107">\<add></span><span class="sxs-lookup"><span data-stu-id="24adf-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24adf-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24adf-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24adf-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="24adf-109">Attributes and Elements</span></span>  
 <span data-ttu-id="24adf-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="24adf-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24adf-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="24adf-111">Attributes</span></span>  
  
|<span data-ttu-id="24adf-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="24adf-112">Attribute</span></span>|<span data-ttu-id="24adf-113">Popis</span><span class="sxs-lookup"><span data-stu-id="24adf-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="24adf-114">name</span><span class="sxs-lookup"><span data-stu-id="24adf-114">name</span></span>|<span data-ttu-id="24adf-115">Povinný atribut řetězce.</span><span class="sxs-lookup"><span data-stu-id="24adf-115">Required String attribute.</span></span><br /><br /> <span data-ttu-id="24adf-116">Obsahuje klíč definovaný uživatelem, který jednoznačně identifikuje typ přenosu.</span><span class="sxs-lookup"><span data-stu-id="24adf-116">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="24adf-117">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="24adf-117">transportConfigurationType</span></span>|<span data-ttu-id="24adf-118">Řetězec, který obsahuje typ, který implementuje konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="24adf-118">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="24adf-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="24adf-119">Child Elements</span></span>  
 <span data-ttu-id="24adf-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="24adf-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="24adf-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="24adf-121">Parent Elements</span></span>  
  
|<span data-ttu-id="24adf-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="24adf-122">Element</span></span>|<span data-ttu-id="24adf-123">Popis</span><span class="sxs-lookup"><span data-stu-id="24adf-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24adf-124">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="24adf-124">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="24adf-125">Kolekce typů, které implementují konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="24adf-125">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="24adf-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="24adf-126">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="24adf-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="24adf-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="24adf-128">Hostování</span><span class="sxs-lookup"><span data-stu-id="24adf-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
