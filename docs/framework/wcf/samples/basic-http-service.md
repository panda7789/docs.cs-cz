---
title: "Základní služba HTTP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27048b43-8a54-4f2a-9952-594bbfab10ad
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cf4d40bce37dea65f2a27421de736779e467e728
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="basic-http-service"></a>Základní služba HTTP
Tento příklad ukazuje, jak implementovat založené na protokolu HTTP, na základě vzdáleného volání Procedur služby - často se používá označuje jako "POX" (prostý formát XML) služby – pomocí [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] REST programovací model. Tato ukázka se skládá ze dvou komponent: vlastním hostováním [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba HTTP (Service.cs) a konzolovou aplikaci (Program.cs), která vytvoří službu a provádí volání do ní.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Služby zpřístupní 2 operations `EchoWithGet` a `EchoWithPost`, která vrací řetězec, který byl předán jako vstup.  
  
 `EchoWithGet` Operaci je opatřen poznámkou <xref:System.ServiceModel.Web.WebGetAttribute>, což naznačuje, že zpracovává operaci HTTP `GET` požadavky. Protože <xref:System.ServiceModel.Web.WebGetAttribute> neurčuje explicitně <xref:System.UriTemplate>, operace očekává vstupní řetězec, který má být předán pomocí parametr řetězce dotazu s názvem `s`. Všimněte si, že formát identifikátoru URI, který služba očekává lze přizpůsobit pomocí <xref:System.ServiceModel.Web.WebGetAttribute.UriTemplate%2A> vlastnost.  
  
 `EchoWithPost` Operaci je opatřen poznámkou <xref:System.ServiceModel.Web.WebInvokeAttribute>, které znamenají, že není `GET` operaci (má vedlejší účinky). Protože <xref:System.ServiceModel.Web.WebInvokeAttribute> neurčuje explicitně `Method`, zpracovává operaci HTTP `POST` požadavky, které mají řetězec v textu požadavku (ve formátu XML pro instanci). Všimněte si, že metoda HTTP a formát identifikátoru URI pro požadavek lze přizpůsobit pomocí <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> a <xref:System.ServiceModel.Web.WebInvokeAttribute.UriTemplate> vlastnosti v uvedeném pořadí.  
  
 Soubor App.config Konfiguruje službu WCF s výchozím <xref:System.ServiceModel.Description.WebHttpEndpoint> který má <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> vlastnost nastavena na hodnotu `true`. V důsledku toho [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury vytvoří automatické stránku nápovědy HTML na základě v `http://localhost:8000/Customers/help` poskytující informace o vytvoření požadavky HTTP na službu a využívat odpověď HTTP služby.  
  
 Program.cs ukazuje, jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanálu lze použít pro volání do služby a zpracování odpovědi. Všimněte si, že toto je pouze jeden ze způsobů, jak přístup k [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby. Je také možné přístup ke službě pomocí jiné třídy rozhraní .NET Framework jako <xref:System.Net.HttpWebRequest> a <xref:System.Net.WebClient>. Další ukázky v sadě SDK (například [automatický výběr formátu](../../../../docs/framework/wcf/samples/automatic-format-selection.md) ukázkové a [základní služba prostředků](../../../../docs/framework/wcf/samples/basic-resource-service.md) ukázkové) ukazují, jak používat tyto třídy ke komunikaci s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.  
  
 Služba s vlastním hostováním a klient se skládá vzorku i v konzolové aplikaci spustit. Konzolové aplikace běží, klient odešle žádosti o službu a zapisuje příslušné informace z odpovědi do okna konzoly.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete řešení pro základní Ukázka služby protokolu Http. Při spouštění [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], musíte spustit jako správce pro vzorovou proběhl úspěšně. To můžete provést kliknutím pravým tlačítkem myši [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ikonu a vyberte **spustit jako správce** v místní nabídce.  
  
2.  Stisknutím kombinace kláves CTRL + SHIFT + B sestavte řešení a potom stiskněte klávesu Ctrl + F5 a spusťte konzolovou aplikaci bez ladění. V okně konzoly se zobrazí a poskytuje identifikátor URI spuštěné služby a identifikátor URI HTML stránka pro spuštěnou službu nápovědy. V libovolném bodě v čase můžete zobrazit na stránce nápovědy HTML zadáním identifikátor URI stránky nápovědy v prohlížeči. Ukázka běží, zapíše klienta stavu aktuální aktivity.  
  
3.  Stisknutím libovolné klávesy ukončit vzorku.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicHttpService`  
  
## <a name="see-also"></a>Viz také  
 [Automatický výběr formátu](../../../../docs/framework/wcf/samples/automatic-format-selection.md)  
 [Služba základních prostředků](../../../../docs/framework/wcf/samples/basic-resource-service.md)
