---
title: Povolení více aktivních sad výsledků
description: Naučte se, jak povolit nebo zakázat MARS v připojovacím řetězci, který funguje s SQL Server, abyste mohli spouštět víc dávek na jednom připojení v ADO.NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
ms.openlocfilehash: 43bdfebce291c3c1d6c90104c5fef440b295934b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286478"
---
# <a name="enabling-multiple-active-result-sets"></a>Povolení více aktivních sad výsledků
Několik aktivních sad výsledků dotazu (MARS) je funkce, která funguje s SQL Server, aby bylo možné spouštět více dávek v jednom připojení. Když je u služby MARS povolený použití s SQL Server, přidá každý objekt příkazu k připojení relaci.  
  
> [!NOTE]
> Jedna relace MARS otevře jedno logické připojení pro službu MARS, které bude používat, a potom jedno logické připojení pro každý aktivní příkaz.  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a>Povolení a zakázání MARS v připojovacím řetězci  
  
> [!NOTE]
> Následující připojovací řetězce používají ukázkovou databázi **AdventureWorks** , která je součástí SQL Server. Zadané připojovací řetězce předpokládají, že je databáze nainstalována na serveru s názvem MSSQL1. Upravte připojovací řetězec podle potřeby pro vaše prostředí.  
  
 Funkce MARS je ve výchozím nastavení zakázána. Můžete ji povolit přidáním dvojice klíčového slova "MultipleActiveResultSets = True" do připojovacího řetězce. Jedinou platnou hodnotou pro povolení služby MARS je "true". Následující příklad ukazuje, jak se připojit k instanci SQL Server a jak určit, že má být povolen MARS.  
  
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
  
 MARS můžete zakázat přidáním dvojice klíčového slova "MultipleActiveResultSets = false" do připojovacího řetězce. Jedinou platnou hodnotou pro zakázání služby MARS je "false". Následující připojovací řetězec ukazuje, jak zakázat MARS.  
  
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
  
## <a name="special-considerations-when-using-mars"></a>Zvláštní důležité důvody při použití MARS  
 Obecně platí, že stávající aplikace by neměly potřebovat úpravu pro použití připojení s povoleným MARS. Pokud ale chcete ve svých aplikacích používat funkce MARS, měli byste se seznámit s následujícími zvláštními požadavky.  
  
### <a name="statement-interleaving"></a>Vynechávání příkazu  
 Operace MARS se na serveru spouštějí synchronně. Příkaz, který prochází příkazy SELECT a BULK INSERT, je povolen. Nicméně příkazy jazyka DML (data Language) a DDL (Data Definition Language) se provádějí atomicky. Jakékoli příkazy, které se pokoušejí provést během provádění atomické dávky, jsou blokované. Paralelní provádění na serveru není funkce MARS.  
  
 Pokud jsou dvě dávky odesílány v rámci připojení MARS, jeden z nich obsahující příkaz SELECT, druhý obsahující příkaz DML, může DML zahájit provádění během provádění příkazu SELECT. Nicméně příkaz DML musí být spuštěn, aby bylo dokončeno, než může provést příkaz SELECT. Pokud jsou oba příkazy spuštěny v rámci stejné transakce, všechny změny provedené příkazem DML po spuštění příkazu SELECT nejsou viditelné pro operaci čtení.  
  
 Příkaz WAITFOR uvnitř příkazu SELECT nevrací transakci, pokud čeká na vyčerpání, to znamená až do vytvoření prvního řádku. To znamená, že žádné další dávky nemohou být spuštěny v rámci stejného připojení, zatímco příkaz WAITFOR čeká.  
  
### <a name="mars-session-cache"></a>Mezipaměť relace MARS  
 Když je připojení otevřené s povoleným MARS, vytvoří se logická relace, která přidá další režii. Pro minimalizaci režie a zvýšení výkonu **SqlClient** v rámci připojení ukládá do mezipaměti relaci Mars. Mezipaměť obsahuje maximálně 10 relací MARS. Tato hodnota není přizpůsobitelná uživatelem. Pokud je dosaženo limitu relace, vytvoří se nová relace – chyba se nevygeneruje. Mezipaměť a relace, které jsou v ní obsažené, jsou vázané na připojení; nesdílí se mezi připojeními. Když se relace uvolní, vrátí se do fondu, pokud se nedosáhne horní meze fondu. Pokud je fond mezipaměti plný, relace je zavřena. Relace MARS do vypršení platnosti nekončí. Vyčistí se jenom v případě, že je objekt připojení vyřazený. Mezipaměť relace MARS není předem načtena. Je načtená, protože aplikace vyžaduje více relací.  
  
