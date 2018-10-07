---
title: Zabezpečení vlastních vazeb
ms.date: 03/30/2017
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
author: BrucePerlerMS
ms.openlocfilehash: 85d069fed9fb1e82670c81003b5ef091c22a8e92
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48841576"
---
# <a name="custom-binding-security"></a>Zabezpečení vlastních vazeb
Tento příklad ukazuje, jak nakonfigurovat zabezpečení a použití vlastní vazby. Ukazuje, jak povolit zabezpečení na úrovni zprávy spolu s zabezpečeného přenosu pomocí vlastní vazby. To je užitečné, když zabezpečeného přenosu je potřebná pro přenos zpráv mezi klientem a službou a současně zprávy musí být zabezpečení na úrovni zprávy. Tato konfigurace není podporována vazeb poskytovaných systémem.

 Tento příklad se skládá z programu konzoly klienta (EXE) a služby konzolový program (EXE). Služba implementuje duplexního kontraktu. Smlouva je definován `ICalculatorDuplex` rozhraní, které zveřejňuje matematických operací (Přidat odečíst, násobení a dělení). `ICalculatorDuplex` Rozhraní umožňuje klientovi k provádění matematických operací spuštěných výsledek výpočtu přes relaci. Nezávisle na sobě, mohou vracet výsledky na službu `ICalculatorDuplexCallback` rozhraní. Duplexní kontrakt vyžaduje relaci, protože kontextu musí být stanovena ke korelaci sadu zprávy odesílané mezi klientem a službou. Vlastní vazby je definován, který podporuje duplexní komunikaci a je bezpečné.

> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.

 Konfigurace služby definuje vlastní vazby, který podporuje následující funkce:

-   Komunikace protokolu TCP chráněny pomocí protokolu TLS/SSL.

-   Zabezpečení zpráv Windows.

 Konfigurace vlastních vazeb umožňuje zabezpečeného přenosu současně povolením zprávy úroveň zabezpečení. Řazení elementů vazby je důležité při definování vlastní vazby, protože každý reprezentuje vrstvu v kanálu zásobníku (viz [vlastních vazeb](../../../../docs/framework/wcf/extending/custom-bindings.md)). Vlastní vazba je definována v konfiguračních souborů klienta a služby, jak je znázorněno v následující ukázková konfigurace.

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

 Vlastní vazba používá certifikát služby pro ověření služby na úrovni přenosu a k ochraně zprávy během přenosu mezi klientem a službou. Toho lze dosáhnout `sslStreamSecurity` element vazby. Certifikát služby je nakonfigurovaný pomocí chování služby, jak je znázorněno v následující ukázková konfigurace.

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

 Kromě toho používá vlastní vazby zabezpečení zpráv s typ přihlašovacích údajů Windows – jedná se o výchozí typ přihlašovacích údajů. Toho lze dosáhnout `security` element vazby. Klient a služba ověření pomocí zabezpečení na úrovni zprávy, když mechanismus ověřování protokolu Kerberos je k dispozici. To se stane, když spuštění ukázky v prostředí služby Active Directory. Pokud mechanismus ověřování protokolu Kerberos není k dispozici, bude použito ověřování NTLM. NTLM ověřuje klienta pro službu, ale neověří služby ke klientovi. `security` Element vazby je nakonfigurován na použití `SecureConversation``authenticationType`, což vede k vytvoření relace zabezpečení klienta a služby. To je nutné povolit duplexního kontraktu služby pro práci.

 Při spuštění ukázky operace žádosti a odpovědi jsou zobrazeny v okně konzoly klienta. Stisknutím klávesy ENTER v okně Klient vypnutí klient.

```
Press <ENTER> to terminate client.
Result(100)
Result(50)
Result(882.5)
Result(441.25)
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)
```

 Když spustíte ukázku, uvidíte zpráv vrácených do klienta na rozhraní zpětného volání odeslané ze služby. Zobrazí se každý přechodný výsledek, za nímž následuje celou rovnici. Po dokončení všech operací. Stiskněte klávesu ENTER pro vypnutí klient.

 Zahrnutý soubor Setup.bat můžete nakonfigurovat klienta a serveru s certifikátem příslušné služby ke spuštění prostředí aplikace, které vyžadují zabezpečení na základě certifikátů. Tento dávkový soubor musí být upravena fungovat na všech počítačích nebo pro práci v případě jiných hostované.

 Následující body nabízí stručný přehled o různých částech dávkové soubory, které se vztahují k této ukázce tak, aby se lze upravit a spustit v příslušné konfiguraci:

