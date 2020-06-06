---
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: dc5c00a2204646863ae2570bb97b8d70e22a72d4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399191"
---
# \<userNameAuthentication>
<span data-ttu-id="b8343-101">Určuje přihlašovací údaje služby na základě uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="b8343-101">Specifies a service's credentials based on user name and password.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="b8343-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8343-102">Syntax</span></span>  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8343-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b8343-103">Attributes and Elements</span></span>  
 <span data-ttu-id="b8343-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b8343-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8343-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="b8343-105">Attributes</span></span>  
  
|<span data-ttu-id="b8343-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="b8343-106">Attribute</span></span>|<span data-ttu-id="b8343-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b8343-107">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="b8343-108">A <xref:System.TimeSpan> Určuje maximální dobu, po kterou je token uložen v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="b8343-108">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="b8343-109">Výchozí hodnota je 00:15:00.</span><span class="sxs-lookup"><span data-stu-id="b8343-109">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="b8343-110">Logická hodnota, která určuje, zda jsou přihlašovací tokeny ukládány do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="b8343-110">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="b8343-111">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="b8343-111">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="b8343-112">Řetězec, který určuje typ vlastního validátoru hesla uživatele, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="b8343-112">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="b8343-113">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="b8343-113">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="b8343-114">Logická hodnota určující, zda jsou skupiny systému Windows zahrnuty v kontextu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b8343-114">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="b8343-115">Výchozí formát je `true`.</span><span class="sxs-lookup"><span data-stu-id="b8343-115">The default is `true`.</span></span><br /><br /> <span data-ttu-id="b8343-116">Nastavení tohoto atributu na `true` má vliv na výkon, protože má za následek rozšíření úplného seskupení.</span><span class="sxs-lookup"><span data-stu-id="b8343-116">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="b8343-117">Tuto vlastnost nastavte na, `false` Pokud nepotřebujete vytvořit seznam skupin, do kterých uživatel patří.</span><span class="sxs-lookup"><span data-stu-id="b8343-117">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="b8343-118">Celé číslo, které určuje maximální počet přihlašovacích tokenů pro ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="b8343-118">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="b8343-119">Tato hodnota by měla být větší než nula.</span><span class="sxs-lookup"><span data-stu-id="b8343-119">This value should be larger than zero.</span></span> <span data-ttu-id="b8343-120">Výchozí hodnota je 128.</span><span class="sxs-lookup"><span data-stu-id="b8343-120">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="b8343-121">Pokud `clientCredentialType` je atribut vazby nastaven na hodnotu `username` , uživatelské jméno je namapováno na účty systému Windows.</span><span class="sxs-lookup"><span data-stu-id="b8343-121">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="b8343-122">Toto chování můžete přepsat pomocí tohoto atributu, což je řetězec, který obsahuje název <xref:System.Web.Security.MembershipProvider> hodnoty, která poskytuje příslušný mechanismus ověřování hesla.</span><span class="sxs-lookup"><span data-stu-id="b8343-122">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="b8343-123">Určuje způsob, jakým se ověřuje heslo k uživatelskému jménu.</span><span class="sxs-lookup"><span data-stu-id="b8343-123">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="b8343-124">Platné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="b8343-124">Valid values are:</span></span><br /><br /> <span data-ttu-id="b8343-125">– Windows</span><span class="sxs-lookup"><span data-stu-id="b8343-125">-   Windows</span></span><br /><span data-ttu-id="b8343-126">– MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="b8343-126">-   MembershipProvider</span></span><br /><span data-ttu-id="b8343-127">– Vlastní</span><span class="sxs-lookup"><span data-stu-id="b8343-127">-   Custom</span></span><br /><br /> <span data-ttu-id="b8343-128">Výchozí hodnota je Windows.</span><span class="sxs-lookup"><span data-stu-id="b8343-128">The default is Windows.</span></span> <span data-ttu-id="b8343-129">Tento atribut je typu <xref:System.ServiceModel.Security.UserNamePasswordValidationMode> .</span><span class="sxs-lookup"><span data-stu-id="b8343-129">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8343-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b8343-130">Child Elements</span></span>  
 <span data-ttu-id="b8343-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="b8343-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b8343-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b8343-132">Parent Elements</span></span>  
  
|<span data-ttu-id="b8343-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="b8343-133">Element</span></span>|<span data-ttu-id="b8343-134">Description</span><span class="sxs-lookup"><span data-stu-id="b8343-134">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="b8343-135">Určuje přihlašovací údaje, které se mají použít při ověřování služby, a nastavení související s ověřováním přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="b8343-135">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8343-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b8343-136">Remarks</span></span>  
 <span data-ttu-id="b8343-137">Pokud žádná z vazeb používaných službou není nakonfigurovaná pro ověřování pomocí uživatelského jména a hesla, atributy pro tento element se ignorují.</span><span class="sxs-lookup"><span data-stu-id="b8343-137">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="b8343-138">Mezi ně patří `customUserNamePasswordValidatorType` ,, `includeWindowsGroups` `membershipProviderName` a `userNamePasswordValidationMode` .</span><span class="sxs-lookup"><span data-stu-id="b8343-138">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="b8343-139">Pokud není žádná z vazeb používaných službou nakonfigurovaná tak, aby pro uživatelské jméno a heslo používala ověřování systému Windows, ignorují se nastavení související s ukládáním přihlašovacích tokenů do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="b8343-139">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="b8343-140">Mezi ně patří `cacheLogonTokenLifetime` , `cacheLogonTokens` a `maxCacheLogonTokens` .</span><span class="sxs-lookup"><span data-stu-id="b8343-140">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8343-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="b8343-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
