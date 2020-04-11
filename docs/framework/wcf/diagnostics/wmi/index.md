---
title: Diagnostika prostřednictvím rozhraní WMI (Windows Management Instrumentation)
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: b14f9401266bdf7edccd7dca12cb818cdd2cb348
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121551"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a>Diagnostika prostřednictvím rozhraní WMI (Windows Management Instrumentation)
Windows Communication Foundation (WCF) zveřejňuje kontrolní data služby za běhu prostřednictvím wcf windows management instrumentace (WMI) zprostředkovatele.  
  
## <a name="enabling-wmi"></a>Povolení technologie WMI  
 Služba WMI je implementací standardu WBEM (Web-Based Enterprise Management) společností Microsoft. Další informace o sdk sady WMI naleznete v [tématu WMI Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page). WBEM je oborový standard pro to, jak aplikace zveřejňují nástroje pro správu externím nástrojům pro správu.  
  
 Zprostředkovatel služby WMI je součást, která zpřístupňuje instrumentaci za běhu prostřednictvím rozhraní kompatibilního s rozhraním wbem. Skládá se ze sady objektů služby WMI, které mají dvojice atributů a hodnot. Dvojice mohou být několika jednoduchých typů. Nástroje pro správu se mohou připojit ke službám prostřednictvím rozhraní za běhu. WCF zveřejňuje atributy služeb, jako jsou adresy, vazby, chování a naslouchací procesy.  
  
 Vestavěného zprostředkovatele služby WMI lze aktivovat v konfiguračním souboru aplikace. To se provádí `wmiProviderEnabled` prostřednictvím atributu [ \<diagnostics>](../../../configure-apps/file-schema/wcf/diagnostics.md) v části [ \<system.serviceModel>,](../../../configure-apps/file-schema/wcf/system-servicemodel.md) jak je znázorněno na následující ukázce konfigurace.  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 Tato položka konfigurace zpřístupňuje rozhraní služby WMI. Aplikace pro správu se nyní mohou připojit prostřednictvím tohoto rozhraní a získat přístup k nástroji pro správu aplikace.  
  
## <a name="accessing-wmi-data"></a>Přístup k datům wmi  
 K datům wmi lze přistupovat mnoha různými způsoby. Společnost Microsoft poskytuje rozhraní WMI rozhraní API pro skripty, aplikace jazyka Visual Basic, aplikace jazyka C++ a rozhraní .NET Framework. Další informace naleznete [v tématu Using WMI](/windows/win32/wmisdk/using-wmi).  
  
> [!CAUTION]
> Pokud používáte metody .NET Framework k programovému přístupu k datům rozhraní WMI, měli byste si být vědomi toho, že tyto metody mohou při navázání připojení vyvolat výjimky. Připojení není navázáno během <xref:System.Management.ManagementObject> výstavby instance, ale na první žádost zahrnující skutečnou výměnu dat. Proto byste měli `try..catch` použít blok zachytit možné výjimky.  
  
 Můžete změnit úroveň trasování a protokolování zpráv, stejně jako možnosti protokolování zpráv pro zdroj `System.ServiceModel` trasování ve službě WMI. To lze provést přístupem k instanci [AppDomainInfo,](appdomaininfo.md) která `LogMessagesAtServiceLevel`zpřístupňuje tyto logické vlastnosti: , `LogMessagesAtTransportLevel`, `LogMalformedMessages`a `TraceLevel`. Proto pokud nakonfigurujete naslouchací proces trasování pro protokolování zpráv, ale nastavte tyto možnosti v `false` konfiguraci, můžete je později změnit na `true` při spuštění aplikace. To efektivně umožní protokolování zpráv za běhu. Podobně pokud povolíte protokolování zpráv v konfiguračním souboru, můžete jej zakázat za běhu pomocí služby WMI.  
  
 Měli byste si být vědomi toho, že pokud žádné `System.ServiceModel` posluchače trasování protokolování zpráv pro protokolování zpráv nebo žádné posluchače trasování pro trasování jsou zadány v konfiguračním souboru, žádné změny jsou uvedeny v platnosti, i když změny jsou přijaty službou WMI. Další informace o správném nastavení příslušných naslouchacích procesů naleznete v [tématu Konfigurace protokolování zpráv](../configuring-message-logging.md) a [konfigurace trasování](../tracing/configuring-tracing.md)zpráv . Úroveň trasování všech ostatních zdrojů trasování určené konfigurace je účinná při spuštění aplikace a nelze ji změnit.  
  
 WCF zpřístupňuje metodu `GetOperationCounterInstanceName` pro skriptování. Tato metoda vrátí název instance čítače výkonu, pokud jí poskytnete název operace. Však neověřuje vstup. Proto pokud zadáte nesprávný název operace, je vrácen nesprávný název čítače.  
  
 Vlastnost `OutgoingChannel` `Service` instance nepočítá kanály otevřené službou pro připojení k jiné službě, pokud klient WCF `Service` k cílové službě není vytvořen v rámci metody.  
  
 **Pozor** Službu WMI <xref:System.TimeSpan> podporuje pouze hodnotu až 3 desetinné čárky. Pokud například služba nastaví jednu <xref:System.TimeSpan.MaxValue>ze svých vlastností na , bude její hodnota zkrácena po 3 desetinných bodech při zobrazení prostřednictvím služby WMI.  
  
