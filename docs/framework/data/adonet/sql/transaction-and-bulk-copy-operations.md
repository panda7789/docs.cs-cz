---
title: Operace transakcí a hromadného kopírování
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f6f0cbc9-f7bf-4d6e-875f-ad1ba0b4aa62
ms.openlocfilehash: 73c375f9acfd193680982994ed0852454cefebe5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791440"
---
# <a name="transaction-and-bulk-copy-operations"></a>Operace transakcí a hromadného kopírování
Operace hromadného kopírování lze provádět jako izolované operace nebo jako součást transakce více kroků. Tato druhá možnost umožňuje provádět více než jednu operaci hromadného kopírování v rámci stejné transakce a provádět další databázové operace (například vložení, aktualizace a odstranění) a zároveň může potvrdit nebo vrátit zpět celou transakci.  
  
 Ve výchozím nastavení se operace hromadného kopírování provádí jako izolovaná operace. Operace hromadného kopírování probíhá netransakčním způsobem bez příležitostí pro vrácení zpět. Pokud potřebujete vrátit zpátky veškerou nebo část hromadného kopírování, když dojde k chybě, můžete použít <xref:System.Data.SqlClient.SqlBulkCopy>transakci spravovanou, provést operaci hromadného kopírování v rámci existující transakce nebo ji zařadit do **System. Transactions**<xref:System.Transactions.Transaction>.  
  
## <a name="performing-a-non-transacted-bulk-copy-operation"></a>Provádění operace hromadného kopírování bez transakcí  
 Následující aplikace konzoly ukazuje, co se stane, když operace hromadného kopírování bez transakcí narazí na chybu zablokuje prostřednictvím operace.  
  
 V příkladu zdrojová tabulka a cílová tabulka obsahují `Identity` sloupec s názvem **ProductID**. Kód nejprve připraví cílovou tabulku odstraněním všech řádků a vložením jednoho řádku, jehož **ProductID** je známo, že existuje ve zdrojové tabulce. Ve výchozím nastavení je nová hodnota pro `Identity` sloupec vygenerována v cílové tabulce pro každý přidaný řádek. V tomto příkladu je možnost nastavena při otevření připojení, která vynutí, aby proces hromadného načtení místo toho používal `Identity` hodnoty ze zdrojové tabulky.  
  
 Operace hromadného kopírování je provedena s <xref:System.Data.SqlClient.SqlBulkCopy.BatchSize%2A> vlastností nastavenou na hodnotu 10. Pokud operace narazí na neplatný řádek, je vyvolána výjimka. V tomto prvním příkladu je operace hromadného kopírování netransakční. Všechny dávky zkopírované až do bodu chyby jsou potvrzeny. dávka obsahující duplicitní klíč se vrátí zpět a operace hromadného kopírování se před zpracováním jiných dávek zastaví.  
  
