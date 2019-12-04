---
title: Koncové body SOAP a HTTP
ms.date: 03/30/2017
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
ms.openlocfilehash: 93f410b8b8632b0158d0a52b12845f1e8cec132c
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716686"
---
# <a name="soap-and-http-endpoints"></a>Koncové body SOAP a HTTP
Tato ukázka předvádí, jak implementovat službu pomocí protokolu RPC a zveřejnit ji ve formátu SOAP a ve formátu "obyčejného starého XML" (POX) pomocí modelu webového programování WCF. Další podrobnosti o vazbě HTTP pro službu najdete v ukázce [základní služby http](../../../../docs/framework/wcf/samples/basic-http-service.md) . Tato ukázka se zaměřuje na podrobnosti, které se vztahují k vystavení stejné služby prostřednictvím protokolu SOAP a protokolu HTTP pomocí různých vazeb.  
  
## <a name="demonstrates"></a>Demonstruje  
 Vystavení služby RPC přes SOAP a HTTP pomocí WCF.  
  
## <a name="discussion"></a>Účely  
 Tato ukázka se skládá ze dvou součástí: projektu webové aplikace (služba), který obsahuje službu WCF a konzolovou aplikaci (klient), která vyvolá operace služby pomocí vazeb SOAP a HTTP.  
  
 Služba WCF zpřístupňuje 2 operace –`GetData` a `PutData` – vyecho řetězec, který byl předán jako vstup. Operace služby jsou opatřeny poznámkou <xref:System.ServiceModel.Web.WebGetAttribute> a <xref:System.ServiceModel.Web.WebInvokeAttribute>. Tyto atributy řídí projekci HTTP těchto operací. Kromě toho jsou opatřeny poznámkami <xref:System.ServiceModel.OperationContractAttribute>, což umožňuje jejich zpřístupnění prostřednictvím vazeb SOAP. Metoda `PutData` služby vyvolá <xref:System.ServiceModel.Web.WebFaultException>, která se pošle zpátky přes HTTP pomocí kódu stavu HTTP a pošle zpátky přes SOAP jako chybu SOAP.  
  
 Soubor Web. config konfiguruje službu WCF se 3 koncovými body:  
  
- Koncový bod ~/Service.svc/mex, který zpřístupňuje metadata služby pro přístup klientů založených na protokolu SOAP.  
  
- Koncový bod ~/Service.svc/http, který klientům umožňuje přístup ke službě pomocí vazby HTTP.  
  
- Koncový bod ~/Service.svc/SOAP, který klientům umožňuje přístup ke službě pomocí vazby SOAP přes HTTP.  
  
 Koncový bod HTTP je nakonfigurovaný pomocí <`webHttp`> standardní koncový bod, který má `helpEnabled` nastavené na `true`. Výsledkem je, že služba zpřístupňuje stránku s podporou standardu XHTML na adrese ~/Service.svc/http/Help, kterou mohou klienti využívající protokol HTTP použít pro přístup ke službě.  
  
 Klientský projekt ukazuje přístup ke službě pomocí proxy protokolu SOAP (vygenerovaného prostřednictvím **Přidat odkaz na službu**) a přístupu ke službě pomocí <xref:System.Net.WebClient>.  
  
 Ukázka se skládá z webové služby a konzolové aplikace. Při spuštění konzolové aplikace klient provede požadavky na službu a zapíše příslušné informace z odpovědí do okna konzoly.  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1. Otevřete řešení ukázky pro koncové body SOAP a HTTP.  
  
2. Stisknutím kombinace kláves CTRL + SHIFT + B Sestavte řešení.  
  
3. Pokud ještě není otevřený, otevřete okno **Průzkumník řešení** stisknutím kombinace kláves CTRL + W, s.  
  
4. V okně **Průzkumník řešení** klikněte pravým tlačítkem myši na projekt **služby** a umístěte kurzor na možnost místní nabídky **ladění** , aby se zobrazila místní nabídka **spustit novou instanci** . Klikněte na **spustit novou instanci**. Tím se spustí vývojový server ASP.NET, který je hostitelem služby.  
  
5. Z okna Průzkumník řešení klikněte pravým tlačítkem myši na projekt klienta a umístěte kurzor na možnost místní nabídky **ladění** , aby se zobrazila místní nabídka **spustit novou instanci** . Klikněte na **spustit novou instanci**.  
  
6. Zobrazí se okno Konzola klienta, ve kterém je uveden identifikátor URI běžící služby a identifikátor URI stránky s nápovědu HTML pro běžící službu. V jakémkoli okamžiku můžete zobrazit stránku HTML Help zadáním identifikátoru URI stránky s nastavením v prohlížeči.  
  
7. Po spuštění ukázkového klienta zapíše klient stav aktuální aktivity.  
  
8. Stisknutím libovolné klávesy ukončete konzolovou aplikaci klienta.  
  
9. Stisknutím SHIFT + F5 zastavíte ladění služby.  
  
10. V oznamovací oblasti systému Windows klikněte pravým tlačítkem myši na ikonu vývojového serveru ASP.NET a v místní nabídce vyberte možnost **zastavit** .  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
