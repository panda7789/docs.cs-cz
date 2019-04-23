---
title: Stažení ukázkových databází (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
ms.openlocfilehash: 1ef5a5ceac6a7f819551f6221b63197786ab4f09
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59339707"
---
# <a name="downloading-sample-databases-linq-to-dataset"></a>Stažení ukázkových databází (LINQ to DataSet)
Ukázky a návody v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dokumentaci použít ukázkovou databází AdventureWorks. Tento produkt zdarma si můžete stáhnout z webu společnosti Microsoft ke stažení. Ukázky a návody v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dokumentace ke službě použít jako úložiště dat serveru SQL Server. SQL Server Express Edition, která je k dispozici bez poplatků, může také sloužit jako úložiště dat místo SQL serveru.  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a>Stažení a instalace databáze AdventureWorks  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a>Ke stažení a instalaci ukázkové databáze AdventureWorks pro SQL Server  
  
1. Spusťte aplikaci Internet Explorer.  
  
2. Přejděte [SQL Server 2005 ukázky a ukázkových databází](https://go.microsoft.com/fwlink/?linkid=31046) webu.  
  
3. Postupujte podle pokynů ke stahování ukázkovou databází AdventureWorks pro váš typ procesoru (například AdventureWorksDB.msi) a uložte. Soubor MSI do místního počítače.  
  
4. Pokud máte předchozí verzi AdventureWorks nainstalovat z položky ke stažení nebo během instalace systému SQL Server, musíte ho odebrat před spuštěním AdventureWorks.msi.  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a>Chcete-li odebrat předchozí stahování ukázkovou databázi AdventureWorks  
  
1. Odpojení databáze AdventureWorks nebo AdventureWorksDW.  
  
2. Z **přidat nebo odebrat programy**vyberte **AdventureWorksDB** nebo **AdventureWorksBI** a klikněte na tlačítko **odebrat**.  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a>Chcete-li odebrat ukázkovou databázi AdventureWorks dříve nainstalovali pomocí instalačního programu  
  
1. Odpojení databáze AdventureWorks nebo AdventureWorksDW.  
  
2. Z **přidat nebo odebrat programy**vyberte **Microsoft SQL Server 2005** a klikněte na tlačítko **změnu**.  
  
3. Z **výběr součásti**vyberte **komponenty pracovní stanice** a potom klikněte na tlačítko **Další**.  
  
4. Z **Vítá vás Průvodce instalací SQL serveru**, klikněte na tlačítko **Další**.  
  
5. Z **kontroly konfigurace systému**, klikněte na tlačítko **Další**.  
  
6. Z **změnit nebo odebrat Instance**, klikněte na tlačítko **změnit nainstalované komponenty**.  
  
7. Z **výběr součástí**, rozbalte **dokumentaci, ukázky a ukázkových databází** uzlu.  
  
8. Vyberte **ukázkový kód a aplikace**. Rozbalte **ukázkových databází**, vybrat ukázkovou databázi chcete odebrat, vyberte **celé funkce bude k dispozici**. Klikněte na **Další**.  
  
9. Klikněte na tlačítko **nainstalovat** a dokončení Průvodce instalací.  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a>Připojit soubory ukázkové databáze AdventureWorks do instance systému SQL Server  
  
1. Po stažení ukázkové databáze instalačního programu soubor dvakrát klikněte **AdventureWorksDB.msi** souboru (nebo jste si stáhli) pro instalaci databáze. Ve výchozím nastavení je databáze nainstaloval do c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.  
  
2. Spuštěním následujícího skriptu SQLCMD nebo SQL Server Management Studio připojte soubory databáze AdventureWorks do instance systému SQL Server:  
  
    ```sql
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     Pokud jste nainstalovali tyto soubory na jinou jednotku nebo adresář, musí cesty odpovídajícím způsobem upravit, ještě před spuštěním `sp_attach_db` uložené procedury.  
  
## <a name="downloading-sql-server-express-edition"></a>Stahuje se SQL Server Express Edition  
 Ukázky a návody v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] část používat jako úložiště dat serveru SQL Server 2005, ale můžete upravit tak, aby místo toho použít SQL Server Express Edition. SQL Server Express Edition je k dispozici bez poplatků a je možné znovu distribuovat ji s aplikacemi. Pokud používáte Visual Studio, SQL Server Express Edition je součástí verze Pro a vyšší.  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a>Stáhněte si a nainstalujte SQL Server Express Edition  
  
1. Spusťte aplikaci Internet Explorer.  
  
2. Přejděte [Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070) stránce pro stažení.  
  
3. Postupujte podle pokynů k instalaci na webové stránce.  
  
## <a name="see-also"></a>Viz také:

- [Začínáme](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
