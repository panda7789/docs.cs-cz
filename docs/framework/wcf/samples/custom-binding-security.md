---
title: Zabezpečení vlastních vazeb
ms.date: 03/30/2017
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
ms.openlocfilehash: 99fa1e7dea09601de5efff9ef8d8c6a66eae1bac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953778"
---
# <a name="custom-binding-security"></a>Zabezpečení vlastních vazeb
Tato ukázka demonstruje, jak nakonfigurovat zabezpečení pomocí vlastní vazby. Ukazuje, jak použít vlastní vazbu k povolení zabezpečení na úrovni zprávy společně se zabezpečeným přenosem. To je užitečné, když zabezpečený přenos vyžaduje k přenosu zpráv mezi klientem a službou a současně musí být zprávy na úrovni zprávy zabezpečené. Tato konfigurace není podporována vazbami poskytovanými systémem.

 Tato ukázka se skládá z klientského konzolového programu (EXE) a programu Service Console (EXE). Služba implementuje oboustranný kontrakt. Kontrakt je definován `ICalculatorDuplex` rozhraním, které zpřístupňuje matematické operace (sčítání, odčítání, násobení a dělení). `ICalculatorDuplex` Rozhraní umožňuje klientovi provádět matematické operace a vypočítat běžící výsledek během relace. Nezávisle, služba může vracet výsledky na `ICalculatorDuplexCallback` rozhraní. Duplexní smlouva vyžaduje relaci, protože je nutné vytvořit kontext, který bude korelovat sadu zpráv odesílaných mezi klientem a službou. Vlastní vazba je definována, která podporuje duplexní komunikaci a je zabezpečená.

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

 Konfigurace služby definuje vlastní vazbu, která podporuje následující:

- Komunikace TCP chráněná pomocí protokolu TLS/SSL.

- Zabezpečení zpráv Windows.

 Vlastní konfigurace vazeb umožňuje zabezpečenou přenos současně s povolením zabezpečení na úrovni zprávy. Řazení elementů vazby je důležité při definování vlastní vazby, protože každá představuje vrstvu v zásobníku kanálů (viz [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md)). Vlastní vazba je definována v konfiguračních souborech služby a klienta, jak je znázorněno v následující ukázkové konfiguraci.

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

 Vlastní vazba používá k ověření služby na úrovni přenosu certifikát služby a chrání zprávy během přenosu mezi klientem a službou. To je dosaženo `sslStreamSecurity` prvkem vazby. Certifikát služby je nakonfigurovaný pomocí chování služby, jak je znázorněno v následující ukázkové konfiguraci.

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

 Navíc vlastní vazba používá zabezpečení zpráv s typem přihlašovacích údajů systému Windows – jedná se o výchozí typ přihlašovacích údajů. To je dosaženo `security` prvkem vazby. Klient i služba jsou ověřovány pomocí zabezpečení na úrovni zpráv, pokud je k dispozici mechanismus ověřování protokolu Kerberos. K tomu dojde, pokud je ukázka spuštěna v prostředí služby Active Directory. Pokud ověřovací mechanismus protokolu Kerberos není k dispozici, použije se ověřování NTLM. Protokol NTLM ověřuje klienta služby, ale neověřuje službu klientovi. Prvek vazby je nakonfigurován tak, aby `SecureConversation` používal `authenticationType`, což vede k vytvoření relace zabezpečení v klientovi i ve službě. `security` Tato možnost je nutná k tomu, aby fungovala činnost duplexního kontraktu služby.

 Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.

```
Press <ENTER> to terminate client.
Result(100)
Result(50)
Result(882.5)
Result(441.25)
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)
```

 Při spuštění ukázky se zobrazí zprávy vracené klientovi do rozhraní zpětného volání odeslaného ze služby. Po dokončení všech operací se zobrazí každý mezilehlé výsledek následovaný celým vzorcem. Pro vypnutí klienta stiskněte klávesu ENTER.

 Zahrnutý soubor Setup. bat vám umožní nakonfigurovat klienta a server s příslušným certifikátem služby pro spuštění hostované aplikace, která vyžaduje zabezpečení na základě certifikátů. Tento dávkový soubor musí být upraven pro práci napříč počítači nebo pro práci v nehostovaném případě.

 Níže najdete stručný přehled různých částí dávkových souborů, které se vztahují k této ukázce, aby je bylo možné upravit tak, aby se spouštěly v příslušné konfiguraci:

