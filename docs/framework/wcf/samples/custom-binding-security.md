---
title: "Zabezpečení vlastních vazeb"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
caps.latest.revision: "30"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 943a56095707efdba0e20c40b2c96e24e8fd4ea3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="custom-binding-security"></a>Zabezpečení vlastních vazeb
Tento příklad ukazuje, jak nakonfigurovat zabezpečení tak, že použití vlastní vazby. Ukazuje, jak použít k povolení zabezpečení na úrovni zpráv společně s zabezpečený přenos vlastní vazby. To je užitečné, když zabezpečení přenosu je potřeba k přenosu zpráv mezi klientem a službou a současně zprávy musí být zabezpečení na úrovni zpráv. Tato konfigurace není podporována vazby poskytované systémem.  
  
 Tato ukázka se skládá z konzoly programu klienta (EXE) a program konzoly služby (EXE). Služba se implementuje duplexního kontraktu. Kontrakt je definována `ICalculatorDuplex` rozhraní, která zpřístupňuje matematické operace (přidat, odečíst, násobit a dělit). `ICalculatorDuplex` Rozhraní umožňuje klientovi provádět matematické operace, výpočet výsledku spuštěných v relaci. Nezávisle, mohou službu vracet výsledky na `ICalculatorDuplexCallback` rozhraní. Duplexní kontrakt vyžaduje relaci, protože kontextu musí být stanovena ke korelaci sadu zprávy odesílané mezi klientem a službu. Vlastní vazby je definována, která podporuje duplexní komunikace a zabezpečení.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Konfigurace služby definuje vlastní vazby, který podporuje následující funkce:  
  
-   Komunikaci TCP chráněný pomocí protokolu TLS/SSL.  
  
-   Zabezpečení zpráv systému Windows.  
  
 Konfigurace vlastních vazeb umožňuje zabezpečený přenos současně povolením zprávy úroveň zabezpečení. Řazení elementů vazby je důležité k definování vlastní vazby, protože každý představuje vrstvy v zásobníku kanál (viz [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md)). Vlastní vazby je definována v konfiguračních souborech klienta a služby, jak je znázorněno v následující ukázka konfigurace.  
  
```xml  
<bindings>  
  <!-- Configure a custom binding. -->  
  <customBinding>  
    <binding name="Binding1">  
      <security authenticationMode="SecureConversation"  
                 requireSecurityContextCancellation="true">  
      </security>  
      <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
      <sslStreamSecurity requireClientCertificate="false"/>  
      <tcpTransport/>  
    </binding>  
  </customBinding>  
</bindings>  
```  
  
 Vlastní vazby používá certifikát služby k ověřování na úrovni přenosu a k ochraně zprávy během přenosu mezi klientem a službou. To lze provést `sslStreamSecurity` prvku vazby. Certifikát služby je nakonfigurovaný pomocí chování služby, jak je znázorněno v následující ukázka konfigurace.  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 Kromě toho používá vlastní vazby zabezpečení zpráv s typ přihlašovacích údajů Windows – jedná se o výchozí typ přihlašovacích údajů. To lze provést `security` prvku vazby. Klienta a služby se ověřují pomocí zabezpečení na úrovni zpráv, pokud se mechanismus ověřování protokolu Kerberos je k dispozici. To se stane, když ukázku běží v prostředí služby Active Directory. Pokud se mechanismus ověřování protokolu Kerberos není k dispozici, je použít ověřování NTLM. NTLM ověřuje klienta pro službu ale neověřuje služby klienta. `security` Prvku vazby je nakonfigurovaný na použití `SecureConversation``authenticationType`, což vede k vytvoření relace zabezpečení na klienta a služby. To je nutné povolit duplexního kontraktu služby pracovat.  
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
```  
Press <ENTER> to terminate client.  
Result(100)  
Result(50)  
Result(882.5)  
Result(441.25)  
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)  
```  
  
 Když spustíte ukázku, uvidíte zprávy vrácen do klienta na rozhraní zpětné volání odeslaných ze služby. Zobrazí se každý zprostředkující výsledek, za nímž následuje celý rovnice po dokončení všech operací. Stisknutím klávesy ENTER vypnout klienta.  
  
 Vložený soubor Setup.bat umožňuje nakonfigurovat certifikát příslušné služby, který chcete spustit hostované aplikace, která vyžaduje zabezpečení na základě certifikátu klienta a serveru. Tento dávkový soubor musí upravit, fungovat na všech počítačích, nebo pro práci v případě bez hostitele.  
  
 Následující poskytuje stručný přehled různých oddílů dávkové soubory, které se vztahují k této ukázce tak, aby může být změněn na spouštění v příslušné konfiguraci:  
  
