---
title: "Ukázka integrace názvového prostoru SystemWebRouting"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: de8869956a59cb47623dbc4d84763e19d6f181bf
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2018
---
# <a name="systemwebrouting-integration-sample"></a>Ukázka integrace názvového prostoru SystemWebRouting
Tento příklad znázorňuje hostování vrstvě integrace s třídy v <xref:System.Web.Routing> oboru názvů. Třídy v <xref:System.Web.Routing> obor názvů povolit aplikaci použití adres URL, které neodpovídají přímo na fyzický prostředek. Použití směrování webové umožňuje vývojáři k vytvoření virtuální adresy pro protokol HTTP, která jsou pak mapována na skutečné [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby. To je užitečné, když musí být hostované služby WCF, bez nutnosti fyzického souboru či prostředku nebo když služby je nutné přistupovat pomocí adresy URL, které neobsahují soubory, jako je například HTML nebo .aspx. Tento příklad ukazuje, jak využívat <xref:System.Web.Routing.RouteTable> třídy za účelem vytvoření virtuální identifikátory URI, které jsou namapovány na spuštění služby definované v souboru global.asax. 

> [!NOTE]
>  Třídy v <xref:System.Web.Routing> obor názvů fungovat pouze pro služby hostované přes protokol HTTP.  
  
Tento příklad používá k vytvoření dvou informačních kanálů RSS WCF: `movies` kanálu a `channels` informačního kanálu. Adresy URL k aktivaci služby neobsahují rozšíření a jsou zaregistrovány v `Application_Start` metodu `Global` třída odvozená z <xref:System.Web.HttpApplication> třídy.  
  
> [!NOTE]
>  Tato ukázka funguje pouze v Internetové informační služby (IIS) 7.0 a novější, jako služby IIS 6.0 používá jinou metodu pro podporu adresy URL bez přípony.  

#### <a name="to-download-this-sample"></a>Chcete-li stáhnout tuto ukázku
  
Tato ukázka může již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí sady Visual Studio, otevřete soubor WebRoutingIntegration.sln.  
  
2.  Pokud chcete spustit řešení a spustí webový server vývoj, stisknutím klávesy F5.  
  
     Zobrazí se pro vzorovou výpis adresáře. Všimněte si, že neexistují žádné soubory s příponou souboru .svc.  
  
3.  Na panelu Adresa přidat `movies` na adresu URL, takže to čte http://localhost: [port] / filmy a stiskněte klávesu ENTER.  
  
     Informační kanál filmy se zobrazí v prohlížeči.  
  
4.  Na panelu Adresa přidat `channels` na adresu URL, takže se čtení http://localhost: [port] / kanálů a stiskněte klávesu ENTER.  
  
     Informační kanál kanály se zobrazí v prohlížeči.  
  
5.  Zavřete webový prohlížeč, stisknutím klávesy ALT + F4.  
  
     Pokud není ukončený vývojový server, klikněte pravým tlačítkem myši na ikonu v oznamovací oblasti a vyberte **Zastavit**.  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>Při použití tohoto příkladu při hostovaný ve službě IIS  
  
1.  Pomocí sady Visual Studio, otevřete soubor WebRoutingIntegration.sln.  
  
2.  Sestavení projektu, stisknutím kombinace kláves CTRL + SHIFT + B.  
  
3.  Vytvoření webové aplikace ve Správci Internetové informační služby (IIS).  
  
    1.  Ve Správci služby IIS klikněte pravým tlačítkem **Default Web Site** a vyberte **přidat aplikaci**.  
  
    2.  Pro **alias**, zadejte v `WebRoutingIntegration`.  
  
    3.  Pro **fyzická cesta**, vyberte složku služby v projektu.  
  
    4.  Press **OK**.  
  
4.  Spustit aplikaci, tak, že kliknete pravým tlačítkem na webové aplikace a výběr **spravovat aplikace** a potom **Procházet**.  
  
5.  Na panelu Adresa přidat `movies` na adresu URL, takže se čtení http://localhost: [port] / filmy a stiskněte klávesu ENTER.  
  
     Informační kanál filmy se zobrazí v prohlížeči.  
  
6.  Na panelu Adresa přidat `channels` na adresu URL, takže se čtení http://localhost: [port] / kanálů a stiskněte klávesu ENTER.  
  
     Informační kanál kanály se zobrazí v prohlížeči.  
  
7.  Zavřete webový prohlížeč, stisknutím klávesy ALT + F4.  
  
 Tento příklad ukazuje, že hostování vrstva je schopný skládání s třídy v <xref:System.Web.Routing> obor názvů pro směrování požadavků služby hostované přes protokol HTTP.  
  
> [!NOTE]
>  Je nutné aktualizovat výchozí verze fondu aplikací na [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] Pokud je nastaven na hodnotu verze 2.  
  
## <a name="see-also"></a>Viz také  
 [Ukázky trvalosti a hostování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
