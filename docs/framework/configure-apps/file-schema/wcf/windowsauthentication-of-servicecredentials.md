---
title: <windowsAuthentication> z <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: 81793b0d58a95166bc23f98d46ce94a5f1e1d018
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940294"
---
# <a name="windowsauthentication-of-servicecredentials"></a><span data-ttu-id="57dda-102">\<windowsAuthentication > \<ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="57dda-102">\<windowsAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="57dda-103">Určuje nastavení pověření služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="57dda-103">Specifies the settings of a Windows service credential.</span></span>  
  
 <span data-ttu-id="57dda-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="57dda-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="57dda-105">\<> chování</span><span class="sxs-lookup"><span data-stu-id="57dda-105">\<behaviors></span></span>  
<span data-ttu-id="57dda-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="57dda-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="57dda-107">\<> chování</span><span class="sxs-lookup"><span data-stu-id="57dda-107">\<behavior></span></span>  
<span data-ttu-id="57dda-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="57dda-108">\<serviceCredentials></span></span>  
<span data-ttu-id="57dda-109">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="57dda-109">\<windowsAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57dda-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57dda-110">Syntax</span></span>  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57dda-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="57dda-111">Attributes and Elements</span></span>  
 <span data-ttu-id="57dda-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="57dda-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57dda-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="57dda-113">Attributes</span></span>  
  
|<span data-ttu-id="57dda-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="57dda-114">Attribute</span></span>|<span data-ttu-id="57dda-115">Popis</span><span class="sxs-lookup"><span data-stu-id="57dda-115">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="57dda-116">Volitelný logický atribut, který určuje, zda systém zahrnuje skupiny systému Windows v kontextu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="57dda-116">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="57dda-117">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="57dda-117">The default is `true`.</span></span><br /><br /> <span data-ttu-id="57dda-118">Nastavení tohoto atributu na `true` má vliv na výkon, protože má za následek rozšíření úplného seskupení.</span><span class="sxs-lookup"><span data-stu-id="57dda-118">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="57dda-119">Nastavte tento atribut na `false` , pokud nepotřebujete vytvořit seznam skupin, do kterých uživatel patří.</span><span class="sxs-lookup"><span data-stu-id="57dda-119">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="57dda-120">Volitelný logický atribut, který určuje, zda jsou povoleny anonymní neověřené volající.</span><span class="sxs-lookup"><span data-stu-id="57dda-120">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="57dda-121">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="57dda-121">The default is `false`.</span></span><br /><br /> <span data-ttu-id="57dda-122">`Windows`Pokud je `clientCredentialType` atribut vazby nastaven na, systém nepovoluje anonymní volající.</span><span class="sxs-lookup"><span data-stu-id="57dda-122">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="57dda-123">To znamená, že přístup k systému má povolen pouze ověřený volající domény nebo pracovní skupiny.</span><span class="sxs-lookup"><span data-stu-id="57dda-123">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="57dda-124">Toto chování můžete přepsat pomocí tohoto atributu.</span><span class="sxs-lookup"><span data-stu-id="57dda-124">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="57dda-125">Toto nastavení se používá s mimořádnou opatrností.</span><span class="sxs-lookup"><span data-stu-id="57dda-125">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57dda-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="57dda-126">Child Elements</span></span>  
 <span data-ttu-id="57dda-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="57dda-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="57dda-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="57dda-128">Parent Elements</span></span>  
  
|<span data-ttu-id="57dda-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="57dda-129">Element</span></span>|<span data-ttu-id="57dda-130">Popis</span><span class="sxs-lookup"><span data-stu-id="57dda-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57dda-131">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="57dda-131">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="57dda-132">Určuje přihlašovací údaje, které se mají použít při ověřování služby, a nastavení související s ověřením přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="57dda-132">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57dda-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="57dda-133">Remarks</span></span>  
 <span data-ttu-id="57dda-134">Tento prvek použijte k určení, zda má být povolen anonymní přístup uživatelů systému Windows `allowAnonymousLogons` nastavením atributu.</span><span class="sxs-lookup"><span data-stu-id="57dda-134">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="57dda-135">Nastavením `includeWindowsGroups` atributu můžete také určit, jestli se mají zahrnout informace o skupině, ke kterým uživatelé patří, do AuthorizationContext.</span><span class="sxs-lookup"><span data-stu-id="57dda-135">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="57dda-136">Pokud je nastavená na `true` (výchozí nastavení), může služba určit skupiny systému Windows, ke kterým klient patří.</span><span class="sxs-lookup"><span data-stu-id="57dda-136">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57dda-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57dda-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
