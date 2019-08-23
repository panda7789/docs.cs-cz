---
title: Zabezpečení zpráv s anonymní metodou
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c321cbf9-8c05-4cce-b5a5-4bf7b230ee03
ms.openlocfilehash: fdcf0c25e4e6cab2c99457112b892f5d2c5bd3b4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930625"
---
# <a name="message-security-anonymous"></a>Zabezpečení zpráv s anonymní metodou
Anonymní ukázka zabezpečení zpráv ukazuje, jak implementovat aplikaci Windows Communication Foundation (WCF), která používá zabezpečení na úrovni zprávy bez ověřování klientů, ale vyžaduje ověření serveru pomocí X. 509 serveru. certifikát. Všechny zprávy aplikací mezi klientem a serverem jsou podepsané a šifrované. Tato ukázka je založená na ukázce [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) . Tato ukázka se skládá z programu klientské konzoly (. exe) a knihovny služeb (. dll) hostované službou Internetová informační služba (IIS). Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď.

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

 Tato ukázka přidá novou operaci do rozhraní kalkulačky, které vrátí `True` , pokud klient nebyl ověřen.

```csharp
public class CalculatorService : ICalculator
{
    public bool IsCallerAnonymous()
    {
        // ServiceSecurityContext.IsAnonymous returns true if the caller is not authenticated.
        return ServiceSecurityContext.Current.IsAnonymous;
    }
    ...
}
```

 Služba zpřístupňuje jeden koncový bod pro komunikaci se službou, definovaná pomocí konfiguračního souboru (Web. config). Koncový bod se skládá z adresy, vazby a kontraktu. Vazba je nakonfigurována s `wsHttpBinding` vazbou. Výchozím režimem `wsHttpBinding` zabezpečení vazby je `Message`. Atribut je nastaven na `None`hodnotu. `clientCredentialType`

```xml
<system.serviceModel>

  <protocolMapping>
    <add scheme="http" binding="wsHttpBinding" />
  </protocolMapping>

  <bindings>
    <wsHttpBinding>
     <!-- This configuration defines the security mode as Message and -->
     <!-- the clientCredentialType as None. This mode provides -->
     <!-- server authentication only using the service certificate. -->

     <binding>
       <security mode="Message">
         <message clientCredentialType="None" />
       </security>
     </binding>
    </wsHttpBinding>
  </bindings>
  ...
</system.serviceModel>
```

 Přihlašovací údaje, které se mají použít k ověřování služby, jsou uvedené v [ \<> chování](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md). Certifikát serveru musí obsahovat stejnou hodnotu `SubjectName` jako hodnota zadaná `findValue` pro atribut, jak je znázorněno v následujícím ukázkovém kódu.

```xml
<behaviors>
  <serviceBehaviors>
    <behavior>
      <!--
    The serviceCredentials behavior allows you to define a service certificate.
    A service certificate is used by a client to authenticate the service and provide message protection.
    This configuration references the "localhost" certificate installed during the setup instructions.
    -->
      <serviceCredentials>
        <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
      </serviceCredentials>
      <serviceMetadata httpGetEnabled="True"/>
      <serviceDebug includeExceptionDetailInFaults="False" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```

 Konfigurace koncového bodu klienta se skládá z absolutní adresy koncového bodu služby, vazby a kontraktu. Režim zabezpečení klienta pro `wsHttpBinding` vazbu je. `Message` Atribut je nastaven na `None`hodnotu. `clientCredentialType`

```xml
<system.serviceModel>
  <client>
    <endpoint name=""
             address="http://localhost/servicemodelsamples/service.svc"
             binding="wsHttpBinding"
             behaviorConfiguration="ClientCredentialsBehavior"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </client>

  <bindings>
    <wsHttpBinding>
      <!--This configuration defines the security mode as -->
      <!--Message and the clientCredentialType as None. -->
      <binding name="Binding1">
        <security mode = "Message">
          <message clientCredentialType="None"/>
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>
  ...
</system.serviceModel>
```

 Ukázka nastaví <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> pro ověřování certifikátu služby. To se provádí v souboru App. config klienta v `behaviors` části. To znamená, že pokud je certifikát v úložišti důvěryhodných osob uživatele, je důvěryhodný, aniž by prováděl ověření řetězu vystavitele certifikátu. Toto nastavení se tady používá pro usnadnění, aby bylo možné spustit ukázku bez vyžadování certifikátů vydaných certifikační autoritou (CA). Toto nastavení je méně bezpečné než výchozí ChainTrust. Před použitím `PeerOrChainTrust` v produkčním kódu by se mělo pečlivě zvážit dopad na zabezpečení tohoto nastavení.

 Implementace klienta přidá volání `IsCallerAnonymous` metody a jinak se neliší od ukázky [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) .

```csharp
// Create a client with a client endpoint configuration.
CalculatorClient client = new CalculatorClient();

// Call the GetCallerIdentity operation.
Console.WriteLine("IsCallerAnonymous returned: {0}", client.IsCallerAnonymous());

// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = client.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

...

//Closing the client gracefully closes the connection and cleans up resources.
client.Close();

Console.WriteLine();
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

 Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.

```
IsCallerAnonymous returned: True
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 Dávkový soubor Setup. bat, který je součástí ukázky zabezpečení zprávy anonymní, vám umožní nakonfigurovat server s relevantním certifikátem pro spuštění hostované aplikace, která vyžaduje zabezpečení založené na certifikátech. Dávkový soubor lze spustit ve dvou režimech. Pokud chcete spustit dávkový soubor v režimu jednoho počítače, zadejte `setup.bat` do příkazového řádku. Pokud ho chcete spustit v režimu služby, `setup.bat service`zadejte. Tento režim použijte při spuštění ukázky v různých počítačích. Podrobnosti najdete v postupu nastavení na konci tohoto tématu.

 V následující části najdete stručný přehled různých částí dávkových souborů:

