---
title: Ukázka zjišťování pomocí oborů
ms.date: 03/30/2017
ms.assetid: 6a37a754-6b8c-4ebe-bdf2-d4f0520271d5
ms.openlocfilehash: 9b65a348c943b07e813e3fe690f1364b77a94890
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972008"
---
# <a name="discovery-with-scopes-sample"></a>Ukázka zjišťování pomocí oborů

Tento příklad ukazuje, jak použít obory k kategorizaci zjistitelných koncových bodů a také jak <xref:System.ServiceModel.Discovery.DiscoveryClient> použít k provedení asynchronního hledání koncových bodů. Tato ukázka ve službě ukazuje, jak přizpůsobit zjišťování pro každý koncový bod přidáním chování zjišťování koncových bodů a jeho použitím k přidání oboru do koncového bodu a také k řízení zjistitelnosti koncového bodu. V klientovi ukázka přechází, jak můžou klienti vytvořit <xref:System.ServiceModel.Discovery.DiscoveryClient> a doladit parametry vyhledávání, aby zahrnovaly obory přidáním oborů <xref:System.ServiceModel.Discovery.FindCriteria>do. Tato ukázka také ukazuje, jak mohou klienti omezit odpovědi přidáním kritéria ukončení.

## <a name="service-features"></a>Funkce služby

Tento projekt zobrazí dva koncové body služby, které jsou <xref:System.ServiceModel.ServiceHost>přidány do. <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> K němu je přidružen každý koncový bod. Toto chování se používá k přidání oborů identifikátorů URI pro oba koncové body. Obory se používají k odlišení každého z těchto koncových bodů tak, aby klienti mohli vyladit hledání. Pro druhý koncový bod lze zjistitelnost zakázat nastavením <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> vlastnosti na. `false` Tím se zajistí, že se metadata zjišťování přidružená k tomuto koncovému bodu neodesílají jako součást jakýchkoli zpráv zjišťování.

## <a name="client-features"></a>Klientské funkce

Metoda ukazuje, jak <xref:System.ServiceModel.Discovery.DiscoveryClient> použít a předat <xref:System.ServiceModel.Discovery.FindCriteria> se dvěma omezeními. `FindCalculatorServiceAddress()` Do kritérií je přidán obor a <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> vlastnost je nastavena na hodnotu 1. Rozsah omezuje výsledky jenom na služby, které publikují stejný obor. Nastavení <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> na 1 omezí odezvy, které <xref:System.ServiceModel.Discovery.DiscoveryClient> čekají na, maximálně 1 koncový bod. <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> Volání je synchronní operace, která blokuje vlákno, dokud není dosažen časový limit nebo byl nalezen jeden koncový bod.

### <a name="to-use-this-sample"></a>Použití této ukázky

1. Tato ukázka používá koncové body HTTP a ke spuštění této ukázky musí být přidány správné seznamy ACL adres URL. Podrobnosti najdete v tématu [Konfigurace HTTP a HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) . Spuštění následujícího příkazu u zvýšeného oprávnění by mělo přidat příslušné seznamy ACL. Pokud příkaz nefunguje tak, jak je, můžete chtít nahradit doménu a uživatelské jméno pro následující argumenty:`netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. Sestavte řešení.

3. Spusťte spustitelný soubor služby z adresáře buildu.

4. Spusťte klientský spustitelný soubor. Upozorňujeme, že klient může službu vyhledat.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryWithScopes`
