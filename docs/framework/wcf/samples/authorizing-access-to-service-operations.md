---
title: Autorizace přístupu k operacím služby
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: 3097c86f50a75dec8a649ca4e1edd2511a046ca8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585529"
---
# <a name="authorizing-access-to-service-operations"></a>Autorizace přístupu k operacím služby
Tato ukázka předvádí, jak použít [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) k povolení použití <xref:System.Security.Permissions.PrincipalPermissionAttribute> atributu k autorizaci přístupu k operacím služby. Tato ukázka je založená na ukázce [Začínáme](getting-started-sample.md) . Služba a klient jsou nakonfigurováni pomocí nástroje [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) . `mode`Atribut [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) byl nastaven na hodnotu `Message` a `clientCredentialType` byl nastaven na hodnotu `Windows` . <xref:System.Security.Permissions.PrincipalPermissionAttribute>Je použit pro každou metodu služby a slouží k omezení přístupu ke každé operaci. Pro přístup k jednotlivým operacím volající musí být správcem systému Windows.  
  
 V této ukázce je klient Konzolová aplikace (. exe) a služba je hostována službou Internetová informační služba (IIS).  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Konfigurační soubor služby používá [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) k nastavení `principalPermissionMode` atributu:  
  
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
  
 Nastavení, `principalPermissionMode` které `UseWindowsGroups` povolí použití <xref:System.Security.Permissions.PrincipalPermissionAttribute> v závislosti na názvech skupin systému Windows.  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>Je použita na každou operaci, aby bylo vyžadováno, aby volající byl součástí skupiny správců systému Windows, jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. Klient úspěšně komunikuje s každou operací, pokud je spuštěn pod účtem, který je součástí skupiny správců. v opačném případě přístup je odepřen. Pokud chcete experimentovat s chybou autorizace, spusťte klienta pod účtem, který není součástí skupiny správců. Ukončete klienta stisknutím klávesy ENTER v okně konzoly.  
  
 Služba může být upozorněna na selhání autorizace implementací <xref:System.ServiceModel.Dispatcher.IErrorHandler> . Viz [rozšíření kontroly nad zpracováním chyb a vytváření sestav](extending-control-over-error-handling-and-reporting.md) pro informace o implementaci `IErrorHandler` .  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).  
