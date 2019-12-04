---
title: Ukázka zjišťování pomocí oborů
ms.date: 03/30/2017
ms.assetid: 6a37a754-6b8c-4ebe-bdf2-d4f0520271d5
ms.openlocfilehash: 23991002a5236c491a9f74c7efe71ceb2bf51a37
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74712067"
---
# <a name="discovery-with-scopes-sample"></a>Ukázka zjišťování pomocí oborů

Tento příklad ukazuje, jak použít obory k kategorizaci zjistitelných koncových bodů a také jak použít <xref:System.ServiceModel.Discovery.DiscoveryClient> k provedení asynchronního hledání koncových bodů. Tato ukázka ve službě ukazuje, jak přizpůsobit zjišťování pro každý koncový bod přidáním chování zjišťování koncových bodů a jeho použitím k přidání oboru do koncového bodu a také k řízení zjistitelnosti koncového bodu. V klientovi ukázka projde, jak můžou klienti vytvořit <xref:System.ServiceModel.Discovery.DiscoveryClient> a doladit parametry vyhledávání, aby zahrnovaly obory přidáním oborů do <xref:System.ServiceModel.Discovery.FindCriteria>. Tato ukázka také ukazuje, jak mohou klienti omezit odpovědi přidáním kritéria ukončení.

## <a name="service-features"></a>Funkce služby

Tento projekt zobrazí dva koncové body služby, které jsou přidány do <xref:System.ServiceModel.ServiceHost>. Ke každému koncovému bodu je přidružená <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>. Toto chování se používá k přidání oborů identifikátorů URI pro oba koncové body. Obory se používají k odlišení každého z těchto koncových bodů tak, aby klienti mohli vyladit hledání. Pro druhý koncový bod je možné zjistitelnost zakázat nastavením vlastnosti <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> na `false`. Tím se zajistí, že se metadata zjišťování přidružená k tomuto koncovému bodu neodesílají jako součást jakýchkoli zpráv zjišťování.

## <a name="client-features"></a>Klientské funkce

Metoda `FindCalculatorServiceAddress()` ukazuje, jak použít <xref:System.ServiceModel.Discovery.DiscoveryClient> a předat <xref:System.ServiceModel.Discovery.FindCriteria> se dvěma omezeními. Do kritérií je přidán obor a vlastnost <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> je nastavena na hodnotu 1. Rozsah omezuje výsledky jenom na služby, které publikují stejný obor. Nastavení <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> na 1 omezuje odezvy, které <xref:System.ServiceModel.Discovery.DiscoveryClient> čeká na až 1 koncový bod. <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> volání je synchronní operace, která blokuje vlákno, dokud není dosažen časový limit nebo byl nalezen jeden koncový bod.

### <a name="to-use-this-sample"></a>Použití této ukázky

1. Tato ukázka používá koncové body HTTP a ke spuštění této ukázky musí být přidány správné seznamy ACL adres URL. Podrobnosti najdete v tématu [Konfigurace HTTP a HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) . Spuštění následujícího příkazu u zvýšeného oprávnění by mělo přidat příslušné seznamy ACL. Pokud příkaz nefunguje tak, jak je, můžete chtít nahradit doménu a uživatelské jméno pro následující argumenty: `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. Sestavte řešení.

3. Spusťte spustitelný soubor služby z adresáře buildu.

4. Spusťte klientský spustitelný soubor. Upozorňujeme, že klient může službu vyhledat.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryWithScopes`
