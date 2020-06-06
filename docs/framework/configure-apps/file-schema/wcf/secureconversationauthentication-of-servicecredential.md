---
title: <secureConversationAuthentication> z <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 336969c654f332ae3d838d8fd6d1c4243838539c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399942"
---
# <a name="secureconversationauthentication-of-servicecredential"></a><span data-ttu-id="b0c18-102">\<secureConversationAuthentication> z \<serviceCredential></span><span class="sxs-lookup"><span data-stu-id="b0c18-102">\<secureConversationAuthentication> of \<serviceCredential></span></span>
<span data-ttu-id="b0c18-103">Určuje nastavení pro službu zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="b0c18-103">Specifies the settings for a secure conversation service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<secureConversationAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="b0c18-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0c18-104">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0c18-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b0c18-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b0c18-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b0c18-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0c18-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="b0c18-107">Attributes</span></span>  
  
|<span data-ttu-id="b0c18-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="b0c18-108">Attribute</span></span>|<span data-ttu-id="b0c18-109">Popis</span><span class="sxs-lookup"><span data-stu-id="b0c18-109">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="b0c18-110">Řetězec, který určuje typ, který se <xref:System.ServiceModel.Security.SecurityStateEncoder> má použít.</span><span class="sxs-lookup"><span data-stu-id="b0c18-110">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b0c18-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b0c18-111">Child Elements</span></span>  
 <span data-ttu-id="b0c18-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="b0c18-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b0c18-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b0c18-113">Parent Elements</span></span>  
  
|<span data-ttu-id="b0c18-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="b0c18-114">Element</span></span>|<span data-ttu-id="b0c18-115">Description</span><span class="sxs-lookup"><span data-stu-id="b0c18-115">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="b0c18-116">Určuje přihlašovací údaje, které se mají použít při ověřování služby, a nastavení související s ověřením přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="b0c18-116">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0c18-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b0c18-117">Remarks</span></span>  
 <span data-ttu-id="b0c18-118">Tento prvek konfigurace slouží k určení seznamu známých typů deklarací pro serializaci souborů cookie tokenu zabezpečení (SCT) a také kodéru ke kódování a zabezpečení informací o souborech cookie.</span><span class="sxs-lookup"><span data-stu-id="b0c18-118">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="b0c18-119">Další informace o SCT naleznete v tématu <xref:System.ServiceModel.Security.SecureConversationServiceCredential> .</span><span class="sxs-lookup"><span data-stu-id="b0c18-119">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0c18-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0c18-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
