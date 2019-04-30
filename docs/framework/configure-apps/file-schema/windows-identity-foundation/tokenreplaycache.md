---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 1567c669b5e682a7a771d7bedc95a8effa474e36
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790504"
---
# <a name="tokenreplaycache"></a><span data-ttu-id="aa124-101">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="aa124-101">\<tokenReplayCache></span></span>
<span data-ttu-id="aa124-102">Registruje mezipaměti opětovného přehrání tokenu služby nebo kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="aa124-102">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="aa124-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="aa124-103">\<system.identityModel></span></span>  
<span data-ttu-id="aa124-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="aa124-104">\<identityConfiguration></span></span>  
<span data-ttu-id="aa124-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="aa124-105">\<caches></span></span>  
<span data-ttu-id="aa124-106">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="aa124-106">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa124-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa124-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <tokenReplayCache type=xs:string>  
      </tokenReplayCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa124-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="aa124-108">Attributes and Elements</span></span>  
 <span data-ttu-id="aa124-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="aa124-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa124-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="aa124-110">Attributes</span></span>  
  
|<span data-ttu-id="aa124-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="aa124-111">Attribute</span></span>|<span data-ttu-id="aa124-112">Popis</span><span class="sxs-lookup"><span data-stu-id="aa124-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aa124-113"> – typ</span><span class="sxs-lookup"><span data-stu-id="aa124-113">type</span></span>|<span data-ttu-id="aa124-114">Typ, který je odvozen od <xref:System.IdentityModel.Tokens.TokenReplayCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="aa124-114">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="aa124-115">Další informace o tom, jak určit vlastní `type`, najdete v článku [vlastní typ reference].</span><span class="sxs-lookup"><span data-stu-id="aa124-115">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="aa124-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="aa124-116">Child Elements</span></span>  
 <span data-ttu-id="aa124-117">Žádný</span><span class="sxs-lookup"><span data-stu-id="aa124-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aa124-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="aa124-118">Parent Elements</span></span>  
  
|<span data-ttu-id="aa124-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="aa124-119">Element</span></span>|<span data-ttu-id="aa124-120">Popis</span><span class="sxs-lookup"><span data-stu-id="aa124-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aa124-121">\<caches></span><span class="sxs-lookup"><span data-stu-id="aa124-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="aa124-122">Zaregistruje mezipamětí používá službu nebo kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="aa124-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa124-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aa124-123">Remarks</span></span>  
 <span data-ttu-id="aa124-124">Mezipaměť opětovného přehrání tokenu slouží ke zjištění přehraná tokeny.</span><span class="sxs-lookup"><span data-stu-id="aa124-124">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="aa124-125">Rozpoznání opětovného přehrání tokenu je povoleno podle [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, který také určuje, maximální dobu vypršení platnosti tokenů.</span><span class="sxs-lookup"><span data-stu-id="aa124-125">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa124-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="aa124-126">Example</span></span>  
 <span data-ttu-id="aa124-127">Následující kód XML ukazuje konfiguraci vlastní mezipaměti pro zjišťování přehraná tokeny.</span><span class="sxs-lookup"><span data-stu-id="aa124-127">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aa124-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa124-128">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [<span data-ttu-id="aa124-129">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="aa124-129">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
