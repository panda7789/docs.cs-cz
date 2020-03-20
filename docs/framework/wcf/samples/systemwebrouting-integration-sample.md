---
title: Ukázka integrace názvového prostoru SystemWebRouting
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 2f12d80085e3ac27dac8ce80b6bb09f69337bfd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143951"
---
# <a name="systemwebrouting-integration-sample"></a>Ukázka integrace názvového prostoru SystemWebRouting
Tato ukázka ukazuje integraci hostitelské vrstvy s <xref:System.Web.Routing> třídami v oboru názvů. Třídy v <xref:System.Web.Routing> oboru názvů umožňují aplikaci používat adresy URL, které přímo neodpovídají fyzickému prostředku. Použití webového směrování umožňuje vývojáři vytvářet virtuální adresy pro protokol HTTP, které jsou pak mapovány zpět na skutečné služby WCF. To je užitečné v případě, že služba WCF musí být hostována bez nutnosti fyzického souboru nebo prostředku, nebo pokud musí být ke službám přistupováno pomocí adres URL, které neobsahují soubory jako HTML nebo ASPX. Tato ukázka ukazuje, <xref:System.Web.Routing.RouteTable> jak využít třídu k vytvoření virtuálních identifikátorů URI, které mapují na spuštěné služby definované v global.asax.

> [!NOTE]
> Třídy v <xref:System.Web.Routing> oboru názvů fungují pouze pro služby hostované přes protokol HTTP.  
  
Tento příklad používá WCF k vytvoření dvou `movies` informačních `channels` kanálů RSS: informačního kanálu a informačního kanálu. Adresy URL pro aktivaci služeb neobsahují rozšíření a `Application_Start` jsou registrovány v metodě `Global` třídy odvozené z <xref:System.Web.HttpApplication> třídy.  
  
> [!NOTE]
> Tato ukázka funguje pouze v internetové informační službě (IIS) 7.0 a novějších, protože služba IIS 6.0 používá jinou metodu pro podporu adres URL bez rozšíření.  

#### <a name="to-download-this-sample"></a>Chcete-li stáhnout tuto ukázku
  
Tato ukázka je již pravděpodobně nainstalována v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  

`<InstallDrive>:\WF_WCF_Samples`  

 Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  

`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>Chcete-li použít tento vzorek  
  
1. V sadě Visual Studio otevřete soubor WebRoutingIntegration.sln.  
  
2. Chcete-li spustit řešení a spustit web development server, stiskněte klávesu F5.  
  
     Zobrazí se seznam adresářů pro ukázku. Všimněte si, že neexistují žádné soubory s příponou souboru SVC.  
  
3. V adresním řádku `movies` přidejte adresu URL, `http://localhost:[port]/movies` aby se přečetla, a stiskněte klávesu ENTER.  
  
     V prohlížeči se zobrazí kanál o filmech.  
  
4. V adresním řádku `channels` přidejte do adresy `http://localhost:[port]/channels` URL, aby se přečetla, a stiskněte klávesu ENTER.  
  
     Kanál kanálů se zobrazí v prohlížeči.  
  
5. Zavřete webový prohlížeč stisknutím kláves ALT+F4.  
  
     Pokud se vývojový server neukončoval, klepněte pravým tlačítkem myši na ikonu oznamovací oblasti a vyberte příkaz **Zastavit**.  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>Použití této ukázky při hostování ve správě ve správě iis  
  
1. V sadě Visual Studio otevřete soubor WebRoutingIntegration.sln.  
  
2. Sestavte projekt stisknutím kombinace kláves CTRL+SHIFT+B.  
  
3. Vytvořte webovou aplikaci ve Správci Internetové informační služby (IIS).  
  
    1. Ve Správci služby IIS klepněte pravým tlačítkem myši na **výchozí web** a vyberte příkaz **Přidat aplikaci**.  
  
    2. Do **aliasu**zadejte . `WebRoutingIntegration`  
  
    3. Pro **fyzickou cestu**vyberte složku Service uvnitř projektu.  
  
    4. Stiskněte **OK**.  
  
4. Spusťte aplikaci tak, že klepnete pravým tlačítkem myši na webovou aplikaci a vyberete **možnost Spravovat aplikaci** a potom **procházet**.  
  
5. V adresním řádku `movies` přidejte do adresy `http://localhost:[port]/movies` URL, aby se přečetla, a stiskněte klávesu ENTER.  
  
     V prohlížeči se zobrazí kanál o filmech.  
  
6. V adresním řádku `channels` přidejte do adresy `http://localhost:[port]/channels` URL, aby se přečetla, a stiskněte klávesu ENTER.  
  
     Kanál kanálů se zobrazí v prohlížeči.  
  
7. Zavřete webový prohlížeč stisknutím kláves ALT+F4.  
  
 Tato ukázka ukazuje, že hostitelská vrstva je <xref:System.Web.Routing> schopna skládat s třídami v oboru názvů pro směrování požadavků služeb hostovaných přes protokol HTTP.  
  
> [!NOTE]
> Pokud je výchozí verze fondu aplikací nastavena na verzi 2, je nutné aktualizovat výchozí verzi fondu aplikací na rozhraní .NET Framework 4.  
  
## <a name="see-also"></a>Viz také

- [Ukázky hostování a perzistence appfabric](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