### <a name="thread-safety"></a>Bezpečný přístup z více vláken  
 Operace MARS nejsou bezpečné pro přístup z více vláken.  
  
### <a name="connection-pooling"></a>Sdružování připojení  
 Připojení s povoleným MARSm jsou ve fondu jako jakékoli jiné připojení. Pokud aplikace otevře dvě připojení, jedna s povoleným MARS a jedna se zakázaným MARSm, jsou tato dvě připojení v samostatných fondech. Další informace najdete v tématu věnovaném [sdružování připojení SQL Server (ADO.NET)](../sql-server-connection-pooling.md).  
  
### <a name="sql-server-batch-execution-environment"></a>SQL Server prostředí pro spuštění dávky  
 Při otevření připojení je definováno výchozí prostředí. Toto prostředí se pak zkopíruje do logické relace MARS.  
  
 Prostředí provádění dávky zahrnuje následující součásti:  
  
- Nastavit možnosti (například ANSI_NULLS, DATE_FORMAT, jazyk, TEXTSIZE)  
  
- Kontext zabezpečení (role uživatel/aplikace)  
  
- Kontext databáze (aktuální databáze)  
  
- Proměnné stavu provádění (například @ @ERROR , @ @ROWCOUNT , @ @FETCH_STATUS @ @IDENTITY )  
  
- Dočasné tabulky nejvyšší úrovně  
  
 Pomocí MARS je k připojení přidruženo výchozí prostředí pro spuštění. Každá nová dávka, která se spustí v rámci daného připojení, obdrží kopii výchozího prostředí. Vždy, když je kód proveden v rámci dané dávky, všechny změny provedené v prostředí jsou vymezeny na konkrétní dávku. Po dokončení spuštění se nastavení spuštění zkopíruje do výchozího prostředí. V případě jedné dávky vydávající několik příkazů, které se mají provést postupně v rámci stejné transakce, jsou sémantika stejná jako ta, která je vystavená připojeními, která zahrnují starší klienty nebo servery.  
  
### <a name="parallel-execution"></a>Paralelní provádění  
 Služba MARS není navržena tak, aby odebrala všechny požadavky na více připojení v aplikaci. Pokud aplikace potřebuje pravdivé paralelní spouštění příkazů na serveru, je třeba použít více připojení.  
  
 Představte si například následující scénář. Vytvoří se dva objekty příkazu, jeden pro zpracování sady výsledků dotazu a další pro aktualizaci dat; sdílejí společné připojení prostřednictvím MARS. V tomto scénáři `Transaction` .`Commit` dojde k neúspěchu aktualizace, dokud všechny výsledky nebyly přečteny na prvním objektu příkazu a vrátila následující výjimku:  
  
 Zpráva: kontext transakce je používán jinou relací.  
  
 Zdroj: Zprostředkovatel dat .NET SqlClient  
  
 Očekáváno: (null)  
  
 Přijato: System. data. SqlClient. SqlException  
  
 Existují tři možnosti pro zpracování tohoto scénáře:  
  
1. Spusťte transakci po vytvoření čtecího zařízení, aby nebylo součástí transakce. Každá aktualizace pak bude svou vlastní transakcí.  
  
2. Po zavření čtecího zařízení potvrďte veškerou práci. To má potenciál pro značnou dávku aktualizací.  
  
3. Nepoužívejte MARS; místo toho použijte samostatné připojení pro každý objekt příkazu, který byste měli mít před MARS.  
  
### <a name="detecting-mars-support"></a>Zjišťování podpory MARS  
 Aplikace může vyhledat podporu služby MARS načtením `SqlConnection.ServerVersion` hodnoty. Hlavní číslo by mělo být 9 pro SQL Server 2005 a 10 pro SQL Server 2008.  
  
## <a name="see-also"></a>Viz také

- [Více aktivních sad výsledků (MARS)](multiple-active-result-sets-mars.md)
- [Přehled ADO.NET](../ado-net-overview.md)
