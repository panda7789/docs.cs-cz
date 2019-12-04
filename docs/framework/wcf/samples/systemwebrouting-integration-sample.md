---
title: Ukázka integrace názvového prostoru SystemWebRouting
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 8be76fa97752680700f1c0eb56c1803fc69155d6
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716628"
---
# <a name="systemwebrouting-integration-sample"></a>Ukázka integrace názvového prostoru SystemWebRouting
Tato ukázka demonstruje integraci vrstvy hostování se třídami v oboru názvů <xref:System.Web.Routing>. Třídy v oboru názvů <xref:System.Web.Routing> umožňují aplikaci používat adresy URL, které přímo neodpovídají fyzickému prostředku. Použití webového směrování umožňuje vývojářům vytvářet virtuální adresy pro protokol HTTP, které jsou pak namapovány zpět na skutečné služby WCF. To je užitečné v případě, že je nutné hostovat služby WCF, aniž by vyžadovaly fyzický soubor nebo prostředek, nebo pokud jsou k dispozici služby s adresami URL, které neobsahují soubory, jako je například. html nebo. aspx. Tato ukázka předvádí, jak použít třídu <xref:System.Web.Routing.RouteTable> k vytvoření virtuálních identifikátorů URI, které jsou mapovány na spuštěné služby definované v souboru Global. asax. 

> [!NOTE]
> Třídy v oboru názvů <xref:System.Web.Routing> fungují pouze pro služby hostované prostřednictvím protokolu HTTP.  
  
V tomto příkladu se používá WCF k vytvoření dvou kanálů RSS: `movies` informační kanál a `channels`ový kanál. Adresy URL pro aktivaci služeb neobsahují rozšíření a jsou registrovány v metodě `Application_Start` `Global` třídy odvozené od třídy <xref:System.Web.HttpApplication>.  
  
> [!NOTE]
> Tato ukázka funguje jenom v Internetová informační služba (IIS) 7,0 a novějším, protože služba IIS 6,0 používá jinou metodu pro podporu adres URL bez přípony.  

#### <a name="to-download-this-sample"></a>Stažení této ukázky
  
Tato ukázka již může být v počítači nainstalována. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>Použití této ukázky  
  
1. Pomocí sady Visual Studio otevřete soubor WebRoutingIntegration. sln.  
  
2. Chcete-li spustit řešení a spustit webový vývojový server, stiskněte klávesu F5.  
  
     Zobrazí se výpis adresáře pro ukázku. Všimněte si, že neexistují žádné soubory s příponou souboru. svc.  
  
3. Do adresního řádku přidejte `movies` k adrese URL, aby četl `http://localhost:[port]/movies` a stiskněte klávesu ENTER.  
  
     Informační kanál filmy se zobrazí v prohlížeči.  
  
4. Do adresního řádku přidejte `channels` k adrese URL, která je čtena `http://localhost:[port]/channels` a stiskněte klávesu ENTER.  
  
     Informační kanál kanály se zobrazí v prohlížeči.  
  
5. Stisknutím kombinace kláves ALT + F4 zavřete webový prohlížeč.  
  
     Pokud se vývojový server neukončil, klikněte pravým tlačítkem myši na ikonu oznamovací oblasti a vyberte **zastavit**.  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>Použití této ukázky při hostování ve službě IIS  
  
1. Pomocí sady Visual Studio otevřete soubor WebRoutingIntegration. sln.  
  
2. Sestavte projekt stisknutím kombinace kláves CTRL + SHIFT + B.  
  
3. Vytvoření webové aplikace ve Správci služby Internetová informační služba (IIS).  
  
    1. Ve Správci služby IIS klikněte pravým tlačítkem na **výchozí web** a vyberte **Přidat aplikaci**.  
  
    2. Jako **alias**zadejte `WebRoutingIntegration`.  
  
    3. Pro **fyzickou cestu**vyberte složku služby v rámci projektu.  
  
    4. Stiskněte **OK**.  
  
4. Spusťte aplikaci kliknutím pravým tlačítkem myši na webovou aplikaci a výběrem **možnosti spravovat aplikaci** a následným kliknutím na tlačítko **Procházet**.  
  
5. Do adresního řádku přidejte `movies` k adrese URL, která je čtena `http://localhost:[port]/movies` a stiskněte klávesu ENTER.  
  
     Informační kanál filmy se zobrazí v prohlížeči.  
  
6. Do adresního řádku přidejte `channels` k adrese URL, která je čtena `http://localhost:[port]/channels` a stiskněte klávesu ENTER.  
  
     Informační kanál kanály se zobrazí v prohlížeči.  
  
7. Stisknutím kombinace kláves ALT + F4 zavřete webový prohlížeč.  
  
 Tato ukázka předvádí, že hostující vrstva je schopna sestavovat s třídami v oboru názvů <xref:System.Web.Routing> pro směrování žádostí o služby hostované přes protokol HTTP.  
  
> [!NOTE]
> Pokud je nastavená na verzi 2, musíte aktualizovat výchozí verzi fondu aplikací na .NET Framework 4.  
  
## <a name="see-also"></a>Viz také:

- [Hostování technologie AppFabric a ukázky trvalosti](https://go.microsoft.com/fwlink/?LinkId=193961)
