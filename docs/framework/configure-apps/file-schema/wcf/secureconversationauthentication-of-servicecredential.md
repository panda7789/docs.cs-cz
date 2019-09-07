---
title: <secureConversationAuthentication> z <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 336969c654f332ae3d838d8fd6d1c4243838539c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399942"
---
# <a name="secureconversationauthentication-of-servicecredential"></a><span data-ttu-id="72cac-102">\<secureConversationAuthentication > \<serviceCredential ></span><span class="sxs-lookup"><span data-stu-id="72cac-102">\<secureConversationAuthentication> of \<serviceCredential></span></span>
<span data-ttu-id="72cac-103">Určuje nastavení pro službu zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="72cac-103">Specifies the settings for a secure conversation service.</span></span>  
  
<span data-ttu-id="72cac-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="72cac-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="72cac-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="72cac-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="72cac-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="72cac-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="72cac-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="72cac-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="72cac-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="72cac-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="72cac-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="72cac-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="72cac-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<secureConversationAuthentication >**</span><span class="sxs-lookup"><span data-stu-id="72cac-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<secureConversationAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72cac-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72cac-111">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72cac-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="72cac-112">Attributes and Elements</span></span>  
 <span data-ttu-id="72cac-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="72cac-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72cac-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="72cac-114">Attributes</span></span>  
  
|<span data-ttu-id="72cac-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="72cac-115">Attribute</span></span>|<span data-ttu-id="72cac-116">Popis</span><span class="sxs-lookup"><span data-stu-id="72cac-116">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="72cac-117">Řetězec, který určuje typ <xref:System.ServiceModel.Security.SecurityStateEncoder> , který se má použít.</span><span class="sxs-lookup"><span data-stu-id="72cac-117">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="72cac-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="72cac-118">Child Elements</span></span>  
 <span data-ttu-id="72cac-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="72cac-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="72cac-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="72cac-120">Parent Elements</span></span>  
  
|<span data-ttu-id="72cac-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="72cac-121">Element</span></span>|<span data-ttu-id="72cac-122">Popis</span><span class="sxs-lookup"><span data-stu-id="72cac-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72cac-123">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="72cac-123">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="72cac-124">Určuje přihlašovací údaje, které se mají použít při ověřování služby, a nastavení související s ověřením přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="72cac-124">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72cac-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72cac-125">Remarks</span></span>  
 <span data-ttu-id="72cac-126">Tento prvek konfigurace slouží k určení seznamu známých typů deklarací pro serializaci souborů cookie tokenu zabezpečení (SCT) a také kodéru ke kódování a zabezpečení informací o souborech cookie.</span><span class="sxs-lookup"><span data-stu-id="72cac-126">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="72cac-127">Další informace o SCT naleznete v tématu <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span><span class="sxs-lookup"><span data-stu-id="72cac-127">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72cac-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72cac-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
