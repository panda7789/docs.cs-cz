---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 37da57a000376f972cd6da9e04be46ddec1b7144
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767536"
---
# <a name="jsonp"></a>JSONP
Tato ukázka předvádí, jak podporovat JSON s odsazení (JSONP) služby WCF REST. JSONP je konvence používaná k vyvolání mezi doménami skriptů a generování značek skriptu v aktuálním dokumentu. Výsledek se vrátí v zadané zpětného volání funkce. JSONP vychází z myšlenky, které přidá značky, jako `<script src="http://..." >` můžete vyhodnotit skriptů z jakékoli domény a skript načte tyto visačky se vyhodnotí v rámci oboru, ve kterém může již definována dalších funkcí.

## <a name="demonstrates"></a>Demonstruje
 Mezi doménami skriptování s JSONP.

## <a name="discussion"></a>Diskuse
 Ukázka zahrnuje webovou stránku, která dynamicky přidá blok skriptu po byl vykreslen na stránce v prohlížeči. Tento blok skriptu volání služby WCF REST, který má jednu operaci `GetCustomer`. Služba WCF REST vrátí název zákazníka a adresa zabalené v názvu funkce zpětného volání. Pokud odpovídá službě WCF REST, je vyvolána funkce zpětného volání na webové stránce s zákaznická data a funkce zpětného volání zobrazí data na webové stránce. Vkládání značky skriptu a provádění funkce zpětného volání je automaticky zpracována ovládacího prvku ScriptManager technologie ASP.NET AJAX. Vzor využití je stejná jako u všech proxy technologie ASP.NET AJAX, a uveďte jeden řádek umožňující JSONP, jak je znázorněno v následujícím kódu:

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 Webové stránky můžete volat službu WCF REST, protože je používán službou <xref:System.ServiceModel.Description.WebScriptEndpoint> s `crossDomainScriptAccessEnabled` nastavena na `true`. Oba tyto konfigurace se provádí v souboru Web.config v rámci \<system.serviceModel > element.

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

 Správce skriptů spravuje interakci se službou a maskuje složitost ručně implementace JSONP přístup okamžitě. Když `crossDomainScriptAccessEnabled` je nastavena na `true` a formátu odpovědi pro operaci je JSON, infrastruktura WCF zkontroluje identifikátor URI požadavku pro parametr řetězce dotazu zpětného volání a zabalí odpověď JSON s hodnotou řetězce dotazu zpětného volání parametr. Ve vzorku volá webovou stránku služby WCF REST s následujícím identifikátorem URI.

```
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 Protože má hodnotu parametru řetězce dotazu zpětného volání `JsonPCallback`, služba WCF vrátí odpověď JSONP je znázorněno v následujícím příkladu.

```
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 Tato odpověď JSONP obsahuje zákaznická data naformátovaná jako JSON zabalena název funkce zpětného volání, která požadované webové stránky. Ovládacímu prvku ScriptManager spustí toto zpětné volání pomocí značky skriptu k provedení žádosti napříč doménami a předat výsledek do onSuccess obslužná rutina, která byla předána GetCustomer operace proxy technologie ASP.NET AJAX.

 Ukázka se skládá ze dvou webové aplikace ASP.NET: jeden obsahuje jenom službu WCF a obsahuje jiný webová stránka .aspx, která volá službu. Při spuštění řešení, Visual Studio 2012 hostovat dva weby na jiném portu, který vytvoří prostředí, ve kterém klienta a služby live v různých doménách.

> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1. Otevřete řešení pro ukázku JSONP.  
  
2. Stisknutím klávesy F5 spusťte `http://localhost:26648/JSONPClientPage.aspx` v prohlížeči.  
  
3. Všimněte si, že po načtení stránky textovými vstupy pro "Name" a "Address" se vyplní podle hodnot.  Tyto hodnoty byly zadány volání služby WCF po vykreslení stránky v prohlížeči.
