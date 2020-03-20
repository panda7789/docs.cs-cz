---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: ade55a5b26826633faf2e7ef7598a4071d613bbc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152538"
---
# <a name="sessiontokenrequirement"></a><span data-ttu-id="c06b6-101">\<> sessionTokenRequirement</span><span class="sxs-lookup"><span data-stu-id="c06b6-101">\<sessionTokenRequirement></span></span>
<span data-ttu-id="c06b6-102">Poskytuje konfiguraci <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> pro třídu nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="c06b6-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="c06b6-103">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c06b6-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c06b6-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="c06b6-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="c06b6-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityKonfigurace>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="c06b6-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="c06b6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="c06b6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="c06b6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<přidat>**](add.md)</span><span class="sxs-lookup"><span data-stu-id="c06b6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="c06b6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>sessionTokenRequirement**</span><span class="sxs-lookup"><span data-stu-id="c06b6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c06b6-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c06b6-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c06b6-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c06b6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c06b6-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c06b6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c06b6-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="c06b6-112">Attributes</span></span>  
  
|<span data-ttu-id="c06b6-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="c06b6-113">Attribute</span></span>|<span data-ttu-id="c06b6-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c06b6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c06b6-115">doba platnosti</span><span class="sxs-lookup"><span data-stu-id="c06b6-115">lifetime</span></span>|<span data-ttu-id="c06b6-116">Určuje životnost tokenů relace.</span><span class="sxs-lookup"><span data-stu-id="c06b6-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c06b6-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c06b6-117">Child Elements</span></span>  
 <span data-ttu-id="c06b6-118">Žádný</span><span class="sxs-lookup"><span data-stu-id="c06b6-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c06b6-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c06b6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c06b6-120">Element</span><span class="sxs-lookup"><span data-stu-id="c06b6-120">Element</span></span>|<span data-ttu-id="c06b6-121">Popis</span><span class="sxs-lookup"><span data-stu-id="c06b6-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c06b6-122">\<přidat></span><span class="sxs-lookup"><span data-stu-id="c06b6-122">\<add></span></span>](add.md)|<span data-ttu-id="c06b6-123">Přidá zadanou obslužnou rutinu tokenu do kolekce obslužné rutiny tokenu.</span><span class="sxs-lookup"><span data-stu-id="c06b6-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c06b6-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="c06b6-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
