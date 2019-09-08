---
title: Stahování ukázkových databází (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
ms.openlocfilehash: c67ee699cf594f476a728c7345b47b0c32dea7ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795176"
---
# <a name="downloading-sample-databases-linq-to-dataset"></a>Stahování ukázkových databází (LINQ to DataSet)
Ukázky a návody v dokumentaci LINQ to DataSet používají ukázkovou databázi AdventureWorks. Zdarma si můžete stáhnout tento produkt z webu služby Stažení softwaru společnosti Microsoft. Ukázky a návody v dokumentaci LINQ to DataSet používají SQL Server jako úložiště dat. SQL Server Express edice, která je k dispozici bezplatně, se dá použít také jako úložiště dat místo SQL Server.  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a>Stažení a instalace databáze AdventureWorks  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a>Stažení a instalace ukázkové databáze AdventureWorks pro SQL Server  
  
1. Otevřete Internet Explorer.  
  
2. Přejít na web [SQL Server 2005 Samples a vzorové databáze](https://go.microsoft.com/fwlink/?linkid=31046) .  
  
3. Postupujte podle pokynů pro stažení ukázkové databáze AdventureWorks pro typ procesoru (například AdventureWorksDB. msi) a uložte soubor. Soubor MSI do místního počítače.  
  
4. Pokud máte nainstalovanou předchozí verzi AdventureWorks ze souboru ke stažení nebo během instalace SQL Server, je nutné ji před spuštěním souboru AdventureWorks. msi odebrat.  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a>Odebrání předchozího stažení ukázkové databáze AdventureWorks  
  
1. Přetáhněte databázi AdventureWorks nebo AdventureWorksDW.  
  
2. V nabídce **Přidat nebo odebrat programy**vyberte **AdventureWorksDB** nebo **AdventureWorksBI** a klikněte na **Odebrat**.  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a>Odebrání ukázkové databáze AdventureWorks, která byla dříve nainstalována pomocí instalačního programu  
  
1. Přetáhněte databázi AdventureWorks nebo AdventureWorksDW.  
  
2. V nabídce **Přidat nebo odebrat programy**vyberte **Microsoft SQL Server 2005** a klikněte na **změnit**.  
  
3. V části **Výběr součástí**vyberte **komponenty pracovní stanice** a pak klikněte na **Další**.  
  
4. V **okně Vítá vás Průvodce instalací SQL Server**klikněte na **Další**.  
  
5. V případě **kontroly konfigurace systému**klikněte na tlačítko **Další**.  
  
6. V části **změnit nebo odebrat instanci**klikněte na **změnit nainstalované součásti**.  
  
7. V části **Výběr funkcí**rozbalte uzel **dokumentace, ukázky a ukázkové databáze** .  
  
8. Vyberte **vzorový kód a aplikace**. Rozbalte položku **ukázkové**databáze, vyberte ukázkovou databázi, kterou chcete odebrat, a vyberte možnost **Celá součást nebude k dispozici**. Klikněte na **Další**.  
  
9. Klikněte na **instalovat** a dokončete Průvodce instalací.  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a>Připojení ukázkových databázových souborů AdventureWorks k instanci SQL Server  
  
1. Po stažení souboru instalačního programu ukázkové databáze dvakrát klikněte na soubor **AdventureWorksDB. msi** (nebo na soubor, který jste stáhli) pro instalaci databáze. Ve výchozím nastavení je databáze nainstalovaná ve složce c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.  
  
2. Připojte soubory databáze AdventureWorks k instanci SQL Server spuštěním následujícího skriptu Script SQLCMD nebo SQL Server Management Studio:  
  
    ```sql
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     Pokud jste tyto soubory nainstalovali na jinou jednotku nebo adresář, musíte je před `sp_attach_db` spuštěním uložené procedury upravit.  
  
## <a name="downloading-sql-server-express-edition"></a>Stahuje se edice SQL Server Express.  
 Ukázky a návody v části LINQ to DataSet jako úložiště dat používají SQL Server 2005, ale dají se místo toho upravit tak, aby používala SQL Server Express Edition. Edice SQL Server Express je k dispozici bez poplatků a je možné ji znovu distribuovat s aplikacemi. Pokud používáte sadu Visual Studio, je SQL Server Express edice součástí edice sady pro a vyšší.  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a>Stažení a instalace edice SQL Server Express  
  
1. Spusťte aplikaci Internet Explorer.  
  
2. Přejít na stránku pro stažení [edice Microsoft SQL Server 2005 Express](https://go.microsoft.com/fwlink/?LinkID=31070) .  
  
3. Postupujte podle pokynů k instalaci na webu.  
  
## <a name="see-also"></a>Viz také:

- [Začínáme](getting-started-linq-to-dataset.md)