-   Vytváří se certifikát serveru.

     Následující řádky z se soubor Setup.bat vytvořte certifikát serveru, který se má použít. `%SERVER_NAME%` Proměnné Určuje název serveru. Změňte tuto proměnnou k určení vlastního názvu serveru. Tento dávkový soubor výchozí hodnota názvu serveru localhost.

     Certifikát je uložen v úložišti CurrentUser pro hostované webové služby.

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

-   Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta.

     Uložte následující řádky v kopírování souborů Setup.bat certifikát serveru do klienta důvěryhodných osob. Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému klienta. Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikát vydaný společností Microsoft – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    >  Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio 2010 příkazový řádek. To vyžaduje, aby proměnné prostředí MSSDK bodu do adresáře, ve kterém je nainstalována sada SDK. Tato proměnná prostředí je nastavena automaticky v rámci Visual Studio 2010 příkazový řádek.

### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku

1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3.  Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači

1.  Otevřete okno Příkazový řádek sady Visual Studio s oprávněními správce a spusťte Setup.bat z instalační složky s ukázkou. Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.

    > [!NOTE]
    >  Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio 2012 příkazový řádek. Proměnné prostředí PATH v nastavení v rámci body příkazový řádek sady Visual Studio 2012 k adresáři, který obsahuje požadované skript Setup.bat spustitelné soubory.  
  
2.  Spusťte Service.exe z \service\bin.  
  
3.  Spusťte Client.exe z \client\bin. Činnost klienta se zobrazí na klientské aplikace konzoly.  
  
4.  Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky v počítačích  
  
1.  Na počítači se službou:  
  
    1.  Vytvořte virtuální adresář s názvem servicemodelsamples na počítači se službou.  
  
    2.  Zkopírujte soubory programu služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači se službou. Ujistěte se, že zkopírujete soubory v podadresáři \bin.  
  
    3.  Zkopírujte soubory Setup.bat a Cleanup.bat k počítači služby.  
  
    4.  Spuštění následujícího příkazu v příkazovém řádku aplikace Visual Studio otevřeného s oprávněními správce: `Setup.bat service`. Tím se vytvoří certifikát služby s názvem subjektu odpovídající název počítače, který byl spuštěn dávkového souboru.  
  
        > [!NOTE]
        >  Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio 2010 příkazový řádek. To vyžaduje, aby proměnné prostředí path v bodu do adresáře, ve kterém je nainstalována sada SDK. Tato proměnná prostředí je nastavena automaticky v rámci Visual Studio 2010 příkazový řádek.

    5.  Změnit [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) uvnitř Service.exe.config souboru tak, aby odrážely název subjektu certifikátu vygenerovaného v předchozím kroku.

    6.  Spusťte Service.exe z příkazového řádku.

2.  Na klientském počítači:

    1.  Zkopírujte soubory programu klienta ze složky \client\bin\ do klientského počítače. Zkopírujte také soubor Cleanup.bat.

    2.  Spusťte Cleanup.bat odebrání starého certifikátů z předchozí ukázky.

    3.  Exportujte certifikát služby tak, že otevřete příkazový řádek sady Visual Studio s oprávněními správce a spuštěním následujícího příkazu na počítači se službou (Nahraďte `%SERVER_NAME%` s plně kvalifikovaný název počítače, kde je služba spuštění):

        ```
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer
        ```

    4.  Zkopírujte %SERVER_NAME%.cer ke klientskému počítači (nahraďte název_serveru % s plně kvalifikovaný název počítače, ve kterém je služba spuštěná).

    5.  Naimportujte certifikát služby tak, že otevřete příkazový řádek sady Visual Studio s oprávněními správce a spuštěním následujícího příkazu v klientském počítači (nahraďte název_serveru % s plně kvalifikovaný název počítače, kde je služba spuštění):

        ```
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople
        ```

         Kroky nejsou nutné v případě, že certifikát vystavil důvěryhodného vystavitele c, d a e.

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

    7.  Pokud služba běží v rámci účtu než NetworkService nebo LocalSystem účet v prostředí domény, je třeba upravit identitě koncového bodu pro koncový bod služby v souboru App.config klienta pro nastavení odpovídající hlavní název uživatele nebo na základě hlavního názvu služby u účtu, který se používá ke spuštění služby. Další informace o identitě koncového bodu, najdete v článku [identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) tématu.

    8.  Spusťte Client.exe z příkazového řádku.

### <a name="to-clean-up-after-the-sample"></a>K vyčištění po vzorku

-   Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.

## <a name="see-also"></a>Viz také
