---
title: <claimTypeRequired>
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: 1c40c5e4b4a24a3c1bbd6e096f12b7b044331c88
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252053"
---
# \<claimTypeRequired>
<span data-ttu-id="4b782-101">Určuje sadu požadovaných deklarací pro příchozí tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4b782-101">Specifies the set of required claims for incoming security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimTypeRequired>**  
  
## <a name="syntax"></a><span data-ttu-id="4b782-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b782-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b782-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4b782-103">Attributes and Elements</span></span>  
 <span data-ttu-id="4b782-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4b782-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b782-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="4b782-105">Attributes</span></span>  
 <span data-ttu-id="4b782-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="4b782-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4b782-107">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4b782-107">Child Elements</span></span>  
  
|<span data-ttu-id="4b782-108">Prvek</span><span class="sxs-lookup"><span data-stu-id="4b782-108">Element</span></span>|<span data-ttu-id="4b782-109">Description</span><span class="sxs-lookup"><span data-stu-id="4b782-109">Description</span></span>|  
|-------------|-----------------|  
|[\<claimType>](claimtype.md)|<span data-ttu-id="4b782-110">Určuje jednu volitelnou nebo požadovanou deklaraci příchozích tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4b782-110">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4b782-111">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4b782-111">Parent Elements</span></span>  
  
|<span data-ttu-id="4b782-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="4b782-112">Element</span></span>|<span data-ttu-id="4b782-113">Description</span><span class="sxs-lookup"><span data-stu-id="4b782-113">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="4b782-114">Určuje nastavení identity na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="4b782-114">Specifies service-level identity settings.</span></span>|
