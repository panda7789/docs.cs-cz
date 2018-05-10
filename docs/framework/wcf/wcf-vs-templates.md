---
title: Šablony Visual Studia pro WCF
ms.date: 03/30/2017
ms.assetid: 6a608575-3535-4190-89da-911e24c8374f
ms.openlocfilehash: 6c37974f93f10870b238617bc196b37c6dbb6dd5
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="wcf-visual-studio-templates"></a>Šablony Visual Studia pro WCF
Šablony sady Visual Studio Windows Communication Foundation (WCF) jsou předdefinovaných šablon projektů a položek, které můžete použít v sadě Visual Studio můžete rychle vytvořit služby WCF a okolního aplikace.  
  
## <a name="using-the-wcf-templates"></a>Pomocí šablon WCF  
 Šablony sady Visual Studio WCF poskytují základní strukturu třídy pro vývoj služby. Konkrétně tyto šablony představují základní definice kontraktu služby, kontrakt dat, implementace služby a konfiguraci. Tyto šablony můžete použít k vytvoření jednoduché služby s minimálním kód interakce, stejně jako stavební blok pro pokročilejší služby.  
  
### <a name="wcf-service-library-project-template"></a>Šablona projektu knihovny služby WCF  
 Šablona projektu knihovny služby WCF je k dispozici v dialogu Nový projekt v části **Visual C# \WCF** a **Visual Basic\WCF**.  
  
 Když vytvoříte nový projekt pomocí **služby WCF** šablony, nový projekt automaticky zahrnuje následující tři soubory:  
  
-   Soubor kontraktu služby (IService1.cs nebo IService1.vb). Soubor kontraktu služby je rozhraní, které se má použít atributy služby WCF. Tento soubor obsahuje definici jednoduchého služby ukazují, jak můžete definovat vaší služby a obsahuje operace na základě parametrů a ukázku kontrakt jednoduché datové. Toto je výchozí soubor, zobrazí se v editoru kódu po vytvoření projektu služby WCF.  
  
-   Soubor implementace služby (Service1.cs nebo Service1.vb). Soubor implementace služby implementuje kontrakt definovaný v souboru kontrakt služby.  
  
-   Konfigurační soubor aplikace (App.config). Konfigurační soubor obsahuje základní prvky modelu služby WCF s zabezpečené vazby HTTP. Také obsahuje koncový bod pro službu a umožňuje metadata exchange.  
  
> [!NOTE]
>  Visual Studio je nakonfigurována pro rozpoznání souboru App.config jako konfiguračního souboru pro projekt při spuštění pomocí [hostitel služby WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md), což je výchozí konfigurace. Pokud hostujete knihovny služby v nástroji spustitelný soubor, musíte přesunout konfigurace kódu do konfiguračního souboru spustitelného souboru procesu, jako konfigurační soubory pro knihovny DLL nejsou platné.  
  
### <a name="wcf-service-application-template"></a>Šablony aplikací služby WCF  
 Šablona služby aplikace WCF je k dispozici v dialogovém okně Nový projekt v části **Visual C# \WCF** a **Visual Basic\WCF**.  
  
 Když vytvoříte nový projekt pomocí **webové aplikace služby WCF** šablona, projekt obsahuje následující čtyři soubory:  
  
-   Soubor hostitele služby (service1.svc).  
  
-   Soubor kontraktu služby (IService1.cs nebo IService1.vb).  
  
-   Soubor implementace služby (Service1.svc.cs nebo Service1.svc.vb).  
  
-   Soubor webové konfigurace (Web.config).  
  
 Šablona automaticky vytvoří webovou stránku (pro nasazení do virtuálního adresáře) a hostuje službu v ní.  
  
### <a name="wcf-web-site-template"></a>Šablona webu WCF  
 Šablona webu WCF je k dispozici v dialogovém okně Nový projekt v části **Visual C# \Web Site\WCF služby** a **Visual služby Site\WCF Basic\Web**. To vytvoří stejné soubory, které jako šablonu aplikace služby WCF, ale umožňuje uspořádat, jako by šlo webovou stránku ASP.NET. Vytvoření složek App_Code a App_Data.  
  
