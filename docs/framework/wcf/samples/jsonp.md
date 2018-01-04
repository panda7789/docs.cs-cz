---
title: JSONP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02332e04f729abd125f43acdbe0883851004537e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="jsonp"></a>JSONP
Tento příklad ukazuje, jak podporovala JSON s odsazení (JSONP) ve službě WCF REST services. JSONP je konvence používaná k vyvolání skripty napříč doménami a generování značek skriptu v aktuálním dokumentu. Výsledkem je vrácený v zadané zpětného volání funkce. JSONP je založena na nápad, které přidá značky, jako \<skript src = "http:/ /..." > můžete vyhodnotit skriptů z jakékoli domény a skriptu načíst tyto značky je vyhodnocován v rámci oboru, ve kterém může již definována dalších funkcí.  
  
## <a name="demonstrates"></a>Demonstruje  
 Mezi doménami skriptování s JSONP.  
  
## <a name="discussion"></a>Diskusní  
 Ukázka zahrnuje webové stránky, která dynamicky přidá blok skriptu po vykreslena stránku v prohlížeči. Tento blok skriptu volání WCF REST služba, která má jednu operaci `GetCustomer`. Služby WCF REST vrátí název a adresu uzavřen do název funkce zpětného volání zákazníka. Pokud službu WCF REST odpoví, vyvolání funkce zpětného volání na webové stránce zákaznická data a funkce zpětného volání zobrazí data na webové stránce. Vkládání značky script a spouštění funkce zpětného volání automaticky zpracováván pomocí prvku ASP.NET AJAX ScriptManager. Vzor používání je stejný jako s všechny proxy servery prvku ASP.NET AJAX, a uveďte jeden řádek povolit JSONP, jak je znázorněno v následujícím kódu:  
  
```csharp  
var proxy = new JsonpAjaxService.CustomerService();  
proxy.set_enableJsonp(true);  
proxy.GetCustomer(onSuccess, onFail, null);  
```  
  
 Webové stránky můžete volat službu WCF REST, protože služba používá technologii <xref:System.ServiceModel.Description.WebScriptEndpoint> s `crossDomainScriptAccessEnabled` nastavena na `true`. Obě tyto konfigurace se provádějí v souboru Web.config pod \<system.serviceModel > elementu.  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
  <standardEndpoints>  
    <webScriptEndpoint>  
      <standardEndpoint name="" crossDomainScriptAccessEnabled="true"/>  
    </webScriptEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 ScriptManager spravuje interakci se službou a rychle skrývá složitosti implementace ručně JSONP přístup. Při `crossDomainScriptAccessEnabled` je nastaven na `true` a odpovědi formátu JSON, je operace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury zkontroluje identifikátor URI požadavku pro parametr řetězce dotazu zpětného volání a zabalí odpověď JSON s hodnotou dotazu zpětného volání parametr řetězce. V ukázce webová stránka volá službu WCF REST s následující identifikátor URI.  
  
```  
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0  
```  
  
 Vzhledem k tomu, že parametr řetězce dotazu zpětného volání má hodnotu `JsonPCallback`, služby WCF vrátí odpověď JSONP vidět v následujícím příkladu.  
  
```  
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});  
```  
  
 Tato odpověď JSONP obsahuje data zákazníků formátu JSON, obklopeno název funkce zpětného volání, která požadované webové stránky. ScriptManager bude provedení tohoto zpětného volání pomocí značky script k provádění požadavku napříč doménami a výsledek předat onSuccess obslužná rutina, která byla předána operaci GetCustomer proxy prvku ASP.NET AJAX.  
  
 Ukázkový soubor obsahuje dva webové aplikace ASP.NET: jeden obsahuje jenom [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby a jinou obsahuje webová stránka .aspx, který zavolá službu. Při spuštění tohoto řešení [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] bude hostitelem dvou webů na jiné porty, které vytvoří prostředí, kde klienta a služby za provozu na různých doménách.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Otevřete řešení pro ukázku JSONP.  
  
2.  Stisknutím klávesy F5 spusťte HYPERLINK "http://localhost:26648/JSONPClientPage.aspx" http://localhost:26648/JSONPClientPage.aspx v prohlížeči.  
  
3.  Všimněte si, že po načtení stránky vstupy text "Název" a "Address" jsou naplněny podle hodnot.  Tyto hodnoty nebyly zadány volání [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby po vykreslení stránky v prohlížeči.
