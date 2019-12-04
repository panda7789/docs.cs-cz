---
title: Vazba dat v klientovi ASP.NET
ms.date: 03/30/2017
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
ms.openlocfilehash: 2db29e0c4cdb87961430b80f317160b90e6756d0
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715385"
---
# <a name="data-binding-in-an-aspnet-client"></a>Vazba dat v klientovi ASP.NET
Tato ukázka předvádí, jak vytvořit vazby dat vrácených typickou Windows Communication Foundation službou (WCF) v aplikaci webových formulářů.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Tato ukázka demonstruje službu, která implementuje kontrakt definující způsob komunikace požadavek-odpověď. Ukázka se skládá z aplikace klientských webových formulářů, která je přístupná z prohlížeče a služby WCF hostované službou Internetová informační služba (IIS).  
  
 Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď. Kontrakt je definován rozhraním `IWeatherService`, které zpřístupňuje operaci s názvem `GetWeatherData`. Tato operace přijme pole měst a vrátí pole `WeatherData` objektů, které reprezentují vysokou a nízkou předpokládanou teplotu města.  
  
 Na stránce ASP.NET Client. aspx je definován ovládací prvek DataGrid ovládacího prvku, který obsahuje grafické znázornění dat vrácených službou. Kód na stránce. aspx volá službu WCF pro data o počasí a vrací data do pole `WeatherData` objektů. Prvek DataGrid určuje, odkud mají být data získána, nastavením jeho vlastnosti `DataSource` na toto pole. K datové vazbě dojde voláním metody `DataBind` ovládacího prvku DataGrid. Veškerý tento kód je obsažen uvnitř.`aspx` `Page_Load` metoda stránky, takže když uživatel aktualizuje stránku prohlížeče, data se aktualizují v prvku DataGrid.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Tento klient ukázky je web, který běží na vývojovém webovém serveru. Chcete-li spustit vývojový webový server, zadejte do příkazového řádku následující příkaz: `%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`. Pak přejděte na `http://localhost:8000/client`. Chcete-li spustit tuto ukázku v rámci počítačů, nahraďte všechny odkazy na `localhost` v souboru Web. config klienta názvem počítače serveru.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`
