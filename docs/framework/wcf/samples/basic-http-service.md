---
title: Základní služba HTTP
ms.date: 03/30/2017
ms.assetid: 27048b43-8a54-4f2a-9952-594bbfab10ad
ms.openlocfilehash: 2e4aee93341404df5f06b096a9a7bf18a3c94f56
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2018
ms.locfileid: "48262381"
---
# <a name="basic-http-service"></a>Základní služba HTTP
Tento příklad ukazuje, jak implementovat služby založené na protokolu HTTP, na základě RPC - popularly označuje jako služba "POX" (Plain Old XML) – pomocí služby Windows Communication Foundation (WCF) REST programovacího modelu. Tato ukázka obsahuje dvě součásti: v místním prostředí služby WCF HTTP (Service.cs) a Konzolová aplikace (Program.cs), který vytvoří službu a provede volání do něj.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Služba WCF poskytuje 2 operace `EchoWithGet` a `EchoWithPost`, která vrací řetězec, který byl předán jako vstup.  
  
 `EchoWithGet` Operace je opatřen poznámkou <xref:System.ServiceModel.Web.WebGetAttribute>, což znamená, že zpracovává operaci HTTP `GET` požadavky. Protože <xref:System.ServiceModel.Web.WebGetAttribute> explicitně neurčí <xref:System.UriTemplate>, operace očekává, že vstupní řetězec předat pomocí parametru řetězce dotazu s názvem `s`. Všimněte si, že formát identifikátoru URI, který očekává, že služba je možné přizpůsobit pomocí <xref:System.ServiceModel.Web.WebGetAttribute.UriTemplate%2A> vlastnost.  
  
 `EchoWithPost` Operace je opatřen poznámkou <xref:System.ServiceModel.Web.WebInvokeAttribute>, které označují, že není `GET` operace (má vedlejší účinky). Protože <xref:System.ServiceModel.Web.WebInvokeAttribute> explicitně neurčí `Method`, zpracovává operaci HTTP `POST` požadavky, které mají řetězce v textu požadavku (ve formátu XML pro instanci). Všimněte si, že metoda protokolu HTTP a formát identifikátoru URI žádosti je možné přizpůsobit pomocí <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> a <xref:System.ServiceModel.Web.WebInvokeAttribute.UriTemplate> vlastnosti v uvedeném pořadí.  
  
 Soubor App.config Konfiguruje službu WCF s výchozím <xref:System.ServiceModel.Description.WebHttpEndpoint> , který má <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> nastavenou na `true`. V důsledku toho infrastruktura WCF vytvoří automatické stránce nápovědy HTML založené na `http://localhost:8000/Customers/help` , který poskytuje informace o tom, jak vytvořit požadavky HTTP na službu a jak využívat služby odpověď HTTP.  
  
 Program.cs ukazuje, jak lze pomocí objektu pro vytváření kanálů WCF provádět volání do služby a zpracování odpovědi. Všimněte si, že toto je pouze jeden způsob, jak získat přístup ke službě WCF. Je také možné získat přístup ke službě pomocí ostatních tříd rozhraní .NET Framework jako <xref:System.Net.HttpWebRequest> a <xref:System.Net.WebClient>.
  
 Ukázka obsahuje služba v místním prostředí a klient i spuštění v rámci konzolové aplikace. Konzolová aplikace běží, klient vytvářejí požadavky na službu a zapíše relevantní informace z odpovědi v okně konzoly.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete řešení pro základní Ukázka služby Http. Při spuštění sady Visual Studio 2012, je nutné spustit jako správce pro ukázku proběhl úspěšně. To udělat tak, že kliknete pravým tlačítkem na ikonu sady Visual Studio 2012 a vyberete **spustit jako správce** v místní nabídce.  
  
2.  Stiskněte kombinaci kláves CTRL + SHIFT + B, sestavte řešení a pak stisknutím kombinace kláves Ctrl + F5 spusťte konzolovou aplikaci bez ladění. V okně konzoly se zobrazí a poskytuje URI spuštěnou službu a stránku pro spuštěnou službu identifikátoru URI HTML s nápovědou. Na stránce nápovědy HTML v libovolném bodě v čase zobrazíte tak, že zadáte identifikátor URI na stránce nápovědy v prohlížeči. Při spuštění ukázky klienta zapíše stavu aktuální aktivity.  
  
3.  Stisknutím libovolné klávesy ukončete vzorovou.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicHttpService`  
