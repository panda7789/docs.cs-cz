---
title: Používání více schémat ověřování u WCF
ms.date: 03/30/2017
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
ms.openlocfilehash: 1874963573a6ec12939bd12b79574f1e2c889bfd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600215"
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a>Používání více schémat ověřování u WCF
WCF teď umožňuje zadat pro jeden koncový bod několik schémat ověřování. Webové hostované služby navíc můžou dědit nastavení ověřování přímo ze služby IIS. Služby v místním prostředí můžou určovat, která schémata ověřování se dají použít. Další informace o nastavení ověřování ve službě IIS najdete v tématu [ověřování služby IIS](https://go.microsoft.com/fwlink/?LinkId=232458) .  
  
## <a name="iis-hosted-services"></a>Služby hostované službou IIS  
 Pro služby hostované službou IIS nastavte schémata ověřování, která chcete používat ve službě IIS. Potom v souboru Web. config vaší služby v konfiguraci vazby zadejte typ clientCredential jako "InheritedFromHost", jak je znázorněno v následujícím fragmentu kódu XML:  
  
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
  
 Můžete určit, že chcete použít jenom podmnožinu ověřovacích schémat s vaší službou pomocí ServiceAuthenticationBehavior nebo \<serviceAuthenticationManager> elementu. Při konfiguraci tohoto v kódu použijte ServiceAuthenticationBehavior, jak je znázorněno v následujícím fragmentu kódu.  
  
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
  
 Při konfiguraci v konfiguračním souboru použijte \<serviceAuthenticationManager> prvek, jak je znázorněno v následujícím fragmentu kódu XML.  
  
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
  
 Tím se zajistí, že se na koncový bod služby považuje jenom podmnožina schémat ověřování, v závislosti na tom, co je ve službě IIS vybrané. To znamená, že vývojář může ze seznamu vyloučit základní ověřování vyřazením ze seznamu serviceAuthenticationManager a dokonce i v případě, že je povolený ve službě IIS, nebude ho použít na koncovém bodu služby.  
  
## <a name="self-hosted-services"></a>Samoobslužné služby  
 Samoobslužné služby jsou nakonfigurovány trochu odlišně, protože neexistují žádné služby IIS, ze kterých by bylo možné dědit nastavení. V tomto případě použijete \<serviceAuthenticationManager> prvek nebo ServiceAuthenticationBehavior k určení nastavení ověřování, které bude děděno. V kódu vypadá takto:  
  
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
  
 A pak můžete zadat InheritFromHost v nastaveních vazby, jak je znázorněno v následujícím fragmentu kódu XML.  
  
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
  
 Alternativně můžete určit schémata ověřování ve vlastní vazbě nastavením schémat ověřování na elementu vazby přenosu HTTP, jak je znázorněno v následujícím fragmentu konfigurace.  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a>Viz také

- [Vazby a zabezpečení](bindings-and-security.md)
- [Koncové body: adresy, vazby a kontrakty](endpoints-addresses-bindings-and-contracts.md)
- [Konfigurace vazeb poskytovaných systémem](configuring-system-provided-bindings.md)
- [Možnosti zabezpečení u vlastních vazeb](security-capabilities-with-custom-bindings.md)
- [Vazby](bindings.md)
- [Vlastní vazby](../extending/custom-bindings.md)
