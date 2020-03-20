---
title: Autorizace přístupu k operacím služby
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: c2ad6977674666ef65df1ea4cfe58cfd4bff8b69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183929"
---
# <a name="authorizing-access-to-service-operations"></a>Autorizace přístupu k operacím služby
Tento příklad ukazuje, jak používat [ \<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) <xref:System.Security.Permissions.PrincipalPermissionAttribute> povolit použití atributu povolit přístup k operacím služby. Tato ukázka je založena na [ukázce Začínáme.](../../../../docs/framework/wcf/samples/getting-started-sample.md) Služba a klient jsou konfigurovány [ \<pomocí wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Atribut `mode` [ \<>zabezpečení](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) byl nastaven `Message` na `clientCredentialType` a byl `Windows`nastaven na . Použije <xref:System.Security.Permissions.PrincipalPermissionAttribute> se pro každou metodu služby a slouží k omezení přístupu ke každé operaci. Volající musí být správce systému Windows pro přístup ke každé operaci.  
  
 V této ukázce je klient konzolovou aplikací (.exe) a služba je hostována internetovou informační službou (IIS).  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Konfigurační soubor služby používá `principalPermissionMode` k nastavení atributu [ \<>serviceAuthorization:](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)  
  
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
  
 Nastavení `principalPermissionMode` na `UseWindowsGroups` umožňuje použití <xref:System.Security.Permissions.PrincipalPermissionAttribute> na základě názvů skupin systému Windows.  
  
 Použití <xref:System.Security.Permissions.PrincipalPermissionAttribute> pro každou operaci vyžaduje volající ho být součástí skupiny správců systému Windows, jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi. Klient úspěšně komunikuje s každou operací, pokud je spuštěn pod účtem, který je součástí skupiny Administrators; v opačném případě je přístup odepřen. Chcete-li experimentovat s chybou autorizace, spusťte klienta pod účtem, který není součástí skupiny Administrators. Stisknutím klávesy ENTER v okně konzoly vypněte klienta.  
  
 Služba může být upozorněna na chyby <xref:System.ServiceModel.Dispatcher.IErrorHandler>autorizace implementací . Informace o implementaci naleznete v tématu Rozšíření `IErrorHandler` [kontroly nad zpracováním chyb a vytvářením sestav.](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo mezi počítači, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
