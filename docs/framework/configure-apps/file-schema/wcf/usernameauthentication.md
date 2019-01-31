---
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: 05aa326c50823810caee5d6552af4d50424251dd
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274004"
---
# <a name="usernameauthentication"></a><span data-ttu-id="79920-101">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="79920-101">\<userNameAuthentication></span></span>
<span data-ttu-id="79920-102">Určuje pověření služby na základě uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="79920-102">Specifies a service's credentials based on user name and password.</span></span>  
  
 <span data-ttu-id="79920-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="79920-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="79920-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="79920-104">\<behaviors></span></span>  
<span data-ttu-id="79920-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="79920-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="79920-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="79920-106">\<behavior></span></span>  
<span data-ttu-id="79920-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="79920-107">\<serviceCredentials></span></span>  
<span data-ttu-id="79920-108">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="79920-108">\<userNameAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79920-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79920-109">Syntax</span></span>  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79920-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="79920-110">Attributes and Elements</span></span>  
 <span data-ttu-id="79920-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="79920-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79920-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="79920-112">Attributes</span></span>  
  
|<span data-ttu-id="79920-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="79920-113">Attribute</span></span>|<span data-ttu-id="79920-114">Popis</span><span class="sxs-lookup"><span data-stu-id="79920-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="79920-115">A <xref:System.TimeSpan> , která určuje maximální délku doby token se uloží do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="79920-115">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="79920-116">Výchozí hodnota je 00:15:00.</span><span class="sxs-lookup"><span data-stu-id="79920-116">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="79920-117">Logická hodnota určující, zda jsou uložené v mezipaměti tokeny přihlášení.</span><span class="sxs-lookup"><span data-stu-id="79920-117">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="79920-118">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="79920-118">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="79920-119">Řetězec, který určuje typ validátoru vlastního uživatelského jména hesla pro použití.</span><span class="sxs-lookup"><span data-stu-id="79920-119">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="79920-120">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="79920-120">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="79920-121">Logická hodnota určující, zda jsou skupiny Windows zahrnuty v kontextu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="79920-121">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="79920-122">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="79920-122">The default is `true`.</span></span><br /><br /> <span data-ttu-id="79920-123">Nastavení tohoto atributu na `true` má dopad na výkon, protože výsledkem rozšíření skupiny úplné.</span><span class="sxs-lookup"><span data-stu-id="79920-123">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="79920-124">Tuto vlastnost nastavte na `false` Pokud není potřeba vytvořit seznam skupin uživatel patří.</span><span class="sxs-lookup"><span data-stu-id="79920-124">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="79920-125">Celé číslo určující maximální počet tokeny přihlášení do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="79920-125">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="79920-126">Tato hodnota by měla být větší než nula.</span><span class="sxs-lookup"><span data-stu-id="79920-126">This value should be larger than zero.</span></span> <span data-ttu-id="79920-127">Výchozí hodnota je 128.</span><span class="sxs-lookup"><span data-stu-id="79920-127">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="79920-128">Když `clientCredentialType` atribut vazby je nastaven na `username`, uživatelské jméno je mapováno na účty Windows.</span><span class="sxs-lookup"><span data-stu-id="79920-128">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="79920-129">Můžete přepsat toto chování pomocí tohoto atributu, což je řetězec, který obsahuje název <xref:System.Web.Security.MembershipProvider> hodnotu, která poskytuje mechanismus ověřování příslušné heslo.</span><span class="sxs-lookup"><span data-stu-id="79920-129">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="79920-130">Určuje způsob, v jaké uživatelské jméno je ověřit heslo.</span><span class="sxs-lookup"><span data-stu-id="79920-130">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="79920-131">Platné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="79920-131">Valid values are:</span></span><br /><br /> <span data-ttu-id="79920-132">– Windows</span><span class="sxs-lookup"><span data-stu-id="79920-132">-   Windows</span></span><br /><span data-ttu-id="79920-133">-MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="79920-133">-   MembershipProvider</span></span><br /><span data-ttu-id="79920-134">– Vlastní</span><span class="sxs-lookup"><span data-stu-id="79920-134">-   Custom</span></span><br /><br /> <span data-ttu-id="79920-135">Výchozí hodnota je Windows.</span><span class="sxs-lookup"><span data-stu-id="79920-135">The default is Windows.</span></span> <span data-ttu-id="79920-136">Tento atribut je typu <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="79920-136">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="79920-137">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="79920-137">Child Elements</span></span>  
 <span data-ttu-id="79920-138">Žádné</span><span class="sxs-lookup"><span data-stu-id="79920-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="79920-139">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="79920-139">Parent Elements</span></span>  
  
|<span data-ttu-id="79920-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="79920-140">Element</span></span>|<span data-ttu-id="79920-141">Popis</span><span class="sxs-lookup"><span data-stu-id="79920-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79920-142">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="79920-142">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="79920-143">Určuje přihlašovací údaje, který se má použít při ověřování služby, a nastavení příslušného ověřování přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="79920-143">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79920-144">Poznámky</span><span class="sxs-lookup"><span data-stu-id="79920-144">Remarks</span></span>  
 <span data-ttu-id="79920-145">Pokud žádná z vazby používané službou je nakonfigurován pro ověřování založené na jméno/heslo uživatele, atributy u tohoto elementu se ignorují.</span><span class="sxs-lookup"><span data-stu-id="79920-145">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="79920-146">Patří mezi ně `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, a `userNamePasswordValidationMode`.</span><span class="sxs-lookup"><span data-stu-id="79920-146">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="79920-147">Pokud žádná z vazby používané službou je nakonfigurován pro použití ověřování Windows pro uživatelské jméno/heslo, jsou ignorovány nastavení týkající se ukládání do mezipaměti tokeny přihlášení.</span><span class="sxs-lookup"><span data-stu-id="79920-147">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="79920-148">Patří mezi ně `cacheLogonTokenLifetime`, `cacheLogonTokens`, a `maxCacheLogonTokens`.</span><span class="sxs-lookup"><span data-stu-id="79920-148">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79920-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79920-149">See also</span></span>
- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
