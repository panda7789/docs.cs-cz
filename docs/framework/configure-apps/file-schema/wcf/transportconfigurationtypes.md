---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 4be08f780c1095b0016bd130b5719a2a7307d019
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854923"
---
# \<transportConfigurationTypes>
<span data-ttu-id="20c0b-101">Představuje kolekci elementů konfigurace, které identifikují typ konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="20c0b-101">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="20c0b-102">Dá se použít k přidání vlastních protokolů.</span><span class="sxs-lookup"><span data-stu-id="20c0b-102">This can be used to add custom WAS protocols.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transportConfigurationTypes>**  
  
## <a name="syntax"></a><span data-ttu-id="20c0b-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20c0b-103">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20c0b-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="20c0b-104">Attributes and Elements</span></span>  
 <span data-ttu-id="20c0b-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="20c0b-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20c0b-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="20c0b-106">Attributes</span></span>  
  
|<span data-ttu-id="20c0b-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="20c0b-107">Attribute</span></span>|<span data-ttu-id="20c0b-108">Popis</span><span class="sxs-lookup"><span data-stu-id="20c0b-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="20c0b-109">name</span><span class="sxs-lookup"><span data-stu-id="20c0b-109">name</span></span>|<span data-ttu-id="20c0b-110">Název přenosu</span><span class="sxs-lookup"><span data-stu-id="20c0b-110">The name of the transport</span></span>|  
|<span data-ttu-id="20c0b-111">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="20c0b-111">transportConfigurationType</span></span>|<span data-ttu-id="20c0b-112">Typ, který implementuje přenos</span><span class="sxs-lookup"><span data-stu-id="20c0b-112">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="20c0b-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="20c0b-113">Child Elements</span></span>  
  
|<span data-ttu-id="20c0b-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="20c0b-114">Element</span></span>|<span data-ttu-id="20c0b-115">Description</span><span class="sxs-lookup"><span data-stu-id="20c0b-115">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-transportconfigurationtype.md)|<span data-ttu-id="20c0b-116">Přidá prvek konfigurace, který identifikuje typ konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="20c0b-116">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="20c0b-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="20c0b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="20c0b-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="20c0b-118">Element</span></span>|<span data-ttu-id="20c0b-119">Description</span><span class="sxs-lookup"><span data-stu-id="20c0b-119">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="20c0b-120">Definuje typ, který hostující prostředí služby vytvoří pro konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="20c0b-120">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="20c0b-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="20c0b-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="20c0b-122">Hosting</span><span class="sxs-lookup"><span data-stu-id="20c0b-122">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
