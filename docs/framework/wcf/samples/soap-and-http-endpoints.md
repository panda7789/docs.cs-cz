---
title: Koncové body SOAP a HTTP
ms.date: 03/30/2017
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
ms.openlocfilehash: f10b1aa4514aee50c0c0d17cabdb9516a3ca7584
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144016"
---
# <a name="soap-and-http-endpoints"></a>Koncové body SOAP a HTTP
Tato ukázka ukazuje, jak implementovat službu založenou na vzdáleném volání procedur a vystavit ji ve formátu SOAP a formátu "Plain Old XML" (POX) pomocí modelu wcf webového programovacího modelu. Další podrobnosti o vazbě HTTP pro službu naleznete v ukázce [základní služby HTTP.](../../../../docs/framework/wcf/samples/basic-http-service.md) Tato ukázka se zaměřuje na podrobnosti, které se jedná o vystavení stejné služby přes SOAP a HTTP pomocí různých vazeb.  
  
## <a name="demonstrates"></a>Demonstruje  
 Vystavení služby RPC přes SOAP a HTTP pomocí WCF.  
  
## <a name="discussion"></a>Diskuse  
 Tato ukázka se skládá ze dvou součástí: projekt webové aplikace (Service), který obsahuje službu WCF a konzolové aplikace (Client), která vyvolá operace služby pomocí soap a HTTP vazby.  
  
 Služba WCF zpřístupňuje`GetData` 2 `PutData` operace – a – že echo řetězec, který byl předán jako vstup. Servisní operace jsou anotovány <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute>s a . Tyto atributy řídí projekci HTTP těchto operací. Kromě toho jsou anotovány <xref:System.ServiceModel.OperationContractAttribute>s , což umožňuje, aby byly vystaveny přes SOAP vazby. `PutData` Metoda služby vyvolá <xref:System.ServiceModel.Web.WebFaultException>, který získá odeslána zpět přes HTTP pomocí stavového kódu HTTP a získá odeslána zpět přes SOAP jako chyba SOAP.  
  
 Soubor Web.config konfiguruje službu WCF se 3 koncovými body:  
  
- Koncový bod ~/service.svc/mex, který zveřejňuje metadata služby pro přístup klienty založené na soap.  
  
- Koncový bod ~/service.svc/http, který umožňuje klientům přístup ke službě pomocí vazby HTTP.  
  
- Koncový bod ~/service.svc/soap, který umožňuje klientům přístup ke službě pomocí vazby SOAP přes HTTP.  
  
 Koncový bod HTTP je konfigurován `webHttp` s <> `helpEnabled` standardní `true`koncový bod, který je nastaven na . V důsledku toho služba zpřístupňuje stránku nápovědy založené na XHTML na adrese ~/service.svc/http/help, kterou mohou klienti se systémem HTTP použít pro přístup ke službě.  
  
 Klientský projekt demonstruje přístup ke službě pomocí serveru PROXY SOAP (generovaného <xref:System.Net.WebClient>pomocí add service **reference)** a přístupu ke službě pomocí .  
  
 Ukázka se skládá z web-hostované služby a konzolové aplikace. Při spuštění aplikace konzoly klient provádí požadavky na službu a zapisuje relevantní informace z odpovědí do okna konzoly.  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1. Otevřete řešení pro ukázku koncových bodů SOAP a HTTP.  
  
2. Stisknutím kláves CTRL+SHIFT+B řešení sestavíte.  
  
3. Pokud ještě není otevřená, otevřete okno **Průzkumníka řešení** stisknutím kombinace kláves CTRL+W, S.  
  
4. V okně **Průzkumník řešení** klepněte pravým tlačítkem myši na projekt **služby** a umístěte kurzor nad možnost kontextové nabídky **Ladění,** aby se zobrazila kontextová nabídka **Spustit novou instanci.** Klepněte na tlačítko **Spustit novou instanci**. Tím se spustí ASP.NET vývojový server, který je hostitelem služby.  
  
5. V oknech Průzkumníka řešení klepněte pravým tlačítkem myši na projekt Klient a umístěte kurzor nad možnost **kontextové** nabídky Ladění, aby se zobrazila kontextová nabídka **Spustit novou instanci.** Klepněte na tlačítko **Spustit novou instanci**.  
  
6. Zobrazí se okno klientské konzole a zobrazí identifikátor URI spuštěné služby a identifikátor URI na stránce nápovědy HTML pro spuštěnou službu. Kdykoli můžete zobrazit stránku nápovědy HTML zadáním identifikátoru URI stránky nápovědy v prohlížeči.  
  
7. Při spuštění ukázky klient zapíše stav aktuální aktivity.  
  
8. Stisknutím libovolné klávesy ukončete aplikaci klientské konzoly.  
  
9. Stisknutím kláves SHIFT+F5 zastavíte ladění služby.  
  
10. V oznamovací oblasti systému Windows klepněte pravým tlačítkem myši na ikonu ASP.NET vývojového serveru a z kontextové nabídky vyberte **zastavit.**  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
