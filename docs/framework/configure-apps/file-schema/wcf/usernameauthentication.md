---
title: '&lt;userNameAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: 1b8a85a3b2699aa88db24d1f7afee3de67dbf39b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656637"
---
# <a name="ltusernameauthenticationgt"></a><span data-ttu-id="a9de8-102">&lt;userNameAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="a9de8-102">&lt;userNameAuthentication&gt;</span></span>
<span data-ttu-id="a9de8-103">Určuje pověření služby na základě uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="a9de8-103">Specifies a service's credentials based on user name and password.</span></span>  
  
 <span data-ttu-id="a9de8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a9de8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a9de8-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="a9de8-105">\<behaviors></span></span>  
<span data-ttu-id="a9de8-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="a9de8-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="a9de8-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="a9de8-107">\<behavior></span></span>  
<span data-ttu-id="a9de8-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="a9de8-108">\<serviceCredentials></span></span>  
<span data-ttu-id="a9de8-109">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="a9de8-109">\<userNameAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9de8-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9de8-110">Syntax</span></span>  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a9de8-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a9de8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a9de8-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a9de8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a9de8-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="a9de8-113">Attributes</span></span>  
  
|<span data-ttu-id="a9de8-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="a9de8-114">Attribute</span></span>|<span data-ttu-id="a9de8-115">Popis</span><span class="sxs-lookup"><span data-stu-id="a9de8-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="a9de8-116">A <xref:System.TimeSpan> , která určuje maximální délku doby token se uloží do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="a9de8-116">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="a9de8-117">Výchozí hodnota je 00:15:00.</span><span class="sxs-lookup"><span data-stu-id="a9de8-117">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="a9de8-118">Logická hodnota určující, zda jsou uložené v mezipaměti tokeny přihlášení.</span><span class="sxs-lookup"><span data-stu-id="a9de8-118">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="a9de8-119">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="a9de8-119">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="a9de8-120">Řetězec, který určuje typ validátoru vlastního uživatelského jména hesla pro použití.</span><span class="sxs-lookup"><span data-stu-id="a9de8-120">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="a9de8-121">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="a9de8-121">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="a9de8-122">Logická hodnota určující, zda jsou skupiny Windows zahrnuty v kontextu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="a9de8-122">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="a9de8-123">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="a9de8-123">The default is `true`.</span></span><br /><br /> <span data-ttu-id="a9de8-124">Nastavení tohoto atributu na `true` má dopad na výkon, protože výsledkem rozšíření skupiny úplné.</span><span class="sxs-lookup"><span data-stu-id="a9de8-124">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="a9de8-125">Tuto vlastnost nastavte na `false` Pokud není potřeba vytvořit seznam skupin uživatel patří.</span><span class="sxs-lookup"><span data-stu-id="a9de8-125">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="a9de8-126">Celé číslo určující maximální počet tokeny přihlášení do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="a9de8-126">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="a9de8-127">Tato hodnota by měla být větší než nula.</span><span class="sxs-lookup"><span data-stu-id="a9de8-127">This value should be larger than zero.</span></span> <span data-ttu-id="a9de8-128">Výchozí hodnota je 128.</span><span class="sxs-lookup"><span data-stu-id="a9de8-128">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="a9de8-129">Když `clientCredentialType` atribut vazby je nastaven na `username`, uživatelské jméno je mapováno na účty Windows.</span><span class="sxs-lookup"><span data-stu-id="a9de8-129">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="a9de8-130">Můžete přepsat toto chování pomocí tohoto atributu, což je řetězec, který obsahuje název <xref:System.Web.Security.MembershipProvider> hodnotu, která poskytuje mechanismus ověřování příslušné heslo.</span><span class="sxs-lookup"><span data-stu-id="a9de8-130">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="a9de8-131">Určuje způsob, v jaké uživatelské jméno je ověřit heslo.</span><span class="sxs-lookup"><span data-stu-id="a9de8-131">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="a9de8-132">Platné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="a9de8-132">Valid values are:</span></span><br /><br /> <span data-ttu-id="a9de8-133">– Windows</span><span class="sxs-lookup"><span data-stu-id="a9de8-133">-   Windows</span></span><br /><span data-ttu-id="a9de8-134">-MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="a9de8-134">-   MembershipProvider</span></span><br /><span data-ttu-id="a9de8-135">– Vlastní</span><span class="sxs-lookup"><span data-stu-id="a9de8-135">-   Custom</span></span><br /><br /> <span data-ttu-id="a9de8-136">Výchozí hodnota je Windows.</span><span class="sxs-lookup"><span data-stu-id="a9de8-136">The default is Windows.</span></span> <span data-ttu-id="a9de8-137">Tento atribut je typu <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="a9de8-137">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a9de8-138">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a9de8-138">Child Elements</span></span>  
 <span data-ttu-id="a9de8-139">Žádné</span><span class="sxs-lookup"><span data-stu-id="a9de8-139">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a9de8-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a9de8-140">Parent Elements</span></span>  
  
|<span data-ttu-id="a9de8-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="a9de8-141">Element</span></span>|<span data-ttu-id="a9de8-142">Popis</span><span class="sxs-lookup"><span data-stu-id="a9de8-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a9de8-143">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="a9de8-143">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="a9de8-144">Určuje přihlašovací údaje, který se má použít při ověřování služby, a nastavení příslušného ověřování přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="a9de8-144">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9de8-145">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a9de8-145">Remarks</span></span>  
 <span data-ttu-id="a9de8-146">Pokud žádná z vazby používané službou je nakonfigurován pro ověřování založené na jméno/heslo uživatele, atributy u tohoto elementu se ignorují.</span><span class="sxs-lookup"><span data-stu-id="a9de8-146">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="a9de8-147">Patří mezi ně `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, a `userNamePasswordValidationMode`.</span><span class="sxs-lookup"><span data-stu-id="a9de8-147">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="a9de8-148">Pokud žádná z vazby používané službou je nakonfigurován pro použití ověřování Windows pro uživatelské jméno/heslo, jsou ignorovány nastavení týkající se ukládání do mezipaměti tokeny přihlášení.</span><span class="sxs-lookup"><span data-stu-id="a9de8-148">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="a9de8-149">Patří mezi ně `cacheLogonTokenLifetime`, `cacheLogonTokens`, a `maxCacheLogonTokens`.</span><span class="sxs-lookup"><span data-stu-id="a9de8-149">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9de8-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9de8-150">See also</span></span>
- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
