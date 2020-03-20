---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 6b5b42285539c2334bccaa04e1ba179d2cf0046c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183574"
---
# <a name="jsonp"></a>JSONP
Tato ukázka ukazuje, jak podporovat JSON s padding (JSONP) ve službách WCF REST. JSONP je konvence používaná k vyvolání skriptů mezi doménami generováním značek skriptů v aktuálním dokumentu. Výsledek je vrácen v zadané funkci zpětného volání. JSONP je založen na myšlence, že značky, jako `<script src="http://..." >` jsou můžete vyhodnotit skripty z libovolné domény a skript načtený těmito značkami je vyhodnocen v rámci oboru, ve kterém již mohou být definovány další funkce.

## <a name="demonstrates"></a>Demonstruje
 Skriptování mezi doménami pomocí jsonp.

## <a name="discussion"></a>Diskuse
 Ukázka obsahuje webovou stránku, která dynamicky přidává blok skriptu po vykreslení stránky v prohlížeči. Tento blok skriptu volá službu WCF `GetCustomer`REST, která má jednu operaci . Služba WCF REST vrátí jméno a adresu zákazníka zabalené v názvu funkce zpětného volání. Když služba WCF REST odpoví, funkce zpětného volání na webové stránce je vyvolána s daty zákazníka a funkce zpětného volání zobrazí data na webové stránce. Vkládání značky skriptu a spuštění funkce zpětného volání je automaticky zpracováno ovládacím prvkem ASP.NET AJAX ScriptManager. Vzor použití je stejný jako u všech ASP.NET proxy ajax, s přidáním jednoho řádku povolit JSONP, jak je znázorněno v následujícím kódu:

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 Webová stránka může volat službu WCF REST, `crossDomainScriptAccessEnabled` protože `true`služba používá sadu with nastavenou <xref:System.ServiceModel.Description.WebScriptEndpoint> na . Obě tyto konfigurace jsou prováděny v souboru Web.config pod elementem \<system.serviceModel>.

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

 ScriptManager spravuje interakci se službou a skryje složitost ruční implementace přístupu JSONP. Pokud `crossDomainScriptAccessEnabled` je `true` nastavena na a formát odpovědi pro operaci je JSON, WCF infrastruktury zkontroluje URI požadavku na parametr řetězce dotazu zpětného volání a zalomí odpověď JSON s hodnotou parametru řetězce dotazu zpětného volání. V ukázce webová stránka volá službu WCF REST s následujícím identifikátorem URI.

```http
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 Vzhledem k tomu, že parametr `JsonPCallback`řetězce dotazu zpětného volání má hodnotu , vrátí služba WCF odpověď JSONP zobrazenou v následujícím příkladu.

```json
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 Tato odpověď JSONP zahrnuje zákaznická data formátovaná jako JSON, zabalená s názvem funkce zpětného volání, který požadovala webová stránka. ScriptManager spustí toto zpětné volání pomocí značky skriptu k provedení požadavku mezi doménami a poté předá výsledek obslužné rutině onSuccess, která byla předána operaci GetCustomer ASP.NET proxy ajax.

 Ukázka se skládá ze dvou ASP.NET webových aplikací: jedna obsahuje pouze službu WCF a druhá obsahuje webovou stránku ASPX, která službu volá. Při spuštění řešení visual studio 2012 bude hostit dva weby na různých portech, což vytvoří prostředí, kde služba a klient žijí v různých doménách.

> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1. Otevřete řešení pro ukázku JSONP.  
  
2. Stisknutím klávesy `http://localhost:26648/JSONPClientPage.aspx` F5 se spustí v prohlížeči.  
  
3. Všimněte si, že po načtení stránky jsou textové vstupy pro "Name" a "Adresa" naplněny hodnotami.  Tyto hodnoty byly dodány z volání služby WCF po dokončení vykreslování stránky prohlížečem.
