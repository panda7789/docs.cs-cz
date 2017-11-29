---
title: "Povolení více aktivních sad"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1d39d1666f63d7d6f7a6154a124280486c3fccce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="enabling-multiple-active-result-sets"></a>Povolení více aktivních sad
Několik sad Active výsledek (MARS) je funkce, která spolupracuje se serverem SQL Server k provádění více jednoho připojení. Pokud MARS je povoleno pro použití se systémem SQL Server, přidá každý objekt příkazu používá relaci připojení.  
  
> [!NOTE]
>  Jedné relace MARS otevře jedno logické připojení pro MARS používat a pak jedno logické připojení u každého příkazu aktivní.  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a>Povolení a zakázání MARS v připojovacím řetězci  
  
> [!NOTE]
>  Následující připojovací řetězce použijte ukázku, která **AdventureWorks** databáze je součástí systému SQL Server. Připojovací řetězce zadaná předpokládá, že je databáze nainstalována na serveru s názvem MSSQL1. Upravte připojovací řetězec v případě potřeby pro vaše prostředí.  
  
 Funkci MARS se ve výchozím nastavení vypnutá. Může být povoleno přidáním "MultipleActiveResultSets = True" dvojici – klíčové slovo připojovacího řetězce. "True" je jedinou platnou hodnotou pro povolení MARS. Následující příklad ukazuje, jak se připojit k instanci systému SQL Server a určení, že by měla být povolená MARS.  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=True"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +   
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=True";  
```  
  
 Můžete zakázat MARS přidáním "MultipleActiveResultSets = False" dvojici – klíčové slovo připojovacího řetězce. "Nepravda" je jedinou platnou hodnotou pro zakázání MARS. Následující připojovací řetězec ukazuje, jak zakázat MARS.  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=False"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +   
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=False";  
```  
  
## <a name="special-considerations-when-using-mars"></a>Zvláštní aspekty při používání MARS  
 Obecně platí stávající aplikace by neměl nutné změny pomocí připojení s MARS. Ale pokud chcete používat funkce MARS ve svých aplikacích byste měli porozumět následující zvláštní aspekty.  
  
### <a name="statement-interleaving"></a>Prokládání – příkaz  
 Operace MARS synchronně spustit na serveru. Příkaz prokládání příkazů vyberte a BULK INSERT je povolen. Však jazyk pro manipulaci dat (DML) a příkazy data definition language (DDL) spusťte atomicky. Všechny příkazy pokusu provést v době, kdy je prováděna atomic batch jsou zablokované. Paralelní provádění na serveru není funkce MARS.  
  
 Pokud dvě dávky se odešlou v části připojení relace MARS, jeden z nich obsahující příkaz SELECT, druhá obsahuje příkaz DML, DML můžete zahájit provádění v rámci provádění příkazu SELECT. Příkaz DML však musíte spustit na dokončení před příkaz SELECT provádět průběh. Pokud oba příkazy běží ve stejné transakci, všechny změny provedené příkaz DML po spuštění provádění příkazu SELECT nejsou viditelné pro operace čtení.  
  
 Příkaz WAITFOR uvnitř příkazu SELECT nepřinese transakce, zatímco čeká, to znamená, dokud se vytvářejí na prvním řádku. To znamená, že žádné další dávky může spustit v rámci stejné připojení při příkaz WAITFOR čeká.  
  
### <a name="mars-session-cache"></a>Mezipaměť relace MARS  
 Po otevření připojení s MARS povoleno se vytvoří relaci logického, přidává další režii. Chcete-li minimalizovat režijní náklady a zvýšit výkon, **SqlClient** ukládá do mezipaměti v rámci připojení relace MARS. Mezipaměť obsahuje maximálně 10 relace MARS. Tato hodnota není uživatel upravit. Pokud bude dosažen limit relace, je vytvořit novou relaci – není generována chyba. Mezipaměť a relací, které v ní jsou připojení; že nejsou sdílená mezi připojení. Po vydání relaci, se vrátí do fondu pokud bylo dosaženo horní limit fondu. Pokud fond mezipaměti je plná, relace je zavřený. Platnost MARS relací. Že jsou pouze vyčistit při uvolnění objekt připojení. Mezipaměť relace MARS není předem načtena. Načte se jako aplikace vyžaduje více relací.  
  
