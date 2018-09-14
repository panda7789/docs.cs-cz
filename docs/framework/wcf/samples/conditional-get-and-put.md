---
title: Podmíněné operace Get a Put
ms.date: 03/30/2017
ms.assetid: 3d22067f-57b8-4e0f-a571-a694512187ae
ms.openlocfilehash: 29819f89327128cdd71cc89eb8d14126522dc2df
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45595120"
---
# <a name="conditional-get-and-put"></a>Podmíněné operace Get a Put
Tento příklad znázorňuje způsob použití nového podmíněné načíst a aktualizovat rozhraní API pro programovací model WCF REST. Protože podmíněné načtení a aktualizace jsou nejvhodnější pro založenému na záznamech prostředků a služeb REST, tento příklad rozšiřuje [služba základních prostředků](../../../../docs/framework/wcf/samples/basic-resource-service.md) vzorku. Tato ukázka se zaměřuje na přidání podpory pro podmíněné načtení a proveďte aktualizaci [služba základních prostředků](../../../../docs/framework/wcf/samples/basic-resource-service.md) ukázkový pomocí nových rozhraní API zavedený [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].  
  
## <a name="demonstrates"></a>Demonstruje  
 Podmíněné načtení a aktualizace  
  
## <a name="discussion"></a>Diskuse  
 Služby WCF v této ukázce poskytuje kolekci zákazníků v záznamech prostředků a způsobem REST. Podrobný popis implementace služby, najdete v tématu [služba základních prostředků](../../../../docs/framework/wcf/samples/basic-resource-service.md) vzorku.  
  
 Tato ukázka přidá podmíněný načtení a funkce aktualizace pro [služba základních prostředků](../../../../docs/framework/wcf/samples/basic-resource-service.md) vzorku. Podmíněné načítají a aktualizují použití značek entit HTTP a hlaviček protokolu HTTP If-None-Match a If-Match se ověřit, že klienti mají, nebo nemají aktuální entity pro daný prostředek. Ale implementace kódu správně analyzovat záhlaví HTTP If-None-Match a If-Match může být zdlouhavé a náchylné k chybě. Proto <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> a <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> metody byly přidány do <xref:System.ServiceModel.Web.IncomingWebRequestContext>, které lze přistupovat pomocí aktuální instancí třídy <xref:System.ServiceModel.Web.WebOperationContext>. Kromě toho `SetETag` metoda byl přidán do <xref:System.ServiceModel.Web.OutgoingWebRequestContext>, což usnadňuje nevrátilo značky platný entity.  
  
 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> Metoda je určena pro použití s operacemi [WebGet]. Trvá, než aktuální značku entity pro daný prostředek, jako `entityTag` parametr, který může být `string`, `int`, `long` nebo `Guid`. <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> Metoda zkontroluje značka entity proti záhlaví HTTP If-None-Match požadavku. Pokud je k dispozici v hlavičce protokolu HTTP If-None-Match značka entity o <xref:System.ServiceModel.Web.WebFaultException> se stavem je vyvolána kód nedojde ke změně (304); v opačném případě vrátí metoda. Podmíněné načtení mechanismus umožňuje klientovi sdělíte serveru, že na něm tuto entitu a pokud klient již nemá ji odeslat pouze aktuální entitu. Příklad použití <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> metoda si můžete prohlédnout ve `GetCustomer` a `GetCustomers` operace služby. Je důležité si uvědomit, která volá do <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> nesmí vracet. Vývojáři by měly implementovat operace tak, že žádost je již znám k dosažení úspěchu před voláním <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> je provedeno, například, že pokud volání <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> není k dispozici, služba bude posílat odpovědi úspěšné stavovým kódem.  
  
 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> Metoda je podobná <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> metody. Také využívá aktuální značku entity pro daný prostředek. Ale je určena pro použití s [WebInvoke] operace, ve kterých je metoda nastavena na "Vložit" nebo "Odstranit". <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> Metoda zkontroluje značka entity proti záhlaví HTTP If-Match požadavku. Pokud není k dispozici v hlavičce protokolu HTTP If-Match značka entity o <xref:System.ServiceModel.Web.WebFaultException> se stavem kód Předběžná podmínka je neplatná (412) je vyvolána výjimka. Aktualizace podmíněného mechanismus umožňuje klientovi sdělíte serveru, má tato entita pro prostředek a povolit pouze klienta ke změně prostředku. Pokud má entita je aktuální. Příklad použití <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> metoda si můžete prohlédnout ve `UpdateCustomer` a `DeleteCustomer` operace služby. Stejně jako u <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A>, je důležité si uvědomit, která volá do <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> nesmí vracet. Vývojáři by měly implementovat operace tak, že žádost je již znám k dosažení úspěchu před voláním <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> je provedeno, například, že pokud volání <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> nebyl k dispozici, služba by odpovědět úspěšné stavovým kódem.  
  
 Ukázka se skládá z služba v místním prostředí a klienta, který běží v rámci konzolové aplikace. Konzolová aplikace běží, klient vytvářejí požadavky na službu a zapíše relevantní informace z odpovědi v okně konzoly.  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Otevřete řešení pro ukázku podmíněné Get a Put. Při spuštění [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], musíte spustit jako správce a spusťte ukázku úspěšně. To můžete provést kliknutím pravým tlačítkem myši [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ikonu a zvolíte **spustit jako správce** v místní nabídce.  
  
2.  Stiskněte kombinaci kláves CTRL + SHIFT + B, sestavte řešení a pak stisknutím kombinace kláves CTRL + F5 spusťte projekt konzolové aplikace. Pokud spuštění tohoto projektu se ladění povoleno (stisknutím klávesy F5 místo CTRL + F5), ladicí program chvíle, kdy je vyvolána výjimka, pomocí zásad správy GET a PUT, kontrola. Pokud k tomu dojde, stisknutím klávesy F5 pokračovat v provádění vzorku.  
  
3.  V okně konzoly se zobrazí písek obsahuje identifikátor URI spuštěnou službu a identifikátor URI na stránce nápovědy HTML pro spuštěnou službu.  
  
4.  Při spuštění ukázky, klient zasílá požadavky službě a zapíše odpovědi v okně konzoly.  
  
5.  Stisknutím libovolné klávesy ukončete vzorovou.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\ConditionalGetAndPut`
