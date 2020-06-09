---
title: Vazba dat v klientovi ASP.NET
ms.date: 03/30/2017
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
ms.openlocfilehash: 134e1d7df3ed6bb245a870ad257fa64ad94e4e9c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602593"
---
# <a name="data-binding-in-an-aspnet-client"></a>Vazba dat v klientovi ASP.NET
Tato ukázka předvádí, jak vytvořit vazby dat vrácených typickou Windows Communication Foundation službou (WCF) v aplikaci webových formulářů.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Tato ukázka demonstruje službu, která implementuje kontrakt definující způsob komunikace požadavek-odpověď. Ukázka se skládá z aplikace klientských webových formulářů, která je přístupná z prohlížeče a služby WCF hostované službou Internetová informační služba (IIS).  
  
 Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď. Kontrakt je definován `IWeatherService` rozhraním, které zveřejňuje operaci s názvem `GetWeatherData` . Tato operace přijme pole měst a vrátí pole `WeatherData` objektů, které reprezentují vysokou a nízkou předpokládanou teplotu pro město.  
  
 Na stránce ASP.NET Client. aspx je definován ovládací prvek DataGrid ovládacího prvku, který obsahuje grafické znázornění dat vrácených službou. Kód na stránce. aspx volá službu WCF pro data o počasí a vrátí data do pole `WeatherData` objektů. Prvek DataGrid určuje, odkud mají být data získána, nastavením jeho `DataSource` vlastnosti na toto pole. Vazba dat je vyvolána voláním `DataBind` metody DataGrid. Veškerý tento kód je obsažen uvnitř.`aspx` Metoda stránky `Page_Load` , takže pokaždé, když uživatel aktualizuje stránku prohlížeče, se data aktualizují v prvku DataGrid.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
3. Tento klient ukázky je web, který běží na vývojovém webovém serveru. Chcete-li spustit vývojový webový server, zadejte do příkazového řádku následující příkaz: `%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client` . Pak přejděte na `http://localhost:8000/client` . Chcete-li spustit tuto ukázku v rámci počítačů, nahraďte všechny odkazy na `localhost` soubor Web. config v klientském počítači názvem serveru aplikace.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`
