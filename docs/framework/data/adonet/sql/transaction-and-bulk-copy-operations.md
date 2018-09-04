---
title: Transakce a operace hromadného kopírování
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f6f0cbc9-f7bf-4d6e-875f-ad1ba0b4aa62
ms.openlocfilehash: 24657f541daf5bb098f8db3b59a3241ecf832d39
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515076"
---
# <a name="transaction-and-bulk-copy-operations"></a>Transakce a operace hromadného kopírování
Operace hromadného kopírování lze provést jako izolované operace nebo jako součást více transakcí kroku. Tato druhou možnost umožňuje provádět více než jednu operaci hromadného kopírování v rámci jedné transakce a také provádění jiných operací databáze (například vložení, aktualizace a odstranění), ale stále mít možnost potvrzení nebo vrácení zpět celou transakci.  
  
 Ve výchozím nastavení se provádí operaci hromadného kopírování jako izolované operace. Dojde k operaci hromadného kopírování tak beztransakční nebude mít možnost vrácení zpět. Pokud je potřeba vrátit zpět nebo její část hromadného kopírování při výskytu chyby, můžete použít <xref:System.Data.SqlClient.SqlBulkCopy>– spravované transakce, proveďte operaci hromadného kopírování v rámci existující transakce nebo být uveden v **System.Transactions** <xref:System.Transactions.Transaction>.  
  
## <a name="performing-a-non-transacted-bulk-copy-operation"></a>Provádění beztransakční hromadného kopírování  
 Následující konzolové aplikace ukazuje, co se stane, když beztransakční hromadného kopírování dojde k chybě partway prostřednictvím operace.  
  
 V příkladu se zdrojové tabulky a cílová tabulka zahrnují `Identity` sloupec s názvem **ProductID**. Kód nejprve připraví cílové tabulky tak, že odstraníte všechny řádky a následného vložení jeden řádek, jehož **ProductID** se ví, že existují ve zdrojové tabulce. Ve výchozím nastavení, novou hodnotu `Identity` sloupec je vygenerována v cílové tabulce pro každý řádek přidán. V tomto příkladu je nastavena možnost, když je otevřeno připojení, která vynutí procesu hromadného načtení použít `Identity` místo hodnoty ze zdrojové tabulky.  
  
 Pomocí provádí se operace hromadného kopírování <xref:System.Data.SqlClient.SqlBulkCopy.BatchSize%2A> vlastnost nastavená na hodnotu 10. Při operaci zjistí neplatný řádek, je vyvolána výjimka. V tomto příkladu první operaci hromadného kopírování je, která nepodporuje transakce. Všechny listy zkopírovat až do chvíle, chyby jsou potvrzeny; dávka obsahuje duplicitní klíč se vrátí zpět, a operaci hromadného kopírování je zastaven před zpracováním jiných dávky.  
  
