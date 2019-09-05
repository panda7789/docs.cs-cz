---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 968c48df9e92a1dfbfb6e248b06cf4f97cece8b4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251818"
---
# <a name="sessiontokenrequirement"></a><span data-ttu-id="09832-101">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="09832-101">\<sessionTokenRequirement></span></span>
<span data-ttu-id="09832-102">Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> třídu nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="09832-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="09832-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="09832-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="09832-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="09832-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="09832-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="09832-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="09832-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="09832-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="09832-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Přidat >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="09832-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="09832-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<sessionTokenRequirement >**</span><span class="sxs-lookup"><span data-stu-id="09832-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09832-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09832-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">  
        <sessionTokenRequirement lifetime=TimeSpan >  
        </sessionTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09832-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="09832-110">Attributes and Elements</span></span>  
 <span data-ttu-id="09832-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="09832-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09832-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="09832-112">Attributes</span></span>  
  
|<span data-ttu-id="09832-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="09832-113">Attribute</span></span>|<span data-ttu-id="09832-114">Popis</span><span class="sxs-lookup"><span data-stu-id="09832-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="09832-115">doba platnosti</span><span class="sxs-lookup"><span data-stu-id="09832-115">lifetime</span></span>|<span data-ttu-id="09832-116">Určuje dobu života tokenů relací.</span><span class="sxs-lookup"><span data-stu-id="09832-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09832-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="09832-117">Child Elements</span></span>  
 <span data-ttu-id="09832-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="09832-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="09832-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="09832-119">Parent Elements</span></span>  
  
|<span data-ttu-id="09832-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="09832-120">Element</span></span>|<span data-ttu-id="09832-121">Popis</span><span class="sxs-lookup"><span data-stu-id="09832-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09832-122">\<add></span><span class="sxs-lookup"><span data-stu-id="09832-122">\<add></span></span>](add.md)|<span data-ttu-id="09832-123">Přidá do kolekce obslužných rutin tokenu zadanou obslužnou rutinu tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="09832-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="09832-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="09832-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
