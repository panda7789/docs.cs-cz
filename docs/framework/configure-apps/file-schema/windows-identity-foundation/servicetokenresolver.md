---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 0983380e553acfe246d6b987784d818b8ae85b17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152577"
---
# <a name="servicetokenresolver"></a>\<> serviceTokenResolver
Registruje překladač tokenů služby, který používají obslužné rutiny v kolekci obslužné rutiny tokenu. Překládání tokenů služby se používá k překladu šifrovacího tokenu na příchozích tokenech a zprávách.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityKonfigurace>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**  
  
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
|type|Určuje typ překládání tokenu služby. <xref:System.IdentityModel.Selectors.SecurityTokenResolver> Typ nebo typ, který je <xref:System.IdentityModel.Selectors.SecurityTokenResolver> odvozen z třídy. Další informace o tom, `type` jak zadat atribut, naleznete v tématu [Vlastní odkazy typu]. Povinná hodnota.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádný  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.|  
  
## <a name="remarks"></a>Poznámky  
 Překládání tokenů služby lze vyřešit šifrovací token na příchozí tokeny a zprávy. Používá se k načtení klíče, který by měl být použit k dešifrování příchozích tokenů. Je nutné `type` zadat atribut. Zadaný typ může <xref:System.IdentityModel.Selectors.SecurityTokenResolver> být buď nebo vlastní <xref:System.IdentityModel.Selectors.SecurityTokenResolver> typ, který je odvozen z třídy.  
  
 Některé obslužné rutiny tokenů umožňují určit nastavení překladače tokenů služby v konfiguraci. Nastavení na obslužné rutiny jednotlivých tokenů přepsat ty zadané v kolekci obslužné rutiny tokenu zabezpečení.  
  
> [!NOTE]
> Určení `<serviceTokenResolver>` prvku jako podřízeného prvku [ \<identityKonfigurace>](identityconfiguration.md) element ubírala, ale je stále podporována z důvodu zpětné kompatibility. Nastavení na `<securityTokenHandlerConfiguration>` prvek přepsat ty `<identityConfiguration>` na prvek.  
  
## <a name="example"></a>Příklad  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
