---
title: Diagnostika prostřednictvím rozhraní WMI (Windows Management Instrumentation)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0862f747cb969a6aa2e63d86e842097260e95b56
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a>Diagnostika prostřednictvím rozhraní WMI (Windows Management Instrumentation)
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]zpřístupní dat kontroly služby za běhu prostřednictvím [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zprostředkovatele Windows Management Instrumentation (WMI).  
  
## <a name="enabling-wmi"></a>Povolení služby WMI  
 Služba WMI je implementace Web-Based Enterprise Management (WBEM) standardní společnosti Microsoft. [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]Sada SDK rozhraní WMI najdete v části [Windows Management Instrumentation](https://msdn.microsoft.com/library/aa394582.aspx). WBEM je oborový standard pro jak aplikace vystavit WMI pro externí nástroje pro správu.  
  
 Zprostředkovatel rozhraní WMI je součást, která zveřejňuje instrumentace za běhu prostřednictvím rozhraní WBEM kompatibilní. Obsahuje sadu objektů rozhraní WMI, které mají dvojice atribut hodnota. Dvojice může mít několik jednoduchých typů. Nástroje pro správu můžete připojit ke službám prostřednictvím rozhraní za běhu. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]zpřístupní atributy služeb, jako je adresy, vazby, chování a naslouchací procesy.  
  
 Předdefinované zprostředkovatele rozhraní WMI je možné aktivovat v konfiguračním souboru aplikace. To se provádí prostřednictvím `wmiProviderEnabled` atribut [ \<diagnostics >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) v [ \<system.serviceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) části, jak znázorňuje následující ukázka konfigurace.  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 Tato položka konfigurace vystavuje rozhraní WMI. Aplikace pro správu teď můžete připojit přes toto rozhraní a přístup WMI aplikace.  
  
## <a name="accessing-wmi-data"></a>Přístup k datům rozhraní WMI  
 Data rozhraní WMI je přístupná v mnoha různými způsoby. Společnost Microsoft poskytuje rozhraní API služby WMI pro skripty, [!INCLUDE[vbprvb](../../../../../includes/vbprvb-md.md)] aplikace, aplikace C++ a [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]. Další informace najdete v tématu [pomocí rozhraní WMI](http://go.microsoft.com/fwlink/?LinkId=95183).  
  
> [!CAUTION]
>  Pokud používáte rozhraní .NET Framework poskytuje metody pro přístup programu ke dat služby WMI, byste měli vědět, že tyto metody může vyvolat výjimky při připojení. Během vytváření služby nebude navázáno připojení <xref:System.Management.ManagementObject> instanci, ale v prvním požadavku zahrnující exchange skutečná data. Proto byste měli používat `try..catch` bloku k zachycení možné výjimky.  
  
 Můžete změnit na trasování a úroveň protokolování zpráv, a také možnosti protokolování zpráv pro `System.ServiceModel` zdroj trasování v rozhraní WMI. To lze provést pomocí přístupu k [AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) instanci, která zpřístupňuje tyto logická hodnota vlastnosti: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, a `TraceLevel`. Proto pokud nakonfigurujete naslouchací proces trasování pro protokolování zpráv, ale nastavit tyto možnosti pro `false` v konfiguraci, můžete později změnit, aby `true` při spuštění aplikace. Efektivně tím povolíte protokolování zpráv za běhu. Podobně pokud povolíte protokolování v konfiguračním souboru zpráv, ji můžete vypnout v době běhu pomocí služby WMI.  
  
 Je třeba si uvědomit, že pokud žádné protokolování zpráv trasování – moduly naslouchání pro protokolování zpráv nebo Ne `System.ServiceModel` trasování – moduly naslouchání pro trasování jsou zadané v konfiguračním souboru, změny jsou přijata žádná platit, i když přijímat změny jsou rozhraní WMI. Další informace o správné nastavení příslušných naslouchací procesy najdete v tématu [konfigurace protokolování zpráv](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) a [Konfigurace trasování](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md). Úroveň trasování ze všech ostatních zdrojů trasování zadáno v konfiguraci je platná, když se aplikace spustí a nelze je změnit.  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]zpřístupní `GetOperationCounterInstanceName` metoda pro skriptování. Tato metoda vrátí název instance čítače výkonu, pokud jste zadali s názvem operaci. Neověřuje však váš vstup. Proto pokud zadáte název nesprávný operace, je vrácen název nesprávné čítače.  
  
 `OutgoingChannel` Vlastnost `Service` instance nepočítá kanály otevřít službou se připojit k jiné službě, pokud [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] klienta do cílové služby není vytvořena v rámci `Service` metoda.  
  
 **Upozornění:** podporuje pouze rozhraní WMI <xref:System.TimeSpan> hodnotu až 3 desetinných míst. Například, pokud vaše služba nastaví její vlastnosti, aby <xref:System.TimeSpan.MaxValue>, jeho hodnota se zkrátí po 3 desetinných míst, při zobrazení v rozhraní WMI.  
  
## <a name="security"></a>Zabezpečení  
 Protože [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zprostředkovatele rozhraní WMI umožňuje zjišťování služeb v prostředí, postupujte opatrně extrémně pro udělení přístupu k němu. Pokud jste uvolnit výchozí přístup pouze správce, může povolit méně důvěryhodné strany přístup k citlivým datům ve vašem prostředí. Pokud jste povolte oprávnění pro vzdálený přístup k rozhraní WMI, konkrétně zahlcení útoky může dojít k. Pokud proces je přetížené nadměrné požadavky rozhraní WMI, může docházet ke snížení jeho výkon.  
  
 Kromě toho pokud jste uvolnit přístupová oprávnění pro soubor MOF, méně důvěryhodné strany můžete upravit chování rozhraní WMI a měnit objekty, které jsou načteny ve schématu WMI. Například pole můžete odebrat tak, že je důležitá data zakryté od správce nebo pole, která naplnit nebo způsobit výjimky jsou přidány do souboru.  
  
 Ve výchozím nastavení [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zprostředkovatele rozhraní WMI uděluje "provést metodu", "zapisovat zprostředkovatele" a "Povolit účet" oprávnění pro správce a oprávnění "Povolit účet" pro ASP.NET, místní služby a síťové služby. Konkrétně na jinou hodnotu než[!INCLUDE[wv](../../../../../includes/wv-md.md)] platforem ASP.NET účtu má přístup pro čtení k oboru názvů WMI ServiceModel. Pokud nechcete udělení těchto oprávnění určitou skupinu uživatelů, si deaktivovat zprostředkovatele rozhraní WMI (je zakázáno ve výchozím nastavení), nebo zakázat přístup pro určité uživatelské skupiny.  
  
 Kromě toho při pokusu o povolení rozhraní WMI prostřednictvím konfigurace není povolené rozhraní WMI z důvodu nedostatečných uživatelských oprávnění. Ale žádná událost se zapíše do protokolu událostí k zaznamenání této chyby.  
  
 Chcete-li upravit úrovně oprávnění uživatele, použijte následující kroky.  
  
1.  Klikněte na tlačítko Start a pak spusťte a zadejte **compmgmt.msc**.  
  
2.  Klikněte pravým tlačítkem na **služby a aplikace/WMI ovládací prvky** vyberte **vlastnosti**.  
  
3.  Vyberte **zabezpečení** kartě a přejděte do **kořenové nebo ServiceModel** oboru názvů. Klikněte **zabezpečení** tlačítko.  
  
4.  Vyberte konkrétní skupinu nebo uživatele, který chcete řízení přístupu a použití **povolit** nebo **Odepřít** políčko konfigurace oprávnění.  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a>Udělení oprávnění registrace služby WCF WMI dalším uživatelům  
 WCF zpřístupní data správy k rozhraní WMI. Dělá to tak hostováním poskytovatele rozhraní WMI v procesu, někdy označuje jako "odpojeného zprostředkovatele". Pro data správy, které mají být exponovány účet, který registruje tohoto zprostředkovatele musí mít příslušná oprávnění. V systému Windows můžete pouze malého privilegovaných účtů zaregistrovat odpojeného zprostředkovatele ve výchozím nastavení. Tento problém je, protože uživatelé běžně chcete vystavit data rozhraní WMI ze služby WCF spuštěn pod účtem, který není v sadě výchozí.  
  
 Pokud chcete poskytnout tento přístup, musí správce udělit následující oprávnění k další účet v následujícím pořadí:  
  
1.  Oprávnění k přístupu k Namespace WMI WCF.  
  
2.  Oprávnění k registraci zprostředkovatele rozhraní WMI odpojené WCF.  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a>Udělit oprávnění k oboru názvů rozhraní WMI  
  
1.  Spusťte následující skript prostředí PowerShell.  
  
    ```powershell  
    write-host ""  
    write-host "Granting Access to root/servicemodel WMI namespace to built in users group"  
    write-host ""  
  
    # Create the binary representation of the permissions to grant in SDDL  
    $newPermissions = "O:BAG:BAD:P(A;CI;CCDCLCSWRPWPRCWD;;;BA)(A;CI;CC;;;NS)(A;CI;CC;;;LS)(A;CI;CC;;;BU)"  
    $converter = new-object system.management.ManagementClass Win32_SecurityDescriptorHelper  
    $binarySD = $converter.SDDLToBinarySD($newPermissions)  
    $convertedPermissions = ,$binarySD.BinarySD  
  
    # Get the object used to set the permissions  
    $security = gwmi -namespace root/servicemodel -class __SystemSecurity  
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "Previous ACL: "$outsddl.SDDL  
  
    # Change the Access Control List (ACL) using SDDL  
    $result = $security.PsBase.InvokeMethod("SetSD",$convertedPermissions)   
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "New ACL:      "$outsddl.SDDL  
    write-host ""  
    ```  
  
     Tento skript prostředí PowerShell používá zabezpečení SDDL Descriptor Definition Language () k udělení přístupu skupiny předdefinované uživatelé k oboru názvů WMI "kořenový/servicemodel". Následující seznamy ACL určuje:  
  
    -   Předdefinovaný účet Administrator (BA) - už měli přístup.  
  
    -   Síťová služba (NS) - už měli přístup.  
  
    -   Místní systém (LS) - už měli přístup.  
  
    -   Předdefinované uživatelé – skupina k udělení přístupu k.  
  
#### <a name="to-grant-provider-registration-access"></a>Zprostředkovatel udělit přístup k registraci  
  
1.  Spusťte následující skript prostředí PowerShell.  
  
    ```powershell  
    write-host ""  
    write-host "Granting WCF provider registration access to built in users group"  
    write-host ""  
    # Set security on ServiceModel provider  
    $provider = get-WmiObject -namespace "root\servicemodel" __Win32Provider  
  
    write-host "Previous ACL: "$provider.SecurityDescriptor  
    $result = $provider.SecurityDescriptor = "O:BUG:BUD:(A;;0x1;;;BA)(A;;0x1;;;NS)(A;;0x1;;;LS)(A;;0x1;;;BU)"  
  
    # Commit the changes and display it to the console  
    $result = $provider.Put()  
    write-host "New ACL:      "$provider.SecurityDescriptor  
    write-host ""  
    ```  
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a>Udělení přístupu na libovolného uživatele nebo skupiny  
 Příklad v této části uděluje oprávnění registrace zprostředkovatele rozhraní WMI na všech místních uživatelů. Pokud chcete udělit přístup na uživatele nebo skupinu, která není součástí, pak je nutné získat tohoto uživatele nebo skupiny identifikátor zabezpečení (SID). Neexistuje žádný jednoduchý způsob, jak získat identifikátor SID pro libovolný uživatel. Přihlaste se jako požadovaného uživatele a potom vydat příkaz prostředí je jednu metodu.  
  
```  
Whoami /user  
```  
  
 To poskytuje SID aktuálního uživatele, ale tuto metodu nelze použít k získání SID na každý libovolný uživatel. Další možností, jak získat identifikátor SID je použití [getsid.exe](http://go.microsoft.com/fwlink/?LinkId=186467) nástroje z [Windows 2000 Resource Kit Tools pro úlohy správy](http://go.microsoft.com/fwlink/?LinkId=178660). Tento nástroj porovná SID dva uživatele (místní nebo doménový) a jako straně vliv vytiskne dva identifikátory SID na příkazový řádek. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Dobře známé identifikátory SID](http://go.microsoft.com/fwlink/?LinkId=186468).  
  
## <a name="accessing-remote-wmi-object-instances"></a>Přístup k rozhraní WMI Vzdálená instance objektů  
 Pokud budete potřebovat pro přístup k [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] instance rozhraní WMI na vzdáleném počítači, je nutné povolit paket o ochraně osobních údajů nástroje, které používáte pro přístup. Následující část popisuje, jak tyto dosáhnout pomocí WMI CIM Studio, testování služby WMI, jakož i rozhraní .NET SDK 2.0.  
  
### <a name="wmi-cim-studio"></a>Rozhraní WMI CIM Studio  
 Pokud jste nainstalovali [nástroje pro správu služby WMI](http://go.microsoft.com/fwlink/?LinkId=95185), můžete použít nástroje CIM Studio WMI k instancím přístup k rozhraní WMI. Nástroje jsou v následující složce  
  
 **%WINDIR%\Program Files\WMI nástroje\\**  
  
1.  V **připojit k oboru názvů:** zadejte **root\ServiceModel** a klikněte na tlačítko **OK.**  
  
2.  V **WMI CIM Studio přihlášení** okně klikněte na tlačítko **možnosti >>** tlačítko rozbalte okno. Vyberte **paket o ochraně osobních údajů** pro **úroveň ověřování**a klikněte na tlačítko **OK**.  
  
### <a name="windows-management-instrumentation-tester"></a>Testování služby WMI  
 Tento nástroj je nainstalována v systému Windows. Ji spustit, spusťte příkaz konzole zadáním **cmd.exe** v **spuštění a spuštění** dialogové okno a klikněte na tlačítko **OK**. Poté zadejte **wbemtest.exe** v příkazovém okně. Pak je spustit nástroj testování služby WMI.  
  
1.  Klikněte **Connect** tlačítko v pravém horním rohu okna.  
  
2.  V novém okně zadejte **root\ServiceModel** pro **Namespace** pole a vyberte možnost **paket o ochraně osobních údajů** pro **úroveň ověřování**. Klikněte na tlačítko **připojit**.  
  
### <a name="using-managed-code"></a>Pomocí spravovaného kódu  
 Máte můžete také přístup k vzdálené instance rozhraní WMI prostřednictvím kódu programu pomocí třídy poskytované <xref:System.Management> oboru názvů. Následující příklad kódu ukazuje, jak to udělat.  
  
```  
String wcfNamespace = String.Format(@"\\{0}\Root\ServiceModel",      
   this.serviceMachineName);  
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
