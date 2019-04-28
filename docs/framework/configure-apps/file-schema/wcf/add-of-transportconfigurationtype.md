---
title: <add> z <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: c71a58b13e89bedb5eed24d784c82fb1525f7625
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701434"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="05bcb-102">\<add> of \<transportConfigurationType></span><span class="sxs-lookup"><span data-stu-id="05bcb-102">\<add> of \<transportConfigurationType></span></span>
<span data-ttu-id="05bcb-103">Tento element je dvojice klíč/hodnota, která identifikuje typ konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="05bcb-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
 <span data-ttu-id="05bcb-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="05bcb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="05bcb-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="05bcb-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="05bcb-106">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="05bcb-106">\<transportConfigurationTypes></span></span>  
<span data-ttu-id="05bcb-107">\<add></span><span class="sxs-lookup"><span data-stu-id="05bcb-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05bcb-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05bcb-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05bcb-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="05bcb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="05bcb-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="05bcb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05bcb-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="05bcb-111">Attributes</span></span>  
  
|<span data-ttu-id="05bcb-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="05bcb-112">Attribute</span></span>|<span data-ttu-id="05bcb-113">Popis</span><span class="sxs-lookup"><span data-stu-id="05bcb-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="05bcb-114">name</span><span class="sxs-lookup"><span data-stu-id="05bcb-114">name</span></span>|<span data-ttu-id="05bcb-115">Povinný atribut řetězce.</span><span class="sxs-lookup"><span data-stu-id="05bcb-115">Required String attribute.</span></span><br /><br /> <span data-ttu-id="05bcb-116">Obsahuje klíč definovaný uživatelem, který jednoznačně identifikuje typ přenosu.</span><span class="sxs-lookup"><span data-stu-id="05bcb-116">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="05bcb-117">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="05bcb-117">transportConfigurationType</span></span>|<span data-ttu-id="05bcb-118">Řetězec, který obsahuje typ, který implementuje konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="05bcb-118">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05bcb-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="05bcb-119">Child Elements</span></span>  
 <span data-ttu-id="05bcb-120">Žádný</span><span class="sxs-lookup"><span data-stu-id="05bcb-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05bcb-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="05bcb-121">Parent Elements</span></span>  
  
|<span data-ttu-id="05bcb-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="05bcb-122">Element</span></span>|<span data-ttu-id="05bcb-123">Popis</span><span class="sxs-lookup"><span data-stu-id="05bcb-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05bcb-124">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="05bcb-124">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="05bcb-125">Kolekce typů, které implementují konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="05bcb-125">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="05bcb-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="05bcb-126">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="05bcb-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05bcb-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="05bcb-128">Hostování</span><span class="sxs-lookup"><span data-stu-id="05bcb-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
