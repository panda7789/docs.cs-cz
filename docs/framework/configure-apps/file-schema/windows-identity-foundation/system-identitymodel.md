---
title: <system.identityModel>
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: 286ae88946692e6894ca3c7ee9e1348415c84ade
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943602"
---
# <a name="systemidentitymodel"></a>\<system.identityModel>
Poskytuje konfiguraci pro povolení možností Windows Identity Foundation (WIF) v aplikacích.  
  
 \<system.identityModel>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Určuje nastavení identity na úrovni služby.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`<configuration>`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
  
## <a name="remarks"></a>Poznámky  
 `<system.identityModel>` Přidejte oddíl do konfiguračního souboru a nakonfigurujte službu nebo aplikaci, aby používala Windows Identity Foundation (WIF). Element je reprezentován <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>třídou. `<system.identityModel>`  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak přidat `<system.identityModel>` oddíl do konfiguračního souboru. Nejprve je nutné přidat konfigurační oddíl a deklaraci oboru názvů pod `<configSections>` prvek. Pak můžete přidat `<system.IdentityModel>` prvek do konfiguračního souboru a zadat jednu nebo více konfigurací identity.  
  
```xml  
<configuration>  
  <configSections>  
    <!--WIF 4.5 sections -->  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
  </configSections>  
  
  ...  
  
  <system.identityModel>  
    <identityConfiguration>  
      <audienceUris>  
        <add value="http://localhost/WebApplication1/" />  
      </audienceUris>  
      <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089">  
        <trustedIssuers>  
          <add thumbprint="313D3B … 9106A9EC" name="SelfSTS" />  
        </trustedIssuers>  
      </issuerNameRegistry>  
      <certificateValidation certificateValidationMode="None"/>  
    </identityConfiguration>  
  </system.identityModel>  
  
  ...  
  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
