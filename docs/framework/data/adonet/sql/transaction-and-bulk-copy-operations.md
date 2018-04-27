---
title: Transakce a operace hromadného kopírování
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f6f0cbc9-f7bf-4d6e-875f-ad1ba0b4aa62
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 40494c887ffa48c6ebc7f020cb4d42eecbd08e75
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="transaction-and-bulk-copy-operations"></a>Transakce a operace hromadného kopírování
Operace hromadného kopírování lze provést jako izolované operace nebo jako součást více krok transakce. Tato druhou možnost umožňuje provádět více než jeden hromadné kopírování v rámci jedné transakce a také provádění jiných databázových operací (například vložení, aktualizace a odstranění) ale stále mít možnost potvrďte nebo vraťte zpět celou transakci.  
  
 Ve výchozím nastavení je jako izolované operaci provést operace hromadného kopírování. Hromadné kopírování nastane způsobem, beztransakční, se nebude mít možnost vrácení zpět. Pokud je nutné vrátit zpět nebo jeho část hromadné kopírování když dojde k chybě, můžete použít <xref:System.Data.SqlClient.SqlBulkCopy>-spravované transakce, provádět hromadné kopírování v rámci existující transakce nebo zařadit v **System.Transactions –** <xref:System.Transactions.Transaction>.  
  
## <a name="performing-a-non-transacted-bulk-copy-operation"></a>Provádění operace beztransakční hromadné kopírování  
 Následující konzolové aplikace zobrazuje, co se stane, když beztransakční hromadné operace kopírování dojde k chybě partway prostřednictvím operaci.  
  
 V příkladu se zdrojové tabulky a cílové tabulky obsahují `Identity` sloupec s názvem **ProductID**. Kód nejprve připraví cílové tabulky odstraněním všechny řádky a následného vložení jeden řádek, jehož **ProductID** se ví, že existují ve zdrojové tabulce. Ve výchozím nastavení pro novou hodnotu `Identity` vygenerování sloupce cílové tabulky pro každý řádek přidat. V tomto příkladu je možnost nastavit po otevření připojení, který vynutí procesu hromadného načtení používat `Identity` místo hodnoty ze zdrojové tabulky.  
  
 Hromadné kopírování se spustí s <xref:System.Data.SqlClient.SqlBulkCopy.BatchSize%2A> vlastnost nastavena na hodnotu 10. Při operaci zaznamená neplatný řádek, je vyvolána výjimka. V tomto prvním příkladu je operace hromadného kopírování, beztransakční. Všechny dávky zkopírovat až do chvíle, chyby se potvrdí; dávka obsahuje duplicitní klíč, je vrácena zpět a operace hromadného kopírování je byl zastaven před zpracováním jiných dávek.  
  
