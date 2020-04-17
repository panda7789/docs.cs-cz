---
title: Šablony Visual Studia pro WCF
ms.date: 03/30/2017
ms.assetid: 6a608575-3535-4190-89da-911e24c8374f
ms.openlocfilehash: 13183ad5f05350c34eebd025eca3faa7d97644f8
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608020"
---
# <a name="wcf-visual-studio-templates"></a>Šablony Visual Studia pro WCF
Windows Communication Foundation (WCF) Visual Studio šablony jsou předdefinované projekt a šablony položek, které můžete použít v sadě Visual Studio rychle vytvářet služby WCF a okolní aplikace.  
  
## <a name="using-the-wcf-templates"></a>Použití šablon WCF  
 Šablony WCF Visual Studio poskytují základní strukturu tříd pro vývoj služeb. Konkrétně tyto šablony poskytují základní definice pro servisní smlouvy, smlouvy o datech, implementace služby a konfigurace. Tyto šablony můžete použít k vytvoření jednoduché služby s minimální interakcí kódu, stejně jako stavební blok pro pokročilejší služby.  
  
### <a name="wcf-service-library-project-template"></a>Šablona projektu knihovny služeb WCF  
 Šablona projektu Knihovna služeb WCF je k dispozici v novém dialogovém okně projektu v části **Visual C#\WCF** a **Visual Basic\WCF**.  
  
 Když vytvoříte nový projekt pomocí šablony **služby WCF,** nový projekt automaticky obsahuje následující tři soubory:  
  
- Soubor servisní smlouvy (IService1.cs nebo IService1.vb). Soubor smlouvy o poskytování služeb je rozhraní, které má atributy služby WCF. Tento soubor poskytuje definici jednoduché služby, která vám ukáže, jak definovat služby, a zahrnuje operace založené na parametrech a ukázku jednoduché datové smlouvy. Toto je výchozí soubor zobrazený v editoru kódu po vytvoření projektu služby WCF.  
  
- Soubor implementace služby (Service1.cs nebo Service1.vb). Soubor implementace služby implementuje smlouvu definovanou v souboru servisní smlouvy.  
  
- Konfigurační soubor aplikace (App.config). Konfigurační soubor poskytuje základní prvky modelu služby WCF se zabezpečenou vazbou HTTP. Obsahuje také koncový bod pro službu a umožňuje výměnu metadat.  
  
> [!NOTE]
> Visual Studio je nakonfigurováno tak, aby rozpoznalo soubor App.config jako konfigurační soubor projektu při spuštění pomocí [hostitele služby WCF (WcfSvcHost.exe),](wcf-service-host-wcfsvchost-exe.md)což je výchozí konfigurace. Pokud hostujete knihovnu služeb ve spustitelném souboru, je třeba přesunout konfigurační kód do konfiguračního souboru spustitelného souboru, protože konfigurační soubory pro knihovny DLL nejsou platné.  
  
### <a name="wcf-service-application-template"></a>Šablona aplikace služby WCF  
 Šablona aplikace služby WCF je k dispozici v dialogovém okně Nový projekt v části **Visual C#\WCF** a **Visual Basic\WCF**.  
  
 Při vytváření nového projektu pomocí šablony **WCF webové aplikační služby** projekt obsahuje následující čtyři soubory:  
  
- Soubor hostitele služby (service1.svc).  
  
- Soubor servisní smlouvy (IService1.cs nebo IService1.vb).  
  
- Soubor implementace služby (Service1.svc.cs nebo Service1.svc.vb).  
  
- Webový konfigurační soubor (Web.config).  
  
 Šablona automaticky vytvoří web (který má být nasazen do virtuálního adresáře) a bude v něm hostuje službu.  
  
### <a name="wcf-web-site-template"></a>Šablona webu WCF  
 Šablona webu WCF je k dispozici v dialogovém okně Nový projekt v části **Visual C#\Web Site\WCF Service** a **Visual Basic\Web Site\WCF Service**. Tím se vytvoří stejné soubory jako šablona aplikace služby WCF, ale uspořádá ji, jako by se jednalo o ASP.NET webu. jsou vytvořeny App_Code a App_Data složky.  
  
