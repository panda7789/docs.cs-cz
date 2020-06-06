---
title: <add> z <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: adf4cd7f02db6535c5950443d09476a9a5ff63fb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850317"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="71294-102">\<add> z \<transportConfigurationType></span><span class="sxs-lookup"><span data-stu-id="71294-102">\<add> of \<transportConfigurationType></span></span>
<span data-ttu-id="71294-103">Tento prvek je dvojice klíč/hodnota, která určuje typ konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="71294-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<transportConfigurationTypes>**](transportconfigurationtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="71294-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71294-104">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71294-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="71294-105">Attributes and Elements</span></span>  
 <span data-ttu-id="71294-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="71294-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71294-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="71294-107">Attributes</span></span>  
  
|<span data-ttu-id="71294-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="71294-108">Attribute</span></span>|<span data-ttu-id="71294-109">Popis</span><span class="sxs-lookup"><span data-stu-id="71294-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="71294-110">name</span><span class="sxs-lookup"><span data-stu-id="71294-110">name</span></span>|<span data-ttu-id="71294-111">Povinný atribut řetězce.</span><span class="sxs-lookup"><span data-stu-id="71294-111">Required String attribute.</span></span><br /><br /> <span data-ttu-id="71294-112">Obsahuje uživatelsky definovaný klíč, který jednoznačně identifikuje typ přenosu.</span><span class="sxs-lookup"><span data-stu-id="71294-112">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="71294-113">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="71294-113">transportConfigurationType</span></span>|<span data-ttu-id="71294-114">Řetězec obsahující typ, který implementuje konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="71294-114">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71294-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="71294-115">Child Elements</span></span>  
 <span data-ttu-id="71294-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="71294-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="71294-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="71294-117">Parent Elements</span></span>  
  
|<span data-ttu-id="71294-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="71294-118">Element</span></span>|<span data-ttu-id="71294-119">Description</span><span class="sxs-lookup"><span data-stu-id="71294-119">Description</span></span>|  
|-------------|-----------------|  
|[\<transportConfigurationTypes>](transportconfigurationtypes.md)|<span data-ttu-id="71294-120">Kolekce typů, které implementují konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="71294-120">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="71294-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="71294-121">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="71294-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="71294-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="71294-123">Hosting</span><span class="sxs-lookup"><span data-stu-id="71294-123">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
