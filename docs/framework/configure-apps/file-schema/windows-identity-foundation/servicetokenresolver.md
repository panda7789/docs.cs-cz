---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 30a53c11b551623311f7ca3f957143fc702568a1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251851"
---
# <a name="servicetokenresolver"></a>\<serviceTokenResolver>
Registruje překladač tokenů služby, který jsou používány obslužnými rutinami v kolekci obslužných rutin tokenu. Překladač tokenů služby se používá k překladu šifrovacího tokenu na příchozích tokenech a zprávách.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceTokenResolver >**  
  
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
|– typ|Určuje typ překladače tokenu služby. Buď typ, nebo typ, který je odvozen <xref:System.IdentityModel.Selectors.SecurityTokenResolver> od třídy. <xref:System.IdentityModel.Selectors.SecurityTokenResolver> Další informace o tom, jak zadat `type` atribut, naleznete v tématu [odkazy na vlastní typ]. Povinný parametr.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.|  
  
## <a name="remarks"></a>Poznámky  
 Překladač tokenů služby se dá použít k vyřešení šifrovacího tokenu u příchozích tokenů a zpráv. Používá se k načtení klíče, který by se měl použít k dešifrování příchozích tokenů. Je nutné zadat `type` atribut. Zadaný typ může být buď <xref:System.IdentityModel.Selectors.SecurityTokenResolver> nebo vlastní typ, který je odvozen <xref:System.IdentityModel.Selectors.SecurityTokenResolver> od třídy.  
  
 Některé obslužné rutiny tokenů umožňují zadat nastavení překladače tokenu služby v konfiguraci. Nastavení pro obslužné rutiny jednotlivých tokenů přepíší ty zadané v kolekci obslužných rutin tokenu zabezpečení.  
  
> [!NOTE]
> Určení prvku jako podřízeného prvku [ \<prvku IdentityConfiguration >](identityconfiguration.md) je zastaralé, ale stále se podporuje z důvodu zpětné kompatibility. `<serviceTokenResolver>` Nastavení na `<securityTokenHandlerConfiguration>` elementu přepíší tyto prvky `<identityConfiguration>` na elementu.  
  
## <a name="example"></a>Příklad  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
 