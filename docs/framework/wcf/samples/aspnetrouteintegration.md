---
title: AspNetRouteIntegration
ms.date: 03/30/2017
ms.assetid: 0638ce0e-d053-47df-a447-688e447a03fb
ms.openlocfilehash: 8d9a0710e5106cbc3d02a06e81f4f8ed9ae3e03b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43475878"
---
# <a name="aspnetrouteintegration"></a>AspNetRouteIntegration
Tato ukázka předvádí, jak hostovat služby Windows Communication Foundation (WCF) REST pomocí technologie ASP.NET trasy. [Služba základních prostředků](../../../../docs/framework/wcf/samples/basic-resource-service.md) ukázka zobrazí v místním prostředí verze tohoto scénáře a popisuje implementaci služby do hloubky. Toto téma se zaměřuje na funkce integrace technologie ASP.NET. Další informace o směrování ASP.NET najdete v tématu <xref:System.Web.Routing>.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Služba WCF poskytuje kolekci zákazníků způsobem resource orientované nebo rozhraní REST. Stejně jako služba WCF na bázi protokolu SOAP může být služba hostována v technologii ASP.NET pomocí souboru SVC. Ale to není často upřednostňuje scénáře HTTP protože vyžaduje s .svc v adrese URL pro službu. Kromě toho vyžaduje nasazení souboru .svc spolu s knihovna služby. Tato omezení se lze vyvarovat hostováním služby pomocí ASP.NET trasy, jak je uvedeno v této ukázce.  
  
 Ukázka hostuje službu v technologii ASP.NET tak, že přidáte <xref:System.ServiceModel.Activation.ServiceRoute> v souboru Global.asax. <xref:System.ServiceModel.Activation.ServiceRoute> Určuje typ služby ("služby" v tomto případě), typ objektu pro vytváření hostitele služby k používání pro službu (<xref:System.ServiceModel.Activation.WebServiceHostFactory> v tomto případě) a základní adresa pro službu HTTP ("~ / zákazníky v tomto případě).  
  
 Kromě toho ukázka zahrnuje soubor Web.config, který se přidá <xref:System.Web.Routing.UrlRoutingModule> (Chcete-li zapnout trasy technologie ASP.NET) a zahrnuje konfigurace pro službu. Konkrétně se konfigurace konfiguruje službu WCF s výchozí <xref:System.ServiceModel.Description.WebHttpEndpoint> , který má <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> nastavení `true`. V důsledku toho infrastruktura WCF vytvoří automatické stránce nápovědy HTML založené na `http://localhost/Customers/help` , který poskytuje informace o tom, jak vytvořit HTTP žádostí o služby a jak získat přístup k služby odpověď HTTP – třeba příklad, jak zákazník Podrobnosti jsou reprezentovány v XML a JSON.  
  
 Vystavení kolekcí zákazníků (a obecněji prostředek) tímto způsobem umožňuje komunikovat se službou jednotným způsobem pomocí identifikátorů URI a HTTP klientovi `GET`, `PUT`, `DELETE` a `POST`.  
  
 Soubor program.cs v projektu klienta ukazuje, jak tohoto klienta lze vytvořené využitím <xref:System.Net.HttpWebRequest>. Všimněte si, že toto je pouze jeden způsob, jak získat přístup ke službě WCF. Je také možné získat přístup ke službě pomocí ostatních tříd rozhraní .NET Framework jako objekt pro vytváření kanálů WCF a <xref:System.Net.WebClient>. Další ukázky v sadě SDK (například [základní služba HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) ukázky a [automatický výběr formátu](../../../../docs/framework/wcf/samples/automatic-format-selection.md) ukázkové) ukazují, jak použít tyto třídy komunikovat se službou WCF.  
  
 Tento příklad se skládá z 3 projekty:  
  
 Služba  
 Projekt webové aplikace, která zahrnuje služby WCF HTTP hostované v technologii ASP.NET.  
  
 Klient  
 Projekt konzolové aplikace, která provádí volání služby.  
  
 Běžné  
 Sdílená knihovna, která obsahuje `Customer` typ používaný klientem a službou. Při spuštění aplikace konzoly klienta, klient vytvářejí požadavky na službu a zapíše relevantní informace z odpovědí do okna konzoly.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete řešení pro integraci směrování ASP.NET ukázku v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.  
  
3.  Pokud ho ještě není otevřený, stiskněte "CTRL + W, S" Otevřít **Průzkumníka řešení** okna.  
  
4.  Z **Průzkumníka řešení** windows, klikněte pravým tlačítkem na **služby** projektu a umístěte kurzor **ladění** možnost místní nabídky tak, aby **Start Nová Instance** se zobrazí místní nabídku a vyberte **spustit novou instanci**.  Tím se spustí serveru ASP.NET development server, který je hostitelem služby.  
  
5.  Z **Průzkumníka řešení** windows, klikněte pravým tlačítkem na **klienta** projektu a umístěte kurzor **ladění** možnost místní nabídky tak, aby **spustit nový Instance** se zobrazí místní nabídku a vyberte **spustit novou instanci**.  
  
6.  V okně konzoly klienta se zobrazí a poskytuje URI spuštěnou službu a identifikátor URI HTML stránka pro spuštěnou službu nápovědy. Na stránce nápovědy HTML v libovolném bodě v čase zobrazíte tak, že zadáte identifikátor URI na stránce nápovědy v prohlížeči. Při spuštění ukázky klienta zapíše stavu aktuální aktivity.  
  
7.  Stisknutím libovolné klávesy ukončete konzolovou aplikaci klienta.  
  
8.  Stiskněte Shift + F5 ukončete ladění služby a v oznamovací oblasti Windows, klikněte pravým tlačítkem na ikonu ASP.NET development server a vyberte **Zastavit** v místní nabídce.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetRouteIntegration`  
  
## <a name="see-also"></a>Viz také
