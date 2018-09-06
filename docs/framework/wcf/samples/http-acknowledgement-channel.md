---
title: Kanál potvrzení HTTP
ms.date: 03/30/2017
ms.assetid: 469f3056-5ef2-4753-8acf-b574d23d83cf
ms.openlocfilehash: d83f3aa590471aa3d83b8f7bd1464ec1e6e106fc
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856229"
---
# <a name="http-acknowledgement-channel"></a>Kanál potvrzení HTTP
Kanál potvrzení HTTP je příkladem vrstvami kanál, který změní vzoru jednosměrné zasílání zpráv, umožňující potvrdit nebo udělit příchozí zprávy a nikoli automaticky odešle oznámení o potvrzení. Kanál potvrzení HTTP taky umožňuje službě potvrzení zpoždění, dokud může být, že se zpracování zprávy se zárukou firemní úrovni.  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.ServiceModel.Channels.ReceiveContext>, Příklad vrstvami kanálu (kanál potvrzení HTTP).  
  
## <a name="discussion"></a>Diskuse  
 Kanál potvrzení HTTP implementuje <xref:System.ServiceModel.Channels.ReceiveContext> tvaru vzorce zasílání zpráv žádost odpověď HTTP jednosměrné vzoru s zpožděných potvrzení. Pomocí tohoto nového modelu služby můžete zajistit zpracování zpráv tím, že odešle oznámení ve formě stavový kód HTTP OK 200 neblokoval klienta, dokud dokončí zpracování zprávy nebo můžete odeslat zprávu selhání klienta v podobě protokolu HTTP Interní Server chyba stavový kód 500. Služba může například odeslání potvrzení po zápisu zprávy do fronty a potom pokračovat ve zpracovávání zprávy asynchronně. V tomto scénáři klient může být jistí, že zprávy se zpracuje alespoň jednou službou, pokud ho opětovné odeslání každou zprávu, dokud se potvrzení přijatých ze služby. Všimněte si, že pokud služba vyžaduje rychlé asynchronních zpráv zpracování přes protokol HTTP bez jakékoli zprávy zpracování záruky, pak bude <xref:System.ServiceModel.Channels.OneWayBindingElement> je vhodnější volbou.  
  
 <xref:System.ServiceModel.Channels.ReceiveContext> slouží k uložení zprávy na místě, zatímco se určuje, zda může být zpráva zpracována na službu. Schopnost služby zprávu úspěšně zpracovat je označen pomocí funkce dokončit <xref:System.ServiceModel.Channels.ReceiveContext> objekt, který odesílá stavový kód HTTP OK a určuje, zda služba může zpracovat zprávy je indikován volání <xref:System.ServiceModel.Channels.ReceiveContext>společnosti `Abandon` Metoda <xref:System.ServiceModel.Channels.ReceiveContext> objektu, který odešle kód stavu HTTP Server s interní chyby.  
  
 V tomto příkladu si klient vyžádá informace o zpracování odesláním identifikátor zaměstnance. Na straně služby Pokud ID zaměstnance přijatých je větší než 50, služba odesílá zpět do klienta kód stavu HTTP 500 (vnitřní chyba serveru), v opačném případě se předpokládá, že zpracování může probíhat úspěšně a odešle kód stavu HTTP 200 ( Úspěšné) do klienta.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Otevřít [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] s oprávněními správce.  
  
2.  Otevřít **HttpAckChannel** řešení.  
  
3.  Spustit novou instanci třídy **služby** projektu kliknutím pravým tlačítkem myši na **Průzkumníka řešení**a výběrem **ladění**, **zahájit novou instanci** v místní nabídce.  
  
4.  Spustit novou instanci třídy **klienta** projektu kliknutím pravým tlačítkem myši na **Průzkumníka řešení**a výběrem **ladění**, a **zahájit novou instanci** v místní nabídce.  
  
5.  Po zahájení službu stisknutím klávesy ENTER v okně klienta umožňuje klientovi odeslat zprávu do služby.  
  
6.  První zpráva se zpracuje ve službě a odešle stavový kód HTTP OK zpět do klienta.  
  
7.  Druhá zpráva neproběhne úspěšně, a odešle zpět klientovi, který vyvolá kód stavu HTTP Server s interní chyby <xref:System.ServiceModel.CommunicationException> na straně klienta.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpAckChannel`
