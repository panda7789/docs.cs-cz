---
title: Sledování SQL
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: e2cb86a92e075d9117f2fe208f2044d4bc30dac9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710014"
---
# <a name="sql-tracking"></a>Sledování SQL
Tato ukázka předvádí, jak napsat vlastní sledování účastník SQL, který zapíše záznamy sledování k databázi SQL. Windows Workflow Foundation (WF) umožňuje získat přehled o spuštění instance pracovního postupu pro sledování pracovního postupu. Modul runtime sledování vysílá pracovního postupu při provádění pracovního postupu pro sledování záznamů. Další informace o sledování pracovního postupu najdete v tématu [pracovního postupu pro sledování a trasování](../workflow-tracking-and-tracing.md).

#### <a name="to-use-this-sample"></a>Pro fungování této ukázky

1.  Ověření je třeba SQL Server 2008, SQL Server 2008 Express nebo novější nainstalován. Skripty zabaleny s ukázkou předpokládá použití instance SQL Express na místním počítači. Pokud máte jinou instanci, upravte prosím databázi související skripty před spuštěním ukázky.

2.  Vytvořte databázi serveru SQL Server sledování spuštěním Trackingsetup.cmd v adresáři skriptů (\WF\Basic\Tracking\SqlTracking\CS\Scripts). Tím se vytvoří databázi s názvem TrackingSample.

    > [!NOTE]
    >  Tento skript vytvoří databázi na výchozí instanci systému SQL Express. Pokud chcete nainstalovat na jinou instanci databáze, upravte skript Trackingsetup.cmd.  
  
3.  Otevřete SqlTrackingSample.sln v sadě Visual Studio 2010.  
  
4.  Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.  
  
5.  Stisknutím klávesy F5 spusťte aplikaci.  
  
     Okno prohlížeče se otevře a zobrazí výpisu adresáře pro aplikaci.  
  
6.  V prohlížeči klikněte na tlačítko StockPriceService.xamlx.  
  
7.  Prohlížeč zobrazí na stránce StockPriceService, který obsahuje místní službě WSDL adresu. Zkopírujte tuto adresu.  
  
     Příkladem adresy místní služby WSDL je `http://localhost:65193/StockPriceService.xamlx?wsdl`.  
  
8.  Pomocí [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], spustit klienta testu WCF (WcfTestClient.exe). Je umístěn v adresáři sady Microsoft Visual Studio 10.0\Common7\IDE.  
  
9. Testovací klient WCF, klikněte na tlačítko **souboru** nabídky a vybereme **přidat službu**. Vložte adresu místní služby v textovém poli. Klikněte na tlačítko **OK** zavřete dialogové okno.  
  
10. Testovací klient WCF, dvakrát klikněte na tlačítko **GetStockPrice**. Tím se otevře `GetStockPrice` operace, která přijímá jeden parametr, typ hodnoty `Contoso` a klikněte na tlačítko **Invoke**.  
  
11. Emitovaný sledování záznamů se zapisují do služby SQL database. Chcete-li zobrazit záznamy sledování, otevřete TrackingSample databázi SQL Management Studio a přejděte do tabulky. Další informace o nástroji SQL Server Management Studio najdete v tématu [Představujeme SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=165645). SQL Server 2008 Management Studio Express si můžete stáhnout [tady](https://go.microsoft.com/fwlink/?LinkId=180520). Zpracování dotazu select a systémem tabulky zobrazí data v rámci záznamy sledování, které jsou uložené v obou tabulkách.  
  
#### <a name="to-uninstall-the-sample"></a>Chcete-li odinstalovat vzorku  
  
1.  Spusťte skript theTrackingcleanup.cmd v adresáři ukázkové (\WF\Basic\Tracking\SqlTracking).  
  
    > [!NOTE]
    >  Trackingcleanup.cmd pokusí odstranit databázi v místním počítači SQL Express. Pokud používáte jiné instance systému SQL server, upravte Trackingcleanup.cmd.

> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`  
  
## <a name="see-also"></a>Viz také:
- [Ukázky AppFabric monitorování](https://go.microsoft.com/fwlink/?LinkId=193959)
