---
title: Zabezpečení zpráv s anonymní metodou
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c321cbf9-8c05-4cce-b5a5-4bf7b230ee03
author: BrucePerlerMS
ms.openlocfilehash: e90232a9e30a7da6234cb2884cdaaceb936d69ab
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48839879"
---
# <a name="message-security-anonymous"></a>Zabezpečení zpráv s anonymní metodou
Zpráva zabezpečení anonymní Ukázka předvádí, jak implementovat aplikace Windows Communication Foundation (WCF), který používá zabezpečení na úrovni zpráv bez ověřování klienta, ale, který vyžaduje ověření serveru pomocí serveru X.509 certifikát. Všechny zprávy aplikace mezi klientem a serverem jsou podepsaný a zašifrovaný. Tato ukázka je založena na [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) vzorku. Tento příklad se skládá z programu konzoly klienta (.exe) a služby knihovny (.dll) hostované v Internetové informační služby (IIS). Služba implementuje kontrakt, který definuje vzor komunikace požadavek odpověď.

> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.

 Tato ukázka přidá novou operaci Kalkulačka rozhraní, která vrací `True` Pokud klient není ověřený.

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

 Služba poskytuje jeden koncový bod pro komunikaci se službou, definované pomocí souboru konfigurace (Web.config). Koncový bod se skládá z adresy, vazby a kontrakt. Je vazba konfigurována se `wsHttpBinding` vazby. Výchozí režim zabezpečení `wsHttpBinding` vazba je `Message`. `clientCredentialType` Atribut je nastaven na `None`.

```xml
<system.serviceModel>

  <protocolMapping>
    <add scheme="http" binding="wsHttpBinding" />
  </protocolMapping>

  <bindings>
    <wsHttpBinding>
     <!--
     <!--This configuration defines the security mode as Message and-->
     <!--the clientCredentialType as None. This mode provides -- >
     <!--server authentication only using the service certificate.-->

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

 Přihlašovací údaje pro ověřování služby jsou uvedeny v [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md). Certifikát serveru musí obsahovat stejnou hodnotu pro `SubjectName` jako hodnota zadaná pro omezení `findValue` atributu, jak je znázorněno v následujícím ukázkovém kódu.

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

 Konfigurace koncového bodu klienta se skládá z absolutní adresu pro koncový bod služby, vazba a kontrakt. Režim zabezpečení klienta `wsHttpBinding` vazba je `Message`. `clientCredentialType` Atribut je nastaven na `None`.

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

 Ukázka sady <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> k <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> pro ověřování certifikátu služby. To se provádí v souboru App.config pro klienta v `behaviors` oddílu. To znamená, že pokud je certifikát v úložišti důvěryhodných osob uživatele, je důvěryhodný bez provedení ověření řetězu certifikátu vystavitele. Toto nastavení se používá zde ke zvýšení pohodlí tak, aby ukázku je možné spouštět bez vyžadování certifikátů vystavených certifikační autoritou (CA). Toto nastavení je méně bezpečné než výchozí, ChainTrust. Bezpečnostních důsledcích tohoto nastavení je třeba pečlivě zvážit před použitím `PeerOrChainTrust` v produkčním kódu.

 Implementace klienta přidá volání `IsCallerAnonymous` metoda a v opačném případě se neliší od [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) vzorku.

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

 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně Klient vypnutí klient.

```
IsCallerAnonymous returned: True
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 Dávkový soubor Setup.bat zprávu zabezpečení anonymní ukázka je součástí umožňuje nakonfigurovat server se příslušný certifikát ke spuštění prostředí aplikace, které vyžadují zabezpečení na základě certifikátů. Dávkový soubor může běžet ve dvou režimech. Pokud chcete spustit dávkový soubor v režimu jednoho počítače, zadejte `setup.bat` na příkazovém řádku. Chcete-li spustit v režimu služby, zadejte `setup.bat service`. Tento režim používejte při spuštění ukázky na počítačích. Zobrazit postup nastavení na konci tohoto tématu, kde podrobnosti.

 Následující body nabízí stručný přehled o různých částech dávkové soubory:

