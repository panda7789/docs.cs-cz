---
title: '&lt;add&gt; – &lt;transportConfigurationType&gt;'
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: 1079b25ce137dc89fc31f46a11f3720486462021
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149134"
---
# <a name="ltaddgt-of-lttransportconfigurationtypegt"></a><span data-ttu-id="38184-102">&lt;add&gt; – &lt;transportConfigurationType&gt;</span><span class="sxs-lookup"><span data-stu-id="38184-102">&lt;add&gt; of &lt;transportConfigurationType&gt;</span></span>
<span data-ttu-id="38184-103">Tento element je dvojice klíč/hodnota, která identifikuje typ konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="38184-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
 <span data-ttu-id="38184-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="38184-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="38184-105">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="38184-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="38184-106">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="38184-106">\<transportConfigurationTypes></span></span>  
<span data-ttu-id="38184-107">\<add></span><span class="sxs-lookup"><span data-stu-id="38184-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38184-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38184-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38184-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="38184-109">Attributes and Elements</span></span>  
 <span data-ttu-id="38184-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="38184-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38184-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="38184-111">Attributes</span></span>  
  
|<span data-ttu-id="38184-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="38184-112">Attribute</span></span>|<span data-ttu-id="38184-113">Popis</span><span class="sxs-lookup"><span data-stu-id="38184-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38184-114">name</span><span class="sxs-lookup"><span data-stu-id="38184-114">name</span></span>|<span data-ttu-id="38184-115">Povinný atribut řetězce.</span><span class="sxs-lookup"><span data-stu-id="38184-115">Required String attribute.</span></span><br /><br /> <span data-ttu-id="38184-116">Obsahuje klíč definovaný uživatelem, který jednoznačně identifikuje typ přenosu.</span><span class="sxs-lookup"><span data-stu-id="38184-116">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="38184-117">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="38184-117">transportConfigurationType</span></span>|<span data-ttu-id="38184-118">Řetězec, který obsahuje typ, který implementuje konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="38184-118">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38184-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="38184-119">Child Elements</span></span>  
 <span data-ttu-id="38184-120">Žádná</span><span class="sxs-lookup"><span data-stu-id="38184-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38184-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="38184-121">Parent Elements</span></span>  
  
|<span data-ttu-id="38184-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="38184-122">Element</span></span>|<span data-ttu-id="38184-123">Popis</span><span class="sxs-lookup"><span data-stu-id="38184-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38184-124">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="38184-124">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="38184-125">Kolekce typů, které implementují konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="38184-125">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="38184-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="38184-126">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="38184-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="38184-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="38184-128">Hostování</span><span class="sxs-lookup"><span data-stu-id="38184-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
