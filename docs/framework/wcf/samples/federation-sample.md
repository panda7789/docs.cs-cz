---
title: Ukázka federace
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: a9c2b91f7d8bdf24476c76fcd479b7f2fb44c90f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="federation-sample"></a>Ukázka federace
Tento příklad znázorňuje federované zabezpečení.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Windows Communication Foundation (WCF) poskytuje podporu pro nasazení architektury federované zabezpečení prostřednictvím `wsFederationHttpBinding`. `wsFederationHttpBinding` Poskytuje vazbu zabezpečeným, spolehlivým a vzájemná spolupráce, který zahrnuje použití protokolu HTTP jako podkladový přenosový mechanismus pro požadavek nebo odpověď komunikace a Text/XML jako přenosový formát pro kódování. Další informace o federační ve WCF najdete v tématu [Federation](../../../../docs/framework/wcf/feature-details/federation.md).  
  
 Tento scénář se skládá ze 4 částí:  
  
-   Služba pro knihkupectví  
  
-   Knihkupectví služby tokenů zabezpečení  
  
-   HomeRealm služby tokenů zabezpečení  
  
-   Klient pro knihkupectví  
  
 Službu pro knihkupectví podporuje dvě operace `BrowseBooks` a `BuyBook`. Umožňuje anonymní přístup k `BrowseBooks` operaci, ale vyžaduje ověřený přístup k přístupu `BuyBooks` operaci. Ověřování má podobu tokenem vydaným službou tokenů zabezpečení pro knihkupectví. Konfigurační soubor pro knihkupectví službu bodů klienty pomocí tokenů zabezpečení pro knihkupectví `wsFederationHttpBinding`.  
  
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
  
 STS pro knihkupectví pak vyžaduje, aby klienti ověřovat pomocí tokenem vydaným službou tokenů zabezpečení HomeRealm. Znovu konfiguračního souboru pro knihkupectví STS bodů klienty pomocí služby tokenů zabezpečení HomeRealm `wsFederationHttpBinding`.  
  
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
  
 Posloupnost událostí při přístupu k `BuyBook` operace vypadá takto:  
  
1.  Klient se ověří na službu STS HomeRealm pomocí pověření systému Windows.  
  
2.  Služba tokenů zabezpečení HomeRealm vystaví token, který můžete použít k ověřování pro knihkupectví tokenů zabezpečení.  
  
3.  Klient se ověří na službu STS knihkupectví pomocí tokenem vydaným službou tokenů zabezpečení HomeRealm.  
  
4.  Služba tokenů zabezpečení knihkupectví vystaví token, který slouží k ověření pro knihkupectví službu.  
  
5.  Klient se ověří pro knihkupectví služby pomocí tokenem vydaným službou tokenů zabezpečení pro knihkupectví.  
  
6.  Klient přistupuje k `BuyBook` operaci.  
  
 Přečtěte si následující pokyny o tom, jak nastavit a tuto ukázku spustit.  
  
> [!NOTE]
>  Musíte mít oprávnění k zápisu do **wwwroot** directory chcete tuto ukázku spustit.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Otevřete příkazové okno SDK. V cestě ukázka spustit Setup.bat. Tím se vytvoří virtuální adresáře, které jsou potřebné pro vzorovou a nainstaluje požadované certifikáty s příslušnými oprávněními.  
  
    > [!NOTE]
    >  Dávkový soubor Setup.bat slouží ke spuštění z Windows příkazový řádek SDK. Se vyžaduje, aby proměnné prostředí MSSDK bodu na adresář, kam nainstalovat sadu SDK. Tato proměnná prostředí bude automaticky nastavena v příkazovém řádku Windows SDK. Na [!INCLUDE[wv](../../../../includes/wv-md.md)], ujistěte se, že Kompatibilita správy služby IIS 6.0 je nainstalovat, protože nastavení používá skripty Správce služby IIS. Spuštění skriptu nastavení [!INCLUDE[wv](../../../../includes/wv-md.md)] vyžaduje oprávnění správce.  
  
2.  Otevřete FederationSample.sln v sadě Visual Studio a vyberte **sestavit řešení** z **sestavení** nabídky. Toto sestavení společné soubory projektu, služba pro knihkupectví, tokenů zabezpečení pro knihkupectví, HomeRealm služby tokenů zabezpečení a nasadí je ve službě IIS. To také sestavení klientská aplikace pro knihkupectví a umístí BookStoreClient.exe spustitelný soubor ve složce FederationSample\BookStoreClient\bin\Debug.  
  
3.  Dvakrát klikněte na BookStoreClient.exe. Zobrazí se okno BookStoreClient.  
  
4.  Můžete procházet k dispozici v knihkupectví webu knihy kliknutím **procházet knihy**.  
  
5.  Chcete-li zakoupit konkrétního seznamu, vyberte seznamu v seznamu a klikněte na tlačítko **koupit kniha**. Aplikace spuštění a ověřuje pomocí služby tokenů zabezpečení HomeRealm ověřování systému Windows.  
  
     Ukázka je nakonfigurován, aby uživatelé mohli nákup knih, které náklady $15 nebo méně. Probíhá pokus o koupit knih, které náklady více než 15 $ má za následek klient pro získávání zpráva Přístup byl odepřen z adresáře služby úložiště.  
  
    > [!NOTE]
    >  Ukázka neaktualizuje úvěr uživatele po nákupu. Můžete opakovaně nákup knih v rámci limitu (pevné) platební uživatele.  
  
#### <a name="to-clean-up"></a>Vyčistěte  
  
1.  Spusťte Cleanup.bat. Tím odstraní virtuální adresáře, které byly vytvořeny během nahoru a také odebere certifikáty nainstalovat během instalace.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
  
## <a name="see-also"></a>Viz také
