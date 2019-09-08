---
title: Diagnostika prostřednictvím rozhraní WMI (Windows Management Instrumentation)
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: 90aae0e22feec5d26fa7ee4c690904ed893489b4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795912"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a>Diagnostika prostřednictvím rozhraní WMI (Windows Management Instrumentation)
Windows Communication Foundation (WCF) zveřejňuje kontrolní data služby za běhu prostřednictvím poskytovatele WCF rozhraní WMI (Windows Management Instrumentation) (WMI).  
  
## <a name="enabling-wmi"></a>Povolení služby WMI  
 WMI je implementace standardu WBEM (Web-Based Enterprise Management) od Microsoftu. Další informace o sadě WMI SDK naleznete v tématu [rozhraní WMI (Windows Management Instrumentation)](/windows/desktop/WmiSdk/wmi-start-page). WBEM je oborovým standardem, jak aplikace vystavují instrumentaci pro správu externích nástrojů pro správu.  
  
 Zprostředkovatel rozhraní WMI je komponenta, která zveřejňuje instrumentaci za běhu prostřednictvím rozhraní kompatibilního se standardem WBEM. Skládá se ze sady objektů WMI, které mají páry atribut/hodnota. Páry můžou být v mnoha jednoduchých typech. Nástroje pro správu se můžou ke službám připojit prostřednictvím rozhraní za běhu. WCF zpřístupňuje atributy služeb, jako jsou adresy, vazby, chování a naslouchací procesy.  
  
 Integrovaného zprostředkovatele WMI lze aktivovat v konfiguračním souboru aplikace. To se provádí pomocí `wmiProviderEnabled` atributu [ \<> diagnostiky](../../../configure-apps/file-schema/wcf/diagnostics.md) v [ \<části System. ServiceModel >](../../../configure-apps/file-schema/wcf/system-servicemodel.md) , jak je znázorněno v následující ukázkové konfiguraci.  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 Tato položka konfigurace zpřístupňuje rozhraní WMI. Aplikace pro správu se teď můžou přes toto rozhraní připojit a přistupovat k instrumentaci správy aplikace.  
  
