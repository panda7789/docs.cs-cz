---
title: Vazba dat v klientovi ASP.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7ceb63315d94c0deed161bb294e8f61bf523bb63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="data-binding-in-an-aspnet-client"></a>Vazba dat v klientovi ASP.NET
Tento příklad ukazuje, jak k vytvoření vazby dat vrácených typické [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby v aplikaci webových formulářů.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Tento příklad znázorňuje služba, která implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi. Ukázka se skládá z klienta aplikace webových formulářů přístupný z prohlížeče a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby hostované Internetové informační služby (IIS).  
  
 Služba se implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi. Kontrakt je definována `IWeatherService` rozhraní, která zpřístupňuje operace s názvem `GetWeatherData`. Tato operace přijímá pole města a vrátí pole `WeatherData` objekty, které představují maximální a minimální prognózy teploty pro města.  
  
 Na [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] stránky .aspx klienta, webové DataGrid – ovládací prvek je definován, obsahující grafické znázornění dat vrácený službou. Kód na volání stránky .aspx [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby pro data počasí a vrací data na pole `WeatherData` objekty. V kolekci DataGrid Určuje, kde pro získání dat z nastavením jeho `DataSource` vlastností do tohoto pole. Datová vazba dochází při volání v kolekci DataGrid `DataBind` metoda. Všechny tohoto kódu je součástí.`aspx` stránky `Page_Load` metoda, tak pokaždé, když uživatel aktualizuje stránku prohlížeče, data se aktualizuje v objektu DataGrid.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tato ukázka klient je webová stránka, která běží v rámci vývojového webového serveru. Ke spuštění vývoj webový server, zadejte na příkazovém řádku následující: "`%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`. Vyhledejte http://localhost: 8000/klienta. Chcete-li tuto ukázku spustit v počítačích, nahraďte všechny odkazy na `localhost` v souboru Web.config klienta s názvem počítače serveru.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`  
  
## <a name="see-also"></a>Viz také
