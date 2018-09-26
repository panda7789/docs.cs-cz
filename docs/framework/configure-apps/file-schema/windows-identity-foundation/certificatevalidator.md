---
title: '&lt;certificateValidator&gt;'
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 65b8aa6fa4422579ce0d1c5e33d3418ea051612a
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47077652"
---
# <a name="ltcertificatevalidatorgt"></a>&lt;certificateValidator&gt;
Určuje vlastní typ pro ověření certifikátu. Tento typ se používá jenom v případě, `certificateValidationMode` atribut [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) prvek je nastaven na "Vlastní".  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<certificateValidation >  
\<certificateValidator >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation>  
      <certificateValidator type=xs:string>  
      </certificateValidator>  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|– typ|Určuje, která je odvozena z vlastního typu <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy. Nastavte `certificateValidationMode` atribut [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) prvku "Vlastní" a pomocí tohoto typu. Další informace o tom, jak zadat `type` atributu naleznete v tématu [odkazů na vlastní typy](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md). Volitelné.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|Určuje nastavení, které obslužné rutiny tokenů používat ověřování certifikátů.|  
  
## <a name="example"></a>Příklad  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
