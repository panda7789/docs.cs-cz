---
title: Sdružování připojení serveru SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e51d44e-7c4e-4040-9332-f0190fe36f07
ms.openlocfilehash: 149511bd4e84baabf11eca014257127b587830df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148995"
---
# <a name="sql-server-connection-pooling-adonet"></a>Sdružování připojení SQL Serveru (ADO.NET)
Připojení k databázovému serveru se obvykle skládá z několika časově náročných kroků. Fyzický kanál, jako je soket nebo pojmenovaný kanál, musí být vytvořen, musí dojít k počátečnímu podání ruky se serverem, musí být analyzovány informace o připojovacím řetězci, připojení musí být ověřeno serverem, kontroly musí být spuštěny pro zařazení do aktuální transakce a tak dále.  
  
 V praxi většina aplikací používá pouze jednu nebo několik různých konfigurací pro připojení. To znamená, že během provádění aplikace bude mnoho identických připojení opakovaně otevřeno a zavírat. Chcete-li minimalizovat náklady na otevření připojení, ADO.NET používá optimalizační techniku nazvanou *sdružování připojení*.  
  
 Sdružování připojení snižuje počet, kolikrát je nutné otevřít nová připojení. *Pooler* udržuje vlastnictví fyzicképřipojení. Spravuje připojení udržováním při životě sadu aktivních připojení pro každou konfiguraci daného připojení. Kdykoli uživatel `Open` volá připojení, pooler hledá dostupné připojení ve fondu. Pokud je k dispozici sdružené připojení, vrátí jej volajícímu namísto otevření nového připojení. Když aplikace `Close` volá připojení, pooler vrátí do sdružené sady aktivních připojení namísto jeho zavření. Jakmile je připojení vráceno do fondu, je připraveno `Open` k opětovnému použití při dalším volání.  
  
 Sdružují se pouze připojení se stejnou konfigurací. ADO.NET udržuje několik fondů současně, jeden pro každou konfiguraci. Připojení jsou rozdělena do fondů podle připojovacího řetězce a identity systému Windows při použití integrovaného zabezpečení. Připojení jsou také sdružené na základě toho, zda jsou zapsány v transakci. Při <xref:System.Data.SqlClient.SqlConnection.ChangePassword%2A>použití <xref:System.Data.SqlClient.SqlCredential> instance ovlivňuje fond připojení. Různé instance <xref:System.Data.SqlClient.SqlCredential> budou používat různé fondy připojení, i když id uživatele a heslo jsou stejné.  
  
 Sdružování připojení může výrazně zvýšit výkon a škálovatelnost vaší aplikace. Ve výchozím nastavení je sdružování připojení povoleno v ADO.NET. Pokud explicitně zakázat, pooler optimalizuje připojení, jak jsou otevřeny a uzavřeny ve vaší aplikaci. Můžete také zadat několik modifikátorů připojovacího řetězce pro řízení chování sdružování připojení. Další informace naleznete v tématu "Řízení sdružování připojení s klíčovými slovy připojovacího řetězce" dále v tomto tématu.  
  
> [!NOTE]
> Pokud je povoleno sdružování připojení a dojde-li k chybě vypršení časového limitu nebo jiné chybě přihlášení, bude vyvolána výjimka a následné pokusy o připojení se nezdaří po dobu dalších pěti sekund, "blokovací období". Pokud se aplikace pokusí připojit v rámci období blokování, bude znovu vyvolána první výjimka. Následné chyby po ukončení blokovacího období budou mít za následek nové blokovací období, které je dvakrát delší než předchozí blokovací období, maximálně jednu minutu.  
  
