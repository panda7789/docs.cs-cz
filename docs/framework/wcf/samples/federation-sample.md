---
title: Ukázka federace
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: 9ec462f88c0e3a039b7f288554be3e28f13ece08
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144666"
---
# <a name="federation-sample"></a>Ukázka federace
Tato ukázka ukazuje federované zabezpečení.  
  
## <a name="sample-details"></a>Podrobnosti ukázky  
 Windows Communication Foundation (WCF) poskytuje podporu pro nasazení federovaných architektur zabezpečení prostřednictvím `wsFederationHttpBinding`. Poskytuje `wsFederationHttpBinding` zabezpečenou, spolehlivou a interoperabilní vazbu, která zahrnuje použití protokolu HTTP jako základního mechanismu přenosu pro komunikaci požadavku a odpovědi a text/XML jako formát vodiče pro kódování. Další informace o Federaci ve WCF naleznete v [tématu Federation](../../../../docs/framework/wcf/feature-details/federation.md).  
  
 Scénář se skládá ze 4 kusů:  
  
- Služba Knihkupectví  
  
- Knihkupectví STS  
  
- HomeRealm STS  
  
- Klient Knihkupectví  
  
 Služba BookStore podporuje dvě `BrowseBooks` `BuyBook`operace a . Umožňuje anonymní přístup `BrowseBooks` k operaci, ale vyžaduje ověřený přístup pro přístup k `BuyBooks` operaci. Ověřování má podobu tokenu vydaného službou BookStore STS. Konfigurační soubor služby Knihkupectví odkazuje klienty na `wsFederationHttpBinding`službu BookStore STS pomocí .  
  
```xml  
<wsFederationHttpBinding>  
<!-- This is the Service binding for the BuyBooks endpoint. It redirects clients to the BookStore STS -->  
    <binding name='BuyBookBinding'>  
        <security mode="Message">  
            <message>  
                <issuerMetadata  
  address='http://localhost/FederationSample/BookStoreSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='BookStoreSTS.com'/>  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 BookStore STS pak vyžaduje, aby klienti ověřit pomocí tokenu vydaného HomeRealm STS. Opět platí, že konfigurační soubor pro BookStore STS `wsFederationHttpBinding`odkazuje klienty na HomeRealm STS pomocí .  
  
```xml  
<wsFederationHttpBinding>  
 <!-- This is the binding for the clients requesting tokens from this STS. It redirects clients to the HomeRealm STS -->  
    <binding name='BookStoreSTSBinding'>  
        <security mode='Message'>  
            <message>  
                <issuerMetadata  
 address='http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='HomeRealmSTS.com' />  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 Posloupnost událostí při `BuyBook` přístupu k operaci je následující:  
  
1. Klient se ověřuje na HomeRealm STS pomocí pověření systému Windows.  
  
2. HomeRealm STS vydává token, který lze použít k ověření na BookStore STS.  
  
3. Klient se ověřuje do úložiště služby StS pomocí tokenu vydaného službou HomeRealm STS.  
  
4. BookStore STS vydává token, který lze použít k ověření služby Knihkupectví.  
  
5. Klient se ověřuje službě BookStore pomocí tokenu vydaného službou StS knihkupectví.  
  
6. Klient přistupuje k `BuyBook` operaci.  
  
 Naleznete v následujících pokynech o nastavení a spuštění této ukázky.  
  
> [!NOTE]
> Chcete-li spustit tuto ukázku, musíte mít oprávnění k zápisu do adresáře **wwwroot.**  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Otevřete příkazové okno sady SDK. V cestě ukázky spusťte Setup.bat. Tím se vytvoří virtuální adresáře požadované pro ukázku a nainstaluje požadované certifikáty s příslušnými oprávněními.  
  
    > [!NOTE]
    > Dávkový soubor Setup.bat je určen ke spuštění z příkazového řádku sady Windows SDK. Vyžaduje, aby proměnná prostředí sady MSSDK přecšuje do adresáře, ve kterém je sada SDK nainstalována. Tato proměnná prostředí je automaticky nastavena v příkazovém řádku sady Windows SDK. V systému Windows Vista je nutné zajistit, aby byla nainstalována kompatibilita služby IIS 6.0, protože nastavení používá skripty správce služby IIS. Spuštění skriptu nastavení v systému Windows Vista vyžaduje oprávnění správce.  
  
2. Otevřete federationsample.sln v sadě Visual Studio a z nabídky **Sestavení** vyberte **Sestavit řešení.** To vytvoří společné soubory projektu, služba Knihkupectví, Knihkupectví STS, HomeRealm STS a nasazuje je ve službě IIS. Tím se také vytvoří klientská aplikace knihkupectví a uloží spustitelný soubor BookStoreClient.exe do složky FederationSample\BookStoreClient\bin\Debug.  
  
3. Poklepejte na soubor BookStoreClient.exe. Zobrazí se okno Klienta knihkupectví.  
  
4. Knihy dostupné v knihkupectví můžete procházet kliknutím na **procházet knihy**.  
  
5. Chcete-li zakoupit určitou knihu, vyberte ji v seznamu a klepněte na tlačítko **Koupit knihu**. Aplikace se spustí a ověřuje pomocí ověřování systému Windows pomocí služby Token zabezpečení HomeRealm.  
  
     Ukázka je nakonfigurována tak, aby uživatelům umožnila nakupovat knihy, které stojí 15 USD nebo méně. Pokus o nákup knih, které stojí více než 15 USD, má za následek, že klient získá zprávu o odepření přístupu ze služby Knihkupectví.  
  
    > [!NOTE]
    > Ukázka neaktualizuje limit kreditu uživatele po nákupu. Knihy můžete opakovaně nakupovat v rámci limitu kreditu uživatele (pevné).  
  
#### <a name="to-clean-up"></a>Chcete-li vyčistit  
  
1. Spusťte Cleanup.bat. Tím odstraníte virtuální adresáře, které byly vytvořeny během instalace, a také odeberete certifikáty nainstalované během instalace.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
