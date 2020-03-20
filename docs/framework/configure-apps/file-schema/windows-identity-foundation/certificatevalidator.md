---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 3f3d79d3567c1714a79423b7767ce3f454b9d52d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152785"
---
# <a name="certificatevalidator"></a>\<certifikátValidator>
Určuje vlastní typ pro ověření certifikátu. Tento typ se používá `certificateValidationMode` pouze v případě, že atribut [ \<certifikátuValidation>](certificatevalidation.md) element je nastaven na "Vlastní".  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityKonfigurace>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>ověření certifikátu**](certificatevalidation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certifikátValidator>**  
  
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
|type|Určuje vlastní typ, který je <xref:System.IdentityModel.Selectors.X509CertificateValidator> odvozen od třídy. Nastavte `certificateValidationMode` atribut [ \<certifikátuValidation>](certificatevalidation.md) elementu na "Vlastní" pro použití tohoto typu. Další informace o tom, `type` jak zadat atribut, naleznete v [tématu Vlastní odkazy na typ](../windows-workflow-foundation/index.md). Nepovinný parametr.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádný  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<>ověření certifikátu](certificatevalidation.md)|Řídí nastavení, která obslužné rutiny tokenů používají k ověření certifikátů.|  
  
## <a name="example"></a>Příklad  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />
</certificateValidation>
```
