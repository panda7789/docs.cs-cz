---
title: Šablony Visual Studia pro WCF
ms.date: 03/30/2017
ms.assetid: 6a608575-3535-4190-89da-911e24c8374f
ms.openlocfilehash: 1b4a600e4ed19b967bcaeb6d880ea181b7c2d61f
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197190"
---
# <a name="wcf-visual-studio-templates"></a>Šablony Visual Studia pro WCF
Šablony sady Visual Studio pro Windows Communication Foundation (WCF) jsou předdefinované šablony projektů a položek, které můžete použít v aplikaci Visual Studio k rychlému vytváření služeb WCF a okolních aplikací.  
  
## <a name="using-the-wcf-templates"></a>Používání šablon WCF  
 Šablony sady Visual Studio pro WCF poskytují základní strukturu tříd pro vývoj služeb. Konkrétně tyto šablony poskytují základní definice pro kontrakt služby, kontrakt dat, implementaci služby a konfiguraci. Tyto šablony můžete použít k vytvoření jednoduché služby s minimální interakcí kódu, jakož i stavebního bloku pro pokročilejší služby.  
  
### <a name="wcf-service-library-project-template"></a>Šablona projektu knihovny služby WCF  
 Šablona projektu knihovny služby WCF je k dispozici v dialogovém okně Nový projekt v **části C#Visual \WCF** a **Visual Basic\WCF**.  
  
 Když vytváříte nový projekt pomocí šablony **služby WCF** , nový projekt automaticky obsahuje následující tři soubory:  
  
- Soubor kontraktu služby (IService1.cs nebo IService1. vb). Soubor kontraktu služby je rozhraní, které používá atributy služby WCF. Tento soubor poskytuje definici jednoduché služby, která vám ukáže, jak definovat vaše služby, a obsahuje operace založené na parametrech a ukázku jednoduchého kontraktu dat. Toto je výchozí soubor zobrazený v editoru kódu po vytvoření projektu služby WCF.  
  
- Soubor implementace služby (Service1.cs nebo Service1. vb). Implementační soubor služby implementuje kontrakt definovaný v souboru kontraktu služby.  
  
- Konfigurační soubor aplikace (App. config). Konfigurační soubor poskytuje základní prvky modelu služby WCF s zabezpečenou vazbou HTTP. Zahrnuje taky koncový bod pro službu a umožňuje výměnu metadat.  
  
> [!NOTE]
> Visual Studio je nakonfigurované tak, aby rozpoznal soubor App. config jako konfigurační soubor pro projekt, když je spuštěný pomocí [hostitele služby WCF (WcfSvcHost. exe)](wcf-service-host-wcfsvchost-exe.md), který je výchozí konfigurací. Pokud hostete knihovnu služby ve spustitelném souboru, je nutné přesunout konfigurační kód do konfiguračního souboru spustitelného souboru, protože konfigurační soubory pro knihovny DLL nejsou platné.  
  
### <a name="wcf-service-application-template"></a>Šablona aplikace služby WCF  
 Šablona aplikace služby WCF je k dispozici v dialogovém okně Nový projekt v **části C#Visual \WCF** a **Visual Basic\WCF**.  
  
 Když vytváříte nový projekt pomocí šablony **služby webové aplikace WCF** , projekt obsahuje následující čtyři soubory:  
  
- Soubor hostitele služby (Service1. svc).  
  
- Soubor kontraktu služby (IService1.cs nebo IService1. vb).  
  
- Soubor implementace služby (Service1.svc.cs nebo Service1. svc. vb).  
  
- Soubor webové konfigurace (Web. config).  
  
 Šablona automaticky vytvoří web (který se má nasadit do virtuálního adresáře) a hostuje službu.  
  
### <a name="wcf-web-site-template"></a>Šablona webu WCF  
 Šablona webu WCF je k dispozici v dialogovém okně Nový projekt v části **Visual C#\Web Site\WCF Service** a **Visual Basic\Web Site\WCF Service**. Tím se vytvoří stejné soubory jako v šabloně aplikace služby WCF, ale uspořádají se, jako by se jednalo o ASP.NET Web. Vytvoří se složky App_Code a App_Data.  
  
