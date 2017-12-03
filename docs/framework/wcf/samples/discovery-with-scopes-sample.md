---
title: "Ukázka zjišťování pomocí oborů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a37a754-6b8c-4ebe-bdf2-d4f0520271d5
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 184c4a5c31969ee060f72d937ab02af733340ca4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="discovery-with-scopes-sample"></a>Ukázka zjišťování pomocí oborů
Tento příklad ukazuje způsob použití obory zařadit do kategorií zjistitelný koncových bodů a jak používat <xref:System.ServiceModel.Discovery.DiscoveryClient> pro asynchronní vyhledávání pro koncové body. Tato ukázka na službu, ukazuje, jak přizpůsobit přidáním koncový bod zjišťování chování a jej použijete k přidání oboru ke koncovému bodu, stejně jako řízení možnosti rozpoznání pro koncový bod zjišťování pro každý koncový bod. Na straně klienta vzorku prochází přes jak klienti mohou vytvářet <xref:System.ServiceModel.Discovery.DiscoveryClient> a optimalizovat vyhledávání parametry, které zahrnují obory přidáním oborů, které chcete <xref:System.ServiceModel.Discovery.FindCriteria>. Tento příklad také ukazuje, jak klienti může omezit odpovědi přidáním kritéria ukončení.  
  
## <a name="service-features"></a>Funkce služby  
 Tento projekt ukazuje, který se přidává do dva koncové body služby <xref:System.ServiceModel.ServiceHost>. Každý koncový bod má <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> s ním spojená. Toto chování se používá k přidání identifikátoru URI obory pro oba koncové body. Obory slouží k rozlišení každý z těchto koncových bodů tak, aby klienti můžete vyladit hledání. Pro druhý koncový bod, zjistitelnost lze zakázat pomocí nastavení <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> vlastnost `false`. Tím se zajistí, že zjišťování metadat přidružené k tomuto koncovému bodu se neposílají jako součást všechny zprávy zjišťování.  
  
## <a name="client-features"></a>Klientských funkcí  
 `FindCalculatorServiceAddress()` Metoda ukazuje způsob použití <xref:System.ServiceModel.Discovery.DiscoveryClient> a předat <xref:System.ServiceModel.Discovery.FindCriteria> dvě omezení. Obor se přidá do kritéria a <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> je nastavena na hodnotu 1. Obor omezí výsledky do pouze služby, které publikovat stejný obor. Nastavení <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> 1 omezením odpovědi <xref:System.ServiceModel.Discovery.DiscoveryClient> čeká na, maximálně 1 koncový bod. <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> Volání je synchronní operace, které blokuje vlákno, dokud nebude dosaženo časového limitu nebo byl nalezen jeden koncový bod.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Tato ukázka používá koncových bodů protokolu HTTP a pokud chcete tuto ukázku spustit, musí být přidán správné seznamy ACL adresy URL. V tématu [konfigurace HTTP a HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) podrobnosti. Spuštěním následujícího příkazu na zvýšená oprávnění měli přidat příslušné seznamy ACL. Můžete nahradit domény a uživatelské jméno pro následující argumenty, pokud příkaz nefunguje, jako je:`netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Sestavte řešení.  
  
3.  Spusťte spustitelný soubor služby z adresáře sestavení.  
  
4.  Spustíte spustitelný soubor klienta. Všimněte si, že klient je schopna zjistit službu.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryWithScopes`  
  
## <a name="see-also"></a>Viz také