### <a name="wcf-service-item-template"></a>Šablony položek služby WCF  
 Šablony položek služby WCF je vlastní šablonu, která poskytuje rychlý způsob, jak přidat do existujících projektů sady Visual Studio služby WCF.  
  
 Chcete-li tuto šablonu použít, přejděte na **Průzkumníku řešení** podokně klikněte pravým tlačítkem na název projektu, přejděte na **přidat**a potom klikněte na **novou položku** ke spuštění **přidat nový Položka** dialogové okno.  
  
 Soubory rozhraní a implementaci služby jsou umístěny v kořenové složce projektu.  
  
 Šablona se pokusí sloučit oddíl konfigurace nové služby pro existující konfigurační soubor, pokud jsou kompatibilní typy.  
  
 Soubor hostitele služby (service1.svc) je vytvořen také v případě existující projekt je webového projektu.  
  
### <a name="wcf-wf-service-project-and-item-template"></a>Projekt WF služby WCF a šablony položky.  
 Tyto šablony vytvořit služby WCF tohoto hostitele služby pracovního procesu, což je pracovní postup, který je přístupný jako webovou službu. Existují samostatné šablony pro XAML nebo imperativní programovací modely. Pomocí šablony, můžete vytvořit pracovní postup po sobě jdoucích nebo stavu počítače. Další informace o těchto typech pracovního postupu najdete v tématu [Windows Workflow Foundation kurzy](http://msdn.microsoft.com/library/e9705654-bd96-4b56-8d98-f1f118112d97). Další informace o vytváření projektů pracovního postupu najdete v tématu [vytváření projekty Workflow starší](/visualstudio/workflow-designer/creating-legacy-workflow-projects).  
  
 Návrháři sady Visual Studio je rychlejší reakce, když XOML pracovní postupy se používají. místo toho kódu založený na typu těch, které jsou. Pracovní postup XOML je výchozí typ pracovního postupu vytvořit.  
  
### <a name="wcf-syndication-service-library-template"></a>Šablona knihovny služby syndikace WCF  
 Tato šablona umožňuje vystavit váš informační kanál RSS nebo ATOM formát jako služby WCF. Další informace najdete v tématu [syndikace WCF](../../../docs/framework/wcf/feature-details/wcf-syndication.md).  
  
#### <a name="changing-the-address-of-the-feed"></a>Změna adresu informačního kanálu  
 Syndikace šablona používá aplikace Internet Explorer během provádění. Když kliknete pravým tlačítkem na projekt v **Průzkumníka řešení** v sadě Visual Studio, vyberte **vlastnosti**, vyberte **ladění** kartě a vy můžete zobrazit výchozí adresa Šablona. Internet Explorer se pokusí otevřít kanál na této adrese.  
  
 Pokud změníte adresu váš informační kanál, musíte změnit taky adresu v **ladění** kartě. Pokud to neprovedete, Internet Explorer pokusy o otevření kanálu na adrese výchozí a selhání.  
  
### <a name="ajax-enabled-wcf-service-item-template"></a>Použití šablony položky služby WCF AJAX  
 Tato šablona zpřístupní ovládacího prvku AJAX jako služby WCF. Další informace o ovládací prvky AJAX, najdete v článku [AJAX řízení dokumentaci](http://go.microsoft.com/fwlink/?LinkId=96717).  
  
### <a name="silverlight-enabled-wcf-service-item-template"></a>Šablony položek služby WCF s podporou technologie Silverlight  
 Tato šablona vytvoří webová služba, která poskytuje data pro klienta Silverlight nebo front-end. Šablony lze přidat na web nebo webovou projekt aplikace pro vytvoření služby WCF, které zahrnují kódu služby a konfigurace, které podporují komunikaci s klienta Silverlight. Pak můžete použít **přidat odkaz na službu** přidat proxy server na klienta služby pro klienta a výměnu dat mezi klienta Silverlight a služby WCF s podporou technologie Silverlight.  
  
 Pro přístup k této šablony, klikněte pravým tlačítkem na projekt webu nebo webové aplikace v **Průzkumníku řešení**, klikněte na tlačítko **přidat novou položku**a klikněte na tlačítko **podporuje technologii Silverlight služby WCF**.  
  
> [!NOTE]
>  Zpřístupní služby WCF podporuje technologii Silverlight `basicHttpBinding` koncového bodu bez povolení nastavení zabezpečení. Proto je možné získat informace o službě všichni klienti, které se připojují k této službě. Zprávy se vyměňují mezi službou a klienta jsou taky není podepsána nebo zašifrována. Pro koncový bod zabezpečení správně, měli byste použít ověřování ASP.NET, HTTPS nebo jiných mechanismů.  
  
## <a name="see-also"></a>Viz také  
 [Hostitel služby WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [Testovací klient WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
