---
title: <claimTypeRequired>
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: 1c40c5e4b4a24a3c1bbd6e096f12b7b044331c88
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252053"
---
# <a name="claimtyperequired"></a><span data-ttu-id="7e4f5-101">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="7e4f5-101">\<claimTypeRequired></span></span>
<span data-ttu-id="7e4f5-102">Určuje sadu požadovaných deklarací pro příchozí tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7e4f5-102">Specifies the set of required claims for incoming security tokens.</span></span>  
  
<span data-ttu-id="7e4f5-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7e4f5-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7e4f5-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="7e4f5-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="7e4f5-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="7e4f5-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="7e4f5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<claimTypeRequired >**</span><span class="sxs-lookup"><span data-stu-id="7e4f5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimTypeRequired>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e4f5-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e4f5-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e4f5-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7e4f5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7e4f5-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7e4f5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e4f5-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="7e4f5-110">Attributes</span></span>  
 <span data-ttu-id="7e4f5-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="7e4f5-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7e4f5-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7e4f5-112">Child Elements</span></span>  
  
|<span data-ttu-id="7e4f5-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="7e4f5-113">Element</span></span>|<span data-ttu-id="7e4f5-114">Popis</span><span class="sxs-lookup"><span data-stu-id="7e4f5-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e4f5-115">\<claimType></span><span class="sxs-lookup"><span data-stu-id="7e4f5-115">\<claimType></span></span>](claimtype.md)|<span data-ttu-id="7e4f5-116">Určuje jednu volitelnou nebo požadovanou deklaraci příchozích tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7e4f5-116">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7e4f5-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7e4f5-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7e4f5-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="7e4f5-118">Element</span></span>|<span data-ttu-id="7e4f5-119">Popis</span><span class="sxs-lookup"><span data-stu-id="7e4f5-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e4f5-120">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="7e4f5-120">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="7e4f5-121">Určuje nastavení identity na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="7e4f5-121">Specifies service-level identity settings.</span></span>|
