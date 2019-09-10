---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 4be08f780c1095b0016bd130b5719a2a7307d019
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854923"
---
# <a name="transportconfigurationtypes"></a><span data-ttu-id="eed97-101">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="eed97-101">\<transportConfigurationTypes></span></span>
<span data-ttu-id="eed97-102">Představuje kolekci elementů konfigurace, které identifikují typ konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="eed97-102">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="eed97-103">Dá se použít k přidání vlastních protokolů.</span><span class="sxs-lookup"><span data-stu-id="eed97-103">This can be used to add custom WAS protocols.</span></span>  
  
<span data-ttu-id="eed97-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="eed97-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="eed97-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="eed97-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="eed97-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceHostingEnvironment >** ](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="eed97-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="eed97-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transportConfigurationTypes >**</span><span class="sxs-lookup"><span data-stu-id="eed97-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transportConfigurationTypes>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eed97-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eed97-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eed97-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="eed97-109">Attributes and Elements</span></span>  
 <span data-ttu-id="eed97-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="eed97-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eed97-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="eed97-111">Attributes</span></span>  
  
|<span data-ttu-id="eed97-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="eed97-112">Attribute</span></span>|<span data-ttu-id="eed97-113">Popis</span><span class="sxs-lookup"><span data-stu-id="eed97-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eed97-114">name</span><span class="sxs-lookup"><span data-stu-id="eed97-114">name</span></span>|<span data-ttu-id="eed97-115">Název přenosu</span><span class="sxs-lookup"><span data-stu-id="eed97-115">The name of the transport</span></span>|  
|<span data-ttu-id="eed97-116">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="eed97-116">transportConfigurationType</span></span>|<span data-ttu-id="eed97-117">Typ, který implementuje přenos</span><span class="sxs-lookup"><span data-stu-id="eed97-117">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eed97-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="eed97-118">Child Elements</span></span>  
  
|<span data-ttu-id="eed97-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="eed97-119">Element</span></span>|<span data-ttu-id="eed97-120">Popis</span><span class="sxs-lookup"><span data-stu-id="eed97-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eed97-121">\<add></span><span class="sxs-lookup"><span data-stu-id="eed97-121">\<add></span></span>](add-of-transportconfigurationtype.md)|<span data-ttu-id="eed97-122">Přidá prvek konfigurace, který identifikuje typ konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="eed97-122">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eed97-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="eed97-123">Parent Elements</span></span>  
  
|<span data-ttu-id="eed97-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="eed97-124">Element</span></span>|<span data-ttu-id="eed97-125">Popis</span><span class="sxs-lookup"><span data-stu-id="eed97-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eed97-126">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="eed97-126">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="eed97-127">Definuje typ, který hostující prostředí služby vytvoří pro konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="eed97-127">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eed97-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eed97-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="eed97-129">Hostování</span><span class="sxs-lookup"><span data-stu-id="eed97-129">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
