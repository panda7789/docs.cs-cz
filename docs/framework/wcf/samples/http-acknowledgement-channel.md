---
title: "Kanál potvrzení HTTP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 469f3056-5ef2-4753-8acf-b574d23d83cf
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d07a17c5ed4302657671e0247e44ac0ef6e75518
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="http-acknowledgement-channel"></a>Kanál potvrzení HTTP
Kanál potvrzení HTTP je příkladem vrstveného kanálu, který změní jednosměrný vzorcem zasílání zpráv, povolení služby vědomí nebo odmítnout příchozí zprávy místo automaticky odesláno potvrzení na potvrzení. Kanál potvrzení HTTP také umožňuje službě potvrzení zpoždění, dokud mohl zajistit firemní úrovni záruku, že dojde ke zpracování zprávy.  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.ServiceModel.Channels.ReceiveContext>, Příklad vrstveného kanál (kanál potvrzení HTTP).  
  
## <a name="discussion"></a>Diskusní  
 Kanál potvrzení HTTP implementuje <xref:System.ServiceModel.Channels.ReceiveContext> ke změně tvaru požadavku a odpovědi HTTP o zasílání zpráv vzor jednosměrný vzor s zpožděné potvrzení. Pomocí této nové vzoru, služby můžete zajistit zpracování zprávy odesláním potvrzení ve formě stavový kód HTTP OK 200 bez blokování klienta, dokud dokončí zpracování zprávy nebo můžete odeslat zprávu selhání klientovi ve formátu protokolu HTTP Interní Server stavový kód chyby 500. Například služby může odesílat potvrzení po napsání zprávu do fronty a poté pokračujte zpracování zprávy asynchronně. V tomto scénáři klienta může být jistí, že jeho zprávy se zpracuje alespoň jednou službou, pokud ji znovu odeslat každou zprávu, dokud ho potvrzení přijal od služby. Všimněte si, že, pokud služba vyžaduje, aby rychlého asynchronní zprávu zpracování přes protokol HTTP, bez jakékoli zprávy zpracování záruky, pak se <xref:System.ServiceModel.Channels.OneWayBindingElement> je vhodnější volbou.  
  
 <xref:System.ServiceModel.Channels.ReceiveContext>slouží k uchování zprávy na místě, když je zjištěno, zda může být zpráva zpracována na službu. Uvedené schopnost služby úspěšně zpracovat zprávu voláním Complete na <xref:System.ServiceModel.Channels.ReceiveContext> objekt, který odesílá stavový kód HTTP OK a zda služba může zpracovat zprávu je indikován volání <xref:System.ServiceModel.Channels.ReceiveContext>na `Abandon` Metoda na <xref:System.ServiceModel.Channels.ReceiveContext> objekt, který odesílá chybový kód stavu HTTP interního serveru.  
  
 V tomto příkladu klient požádá informace zpracování odesláním identifikátor zaměstnance. Na konci služby Pokud ID zaměstnance přijatých je vyšší než 50, služba odesílá kód stavu HTTP 500 (vnitřní chyba serveru) zpět do klienta, jinak se předpokládá, že lze úspěšně provést zpracování a odešle kód stavu HTTP 200 ( Úspěšné) na klientovi.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Otevřete [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] s oprávněními správce.  
  
2.  Otevřete **HttpAckChannel** řešení.  
  
3.  Spusťte novou instanci třídy **služby** projektu kliknutím pravým tlačítkem na projekt v **Průzkumníku řešení**a výběr **ladění**, **spustit novou instanci** v místní nabídce.  
  
4.  Spusťte novou instanci třídy **klienta** projektu kliknutím pravým tlačítkem na projekt v **Průzkumníku řešení**a výběr **ladění**, a **spustit novou instanci** v místní nabídce.  
  
5.  Jakmile služba spuštěna, stiskněte klávesu ENTER v okně klienta k odeslání zprávy do služby klienta.  
  
6.  Zpracování první zprávu ve službě, a odešle stavový kód HTTP OK zpět do klienta.  
  
7.  O druhou zprávu úspěšná a odešle chybový kód stavu HTTP interního serveru zpět do klienta, které vyvolá <xref:System.ServiceModel.CommunicationException> na straně klienta.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpAckChannel`
