---
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: 399158632d5c17a35ded02691ba35a231e6cdc6e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940535"
---
# <a name="usernameauthentication"></a><span data-ttu-id="fd587-101">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="fd587-101">\<userNameAuthentication></span></span>
<span data-ttu-id="fd587-102">Určuje přihlašovací údaje služby na základě uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="fd587-102">Specifies a service's credentials based on user name and password.</span></span>  
  
 <span data-ttu-id="fd587-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fd587-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="fd587-104">\<> chování</span><span class="sxs-lookup"><span data-stu-id="fd587-104">\<behaviors></span></span>  
<span data-ttu-id="fd587-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="fd587-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="fd587-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="fd587-106">\<behavior></span></span>  
<span data-ttu-id="fd587-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="fd587-107">\<serviceCredentials></span></span>  
<span data-ttu-id="fd587-108">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="fd587-108">\<userNameAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd587-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd587-109">Syntax</span></span>  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd587-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fd587-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fd587-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fd587-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd587-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="fd587-112">Attributes</span></span>  
  
|<span data-ttu-id="fd587-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="fd587-113">Attribute</span></span>|<span data-ttu-id="fd587-114">Popis</span><span class="sxs-lookup"><span data-stu-id="fd587-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="fd587-115">A <xref:System.TimeSpan> určuje maximální dobu, po kterou je token uložen v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="fd587-115">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="fd587-116">Výchozí hodnota je 00:15:00.</span><span class="sxs-lookup"><span data-stu-id="fd587-116">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="fd587-117">Logická hodnota, která určuje, zda jsou přihlašovací tokeny ukládány do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="fd587-117">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="fd587-118">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="fd587-118">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="fd587-119">Řetězec, který určuje typ vlastního validátoru hesla uživatele, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="fd587-119">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="fd587-120">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="fd587-120">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="fd587-121">Logická hodnota určující, zda jsou skupiny systému Windows zahrnuty v kontextu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="fd587-121">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="fd587-122">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="fd587-122">The default is `true`.</span></span><br /><br /> <span data-ttu-id="fd587-123">Nastavení tohoto atributu na `true` má vliv na výkon, protože má za následek rozšíření úplného seskupení.</span><span class="sxs-lookup"><span data-stu-id="fd587-123">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="fd587-124">Tuto vlastnost nastavte na `false` , pokud nepotřebujete vytvořit seznam skupin, do kterých uživatel patří.</span><span class="sxs-lookup"><span data-stu-id="fd587-124">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="fd587-125">Celé číslo, které určuje maximální počet přihlašovacích tokenů pro ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="fd587-125">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="fd587-126">Tato hodnota by měla být větší než nula.</span><span class="sxs-lookup"><span data-stu-id="fd587-126">This value should be larger than zero.</span></span> <span data-ttu-id="fd587-127">Výchozí hodnota je 128.</span><span class="sxs-lookup"><span data-stu-id="fd587-127">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="fd587-128">`username`Pokud je `clientCredentialType` atribut vazby nastaven na hodnotu, uživatelské jméno je namapováno na účty systému Windows.</span><span class="sxs-lookup"><span data-stu-id="fd587-128">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="fd587-129">Toto chování můžete přepsat pomocí tohoto atributu, což je řetězec, který obsahuje název <xref:System.Web.Security.MembershipProvider> hodnoty, která poskytuje příslušný mechanismus ověřování hesla.</span><span class="sxs-lookup"><span data-stu-id="fd587-129">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="fd587-130">Určuje způsob, jakým se ověřuje heslo k uživatelskému jménu.</span><span class="sxs-lookup"><span data-stu-id="fd587-130">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="fd587-131">Platné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="fd587-131">Valid values are:</span></span><br /><br /> <span data-ttu-id="fd587-132">– Windows</span><span class="sxs-lookup"><span data-stu-id="fd587-132">-   Windows</span></span><br /><span data-ttu-id="fd587-133">– MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="fd587-133">-   MembershipProvider</span></span><br /><span data-ttu-id="fd587-134">– Vlastní</span><span class="sxs-lookup"><span data-stu-id="fd587-134">-   Custom</span></span><br /><br /> <span data-ttu-id="fd587-135">Výchozí hodnota je Windows.</span><span class="sxs-lookup"><span data-stu-id="fd587-135">The default is Windows.</span></span> <span data-ttu-id="fd587-136">Tento atribut je typu <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="fd587-136">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd587-137">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fd587-137">Child Elements</span></span>  
 <span data-ttu-id="fd587-138">Žádné</span><span class="sxs-lookup"><span data-stu-id="fd587-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd587-139">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fd587-139">Parent Elements</span></span>  
  
|<span data-ttu-id="fd587-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="fd587-140">Element</span></span>|<span data-ttu-id="fd587-141">Popis</span><span class="sxs-lookup"><span data-stu-id="fd587-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd587-142">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="fd587-142">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="fd587-143">Určuje přihlašovací údaje, které se mají použít při ověřování služby, a nastavení související s ověřováním přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="fd587-143">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd587-144">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fd587-144">Remarks</span></span>  
 <span data-ttu-id="fd587-145">Pokud žádná z vazeb používaných službou není nakonfigurovaná pro ověřování pomocí uživatelského jména a hesla, atributy pro tento element se ignorují.</span><span class="sxs-lookup"><span data-stu-id="fd587-145">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="fd587-146">Mezi ně `customUserNamePasswordValidatorType`patří `includeWindowsGroups` ,`membershipProviderName`, a `userNamePasswordValidationMode`.</span><span class="sxs-lookup"><span data-stu-id="fd587-146">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="fd587-147">Pokud není žádná z vazeb používaných službou nakonfigurovaná tak, aby pro uživatelské jméno a heslo používala ověřování systému Windows, ignorují se nastavení související s ukládáním přihlašovacích tokenů do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="fd587-147">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="fd587-148">Mezi ně patří `cacheLogonTokenLifetime`, `cacheLogonTokens`a `maxCacheLogonTokens`.</span><span class="sxs-lookup"><span data-stu-id="fd587-148">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd587-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd587-149">See also</span></span>

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
