---
title: Ukázka federace
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: bc2c28300d9bfc3c30388f8d13e05a23a9f37287
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311458"
---
# <a name="federation-sample"></a>Ukázka federace
V této ukázce federovaného zabezpečení.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Windows Communication Foundation (WCF) poskytuje podporu pro nasazení architektury zabezpečení prostřednictvím `wsFederationHttpBinding`. `wsFederationHttpBinding` Poskytuje zabezpečené, spolehlivé a interoperabilní vazbu, která zahrnuje použití protokolu HTTP jako podkladový přenosový mechanismus pro komunikaci požadavek/odpověď a Text/XML jako přenosový formát pro kódování. Další informace o federace ve službě WCF najdete v tématu [federace](../../../../docs/framework/wcf/feature-details/federation.md).  
  
 Tento scénář se skládá ze 4 částí:  
  
-   Služba knihkupectví  
  
-   Knihkupectví služby tokenů zabezpečení  
  
-   HomeRealm služby tokenů zabezpečení  
  
-   Knihkupectví klienta  
  
 Služba knihkupectví podporuje dvě operace `BrowseBooks` a `BuyBook`. To umožňuje anonymní přístup k `BrowseBooks` operace, ale vyžaduje ověřený přístup k přístupu `BuyBooks` operace. Ověřování má formu tokenem vydaným službou tokenů zabezpečení knihkupectví. Konfigurační soubor služby knihkupectví body klientů pomocí služby tokenů zabezpečení knihkupectví `wsFederationHttpBinding`.  
  
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
  
 Služba tokenů zabezpečení knihkupectví pak vyžaduje, že klienti ověřování pomocí tokenu vydaného službou HomeRealm STS. Znovu, konfigurační soubor služby STS knihkupectví odkazuje klientů pomocí služby tokenů zabezpečení HomeRealm `wsFederationHttpBinding`.  
  
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
  
 Posloupnost událostí, když přistupoval k `BuyBook` operace vypadá takto:  
  
1. Klient se ověří na službu STS HomeRealm pomocí přihlašovacích údajů Windows.  
  
2. Služba tokenů zabezpečení HomeRealm vystaví token, který slouží k ověření na službu STS knihkupectví.  
  
3. Klient se ověří pomocí tokenu vystaví služba HomeRealm STS Služba tokenů zabezpečení knihkupectví.  
  
4. Služba tokenů zabezpečení knihkupectví vystaví token, který slouží k ověření služby knihkupectví.  
  
5. Klient se ověří ve službě knihkupectví pomocí tokenu vystaví služba STS knihkupectví.  
  
6. Klient přistupuje k `BuyBook` operace.  
  
 Přečtěte si následující pokyny o tom, jak nastavit a spustit tento příklad.  
  
> [!NOTE]
>  Musíte mít oprávnění k zápisu **wwwroot** adresář pro tuto ukázku spustit.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Otevřete příkazové okno sady SDK. V cestě ukázkové spuštění Setup.bat. To vytvoří virtuální adresáře, vyžaduje se pro ukázku a nainstaluje požadované certifikáty s příslušnými oprávněními.  
  
    > [!NOTE]
    >  Dávkový soubor Setup.bat je navržena pro spouštění na příkazovém řádku sady SDK Windows. To vyžaduje, aby proměnné prostředí MSSDK bodu do adresáře, ve kterém je nainstalována sada SDK. Tato proměnná prostředí je nastavena automaticky v příkazovém řádku Windows SDK. Na [!INCLUDE[wv](../../../../includes/wv-md.md)], ujistěte se, že Kompatibilita správy služby IIS 6.0 je nainstalovat, protože nastavení používá skripty Správce služby IIS. Spouštění skriptu nastavení na [!INCLUDE[wv](../../../../includes/wv-md.md)] vyžaduje oprávnění správce.  
  
2. Otevřete FederationSample.sln v sadě Visual Studio a vyberte **sestavit řešení** z **sestavení** nabídky. To vytvoří běžné soubory projektu, knihkupectví služby, knihkupectví STS, HomeRealm STS a nasadí ve službě IIS. To také vytvoří knihkupectví klientská aplikace a umístí BookStoreClient.exe spustitelný soubor ve složce FederationSample\BookStoreClient\bin\Debug.  
  
3. Double-click BookStoreClient.exe. Zobrazí se okno BookStoreClient.  
  
4. K dispozici v knihkupectví knih můžete procházet kliknutím **procházet knihy**.  
  
5. Pokud chcete zakoupit konkrétní adresáře, v seznamu vyberte knihy a klikněte na **zakoupení knihy**. Aplikace spuštění a ověřuje pomocí služby tokenů zabezpečení HomeRealm ověřování Windows.  
  
     Ukázka je nakonfigurovaná tak, aby uživatelům nákup knih, které nákladů 15 USD nebo nižší. Došlo k pokusu o zakoupení knihy, které víc než 15 USD za následek klienta získávání zpráva Přístup byl odepřen z službu Store knihy nákladů.  
  
    > [!NOTE]
    >  Ukázka neaktualizuje uživatele kreditního limitu po nákupu. Můžete opakovaně nákup knih v rámci daného uživatele (pevné) kreditního limitu.  
  
#### <a name="to-clean-up"></a>Vyčistit  
  
1. Spusťte Cleanup.bat. To odstraní virtuální adresáře, které byly vytvořené během nastavení a také odebere během instalace nainstalovat certifikáty.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
