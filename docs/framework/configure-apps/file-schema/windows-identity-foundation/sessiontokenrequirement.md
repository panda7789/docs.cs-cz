---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: ade55a5b26826633faf2e7ef7598a4071d613bbc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152538"
---
# \<sessionTokenRequirement>
<span data-ttu-id="59e3e-101">Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> třídu nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="59e3e-101">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="59e3e-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59e3e-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59e3e-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="59e3e-103">Attributes and Elements</span></span>  
 <span data-ttu-id="59e3e-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="59e3e-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59e3e-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="59e3e-105">Attributes</span></span>  
  
|<span data-ttu-id="59e3e-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="59e3e-106">Attribute</span></span>|<span data-ttu-id="59e3e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="59e3e-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59e3e-108">doba platnosti</span><span class="sxs-lookup"><span data-stu-id="59e3e-108">lifetime</span></span>|<span data-ttu-id="59e3e-109">Určuje dobu života tokenů relací.</span><span class="sxs-lookup"><span data-stu-id="59e3e-109">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59e3e-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="59e3e-110">Child Elements</span></span>  
 <span data-ttu-id="59e3e-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="59e3e-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59e3e-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="59e3e-112">Parent Elements</span></span>  
  
|<span data-ttu-id="59e3e-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="59e3e-113">Element</span></span>|<span data-ttu-id="59e3e-114">Description</span><span class="sxs-lookup"><span data-stu-id="59e3e-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="59e3e-115">Přidá do kolekce obslužných rutin tokenu zadanou obslužnou rutinu tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="59e3e-115">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="59e3e-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="59e3e-116">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