## <a name="security"></a>Zabezpečení  
 Vzhledem k tomu, že zprostředkovatel WMI WCF umožňuje zjišťování služeb v prostředí, měli byste být velmi opatrní při udělování přístupu k němu. Pokud uvolníte výchozí přístup pouze pro správce, můžete méně důvěryhodným stranám povolit přístup k citlivým datům ve vašem prostředí. Konkrétně pokud uvolníte oprávnění pro vzdálený přístup služby WMI, může dojít k zaplavujícím útokům. Pokud je proces zaplaven nadměrnými požadavky služby WMI, může být jeho výkon snížen.  
  
 Pokud navíc uvolníte přístupová oprávnění pro soubor MOF, méně důvěryhodné strany mohou manipulovat s chováním systému WMI a měnit objekty načtené do schématu systému WMI. Pole lze například odebrat tak, aby byla před správcem skryta kritická data nebo aby byla do souboru přidána pole, která nenaplňují nebo nezpůsobují výjimky.  
  
 Ve výchozím nastavení uděluje zprostředkovatel wmi wmi oprávnění "metoda spuštění", "zápis zprostředkovatele" a oprávnění "povolit účet" pro správce a oprávnění "povolit účet" pro ASP.NET, místní služby a síťové služby. Zejména na platformách, které nejsou platformami systému Windows Vista, má účet ASP.NET přístup pro čtení do oboru názvů WMI ServiceModel. Pokud nechcete udělit tato oprávnění určité skupině uživatelů, měli byste buď deaktivovat zprostředkovatele služby WMI (ve výchozím nastavení je zakázáno), nebo zakázat přístup pro konkrétní skupinu uživatelů.  
  
 Pokud se navíc pokusíte povolit službu WMI prostřednictvím konfigurace, služba WMI nemusí být povolena z důvodu nedostatečných uživatelských oprávnění. Do protokolu událostí však není zapsána žádná událost, která by tuto chybu zaznamenala.  
  
 Chcete-li upravit úrovně uživatelských oprávnění, použijte následující kroky.  
  
1. Klepněte na tlačítko Start a potom na příkaz Spustit a zadejte **příkaz compmgmt.msc**.  
  
2. Klepnutím pravým tlačítkem myši na **položku Služby a ovládací prvky aplikace/služby WMI** vyberte příkaz **Vlastnosti**.  
  
3. Vyberte kartu **Zabezpečení** a přejděte do oboru názvů **Root/ServiceModel.** Klepněte na tlačítko **Zabezpečení.**  
  
4. Vyberte konkrétní skupinu nebo uživatele, u kterého chcete řídit přístup, a pomocí zaškrtávacího políčka **Povolit** nebo **Odepřít** nakonfigurujte oprávnění.  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a>Udělení oprávnění k registraci wmi wmi dalším uživatelům  
 WCF zpřístupňuje data správy do wmi. Činí tak hostováním v procesu zprostředkovatele služby WMI, někdy nazývaného "oddělený zprostředkovatel". Aby byla data správy vystavena, musí mít účet, který registruje tohoto zprostředkovatele, příslušná oprávnění. V systému Windows může ve výchozím nastavení zaregistrovat oddělené zprostředkovatele pouze malá sada privilegovaných účtů. Jedná se o problém, protože uživatelé obvykle chtějí vystavit data služby WMI ze služby WCF spuštěné pod účtem, který není ve výchozí sadě.  
  
 Chcete-li tento přístup poskytnout, musí správce udělit další účet následující oprávnění v následujícím pořadí:  
  
