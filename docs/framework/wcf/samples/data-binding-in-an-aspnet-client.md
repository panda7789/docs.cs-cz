---
title: Vazba dat v klientovi ASP.NET
ms.date: 03/30/2017
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
ms.openlocfilehash: c068c1cab5a5b9dad75e781e58076f4066a3b2a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145004"
---
# <a name="data-binding-in-an-aspnet-client"></a>Vazba dat v klientovi ASP.NET
Tato ukázka ukazuje, jak vázat data vrácená typickou službou WCF (Windows Communication Foundation) v aplikaci webových formulářů.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Tato ukázka ukazuje službu, která implementuje smlouvu, která definuje vzor komunikace požadavek odpověď. Ukázka se skládá z klientské webové aplikace přístupné z prohlížeče a služby WCF hostované Internetovou informační službou (IIS).  
  
 Služba implementuje smlouvu, která definuje vzor komunikace požadavek odpověď. Kontrakt je definován `IWeatherService` rozhraním, které zveřejňuje `GetWeatherData`operaci s názvem . Tato operace přijme pole měst a vrátí `WeatherData` pole objektů, které představují vysokou a nízkou předpokládanou teplotu pro město.  
  
 Na stránce ASP.NET klienta .aspx je definován webový ovládací prvek DataGrid, který obsahuje grafické znázornění dat vrácených službou. Kód na stránce ASPX volá službu WCF pro data o `WeatherData` počasí a vrátí data do pole objektů. DataGrid určuje, odkud získat data z `DataSource` nastavením jeho vlastnost i na toto pole. Datové vazby dochází s voláním `DataBind` DataGrid metody. Celý tento kód je obsažen uvnitř .`aspx` `Page_Load` stránku, takže pokaždé, když uživatel aktualizuje stránku prohlížeče, data se aktualizují v DataGrid.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Klient této ukázky je web, který je spuštěn pod vývojovým webovým serverem. Chcete-li spustit vývojový webový server, zadejte do příkazového řádku následující příkaz: `%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`. Potom přejděte na . `http://localhost:8000/client` Chcete-li spustit tuto ukázku v `localhost` počítačích, nahraďte všechny odkazy v souboru Web.config klienta názvem počítače serveru.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`
