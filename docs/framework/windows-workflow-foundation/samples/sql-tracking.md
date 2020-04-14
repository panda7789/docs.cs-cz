---
title: Sledování SQL
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: 72bfcaac2903b3e7fa5679422ad4feaa79e93211
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243177"
---
# <a name="sql-tracking"></a>Sledování SQL

Tato ukázka ukazuje, jak napsat vlastní SQL sledování účastníka, který zapisuje záznamy sledování do databáze SQL. Windows Workflow Foundation (WF) poskytuje sledování pracovního postupu pro získání přehledu o provádění instance pracovního postupu. Doba sledování runtime vyzařuje záznamy sledování pracovního postupu během provádění pracovního postupu. Další informace o sledování pracovního postupu naleznete v [tématu Sledování pracovního postupu a trasování](../workflow-tracking-and-tracing.md).

## <a name="use-the-sample"></a>Použijte vzorek

1. Ověřte, zda máte nainstalován server SQL Server 2008, SQL Server 2008 Express nebo novější. Skripty zabalené s ukázkou předpokládají použití instance SQL Express v místním počítači. Pokud máte jinou instanci, upravte před spuštěním ukázky skripty související s databází.

2. Databázi sledování serveru SQL Server vytvořte spuštěním souboru Trackingsetup.cmd v adresáři skriptů (\WF\Basic\Tracking\SqlTracking\CS\Scripts). Tím se vytvoří databáze s názvem TrackingSample.

   > [!NOTE]
   > Skript vytvoří databázi na výchozí instanci SQL Express. Pokud ji chcete nainstalovat do jiné instance databáze, upravte skript Trackingsetup.cmd.

3. Otevřete sqltrackingsample.sln v sadě Visual Studio 2010.

4. Řešení sestavte stisknutím **klávesy Ctrl**+**Shift**+**B.**

5. Stisknutím **klávesy F5** spusťte aplikaci.

   Otevře se okno prohlížeče a zobrazí výpis adresáře pro aplikaci.

6. V prohlížeči klikněte na Soubor StockPriceService.xamlx.

7. Prohlížeč zobrazí stránku StockPriceService, která obsahuje adresu WSDL místní služby. Zkopírujte tuto adresu.

   Příkladem adresy WSDL místní služby je `http://localhost:65193/StockPriceService.xamlx?wsdl`.

8. Pomocí Průzkumníka souborů spusťte testovacího klienta WCF (WcfTestClient.exe). Je umístěn v *adresáři Microsoft Visual Studio 10.0\Common7\IDE*.

9. V testovacím klientovi WCF klepněte na **nabídku Soubor** a vyberte **Přidat službu**. Vložte adresu místní služby do textového pole. Klepnutím na **tlačítko OK** zavřete dialogové okno.

10. V testovacím klientovi WCF poklepejte na **příkaz GetStockPrice**. Tím se `GetStockPrice` otevře operace, která přebírá `Contoso` jeden parametr, zadejte hodnotu a klepněte na tlačítko **Vyvolat**.

11. Vyzařované záznamy sledování jsou zapsány do databáze SQL. Chcete-li zobrazit záznamy sledování, otevřete databázi TrackingSample v aplikaci SQL Management Studio a přejděte do tabulek. Spuštěním výběrového dotazu v tabulkách se zobrazí data v rámci záznamů sledování uložených v příslušných tabulkách.

   Další informace o aplikaci SQL Server Management Studio naleznete [v tématu Introducing SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms). Stáhněte si SQL Server Management Studio [zde](https://aka.ms/ssmsfullsetup).

## <a name="uninstall-the-sample"></a>Odinstalace ukázky

1. Spusťte skript Trackingcleanup.cmd v ukázkovém adresáři (*\WF\Basic\Tracking\SqlTracking*).

    > [!NOTE]
    > Trackingcleanup.cmd pokusí odstranit databázi v místním počítači SQL Express. Pokud používáte jinou instanci serveru SQL, upravte Trackingcleanup.cmd.

> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`

## <a name="see-also"></a>Viz také

- [Vzorky monitorování appfabricu](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