## <a name="pool-creation-and-assignment"></a>Vytvoření a přiřazení fondu  
 Při prvním otevření připojení je vytvořen fond připojení na základě algoritmu přesného párování, který přidružuje fond k připojovacímu řetězci v připojení. Každý fond připojení je přidružen k odlišnému připojovacímu řetězci. Při otevření nového připojení, pokud připojovací řetězec není přesná shoda s existujícím fondem, je vytvořen nový fond. Připojení jsou sdružená podle procesu, podle domény aplikace, podle připojovacího řetězce a při použití integrovaného zabezpečení podle identity systému Windows. Připojovací řetězce musí být také přesnou shodu; klíčová slova dodaná v jiném pořadí pro stejné připojení budou sdružena samostatně.  
  
 V následujícím příkladu jazyka <xref:System.Data.SqlClient.SqlConnection> C# jsou vytvořeny tři nové objekty, ale ke správě jsou vyžadovány pouze dva fondy připojení. Všimněte si, že první a druhý připojovací řetězce se liší podle hodnoty přiřazené pro `Initial Catalog`.  
  
```csharp
using (SqlConnection connection = new SqlConnection(  
  "Integrated Security=SSPI;Initial Catalog=Northwind"))  
    {  
        connection.Open();
        // Pool A is created.  
    }  
  
using (SqlConnection connection = new SqlConnection(  
  "Integrated Security=SSPI;Initial Catalog=pubs"))  
    {  
        connection.Open();
        // Pool B is created because the connection strings differ.  
    }  
  
using (SqlConnection connection = new SqlConnection(  
  "Integrated Security=SSPI;Initial Catalog=Northwind"))  
    {  
        connection.Open();
        // The connection string matches pool A.  
    }  
```  
  
 Pokud `MinPoolSize` není zadán v připojovacím řetězci nebo je zadán jako nula, připojení ve fondu bude uzavřenpo určité době nečinnosti. Pokud je však zadaný `MinPoolSize` je větší než nula, fond připojení není zničen, `AppDomain` dokud je uvolněn a proces končí. Údržba neaktivních nebo prázdných fondů zahrnuje minimální režii systému.  
  
> [!NOTE]
> Fond je automaticky vymazána, když dojde k závažné chybě, jako je například převzetí služeb při selhání.  
  
## <a name="adding-connections"></a>Přidání připojení  
 Fond připojení je vytvořen pro každý jedinečný připojovací řetězec. Při vytvoření fondu jsou vytvořeny a přidány do fondu více objektů připojení, aby byl splněn požadavek na minimální velikost fondu. Připojení jsou přidány do fondu podle potřeby až do maximální velikostfondu zadaná (100 je výchozí). Připojení jsou uvolněny zpět do fondu, když jsou uzavřeny nebo vyřazeny.  
  
 Pokud <xref:System.Data.SqlClient.SqlConnection> je požadován objekt, je získán z fondu, pokud je k dispozici použitelné připojení. Aby bylo možné připojení použít, musí být nevyužité, musí mít odpovídající kontext transakce nebo být nepřidruženo k libovolnému kontextu transakce a mít platné propojení se serverem.  
  
 Sdružovací služba připojení splňuje požadavky na připojení přerozdělením připojení při jejich uvolnění zpět do fondu. Pokud bylo dosaženo maximální velikosti fondu a není k dispozici žádné použitelné připojení, je požadavek zařazen do fronty. Pooler se pak pokusí získat zpět všechna připojení, dokud není dosaženo časového limitu (výchozí hodnota je 15 sekund). Pokud pooler nemůže splnit požadavek před časový limit připojení, je vyvolána výjimka.  
  
> [!CAUTION]
> Důrazně doporučujeme, abyste vždy zavřít připojení po dokončení jeho použití tak, aby připojení bude vrácena do fondu. Můžete to provést pomocí `Close` `Dispose` nebo metody `Connection` objektu nebo otevřením `using` všechna připojení uvnitř příkazu v jazyce C# nebo `Using` příkaz v jazyce Visual Basic. Připojení, která nejsou explicitně uzavřena, nemusí být přidána nebo vrácena do fondu. Další informace naleznete [v tématu using Statement](../../../csharp/language-reference/keywords/using-statement.md) or How [to: Dispose of a System Resource](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md) for Visual Basic.  
  
