---
title: Diagnostika prostřednictvím rozhraní WMI (Windows Management Instrumentation)
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: b7c898f1af91f639939e5480687b5967bf57d246
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406917"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a>Diagnostika prostřednictvím rozhraní WMI (Windows Management Instrumentation)
Windows Communication Foundation (WCF) poskytuje dat kontroly služby za běhu pomocí zprostředkovatele WCF Windows Management Instrumentation (WMI).  
  
## <a name="enabling-wmi"></a>Povolení rozhraní WMI  
 Rozhraní WMI se výlučně implementace Microsoftu Web-Based Enterprise Management (WBEM) standard. Další informace o sadě SDK rozhraní WMI najdete v tématu [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page). WBEM je oborový standard pro aplikace jak vystavit WMI pro externí nástroje pro správu.  
  
 Zprostředkovatel rozhraní WMI je komponenta, která zveřejňuje instrumentace za běhu pomocí rozhraní WBEM kompatibilní. Zahrnuje sadu objektů WMI, které mají páry atribut hodnota. Páry může být několik jednoduchých typů. Nástroje pro správu můžou připojit ke službám prostřednictvím rozhraní za běhu. WCF zpřístupňuje atributy služeb, jako jsou adresy, vazby, chování a naslouchací procesy.  
  
 Předdefinovaný poskytovatel rozhraní WMI je aktivovat v konfiguračním souboru aplikace. To se provádí prostřednictvím `wmiProviderEnabled` atribut [ \<diagnostiky >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) v [ \<system.serviceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) části, jak je znázorněno v následující ukázce konfigurace.  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 Tato položka konfigurace vystavuje rozhraní WMI. Správa aplikací teď můžete připojit přes toto rozhraní a přístup WMI aplikace.  
  
