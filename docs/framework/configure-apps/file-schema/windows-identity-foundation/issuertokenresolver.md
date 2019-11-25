---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 451750a1facd9a886b53427a8d54580d1a939fa5
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968509"
---
# <a name="issuertokenresolver"></a>\<issuerTokenResolver >
Registruje překladač tokenů vystavitele, který jsou používány obslužnými rutinami v kolekci obslužných rutin tokenu. Překladač tokenů vystavitele se používá k překladu podpisového tokenu na příchozích tokenech a zprávách.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuerTokenResolver >**  
  
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
|– typ|Určuje typ překladače tokenu vystavitele. Musí být buď třída <xref:System.IdentityModel.Tokens.IssuerTokenResolver>, nebo typ, který je odvozený od <xref:System.IdentityModel.Tokens.IssuerTokenResolver> třídy. Požadováno.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md)|Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.|  
  
## <a name="remarks"></a>Poznámky  
 Překladač tokenů vystavitele se používá k překladu podpisového tokenu na příchozích tokenech a zprávách. Slouží k načtení kryptografického materiálu, který se používá k ověření podpisu. Je nutné zadat atribut `type`. Zadaný typ může být buď <xref:System.IdentityModel.Tokens.IssuerTokenResolver>, nebo vlastní typ, který je odvozený od <xref:System.IdentityModel.Tokens.IssuerTokenResolver> třídy.  
  
 Některé obslužné rutiny tokenů umožňují zadat nastavení překladače tokenu vystavitele v konfiguraci. Nastavení pro obslužné rutiny jednotlivých tokenů přepíší ty zadané v kolekci obslužných rutin tokenu zabezpečení.  
  
> [!NOTE]
> Určení prvku `<issuerTokenResolver>` jako podřízený element elementu [\<identityConfiguration >](identityconfiguration.md) je zastaralé, ale stále se podporuje z důvodu zpětné kompatibility. Nastavení v prvku `<securityTokenHandlerConfiguration>` přepíší ty na `<identityConfiguration>` elementu.  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje konfiguraci překladače tokenu vystavitele, který je založen na vlastní třídě, která je odvozena od <xref:System.IdentityModel.Tokens.IssuerTokenResolver>. Překladač tokenů udržuje slovník dvojic klíčů cílové skupiny, které jsou inicializovány z vlastního elementu konfigurace (`<AddAudienceKeyPair>`) definovaného pro třídu. Třída přepíše metodu <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> pro zpracování tohoto elementu. Přepsání je uvedeno v následujícím příkladu. Nicméně metody, které volá, nejsou zobrazeny pro zkrácení. Úplný příklad najdete v ukázce `CustomToken`.  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a>Příklad
  
```csharp
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