## <a name="accessing-wmi-data"></a>Přístup k datům WMI  
 K datům WMI lze přistupovat mnoha různými způsoby. Microsoft poskytuje rozhraní API služby WMI pro skripty, Visual Basic C++ aplikace, aplikace a .NET Framework. Další informace najdete v tématu [použití rozhraní WMI](https://go.microsoft.com/fwlink/?LinkId=95183).  
  
> [!CAUTION]
> Pokud používáte metody poskytnuté .NET Framework pro programový přístup k datům WMI, měli byste si uvědomit, že tyto metody mohou vyvolat výjimky při navázání spojení. Připojení není během vytváření <xref:System.Management.ManagementObject> instance navázáno, ale na první požadavek týkající se skutečného výměny dat. Proto byste měli použít `try..catch` blok k zachycení možných výjimek.  
  
 V rozhraní WMI můžete změnit úroveň trasování a protokolování zpráv a také možnosti protokolování zpráv pro `System.ServiceModel` zdroj trasování. To lze provést přístupem k instanci [AppDomainInfo](appdomaininfo.md) , která zpřístupňuje tyto logické vlastnosti: `LogMessagesAtServiceLevel` `TraceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`a. Proto pokud nakonfigurujete naslouchací proces trasování pro protokolování zpráv, ale tyto možnosti nastavíte `false` na v konfiguraci, můžete je později změnit na `true` , pokud je aplikace spuštěná. Tím se efektivně povolí protokolování zpráv za běhu. Podobně platí, že pokud povolíte protokolování zpráv v konfiguračním souboru, můžete ho za běhu zakázat pomocí rozhraní WMI.  
  
 Měli byste si uvědomit, že pokud pro protokolování zpráv nejsou k dispozici naslouchací procesy trasování `System.ServiceModel` zpráv, nebo pokud nejsou v konfiguračním souboru žádné naslouchací procesy trasování pro trasování, neprojeví se žádné změny, a to ani v případě, že se změny nepřijímají rozhraním WMI. Další informace o správném nastavení příslušného naslouchacího procesu najdete v tématu [Konfigurace protokolování zpráv](../configuring-message-logging.md) a [Konfigurace trasování](../tracing/configuring-tracing.md). Úroveň trasování všech ostatních zdrojů trasování určených konfigurací je platná při spuštění aplikace a nelze ji změnit.  
  
 WCF zpřístupňuje `GetOperationCounterInstanceName` metodu pro skriptování. Tato metoda vrací název instance čítače výkonu, pokud jej zadáte s názvem operace. Neověřuje ale vaše zadání. Proto pokud zadáte nesprávný název operace, vrátí se nesprávný název čítače.  
  
 Vlastnost instance nepočítá kanály, které služba otevřela, aby se mohla připojit k jiné službě, pokud není v rámci `Service` metody vytvořen klient služby WCF pro cílovou službu. `Service` `OutgoingChannel`  
  
 **Upozornění** WMI podporuje <xref:System.TimeSpan> pouze hodnotu až 3 desetinná místa. Například pokud vaše služba nastavuje jednu z jejích vlastností na <xref:System.TimeSpan.MaxValue>, její hodnota se zkrátí po 3 desítkových bodech při zobrazení prostřednictvím rozhraní WMI.  
  
## <a name="security"></a>Zabezpečení  
 Vzhledem k tomu, že zprostředkovatel rozhraní WMI služby WCF umožňuje zjišťování služeb v prostředí, měli byste pro udělení přístupu využít mimořádně opatrní. Pokud nebudete mít přístup k citlivým datům ve vašem prostředí jen výchozím správcem, můžete jim udělit méně důvěryhodné strany. Konkrétně, pokud k přístupu ke vzdálenému přístupu přes rozhraní WMI přistupujete, může dojít k útokům při zahlcení. Pokud je proces zahlcen nadměrnými požadavky rozhraní WMI, může jeho výkon zhoršit.  
  
 Kromě toho platí, že pokud pro soubor MOF dojde k nedostatku oprávnění, nedůvěryhodné strany budou moci manipulovat s chováním služby WMI a měnit objekty, které jsou načteny ve schématu WMI. Například je možné odebrat pole tak, aby důležitá data byla skryta od správce nebo aby se do souboru přidala pole, která neplní nebo nezpůsobí výjimky.  
  
 Ve výchozím nastavení udělí zprostředkovatel WMI WCF oprávnění "spouštět metodu", "Provider Write" a "Enable Account" pro správce a oprávnění "Povolit účet" pro ASP.NET, místní službu a síťovou službu. Konkrétně na jiných[!INCLUDE[wv](../../../../../includes/wv-md.md)] platformách než na platformách má účet ASP.NET oprávnění ke čtení pro obor názvů rozhraní WMI ServiceModel. Pokud nechcete tato oprávnění udělit konkrétní skupině uživatelů, měli byste buď deaktivovat poskytovatele rozhraní WMI (ve výchozím nastavení je zakázaný), nebo zakázat přístup pro konkrétní skupinu uživatelů.  
  
 Kromě toho, pokud se pokusíte povolit rozhraní WMI prostřednictvím konfigurace, rozhraní WMI nemusí být povoleno z důvodu nedostatečného oprávnění uživatele. Nicméně žádná událost není zapsána do protokolu událostí, aby mohla zaznamenat tuto chybu.  
  
 Chcete-li upravit úrovně oprávnění uživatele, použijte následující postup.  
  
1. Klikněte na Start, pak na spustit a zadejte **compmgmt. msc**.  
  
2. Klikněte pravým tlačítkem na **služby a ovládací prvky Application/WMI** a vyberte **vlastnosti**.  
  
3. Vyberte kartu **zabezpečení** a přejděte do oboru názvů **root/ServiceModel** . Klikněte na tlačítko **zabezpečení** .  
  
4. Vyberte konkrétní skupinu nebo uživatele, kterým chcete řídit přístup, a pro konfiguraci oprávnění použijte zaškrtávací políčko **Povolit** nebo **Odepřít** .  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a>Udělení oprávnění k registraci rozhraní WMI WCF dalším uživatelům  
 WCF zpřístupňuje data správy rozhraní WMI. Je tak hostitelem zprostředkovatele rozhraní WMI v procesu, někdy označovaného jako "oddělený poskytovatel". Aby bylo možné zveřejnit data správy, musí mít účet, který registruje tohoto poskytovatele, příslušná oprávnění. V systému Windows je ve výchozím nastavení možné zaregistrovat oddělené zprostředkovatele jenom v malých sestavách privilegovaných účtů. Tato chyba je způsobena tím, že uživatelé obvykle chtějí vystavit data služby WMI ze služby WCF spuštěné v rámci účtu, který není ve výchozí sadě.  
  
 K poskytnutí tohoto přístupu musí správce udělit dodatečnému účtu následující oprávnění v následujícím pořadí:  
  
1. Oprávnění pro přístup k oboru názvů WMI služby WCF.  
  
2. Oprávnění k registraci zprostředkovatele rozhraní WMI pro oddělené služby WCF.  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a>Udělení přístupových oprávnění k oboru názvů rozhraní WMI  
  
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
  
     Tento skript PowerShellu používá jazyk SDDL (Security Descriptor Definition Language) k udělení přístupu předdefinovaných uživatelů do oboru názvů "root/ServiceModel" rozhraní WMI. Určuje následující seznamy ACL:  
  
    - Předdefinovaný správce (BA) – již měl přístup.  
  
    - Síťová služba (NS) – již měl přístup.  
  
    - Místní systém (LS) – již měl přístup.  
  
    - Předdefinované uživatele – skupina, pro kterou má být udělen přístup.  
  
#### <a name="to-grant-provider-registration-access"></a>Udělení přístupu k registraci poskytovatele  
  
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
 Příklad v této části uděluje oprávnění k registraci zprostředkovatele rozhraní WMI všem místním uživatelům. Pokud chcete udělit přístup uživateli nebo skupině, která není integrovaná v, musíte získat identifikátor zabezpečení (SID) daného uživatele nebo skupiny. Neexistuje žádný jednoduchý způsob, jak získat SID pro libovolného uživatele. Jedna z metod se přihlaste jako požadovaný uživatel a pak vydejte následující příkaz prostředí.  
  
```  
Whoami /user  
```  
  
 Tato metoda poskytuje identifikátor SID aktuálního uživatele, ale tuto metodu nelze použít k získání čísla SID pro libovolného uživatele. Další metodou získání identifikátoru SID je použití nástroje [getsid. exe](https://go.microsoft.com/fwlink/?LinkId=186467) z [nástrojů sady Windows 2000 Resource Kit pro úlohy správy](https://go.microsoft.com/fwlink/?LinkId=178660). Tento nástroj porovná identifikátor SID dvou uživatelů (místní nebo doména) a jako vedlejší efekt budou tyto dva identifikátory SID vytištěny na příkazovém řádku. Další informace najdete v tématu [dobře známé identifikátory SID](https://go.microsoft.com/fwlink/?LinkId=186468).  
  
## <a name="accessing-remote-wmi-object-instances"></a>Přístup k instancím vzdálených objektů služby WMI  
 Pokud potřebujete přístup k instancím WCF WMI na vzdáleném počítači, musíte povolit ochranu osobních údajů paketů u nástrojů, které používáte pro přístup. Následující část popisuje, jak dosáhnout těchto možností pomocí rozhraní WMI CIM Studio, rozhraní WMI (Windows Management Instrumentation) testeru a sady .NET SDK 2,0.  
  
### <a name="wmi-cim-studio"></a>WMI CIM Studio  
 Pokud jste nainstalovali [Nástroje pro správu služby WMI](https://go.microsoft.com/fwlink/?LinkId=95185), můžete k přístupu k INSTANCÍM rozhraní WMI použít rozhraní WMI CIM. Nástroje jsou v následující složce  
  
 **%windir%\Program Files\WMI Tools\\**  
  
1. V okně **připojit k oboru názvů:** zadejte **root\ServiceModel** a klikněte na **OK.**  
  
2. V okně **přihlášení WMI CIM Studio** kliknutím na tlačítko **Možnosti > >** okno rozbalte. Vyberte možnost **Ochrana osobních údajů paketů** pro **úroveň ověřování**a klikněte na tlačítko **OK**.  
  
### <a name="windows-management-instrumentation-tester"></a>rozhraní WMI (Windows Management Instrumentation) Tester  
 Tento nástroj je nainstalován systémem Windows. Pokud ho chcete spustit, spusťte konzolu příkazů tak, že v dialogovém okně **Spustit/spustit** zadáte **cmd. exe** a kliknete na **OK**. Pak do příkazového okna zadejte **WBEMTest. exe** . Pak se spustí nástroj rozhraní WMI (Windows Management Instrumentation) Tester.  
  
1. Klikněte na tlačítko **připojit** v pravém horním rohu okna.  
  
2. V novém okně zadejte **root\ServiceModel** do pole **obor názvů** a vyberte **ochrana paketů** pro **úroveň ověřování**. Klikněte na **Připojit**.  
  
### <a name="using-managed-code"></a>Použití spravovaného kódu  
 Vzdálené instance služby WMI můžete získat také programově pomocí tříd poskytovaných <xref:System.Management> oborem názvů. Následující příklad kódu ukazuje, jak to provést.  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