### <a name="thread-safety"></a>Bezpečnost vlákna  
 Operace MARS nejsou bezpečné pro přístup z více vláken.  
  
### <a name="connection-pooling"></a>Sdružování připojení  
 MARS povoleno připojení jsou ve fondu, podobně jako jakékoli jiné připojení. Pokud aplikace otevře dvě připojení, jeden s MARS povolené a jeden s MARS zakázáno, jsou dvě připojení v samostatné fondy. Další informace najdete v tématu [SQL sdružování připojení serveru (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
### <a name="sql-server-batch-execution-environment"></a>Prostředí pro spuštění dávky SQL serveru  
 Po otevření připojení je definován výchozí prostředí. Toto prostředí poté zkopíruje do logické relace MARS.  
  
 Prostředí pro spuštění dávky zahrnuje následující součásti:  
  
-   Nastavení možností (například ANSI_NULLS, DATE_FORMAT, jazyka, velikost textu)  
  
-   Kontext zabezpečení (role uživatele nebo aplikace)  
  
-   Kontext databáze (aktuální databázi)  
  
-   Proměnné stavu spuštění (například @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)  
  
-   Nejvyšší úrovně dočasných tabulek  
  
 S MARS je přidružena k připojení k prostředí pro spouštění výchozí. Každých nové dávky, která spustí provádění v rámci dané připojení obdrží kopii výchozího prostředí. Při každém spuštění kódu v rámci dané batch, všechny změny provedené v prostředí jsou omezená na určité dávky. Po dokončení provádění, nastavení spuštění se zkopírují do výchozího prostředí. V případě jedné dávkové vydání několik příkazů postupně provést v rámci stejné transakci sémantika je stejná jako ta, vystavené připojení zahrnující starších klientů nebo serverů.  
  
### <a name="parallel-execution"></a>Paralelní provádění  
 MARS nebyla navržena pro odebrat všechny požadavky pro víc připojení v aplikaci. Pokud aplikace potřebuje true paralelní provádění příkazů na serveru, je třeba použít víc připojení.  
  
 Představte si třeba následující scénář. Dva objekty příkaz se vytvoření, jeden pro zpracování je sada výsledků dotazu a druhý pro aktualizace dat; sdílejí společné připojení prostřednictvím MARS. V tomto scénáři `Transaction`.`Commit` na aktualizaci selhávat, dokud se všechny výsledky byly načteny na první objekt příkazu je následující výjimky:  
  
 Zpráva: Kontext transakce používá jiná relace.  
  
 Zdroj: Zprostředkovatel dat SqlClient .net  
  
 Očekávané: (null)  
  
 Přijaté: System.Data.SqlClient.SqlException  
  
 Existují tři možnosti pro zpracování tento scénář:  
  
1.  Spuštění transakce po vytvoření čtečky tak, že není součástí transakce. Každá aktualizace se pak stane vlastní transakce.  
  
2.  Potvrďte všechny pracovní po zavření čtečky. To se může pro významné hromadné aktualizace.  
  
3.  Nepoužívejte MARS; Místo toho pomocí samostatného připojení pro každý objekt příkazu, jako byste před MARS.  
  
### <a name="detecting-mars-support"></a>Zjišťování MARS podpory  
 Aplikace můžete zkontrolovat pro MARS podporují přečíst `SqlConnection.ServerVersion` hodnotu. Hlavní číslo by mělo být 9 pro SQL Server 2005 a 10 pro SQL Server 2008.  
  
## <a name="see-also"></a>Viz také  
 [Více sad výsledků dotazu Active (MARS)](../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
