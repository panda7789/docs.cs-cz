---
title: <windowsAuthentication> z <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: ded04f6e87fce2e12dac8f681ba2d4178f8fd204
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399116"
---
# <a name="windowsauthentication-of-servicecredentials"></a><span data-ttu-id="3cf8b-102">\<windowsAuthentication> z \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="3cf8b-102">\<windowsAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="3cf8b-103">Určuje nastavení pověření služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="3cf8b-103">Specifies the settings of a Windows service credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="3cf8b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3cf8b-104">Syntax</span></span>  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3cf8b-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3cf8b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3cf8b-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3cf8b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3cf8b-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="3cf8b-107">Attributes</span></span>  
  
|<span data-ttu-id="3cf8b-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="3cf8b-108">Attribute</span></span>|<span data-ttu-id="3cf8b-109">Popis</span><span class="sxs-lookup"><span data-stu-id="3cf8b-109">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="3cf8b-110">Volitelný logický atribut, který určuje, zda systém zahrnuje skupiny systému Windows v kontextu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3cf8b-110">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="3cf8b-111">Výchozí formát je `true`.</span><span class="sxs-lookup"><span data-stu-id="3cf8b-111">The default is `true`.</span></span><br /><br /> <span data-ttu-id="3cf8b-112">Nastavení tohoto atributu na `true` má vliv na výkon, protože má za následek rozšíření úplného seskupení.</span><span class="sxs-lookup"><span data-stu-id="3cf8b-112">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="3cf8b-113">Nastavte tento atribut na, `false` Pokud nepotřebujete vytvořit seznam skupin, do kterých uživatel patří.</span><span class="sxs-lookup"><span data-stu-id="3cf8b-113">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="3cf8b-114">Volitelný logický atribut, který určuje, zda jsou povoleny anonymní neověřené volající.</span><span class="sxs-lookup"><span data-stu-id="3cf8b-114">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="3cf8b-115">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="3cf8b-115">The default is `false`.</span></span><br /><br /> <span data-ttu-id="3cf8b-116">Pokud `clientCredentialType` je atribut vazby nastaven na `Windows` , systém nepovoluje anonymní volající.</span><span class="sxs-lookup"><span data-stu-id="3cf8b-116">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="3cf8b-117">To znamená, že přístup k systému má povolen pouze ověřený volající domény nebo pracovní skupiny.</span><span class="sxs-lookup"><span data-stu-id="3cf8b-117">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="3cf8b-118">Toto chování můžete přepsat pomocí tohoto atributu.</span><span class="sxs-lookup"><span data-stu-id="3cf8b-118">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="3cf8b-119">Toto nastavení se používá s mimořádnou opatrností.</span><span class="sxs-lookup"><span data-stu-id="3cf8b-119">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3cf8b-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3cf8b-120">Child Elements</span></span>  
 <span data-ttu-id="3cf8b-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="3cf8b-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3cf8b-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3cf8b-122">Parent Elements</span></span>  
  
|<span data-ttu-id="3cf8b-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="3cf8b-123">Element</span></span>|<span data-ttu-id="3cf8b-124">Description</span><span class="sxs-lookup"><span data-stu-id="3cf8b-124">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="3cf8b-125">Určuje přihlašovací údaje, které se mají použít při ověřování služby, a nastavení související s ověřením přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="3cf8b-125">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3cf8b-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3cf8b-126">Remarks</span></span>  
 <span data-ttu-id="3cf8b-127">Tento prvek použijte k určení, zda má být povolen anonymní přístup uživatelů systému Windows nastavením `allowAnonymousLogons` atributu.</span><span class="sxs-lookup"><span data-stu-id="3cf8b-127">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="3cf8b-128">Nastavením atributu můžete také určit, jestli se mají zahrnout informace o skupině, ke kterým uživatelé patří, do AuthorizationContext `includeWindowsGroups` .</span><span class="sxs-lookup"><span data-stu-id="3cf8b-128">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="3cf8b-129">Pokud je nastavená na `true` (výchozí nastavení), může služba určit skupiny systému Windows, ke kterým klient patří.</span><span class="sxs-lookup"><span data-stu-id="3cf8b-129">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cf8b-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="3cf8b-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