1. Oprávnění k přístupu k oboru názvů WCF WMI.  
  
2. Oprávnění k registraci zprostředkovatele wcf odděleného zprostředkovatele služby WMI.  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a>Udělení oprávnění k přístupu k oboru názvů wmi  
  
1. Spusťte následující skript prostředí PowerShell.  
  
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
  
     Tento skript prostředí PowerShell používá jazyk definice popisovače zabezpečení (SDDL) k udělení přístupu skupiny Předdefinovaných uživatelů k oboru názvů WMI "root/servicemodel". Určuje následující seznamy ACL:  
  
    - Vestavěný správce (BA) - již měl přístup.  
  
    - Síťová služba (NS) - již měla přístup.  
  
    - Místní systém (LS) - již měl přístup.  
  
    - Předdefinované uživatelé – skupina, ke které má být přístup.  
  
#### <a name="to-grant-provider-registration-access"></a>Udělení přístupu k registraci zprostředkovatele  
  
1. Spusťte následující skript prostředí PowerShell.  
  
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
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a>Udělení přístupu libovolným uživatelům nebo skupinám  
 Příklad v této části uděluje oprávnění k registraci zprostředkovatele služby WMI všem místním uživatelům. Pokud chcete udělit přístup k uživateli nebo skupině, která není integrovaná, musíte získat identifikátor zabezpečení tohoto uživatele nebo skupiny (SID). Neexistuje žádný jednoduchý způsob, jak získat SID pro libovolného uživatele. Jednou z metod je přihlásit se jako požadovaný uživatel a potom vydat následující příkaz prostředí.  
  
```console
Whoami /user  
```  
  
 To poskytuje SID aktuálního uživatele, ale tuto metodu nelze použít k získání SID na libovolný uživatel. Další metodou získání sid je použití nástroje [getsid.exe](/windows/win32/wmisdk/using-wmi) z nástrojů sady Windows 2000 Resource Kit pro úkoly správy. Tento nástroj porovnává SID dvou uživatelů (místní nebo domény) a jako vedlejší efekt vytiskne dva SID s příkazovým řádkem. Další informace naleznete v [tématu Známé SID](https://support.microsoft.com/help/243330/well-known-security-identifiers-in-windows-operating-systems).  
  
## <a name="accessing-remote-wmi-object-instances"></a>Přístup ke vzdáleným instancím objektů služby WMI  
 Pokud potřebujete přístup k instancíw WMI WCF ve vzdáleném počítači, musíte povolit ochranu osobních údajů paketů v nástrojích, které používáte pro přístup. Následující část popisuje, jak jich dosáhnout pomocí wmi CIM Studio, Windows Management Instrumentation Tester a .NET SDK 2.0.  
  
### <a name="wmi-cim-studio"></a>WMI CIM Studio

Pokud jste nainstalovali nástroje pro správu služby WMI, můžete k instancím služby WMI použít aplikaci WMI CIM Studio. Nástroje jsou v následující složce:
  
*%windir%\Program Files\Nástroje WMI\\*
  
1. V okně **Připojit k oboru názvů:** zadejte **root\ServiceModel** a klepněte na **tlačítko OK.**  
  
2. V okně **Přihlášení aplikace WMI CIM Studio** rozbalte okno klepnutím na tlačítko **Možnosti >>.** Vyberte **úroveň ochrany osobních údajů paketů** pro **ověřování**a klepněte na tlačítko **OK**.  
  
### <a name="windows-management-instrumentation-tester"></a>Tester pro správu systému Windows  
 Tento nástroj je nainstalován systémem Windows. Chcete-li ji spustit, spusťte konzolu příkazů zadáním příkazu **cmd.exe** v dialogovém okně **Start/Spustit** a klepněte na tlačítko **OK**. Potom zadejte **wbemtest.exe** v příkazovém okně. Poté je spuštěn nástroj Windows Management Instrumentation Tester.  
  
1. Klikněte na tlačítko **Připojit** v pravém horním rohu okna.  
  
2. V novém okně zadejte **root\ServiceModel** pro pole **Obor názvů** a vyberte úroveň **ochrany osobních údajů paketů** pro **ověřování**. Klikněte na **Připojit**.  
  
### <a name="using-managed-code"></a>Použití spravovaného kódu  
 Ke vzdáleným instancím služby WMI můžete také <xref:System.Management> přistupovat programově pomocí tříd poskytovaných oborem názvů. Následující ukázka kódu ukazuje, jak to provést.  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
