---
title: AspNetRouteIntegration
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0638ce0e-d053-47df-a447-688e447a03fb
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 93d248030c4b32bd7725cf9c6fbbb829a19f7845
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="aspnetrouteintegration"></a>AspNetRouteIntegration
Tento příklad ukazuje, jak hostovat [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] směruje služby REST pomocí technologie ASP.NET. [Základní služba prostředků](../../../../docs/framework/wcf/samples/basic-resource-service.md) ukázka zobrazuje vlastním hostováním verze tohoto scénáře a implementaci služby podrobněji popisuje. Toto téma se zaměřuje na funkce integrace technologie ASP.NET. Další informace o směrování ASP.NET najdete v tématu <xref:System.Web.Routing>.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Service poskytuje kolekci zákazníkům způsobem prostředků-zaměřené na konkrétní nebo REST. Stejně jako založený na protokolu SOAP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] službu, službu může být hostovaný v technologii ASP.NET pomocí souboru .svc. Je to ale často není upřednostňovaný pro scénáře HTTP protože vyžaduje s .svc v adrese URL pro službu. Kromě toho vyžaduje nasazení soubor .svc společně s knihovny služby. Tato omezení můžete zabránit hostování služby pomocí ASP.NET trasy, jak je ukázáno v této ukázce.  
  
 Ukázka hostuje službu v ASP.NET přidáním <xref:System.ServiceModel.Activation.ServiceRoute> v souboru Global.asax. <xref:System.ServiceModel.Activation.ServiceRoute> Určuje typ služby ("služba" v tomto případě), typ objektu pro vytváření hostitele služby k používání pro službu (<xref:System.ServiceModel.Activation.WebServiceHostFactory> v takovém případě) a základní adresa pro službu HTTP ("~ / zákazníků v tomto případě).  
  
 Kromě toho zahrnuje v ukázkovém souboru Web.config, který přidá <xref:System.Web.Routing.UrlRoutingModule> (Chcete-li zapnout směrování ASP.NET) a zahrnuje konfiguraci pro službu. Na konkrétní konfiguraci nakonfiguruje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby s výchozím <xref:System.ServiceModel.Description.WebHttpEndpoint> který má <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> nastavení `true`. V důsledku toho [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury vytvoří automatické stránku nápovědy HTML na základě v `http://localhost/Customers/help` , který poskytuje informace o tom, jak vytvořit HTTP požadavků a získání přístupu služby odpověď HTTP – například příklad Podrobnosti o odběrateli jsou reprezentované v XML a JSON.  
  
 Vystavení kolekci zákazníků (a obecně platí, žádný prostředek) tímto způsobem umožňuje klientům komunikovat se službou jednotným způsobem pomocí identifikátory URI a HTTP `GET`, `PUT`, `DELETE` a `POST`.  
  
 Program.cs v projektu klienta ukazuje, jak mohou být klienta vytvořené pomocí <xref:System.Net.HttpWebRequest>. Všimněte si, že toto je pouze jeden ze způsobů, jak přístup k [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby. Je také možné přístup ke službě pomocí jiné třídy rozhraní .NET Framework jako [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanálu a <xref:System.Net.WebClient>. Další ukázky v sadě SDK (například [základní služba HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) ukázka a [automatický výběr formátu](../../../../docs/framework/wcf/samples/automatic-format-selection.md) ukázkové) ukazují, jak používat tyto třídy ke komunikaci s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.  
  
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
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetRouteIntegration`  
  
## <a name="see-also"></a>Viz také