-   Vytváří se certifikát serveru.

     Následující řádky z dávkový soubor Setup.bat vytvořte certifikát serveru, který se má použít.

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     % Proměnná % název_serveru Určuje název serveru. Certifikát je uložen v úložišti LocalMachine. Pokud instalační dávkový soubor se spustí s parametrem služby (například `setup.bat service`) název_serveru % obsahuje název plně kvalifikované domény počítače. Jinak je výchozí hodnota je localhost.

-   Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta.

     Následující řádek zkopíruje certifikát serveru do úložiště důvěryhodných osob klienta. Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému klienta. Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikát vydaný společností Microsoft – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

-   Udělení oprávnění pro privátní klíč certifikátu.

     Následující řádky do dávkový soubor Setup.bat uložené v úložišti LocalMachine přístupné pro certifikát serveru Ujistěte se, [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] účet pracovního procesu.

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
>  Pokud používáte mimo USA Anglickou verzi Windows, musíte upravit soubor Setup.bat a nahraďte `NT AUTHORITY\NETWORK SERVICE` název účtu se místní ekvivalent.

### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku

1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači

1.  Ujistěte se, že cesta obsahuje složku, ve kterém jsou umístěny Makecert.exe a FindPrivateKey.exe.

2.  Spusťte Setup.bat z instalační složky s ukázkou v příkazovém řádku aplikace Visual Studio spusťte s oprávněními správce. Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.

    > [!NOTE]
    > Instalační dávkový soubor je určen ke spuštění z příkazového řádku aplikace Visual Studio. To vyžaduje, aby proměnné prostředí path v bodu do adresáře, ve kterém je nainstalována sada SDK. Tato proměnná prostředí je nastavena automaticky v rámci příkazového řádku aplikace Visual Studio.  
  
3.  Ověření přístupu ke službě pomocí prohlížeče tak, že zadáte adresu `http://localhost/servicemodelsamples/service.svc`.  
  
4.  Spusťte Client.exe z \client\bin. Činnost klienta se zobrazí na klientské aplikace konzoly.  
  
5.  Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky v počítačích  
  
1.  Vytvoření adresáře na počítači se službou. Vytvořte virtuální aplikaci s názvem servicemodelsamples pro tento adresář pomocí nástroje pro správu Internetové informační služby (IIS).  
  
2.  Zkopírujte soubory programu služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači se službou. Ujistěte se, že zkopírujete soubory v podadresáři \bin. Také kopírovat soubory Setup.bat a Cleanup.bat k počítači služby.  
  
3.  Vytvoření adresáře v klientském počítači pro binární soubory klienta.  
  
4.  Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači. Také kopírovat soubory Setup.bat Cleanup.bat a ImportServiceCert.bat do klienta.  
  
5.  Na serveru, spusťte `setup.bat service` v příkazovém řádku aplikace Visual Studio otevřené s oprávněními správce. Spuštění `setup.bat` s `service` argument vytvoří certifikát služby se plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.  
  
6.  Upravit soubor Web.config tak, aby odrážely nový název certifikátu (v `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), což je stejné jako plně kvalifikovaný název domény počítače.  
  
7.  Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.  
  
8.  V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby.  
  
9. Na straně klienta spouštění ImportServiceCert.bat v příkazovém řádku aplikace Visual Studio otevřeného s oprávněními správce. To importuje certifikát služby ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.  
  
10. Na klientském počítači spusťte Client.exe z příkazového řádku. Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>K vyčištění po vzorku  
  
-   Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.  
  
> [!NOTE]
>  Tento skript neodebere certifikáty služeb v klientském počítači při spuštění této ukázky na počítačích. Pokud jste provedli ukázky Windows Communication Foundation (WCF), které používají certifikáty na počítačích, je potřeba vymazat certifikáty služeb, které jsou nainstalovány v CurrentUser - TrustedPeople úložiště. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`

## <a name="see-also"></a>Viz také
