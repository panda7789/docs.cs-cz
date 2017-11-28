---
title: "Šablony Visual Studia pro WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a608575-3535-4190-89da-911e24c8374f
caps.latest.revision: "31"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a659fa3801d52da4fa4837b7df4fea9e4ac6cf5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="wcf-visual-studio-templates"></a>Šablony Visual Studia pro WCF
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] šablony jsou předdefinovaných šablon projektů a položek, můžete použít v [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] rychle sestavíte [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby a okolního aplikace.  
  
## <a name="using-the-wcf-templates"></a>Pomocí šablon WCF  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] šablony poskytují základní strukturu třídy pro vývoj služby. Konkrétně tyto šablony představují základní definice kontraktu služby, kontrakt dat, implementace služby a konfiguraci. Tyto šablony můžete použít k vytvoření jednoduché služby s minimálním kód interakce, stejně jako stavební blok pro pokročilejší služby.  
  
### <a name="wcf-service-library-project-template"></a>Šablona projektu knihovny služby WCF  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Šablona projektu knihovny služby je k dispozici v dialogu Nový projekt v části **Visual C# \WCF** a **Visual Basic\WCF**.  
  
 Když vytvoříte nový projekt pomocí **služby WCF** šablony, nový projekt automaticky zahrnuje následující tři soubory:  
  
-   Soubor kontraktu služby (IService1.cs nebo IService1.vb). Soubor kontraktu služby je rozhraní, které má [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby atributy použité. Tento soubor obsahuje definici jednoduchého služby ukazují, jak můžete definovat vaší služby a obsahuje operace na základě parametrů a ukázku kontrakt jednoduché datové. Toto je výchozí soubor po vytvoření zobrazí v editoru kódu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projektu služby.  
  
-   Soubor implementace služby (Service1.cs nebo Service1.vb). Soubor implementace služby implementuje kontrakt definovaný v souboru kontrakt služby.  
  
-   Konfigurační soubor aplikace (App.config). Konfigurační soubor obsahuje základní prvky [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] modelu služby s zabezpečené vazby HTTP. Také obsahuje koncový bod pro službu a umožňuje metadata exchange.  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]je nakonfigurována pro rozpoznání souboru App.config jako konfiguračního souboru pro projekt při spuštění pomocí [hostitel služby WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md), což je výchozí konfigurace. Pokud hostujete knihovny služby v nástroji spustitelný soubor, musíte přesunout konfigurace kódu do konfiguračního souboru spustitelného souboru procesu, jako konfigurační soubory pro knihovny DLL nejsou platné.  
  
### <a name="wcf-service-application-template"></a>Šablony aplikací služby WCF  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Šablony služby aplikace je k dispozici v dialogovém okně Nový projekt v části **Visual C# \WCF** a **Visual Basic\WCF**.  
  
 Když vytvoříte nový projekt pomocí **webové aplikace služby WCF** šablona, projekt obsahuje následující čtyři soubory:  
  
-   Soubor hostitele služby (service1.svc).  
  
-   Soubor kontraktu služby (IService1.cs nebo IService1.vb).  
  
-   Soubor implementace služby (Service1.svc.cs nebo Service1.svc.vb).  
  
-   Soubor webové konfigurace (Web.config).  
  
 Šablona automaticky vytvoří webovou stránku (pro nasazení do virtuálního adresáře) a hostuje službu v ní.  
  
### <a name="wcf-web-site-template"></a>Šablona webu WCF  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Šablona webu je k dispozici v dialogovém okně Nový projekt v části **Visual C# \Web Site\WCF služby** a **Visual služby Site\WCF Basic\Web**. To vytvoří stejné soubory, které jako šablonu aplikace služby WCF, ale umožňuje uspořádat, jako by šlo webovou stránku ASP.NET. Vytvoření složek App_Code a App_Data.  
  
### <a name="wcf-service-item-template"></a>Šablony položek služby WCF  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Položku služby. šablona je vlastní šablonu, která poskytuje rychlý způsob, jak přidat [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services do stávající [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] projekty.  
  
 Chcete-li tuto šablonu použít, přejděte na **Průzkumníku řešení** podokně klikněte pravým tlačítkem na název projektu, přejděte na **přidat**a potom klikněte na **novou položku** ke spuštění **přidat nový Položka** dialogové okno.  
  
 Soubory rozhraní a implementaci služby jsou umístěny v kořenové složce projektu.  
  
 Šablona se pokusí sloučit oddíl konfigurace nové služby pro existující konfigurační soubor, pokud jsou kompatibilní typy.  
  
 Soubor hostitele služby (service1.svc) je vytvořen také v případě existující projekt je webového projektu.  
  
### <a name="wcf-wf-service-project-and-item-template"></a>Projekt WF služby WCF a šablony položky.  
 Tyto šablony vytvořit [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby, které jsou hostiteli služby pracovního postupu, což je pracovní postup, který je přístupný jako webovou službu. Existují samostatné šablony pro XAML nebo imperativní programovací modely. Pomocí šablony, můžete vytvořit pracovní postup po sobě jdoucích nebo stavu počítače. Další informace o těchto typech pracovního postupu najdete v tématu [Windows Workflow Foundation kurzy](http://msdn.microsoft.com/en-us/e9705654-bd96-4b56-8d98-f1f118112d97). [!INCLUDE[crabout](../../../includes/crabout-md.md)]vytváření projektů pracovního postupu, najdete v části [vytváření projekty Workflow starší](/visualstudio/workflow-designer/creating-legacy-workflow-projects).  
  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]Když XOML pracovní postupy se používají. místo toho kódu založený na typu ty, které není rychlejšího Návrhář. Pracovní postup XOML je výchozí typ pracovního postupu vytvořit.  
  
### <a name="wcf-syndication-service-library-template"></a>Šablona knihovny služby syndikace WCF  
 Tato šablona vám umožní vystavit váš informační kanál RSS nebo ATOM formát jako [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby. Další informace najdete v tématu [syndikace WCF](../../../docs/framework/wcf/feature-details/wcf-syndication.md).  
  
#### <a name="changing-the-address-of-the-feed"></a>Změna adresu informačního kanálu  
 Syndikace šablona používá aplikace Internet Explorer během provádění. Když kliknete pravým tlačítkem na projekt v **Průzkumníka řešení** v [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], vyberte **vlastnosti**, vyberte **ladění** kartě a vy můžete zobrazit výchozí adresa Šablona. Internet Explorer se pokusí otevřít kanál na této adrese.  
  
 Pokud změníte adresu váš informační kanál, musíte změnit taky adresu v **ladění** kartě. Pokud to neprovedete, Internet Explorer pokusy o otevření kanálu na adrese výchozí a selhání.  
  
### <a name="ajax-enabled-wcf-service-item-template"></a>Použití šablony položky služby WCF AJAX  
 Tato šablona zpřístupní jako ovládací prvek AJAX [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby. Další informace o ovládací prvky AJAX, najdete v článku [AJAX řízení dokumentaci](http://go.microsoft.com/fwlink/?LinkId=96717).  
  
### <a name="silverlight-enabled-wcf-service-item-template"></a>Šablony položek služby WCF s podporou technologie Silverlight  
 Tato šablona vytvoří webová služba, která poskytuje data pro klienta Silverlight nebo front-end. Šablony lze přidat na web nebo webový projekt aplikace k vytvoření [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service, která zahrnuje kódu služby a konfigurace, které podporují komunikaci s klienta Silverlight. Pak můžete použít **přidat odkaz na službu** přidat proxy server na klienta služby pro klienta a výměnu dat mezi klienta Silverlight a služby WCF s podporou technologie Silverlight.  
  
 Pro přístup k této šablony, klikněte pravým tlačítkem na projekt webu nebo webové aplikace v **Průzkumníku řešení**, klikněte na tlačítko **přidat novou položku**a klikněte na tlačítko **podporuje technologii Silverlight služby WCF**.  
  
> [!NOTE]
>  Zpřístupní služby WCF podporuje technologii Silverlight `basicHttpBinding` koncového bodu bez povolení nastavení zabezpečení. Proto je možné získat informace o službě všichni klienti, které se připojují k této službě. Zprávy se vyměňují mezi službou a klienta jsou taky není podepsána nebo zašifrována. Pro koncový bod zabezpečení správně, měli byste použít ověřování ASP.NET, HTTPS nebo jiných mechanismů.  
  
## <a name="see-also"></a>Viz také  
 [Hostitel služby WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [Testovacího klienta WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
