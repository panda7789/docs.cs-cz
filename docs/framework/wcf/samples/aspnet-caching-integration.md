---
title: Integrace mezipaměti ASP.NET
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: 744ecbff8b51565906ff4c619ba8c8aecff123c7
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805405"
---
# <a name="aspnet-caching-integration"></a>Integrace mezipaměti ASP.NET
Tento příklad ukazuje, jak využívat výstupní mezipaměti technologie ASP.NET pomocí programovacího modelu WCF WEB HTTP. Najdete v tématu [základní služba prostředků](../../../../docs/framework/wcf/samples/basic-resource-service.md) ukázku vlastním hostováním verzi tento scénář, který popisuje implementace služby podrobněji. Toto téma se zaměřuje na funkce integrace výstupní mezipaměti technologie ASP.NET.  
  
## <a name="demonstrates"></a>Demonstruje  
 Integrace s ASP.NET výstupní mezipaměti  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`  
  
## <a name="discussion"></a>Diskusní  
 Ukázce se používá <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> využívat ASP.NET ukládání výstupu do mezipaměti ve službě Windows Communication Foundation (WCF). <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> Se použije k operacím služby a poskytuje název profilu mezipaměti v konfiguračním souboru, která má být použita k odpovědím z danou operaci.  
  
 V souboru Service.cs ukázkový projekt služby jak `GetCustomer` a `GetCustomers` operace jsou označené jako <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, který poskytuje název profilu mezipaměti "CacheFor60Seconds". V souboru Web.config projektu služby, je profil mezipaměti "CacheFor60Seconds" uvedených v části <`caching`> elementu <`system.web`>. Pro tento profil mezipaměti, hodnota `duration` atribut je "60", takže odpovědi související s tímto profilem se ukládat do mezipaměti ve výstupní mezipaměti technologie ASP.NET po dobu 60 sekund. Navíc pro tento profil mezipaměti `varmByParam` je nastavena na hodnotu "format" Ano požadavky s různými hodnotami `format` dotaz parametr řetězce jejich odpovědi v mezipaměti samostatně. Nakonec mezipaměti profilu `varyByHeader` atribut je nastaven na "Přijmout", aby jejich odpovědi v mezipaměti samostatně požadavků s různé hodnoty hlavičky Accept.  
  
 Program.cs v projektu klienta ukazuje, jak mohou být klienta vytvořené pomocí <xref:System.Net.HttpWebRequest>. Všimněte si, že se jedná pouze jeden způsob pro přístup ke službě WCF. Je také možné přístup ke službě pomocí jiné třídy rozhraní .NET Framework jako kanálu WCF a <xref:System.Net.WebClient>. Další ukázky v sadě SDK (například [základní služba HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) ukázka a [automatický výběr formátu](../../../../docs/framework/wcf/samples/automatic-format-selection.md) ukázkové) ukazují, jak používat tyto třídy pro komunikaci se službou WCF.  
  
## <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
 Ukázka se skládá ze tří projektů:  
  
-   **Služba**: projektu A webové aplikace, který zahrnuje služby WCF HTTP hostované v technologii ASP.NET.  
  
-   **Klient**: projekt konzolové aplikace, která provádí volání do služby.  
  
-   **Běžné**: sdílené knihovny, které obsahuje typ zákazníka používané klientem a službou.  
  
 Klienta konzolové aplikace běží, klient odešle žádosti o službu a zapisuje příslušné informace z odpovědi do okna konzoly.  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Otevřete řešení pro ukázku integrace ukládání do mezipaměti technologie ASP.NET.  
  
2.  Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.  
  
3.  Pokud **Průzkumníku řešení** okno ještě není otevřené, stiskněte CTRL + W + S.  
  
4.  Z **Průzkumníku řešení** okna, klikněte pravým tlačítkem **služby** projektu a vyberte **spustit novou instanci**. Spustí vývojový server ASP.NET, který hostuje službu.  
  
5.  Z **Průzkumníku řešení** okna, klikněte pravým tlačítkem **klienta** projektu a vyberte **spustit novou instanci**.  
  
6.  V okně konzoly klienta se zobrazí a poskytuje identifikátor URI spuštěné služby a identifikátor URI HTML stránka pro spuštěnou službu nápovědy. V libovolném bodě v čase můžete zobrazit na stránce nápovědy HTML zadáním identifikátor URI stránky nápovědy v prohlížeči.  
  
7.  Ukázka běží, zapíše klienta stavu aktuální aktivity.  
  
8.  Stisknutím libovolné klávesy ukončit klientská aplikace konzoly.  
  
9. Stisknutím klávesy SHIFT + F5 ukončete ladění služby.  
  
10. V oznamovací oblasti systému Windows klikněte pravým tlačítkem na ikonu ASP.NET development server a vyberte **Zastavit**.
