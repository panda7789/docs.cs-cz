---
title: <add> z <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: adf4cd7f02db6535c5950443d09476a9a5ff63fb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850317"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="12e5c-102">\<Přidat > \<> transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="12e5c-102">\<add> of \<transportConfigurationType></span></span>
<span data-ttu-id="12e5c-103">Tento prvek je dvojice klíč/hodnota, která určuje typ konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="12e5c-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
<span data-ttu-id="12e5c-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="12e5c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="12e5c-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="12e5c-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="12e5c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceHostingEnvironment >** ](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="12e5c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="12e5c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<transportConfigurationTypes >** ](transportconfigurationtypes.md)</span><span class="sxs-lookup"><span data-stu-id="12e5c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<transportConfigurationTypes>**](transportconfigurationtypes.md)</span></span>\
<span data-ttu-id="12e5c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="12e5c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12e5c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12e5c-109">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12e5c-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="12e5c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="12e5c-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="12e5c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12e5c-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="12e5c-112">Attributes</span></span>  
  
|<span data-ttu-id="12e5c-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="12e5c-113">Attribute</span></span>|<span data-ttu-id="12e5c-114">Popis</span><span class="sxs-lookup"><span data-stu-id="12e5c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="12e5c-115">name</span><span class="sxs-lookup"><span data-stu-id="12e5c-115">name</span></span>|<span data-ttu-id="12e5c-116">Povinný atribut řetězce.</span><span class="sxs-lookup"><span data-stu-id="12e5c-116">Required String attribute.</span></span><br /><br /> <span data-ttu-id="12e5c-117">Obsahuje uživatelsky definovaný klíč, který jednoznačně identifikuje typ přenosu.</span><span class="sxs-lookup"><span data-stu-id="12e5c-117">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="12e5c-118">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="12e5c-118">transportConfigurationType</span></span>|<span data-ttu-id="12e5c-119">Řetězec obsahující typ, který implementuje konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="12e5c-119">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="12e5c-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="12e5c-120">Child Elements</span></span>  
 <span data-ttu-id="12e5c-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="12e5c-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="12e5c-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="12e5c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="12e5c-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="12e5c-123">Element</span></span>|<span data-ttu-id="12e5c-124">Popis</span><span class="sxs-lookup"><span data-stu-id="12e5c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12e5c-125">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="12e5c-125">\<transportConfigurationTypes></span></span>](transportconfigurationtypes.md)|<span data-ttu-id="12e5c-126">Kolekce typů, které implementují konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="12e5c-126">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="12e5c-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="12e5c-127">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="12e5c-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12e5c-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="12e5c-129">Hostování</span><span class="sxs-lookup"><span data-stu-id="12e5c-129">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
