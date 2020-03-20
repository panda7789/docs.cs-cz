---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 67d7e0aa5b6b05bfe8b17a1b1efebb1fbddbb0eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152668"
---
# <a name="issuertokenresolver"></a>\<> překladače tokenu
Registruje překladač tokenů vystavitelů, který používají obslužné rutiny v kolekci obslužné rutiny tokenu. Překladač tokenů vystavithonu se používá k vyřešení podpisového tokenu na příchozích tokenech a zprávách.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityKonfigurace>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>překladače tokenu**  
  
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
|type|Určuje typ překládání tokenů vystavitenu. Musí být <xref:System.IdentityModel.Tokens.IssuerTokenResolver> třída nebo typ, který <xref:System.IdentityModel.Tokens.IssuerTokenResolver> je odvozen z třídy. Povinná hodnota.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádný  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.|  
  
## <a name="remarks"></a>Poznámky  
 Překladač tokenů vystavithonu se používá k vyřešení podpisového tokenu na příchozích tokenech a zprávách. Používá se k načtení kryptografického materiálu, který se používá ke kontrole podpisu. Je nutné `type` zadat atribut. Zadaný typ může <xref:System.IdentityModel.Tokens.IssuerTokenResolver> být buď nebo vlastní <xref:System.IdentityModel.Tokens.IssuerTokenResolver> typ, který je odvozen z třídy.  
  
 Některé obslužné rutiny tokenů umožňují určit nastavení překladače tokenů vystavithonu v konfiguraci. Nastavení na obslužné rutiny jednotlivých tokenů přepsat ty zadané v kolekci obslužné rutiny tokenu zabezpečení.  
  
> [!NOTE]
> Určení `<issuerTokenResolver>` prvku jako podřízeného prvku [ \<identityKonfigurace>](identityconfiguration.md) element ubírala, ale je stále podporována z důvodu zpětné kompatibility. Nastavení na `<securityTokenHandlerConfiguration>` prvek přepsat ty `<identityConfiguration>` na prvek.  
  
## <a name="example"></a>Příklad  
 Následující jazyk XML zobrazuje konfiguraci pro překladače tokenů vystavithonu, který je založen na vlastní třídě, která je odvozena od <xref:System.IdentityModel.Tokens.IssuerTokenResolver>. Překladač tokenů udržuje slovník párů publika a klíčů, který je inicializován z vlastního konfiguračního prvku (`<AddAudienceKeyPair>`) definovaného pro třídu. Třída přepíše <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> metodu ke zpracování tohoto prvku. Přepsání je znázorněno v následujícím příkladu; metody, které volá však nejsou zobrazeny pro stručnost. Úplný příklad naleznete v `CustomToken` ukázce.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
