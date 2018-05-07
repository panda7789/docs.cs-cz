---
title: Podmíněné operace Get a Put
ms.date: 03/30/2017
ms.assetid: 3d22067f-57b8-4e0f-a571-a694512187ae
ms.openlocfilehash: f2d170da80de1186aa41b4821da52d58a0bb0e0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="conditional-get-and-put"></a>Podmíněné operace Get a Put
Tento příklad znázorňuje, jak používat nové podmíněného načtení a aktualizace rozhraní API pro programovací model WCF REST. Protože podmíněného načtení a aktualizace jsou nejvhodnější pro orientované prostředků a rozšiřuje služby REST, tato ukázka [základní služba prostředků](../../../../docs/framework/wcf/samples/basic-resource-service.md) ukázka. Tato ukázka se zaměřuje na přidání podpory pro podmíněné načtení a proveďte aktualizaci [základní služba prostředků](../../../../docs/framework/wcf/samples/basic-resource-service.md) ukázkové pomocí nových rozhraní API byla zavedená v [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].  
  
## <a name="demonstrates"></a>Demonstruje  
 Podmíněné načtení a aktualizace  
  
## <a name="discussion"></a>Diskusní  
 Služby WCF v této ukázce zpřístupní kolekce zákazníků v orientované prostředků a REST způsobem. Podrobný popis implementace služby, najdete v tématu [základní služba prostředků](../../../../docs/framework/wcf/samples/basic-resource-service.md) ukázka.  
  
 Tato ukázka přidá podmíněného načtení a aktualizace funkcí [základní služba prostředků](../../../../docs/framework/wcf/samples/basic-resource-service.md) ukázka. Podmíněné načítají a aktualizují pomocí značek entit HTTP a hlavičky protokolu HTTP If-None-Match a If-Match k ověření, že klienti mají, nebo nemáte nejaktuálnější entity pro daný prostředek. Ale implementace kód správně analyzovat hlavičky protokolu HTTP If-None-Match a If-Match může být zdlouhavé a náchylné k chybě. Proto <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> a <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> metody jsou přidané do <xref:System.ServiceModel.Web.IncomingWebRequestContext>, který lze přistupovat pomocí aktuální instancí třídy <xref:System.ServiceModel.Web.WebOperationContext>. Kromě toho `SetETag` metoda byl přidán do <xref:System.ServiceModel.Web.OutgoingWebRequestContext>, snadněji vrátit značek platný entit.  
  
 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> Metoda je určena pro použití s operacemi [WebGet]. Jak dlouho trvá aktuální značce entity pro daný prostředek, jako `entityTag` parametr, který může být `string`, `int`, `long` nebo `Guid`. <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> Metoda zkontroluje značky entity proti hlavičku protokolu HTTP If-None-Match požadavku. Pokud je k dispozici v hlavičce protokolu HTTP If-None-Match značky entity pak <xref:System.ServiceModel.Web.WebFaultException> stavem je vyvolána kód nedojde ke změně (304); jinak vrátí metoda. Tento mechanismus podmíněného načtení umožňuje klientovi sdělíte serveru, který obsahuje tuto entitu a odeslat pouze aktuální entity, pokud klient již nemá ho. Příklad použití <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> metoda si můžete prohlédnout ve `GetCustomer` a `GetCustomers` operace služby. Je důležité si uvědomit, který volá, aby se <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> nemusí vracet. Vývojáři měli implementovat operaci tak, že požadavek je již znám úspěšný před voláním <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> prováděny, například že pokud volání <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> nejsou k dispozici, služba by odeslání odpovědi se úspěšně stavovým kódem.  
  
 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> Metoda je podobná <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> metoda. Také trvá aktuální značce entity pro daný prostředek. Je však určena pro použití s operací [WebInvoke], ve kterých je metoda nastavena na "PUT" nebo "Odstranit". <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> Metoda zkontroluje značky entity proti hlavičku protokolu HTTP If-Match požadavku. Pokud není k dispozici v hlavičce protokolu HTTP If-Match značky entity pak <xref:System.ServiceModel.Web.WebFaultException> stavem je vyvolána kód předběžnou se nezdařilo (412). Mechanismus podmíněného aktualizace umožňuje klientovi sdělíte serveru, zda má tento entity pro daný prostředek a povolit pouze klienta ke změně prostředku. Pokud má entita je aktuální. Příklad použití <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> metoda si můžete prohlédnout ve `UpdateCustomer` a `DeleteCustomer` operace služby. Jenom jako s <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A>, je důležité si uvědomit, který volá, aby se <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> nemusí vracet. Vývojáři měli implementovat operaci tak, že požadavek je již znám úspěšný před voláním <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> prováděny, například pokud volání <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> nebyly k dispozici, služba by odpovídat úspěšné stavový kód.  
  
 Ukázkový soubor obsahuje služba s vlastním hostováním a klienta, který běží v konzolové aplikaci. Konzolové aplikace běží, klient odešle žádosti o službu a zapisuje příslušné informace z odpovědi do okna konzoly.  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Otevřete řešení pro ukázku podmíněného Get a Put. Při spouštění [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], musíte spustit jako správce a ukázku úspěšně vykonat. To můžete provést kliknutím pravým tlačítkem myši [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ikonu a výběr **spustit jako správce** v místní nabídce.  
  
2.  Stisknutím kombinace kláves CTRL + SHIFT + B sestavte řešení a potom stiskněte klávesu CTRL + F5 a spusťte projekt konzolové aplikace. Pokud se tento projekt službou ladění povoleno (stisknutím klávesy F5 místo CTRL + F5), ladicí program zastaví, pokud je vyvolána výjimka, pomocí zásad správy GET a PUT kontrola. Pokud k tomu dojde, stisknutím klávesy F5 pokračovat v provádění vzorku.  
  
3.  V okně konzoly zobrazí písku poskytuje identifikátor URI spuštěné služby a identifikátor URI na stránce nápovědy HTML pro spuštěné služby.  
  
4.  Ukázka běží, klient odešle požadavky do služby a zapíše odpovědi do okna konzoly.  
  
5.  Stisknutím libovolné klávesy ukončit vzorku.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\ConditionalGetAndPut`
