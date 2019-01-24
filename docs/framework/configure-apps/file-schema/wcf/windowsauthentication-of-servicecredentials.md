---
title: '&lt;windowsAuthentication&gt; – &lt;serviceCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: 3077baf49c13c91c6293823aa841525bf07ca7f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616261"
---
# <a name="ltwindowsauthenticationgt-of-ltservicecredentialsgt"></a><span data-ttu-id="a3fea-102">&lt;windowsAuthentication&gt; – &lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="a3fea-102">&lt;windowsAuthentication&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="a3fea-103">Určuje nastavení přihlašovacích údajů služby Windows.</span><span class="sxs-lookup"><span data-stu-id="a3fea-103">Specifies the settings of a Windows service credential.</span></span>  
  
 <span data-ttu-id="a3fea-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a3fea-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a3fea-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="a3fea-105">\<behaviors></span></span>  
<span data-ttu-id="a3fea-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="a3fea-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="a3fea-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="a3fea-107">\<behavior></span></span>  
<span data-ttu-id="a3fea-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="a3fea-108">\<serviceCredentials></span></span>  
<span data-ttu-id="a3fea-109">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="a3fea-109">\<windowsAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3fea-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3fea-110">Syntax</span></span>  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3fea-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a3fea-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a3fea-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a3fea-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3fea-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="a3fea-113">Attributes</span></span>  
  
|<span data-ttu-id="a3fea-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="a3fea-114">Attribute</span></span>|<span data-ttu-id="a3fea-115">Popis</span><span class="sxs-lookup"><span data-stu-id="a3fea-115">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="a3fea-116">Volitelný logický atribut, který určuje, zda tento systém zahrnuje skupiny Windows v kontextu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="a3fea-116">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="a3fea-117">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="a3fea-117">The default is `true`.</span></span><br /><br /> <span data-ttu-id="a3fea-118">Nastavení tohoto atributu na `true` má dopad na výkon, protože výsledkem rozšíření skupiny úplné.</span><span class="sxs-lookup"><span data-stu-id="a3fea-118">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="a3fea-119">Tento atribut nastavte na `false` Pokud není potřeba vytvořit seznam skupin uživatel patří.</span><span class="sxs-lookup"><span data-stu-id="a3fea-119">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="a3fea-120">Volitelný logický atribut, který určuje, jestli jsou povolené anonymní, neověření volající.</span><span class="sxs-lookup"><span data-stu-id="a3fea-120">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="a3fea-121">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="a3fea-121">The default is `false`.</span></span><br /><br /> <span data-ttu-id="a3fea-122">Když `clientCredentialType` atribut vazby je nastaven na `Windows`, systém nepovoluje anonymní volající.</span><span class="sxs-lookup"><span data-stu-id="a3fea-122">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="a3fea-123">To znamená, že pouze domény nebo pracovní skupině authenticated volající je povolen přístup k systému.</span><span class="sxs-lookup"><span data-stu-id="a3fea-123">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="a3fea-124">Toto chování můžete přepsat pomocí tohoto atributu.</span><span class="sxs-lookup"><span data-stu-id="a3fea-124">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="a3fea-125">Pomocí tohoto nastavení s nejvyšší opatrností.</span><span class="sxs-lookup"><span data-stu-id="a3fea-125">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3fea-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a3fea-126">Child Elements</span></span>  
 <span data-ttu-id="a3fea-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="a3fea-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a3fea-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a3fea-128">Parent Elements</span></span>  
  
|<span data-ttu-id="a3fea-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="a3fea-129">Element</span></span>|<span data-ttu-id="a3fea-130">Popis</span><span class="sxs-lookup"><span data-stu-id="a3fea-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3fea-131">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="a3fea-131">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="a3fea-132">Určuje přihlašovací údaje pro ověřování služby a nastavení vztahující se k ověření přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="a3fea-132">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3fea-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a3fea-133">Remarks</span></span>  
 <span data-ttu-id="a3fea-134">Tento element slouží k určení, jestli se má povolit přístup anonymní uživatelé Windows tak, že nastavíte `allowAnonymousLogons` atribut.</span><span class="sxs-lookup"><span data-stu-id="a3fea-134">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="a3fea-135">Můžete také určit, zda mají být zahrnuty informace o skupinách, ke kterému uživatelé patří AuthorizationContext tak, že nastavíte `includeWindowsGroups` atribut.</span><span class="sxs-lookup"><span data-stu-id="a3fea-135">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="a3fea-136">Pokud je nastavena na `true` (výchozí nastavení), službu můžete určit skupiny Windows, na které klient patří.</span><span class="sxs-lookup"><span data-stu-id="a3fea-136">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3fea-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3fea-137">See also</span></span>
- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