> [!NOTE]
> Tato ukázka nebude spuštěna, pokud jste nevytvořili pracovní tabulky, jak je popsáno v tématu [hromadné kopírování – příklad nastavení](bulk-copy-example-setup.md). Tento kód je k dispozici k předvedení syntaxe pouze pro použití **SqlBulkCopy** . Pokud se zdrojové a cílové tabulky nacházejí ve stejné instanci SQL Server, je snazší a rychlejší použít příkaz Transact-SQL`INSERT … SELECT` ke zkopírování dat.  
  
 [!code-csharp[DataWorks SqlBulkCopy.DefaultTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.DefaultTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.DefaultTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.DefaultTransaction/VB/source.vb#1)]  
  
## <a name="performing-a-dedicated-bulk-copy-operation-in-a-transaction"></a>Provádění vyhrazené operace hromadného kopírování v transakci  
 Ve výchozím nastavení je operace hromadného kopírování svou vlastní transakcí. Pokud chcete provést vyhrazenou operaci hromadného kopírování, vytvořte novou instanci <xref:System.Data.SqlClient.SqlBulkCopy> s připojovacím řetězcem nebo použijte existující <xref:System.Data.SqlClient.SqlConnection> objekt bez aktivní transakce. V každém scénáři operace hromadného kopírování vytvoří a potom potvrdí nebo vrátí zpět transakci.  
  
 Můžete explicitně zadat <xref:System.Data.SqlClient.SqlBulkCopyOptions.UseInternalTransaction> možnost <xref:System.Data.SqlClient.SqlBulkCopy> v konstruktoru třídy, aby explicitně způsobila spuštění hromadného kopírování ve vlastní transakci, což způsobí, že každá dávka operace hromadného kopírování bude provedena v rámci samostatné transakce.  
  
> [!NOTE]
> Vzhledem k tomu, že různé dávky jsou spouštěny v různých transakcích, pokud během operace hromadného kopírování dojde k chybě, všechny řádky v aktuální dávce budou vráceny zpět, ale řádky z předchozích dávek budou v databázi zůstat.  
  
 Následující Konzolová aplikace je podobná předchozímu příkladu s jednou výjimkou: V tomto příkladu operace hromadného kopírování spravuje své vlastní transakce. Všechny dávky zkopírované až do bodu chyby jsou potvrzeny. dávka obsahující duplicitní klíč se vrátí zpět a operace hromadného kopírování se před zpracováním jiných dávek zastaví.  
  
> [!IMPORTANT]
> Tato ukázka nebude spuštěna, pokud jste nevytvořili pracovní tabulky, jak je popsáno v tématu [hromadné kopírování – příklad nastavení](bulk-copy-example-setup.md). Tento kód je k dispozici k předvedení syntaxe pouze pro použití **SqlBulkCopy** . Pokud se zdrojové a cílové tabulky nacházejí ve stejné instanci SQL Server, je snazší a rychlejší použít příkaz Transact-SQL`INSERT … SELECT` ke zkopírování dat.  
  
 [!code-csharp[DataWorks SqlBulkCopy.InternalTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.InternalTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.InternalTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.InternalTransaction/VB/source.vb#1)]  
  
## <a name="using-existing-transactions"></a>Používání stávajících transakcí  
 Můžete zadat existující <xref:System.Data.SqlClient.SqlTransaction> objekt jako parametr <xref:System.Data.SqlClient.SqlBulkCopy> v konstruktoru. V této situaci je operace hromadného kopírování prováděna v existující transakci a není provedena žádná změna stavu transakce (tj. není potvrzena ani přerušena). To umožňuje aplikaci zahrnout operaci hromadného kopírování do transakce s dalšími operacemi databáze. Pokud však neurčíte <xref:System.Data.SqlClient.SqlTransaction> objekt a předáte nulový odkaz a připojení má aktivní transakci, je vyvolána výjimka.  
  
 Pokud potřebujete vrátit zpět celou operaci hromadného kopírování, protože dojde k chybě, nebo pokud by hromadné kopírování mělo být provedeno jako součást většího procesu, který lze vrátit zpět, můžete <xref:System.Data.SqlClient.SqlTransaction> objektu <xref:System.Data.SqlClient.SqlBulkCopy> konstruktoru poskytnout objekt.  
  
 Následující Konzolová aplikace je podobná prvnímu příkladu (bez transakčního příkazu) s jednou výjimkou: v tomto příkladu je operace hromadného kopírování zahrnuta ve větší, externí transakci. Pokud dojde k chybě narušení primárního klíče, celá transakce se vrátí zpět a do cílové tabulky se nepřidá žádné řádky.  
  
> [!IMPORTANT]
> Tato ukázka nebude spuštěna, pokud jste nevytvořili pracovní tabulky, jak je popsáno v tématu [hromadné kopírování – příklad nastavení](bulk-copy-example-setup.md). Tento kód je k dispozici k předvedení syntaxe pouze pro použití **SqlBulkCopy** . Pokud se zdrojové a cílové tabulky nacházejí ve stejné instanci SQL Server, je snazší a rychlejší použít příkaz Transact-SQL`INSERT … SELECT` ke zkopírování dat.  
  
 [!code-csharp[DataWorks SqlBulkCopy.SqlTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.SqlTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.SqlTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.SqlTransaction/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Operace hromadného kopírování na SQL Serveru](bulk-copy-operations-in-sql-server.md)
- [Přehled ADO.NET](../ado-net-overview.md)
