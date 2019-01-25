---
title: Ukázka zjišťování pomocí oborů
ms.date: 03/30/2017
ms.assetid: 6a37a754-6b8c-4ebe-bdf2-d4f0520271d5
ms.openlocfilehash: 0d874116b90f423fbb78803a3641ef55fc848952
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54508766"
---
# <a name="discovery-with-scopes-sample"></a>Ukázka zjišťování pomocí oborů
Tento příklad ukazuje, jak pomocí oborů zařadit zjistitelné koncových bodů i jak používat <xref:System.ServiceModel.Discovery.DiscoveryClient> provést asynchronní hledání pro koncové body. Ve službě Tato ukázka předvádí, jak přizpůsobit přidáním chování koncového bodu zjišťování a pomocí přidání oboru ke koncovému bodu, stejně jako řízení zjistitelnost koncového bodu zjišťování pro každý koncový bod. Na straně klienta překročí jak můžou klienti vytvořit ukázky <xref:System.ServiceModel.Discovery.DiscoveryClient> a doladit parametry patří oborů tak, že přidáte obory pro hledání <xref:System.ServiceModel.Discovery.FindCriteria>. Tento příklad také ukazuje, jak klienti odpovědi omezit tak, že přidáte ukončovacího kritéria.  
  
## <a name="service-features"></a>Funkce služby  
 Ukazuje dva koncové body služby se přidávají do tohoto projektu <xref:System.ServiceModel.ServiceHost>. Každý koncový bod má <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> s ním spojená. Toto chování slouží k přidání identifikátoru URI oborů pro oba koncové body. Obory slouží k odlišení každý z těchto koncových bodů tak, aby klienti uživatele můžete podrobně upravit vyhledávání. Pro druhý koncový bod, zjistitelnost lze zakázat nastavením <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> vlastnost `false`. Tím se zajistí, že jako součást všechny zprávy zjišťování nejsou zasílány zjišťování metadata přidružená k tomuto koncovému bodu.  
  
## <a name="client-features"></a>Funkce klienta  
 `FindCalculatorServiceAddress()` Metoda ukazuje způsob použití <xref:System.ServiceModel.Discovery.DiscoveryClient> a předejte mu <xref:System.ServiceModel.Discovery.FindCriteria> dvě omezení. Rozsah je přidán do kritéria a <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> je nastavena na 1. Rozsah omezuje výsledky do služeb, které publikují ve stejném rozsahu. Nastavení <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> 1 omezuje odpovědi <xref:System.ServiceModel.Discovery.DiscoveryClient> čeká na maximálně 1 koncový bod. <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> Volání je asynchronní operace, která blokuje vlákno, dokud nebude dosaženo časového limitu nebo se nachází jeden koncový bod.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Tato ukázka používá koncové body HTTP a pokud chcete tuto ukázku spustit, musíte přidat správné seznamy ACL adresy URL. Zobrazit [konfigurace HTTP a HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) podrobnosti. Provádění se zvýšenými oprávněními následující příkaz by měl přidat příslušné seznamy ACL. Můžete nahradit doména a uživatelské jméno pro následující argumenty, pokud příkaz nefunguje, jako je: `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Sestavte řešení.  
  
3.  Spusťte spustitelný soubor služby z adresáře sestavení.  
  
4.  Spusťte klientský spustitelný soubor. Všimněte si, že se najít službu klienta.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryWithScopes`  
  
## <a name="see-also"></a>Viz také:
