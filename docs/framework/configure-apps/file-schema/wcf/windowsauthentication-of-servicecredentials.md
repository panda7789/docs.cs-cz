---
title: "&lt;windowsAuthentication&gt; – &lt;serviceCredentials&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2b6043b35ea9dbed1e1e6e170035436038334b34
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltwindowsauthenticationgt-of-ltservicecredentialsgt"></a><span data-ttu-id="1a8b1-102">&lt;windowsAuthentication&gt; – &lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="1a8b1-102">&lt;windowsAuthentication&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="1a8b1-103">Určuje nastavení pověření služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="1a8b1-103">Specifies the settings of a Windows service credential.</span></span>  
  
 <span data-ttu-id="1a8b1-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1a8b1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1a8b1-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="1a8b1-105">\<behaviors></span></span>  
<span data-ttu-id="1a8b1-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="1a8b1-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="1a8b1-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="1a8b1-107">\<behavior></span></span>  
<span data-ttu-id="1a8b1-108">\<– serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="1a8b1-108">\<serviceCredentials></span></span>  
<span data-ttu-id="1a8b1-109">\<windowsAuthentication ></span><span class="sxs-lookup"><span data-stu-id="1a8b1-109">\<windowsAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a8b1-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a8b1-110">Syntax</span></span>  
  
```xml  
<windowsAuthentication  
      allowAnonymousLogons="Boolean"  
      includeWindowsGroups="Boolean" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a8b1-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1a8b1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1a8b1-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1a8b1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a8b1-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="1a8b1-113">Attributes</span></span>  
  
|<span data-ttu-id="1a8b1-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="1a8b1-114">Attribute</span></span>|<span data-ttu-id="1a8b1-115">Popis</span><span class="sxs-lookup"><span data-stu-id="1a8b1-115">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="1a8b1-116">Volitelný logický atribut, který určuje, zda systém zahrnuje skupiny systému Windows v kontextu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="1a8b1-116">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="1a8b1-117">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="1a8b1-117">The default is `true`.</span></span><br /><br /> <span data-ttu-id="1a8b1-118">Nastavení tohoto atributu na `true` má dopad na výkon, jako je výsledkem rozšíření skupiny úplné.</span><span class="sxs-lookup"><span data-stu-id="1a8b1-118">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="1a8b1-119">Nastavte tento atribut `false` Pokud není potřeba vytvořit seznam skupin uživatel patří do.</span><span class="sxs-lookup"><span data-stu-id="1a8b1-119">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="1a8b1-120">Volitelný logický atribut, který určuje, zda jsou povoleny anonymní, neověřené volající.</span><span class="sxs-lookup"><span data-stu-id="1a8b1-120">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="1a8b1-121">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="1a8b1-121">The default is `false`.</span></span><br /><br /> <span data-ttu-id="1a8b1-122">Když `clientCredentialType` atribut vazby je nastaven na `Windows`, systém nepovoluje anonymní volající.</span><span class="sxs-lookup"><span data-stu-id="1a8b1-122">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="1a8b1-123">To znamená, že pouze doméně nebo pracovní skupině authenticated volající mají povolena přístup k systému.</span><span class="sxs-lookup"><span data-stu-id="1a8b1-123">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="1a8b1-124">Toto chování můžete přepsat pomocí tohoto atributu.</span><span class="sxs-lookup"><span data-stu-id="1a8b1-124">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="1a8b1-125">Pomocí tohoto nastavení s velmi opatrní.</span><span class="sxs-lookup"><span data-stu-id="1a8b1-125">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1a8b1-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1a8b1-126">Child Elements</span></span>  
 <span data-ttu-id="1a8b1-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="1a8b1-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1a8b1-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1a8b1-128">Parent Elements</span></span>  
  
|<span data-ttu-id="1a8b1-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="1a8b1-129">Element</span></span>|<span data-ttu-id="1a8b1-130">Popis</span><span class="sxs-lookup"><span data-stu-id="1a8b1-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a8b1-131">\<– serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="1a8b1-131">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="1a8b1-132">Určuje pověření, která se použije v ověřování služby a nastavení související s ověření pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="1a8b1-132">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a8b1-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1a8b1-133">Remarks</span></span>  
 <span data-ttu-id="1a8b1-134">Tento prvek slouží k určení, zda povolit přístup anonymní uživatelé Windows nastavením `allowAnonymousLogons` atribut.</span><span class="sxs-lookup"><span data-stu-id="1a8b1-134">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="1a8b1-135">Můžete také určit, zda mají být zahrnuty informace o skupině, do které patří uživatelé kontext ověřování nastavením `includeWindowsGroups` atribut.</span><span class="sxs-lookup"><span data-stu-id="1a8b1-135">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="1a8b1-136">Pokud je nastaven na hodnotu `true` (výchozí nastavení), může služba zjistit skupiny systému Windows, na které klient patří.</span><span class="sxs-lookup"><span data-stu-id="1a8b1-136">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a8b1-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="1a8b1-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WindowsServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>  
 <xref:System.ServiceModel.Security.WindowsServiceCredential>
