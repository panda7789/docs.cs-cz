---
title: AspNetRouteIntegration
ms.date: 03/30/2017
ms.assetid: 0638ce0e-d053-47df-a447-688e447a03fb
ms.openlocfilehash: 671857b0ace2e18f0dac7fd8033a20f3af889c8b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="aspnetrouteintegration"></a>AspNetRouteIntegration
Tento příklad znázorňuje způsob k hostování služby Windows Communication Foundation (WCF) REST pomocí směrování ASP.NET. [Základní služba prostředků](../../../../docs/framework/wcf/samples/basic-resource-service.md) ukázka zobrazuje vlastním hostováním verze tohoto scénáře a implementaci služby podrobněji popisuje. Toto téma se zaměřuje na funkce integrace technologie ASP.NET. Další informace o směrování ASP.NET najdete v tématu <xref:System.Web.Routing>.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Služby WCF poskytuje kolekci zákazníkům způsobem prostředků-zaměřené na konkrétní nebo REST. Stejně jako služby WCF na bázi protokolu SOAP může být služba hostovaný v technologii ASP.NET pomocí souboru .svc. Je to ale často není upřednostňovaný pro scénáře HTTP protože vyžaduje s .svc v adrese URL pro službu. Kromě toho vyžaduje nasazení soubor .svc společně s knihovny služby. Tato omezení můžete zabránit hostování služby pomocí ASP.NET trasy, jak je ukázáno v této ukázce.  
  
 Ukázka hostuje službu v ASP.NET přidáním <xref:System.ServiceModel.Activation.ServiceRoute> v souboru Global.asax. <xref:System.ServiceModel.Activation.ServiceRoute> Určuje typ služby ("služba" v tomto případě), typ objektu pro vytváření hostitele služby k používání pro službu (<xref:System.ServiceModel.Activation.WebServiceHostFactory> v takovém případě) a základní adresa pro službu HTTP ("~ / zákazníků v tomto případě).  
  
 Kromě toho zahrnuje v ukázkovém souboru Web.config, který přidá <xref:System.Web.Routing.UrlRoutingModule> (Chcete-li zapnout směrování ASP.NET) a zahrnuje konfiguraci pro službu. Na konkrétní konfiguraci konfiguruje službu WCF s výchozím <xref:System.ServiceModel.Description.WebHttpEndpoint> který má <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> nastavení `true`. V důsledku toho infrastruktury WCF vytvoří automatické stránku nápovědy HTML na základě v `http://localhost/Customers/help` , který poskytuje informace o tom, jak vytvořit HTTP požadavků a získání přístupu služby odpověď HTTP – například příklad zákazníka Podrobnosti jsou reprezentované v XML a JSON.  
  
 Vystavení kolekci zákazníků (a obecně platí, žádný prostředek) tímto způsobem umožňuje klientům komunikovat se službou jednotným způsobem pomocí identifikátory URI a HTTP `GET`, `PUT`, `DELETE` a `POST`.  
  
 Program.cs v projektu klienta ukazuje, jak mohou být klienta vytvořené pomocí <xref:System.Net.HttpWebRequest>. Všimněte si, že se jedná pouze jeden způsob pro přístup ke službě WCF. Je také možné přístup ke službě pomocí jiné třídy rozhraní .NET Framework jako kanálu WCF a <xref:System.Net.WebClient>. Další ukázky v sadě SDK (například [základní služba HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) ukázka a [automatický výběr formátu](../../../../docs/framework/wcf/samples/automatic-format-selection.md) ukázkové) ukazují, jak používat tyto třídy pro komunikaci se službou WCF.  
  
 Tato ukázka se skládá ze 3 projekty:  
  
 Služba  
 Projekt webové aplikace, který zahrnuje služby WCF HTTP hostované v technologii ASP.NET.  
  
 Klient  
 Projekt konzolové aplikace, která provádí volání do služby.  
  
 Běžné  
 Sdílenou knihovnu, která obsahuje `Customer` typ používaný klientem a službou. Klienta konzolové aplikace běží, klient odešle žádosti o službu a zapisuje příslušné informace z odpovědi do okna konzoly.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete řešení pro ukázku integrace trasy technologie ASP.NET v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.  
  
3.  Pokud již není otevřený, stiskněte klávesu "CTRL + W, S" Otevřít **Průzkumníku řešení** okno.  
  
4.  Z **Průzkumníku řešení** windows, klikněte pravým tlačítkem myši **služby** projektu a umístěte kurzor myši **ladění** možnost místní nabídky tak, aby **Start Nová Instance** se zobrazí kontextovou nabídku a vyberte **spustit novou instanci**.  Spustí vývojový server ASP.NET, který hostuje službu.  
  
5.  Z **Průzkumníku řešení** windows, klikněte pravým tlačítkem myši **klienta** projektu a umístěte kurzor myši **ladění** možnost místní nabídky tak, aby **spustit nový Instance** se zobrazí kontextovou nabídku a vyberte **spustit novou instanci**.  
  
6.  V okně konzoly klienta se zobrazí a poskytuje identifikátor URI spuštěné služby a identifikátor URI HTML stránka pro spuštěnou službu nápovědy. V libovolném bodě v čase můžete zobrazit na stránce nápovědy HTML zadáním identifikátor URI stránky nápovědy v prohlížeči. Ukázka běží, zapíše klienta stavu aktuální aktivity.  
  
7.  Stisknutím libovolné klávesy ukončit klientská aplikace konzoly.  
  
8.  Stisknutím klávesy Shift + F5 ukončete ladění služby a v oznamovací oblasti systému Windows klikněte pravým tlačítkem na ikonu ASP.NET development server a vyberte **Zastavit** v místní nabídce.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetRouteIntegration`  
  
## <a name="see-also"></a>Viz také