> [!NOTE]
> Nevolejte `Close` nebo `Dispose` na `Connection`, `DataReader`, , nebo jakýkoli `Finalize` jiný spravovaný objekt v metodě vaší třídy. Ve finalizační metodě uvolněte pouze nespravované prostředky, které přímo vlastní vaše třída. Pokud vaše třída nevlastní žádné nespravované prostředky, `Finalize` nezahrnujte metodu do definice třídy. Další informace naleznete v [tématu Garbage Collection](../../../standard/garbage-collection/index.md).  
  
Další informace o událostech spojených s otevíráním a zavíráním připojení naleznete v [tématu Audit přihlášení třídy událostí](/sql/relational-databases/event-classes/audit-login-event-class) a [třídy odhlášení auditu](/sql/relational-databases/event-classes/audit-logout-event-class) v dokumentaci k serveru SQL Server.  
  
## <a name="removing-connections"></a>Odebrání připojení  
 Sdružovací služba připojení odebere připojení z fondu poté, co byl nečinný po dobu přibližně 4-8 minut, nebo pokud pooler zjistí, že připojení se serverem byla přerušena. Všimněte si, že přerušené připojení lze zjistit pouze po pokusu o komunikaci se serverem. Pokud je nalezeno připojení, které již není připojeno k serveru, je označeno jako neplatné. Neplatná připojení jsou odebrána z fondu připojení pouze v případě, že jsou uzavřeny nebo regenerované.  
  
 Pokud existuje připojení k serveru, který zmizel, toto připojení lze nakreslit z fondu i v případě, že sdružovací připojení nezjistilpřerušené připojení a označil jej jako neplatné. To je případ, protože režie kontroly, že připojení je stále platný by eliminovat výhody s pooler tím, že způsobí další odezvu na server dojít. V takovém případě první pokus o použití připojení zjistí, že připojení bylo přerušeno a je vyvolána výjimka.  
  
## <a name="clearing-the-pool"></a>Vymazání fondu  
 ADO.NET 2.0 zavedla dvě nové metody <xref:System.Data.SqlClient.SqlConnection.ClearAllPools%2A> <xref:System.Data.SqlClient.SqlConnection.ClearPool%2A>pro vyčištění bazénu: a . `ClearAllPools`vymaže fondy připojení `ClearPool` pro daného zprostředkovatele a vymaže fond připojení, který je přidružen k určitému připojení. Pokud jsou v době volání používána připojení, jsou odpovídajícím způsobem označena. Když jsou uzavřeny, jsou zahozeny namísto vrácení do fondu.  
  
## <a name="transaction-support"></a>Podpora transakcí  
 Připojení jsou čerpána z fondu a přiřazena na základě kontextu transakce. Pokud `Enlist=false` není zadán v připojovacím řetězci, fond připojení <xref:System.Transactions.Transaction.Current%2A> zajišťuje, že připojení je zapsán v kontextu. Pokud je připojení uzavřeno a vráceno do `System.Transactions` fondu s zapsanou transakcí, je odloženo tak, že `System.Transactions` další požadavek pro tento fond připojení se stejnou transakcí vrátí stejné připojení, pokud je k dispozici. Pokud je takový požadavek vydán a nejsou k dispozici žádná sdružená připojení, je připojení nakresleno z netransakční části fondu a zapsáno. Pokud v žádné oblasti fondu nejsou k dispozici žádná připojení, je vytvořeno a zapsáno nové připojení.  
  
 Když je připojení uzavřeno, je uvolněna zpět do fondu a do příslušného dělení na základě jeho kontextu transakce. Proto můžete zavřít připojení bez generování chyby, i když distribuovaná transakce stále čeká na vyřízení. To umožňuje potvrdit nebo přerušit distribuované transakce později.  
  
## <a name="controlling-connection-pooling-with-connection-string-keywords"></a>Řízení sdružování připojení pomocí klíčových slov připojovacího řetězce  
 Vlastnost `ConnectionString` objektu <xref:System.Data.SqlClient.SqlConnection> podporuje dvojice klíčů a hodnot připojovacího řetězce, které lze použít k úpravě chování logiky sdružování připojení. Další informace naleznete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="pool-fragmentation"></a>Fragmentace fondu  
 Fragmentace fondu je běžný problém v mnoha webových aplikacích, kde aplikace může vytvořit velký počet fondů, které nejsou uvolněny, dokud proces ukončí. To ponechává velký počet připojení otevřené a náročné paměti, což má za následek nízký výkon.  
  
