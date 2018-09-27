---
title: '&lt;issuerNameRegistry&gt;'
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: de3ceb5d84d17307c69e9155834a0a584e6920a1
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47399150"
---
# <a name="ltissuernameregistrygt"></a>&lt;issuerNameRegistry&gt;
Nakonfiguruje registru názvu vystavitele, který se používá obslužné rutiny v kolekci obslužná rutina tokenů.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
\<issuerNameRegistry >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry type=xs:string>  
          <optionalCustomConfigurationElements />  
        </issuerNameRegistry>  
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
|– typ|Typ, který je odvozen od <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třídy. Další informace o tom, jak určit vlastní `type`, najdete v článku [vlastní typ reference].|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)|Když `type` atribut určuje registru názvu vystavitele založená na konfiguraci ( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídy), [ \<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) elementu musí být zadán. [ \<TrustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element může trvat `<add>`, `<clear>`, nebo `<remove>` prvků jako podřízených prvků.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Konfigurace pro kolekci zabezpečení poskytuje obslužné rutiny tokenů.|  
  
## <a name="remarks"></a>Poznámky  
 Všechny tokeny vystavitele se ověřují pomocí registru názvu vystavitele. Toto je objekt, který je odvozen z <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třídy. Registru názvu vystavitele je použito k přidružení symbolický název, který kryptografický materiál, který je nezbytný k ověřování podpisů tokeny vytvářených odpovídající vystavitele. Registru názvu vystavitele udržuje seznam vystavitelů, které jsou důvěryhodné aplikace předávající strany (RP). Typ registru názvu vystavitele je určen pomocí `type` atribut. `<issuerNameRegistry>` Prvek může mít jeden nebo více podřízených elementů, které poskytují konfigurace pro zadaný typ. Poskytuje logiku, která zpracovává tyto podřízené prvky tak, že přepíšete <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> metody.  
  
 Technologie WIF umožňuje jednoho vystavitele registru typ názvu hned po spuštění <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídy. Tato třída používá sadu důvěryhodných vystavitelů certifikátů, které jsou určené v konfiguraci. Vyžaduje podřízený element konfigurace `<trustedIssuers>`, v rámci kolekce důvěryhodných vystavitelů certifikátů je nakonfigurována. Důvěryhodné certifikáty jsou zadány pomocí ASN.1 kódované podobě kryptografický otisk certifikátu a přidání nebo odebrání z kolekce s použitím `<add>`, `<clear>`, nebo `<remove>` elementy.  
  
 `<issuerNameRegistry>` Prvek je reprezentován <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> třídy.  
  
> [!NOTE]
>  Zadání `<issuerNameRegistry>` prvek jako podřízený prvek [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) prvek se už nepoužívá, ale je z důvodu zpětné kompatibility stále podporována. Nastavení `<securityTokenHandlerConfiguration>` element mají přednost před akcemi na `<identityConfiguration>` elementu.  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje, jak zadat vystavitele konfigurace na základě názvu registru.  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
