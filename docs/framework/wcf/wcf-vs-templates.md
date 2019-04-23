---
title: Šablony Visual Studia pro WCF
ms.date: 03/30/2017
ms.assetid: 6a608575-3535-4190-89da-911e24c8374f
ms.openlocfilehash: b0cca0cd585a45b795db4d573659e0d19ecd78dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130894"
---
# <a name="wcf-visual-studio-templates"></a>Šablony Visual Studia pro WCF
Šablony sady Visual Studio Windows Communication Foundation (WCF) jsou předdefinované šablony projektů a položek, které můžete použít k rychlému vytvoření služby WCF a okolního aplikace v sadě Visual Studio.  
  
## <a name="using-the-wcf-templates"></a>Použití šablon WCF  
 Šablony sady Visual Studio WCF poskytují strukturu základní třída pro vývoj služby. Konkrétně tyto šablony představují základní definice kontraktu služby, kontraktu dat, implementace služby a konfiguraci. Tyto šablony můžete použít k vytvoření jednoduché služby s minimem kódu interakce, stejně jako stavební blok pro pokročilejší služby.  
  
### <a name="wcf-service-library-project-template"></a>Šablona projektu knihovny služby WCF  
 Šablona projektu knihovny služby WCF je k dispozici v dialogovém okně Nový projekt v rámci **Visual C# \WCF** a **Visual Basic\WCF**.  
  
 Když vytvoříte nový projekt používá **služby WCF** šablona, nový projekt automaticky zahrnuje následující tři soubory:  
  
-   Soubor kontraktu služby (IService1.cs nebo IService1.vb). Soubor kontraktu služby je rozhraní, které se má použít atributy služby WCF. Tento soubor obsahuje definici jednoduchou službu, která ukazují, jak definovat vaše služby a zahrnuje parametry operace a ukázku jednoduchý datový kontrakt. Toto je výchozí soubor, zobrazí v editoru kódu po vytvoření projektu služby WCF.  
  
-   (Service1.cs nebo Service1.vb) služby implementační soubor. Soubor implementace služby implementuje kontrakt definovaný v souboru kontraktu služby.  
  
-   Konfigurační soubor aplikace (App.config). Konfigurační soubor obsahuje základní prvky modelu služby WCF s bezpečnou vazbu protokolu HTTP. Také obsahuje koncový bod služby a umožňuje výměny metadat.  
  
> [!NOTE]
>  Visual Studio je nakonfigurována pro rozpoznání souboru App.config jako konfigurační soubor pro projekt při spuštění pomocí [hostitel služby WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md), což je výchozí konfigurace. Pokud hostujete knihovna služby ve spustitelném souboru, budete muset přesunout kód konfigurace do konfiguračního souboru spustitelnému souboru, protože konfigurační soubory, knihovny DLL nejsou platné.  
  
### <a name="wcf-service-application-template"></a>Šablona aplikace služby WCF  
 Šablona aplikace služby WCF je k dispozici v dialogovém okně Nový projekt v rámci **Visual C# \WCF** a **Visual Basic\WCF**.  
  
 Když vytvoříte nový projekt používá **webové aplikace služby WCF** šablony projektu obsahuje následující čtyři soubory:  
  
-   Hostitel služby souborů (service1.svc).  
  
-   Soubor kontraktu služby (IService1.cs nebo IService1.vb).  
  
-   Soubor implementace služby (Service1.svc.cs nebo Service1.svc.vb).  
  
-   Soubor webové konfigurace (Web.config).  
  
 Šablona automaticky vytvoří webového serveru (který se má nasadit do virtuálního adresáře) a hostuje službu v ní.  
  
### <a name="wcf-web-site-template"></a>Šablona webu WCF  
 Šablona webu WCF je k dispozici v dialogovém okně Nový projekt v rámci **Visual C# \Web Site\WCF služby** a **služby Site\WCF Visual Basic\Web**. Vytvoří stejné soubory jako šablony aplikace služby WCF, ale slouží k uspořádání ho jako by šlo webové stránky ASP.NET. Jsou vytvořeny složky App_Code a App_Data.  
  
