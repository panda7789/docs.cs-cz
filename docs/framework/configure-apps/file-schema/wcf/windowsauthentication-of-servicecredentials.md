---
title: <windowsAuthentication> z <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: ded04f6e87fce2e12dac8f681ba2d4178f8fd204
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399116"
---
# <a name="windowsauthentication-of-servicecredentials"></a><span data-ttu-id="16885-102">\<windowsAuthentication > \<ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="16885-102">\<windowsAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="16885-103">Určuje nastavení pověření služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="16885-103">Specifies the settings of a Windows service credential.</span></span>  
  
<span data-ttu-id="16885-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="16885-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="16885-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="16885-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="16885-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="16885-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="16885-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="16885-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="16885-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="16885-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="16885-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="16885-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="16885-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<windowsAuthentication >**</span><span class="sxs-lookup"><span data-stu-id="16885-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16885-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16885-111">Syntax</span></span>  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16885-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="16885-112">Attributes and Elements</span></span>  
 <span data-ttu-id="16885-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="16885-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16885-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="16885-114">Attributes</span></span>  
  
|<span data-ttu-id="16885-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="16885-115">Attribute</span></span>|<span data-ttu-id="16885-116">Popis</span><span class="sxs-lookup"><span data-stu-id="16885-116">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="16885-117">Volitelný logický atribut, který určuje, zda systém zahrnuje skupiny systému Windows v kontextu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="16885-117">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="16885-118">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="16885-118">The default is `true`.</span></span><br /><br /> <span data-ttu-id="16885-119">Nastavení tohoto atributu na `true` má vliv na výkon, protože má za následek rozšíření úplného seskupení.</span><span class="sxs-lookup"><span data-stu-id="16885-119">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="16885-120">Nastavte tento atribut na `false` , pokud nepotřebujete vytvořit seznam skupin, do kterých uživatel patří.</span><span class="sxs-lookup"><span data-stu-id="16885-120">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="16885-121">Volitelný logický atribut, který určuje, zda jsou povoleny anonymní neověřené volající.</span><span class="sxs-lookup"><span data-stu-id="16885-121">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="16885-122">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="16885-122">The default is `false`.</span></span><br /><br /> <span data-ttu-id="16885-123">`Windows`Pokud je `clientCredentialType` atribut vazby nastaven na, systém nepovoluje anonymní volající.</span><span class="sxs-lookup"><span data-stu-id="16885-123">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="16885-124">To znamená, že přístup k systému má povolen pouze ověřený volající domény nebo pracovní skupiny.</span><span class="sxs-lookup"><span data-stu-id="16885-124">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="16885-125">Toto chování můžete přepsat pomocí tohoto atributu.</span><span class="sxs-lookup"><span data-stu-id="16885-125">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="16885-126">Toto nastavení se používá s mimořádnou opatrností.</span><span class="sxs-lookup"><span data-stu-id="16885-126">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16885-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="16885-127">Child Elements</span></span>  
 <span data-ttu-id="16885-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="16885-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="16885-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="16885-129">Parent Elements</span></span>  
  
|<span data-ttu-id="16885-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="16885-130">Element</span></span>|<span data-ttu-id="16885-131">Popis</span><span class="sxs-lookup"><span data-stu-id="16885-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="16885-132">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="16885-132">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="16885-133">Určuje přihlašovací údaje, které se mají použít při ověřování služby, a nastavení související s ověřením přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="16885-133">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16885-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="16885-134">Remarks</span></span>  
 <span data-ttu-id="16885-135">Tento prvek použijte k určení, zda má být povolen anonymní přístup uživatelů systému Windows `allowAnonymousLogons` nastavením atributu.</span><span class="sxs-lookup"><span data-stu-id="16885-135">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="16885-136">Nastavením `includeWindowsGroups` atributu můžete také určit, jestli se mají zahrnout informace o skupině, ke kterým uživatelé patří, do AuthorizationContext.</span><span class="sxs-lookup"><span data-stu-id="16885-136">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="16885-137">Pokud je nastavená na `true` (výchozí nastavení), může služba určit skupiny systému Windows, ke kterým klient patří.</span><span class="sxs-lookup"><span data-stu-id="16885-137">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16885-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16885-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
