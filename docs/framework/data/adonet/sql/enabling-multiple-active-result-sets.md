---
title: Povolení více aktivních sad výsledků
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
ms.openlocfilehash: 9930b0081ef67ed006e399e3e5b44e88a47933c1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147547"
---
# <a name="enabling-multiple-active-result-sets"></a>Povolení více aktivních sad výsledků
Více sad aktivní výsledků (MARS) je funkce, která funguje se serverem SQL Server, aby bylo možné spouštění více dávek na jedno připojení. Pokud MARS je povolené pro použití se serverem SQL Server, přidá každý objekt příkazu použít relaci připojení.  
  
> [!NOTE]
>  Jedné relace MARS otevře pro MARS použít několik logických připojení a pak jeden logický připojení pro každý aktivní příkaz.  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a>Povolení a zakázání MARS v připojovacím řetězci  
  
> [!NOTE]
>  Následující připojovací řetězce použitím této ukázky **AdventureWorks** databáze je součástí systému SQL Server. Připojovací řetězce k dispozici se předpokládá, že je databáze nainstalována na serveru s názvem MSSQL1. Úprava připojovacího řetězce podle potřeby pro vaše prostředí.  
  
 Ve výchozím nastavení je zakázána funkce MARS. To se dá nastavit tak, že přidáte "MultipleActiveResultSets = True" spárovat – klíčové slovo připojovacího řetězce. Jediná platná hodnota pro povolování relace MARS je "True". Následující příklad ukazuje, jak se připojit k instanci systému SQL Server a jak určit, že by měla být povolená MARS.  
  
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
  
 MARS můžete zakázat tak, že přidáte "MultipleActiveResultSets = False" spárovat – klíčové slovo připojovacího řetězce. "False" je jedinou platnou hodnotou pro zakázání MARS. Následující připojovací řetězec ukazuje, jak zakázat MARS.  
  
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
 Obecně platí stávající aplikace nemusí změny použít pro připojení MARS. Ale pokud chcete používat funkce MARS ve svých aplikacích, měli byste porozumět následující zvláštní požadavky.  
  
### <a name="statement-interleaving"></a>Prokládání – příkaz  
 Operace MARS synchronnímu provádění na serveru. Příkaz prokládání příkazů SELECT a BULK INSERT je povolen. Však jazyk pro manipulaci dat (DML) a data (příkazy DDL definition language) spusťte atomicky. Všechny příkazy pokusu o provedení při provádění atomických batch jsou zablokované. Paralelní provádění na serveru není funkce MARS.  
  
 Pokud jsou dvě dávky odeslané v rámci připojení MARS, jeden z nich obsahující příkaz SELECT, druhý příkaz DML, který obsahuje DML můžete zahájit provádění v rámci spuštění příkazu SELECT. Nicméně příkaz DML musí být spuštěny pro dokončení před příkaz SELECT lze dosáhnout pokroku. Pokud oba příkazy běží v rámci stejné transakce, všechny změny provedené příkazem DML po zahájení provádění příkazu SELECT nejsou viditelné pro operace čtení.  
  
 Příkaz WAITFOR uvnitř příkazu SELECT transakci nevydává, zatímco čeká, to znamená, dokud je vytvořen na prvním řádku. Z toho vyplývá, že žádné další dávky můžete spustit v rámci stejného připojení při čekání příkazu WAITFOR.  
  
### <a name="mars-session-cache"></a>Mezipaměť relace MARS  
 Při otevření připojení s MARS povolena, se vytvoří logickou relaci, přidává režijní náklady na další. Aby se minimalizovala režijní náklady a zvýšit výkon, **SqlClient** ukládá do mezipaměti v rámci určitého připojení relace MARS. Mezipaměť obsahuje maximálně 10 relace MARS. Tato hodnota není měnitelné uživatele. Pokud dosáhnete limitu relace, je vytvořena nová relace – není generována chyba. Mezipaměť a relace jsou v něm obsažené se za připojení. že se mezi připojení nesdílí. Když se uvolní relace, je vrácen do fondu pokud bylo dosaženo horního limitu fondu. Pokud fond mezipaměti je plná, není zavřena relace. Relace MARS, nevyprší platnost. Jsou pouze vyčistily při uvolnění objekt připojení. Mezipaměť relace MARS se předem načtena. Načte se aplikace vyžaduje další relace.  
  