### <a name="wcf-service-item-template"></a>Šablona položky služby WCF  
 Šablona položky služeb WCF je vlastní šablonu, která poskytuje rychlý způsob, jak přidat do existujících projektů sady Visual Studio služeb WCF.  
  
 Tuto šablonu použít, přejděte na **Průzkumníka řešení** podokně klikněte pravým tlačítkem na název vašeho projektu, přejděte na **přidat**a potom klikněte na tlačítko **nová položka** ke spuštění **přidat nový Položka** dialogové okno.  
  
 Služby rozhraní a implementaci soubory jsou umístěny v kořenové složce projektu.  
  
 Šablonu se pokusí sloučit oddíl konfigurace nové služby do existující konfigurační soubor, pokud jsou nekompatibilní typy.  
  
 Pokud je existující projekt webového projektu je také vytvoří soubor hostitele služby (service1.svc).  
  
### <a name="wcf-wf-service-project-and-item-template"></a>Projekt pracovního postupu služby WCF a šablonu položky.  
 Tyto šablony vytvoření služby WCF, které jsou hostiteli služby pracovního postupu, což je pracovní postup, který je přístupný jako webovou službu. Existují samostatné šablony pro XAML nebo imperativní programovací modely. Pomocí šablon, můžete vytvořit pracovní postup sekvenční nebo stavového stroje. Další informace o těchto typech pracovního postupu, naleznete v tématu [jak: Vytvoření pracovního postupu](../windows-workflow-foundation/how-to-create-a-workflow.md). Další informace o vytváření projektů pracovních postupů najdete v tématu [vytváření projektů pracovních postupů starších verzí](/visualstudio/workflow-designer/creating-legacy-workflow-projects).  
  
 Návrhář Visual Studio je rychlejší reakce, když typ XOML, pracovní postupy se používají místo toho kódu na základě těch, které jsou. XOML pracovního postupu je výchozí typ pracovního postupu má být vytvořen.  
  
### <a name="wcf-syndication-service-library-template"></a>Šablona knihovna služby syndikace WCF  
 Tato šablona umožňuje vystavit vaše informačního kanálu ve formátu RSS nebo ATOM jako služba WCF. Další informace najdete v tématu [syndikace WCF](../../../docs/framework/wcf/feature-details/wcf-syndication.md).  
  
#### <a name="changing-the-address-of-the-feed"></a>Změna adresy informačního kanálu  
 Syndikace šablony používá prohlížeč Internet Explorer během provádění. Když kliknete pravým tlačítkem na projekt v **Průzkumníka řešení** v sadě Visual Studio, vyberte **vlastnosti**a pak vyberte **ladění** kartu můžete zobrazit výchozí adresa Šablona. Aplikace Internet Explorer se pokusí otevřít kanál na této adrese.  
  
 Pokud změníte adresu váš kanál, je nutné také změnit adresu v **ladění** kartu. Pokud to neprovedete, Internet Explorer pokusy o otevření kanálu na výchozí adrese a selhání.  
  
### <a name="ajax-enabled-wcf-service-item-template"></a>Šablona položky služby WCF s povoleným AJAX  
 Tato šablona poskytuje ovládací prvek AJAX jako služba WCF. Další informace o ovládacích prvků AJAX, najdete v článku [dokumentaci ovládacího prvku AJAX](https://go.microsoft.com/fwlink/?LinkId=96717).  
  
### <a name="silverlight-enabled-wcf-service-item-template"></a>Šablona položky služby WCF s podporou technologie Silverlight  
 Tato šablona vytvoří webovou službu poskytující data Silverlight klientu nebo front-endu. Šablony můžete přidat do projektu webové stránky nebo webové aplikace k vytvoření služby WCF, která zahrnuje kód služby a konfigurace, které podporují komunikaci s klientem programu Silverlight. Pak můžete použít **přidat odkaz na službu** přidání proxy serveru klienta služby do klienta a vyměňovat data mezi klientem programu Silverlight a služby WCF s podporou technologie Silverlight.  
  
 Pro přístup k této šablony, klikněte pravým tlačítkem na projekt webové stránky nebo webové aplikace v **Průzkumníka řešení**, klikněte na tlačítko **přidat novou položku**a klikněte na tlačítko **služba WCF podporující Silverlight**.  
  
> [!NOTE]
>  Poskytuje služba WCF podporující technologii Silverlight `basicHttpBinding` koncového bodu bez povolení nastavení zabezpečení. Proto je možné získat informace o službě všichni klienti, které se připojují k této službě. Zprávy se vyměňují mezi službou a klienta jsou také není podepsána nebo zašifrována. K zabezpečení koncového bodu správně, měli byste použít ověřování, HTTPS nebo jiných mechanismů technologie ASP.NET.  
  
## <a name="see-also"></a>Viz také:

- [Hostitel služby WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
- [Testovací klient WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