### <a name="wcf-service-item-template"></a>Šablona předmětu servisu WCF  
 Šablona služby WCF je vlastní šablona, která poskytuje rychlý způsob, jak přidat služby WCF do existujících projektů sady Visual Studio.  
  
 Chcete-li použít tuto šablonu, přejděte do podokna **Průzkumník řešení,** klikněte pravým tlačítkem myši na název projektu, přejděte na **Přidat**a potom klepnutím na tlačítko **Nová položka** spusťte dialogové okno Přidat **novou položku.**  
  
 Rozhraní služby a soubory implementace jsou umístěny ve složce kořenového projektu.  
  
 Šablona se pokusí sloučit část konfigurace nové služby do existujícího konfiguračního souboru, pokud jsou kompatibilní typy.  
  
 Soubor hostitele služby (service1.svc) je také vytvořen, pokud je existující projekt webový projekt.  
  
### <a name="wcf-wf-service-project-and-item-template"></a>Projekt služby WF wcf a šablona položky.  
 Tyto šablony vytvářejí služby WCF, které jsou hostiteli služby pracovního postupu, což je pracovní postup, ke kterému lze přistupovat jako k webové službě. Existují samostatné šablony pro xaml nebo imperativní programovací modely. Pomocí šablon můžete vytvořit sekvenční pracovní postup nebo pracovní postup stavového počítače. Další informace o těchto typech pracovního postupu naleznete v [tématu How to: Create a Workflow](../windows-workflow-foundation/how-to-create-a-workflow.md). Další informace o vytváření projektů pracovního postupu naleznete v [tématu Vytváření starších projektů pracovního postupu](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer).  
  
 Návrhář visual studio je citlivější při použití pracovních postupů typu XOML namísto pracovních postupů založených na kódu. Pracovní postup XOML je výchozí typ pracovního postupu, který má být vytvořen.  
  
### <a name="wcf-syndication-service-library-template"></a>Šablona knihovny syndikační služby WCF  
 Tato šablona umožňuje vystavit informační kanál ve formátu RSS nebo ATOM jako službu WCF. Další informace naleznete v tématu [WCF Syndication](./feature-details/wcf-syndication.md).  
  
#### <a name="changing-the-address-of-the-feed"></a>Změna adresy informačního kanálu  
 Šablona syndikace používá aplikaci Internet Explorer během provádění. Po kliknutí pravým tlačítkem myši na projekt v **Průzkumníkovi řešení** v sadě Visual Studio vyberte **vlastnosti**, vyberte kartu **Ladění** a zobrazí se výchozí adresa šablony. Aplikace Internet Explorer se pokusí otevřít informační kanál na této adrese.  
  
 Pokud změníte adresu zdroje, musíte také změnit adresu na kartě **Ladění.** Pokud tak neučiníte, aplikace Internet Explorer se pokusí otevřít informační kanál na výchozí adrese a nezdaří se.  
  
### <a name="ajax-enabled-wcf-service-item-template"></a>Šablona předmětu servisu WCF povolena technologií AJAX  
 Tato šablona zpřístupňuje ovládací prvek AJAX jako službu WCF. Další informace o ovládacích prvcích AJAX naleznete v [dokumentaci k ovládacímu prvku AJAX](/aspnet/ajax/).  
  
### <a name="silverlight-enabled-wcf-service-item-template"></a>Šablona předmětu služby WCF s podporou programu Silverlight  
 Tato šablona vytvoří webovou službu, která poskytuje data klientovi Silverlight nebo front-endu. Šablonu lze přidat do webového serveru nebo projektu webové aplikace a vytvořit tak službu WCF, která zahrnuje kód služby a konfiguraci, která podporuje komunikaci s klientem Programu Silverlight. Potom můžete použít **add service reference** přidat klienta proxy služby do klienta a vyměňovat data mezi klientem Silverlight a službou WCF s podporou Silverlight.  
  
 Chcete-li získat přístup k této šabloně, klepněte pravým tlačítkem myši na webový server nebo projekt webové aplikace v **Průzkumníku řešení**, klepněte na tlačítko **Přidat novou položku**a klepněte na příkaz **WCF service s podporou programu Silverlight**.  
  
> [!NOTE]
> Služba WCF s podporou programu `basicHttpBinding` Silverlight zpřístupňuje koncový bod bez povolení nastavení zabezpečení. Proto informace o službě mohou získat všichni klienti, kteří se k této službě připojují. Zprávy vyměňované mezi službou a klientem také nejsou podepsány nebo šifrovány. Chcete-li správně zabezpečit koncový bod, měli byste použít ASP.NET ověřování, HTTPS nebo jiné mechanismy.  
  
## <a name="see-also"></a>Viz také

- [Hostitel služby WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
- [Testovací klient WCF (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
