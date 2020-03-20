---
title: Povolení více aktivních sad výsledků
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
ms.openlocfilehash: 72125be835298218e5445fe1915d6a17f5008bb2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148722"
---
# <a name="enabling-multiple-active-result-sets"></a>Povolení více aktivních sad výsledků
Více sad aktivních výsledků (MARS) je funkce, která pracuje s SQL Server povolit provádění více dávek na jedno připojení. Pokud je mars povolen pro použití se serverem SQL Server, každý použitý objekt příkazu přidá relaci připojení.  
  
> [!NOTE]
> Jedna relace MARS otevře jedno logické připojení pro MARS pro použití a pak jedno logické připojení pro každý aktivní příkaz.  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a>Povolení a zakázání marsu v připojovacím řetězci  
  
> [!NOTE]
> Následující připojovací řetězce používají ukázkovou databázi **AdventureWorks,** která je součástí serveru SQL Server. Poskytnuté připojovací řetězce předpokládají, že databáze je nainstalována na serveru s názvem MSSQL1. Podle potřeby upravte připojovací řetězec pro vaše prostředí.  
  
 Funkce MARS je ve výchozím nastavení zakázána. To může být povoleno přidáním "MultipleActiveResultSets=True" pár klíčových slov do připojovacího řetězce. "True" je jediná platná hodnota pro povolení MARS. Následující příklad ukazuje, jak se připojit k instanci SQL Server a jak určit, že MARS by měla být povolena.  
  
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
  
 Mars můžete zakázat přidáním dvojice klíčových slov MultipleActiveResultSets=False do připojovacího řetězce. "False" je jediná platná hodnota pro zakázání MARS. Následující připojovací řetězec ukazuje, jak zakázat MARS.  
  
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
  
## <a name="special-considerations-when-using-mars"></a>Zvláštní aspekty při použití MARS  
 Obecně platí, že existující aplikace by neměly vyžadovat úpravy, aby bylo nutné používat připojení s podporou MARS. Pokud však chcete používat funkce MARS ve vašich aplikacích, měli byste pochopit následující zvláštní aspekty.  
  
### <a name="statement-interleaving"></a>Prokládání výkazu  
 Operace MARS se provádějí synchronně na serveru. Prokládání příkazů SELECT a BULK INSERT je povoleno. Příkazy jazyka pro manipulaci s daty (DML) a jazyka definice dat (DDL) se však provádějí atomicky. Všechny příkazy, které se pokoušejí provést při provádění atomické dávky, jsou blokovány. Paralelní spuštění na serveru není funkce MARS.  
  
 Pokud jsou dvě dávky odeslány v rámci připojení MARS, jeden z nich obsahuje příkaz SELECT, druhý obsahující příkaz DML, DML může zahájit provádění v rámci provádění příkazu SELECT. Příkaz DML však musí být spuštěn do dokončení, než může příkaz SELECT dosáhnout pokroku. Pokud jsou oba příkazy spuštěny v rámci stejné transakce, všechny změny provedené příkazem DML po spuštění příkazu SELECT nejsou viditelné pro operaci čtení.  
  
 Příkaz WAITFOR uvnitř příkazu SELECT neposkytuje transakce během čekání, to znamená, dokud není vytvořen první řádek. To znamená, že žádné jiné dávky lze spustit v rámci stejného připojení při čekání příkazwaitfor.  
  
### <a name="mars-session-cache"></a>Mezipaměť relace MARS  
 Při otevření připojení s povolenou funkcí MARS je vytvořena logická relace, která přidává další režii. Chcete-li minimalizovat režii a zvýšit výkon, **SqlClient** ukládá relace MARS v rámci připojení. Mezipaměť obsahuje maximálně 10 relací MARS. Tato hodnota není uživatelsky nastavitelná. Pokud je dosaženo limitu relace, je vytvořena nová relace – není generována chyba. Mezipaměť a relace obsažené v něm jsou na připojení; nejsou sdíleny mezi připojeními. Při uvolnění relace je vrácena do fondu, pokud bylo dosaženo horního limitu fondu. Pokud je fond mezipamětí plný, relace je uzavřena. Mars relace nevyprší. Jsou vyčištěny pouze při uvolnění objektu připojení. Mezipaměť relace MARS není předinstalována. Je načten, protože aplikace vyžaduje více relací.  
  