> [!NOTE]
>  Tato ukázka se nespustí, pokud jste vytvořili pracovní tabulky, jak je popsáno v [hromadné kopírování příklad instalace](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Tento kód je určen k předvedení syntaxe pro používání **SqlBulkCopy** pouze. Pokud zdrojové a cílové tabulky jsou umístěny ve stejné instanci systému SQL Server, je jednodušší a rychlejší použít [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] `INSERT … SELECT` příkaz Kopírovat data.  
  
 [!code-csharp[DataWorks SqlBulkCopy.DefaultTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.DefaultTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.DefaultTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.DefaultTransaction/VB/source.vb#1)]  
  
## <a name="performing-a-dedicated-bulk-copy-operation-in-a-transaction"></a>Provádění operace vyhrazené hromadné kopírování do transakce  
 Ve výchozím nastavení je operace hromadného kopírování vlastní transakce. Když chcete provést operace vyhrazené hromadné kopírování, vytvořit novou instanci třídy <xref:System.Data.SqlClient.SqlBulkCopy> připojovací řetězec, nebo použijte existující <xref:System.Data.SqlClient.SqlConnection> objektu bez aktivní transakce. V každém scénáři operace hromadného kopírování vytvoří a potom potvrdí nebo vrátí zpět transakci.  
  
 Můžete explicitně zadáte <xref:System.Data.SqlClient.SqlBulkCopyOptions.UseInternalTransaction> možnost <xref:System.Data.SqlClient.SqlBulkCopy> konstruktoru třídy explicitně způsobí operace hromadného kopírování na provedení v jeho vlastní transakce, způsobuje jednotlivých dávek hromadné kopírování provést v oddělené transakci.  
  
> [!NOTE]
>  Vzhledem k tomu, že různé dávky jsou spouštěny v různých transakcí, pokud dojde k chybě během operace hromadného kopírování, bude vrácena zpět všechny řádky v aktuální dávku, ale řádky z předchozí dávky zůstanou v databázi.  
  
 Následující aplikace konzoly je podobně jako v předchozím příkladu s jednou výjimkou: V tomto příkladu operace hromadného kopírování spravuje vlastní transakce. Všechny dávky zkopírovat až do chvíle, chyby se potvrdí; dávka obsahuje duplicitní klíč, je vrácena zpět a operace hromadného kopírování je byl zastaven před zpracováním jiných dávek.  
  
> [!IMPORTANT]
>  Tato ukázka se nespustí, pokud jste vytvořili pracovní tabulky, jak je popsáno v [hromadné kopírování příklad instalace](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Tento kód je určen k předvedení syntaxe pro používání **SqlBulkCopy** pouze. Pokud zdrojové a cílové tabulky jsou umístěny ve stejné instanci systému SQL Server, je jednodušší a rychlejší použít [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] `INSERT … SELECT` příkaz Kopírovat data.  
  
 [!code-csharp[DataWorks SqlBulkCopy.InternalTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.InternalTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.InternalTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.InternalTransaction/VB/source.vb#1)]  
  
## <a name="using-existing-transactions"></a>Použití existující transakcí  
 Můžete zadat existující <xref:System.Data.SqlClient.SqlTransaction> objekt jako parametr v <xref:System.Data.SqlClient.SqlBulkCopy> konstruktor. V takovém případě se provádí operace hromadného kopírování v stávající transakce a nebudou provedeny žádné změny stavu transakce (tedy ho je potvrzené ani přerušena). To umožňuje aplikace, aby zahrnovala operace hromadného kopírování v transakci s dalšími operacemi databáze. Ale pokud nezadáte <xref:System.Data.SqlClient.SqlTransaction> objektu a předejte jí odkazovat na hodnotu null a připojení má aktivní transakce, je vyvolána výjimka.  
  
 Pokud je nutné vrátit zpět, celý hromadné operace kopírování, protože by došlo k chybě, nebo pokud hromadné kopírování by měly spouštět jako součást větší proces, který je možné vrátit zpět, můžete zadat <xref:System.Data.SqlClient.SqlTransaction> do objektu <xref:System.Data.SqlClient.SqlBulkCopy> konstruktor.  
  
 Následující aplikace konzoly je podobná první (beztransakční) příkladu s jednou výjimkou: v tomto příkladu je operace hromadného kopírování součástí větší, externí transakce. Když dojde k chybě porušení primárního klíče, celá transakce bude vrácena zpět a žádné řádky jsou přidány do cílové tabulky.  
  
> [!IMPORTANT]
>  Tato ukázka se nespustí, pokud jste vytvořili pracovní tabulky, jak je popsáno v [hromadné kopírování příklad instalace](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Tento kód je určen k předvedení syntaxe pro používání **SqlBulkCopy** pouze. Pokud zdrojové a cílové tabulky jsou umístěny ve stejné instanci systému SQL Server, je jednodušší a rychlejší použít [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] `INSERT … SELECT` příkaz Kopírovat data.  
  
 [!code-csharp[DataWorks SqlBulkCopy.SqlTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.SqlTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.SqlTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.SqlTransaction/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Operace hromadného kopírování na SQL Serveru](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
