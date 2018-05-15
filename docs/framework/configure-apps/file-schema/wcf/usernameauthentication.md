---
title: '&lt;UserNameAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: d81bf3441f4999683b9dc9ab956fff517c20e80e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltusernameauthenticationgt"></a><span data-ttu-id="8be27-102">&lt;UserNameAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="8be27-102">&lt;userNameAuthentication&gt;</span></span>
<span data-ttu-id="8be27-103">Určuje pověření služby na základě uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="8be27-103">Specifies a service's credentials based on user name and password.</span></span>  
  
 <span data-ttu-id="8be27-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8be27-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8be27-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="8be27-105">\<behaviors></span></span>  
<span data-ttu-id="8be27-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="8be27-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="8be27-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="8be27-107">\<behavior></span></span>  
<span data-ttu-id="8be27-108">\<– serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="8be27-108">\<serviceCredentials></span></span>  
<span data-ttu-id="8be27-109">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="8be27-109">\<userNameAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8be27-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8be27-110">Syntax</span></span>  
  
```xml  
<userNameAuthentication  
   cacheLogonTokenLifetime="TimeSpan"  
   cacheLogonTokens="Boolean"   
   customUserNamePasswordValidatorType="String"  
   includeWindowsGroups="Boolean"   
   maxCacheLogonTokens="Integer"  
   membershipProviderName="String"  
   userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8be27-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8be27-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8be27-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8be27-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8be27-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="8be27-113">Attributes</span></span>  
  
|<span data-ttu-id="8be27-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="8be27-114">Attribute</span></span>|<span data-ttu-id="8be27-115">Popis</span><span class="sxs-lookup"><span data-stu-id="8be27-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="8be27-116">A <xref:System.TimeSpan> , určuje maximální délku doby token se uloží do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="8be27-116">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="8be27-117">Výchozí hodnota je 00:15:00.</span><span class="sxs-lookup"><span data-stu-id="8be27-117">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="8be27-118">Logická hodnota, která určuje, zda jsou tokeny přihlášení do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="8be27-118">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="8be27-119">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="8be27-119">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="8be27-120">Řetězec, který určuje typ validátor hesel vlastní uživatelské jméno, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="8be27-120">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="8be27-121">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="8be27-121">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="8be27-122">Logická hodnota, která určuje, zda skupiny systému Windows jsou zahrnuty v kontextu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8be27-122">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="8be27-123">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="8be27-123">The default is `true`.</span></span><br /><br /> <span data-ttu-id="8be27-124">Nastavení tohoto atributu na `true` má dopad na výkon, jako je výsledkem rozšíření skupiny úplné.</span><span class="sxs-lookup"><span data-stu-id="8be27-124">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="8be27-125">Tuto vlastnost nastavit na `false` Pokud není potřeba vytvořit seznam skupin uživatel patří do.</span><span class="sxs-lookup"><span data-stu-id="8be27-125">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="8be27-126">Celé číslo, které určuje maximální počet tokeny přihlášení do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="8be27-126">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="8be27-127">Tato hodnota by měla být větší než nula.</span><span class="sxs-lookup"><span data-stu-id="8be27-127">This value should be larger than zero.</span></span> <span data-ttu-id="8be27-128">Výchozí hodnota je 128.</span><span class="sxs-lookup"><span data-stu-id="8be27-128">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="8be27-129">Když `clientCredentialType` atribut vazby je nastaven na `username`, uživatelské jméno je namapována na účty v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="8be27-129">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="8be27-130">Můžete přepsat toto chování pomocí tento atribut, který je řetězec, který obsahuje název <xref:System.Web.Security.MembershipProvider> hodnotu, která poskytuje mechanismus ověřování příslušné heslo.</span><span class="sxs-lookup"><span data-stu-id="8be27-130">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="8be27-131">Určuje způsob, které uživatelské jméno je ověřit heslo.</span><span class="sxs-lookup"><span data-stu-id="8be27-131">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="8be27-132">Platné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="8be27-132">Valid values are:</span></span><br /><br /> <span data-ttu-id="8be27-133">-Windows</span><span class="sxs-lookup"><span data-stu-id="8be27-133">-   Windows</span></span><br /><span data-ttu-id="8be27-134">-MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="8be27-134">-   MembershipProvider</span></span><br /><span data-ttu-id="8be27-135">-Vlastní</span><span class="sxs-lookup"><span data-stu-id="8be27-135">-   Custom</span></span><br /><br /> <span data-ttu-id="8be27-136">Výchozí hodnota je Windows.</span><span class="sxs-lookup"><span data-stu-id="8be27-136">The default is Windows.</span></span> <span data-ttu-id="8be27-137">Tento atribut je typu <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="8be27-137">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8be27-138">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8be27-138">Child Elements</span></span>  
 <span data-ttu-id="8be27-139">Žádné</span><span class="sxs-lookup"><span data-stu-id="8be27-139">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8be27-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8be27-140">Parent Elements</span></span>  
  
|<span data-ttu-id="8be27-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="8be27-141">Element</span></span>|<span data-ttu-id="8be27-142">Popis</span><span class="sxs-lookup"><span data-stu-id="8be27-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8be27-143">\<– serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="8be27-143">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="8be27-144">Určí pověření, které mají být použity v ověřování služby, a ověření přihlašovacích údajů klienta související nastavení.</span><span class="sxs-lookup"><span data-stu-id="8be27-144">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8be27-145">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8be27-145">Remarks</span></span>  
 <span data-ttu-id="8be27-146">Pokud žádná vazby používá služba je nakonfigurována pro ověřování založené na jméno/heslo uživatele, se ignorují atributy pro tento element.</span><span class="sxs-lookup"><span data-stu-id="8be27-146">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="8be27-147">Mezi ně patří `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, a `userNamePasswordValidationMode`.</span><span class="sxs-lookup"><span data-stu-id="8be27-147">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="8be27-148">Pokud žádná z vazby používané služby je nakonfigurovaný na použití ověřování systému Windows pro uživatelské jméno a heslo, nastavení související s ukládání do mezipaměti tokenů přihlášení se ignorují.</span><span class="sxs-lookup"><span data-stu-id="8be27-148">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="8be27-149">Patří mezi ně `cacheLogonTokenLifetime`, `cacheLogonTokens`, a `maxCacheLogonTokens`.</span><span class="sxs-lookup"><span data-stu-id="8be27-149">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8be27-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="8be27-150">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UserNameServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
