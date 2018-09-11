---
title: Integrace mezipaměti ASP.NET
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: 55e6213bf0c4c212ebcf4e68882d16532c0e4229
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44353574"
---
# <a name="aspnet-caching-integration"></a>Integrace mezipaměti ASP.NET
Tato ukázka předvádí, jak využívat výstupní mezipaměti ASP.NET programovací model webových služeb HTTP WCF. Podrobnosti najdete [služba základních prostředků](../../../../docs/framework/wcf/samples/basic-resource-service.md) ukázky v místním prostředí verze tohoto scénáře, který popisuje implementaci služby do hloubky. Toto téma se zaměřuje na funkce integrace výstupní mezipaměti technologie ASP.NET.  
  
## <a name="demonstrates"></a>Demonstruje  
 Integrace s ASP.NET výstupní mezipaměti  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`  
  
## <a name="discussion"></a>Diskuse  
 Ukázka používá <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> využívat technologie ASP.NET ukládání výstupu do mezipaměti ve službě Windows Communication Foundation (WCF). <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> Se použije k operacím služby a poskytuje název profilu mezipaměti v konfiguračním souboru, který bude použito k odpovědím z danou operaci.  
  
 V souboru Service.cs ukázkový projekt služby jak `GetCustomer` a `GetCustomers` operace jsou označené <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, která poskytuje název profilu mezipaměti "CacheFor60Seconds". V souboru Web.config projekt služby, profil mezipaměti "CacheFor60Seconds" není k dispozici <`caching`> elementu <`system.web`>. Pro tento profil mezipaměti, hodnota `duration` atribut je "60", takže odpovědi přidružený k tomuto profilu jsou uložené v mezipaměti do výstupní mezipaměti ASP.NET po dobu 60 sekund. Také, pro tento profil mezipaměti `varmByParam` atribut je nastaven na "format" požádá s různými hodnotami parametru `format` parametru řetězce dotazu odpovědi v mezipaměti samostatně. A konečně, mezipaměti profilu `varyByHeader` atribut je nastaven na "Přijmout", takže jejich odpovědi v mezipaměti samostatně žádosti se různé hodnoty hlavičky Accept.  
  
 Soubor program.cs v projektu klienta ukazuje, jak tohoto klienta lze vytvořené využitím <xref:System.Net.HttpWebRequest>. Všimněte si, že toto je pouze jeden způsob, jak získat přístup ke službě WCF. Je také možné získat přístup ke službě pomocí ostatních tříd rozhraní .NET Framework jako objekt pro vytváření kanálů WCF a <xref:System.Net.WebClient>. Další ukázky v sadě SDK (například [základní služba HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) vzorku a [automatický výběr formátu](../../../../docs/framework/wcf/samples/automatic-format-selection.md) ukázkové) ukazují, jak použít tyto třídy komunikovat se službou WCF.  
  
## <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
 Ukázkový soubor obsahuje tři projekty:  
  
-   **Služba**: webové aplikace A projekt, který zahrnuje služby WCF HTTP hostované v technologii ASP.NET.  
  
-   **Klient**: projekt konzolové aplikace, která provádí volání služby.  
  
-   **Běžné**: sdílené knihovny, který obsahuje typ zákazníka používá klienta a služby.  
  
 Při spuštění aplikace konzoly klienta, klient vytvářejí požadavky na službu a zapíše relevantní informace z odpovědí do okna konzoly.  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Otevřete řešení pro ukázka integrace ukládání do mezipaměti technologie ASP.NET.  
  
2.  Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.  
  
3.  Pokud **Průzkumníka řešení** okno ještě není otevřené, stiskněte CTRL + W + S.  
  
4.  Z **Průzkumníka řešení** okna, klikněte pravým tlačítkem **služby** projektu a vyberte **spustit novou instanci**. Tím se spustí serveru ASP.NET development server, který je hostitelem služby.  
  
5.  Z **Průzkumníka řešení** okna, klikněte pravým tlačítkem **klienta** projektu a vyberte **spustit novou instanci**.  
  
6.  V okně konzoly klienta se zobrazí a poskytuje URI spuštěnou službu a identifikátor URI HTML stránka pro spuštěnou službu nápovědy. Na stránce nápovědy HTML v libovolném bodě v čase zobrazíte tak, že zadáte identifikátor URI na stránce nápovědy v prohlížeči.  
  
7.  Při spuštění ukázky klienta zapíše stavu aktuální aktivity.  
  
8.  Stisknutím libovolné klávesy ukončete konzolovou aplikaci klienta.  
  
9. Stiskněte SHIFT + F5 ukončete ladění služby.  
  
10. V oznamovací oblasti Windows, klikněte pravým tlačítkem myši klikněte na ikonu ASP.NET development server a vyberte **Zastavit**.
