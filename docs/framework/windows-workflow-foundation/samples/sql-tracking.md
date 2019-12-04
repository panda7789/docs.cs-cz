---
title: Sledování SQL
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: c1bb4492695df3ff803dff893de24453d7c03dfb
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715568"
---
# <a name="sql-tracking"></a>Sledování SQL
Tato ukázka předvádí, jak napsat vlastního účastníka sledování SQL, který zapisuje záznamy sledování do databáze SQL. Programovací model Windows Workflow Foundation (WF) poskytuje sledování pracovního postupu, které vám umožní získat přehled o spuštění instance pracovního postupu. Sledovací modul Sledování generuje záznamy sledování pracovních postupů během provádění pracovního postupu. Další informace o sledování pracovního postupu najdete v tématu [sledování a trasování pracovních postupů](../workflow-tracking-and-tracing.md).

#### <a name="to-use-this-sample"></a>Použití této ukázky

1. Ověřte, že máte nainstalované SQL Server 2008 SQL Server 2008 Express nebo novější. Skripty, které jsou součástí ukázky, předpokládají použití instance SQL Express na místním počítači. Pokud máte jinou instanci, před spuštěním ukázky prosím upravte skripty související s databází.

2. Vytvořte databázi sledování SQL Server spuštěním Trackingsetup. cmd v adresáři Scripts (\WF\Basic\Tracking\SqlTracking\CS\Scripts). Tím se vytvoří databáze s názvem TrackingSample.

    > [!NOTE]
    > Skript vytvoří databázi ve výchozí instanci serveru SQL Express. Pokud ho chcete nainstalovat do jiné instance databáze, upravte skript Trackingsetup. cmd.

3. Otevřete SqlTrackingSample. sln v aplikaci Visual Studio 2010.

4. Stisknutím kombinace kláves CTRL + SHIFT + B Sestavte řešení.

5. Stisknutím klávesy F5 spusťte aplikaci.

     Otevře se okno prohlížeče a zobrazí se výpis adresáře pro aplikaci.

6. V prohlížeči klikněte na StockPriceService. xamlx.

7. Prohlížeč zobrazí stránku StockPriceService, která obsahuje adresu WSDL místní služby. Zkopírujte tuto adresu.

     Příklad adresy WSDL místní služby je `http://localhost:65193/StockPriceService.xamlx?wsdl`.

8. Pomocí Průzkumníka souborů spusťte testovacího klienta WCF (WcfTestClient. exe). Je umístěn v adresáři Microsoft Visual Studio 10.0 \ Common7\IDE.

9. V testovacím klientovi WCF klikněte na nabídku **soubor** a vyberte **Přidat službu**. Do textového pole vložte adresu místní služby. Kliknutím na tlačítko **OK** zavřete dialogové okno.

10. V testovacím klientovi WCF poklikejte na **GetStockPrice**. Tím se otevře operace `GetStockPrice`, která přijímá jeden parametr, zadáte hodnotu `Contoso` a kliknete na **vyvolat**.

11. Vypouštěné záznamy sledování se zapisují do SQL Database. Chcete-li zobrazit záznamy sledování, otevřete databázi TrackingSample ve službě SQL Management Studio a přejděte do tabulky. Další informace o SQL Server Management Studio najdete v tématu [Úvod do SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=165645). SQL Server 2008 Management Studio Express si můžete stáhnout [tady](https://go.microsoft.com/fwlink/?LinkId=180520). Spuštění dotazu SELECT v tabulkách zobrazuje data v záznamech sledování uložených v příslušných tabulkách.

#### <a name="to-uninstall-the-sample"></a>Odinstalace ukázky

1. Spusťte skript theTrackingcleanup. cmd v ukázkovém adresáři (\WF\Basic\Tracking\SqlTracking).

    > [!NOTE]
    > Trackingcleanup. cmd se pokusí odstranit databázi v místním počítači SQL Express. Pokud používáte jinou instanci systému SQL Server, upravte Trackingcleanup. cmd.

> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`

## <a name="see-also"></a>Viz také:

- [Ukázky monitorování technologie AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
