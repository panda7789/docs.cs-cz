---
title: Autorizace přístupu k operacím služby
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: 857e1ebe21dcb37764ddf60570a00ec35b205c8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61955004"
---
# <a name="authorizing-access-to-service-operations"></a>Autorizace přístupu k operacím služby
Tato ukázka předvádí, jak používat [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) povolit používání <xref:System.Security.Permissions.PrincipalPermissionAttribute> atribut k autorizaci přístupu k operacím služby. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) vzorku. Klienta a služby jsou nakonfigurovány [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). `mode` Atribut [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) byla nastavena na `Message` a `clientCredentialType` byla nastavena na `Windows`. <xref:System.Security.Permissions.PrincipalPermissionAttribute> Je použít pro každou metodu služby a použít k omezení přístupu k jednotlivých operacích. Volající musí být správce Windows pro přístup k každé operace.  
  
 V této ukázce je konzolová aplikace (.exe) klient a služba je hostována v Internetové informační služby (IIS).  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
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
  
 Nastavení `principalPermissionMode` k `UseWindowsGroups` umožňuje použití <xref:System.Security.Permissions.PrincipalPermissionAttribute> podle názvu skupiny Windows.  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> Platí pro každou operaci tak, aby vyžadovala volajícímu být součástí skupiny administrators Windows, jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,   
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Klient úspěšně komunikuje s každou operaci, pokud je spuštěn pod účtem, který je součástí skupiny Administrators; v opačném případě je přístup odepřen. Můžete experimentovat s selhání autorizace, spusťte klienta pomocí účtu, který není součástí skupiny Administrators. Stisknutím klávesy ENTER v okně konzoly vypnutí klient.  
  
 Služby můžete být upozorněni selhání autorizace implementací <xref:System.ServiceModel.Dispatcher.IErrorHandler>. Zobrazit [rozšíří ovládací prvek průběhu zpracování chyb a vytváření sestav](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) informace o implementaci `IErrorHandler`.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