## <a name="accessing-wmi-data"></a>Přístup k datům služby WMI  
 Data rozhraní WMI je možný v mnoha různými způsoby. Společnost Microsoft poskytuje rozhraní API služby WMI pro skripty, Visual Basic aplikací, aplikací v jazyce C++ a [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]. Další informace najdete v tématu [pomocí rozhraní WMI](https://go.microsoft.com/fwlink/?LinkId=95183).  
  
> [!CAUTION]
>  Pokud používáte rozhraní .NET Framework poskytuje metody k programovému přístupu ke službě data rozhraní WMI, byste měli vědět, že tyto metody může vyvolat výjimky, když se připojení. Během procesu vytváření nebude navázáno připojení <xref:System.Management.ManagementObject> instance, ale na první žádost o zahrnující skutečná data systému exchange. Proto byste měli použít `try..catch` blok catch výjimky.  
  
 Můžete změnit trasování a úroveň protokolování zprávy, stejně jako možnosti protokolování zpráv `System.ServiceModel` zdroj trasování v rozhraní WMI. To můžete udělat přechodem k [AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) instanci, která poskytuje tyto logické vlastnosti: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, a `TraceLevel`. Proto pokud nakonfigurovat naslouchací proces trasování pro protokolování zpráv, ale nastavit tyto možnosti na `false` v konfiguraci, můžete později změnit jejich `true` při spouštění aplikace. To vám umožní efektivní protokolování zpráv za běhu. Podobně pokud povolíte protokolování. v konfiguračním souboru, můžete ho zakázat za běhu pomocí rozhraní WMI.  
  
 Je třeba si uvědomit, že pokud žádné protokolování zpráv trasování naslouchacích procesů pro protokolování zpráv nebo Ne `System.ServiceModel` naslouchacích procesů trasování pro trasování jsou uvedeny v konfiguračním souboru, žádná z vašich změn provedených platit, i když jsou změny přijaty rozhraní WMI. Další informace o správné nastavení příslušných naslouchacích procesů, naleznete v tématu [konfigurace protokolování zpráv](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) a [Konfigurace trasování](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md). Úroveň trasování pro všechny ostatní zdroje trace zadáno v konfiguraci je účinné, když se aplikace spustí a nedá se změnit.  
  
 Zpřístupňuje WCF `GetOperationCounterInstanceName` metodu pro skriptování. Tato metoda vrátí název instance čítače výkonu, pokud zadáte s názvem operace. Neověřuje však váš vstup. Proto pokud zadáte název nesprávná operace, je vrácen název nesprávné čítače.  
  
 `OutgoingChannel` Vlastnost `Service` instance nepočítá otevírány služby pro připojení k jiné službě, v případě klienta WFG pro cílové služby není v rámci kanálů `Service` metoda.  
  
 **Upozornění:** WMI podporuje pouze <xref:System.TimeSpan> hodnotu až 3 desetinné čárky. Například, pokud vaše služba nastavuje jednu z vlastností <xref:System.TimeSpan.MaxValue>, její hodnota je zkrácen po 3 desetinné čárky při prohlížení prostřednictvím rozhraní WMI.  
  
## <a name="security"></a>Zabezpečení  
 Protože zprostředkovatel rozhraní WMI WCF umožňuje zjišťování služeb v prostředí, by měly využít extrémně opatrní pro udělení přístupu k němu. Pokud jste zmírnit výchozí přístup jen pro správce, může povolit méně důvěryhodnému strany přístup k citlivým datům ve vašem prostředí. Pokud jste povolte oprávnění pro vzdálený přístup pomocí rozhraní WMI, konkrétně zahlcení útoky může dojít k. Pokud proces je budete zaplaveni nadměrné požadavky rozhraní WMI, může snížit výkon.  
  
 Kromě toho pokud můžete uvolnit oprávnění k přístupu k souboru MOF, méně důvěryhodnému strany lze manipulovat s chování služby WMI a měnit objekty, které jsou načteny ve schématu WMI. Například pole lze odebrat tak, aby je důležitá data skryty od správce nebo pole, která naplnit nebo způsobit výjimky jsou přidány do souboru.  
  
 Ve výchozím nastavení, zprostředkovatel rozhraní WMI WCF uděluje "metodu execute", "zapisovat zprostředkovatele" a "Povolit účet" oprávnění pro správce a oprávnění "Povolit účet" pro technologii ASP.NET, Local Service a Network Service. Konkrétně se na jinou hodnotu než[!INCLUDE[wv](../../../../../includes/wv-md.md)] platformy, účtu technologie ASP.NET má přístup pro čtení k oboru názvů WMI ServiceModel. Pokud nechcete udělení těchto oprávnění určitou skupinu uživatelů, si deaktivace zprostředkovatele rozhraní WMI (je zakázané ve výchozím nastavení), nebo zakázat přístup pro konkrétního uživatele skupiny.  
  
 Navíc je při pokusu o povolení rozhraní WMI prostřednictvím konfigurace nemusí být povoleny služby WMI z důvodu nedostatečných uživatelských oprávnění. Žádné události je však zapsané do protokolu událostí pro záznam této chyby.  
  
 Chcete-li změnit úrovně oprávnění uživatele, postupujte následovně.  
  
1.  Klikněte na tlačítko Start a pak spusťte a zadejte **compmgmt.msc**.  
  
2.  Klikněte pravým tlačítkem na **služeb a ovládací prvky aplikace/služby WMI** vyberte **vlastnosti**.  
  
3.  Vyberte **zabezpečení** kartu a přejděte **kořenový/ServiceModel** oboru názvů. Klikněte na tlačítko **zabezpečení** tlačítko.  
  
4.  Vyberte konkrétní skupinu nebo uživatele, kterou chcete řízení přístupu a použití **povolit** nebo **Odepřít** zaškrtávací políčko ke konfiguraci oprávnění.  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a>Udělení oprávnění registrace služby WMI WCF dalším uživatelům  
 WCF zpřístupňuje data správy ke službě WMI. Dělá to tak, že hostitelem poskytovatele služby WMI v procesu, někdy označuje jako "oddělený zprostředkovatel". Pro správu data zpřístupní účet, který registruje tohoto zprostředkovatele musí mít příslušná oprávnění. Ve Windows lze zaregistrovat pouze malou sadu privilegované účty oddělení zprostředkovatelé ve výchozím nastavení. To je problém, protože uživatelé běžně chcete je zveřejnit dat služby WMI ze služby WCF spuštěný pod účtem, který není v výchozí nastavení.  
  
 Pokud chcete poskytnout tento přístup, musí správce, udělte oprávnění na další účet v následujícím pořadí:  
  
1.  Oprávnění pro přístup k rozhraní WMI Namespace WCF.  
  
2.  Oprávnění k registraci zprostředkovatele rozhraní WMI odděleném WCF.  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a>Udělení oprávnění k oboru názvů rozhraní WMI  
  
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
  
     Tento skript Powershellu používá zabezpečení SDDL Descriptor Definition Language () k udělení přístupu integrované uživatelé skupiny k oboru názvů WMI "kořenový/servicemodel". Určuje následující seznamy ACL:  
  
    -   Předdefinovaný účet Administrator (BA) - už měli přístup.  
  
    -   Síťová služba (NS) - už měli přístup.  
  
    -   Místní systém (LS) - už měli přístup.  
  
    -   Integrované uživatelé – skupinu, kterou chcete udělit přístup k.  
  
#### <a name="to-grant-provider-registration-access"></a>Poskytovatel udělit přístup k registraci  
  
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
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a>Udělení přístupu k libovolného uživatele nebo skupiny  
 Příklad v této části uděluje oprávnění registrace zprostředkovatele rozhraní WMI pro všechny místní uživatele. Pokud chcete udělit přístup pro uživatele nebo skupiny, které není vestavěný, pak musíte získat tohoto uživatele nebo skupiny identifikátor zabezpečení (SID). Neexistuje žádné jednoduchý způsob, jak získat identifikátor SID pro libovolného uživatele. Jedním ze způsobů je přihlášení jako požadovaného uživatele a potom vydejte následující příkaz prostředí.  
  
```  
Whoami /user  
```  
  
 To poskytuje SID aktuálního uživatele, ale tuto metodu nelze použít k načtení SID pro jakékoli libovolného uživatele. Získat identifikátor SID jinou metodou je použít [getsid.exe](https://go.microsoft.com/fwlink/?LinkId=186467) nástroj z [Windows 2000 Resource Kit Tools pro úlohy správy](https://go.microsoft.com/fwlink/?LinkId=178660). Tento nástroj porovná SID dva uživatele (místní nebo doménový) a jako souběžného efekt vytiskne dvě čísla SID do příkazového řádku. Další informace najdete v tématu [dobře známé identifikátory SID](https://go.microsoft.com/fwlink/?LinkId=186468).  
  
## <a name="accessing-remote-wmi-object-instances"></a>Přistupující objekt instance vzdáleného rozhraní WMI  
 Pokud potřebujete pro přístup k instancím WCF služby WMI na vzdáleném počítači, je nutné povolit paket o ochraně osobních údajů v nabídce Nástroje, které používáte pro přístup. Následující část popisuje, jak tyto dosáhnout pomocí nástroje CIM Studio WMI, nástroj testování služby WMI Windows, stejně jako .NET SDK 2.0.  
  
### <a name="wmi-cim-studio"></a>Rozhraní WMI CIM Studio  
 Pokud jste nainstalovali [nástroje pro správu služby WMI](https://go.microsoft.com/fwlink/?LinkId=95185), můžete použít nástroje CIM Studio WMI do instancí služby WMI přístup. Nástroje jsou v následující složce  
  
 **%WINDIR%\Program Files\WMI nástroje\\**  
  
1.  V **připojit k oboru názvů:** okno, zadejte **root\ServiceModel** a klikněte na tlačítko **OK.**  
  
2.  V **WMI CIM Studio přihlášení** okna, klikněte na tlačítko **možnosti >>** tlačítko pro rozbalení v okně. Vyberte **paket o ochraně osobních údajů** pro **úroveň ověřování**a klikněte na tlačítko **OK**.  
  
### <a name="windows-management-instrumentation-tester"></a>Testování služby Windows Management Instrumentation  
 Tento nástroj je nainstalován ve Windows. K jeho spuštění spuštění nástroje command console tak, že zadáte **cmd.exe** v **spuštění nebo spuštění** dialogové okno a klikněte na tlačítko **OK**. Potom zadejte **wbemtest.exe** v příkazovém okně. Pak je spustit nástroj testování služby Windows Management Instrumentation.  
  
1.  Klikněte na tlačítko **připojit** tlačítko v pravém horním rohu okna.  
  
2.  V novém okně zadejte **root\ServiceModel** pro **Namespace** pole a vyberte **paket o ochraně osobních údajů** pro **úroveň ověřování**. Klikněte na tlačítko **připojit**.  
  
### <a name="using-managed-code"></a>Pomocí spravovaného kódu  
 Dostanete také vzdálené instance rozhraní WMI prostřednictvím kódu programu pomocí tříd poskytovaných oborem <xref:System.Management> oboru názvů. Následující příklad kódu ukazuje, jak to provést.  
  
```  
String wcfNamespace = String.Format(@"\\{0}\Root\ServiceModel",      
   this.serviceMachineName);  
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