> [!NOTE]
>  Tato ukázka se nespustí, pokud jste vytvořili pracovní tabulky, jak je popsáno v [příklad nastavení hromadného kopírování](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Tento kód je k dispozici k předvedení syntaxe pro používání **SqlBulkCopy** pouze. Pokud zdrojové a cílové tabulky jsou umístěny ve stejné instanci systému SQL Server, je jednodušší a rychlejší je použít [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] `INSERT … SELECT` příkaz Kopírovat data.  
  
 [!code-csharp[DataWorks SqlBulkCopy.DefaultTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.DefaultTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.DefaultTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.DefaultTransaction/VB/source.vb#1)]  
  
## <a name="performing-a-dedicated-bulk-copy-operation-in-a-transaction"></a>Provádění vyhrazené hromadného kopírování v transakci  
 Ve výchozím nastavení je operaci hromadného kopírování vlastní transakce. Pokud chcete provést vyhrazené hromadného kopírování, vytvořte novou instanci třídy <xref:System.Data.SqlClient.SqlBulkCopy> pomocí připojovacího řetězce, nebo použít existující <xref:System.Data.SqlClient.SqlConnection> objekt bez aktivní transakce. V každém scénáři operaci hromadného kopírování vytvoří a potom potvrzení nebo vrátí zpět transakce.  
  
 Můžete explicitně určit <xref:System.Data.SqlClient.SqlBulkCopyOptions.UseInternalTransaction> možnost <xref:System.Data.SqlClient.SqlBulkCopy> konstruktoru třídy explicitně vyvolat operaci hromadného kopírování pro spuštění ve své vlastní transakce, způsobí každé dávky operaci hromadného kopírování ke spuštění v rámci samostatných transakcích.  
  
> [!NOTE]
>  Protože různé listy jsou provedeny v různých transakcí, pokud dojde k chybě při operaci hromadného kopírování, bude vrácena zpět všechny řádky do aktuální dávky, ale řádky z předchozích dávek zůstanou v databázi.  
  
 Následující konzolové aplikace je podobný jako předchozí příklad s jednou výjimkou: V tomto příkladu operaci hromadného kopírování spravuje svou vlastní transakce. Všechny listy zkopírovat až do chvíle, chyby jsou potvrzeny; dávka obsahuje duplicitní klíč se vrátí zpět, a operaci hromadného kopírování je zastaven před zpracováním jiných dávky.  
  
> [!IMPORTANT]
>  Tato ukázka se nespustí, pokud jste vytvořili pracovní tabulky, jak je popsáno v [příklad nastavení hromadného kopírování](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Tento kód je k dispozici k předvedení syntaxe pro používání **SqlBulkCopy** pouze. Pokud zdrojové a cílové tabulky jsou umístěny ve stejné instanci systému SQL Server, je jednodušší a rychlejší je použít [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] `INSERT … SELECT` příkaz Kopírovat data.  
  
 [!code-csharp[DataWorks SqlBulkCopy.InternalTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.InternalTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.InternalTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.InternalTransaction/VB/source.vb#1)]  
  
## <a name="using-existing-transactions"></a>Použití existující transakce  
 Můžete zadat existující <xref:System.Data.SqlClient.SqlTransaction> objektu jako parametr <xref:System.Data.SqlClient.SqlBulkCopy> konstruktoru. V takovém případě se provádí operaci hromadného kopírování v existující transakce a se neprovedly žádné změny stavu transakce (to znamená, ho potvrzené ani přerušen). Díky tomu aplikace, aby zahrnovala operaci hromadného kopírování v rámci transakce s dalšími operacemi databáze. Nicméně pokud není zadán <xref:System.Data.SqlClient.SqlTransaction> objektu a předejte jí odkaz s hodnotou null a připojení má aktivní transakce, je vyvolána výjimka.  
  
 Pokud je potřeba vrátit zpět, celý hromadné operace kopírování, protože dojde k chybě nebo pokud hromadného kopírování by měly spouštět jako součást většího procesu, který může být vrácena zpět, můžete zadat <xref:System.Data.SqlClient.SqlTransaction> objektu <xref:System.Data.SqlClient.SqlBulkCopy> konstruktoru.  
  
 Následující aplikace konzoly je podobná první (beztransakční) příklad, s jednou výjimkou: v tomto příkladu operaci hromadného kopírování je součástí větší, externí transakci. Když dojde k chybě porušení primárního klíče, celá transakce bude vrácena zpět a žádné řádky se přidají do cílové tabulky.  
  
> [!IMPORTANT]
>  Tato ukázka se nespustí, pokud jste vytvořili pracovní tabulky, jak je popsáno v [příklad nastavení hromadného kopírování](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Tento kód je k dispozici k předvedení syntaxe pro používání **SqlBulkCopy** pouze. Pokud zdrojové a cílové tabulky jsou umístěny ve stejné instanci systému SQL Server, je jednodušší a rychlejší je použít [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] `INSERT … SELECT` příkaz Kopírovat data.  
  
 [!code-csharp[DataWorks SqlBulkCopy.SqlTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.SqlTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.SqlTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.SqlTransaction/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Operace hromadného kopírování na SQL Serveru](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
