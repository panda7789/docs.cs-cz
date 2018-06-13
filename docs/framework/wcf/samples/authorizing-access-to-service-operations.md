---
title: Autorizace přístupu k operacím služby
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: b7f8b9b5fc4e6524da49b4d3f23de90a123e92e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33501478"
---
# <a name="authorizing-access-to-service-operations"></a>Autorizace přístupu k operacím služby
Tento příklad znázorňuje způsob použití [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) povolit používání <xref:System.Security.Permissions.PrincipalPermissionAttribute> atribut k autorizaci přístupu k operacím služby. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) ukázka. Klienta a služby jsou konfigurováni pomocí [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). `mode` Atribut [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) byla nastavena na `Message` a `clientCredentialType` byla nastavena na `Windows`. <xref:System.Security.Permissions.PrincipalPermissionAttribute> Je použít pro každou metodu služby a slouží k omezení přístupu na každou operaci. Volající musí být správcem systému Windows pro přístup k jednotlivých operací.  
  
 V této ukázce klienta je konzolová aplikace (.exe) a služba je hostovaná Internetové informační služby (IIS).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Konfigurační soubor služby používá [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) nastavit `principalPermissionMode` atribut:  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior>   
      <!-- The serviceAuthorization behavior sets the  
           principalPermissionMode to UseWindowsGroups.  
           This puts a WindowsPrincipal on the current thread when a   
           service is invoked. -->  
      <serviceAuthorization principalPermissionMode="UseWindowsGroups" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Nastavení `principalPermissionMode` k `UseWindowsGroups` umožňuje použití <xref:System.Security.Permissions.PrincipalPermissionAttribute> podle názvů skupin systému Windows.  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> Se použijí na každou operaci tak, aby vyžadovala volajícího, aby být součástí skupiny administrators systému Windows, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
[PrincipalPermission(SecurityAction.Demand,   
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Klient úspěšně komunikuje s každou operaci, pokud je spuštěn pod účtem, který je součástí skupiny Administrators; jinak byl odepřen přístup. A experimentovat s selhání autorizace, spusťte klienta pod účtem, který není součástí skupiny Administrators. Stisknutím klávesy ENTER v okně konzoly vypnout klienta.  
  
 Službu můžete informováni o selhání ověřování implementací <xref:System.ServiceModel.Dispatcher.IErrorHandler>. V tématu [rozšíření řízení přes zpracování chyb a generování sestav](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) informace o implementaci `IErrorHandler`.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Viz také
