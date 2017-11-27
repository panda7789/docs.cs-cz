---
title: "&lt;add&gt; – &lt;transportConfigurationType&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cb00a5d5a2b4f64cdce6832faef4822b63f426d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-lttransportconfigurationtypegt"></a><span data-ttu-id="663d1-102">&lt;add&gt; – &lt;transportConfigurationType&gt;</span><span class="sxs-lookup"><span data-stu-id="663d1-102">&lt;add&gt; of &lt;transportConfigurationType&gt;</span></span>
<span data-ttu-id="663d1-103">Tento element je dvojice klíč/hodnota, které jsou uvedeny typy konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="663d1-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
 <span data-ttu-id="663d1-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="663d1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="663d1-105">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="663d1-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="663d1-106">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="663d1-106">\<transportConfigurationTypes></span></span>  
<span data-ttu-id="663d1-107">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="663d1-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="663d1-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="663d1-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="String"  
               transportConfigurationType="String"/>   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="663d1-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="663d1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="663d1-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="663d1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="663d1-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="663d1-111">Attributes</span></span>  
  
|<span data-ttu-id="663d1-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="663d1-112">Attribute</span></span>|<span data-ttu-id="663d1-113">Popis</span><span class="sxs-lookup"><span data-stu-id="663d1-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="663d1-114">name</span><span class="sxs-lookup"><span data-stu-id="663d1-114">name</span></span>|<span data-ttu-id="663d1-115">Požadovaný atribut řetězec.</span><span class="sxs-lookup"><span data-stu-id="663d1-115">Required String attribute.</span></span><br /><br /> <span data-ttu-id="663d1-116">Obsahuje klíč definovaný uživatelem, který jedinečně identifikuje typ přenosu.</span><span class="sxs-lookup"><span data-stu-id="663d1-116">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="663d1-117">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="663d1-117">transportConfigurationType</span></span>|<span data-ttu-id="663d1-118">Řetězec, který obsahuje typ, který implementuje konkrétní přenosu.</span><span class="sxs-lookup"><span data-stu-id="663d1-118">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="663d1-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="663d1-119">Child Elements</span></span>  
 <span data-ttu-id="663d1-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="663d1-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="663d1-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="663d1-121">Parent Elements</span></span>  
  
|<span data-ttu-id="663d1-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="663d1-122">Element</span></span>|<span data-ttu-id="663d1-123">Popis</span><span class="sxs-lookup"><span data-stu-id="663d1-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="663d1-124">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="663d1-124">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="663d1-125">Kolekce typů, které implementují konkrétní přenosu.</span><span class="sxs-lookup"><span data-stu-id="663d1-125">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="663d1-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="663d1-126">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="net.udp"  
      transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="see-also"></a><span data-ttu-id="663d1-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="663d1-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="663d1-128">Hostování</span><span class="sxs-lookup"><span data-stu-id="663d1-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
