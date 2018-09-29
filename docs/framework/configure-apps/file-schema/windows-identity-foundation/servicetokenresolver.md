---
title: '&lt;serviceTokenResolver&gt;'
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: d4b64e2c88e153834b7cf5a83bd6258b6dfd471f
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/29/2018
ms.locfileid: "47454286"
---
# <a name="ltservicetokenresolvergt"></a>&lt;serviceTokenResolver&gt;
Zaregistruje překladač tokenů služby, který se používá obslužné rutiny v kolekci obslužné rutiny tokenů. Překladač tokenů služby se používá k překladu šifrování tokenu na příchozí tokeny a zprávy.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
\<serviceTokenResolver >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|– typ|Určuje typ služby překladač tokenů. Buď <xref:System.IdentityModel.Selectors.SecurityTokenResolver> typ nebo typ, který je odvozen od <xref:System.IdentityModel.Selectors.SecurityTokenResolver> třídy. Další informace o tom, jak zadat `type` atributu naleznete v tématu [vlastní typ reference]. Požadováno.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádná  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Konfigurace pro kolekci zabezpečení poskytuje obslužné rutiny tokenů.|  
  
## <a name="remarks"></a>Poznámky  
 Překladač tokenů služby lze použít k vyřešení šifrování tokenu na příchozí tokeny a zprávy. Používá se k načtení klíče, který se má použít k dešifrování příchozí tokeny. Je nutné zadat `type` atribut. Zadaný typ může být buď <xref:System.IdentityModel.Selectors.SecurityTokenResolver> nebo vlastní typ, který je odvozen od <xref:System.IdentityModel.Selectors.SecurityTokenResolver> třídy.  
  
 Některé obslužné rutiny tokenů vám umožňují určit nastavení překladač tokenů služby v konfiguraci. Nastavení na jednotlivých obslužné rutiny tokenů přepsání zadaná v kolekci obslužné rutiny tokenů zabezpečení.  
  
> [!NOTE]
>  Zadání `<serviceTokenResolver>` prvek jako podřízený prvek [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) prvek se už nepoužívá, ale je z důvodu zpětné kompatibility stále podporována. Nastavení `<securityTokenHandlerConfiguration>` element mají přednost před akcemi na `<identityConfiguration>` elementu.  
  
## <a name="example"></a>Příklad  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