- Vytváří se certifikát serveru.

     Následující řádky ze souboru Setup. bat vytvoří certifikát serveru, který se má použít. `%SERVER_NAME%` Proměnná Určuje název serveru. Změňte tuto proměnnou tak, aby určovala vlastní název serveru. Tento soubor dávky nastaví název serveru na localhost.

     Certifikát je uložený v úložišti CurrentUser pro služby hostované na webu.

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta.

     Následující řádky v souboru Setup. bat kopírují certifikát serveru do úložiště Důvěryhodné osoby z klienta. Tento krok je povinný, protože certifikáty vygenerované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem. Pokud už máte certifikát, který je rootem v důvěryhodném kořenovém certifikátu klienta – například certifikát vydaný společností Microsoft – tento krok naplnění úložiště certifikátů klienta s certifikátem serveru není vyžadován.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    >  Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z příkazového řádku sady Visual Studio 2010. Vyžaduje, aby proměnná prostředí MSSDK odkazovala na adresář, ve kterém je sada SDK nainstalována. Tato proměnná prostředí se automaticky nastaví v rámci příkazového řádku sady Visual Studio 2010.

### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

### <a name="to-run-the-sample-on-the-same-computer"></a>Spuštění ukázky na stejném počítači

1. Otevřete okno Developer Command Prompt pro Visual Studio s oprávněními správce a spusťte Setup. bat z ukázkové instalační složky. Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.

    > [!NOTE]
    >  Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z příkazového řádku sady Visual Studio 2012. Proměnná prostředí PATH nastavená v příkazovém řádku sady Visual Studio 2012 odkazuje na adresář, který obsahuje spustitelné soubory, které vyžaduje skript Setup. bat.  
  
2. Spustit Service. exe z \service\bin.  
  
3. Spustit soubor Client. exe z \client\bin. Aktivita klienta se zobrazí v klientské aplikaci konzoly.  
  
4. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Spuštění ukázky mezi počítači  
  
1. Na počítači služby:  
  
    1. Na počítači služby vytvořte virtuální adresář s názvem ServiceModelSamples.  
  
    2. Zkopírujte programové soubory služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači služby. Ujistěte se, že jste zkopírovali soubory do podadresáře \Bin.  
  
    3. Zkopírujte soubory Setup. bat a Cleanup. bat do počítače služby.  
  
    4. Spusťte následující příkaz v Developer Command Prompt pro Visual Studio otevřené s oprávněními správce: `Setup.bat service`. Tím se vytvoří certifikát služby s názvem subjektu, který odpovídá názvu počítače, ve kterém byl dávkový soubor spuštěn.  
  
        > [!NOTE]
        >  Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z příkazového řádku sady Visual Studio 2010. Vyžaduje, aby proměnná prostředí PATH odkazovala na adresář, ve kterém je nainstalována sada SDK. Tato proměnná prostředí se automaticky nastaví v rámci příkazového řádku sady Visual Studio 2010.

    5. Změňte > serviceCertificate v souboru Service. exe. config tak, aby odrážela název subjektu certifikátu vygenerovaného v předchozím kroku. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)

    6. Spusťte Service. exe z příkazového řádku.

2. V klientském počítači:

    1. Zkopírujte soubory klientského programu ze složky \client\bin\ do klientského počítače. Zkopírujte také soubor Cleanup. bat.

    2. Spuštěním nástroje CleanUp. bat odeberte všechny staré certifikáty z předchozích ukázek.

    3. Exportujte certifikát služby otevřením Developer Command Prompt pro sadu Visual Studio s oprávněními správce a spuštěním následujícího příkazu na počítači služby (nahraďte `%SERVER_NAME%` plně kvalifikovaným názvem počítače, kde Služba je spuštěná):

        ```
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer
        ```

    4. Zkopírujte% název_serveru%. cer do klientského počítače (nahraďte% název_serveru% plně kvalifikovaným názvem počítače, ve kterém je služba spuštěná).

    5. Importujte certifikát služby otevřením Developer Command Prompt pro sadu Visual Studio s oprávněními správce a spuštěním následujícího příkazu v klientském počítači (nahraďte% název_serveru% plně kvalifikovaným názvem počítače, kde Služba je spuštěná):

        ```
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople
        ```

         Postup c, d a e není nutný, pokud certifikát vystavuje důvěryhodný Vystavitel.

    6. Upravte soubor App. config klienta následujícím způsobem:

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

    7. Pokud je služba spuštěná pod jiným účtem než účtem NetworkService nebo LocalSystem v doménovém prostředí, možná budete muset změnit identitu koncového bodu pro koncový bod služby v souboru App. config klienta k nastavení příslušného hlavního názvu uživatele (UPN) nebo hlavního názvu služby (SPN). na účtu, který se používá ke spuštění služby. Další informace o identitě koncového bodu najdete v tématu [identita služby a ověřování](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) .

    8. Spusťte soubor Client. exe z příkazového řádku.

### <a name="to-clean-up-after-the-sample"></a>Vyčištění po ukázce

- Po dokončení ukázky Spusťte Cleanup. bat ve složce Samples.
