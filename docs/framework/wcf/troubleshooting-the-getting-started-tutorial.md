---
title: "Odstraňování problémů v kurzu Začínáme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 55288074b35bcb00d6c6b453f1320ad40d26a5f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-the-getting-started-tutorial"></a>Odstraňování problémů v kurzu Začínáme
Toto téma uvádí nejběžnější problémy vzniklé při práci prostřednictvím kurzu Začínáme a způsob jejich řešení.  
  
1.  [Nedaří se mi najít soubory projektu na pevném disku.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q1)  
  
2.  [Probíhá pokus o spuštění služby aplikace: HTTP nebylo možné zaregistrovat http://+:8000/ServiceModelSamples/Service/ adresy URL. Váš proces nemá přístupová práva na tento obor názvů.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q2)  
  
3.  [Pokus o použití nástroje Svcutil.exe: 'svcutil' nebyl rozpoznán jako vnitřního ani vnějšího příkazu, spustitelného programu nebo dávkového souboru.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q3)  
  
4.  [Nepodařilo se najít soubor App.config generované Svcutil.exe.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q4)  
  
5.  [Kompilování klientská aplikace: 'CalculatorClient' neobsahuje definici '&lt;název metody&gt;'a žádná metoda rozšíření'&lt;název metody&gt;' přijímající první argument typu 'CalculatorClient. nebyla nalezena (chybějící using – direktiva nebo odkaz na sestavení?)](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q5)  
  
6.  [Kompilování klientská aplikace: typu nebo oboru názvů 'CalculatorClient' nebyl nalezen (chybějící using – direktiva nebo odkaz na sestavení?)](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q6)  
  
7.  [Spuštění klienta: neošetřená výjimka: System.ServiceModel.EndpointNotFoundException: Nelze se připojit k http://localhost: 8000/ServiceModelSamples/Service/CalculatorService. Kód chyby TCP 10061: žádné připojení může vytvořit, protože cílový počítač je aktivně odmítl.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q7)  
  
<a name="BKMK_q1"></a>   
## <a name="i-am-unable-to-find-the-project-files-on-my-hard-drive"></a>Nedaří se mi najít soubory projektu na pevném disku.  
 [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)]uloží soubory v c:\users projektu\\< uživatele name\Documents\\< verze sady Visual Studio\>\Projects v [!INCLUDE[wv](../../../includes/wv-md.md)] a [!INCLUDE[win7_client_secondref](../../../includes/win7-client-secondref-md.md)]a c:\Documents and Settings\\< uživatelské jméno\>Dokumenty \My\\< verze sady Visual Studio\>\Projects v dřívějších verzích systému Windows.  
  
<a name="BKMK_q2"></a>   
## <a name="attempting-to-run-the-service-application-http-could-not-register-url-http8000servicemodelsamplesservice-your-process-does-not-have-access-rights-to-this-namespace"></a>Probíhá pokus o spuštění služby aplikace: HTTP nebylo možné zaregistrovat http://+:8000/ServiceModelSamples/Service/ adresy URL. Váš proces nemá přístupová práva na tento obor názvů.  
 Proces, který je hostitelem [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby musí být spuštěna s oprávněními správce. Pokud používáte službu z uvnitř [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] musíte spustit [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] jako správce. Klepněte na tlačítko **spustit**, klikněte pravým tlačítkem na [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] a vyberte **spustit jako správce**. Pokud používáte službu z příkazového řádku řádku je nutné spustit okně příkazového řádku jako správce podobným způsobem. Klikněte na tlačítko **spustit**, klikněte pravým tlačítkem na **příkazového řádku** a vyberte **spustit jako správce**.  
  
<a name="BKMK_q3"></a>   
## <a name="attempting-to-use-the-svcutilexe-tool-svcutil-is-not-recognized-as-an-internal-or-external-command-operable-program-or-batch-file"></a>Pokus o použití nástroje Svcutil.exe: 'svcutil' nebyl rozpoznán jako vnitřního ani vnějšího příkazu, spustitelného programu nebo dávkového souboru.  
 Svcutil.exe musí být v cestě k systému. Nejsnazším řešením je použití příkazového řádku. Klikněte na tlačítko **spustit**, vyberte **všechny programy**, [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], **nástroje sady Visual Studio**, a [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] **příkazového řádku**. Tento příkaz nastaví cestu systému do správných umístění pro všechny nástroje dodávána jako součást [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
<a name="BKMK_q4"></a>   
## <a name="unable-to-find-the-appconfig-file-generated-by-svcutilexe"></a>Nepodařilo se najít soubor App.config generované Svcutil.exe.  
 **Přidat existující položku** dialogové okno zobrazí ve výchozím nastavení pouze soubory s těmito příponami: .cs, RESX, .settings, XSD, WSDL. Můžete zadat, že chcete zobrazit všechny typy souborů tak, že vyberete **všechny soubory (\*.\*)**  v rozevíracím seznamu v pravém dolním rohu **přidat existující položku** dialogové okno.  
  
<a name="BKMK_q5"></a>   
## <a name="compiling-the-client-application-calculatorclient-does-not-contain-a-definition-for-method-name-and-no-extension-method-method-name-accepting-a-first-argument-of-type-calculatorclient-could-be-found-are-you-missing-a-using-directive-or-an-assembly-reference"></a>Kompilování klientská aplikace: 'CalculatorClient' neobsahuje definici '\<název metody >' a žádná metoda rozšíření '\<název metody >' přijímající první argument typu 'CalculatorClient' nebyla nalezena (jste si Chybí using – direktiva nebo odkaz na sestavení?)  
 Pouze těch metod, které jsou označené `ServiceOperationAttribute` jsou viditelné na vnějším světem. Pokud byl vynechán `ServiceOperationAttribute` atribut z jedné z metod v `ICalculator` rozhraní se vám tato zpráva Chyba při kompilaci klientská aplikace, která zavolá operaci chybí atribut.  
  
<a name="BKMK_q6"></a>   
## <a name="compiling-the-client-application-the-type-or-namespace-name-calculatorclient-could-not-be-found-are-you-missing-a-using-directive-or-an-assembly-reference"></a>Kompilování klientská aplikace: typu nebo oboru názvů 'CalculatorClient' nebyl nalezen (chybějící using – direktiva nebo odkaz na sestavení?)  
 Pokud nepřidáte soubor Proxy.cs nebo Proxy.vb do projektu klienta se tato chyba.  
  
<a name="BKMK_q7"></a>   
## <a name="running-the-client-unhandled-exception-systemservicemodelendpointnotfoundexception-could-not-connect-to-httplocalhost8000servicemodelsamplesservicecalculatorservice-tcp-error-code-10061-no-connection-could-be-made-because-the-target-machine-actively-refused-it"></a>Spuštění klienta: neošetřená výjimka: System.ServiceModel.EndpointNotFoundException: Nelze se připojit k http://localhost: 8000/ServiceModelSamples/Service/CalculatorService. Kód chyby TCP 10061: žádné připojení může vytvořit, protože cílový počítač je aktivně odmítl.  
 K této chybě dojde, pokud spustíte klientskou aplikaci bez spuštění služby.  
  
<a name="BKMK_q8"></a>   
## <a name="unhandled-exception-systemservicemodelsecuritysecuritynegotiationexception-soap-security-negotiation-with-httplocalhost8000servicemodelsamplesservicecalculatorservice-for-target-httplocalhost8000servicemodelsamplesservicecalculatorservice-failed"></a>Neošetřená výjimka: System.ServiceModel.Security.SecurityNegotiationException: zabezpečení vyjednávání protokolu SOAP se "http://localhost: 8000/ServiceModelSamples/Service/CalculatorService' pro cíl"http://localhost: 8000/ServiceModelSamples/Service/CalculatorService' se nezdařilo  
 K této chybě dojde v počítači připojeném k doméně, který nemá připojení k síti. Buď připojení počítače k síti nebo vypněte zabezpečení pro klienta a služby. Pro službu upravte kód, který vytvoří WSHttpBinding takto.  
  
```  
// Step 3 of the hosting procedure: Add a service endpoint  
selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
```  
  
 Pro klienta, změnit  **\<zabezpečení >** prvek v rámci  **\<vazby >** elementu, který chcete být následující:  
  
```xml  
<security mode="Node" />  
```  
  
## <a name="see-also"></a>Viz také  
 [Kurz Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [Řešení problémů s WCF – úvodní příručka](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)  
 [Řešení problémů s instalací](../../../docs/framework/wcf/troubleshooting-setup-issues.md)
