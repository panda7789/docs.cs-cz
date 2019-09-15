---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 1fc85838d7491f94b8da1e0ab458d6d021cd2b32
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989781"
---
# <a name="jsonp"></a>JSONP
Tato ukázka demonstruje, jak podporovat JSON s odsazením (JSONP) ve službách WCF REST. JSONP je konvence, která se používá k vyvolání skriptů mezi doménami generováním značek skriptu v aktuálním dokumentu. Výsledek je vrácen v zadané funkci zpětného volání. JSONP je založen na nápadu, který značky `<script src="http://..." >` , jako je například, může vyhodnotit skripty z jakékoli domény a skript načtený těmito značkami je vyhodnocen v rámci oboru, ve kterém již mohou být definovány jiné funkce.

## <a name="demonstrates"></a>Demonstruje
 Skriptování mezi doménami pomocí JSONP.

## <a name="discussion"></a>Účely
 Ukázka obsahuje webovou stránku, která dynamicky přidá blok skriptu po vykreslení stránky v prohlížeči. Tento blok skriptu volá službu WCF REST, která má jedinou operaci, `GetCustomer`. Služba WCF REST vrátí jméno a adresu zákazníka zabalené do názvu funkce zpětného volání. Pokud služba WCF REST reaguje, je funkce zpětného volání na webové stránce vyvolána pomocí zákaznických dat a funkce zpětného volání zobrazí data na webové stránce. Vložení značky Script a provedení funkce zpětného volání je automaticky zpracováno ovládacím prvkem ASP.NET AJAX ScriptManager. Vzor použití je stejný jako u všech proxy ASP.NET AJAX, s přidáním jednoho řádku pro povolení JSONP, jak je znázorněno v následujícím kódu:

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 Webová stránka může zavolat službu WCF REST, protože služba používá <xref:System.ServiceModel.Description.WebScriptEndpoint> sadu s `crossDomainScriptAccessEnabled` nastavenou na `true`. Obě tyto konfigurace jsou provedeny v souboru \<Web. config v prvku System. ServiceModel >.

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

 ScriptManager spravuje interakci se službou a skrývá složitost ruční implementace přístupu JSONP. Když `crossDomainScriptAccessEnabled` je nastavené `true` na a formát odpovědi pro operaci je JSON, infrastruktura WCF zkontroluje identifikátor URI žádosti pro parametr řetězce dotazu zpětného volání a zabalí odpověď JSON s hodnotou řetězce dotazu zpětného volání. ukazatele. V ukázce webová stránka volá službu WCF REST s následujícím identifikátorem URI.

```http
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 Vzhledem k tomu `JsonPCallback`, že parametr řetězce dotazu zpětného volání má hodnotu, služba WCF vrátí odpověď JSONP zobrazenou v následujícím příkladu.

```json
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 Tato odpověď JSONP zahrnuje zákaznická data formátovaná jako JSON, zabalená pomocí názvu funkce zpětného volání, kterou požaduje požadovaná webová stránka. ScriptManager spustí toto zpětné volání pomocí značky skriptu, aby provedl požadavek mezi doménami, a poté předává výsledek obslužné rutině úspěch, která byla předána do operace GetCustomer v proxy ASP.NET AJAX.

 Ukázka se skládá ze dvou webových aplikací ASP.NET: jeden obsahuje pouze službu WCF a druhý obsahuje webovou stránku. aspx, která volá službu. Při spuštění řešení bude Visual Studio 2012 hostovat tyto dvě weby na různých portech, čímž se vytvoří prostředí, ve kterém je služba a klient v různých doménách aktivní.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1. Otevřete řešení pro ukázku JSONP.  
  
2. Stisknutím klávesy F5 spustíte `http://localhost:26648/JSONPClientPage.aspx` v prohlížeči.  
  
3. Všimněte si, že po načtení stránky se textové vstupy pro "název" a "adresa" vyplní hodnotami.  Tyto hodnoty byly zadány z volání služby WCF poté, co prohlížeč dokončil vykreslování stránky.