### <a name="thread-safety"></a>Bezpečnost vlákna  
 Operace MARS nejsou bezpečné pro vlákna.  
  
### <a name="connection-pooling"></a>Sdružování připojení  
 Připojení MARS povolené ve fondu stejně jako jakékoli jiné připojení. Pokud se aplikace otevře dvě připojení, jednu s MARS povolená a jednu s MARS zakázán, jsou dvě připojení v samostatné fondy. Další informace najdete v tématu [SQL sdružování připojení serveru (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
### <a name="sql-server-batch-execution-environment"></a>Prostředí pro spuštění dávky SQL serveru  
 Při otevření připojení, je definován výchozí prostředí. Toto prostředí je poté zkopírován do logické relace MARS.  
  
 Prostředí pro spouštění služby batch zahrnuje následující součásti:  
  
-   Nastavení možností (například ANSI_NULLS DATE_FORMAT, jazyka, velikost textu)  
  
-   Kontext zabezpečení (role uživatelů a aplikací)  
  
-   Kontext databáze (aktuální databáze)  
  
-   Proměnné stavu spuštění (například @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)  
  
-   Nejvyšší úrovně dočasné tabulky  
  
 S MARS je výchozí prostředí spuštění přidružené k připojení. Každý nový list, který se spustí provádění v rámci dané připojení obdrží kopii výchozího prostředí. Pokaždé, když je kód spuštěn v dané dávce, všechny změny provedené v prostředí oborem pro určité služby batch. Jakmile se dokončí provádění, nastavení spuštění se zkopírují do výchozího prostředí. V případě vydávání několika příkazů postupně provádět v rámci stejné transakce v jedné dávce sémantika je stejné jako vystavené připojení týkajících se starších klientů nebo serverů.  
  
### <a name="parallel-execution"></a>Paralelní provádění  
 Chcete-li odebrat všechny požadavky pro víc připojení v aplikaci není určená MARS. Pokud aplikace potřebuje true pro paralelní zpracování příkazů pro server, by měla sloužit více připojení.  
  
 Představte si třeba následující scénář. Příkaz jsou vytvořeny dva objekty, jeden pro zpracování je sada výsledků dotazu a druhý pro aktualizaci dat; sdílejí společné připojení přes MARS. V tomto scénáři `Transaction`.`Commit` Při aktualizaci selhávat, dokud se všechny výsledky byly načteny na první příkaz objekt, což má za následek následující výjimku:  
  
 zpráva: Kontext transakce používá jiná relace.  
  
 Zdroj: Zprostředkovatel dat SqlClient .NET  
  
 Byl očekáván: (null)  
  
 Přijal: System.Data.SqlClient.SqlException  
  
 Existují tři možnosti pro takové situaci:  
  
1.  Spuštění transakce po vytvoření čtečky tak, že není součástí transakce. Každá aktualizace se pak stane vlastní transakce.  
  
2.  Potvrďte veškerou práci po zavření čtečky. Toto řešení má potenciál pro významné hromadné aktualizace.  
  
3.  Nepoužívejte MARS; Místo toho použijte samostatného připojení pro každý objekt příkazu, jako byste před MARS.  
  
### <a name="detecting-mars-support"></a>Zjišťování MARS podpory  
 Aplikace můžete zkontrolovat MARS podpory najdete `SqlConnection.ServerVersion` hodnotu. Hlavní číslo musí být pro SQL Server 2005 9 a 10 pro SQL Server 2008.  
  
## <a name="see-also"></a>Viz také:

- [Více aktivních sad výsledků (MARS)](../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