### <a name="thread-safety"></a>Bezpečnost vlákna  
 Operace MARS nejsou bezpečné pro přístup z více vláken.  
  
### <a name="connection-pooling"></a>Sdružování připojení  
 Připojení s podporou MARS jsou sdružená jako jakékoli jiné připojení. Pokud aplikace otevře dvě připojení, jedno s povolenou funkcí MARS a jedno se zakázaným marsem, jsou dvě připojení v samostatných fondech. Další informace naleznete v tématu [SQL Server Connection Pooling (ADO.NET)](../sql-server-connection-pooling.md).  
  
### <a name="sql-server-batch-execution-environment"></a>Prostředí pro spuštění dávky serveru SQL Server  
 Při otevření připojení je definováno výchozí prostředí. Toto prostředí je pak zkopírováno do logické relace MARS.  
  
 Prostředí spuštění dávky zahrnuje následující součásti:  
  
- Nastavit možnosti (například ANSI_NULLS, DATE_FORMAT, JAZYK, VELIKOST TEXTU)  
  
- Kontext zabezpečení (role uživatele/aplikace)  
  
- Kontext databáze (aktuální databáze)  
  
- Proměnné stavu spuštění (například@ERROR@@ROWCOUNT,@FETCH_STATUS @IDENTITY@ , @ @ )  
  
- Dočasné tabulky nejvyšší úrovně  
  
 S MARS výchozí spuštění prostředí je spojena s připojením. Každá nová dávka, která se spustí v rámci daného připojení, obdrží kopii výchozího prostředí. Vždy, když je kód spuštěn v rámci dané dávky, všechny změny provedené v prostředí jsou vymezeny na konkrétní dávku. Po dokončení spuštění jsou nastavení spuštění zkopírovány do výchozího prostředí. V případě jedné dávky vydávání několik příkazů, které mají být provedeny postupně v rámci stejné transakce, sémantiku jsou stejné jako ty, které jsou vystaveny připojení zahrnující starší klienty nebo servery.  
  
### <a name="parallel-execution"></a>Paralelní provádění  
 MARS není určen k odebrání všech požadavků pro více připojení v aplikaci. Pokud aplikace potřebuje skutečné paralelní provádění příkazů proti serveru, by měla být použita více připojení.  
  
 Představte si například následující scénář. Jsou vytvořeny dva objekty příkazů, jeden pro zpracování sady výsledků a druhý pro aktualizaci dat; sdílejí společné spojení přes MARS. V tomto scénáři `Transaction`.`Commit` se nezdaří při aktualizaci, dokud všechny výsledky byly přečteny na první příkaz objektu, dávat následující výjimku:  
  
 Zpráva: Kontext transakce je používán jinou relací.  
  
 Zdroj: Zprostředkovatel dat .NET SqlClient  
  
 Bylo očekáváno: (null)  
  
 Přijato: System.Data.SqlClient.SqlException  
  
 Existují tři možnosti pro zpracování tohoto scénáře:  
  
1. Spusťte transakci po vytvoření čtečky tak, aby nebyla součástí transakce. Každá aktualizace se pak stane vlastní transakcí.  
  
2. Po zavření čtečky odevzkaďte veškerou práci. To má potenciál pro podstatnou dávku aktualizací.  
  
3. Nepoužívejte MARS; místo toho použít samostatné připojení pro každý objekt příkazu, jako byste měli před MARS.  
  
### <a name="detecting-mars-support"></a>Detekce podpory MARS  
 Aplikace může zkontrolovat podporu MARS `SqlConnection.ServerVersion` čtením hodnoty. Hlavní číslo by mělo být 9 pro SQL Server 2005 a 10 pro SQL Server 2008.  
  
## <a name="see-also"></a>Viz také

- [Více aktivních sad výsledků (MARS)](multiple-active-result-sets-mars.md)
- [Přehled ADO.NET](../ado-net-overview.md)