-   Vytvoření certifikátu serveru.  
  
     Následující řádky ze souboru Setup.bat vytvořit certifikát serveru, který chcete použít. `%SERVER_NAME%` Proměnná Určuje název serveru. Změňte tuto proměnnou k určení vlastního názvu serveru. Tento dávkový soubor výchozí název serveru a localhost.  
  
     Certifikát je uložen v úložišti CurrentUser pro hostované webové služby.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta.  
  
     Následující řádky do kopírování souborů Setup.bat certifikát serveru do důvěryhodných osob klienta úložiště. Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta. Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vystavený Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio 2010 příkazový řádek. Se vyžaduje, aby proměnné prostředí MSSDK bodu na adresář, kam nainstalovat sadu SDK. Tato proměnná prostředí bude automaticky nastavena v rámci Visual Studio 2010 příkazový řádek.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači  
  
1.  Otevřete okno příkazového řádku Visual Studio s oprávněními správce a spusťte Setup.bat z ukázkové složky instalace. Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.  
  
    > [!NOTE]
    >  Dávkový soubor Setup.bat slouží ke spouštění z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku. Nastavit proměnné prostředí PATH v rámci [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek odkazuje na adresář, který obsahuje požadované skriptem Setup.bat spustitelné soubory.  
  
2.  Spusťte Service.exe z \service\bin.  
  
3.  Spusťte Client.exe z \client\bin. Činnost klienta se zobrazí na klientskou aplikaci konzoly.  
  
4.  Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky mezi počítači  
  
1.  Na počítači se službou:  
  
    1.  Vytvořte virtuální adresář s názvem servicemodelsamples na počítači se službou.  
  
    2.  Zkopírujte soubory programu služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači se službou. Ujistěte se, že zkopírujete soubory v podadresáři \bin.  
  
    3.  Zkopírujte soubory Setup.bat a Cleanup.bat na počítač služby.  
  
    4.  Spusťte následující příkaz v příkazovém řádku Visual Studia otevřít s oprávněními správce: `Setup.bat service`. Tím se vytvoří certifikát služby s názvem subjektu odpovídající názvu počítače, který byl spuštěn dávkového souboru.  
  
        > [!NOTE]
        >  Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio 2010 příkazový řádek. To vyžaduje, aby proměnné prostředí path přejděte na adresář, kam nainstalovat sadu SDK. Tato proměnná prostředí bude automaticky nastavena v rámci Visual Studio 2010 příkazový řádek.  
  
    5.  Změna [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) v souboru Service.exe.config tak, aby odrážela název předmětu certifikátu vygenerované v předchozím kroku.  
  
    6.  Spusťte Service.exe z příkazového řádku.  
  
2.  Na klientském počítači:  
  
    1.  Zkopírujte soubory programu klienta ze složky \client\bin\ do klientského počítače. Taky zkopírujte soubor Cleanup.bat.  
  
    2.  Spusťte Cleanup.bat odebrat všechny certifikáty, staré z předchozí ukázky.  
  
    3.  Exportujte certifikát služby tak, že otevřete příkazový řádek sady Visual Studio s oprávněními správce a spuštěním následujícího příkazu na počítači se službou (Nahraďte `%SERVER_NAME%` s plně kvalifikovaný název počítače, kde je služba spuštění):  
  
        ```  
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer  
        ```  
  
    4.  Zkopírujte %SERVER_NAME%.cer do klientského počítače (substitute název_serveru % s plně kvalifikovaný název počítače, kde je služba spuštěná).  
  
    5.  Importujte certifikát služby, že otevřete příkazový řádek sady Visual Studio s oprávněními správce a spuštěním následujícího příkazu na klientském počítači (substitute název_serveru % s plně kvalifikovaný název počítače, kde je služba spuštění):  
  
        ```  
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople  
        ```  
  
         Kroky c, d a e nejsou nutné v případě, že certifikát je vydán důvěryhodného vystavitele.  
  
    6.  Upravte soubor App.config klienta následujícím způsobem:  
  
        ```xml  
        <client>  
            <endpoint name="default"  
                address="net.tcp://ReplaceThisWithServiceMachineName:8000/ServiceModelSamples/Service"   
                binding="customBinding"   
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex"  
        behaviorConfiguration="CalculatorClientBehavior" />  
        </client>  
        ```  
  
    7.  Služba běží pod účtu, než NetworkService nebo pod účtem LocalSystem v prostředí domény, může být potřeba změnit identitu koncového bodu pro koncový bod služby v souboru App.config klienta nastavit na příslušný hlavní název uživatele nebo na základě hlavního názvu služby na účet, který se používá ke spouštění služby. Další informace o identitě koncového bodu najdete v tématu [identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) tématu.  
  
    8.  Spusťte Client.exe z příkazového řádku.  
  
### <a name="to-clean-up-after-the-sample"></a>Vyčistěte po vzorku  
  
-   Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.  
  
## <a name="see-also"></a>Viz také