### <a name="wcf-service-item-template"></a>Šablona položky služby WCF  
 Šablona položky služby WCF je vlastní šablona, která poskytuje rychlý způsob, jak přidat služby WCF do stávajících projektů sady Visual Studio.  
  
 Chcete-li použít tuto šablonu, přejděte do podokna **Průzkumník řešení** , klikněte pravým tlačítkem myši na název projektu, přejděte na položku **Přidat**a poté klikněte na možnost **Nová položka** . tím otevřete dialogové okno **Přidat novou položku** .  
  
 Rozhraní služby a implementační soubory jsou umístěny do kořenové složky projektu.  
  
 Šablona se pokusí sloučit konfigurační oddíl nové služby do stávajícího konfiguračního souboru, pokud jsou kompatibilní typy.  
  
 Soubor hostitele služby (Service1. svc) se vytvoří také v případě, že existující projekt je webový projekt.  
  
### <a name="wcf-wf-service-project-and-item-template"></a>Projekt a Šablona položky služby WCF WF.  
 Tyto šablony vytvářejí služby WCF, které hostují službu pracovního postupu, což je pracovní postup, který je možné použít jako webovou službu. Pro XAML nebo imperativní programovací modely existují samostatné šablony. Pomocí šablon můžete vytvořit pracovní postup sekvenčního nebo stavového stroje. Další informace o těchto typech pracovního postupu najdete v tématu [Postupy: vytvoření pracovního postupu](../windows-workflow-foundation/how-to-create-a-workflow.md). Další informace o vytváření projektů pracovních postupů najdete v tématu [vytváření starších projektů pracovních postupů](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer).  
  
 Návrhář sady Visual Studio je při použití pracovních postupů typu XOML místo na základě kódu rychlejší reagovat. Pracovní postup XOML je výchozí typ pracovního postupu, který se má vytvořit.  
  
### <a name="wcf-syndication-service-library-template"></a>Šablona knihovny syndikací služby WCF  
 Tato šablona vám umožní zveřejnit váš informační kanál ve formátu RSS nebo ATOM jako služba WCF. Další informace najdete v tématu [Syndikace WCF](./feature-details/wcf-syndication.md).  
  
#### <a name="changing-the-address-of-the-feed"></a>Změna adresy informačního kanálu  
 Šablona syndikace používá během provádění Internet Explorer. Když kliknete pravým tlačítkem myši na projekt v **Průzkumníku řešení** v aplikaci Visual Studio, vyberte možnost **vlastnosti**, poté vyberte kartu **ladění** a můžete zobrazit výchozí adresu šablony. Aplikace Internet Explorer se pokusí otevřít informační kanál na této adrese.  
  
 Změníte-li adresu kanálu, je nutné také změnit adresu na kartě **ladění** . Pokud to neuděláte, pokusí se Internet Explorer otevřít informační kanál na výchozí adrese a selhat.  
  
### <a name="ajax-enabled-wcf-service-item-template"></a>Šablona položky služby WCF s povoleným AJAX  
 Tato šablona zveřejňuje ovládací prvek AJAX jako službu WCF. Další informace o ovládacích prvcích AJAX naleznete v [dokumentaci k ovládacímu prvku AJAX](https://go.microsoft.com/fwlink/?LinkId=96717).  
  
### <a name="silverlight-enabled-wcf-service-item-template"></a>Šablona položky služby WCF s povolenou technologií Silverlight  
 Tato šablona vytvoří webovou službu, která poskytuje data pro klienta Silverlight nebo front-end. Šablonu lze přidat do projektu webu nebo webové aplikace, chcete-li vytvořit službu WCF, která zahrnuje kód a konfiguraci služby, které podporují komunikaci s klientem Silverlight. Pak můžete použít **Přidat odkaz na službu** k přidání klientského proxy serveru k klientovi a k výměně dat mezi klientem Silverlight a službou WCF s podporou technologie Silverlight.  
  
 Chcete-li získat přístup k této šabloně, klikněte pravým tlačítkem myši na projekt webu nebo webové aplikace v **Průzkumník řešení**, klikněte na možnost **Přidat novou položku**a klikněte na možnost **Služba WCF s podporou technologie Silverlight**.  
  
> [!NOTE]
> Služba WCF s podporou technologie Silverlight zpřístupňuje koncový bod `basicHttpBinding` bez povolení nastavení zabezpečení. Proto mohou být informace o službě získány všemi klienty, kteří se k této službě připojují. Zprávy vyměňované mezi službou a klientem nejsou také podepsány nebo zašifrovány. Pro správné zabezpečení koncového bodu byste měli použít ověřování ASP.NET, HTTPS nebo jiné mechanismy.  
  
## <a name="see-also"></a>Viz také:

- [Hostitel služby WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
- [Testovací klient WCF (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