- Vytváří se certifikát serveru.

     Následující řádky z dávkového souboru Setup. bat vytvoří certifikát serveru, který se má použít.

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     Proměnná% Název_serveru% Určuje název serveru. Certifikát je uložený v úložišti LocalMachine. Pokud je instalační dávkový soubor spuštěn s argumentem služby (například `setup.bat service`),% název_serveru% obsahuje plně kvalifikovaný název domény počítače. V opačném případě se použije jako localhost.

- Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta.

     Následující řádek zkopíruje certifikát serveru do úložiště Důvěryhodné osoby z klienta. Tento krok je povinný, protože certifikáty vygenerované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem. Pokud už máte certifikát, který je rootem v důvěryhodném kořenovém certifikátu klienta – například certifikát vydaný společností Microsoft – tento krok naplnění úložiště certifikátů klienta s certifikátem serveru není vyžadován.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- Udělení oprávnění k privátnímu klíči certifikátu.

     Následující řádky v dávkovém souboru Setup. bat umožňují, aby byl certifikát serveru uložený v úložišti LocalMachine dostupný pro účet pracovního procesu ASP.NET.

    ```bat
    echo ************
    echo setting privileges on server certificates
    echo ************
    for /F "delims=" %%i in ('"%MSSDK%\bin\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
    (ver | findstr "5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
    iisreset
    ```

> [!NOTE]
> Pokud používáte jinou než U. S. Anglická edice Windows: musíte upravit soubor Setup. bat a nahradit `NT AUTHORITY\NETWORK SERVICE` název účtu svým regionálním ekvivalentem.

### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

### <a name="to-run-the-sample-on-the-same-computer"></a>Spuštění ukázky na stejném počítači

1. Ujistěte se, že cesta obsahuje složku, ve které jsou umístěny nástroje MakeCert. exe a FindPrivateKey. exe.

2. Spusťte Setup. bat z ukázkové instalační složky ve Developer Command Prompt pro Visual Studio spusťte s oprávněními správce. Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.

    > [!NOTE]
    > Instalační dávkový soubor je navržený tak, aby se spouštěl z Developer Command Prompt pro Visual Studio. Vyžaduje, aby proměnná prostředí PATH odkazovala na adresář, ve kterém je nainstalována sada SDK. Tato proměnná prostředí se automaticky nastaví v rámci Developer Command Prompt pro Visual Studio.  
  
3. Zadáním adresy `http://localhost/servicemodelsamples/service.svc`ověřte přístup ke službě pomocí prohlížeče.  
  
4. Spustit soubor Client. exe z \client\bin. Aktivita klienta se zobrazí v klientské aplikaci konzoly.  
  
5. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Spuštění ukázky mezi počítači  
  
1. Vytvořte adresář na počítači služby. Vytvořte virtuální aplikaci s názvem ServiceModelSamples pro tento adresář pomocí nástroje pro správu služby Internetová informační služba (IIS).  
  
2. Zkopírujte programové soubory služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači služby. Ujistěte se, že jste zkopírovali soubory do podadresáře \Bin. Zkopírujte také soubory Setup. bat a Cleanup. bat do počítače služby.  
  
3. Vytvořte v klientském počítači adresář pro binární soubory klienta.  
  
4. Zkopírujte soubory klientských programů do adresáře klienta v klientském počítači. Zkopírujte také do klienta soubory Setup. bat, Cleanup. bat a ImportServiceCert. bat.  
  
5. Na serveru spusťte `setup.bat service` v Developer Command Prompt pro Visual Studio otevřené s oprávněními správce. Při `setup.bat` spuštění`service` s argumentem se vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a vyexportuje certifikát služby do souboru s názvem Service. cer.  
  
6. Upravte soubor Web. config tak, aby odrážel nový název certifikátu ( `findValue` v atributu [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), který je stejný jako plně kvalifikovaný název domény počítače.  
  
7. Zkopírujte soubor Service. cer z adresáře služby do adresáře klienta v klientském počítači.  
  
8. V souboru Client. exe. config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.  
  
9. Na straně klienta spusťte ImportServiceCert. bat ve Developer Command Prompt pro Visual Studio otevřené s oprávněními správce. Tím se certifikát služby importuje ze souboru Service. cer do úložiště CurrentUser-TrustedPeople.  
  
10. V klientském počítači spusťte z příkazového řádku soubor Client. exe. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Vyčištění po ukázce  
  
- Po dokončení ukázky Spusťte Cleanup. bat ve složce Samples.  
  
> [!NOTE]
> Tento skript při spuštění této ukázky mezi počítači neodebere certifikáty služby na klientovi. Pokud jste spustili ukázky Windows Communication Foundation (WCF), které používají certifikáty napříč počítači, nezapomeňte vymazat certifikáty služby, které byly nainstalovány v úložišti CurrentUser-TrustedPeople. K tomu použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`Například:`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`
