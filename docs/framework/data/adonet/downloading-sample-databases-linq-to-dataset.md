---
title: Stažení ukázkové databáze (LINQ na DataSet)
ms.date: 03/30/2017
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
ms.openlocfilehash: f2488b0e1bfc578679a2a2802c332439f374a341
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763050"
---
# <a name="downloading-sample-databases-linq-to-dataset"></a>Stažení ukázkové databáze (LINQ na DataSet)
Ukázky a návody v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dokumentace použít ukázkovou databázi AdventureWorks. Tento produkt zdarma si můžete stáhnout z webu Microsoft download. Ukázky a návody v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dokumentace použít jako úložiště dat serveru SQL Server. SQL Server Express Edition, která je k dispozici bezplatně, můžete také použít jako úložiště dat místo systému SQL Server.  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a>Stažení a instalaci databázi AdventureWorks  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a>Chcete-li stáhnout a nainstalovat ukázkovou databázi AdventureWorks pro SQL Server  
  
1.  Otevřete Internet Explorer.  
  
2.  Přejděte na [SQL Server 2005 ukázky a ukázkové databáze](http://go.microsoft.com/fwlink/?linkid=31046) webu.  
  
3.  Postupujte podle pokynů pro stahování ukázkovou databázi AdventureWorks pro váš typ procesoru (například AdventureWorksDB.msi) a uložte. Soubor MSI do místního počítače.  
  
4.  Pokud máte předchozí verzi AdventureWorks nainstalovat z stahování nebo během instalace systému SQL Server, je nutné ji odebrat před spuštěním AdventureWorks.msi.  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a>Chcete-li odebrat předchozí stahování ukázkovou databázi AdventureWorks  
  
1.  Vyřaďte databázi AdventureWorks nebo AdventureWorksDW.  
  
2.  Z **přidat nebo odebrat programy**, vyberte **AdventureWorksDB** nebo **AdventureWorksBI** a klikněte na tlačítko **odebrat**.  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a>Chcete-li odebrat dříve pomocí instalačního programu nainstalovat ukázkovou databázi AdventureWorks  
  
1.  Vyřaďte databázi AdventureWorks nebo AdventureWorksDW.  
  
2.  Z **přidat nebo odebrat programy**, vyberte **Microsoft SQL Server 2005** a klikněte na tlačítko **změnu**.  
  
3.  Z **výběr součásti**, vyberte **součásti pracovní stanice** a pak klikněte na **Další**.  
  
4.  Z **Vítá vás Průvodce instalací serveru SQL**, klikněte na tlačítko **Další**.  
  
5.  Z **kontroly konfigurace systému**, klikněte na tlačítko **Další**.  
  
6.  Z **změnit nebo odebrat instanci**, klikněte na tlačítko **změnit nainstalované komponenty**.  
  
7.  Z **výběr funkce**, rozbalte **dokumentace, ukázky a ukázkové databáze** uzlu.  
  
8.  Vyberte **ukázkový kód a aplikace**. Rozbalte položku **ukázkové databáze**, vyberte v ukázkové databázi odebrat, a vyberte **celá funkce nedostupná**. Klikněte na tlačítko **Další**.  
  
9. Klikněte na tlačítko **nainstalovat** a dokončete Průvodce instalací.  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a>Připojit soubory AdventureWorks ukázkové databáze na instanci systému SQL Server  
  
1.  Po souboru ukázkové databáze instalačního souboru stáhl, dvakrát klikněte **AdventureWorksDB.msi** souboru (nebo soubor, který jste stáhli) pro instalaci databáze. Ve výchozím nastavení je databáze nainstalována na c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.  
  
2.  Připojte soubory databáze AdventureWorks do instance systému SQL Server, a to spuštěním následujícího skriptu SQLCMD nebo SQL Server Management Studio:  
  
    ```  
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     Pokud jste nainstalovali tyto soubory na jinou jednotku nebo adresář, musíte cesty změnit správně před spuštěním `sp_attach_db` uložené procedury.  
  
## <a name="downloading-sql-server-express-edition"></a>Stahování systému SQL Server Express Edition  
 Ukázky a návody v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] části používat SQL Server 2005 jako úložiště dat ale můžete upravit tak, aby místo toho použít SQL Server Express Edition. SQL Server Express Edition je k dispozici bezplatně a je možné znovu distribuovat ji s aplikacemi. Pokud používáte Visual Studio, SQL Server Express Edition je součástí verze Pro a vyšší.  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a>Stáhněte a nainstalujte SQL Server Express Edition  
  
1.  Spusťte Internet Explorer.  
  
2.  Přejděte na [Microsoft SQL Server 2005 Express Edition](http://go.microsoft.com/fwlink/?LinkID=31070) stránce pro stažení.  
  
3.  Postupujte podle pokynů k instalaci na webu.  
  
## <a name="see-also"></a>Viz také  
 [Začínáme](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
