---
title: "Používání více schémat ověřování u WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cf74b38c15cf8dc68218c39246c8999c4ec44493
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a>Používání více schémat ověřování u WCF
WCF teď umožňuje zadat více schémat ověřování v jednom koncovém bodě. Kromě toho hostovaná na webu služby může dědit vlastnosti jejich nastavení ověřování přímo ze služby IIS. Samoobslužné hostované služby můžete určit, jaké ověřování můžete použít schémata. Další informace o nastavení ověřování ve službě IIS najdete v tématu [ověřování služby IIS](http://go.microsoft.com/fwlink/?LinkId=232458)  
  
## <a name="iis-hosted-services"></a>Služba IIS hostované služby  
 Pro službu IIS hostované služby nastavte schémat ověřování, který si přejete použít ve službě IIS. V souboru web.config vaší služby, v konfiguraci vazby zadejte typ clientCredential jako "InheritedFromHost" jak je znázorněno v následujícím fragmentu kódu XML:  
  
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
  
 Můžete zadat, že chcete pouze podmnožinu schémat ověřování pro použití s služby pomocí ServiceAuthenticationBehavior nebo \<serviceAuthenticationManager > elementu. Když tato konfigurace v kódu pomocí ServiceAuthenticationBehavior, jak je znázorněno v následující fragment kódu.  
  
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
  
 Při konfiguraci v konfiguračním souboru, použijte \<serviceAuthenticationManager > elementu, jak je znázorněno v následujícím fragmentu kódu XML.  
  
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
  
 Tím bude zajištěno, že budou považovány za jenom podmnožinu schémat ověřování, které jsou zde uvedeny pro použití na koncový bod služby, v závislosti na tom, co je vybrané v IIS. To znamená, které můžete vyloučit vývojář vyslovení základní ověřování ze seznamu vynecháním ze seznamu serviceAuthenticationManager a i v případě, že je povolena ve službě IIS, nebudou použity na koncový bod služby  
  
## <a name="self-hosted-services"></a>Samoobslužné hostované služby  
 Vlastním hostováním služby jsou nakonfigurovány trochu jinak, protože neexistuje žádné služby IIS pro dědění nastavení z. Tady můžete použít \<serviceAuthenticationManager > elementu nebo ServiceAuthenticationBehavior a zadejte nastavení ověřování, které zdědí. V kódu vypadá takto:  
  
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
  
 A můžete pak určit InheritFromHost v nastaveních vazby, jak je znázorněno v následujícím fragmentu kódu XML.  
  
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
  
 Alternativně můžete zadat schémat ověřování v vlastní vazby, nastavením schémat ověřování v HTTP přenosu prvku vazby, jak je znázorněno v následujícím fragmentu kódu konfigurace.  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a>Viz také  
 [Vazby a zabezpečení](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [Koncové body: Adresy, vazby a kontrakty](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Možnosti zabezpečení u vlastních vazeb](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [Vazby](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [Vazby](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [Vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md)
