---
title: Používání více schémat ověřování u WCF
ms.date: 03/30/2017
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
ms.openlocfilehash: 9f2c9944b424ba527fb20562706d5ad7fc3f8359
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58465487"
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a>Používání více schémat ověřování u WCF
WCF umožňuje zadat více schémat ověřování v jednom koncovém bodu. Kromě toho hostovaná na webu služby může dědit jejich nastavení ověřování přímo ze služby IIS. V místním prostředí služby můžete zadat ověření je možné schémata. Další informace o nastavení ověřování ve službě IIS najdete v tématu [ověřování služby IIS](https://go.microsoft.com/fwlink/?LinkId=232458)  
  
## <a name="iis-hosted-services"></a>IIS-Hosted Services  
 Služby hostované v IIS nastavte ověřovací schémata, které chcete použít ve službě IIS. V souboru web.config vaší služby v konfiguraci vazby zadejte typ clientcredential systému jako "InheritedFromHost" jak je znázorněno v následující fragment kódu XML:  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 Můžete určit, že chcete pouze podmnožinu schémata ověřování, který se má použít ve vaší službě pomocí ServiceAuthenticationBehavior nebo \<serviceAuthenticationManager > element. Když tato konfigurace v kódu pomocí ServiceAuthenticationBehavior, jak je znázorněno v následujícím fragmentu kódu.  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 Při konfiguraci v konfiguračním souboru, použijte \<serviceAuthenticationManager > jak ukazuje následující fragment kódu XML.  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 Tím se zajistí, že pouze podmnožinu ověřovací schémata tady se budou považovat za pro použití u koncového bodu služby v závislosti na tom, co je vybrané v IIS. To znamená, že, které se můžete vyloučit vývojář Řekněme, že základní ověřování ze seznamu vynecháním v třídě serviceAuthenticationManager výpisu a i když je povolená ve službě IIS, nebude použita na koncový bod služby  
  
## <a name="self-hosted-services"></a>V místním prostředí služby  
 V místním prostředí služby se konfigurují trochu jinak, protože neexistuje žádná služba IIS dědit nastavení z. Zde použijete \<serviceAuthenticationManager > element nebo ServiceAuthenticationBehavior k určení, které se budou dědit nastavení ověřování. V kódu vypadá takto:  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 V konfiguraci vypadá takto:  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 A můžete pak určit InheritFromHost v nastaveních vazbu, jak je znázorněno v následující fragment kódu XML.  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 Alternativně můžete zadat ověřovací schémata v vlastní vazby, nastavením schémat ověřování v HTTP přenosu element vazby, jak je znázorněno v následujícím fragmentu kódu config.  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a>Viz také:
- [Vazby a zabezpečení](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
- [Koncové body: Adresy, vazby a kontrakty](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [Konfigurace vazeb poskytovaných systémem](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Možnosti zabezpečení u vlastních vazeb](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [Vazby](../../../../docs/framework/wcf/feature-details/bindings.md)
- [Vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md)