### <a name="pool-fragmentation-due-to-integrated-security"></a>Fragmentace fondu díky integrovanému zabezpečení  
 Připojení jsou sdružena podle připojovacího řetězce a identity uživatele. Proto pokud používáte základní ověřování nebo ověřování systému Windows na webu a integrované přihlášení zabezpečení, získáte jeden fond na uživatele. Přestože to zlepšuje výkon následných požadavků na databázi pro jednoho uživatele, tento uživatel nemůže využít výhod připojení jiných uživatelů. Výsledkem je také alespoň jedno připojení na uživatele k databázovému serveru. Jedná se o vedlejší účinek konkrétní architektury webových aplikací, které musí vývojáři zvážit s požadavky na zabezpečení a auditování.  
  
### <a name="pool-fragmentation-due-to-many-databases"></a>Fragmentace fondu z důvodu mnoha databází  
 Mnoho poskytovatelů služeb Internetu hostuje několik webů na jednom serveru. Mohou použít jednu databázi k potvrzení přihlášení ověřování pomocí formuláře a potom otevřít připojení k určité databázi pro tohoto uživatele nebo skupinu uživatelů. Připojení k databázi ověřování je sdružené a používá každý. Existuje však samostatný fond připojení ke každé databázi, které zvyšují počet připojení k serveru.  
  
 To je také vedlejší účinek návrhu aplikace. Existuje poměrně jednoduchý způsob, jak se vyhnout tento vedlejší účinek bez ohrožení zabezpečení při připojení k serveru SQL Server. Namísto připojení k samostatné databázi pro každého uživatele nebo skupinu se připojte ke stejné databázi na serveru a potom spusťte příkaz Transact-SQL USE a změňte na požadovanou databázi. Následující fragment kódu ukazuje vytvoření počátečního `master` připojení k databázi a následné `databaseName` přepnutí na požadovanou databázi zadanou v proměnné řetězce.  
  
```vb  
' Assumes that command is a valid SqlCommand object and that  
' connectionString connects to master.  
    command.Text = "USE DatabaseName"  
Using connection As New SqlConnection(connectionString)  
    connection.Open()  
    command.ExecuteNonQuery()  
End Using  
```  
  
```csharp  
// Assumes that command is a SqlCommand object and that  
// connectionString connects to master.  
command.Text = "USE DatabaseName";  
using (SqlConnection connection = new SqlConnection(  
  connectionString))  
  {  
    connection.Open();  
    command.ExecuteNonQuery();  
  }  
```  
  
## <a name="application-roles-and-connection-pooling"></a>Role aplikací a sdružování připojení  
 Po aktivaci role aplikace serveru SQL `sp_setapprole` Server voláním uložené procedury systému nelze obnovit kontext zabezpečení tohoto připojení. Pokud je však povoleno sdružování, je připojení vráceno do fondu a při opakovaném použití sdruženého připojení dojde k chybě. Další informace naleznete v článku znalostní báze Knowledge Base "[Chyby role aplikace SQL se sdružováním prostředků technologie OLE DB](https://support.microsoft.com/default.aspx?scid=KB;EN-US;Q229564)" .  
  
### <a name="application-role-alternatives"></a>Alternativy rolí aplikace  
 Doporučujeme využít výhod mechanismů zabezpečení, které můžete použít namísto rolí aplikace. Další informace naleznete [v tématu Vytváření rolí aplikací na serveru SQL Server](./sql/creating-application-roles-in-sql-server.md).  
  
## <a name="see-also"></a>Viz také

- [Sdružování připojení](connection-pooling.md)
- [SQL Server a ADO.NET](./sql/index.md)
- [Čítače výkonu](performance-counters.md)
- [Přehled ADO.NET](ado-net-overview.md)
