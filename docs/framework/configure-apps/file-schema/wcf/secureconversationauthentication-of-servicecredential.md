---
title: <secureConversationAuthentication> z <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 61034c2c66a6d8e27a87ec5380aa7297247eb31e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935834"
---
# <a name="secureconversationauthentication-of-servicecredential"></a>\<secureConversationAuthentication > \<serviceCredential >
Určuje nastavení pro službu zabezpečené konverzace.  
  
 \<system.ServiceModel>  
\<> chování  
\<serviceBehaviors>  
\<> chování  
\<serviceCredentials>  
\<secureConversationAuthentication>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`securityStateEncoderType`|Řetězec, který určuje typ <xref:System.ServiceModel.Security.SecurityStateEncoder> , který se má použít.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Určuje přihlašovací údaje, které se mají použít při ověřování služby, a nastavení související s ověřením přihlašovacích údajů klienta.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek konfigurace slouží k určení seznamu známých typů deklarací pro serializaci souborů cookie tokenu zabezpečení (SCT) a také kodéru ke kódování a zabezpečení informací o souborech cookie. Další informace o SCT naleznete v tématu <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
