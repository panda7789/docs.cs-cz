---
title: Ukázka federace
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: 00cb9a13a01687fb41f1d5c09f277d582f706e3b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594683"
---
# <a name="federation-sample"></a>Ukázka federace
Tato ukázka demonstruje federované zabezpečení.  
  
## <a name="sample-details"></a>Podrobnosti ukázky  
 Windows Communication Foundation (WCF) poskytuje podporu pro nasazení federovaných architektur zabezpečení prostřednictvím `wsFederationHttpBinding` . `wsFederationHttpBinding`Poskytuje zabezpečenou, spolehlivou a interoperabilní vazbu, která zahrnuje použití http jako základního přenosového mechanismu pro komunikaci typu požadavek/odpověď a text/XML jako formát přenosu pro kódování. Další informace o federaci v WCF najdete v článku [federace](../feature-details/federation.md).  
  
 Scénář se skládá ze 4 kusů:  
  
- Služba BookStore  
  
- BookStore STS  
  
- HomeRealm STS  
  
- Klient BookStore  
  
 Služba BookStore podporuje dvě operace, `BrowseBooks` a `BuyBook` . Umožňuje anonymní přístup k `BrowseBooks` operaci, ale vyžaduje ověřený přístup pro přístup k této `BuyBooks` operaci. Ověřování má formu tokenu vydaného službou BookStore STS. Konfigurační soubor pro službu BookStore odkazuje na klienty služby BookStore STS pomocí `wsFederationHttpBinding` .  
  
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
  
 BookStore STS pak vyžaduje, aby se klienti ověřovali pomocí tokenu vydaného službou HomeRealm STS. Konfigurační soubor pro službu BookStore STS se znovu odkazuje na klienty služby HomeRealm STS pomocí `wsFederationHttpBinding` .  
  
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
  
 Sekvence událostí při přístupu k `BuyBook` operaci je následující:  
  
1. Klient se ověřuje pomocí pověření služby HomeRealm STS prostřednictvím přihlašovacích údajů systému Windows.  
  
2. Služba HomeRealm STS vydá token, který se dá použít k ověření v knihkupectví STS.  
  
3. Klient se ověřuje pro službu BookStore STS pomocí tokenu vydaného službou HomeRealm STS.  
  
4. Služba BookStore STS vydá token, který lze použít k ověření ve službě BookStore.  
  
5. Klient se ověřuje pro službu BookStore pomocí tokenu vydaného službou BookStore STS.  
  
6. Klient přistupuje k `BuyBook` operaci.  
  
 V následujících pokynech se dozvíte, jak nastavit a spustit tuto ukázku.  
  
> [!NOTE]
> Pro spuštění této ukázky musíte mít oprávnění k zápisu do adresáře **wwwroot** .  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Otevřete okno příkazového řádku sady SDK. V ukázkové cestě spusťte Setup. bat. Tím se vytvoří virtuální adresáře vyžadované pro ukázku a nainstalují se požadované certifikáty s příslušnými oprávněními.  
  
    > [!NOTE]
    > Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z příkazového řádku Windows SDK. Vyžaduje, aby proměnná prostředí MSSDK odkazovala na adresář, ve kterém je sada SDK nainstalována. Tato proměnná prostředí se automaticky nastaví v rámci Windows SDK příkazového řádku. V systému Windows Vista je nutné zajistit, aby byla nainstalovaná Kompatibilita správy služby IIS 6,0, protože nastavení používá skripty Správce služby IIS. Spuštění skriptu pro nastavení v systému Windows Vista vyžaduje oprávnění správce.  
  
2. Otevřete FederationSample. sln v aplikaci Visual Studio a v nabídce **sestavení** vyberte **Sestavit řešení** . Tím se vytvoří společné soubory projektu, služba Bookstore, Bookstore STS, HomeRealm STS a nasadí je ve službě IIS. Tím se také vytvoří klientská aplikace pro Bookstore a ve složce FederationSample\BookStoreClient\bin\Debug se umístí spustitelný soubor BookStoreClient. exe.  
  
3. Dvakrát klikněte na BookStoreClient. exe. Zobrazí se okno BookStoreClient.  
  
4. Knihy, které jsou k dispozici v knihkupectví, můžete procházet kliknutím na **Procházet knihy**.  
  
5. Pokud si chcete koupit určitou knihu, vyberte v seznamu knihu a klikněte na **koupit knihu**. Aplikace se spustí a ověří pomocí ověřování systému Windows pomocí služby tokenu zabezpečení HomeRealm.  
  
     Tato ukázka je nakonfigurovaná tak, aby umožňovala uživatelům koupit knihy, které $15 nebo méně. Při pokusu o zakoupení knih s vyššími náklady, než $15, dojde v klientovi k získání zprávy o odepření přístupu ze služby Book Store.  
  
    > [!NOTE]
    > Ukázka neaktualizuje limit úvěru uživatele po nákupu. V rámci limitu úvěru uživatele můžete opakovaně nakupovat knihy.  
  
#### <a name="to-clean-up"></a>Vyčištění  
  
1. Spusťte nástroj CleanUp. bat. Tím odstraníte virtuální adresáře, které byly vytvořeny během instalace, a zároveň dojde k odebrání certifikátů nainstalovaných během instalace.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
