---
title: Ukázka integrace názvového prostoru SystemWebRouting
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 944eb8f2bd907308e60525f8917fcad826caa472
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932063"
---
# <a name="systemwebrouting-integration-sample"></a>Ukázka integrace názvového prostoru SystemWebRouting
V této ukázce integration hostování vrstvy s třídami v <xref:System.Web.Routing> oboru názvů. Třídy v <xref:System.Web.Routing> oboru názvů umožňují aplikaci pro použití adresy URL, které neodpovídají přímo fyzické prostředky. Použití směrování webových umožňuje vývojářům vytvářet virtuální adresy pro protokol HTTP, které jsou pak mapována na skutečné služby WCF. To je užitečné, když bez nutnosti fyzického souboru nebo prostředku, musí být hostovaný ve službě WCF, nebo když služby musí přistupovat pomocí adresy URL, které neobsahují soubory, jako jsou HTML nebo .aspx. Tato ukázka předvádí, jak využívat <xref:System.Web.Routing.RouteTable> třídy za účelem vytvoření virtuální identifikátory URI, která je namapována na spuštění služby definované v souboru global.asax. 

> [!NOTE]
>  Třídy v <xref:System.Web.Routing> obor názvů fungovat pouze pro služby hostované přes protokol HTTP.  
  
Tento příklad používá k vytvoření dvou informační kanály RSS WCF: `movies` informační kanál a `channels` informačního kanálu. Adresy URL k aktivaci služby neobsahují rozšíření a jsou registrované ve `Application_Start` metodu `Global` třída odvozená z <xref:System.Web.HttpApplication> třídy.  
  
> [!NOTE]
>  Tento příklad funguje pouze v Internetové informační služby (IIS) 7.0 a novější, jako služby IIS 6.0 používá jinou metodu pro podporu adres URL bez přípon.  

#### <a name="to-download-this-sample"></a>Chcete-li stáhnout tuto ukázku
  
Tato ukázka může již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí sady Visual Studio, otevřete soubor WebRoutingIntegration.sln.  
  
2.  Spuštění řešení a spustit webový server vývoje, stiskněte klávesu F5.  
  
     Zobrazí se seznam adresářů pro vzorku. Všimněte si, že neexistují žádné soubory s příponou souboru .svc.  
  
3.  Na panelu Adresa přidat `movies` na adresu URL, takže se načte `http://localhost:[port]/movies` a stiskněte klávesu ENTER.  
  
     Informační kanál videa se zobrazí v prohlížeči.  
  
4.  Na panelu Adresa přidat `channels` na adresu URL, to je čtení `http://localhost:[port]/channels` a stiskněte klávesu ENTER.  
  
     Informační kanály kanál se zobrazí v prohlížeči.  
  
5.  Zavřete webový prohlížeč, stisknutím klávesy ALT + F4.  
  
     Pokud není ukončený vývojový server, klikněte pravým tlačítkem na ikonu v oznamovací oblasti a vyberte **Zastavit**.  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>Pro fungování této ukázky, když jsou hostované ve službě IIS  
  
1.  Pomocí sady Visual Studio, otevřete soubor WebRoutingIntegration.sln.  
  
2.  Sestavte projekt, stisknutím kombinace kláves CTRL + SHIFT + B.  
  
3.  Vytvoření webové aplikace ve Správci Internetové informační služby (IIS).  
  
    1.  Ve Správci služby IIS klikněte pravým tlačítkem myši **výchozí webový server** a vyberte **přidat aplikaci**.  
  
    2.  Pro **alias**, zadejte v `WebRoutingIntegration`.  
  
    3.  Pro **fyzická cesta**, vyberte složku služby v rámci projektu.  
  
    4.  Stisknutím klávesy **OK**.  
  
4.  Spuštění aplikace, že pravým tlačítkem myši na webovou aplikaci a vyberete **spravovat aplikaci** a potom **Procházet**.  
  
5.  Na panelu Adresa přidat `movies` na adresu URL, to je čtení `http://localhost:[port]/movies` a stiskněte klávesu ENTER.  
  
     Informační kanál videa se zobrazí v prohlížeči.  
  
6.  Na panelu Adresa přidat `channels` na adresu URL, to je čtení `http://localhost:[port]/channels` a stiskněte klávesu ENTER.  
  
     Informační kanály kanál se zobrazí v prohlížeči.  
  
7.  Zavřete webový prohlížeč, stisknutím klávesy ALT + F4.  
  
 Tento příklad ukazuje, že je schopen sestavování s třídami v hostování vrstvy <xref:System.Web.Routing> obor názvů pro směrování požadavků služby hostované přes protokol HTTP.  
  
> [!NOTE]
>  Je nutné aktualizovat na verzi fondu aplikací výchozí, aby [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] Pokud je nastavené na verzi 2.  
  
## <a name="see-also"></a>Viz také  
 [Hostování AppFabric a ukázky trvalosti](http://go.microsoft.com/fwlink/?LinkId=193961)
