---
title: '&lt;issuerTokenResolver&gt;'
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: eefd18c206b7f013c3a423df424c795583c0dde8
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47216328"
---
# <a name="ltissuertokenresolvergt"></a>&lt;issuerTokenResolver&gt;
Zaregistruje překladač tokenů vystavitele, který se používá obslužné rutiny v kolekci obslužné rutiny tokenů. Překladač tokenů vystavitele se používá k překladu podpisový token na příchozí tokeny a zprávy.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
\<issuerTokenResolver >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerTokenResolver type=xs:string>  
        </issuerTokenResolver>  
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
|– typ|Určuje typ překladač tokenů vystavitele. Musí být buď <xref:System.IdentityModel.Tokens.IssuerTokenResolver> třídy nebo typ, který je odvozen od <xref:System.IdentityModel.Tokens.IssuerTokenResolver> třídy. Požadováno.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Konfigurace pro kolekci zabezpečení poskytuje obslužné rutiny tokenů.|  
  
## <a name="remarks"></a>Poznámky  
 Překladač tokenů vystavitele se používá k překladu podpisový token na příchozí tokeny a zprávy. Používá se k načtení kryptografický materiál, který se používá pro kontrolu podpisu. Je nutné zadat `type` atribut. Zadaný typ může být buď <xref:System.IdentityModel.Tokens.IssuerTokenResolver> nebo vlastní typ, který je odvozen od <xref:System.IdentityModel.Tokens.IssuerTokenResolver> třídy.  
  
 Některé obslužné rutiny tokenů vám umožňují určit nastavení vystavitele překladač tokenů v konfiguraci. Nastavení na jednotlivých obslužné rutiny tokenů přepsání zadaná v kolekci obslužné rutiny tokenů zabezpečení.  
  
> [!NOTE]
>  Zadání `<issuerTokenResolver>` prvek jako podřízený prvek [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) prvek se už nepoužívá, ale je z důvodu zpětné kompatibility stále podporována. Nastavení `<securityTokenHandlerConfiguration>` element mají přednost před akcemi na `<identityConfiguration>` elementu.  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje konfiguraci pro překladač tokenů vystavitele, který je založen na vlastní třídu, která je odvozena z <xref:System.IdentityModel.Tokens.IssuerTokenResolver>. Překladač tokenů udržuje slovník párů klíč cílové skupiny, který je inicializován z prvku vlastní konfigurace (`<AddAudienceKeyPair>`) definovaný pro třídu. Třída přepsání <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> metodu ke zpracování tohoto elementu. Přepsání je znázorněno v následujícím příkladu; metody, které volá, ale nejsou zobrazeny pro zkrácení. Kompletní příklad najdete v článku `CustomToken` vzorku.  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a>Příklad  
  
```  
public override void LoadCustomConfiguration(System.Xml.XmlNodeList nodelist)  
{  
    foreach (XmlNode node in nodelist)  
    {  
        XmlDictionaryReader rdr = XmlDictionaryReader.CreateDictionaryReader(new XmlTextReader(new StringReader(node.OuterXml)));  
        rdr.MoveToContent();  
  
        string symmetricKey = rdr.GetAttribute("symmetricKey");  
        string audience = rdr.GetAttribute("audience");  
  
        this.AddAudienceKeyPair(audience, symmetricKey);  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
