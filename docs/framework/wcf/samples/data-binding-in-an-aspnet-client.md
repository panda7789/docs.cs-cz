---
title: Vazba dat v klientovi ASP.NET
ms.date: 03/30/2017
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
ms.openlocfilehash: dde5ec9ac944b205051b2499c7aceac2e6d84b92
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850234"
---
# <a name="data-binding-in-an-aspnet-client"></a>Vazba dat v klientovi ASP.NET
Tato ukázka předvádí, jak vytvořit vazbu dat vrácených typické služby Windows Communication Foundation (WCF) v aplikaci webových formulářů.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 V této ukázce je služba, která implementuje kontrakt, který definuje vzor komunikace požadavek odpověď. Ukázka se skládá z klientské aplikace webových formulářů přístupný z prohlížeče a služby WCF hostované v Internetové informační služby (IIS).  
  
 Služba implementuje kontrakt, který definuje vzor komunikace požadavek odpověď. Smlouva je definován `IWeatherService` rozhraní, které uvádí operace s názvem `GetWeatherData`. Tato operace přijímá pole města a vrátí pole `WeatherData` objekty, které představují vysoké a nízké předpokládaných teploty pro město.  
  
 Na [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] klientské stránky ASPX, DataGrid Web je definovaný ovládací prvek, který obsahuje grafickou reprezentaci dat vrácené službou. Kód na stránku .aspx volá službu WCF data o počasí a vrací data do pole `WeatherData` objekty. Ovládací prvek DataGrid Určuje, kde získat data z nastavením jeho `DataSource` vlastnosti pro toto pole. Pomocí volání ovládacího prvku DataGrid dojde k datové vazby `DataBind` metody. Veškerý tento kód je vnitřní součástí.`aspx` na stránce `Page_Load` metodu, tak pokaždé, když uživatel aktualizuje stránku v prohlížeči, data se aktualizuje v mřížce DataGrid.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tato ukázka klienta je webová stránka, na kterém běží pod vývojovému webovému serveru. Pokud chcete spustit vývojovému webovému serveru, zadejte na příkazovém řádku následující: `%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`. Vyhledejte `http://localhost:8000/client`. Chcete-li tuto ukázku spustit na počítačích, nahradit všechny odkazy na `localhost` v souboru Web.config klienta s názvem počítače serveru.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`
