---
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: dc5c00a2204646863ae2570bb97b8d70e22a72d4
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399191"
---
# <a name="usernameauthentication"></a><span data-ttu-id="03b1e-101">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="03b1e-101">\<userNameAuthentication></span></span>
<span data-ttu-id="03b1e-102">Určuje přihlašovací údaje služby na základě uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="03b1e-102">Specifies a service's credentials based on user name and password.</span></span>  
  
<span data-ttu-id="03b1e-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="03b1e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="03b1e-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="03b1e-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="03b1e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="03b1e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="03b1e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="03b1e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="03b1e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="03b1e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="03b1e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="03b1e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="03b1e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<userNameAuthentication >**</span><span class="sxs-lookup"><span data-stu-id="03b1e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03b1e-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03b1e-110">Syntax</span></span>  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03b1e-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="03b1e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="03b1e-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="03b1e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03b1e-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="03b1e-113">Attributes</span></span>  
  
|<span data-ttu-id="03b1e-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="03b1e-114">Attribute</span></span>|<span data-ttu-id="03b1e-115">Popis</span><span class="sxs-lookup"><span data-stu-id="03b1e-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="03b1e-116">A <xref:System.TimeSpan> určuje maximální dobu, po kterou je token uložen v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="03b1e-116">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="03b1e-117">Výchozí hodnota je 00:15:00.</span><span class="sxs-lookup"><span data-stu-id="03b1e-117">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="03b1e-118">Logická hodnota, která určuje, zda jsou přihlašovací tokeny ukládány do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="03b1e-118">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="03b1e-119">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="03b1e-119">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="03b1e-120">Řetězec, který určuje typ vlastního validátoru hesla uživatele, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="03b1e-120">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="03b1e-121">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="03b1e-121">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="03b1e-122">Logická hodnota určující, zda jsou skupiny systému Windows zahrnuty v kontextu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="03b1e-122">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="03b1e-123">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="03b1e-123">The default is `true`.</span></span><br /><br /> <span data-ttu-id="03b1e-124">Nastavení tohoto atributu na `true` má vliv na výkon, protože má za následek rozšíření úplného seskupení.</span><span class="sxs-lookup"><span data-stu-id="03b1e-124">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="03b1e-125">Tuto vlastnost nastavte na `false` , pokud nepotřebujete vytvořit seznam skupin, do kterých uživatel patří.</span><span class="sxs-lookup"><span data-stu-id="03b1e-125">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="03b1e-126">Celé číslo, které určuje maximální počet přihlašovacích tokenů pro ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="03b1e-126">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="03b1e-127">Tato hodnota by měla být větší než nula.</span><span class="sxs-lookup"><span data-stu-id="03b1e-127">This value should be larger than zero.</span></span> <span data-ttu-id="03b1e-128">Výchozí hodnota je 128.</span><span class="sxs-lookup"><span data-stu-id="03b1e-128">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="03b1e-129">`username`Pokud je `clientCredentialType` atribut vazby nastaven na hodnotu, uživatelské jméno je namapováno na účty systému Windows.</span><span class="sxs-lookup"><span data-stu-id="03b1e-129">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="03b1e-130">Toto chování můžete přepsat pomocí tohoto atributu, což je řetězec, který obsahuje název <xref:System.Web.Security.MembershipProvider> hodnoty, která poskytuje příslušný mechanismus ověřování hesla.</span><span class="sxs-lookup"><span data-stu-id="03b1e-130">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="03b1e-131">Určuje způsob, jakým se ověřuje heslo k uživatelskému jménu.</span><span class="sxs-lookup"><span data-stu-id="03b1e-131">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="03b1e-132">Platné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="03b1e-132">Valid values are:</span></span><br /><br /> <span data-ttu-id="03b1e-133">– Windows</span><span class="sxs-lookup"><span data-stu-id="03b1e-133">-   Windows</span></span><br /><span data-ttu-id="03b1e-134">– MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="03b1e-134">-   MembershipProvider</span></span><br /><span data-ttu-id="03b1e-135">– Vlastní</span><span class="sxs-lookup"><span data-stu-id="03b1e-135">-   Custom</span></span><br /><br /> <span data-ttu-id="03b1e-136">Výchozí hodnota je Windows.</span><span class="sxs-lookup"><span data-stu-id="03b1e-136">The default is Windows.</span></span> <span data-ttu-id="03b1e-137">Tento atribut je typu <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="03b1e-137">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="03b1e-138">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="03b1e-138">Child Elements</span></span>  
 <span data-ttu-id="03b1e-139">Žádné</span><span class="sxs-lookup"><span data-stu-id="03b1e-139">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="03b1e-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="03b1e-140">Parent Elements</span></span>  
  
|<span data-ttu-id="03b1e-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="03b1e-141">Element</span></span>|<span data-ttu-id="03b1e-142">Popis</span><span class="sxs-lookup"><span data-stu-id="03b1e-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03b1e-143">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="03b1e-143">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="03b1e-144">Určuje přihlašovací údaje, které se mají použít při ověřování služby, a nastavení související s ověřováním přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="03b1e-144">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03b1e-145">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03b1e-145">Remarks</span></span>  
 <span data-ttu-id="03b1e-146">Pokud žádná z vazeb používaných službou není nakonfigurovaná pro ověřování pomocí uživatelského jména a hesla, atributy pro tento element se ignorují.</span><span class="sxs-lookup"><span data-stu-id="03b1e-146">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="03b1e-147">Mezi ně `customUserNamePasswordValidatorType`patří `includeWindowsGroups` ,`membershipProviderName`, a `userNamePasswordValidationMode`.</span><span class="sxs-lookup"><span data-stu-id="03b1e-147">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="03b1e-148">Pokud není žádná z vazeb používaných službou nakonfigurovaná tak, aby pro uživatelské jméno a heslo používala ověřování systému Windows, ignorují se nastavení související s ukládáním přihlašovacích tokenů do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="03b1e-148">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="03b1e-149">Mezi ně patří `cacheLogonTokenLifetime`, `cacheLogonTokens`a `maxCacheLogonTokens`.</span><span class="sxs-lookup"><span data-stu-id="03b1e-149">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03b1e-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03b1e-150">See also</span></span>

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
