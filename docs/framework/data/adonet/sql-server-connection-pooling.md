---
title: Sdružování připojení SQL Serveru (ADO.NET)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e51d44e-7c4e-4040-9332-f0190fe36f07
ms.openlocfilehash: 0a8d10b9d6ae80bb4fa38445e0335151661c41eb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918142"
---
# <a name="sql-server-connection-pooling-adonet"></a>Sdružování připojení SQL Serveru (ADO.NET)
Připojení k databázovému serveru se obvykle skládá z několika časově náročných kroků. Musí se navázat fyzický kanál, jako je například soket nebo pojmenovaný kanál. musí se vyskytnout počáteční Metoda handshake se serverem, informace o připojovacím řetězci musí být analyzovány, musí být spuštěny pro zařazení do aktuální transakce a tak dále.  
  
 V praxi většina aplikací používá pro připojení jenom jednu nebo několik různých konfigurací. To znamená, že během provádění aplikace se opakovaně otevírají a zavřou spousta identických připojení. Pro minimalizaci nákladů na otevírání připojení používá ADO.NET techniku optimalizace nazývanující *sdružování připojení*.  
  
 Sdružování připojení snižuje počet, kolikrát musí být otevřená nová připojení. *Pooler* udržuje vlastnictví fyzického připojení. Spravuje připojení tak, že udržuje pro každou konfiguraci připojení sadu aktivních připojení. Pokaždé, když `Open` uživatel volá připojení, Pooler vyhledá dostupné připojení ve fondu. Pokud je připojení ve fondu k dispozici, vrátí ho volajícímu místo otevření nového připojení. Když aplikace volá `Close` připojení, vrátí ji Pooler do fondu sady aktivních připojení místo jejího zavření. Jakmile se připojení vrátí do fondu, je připraveno k opětovnému použití při dalším `Open` volání.  
  
 Sdružená můžou být jenom připojení se stejnou konfigurací. ADO.NET udržuje několik fondů ve stejnou dobu, jednu pro každou konfiguraci. Připojení jsou při použití integrovaného zabezpečení rozdělená na fondy podle připojovacího řetězce a identity Windows. Připojení jsou také sdružená na základě toho, zda jsou zařazeny do transakce. Když použijete <xref:System.Data.SqlClient.SqlConnection.ChangePassword%2A> <xref:System.Data.SqlClient.SqlCredential> , instance ovlivní fond připojení. Různé instance <xref:System.Data.SqlClient.SqlCredential> nástroje budou používat různé fondy připojení, a to i v případě, že je ID uživatele a heslo stejné.  
  
 Připojení sdružování můžou významně zlepšit výkon a škálovatelnost vaší aplikace. Ve výchozím nastavení je sdružování připojení povolené v ADO.NET. Pokud je explicitně nezakážete, Pooler optimalizuje připojení při jejich otevření a zavření ve vaší aplikaci. Můžete také dodat několik modifikátorů připojovacího řetězce pro řízení chování sdružování připojení. Další informace najdete v části řízení sdružování připojení pomocí klíčových slov připojovacího řetězce dále v tomto tématu.  
  
> [!NOTE]
> Když je sdružování připojení povolené a pokud dojde k chybě časového limitu nebo jiné chybě přihlášení, vyvolá se výjimka a následné pokusy o připojení selžou po dobu dalších pěti sekund, což je "blokující perioda". Pokud se aplikace pokusí připojit v rámci blokujícího období, bude znovu vyvolána první výjimka. Následná selhání po uplynutí doby blokování budou mít za následek novou dobu blokování, která bude dvakrát po dobu, po kterou se zablokuje, maximálně po dobu jedné minuty.  
  
## <a name="pool-creation-and-assignment"></a>Vytvoření a přiřazení fondu  
 Při prvním otevření připojení se vytvoří fond připojení založený na přesně odpovídajícím algoritmu, který přidruží fond k připojovacímu řetězci v připojení. Každý fond připojení je přidružený k jedinečnému připojovacímu řetězci. Pokud se při otevření nového připojení nejedná o přesný řetězec odpovídající existujícímu fondu, vytvoří se nový fond. Připojení jsou sdružená podle procesu, podle domény aplikace, podle připojovacího řetězce a při použití integrovaného zabezpečení podle identity systému Windows. Připojovací řetězce musí mít také přesnou shodu; Klíčová slova dodaná v jiném pořadí pro stejné připojení budou sdružená samostatně.  
  
 V následujícím C# příkladu jsou vytvořeny tři nové <xref:System.Data.SqlClient.SqlConnection> objekty, ale pro jejich správu jsou vyžadovány pouze dva fondy připojení. Všimněte si, že první a druhý řetězec připojení se liší podle přiřazené `Initial Catalog`hodnoty.  
  
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
  
 Pokud `MinPoolSize` buď není zadáno v připojovacím řetězci nebo je zadáno jako nula, připojení ve fondu budou po určité době nečinnosti zavřena. Pokud je však zadaná `MinPoolSize` hodnota větší než nula, fond připojení nebude zničen, `AppDomain` dokud nebude uvolněn a proces skončí. Údržba neaktivních nebo prázdných fondů zahrnuje minimální nároky na systém.  
  
> [!NOTE]
> Fond se automaticky vymaže, když dojde k závažné chybě, třeba při převzetí služeb při selhání.  
  
## <a name="adding-connections"></a>Přidávání připojení  
 U každého jedinečného připojovacího řetězce se vytvoří fond připojení. Při vytvoření fondu se vytvoří víc objektů připojení a přidají se do fondu, aby se splnil minimální požadavek na velikost fondu. Připojení se do fondu přidají podle potřeby až do maximální zadané velikosti fondu (výchozí hodnota je 100). Připojení se uvolní zpátky do fondu, když se zavřou nebo odstraněly.  
  
 Když je požadován objekt, získá se z fondu, pokud je k dispozici použitelné připojení. <xref:System.Data.SqlClient.SqlConnection> Aby bylo možné použít připojení, musí být připojení nepoužitelné, mít odpovídající kontext transakce nebo být Nepřidruženo k jakémukoli kontextu transakce a musí obsahovat platný odkaz na server.  
  
 Pooler připojení splňuje požadavky na připojení tím, že je znovu přidělí, protože se uvolní do fondu. Pokud byla dosažena maximální velikost fondu a není k dispozici žádné použitelné připojení, je požadavek zařazen do fronty. Pooler se pak pokusí uvolnit všechna připojení až do vypršení časového limitu (výchozí hodnota je 15 sekund). Pokud Pooler nemůže požadavek splnit, než vyprší časový limit připojení, je vyvolána výjimka.  
  
> [!CAUTION]
>  Důrazně doporučujeme, abyste připojení vždy zavřeli, až ho budete používat, aby se připojení vrátilo do fondu. `Close` Můžete to provést pomocí metody `Connection` nebo objektu nebo `Dispose` otevřením všech C# `Using` připojení uvnitř `using` příkazu v nebo v příkazu Visual Basic. Nemusejí být do fondu přidány ani vráceny připojení, která nejsou explicitně zavřena. Další informace naleznete v tématu [using](../../../csharp/language-reference/keywords/using-statement.md) a [How to: Dispose systémového prostředku](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md) pro Visual Basic.  
  
> [!NOTE]
> `Close` Nevolejte nebo `Dispose` na `Connection`, `Finalize` nebo na jiný spravovaný objekt v metodě vaší třídy. `DataReader` V finalizační metodě pouze uvolní nespravované prostředky, které vaše třída vlastní. Pokud vaše třída nevlastní žádné nespravované prostředky, `Finalize` nezahrnujte metodu do definice třídy. Další informace najdete v tématu [uvolňování paměti](../../../standard/garbage-collection/index.md).  
  
Další informace o událostech spojených s otevřením a zavřením připojení najdete v tématu [audit třídy událostí přihlášení](/sql/relational-databases/event-classes/audit-login-event-class) a [třídy události odhlášení auditu](/sql/relational-databases/event-classes/audit-logout-event-class) v dokumentaci k SQL Server.  
  
## <a name="removing-connections"></a>Odebírání připojení  
 Připojení Pooler Odebere připojení z fondu poté, co bylo nečinné po dobu přibližně 4-8 minut, nebo pokud Pooler zjistí, že spojení se serverem bylo přerušeno. Je možné, že se po pokusu o komunikaci se serverem zjistí zavážné připojení. Pokud se zjistí připojení, které už není připojené k serveru, je označený jako neplatný. Neplatná připojení jsou odebrána z fondu připojení pouze v případě, že jsou zavřena nebo znovu získána.  
  
 Pokud připojení existuje na serveru, který zmizel, může být toto připojení vykresleno z fondu i v případě, že Pooler připojení nerozpoznalo vážné připojení a označil ho jako neplatný. Jedná se o případ, že režie kontroly, že připojení je stále platné, by vyloučila výhody použití Pooler tím, že by mohlo dojít k dalšímu přenosu zpráv do serveru. Pokud k tomu dojde, při prvním pokusu o použití připojení zjistíte, že připojení bylo vážně navázáno, a vyvolá se výjimka.  
  
## <a name="clearing-the-pool"></a>Vymazávání fondu  
 ADO.NET 2,0 zavedl dvě nové metody pro vymazání fondu: <xref:System.Data.SqlClient.SqlConnection.ClearAllPools%2A> a <xref:System.Data.SqlClient.SqlConnection.ClearPool%2A>. `ClearAllPools`Vymaže fondy připojení pro daného zprostředkovatele a `ClearPool` vymaže fond připojení, který je přidružen ke konkrétnímu připojení. Pokud jsou v době volání používána připojení, jsou označeny příznakem odpovídajícím způsobem. Pokud jsou uzavřeny, budou namísto návratu do fondu zahozeny.  
  
## <a name="transaction-support"></a>Podpora transakcí  
 Připojení jsou vykreslena z fondu a přiřazena na základě kontextu transakce. Pokud `Enlist=false` není v připojovacím řetězci zadán, fond připojení zajistí, že je připojení zařazeno <xref:System.Transactions.Transaction.Current%2A> v kontextu. Když je připojení uzavřeno a vráceno do fondu se zařazenou `System.Transactions` transakcí, je nastaveno tak, že další požadavek pro daný fond připojení se stejnou `System.Transactions` transakcí vrátí stejné připojení, pokud je k dispozici. Pokud je taková žádost vystavená a nejsou k dispozici žádná připojení ve fondu, připojení se vykreslí z části fondu, která není v transakčním režimu, a zařadí se do ní. Pokud nejsou žádná připojení dostupná v žádné z oblastí fondu, vytvoří se nové připojení a zařadí se.  
  
 Když je připojení ukončeno, je uvolněno zpátky do fondu a do příslušného dílčího dělení na základě jeho transakčního kontextu. Proto můžete připojení zavřít bez vygenerování chyby, i když distribuovaná transakce stále čeká na vyřízení. To vám umožní později odeslat nebo zrušit distribuovanou transakci.  
  
## <a name="controlling-connection-pooling-with-connection-string-keywords"></a>Řízení sdružování připojení pomocí klíčových slov připojovacího řetězce  
 `ConnectionString` Vlastnost<xref:System.Data.SqlClient.SqlConnection> objektu podporuje páry klíč/hodnota připojovacího řetězce, které lze použít k úpravě chování logiky sdružování připojení. Další informace naleznete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="pool-fragmentation"></a>Fragmentace fondu  
 Fragmentace fondu je běžný problém v mnoha webových aplikacích, kde aplikace může vytvořit velký počet fondů, které nejsou uvolněny, dokud se proces neukončí. Tím dojde k tomu, že se velké množství připojení otevře a spotřebovává paměť, což vede k špatnému výkonu.  
  
### <a name="pool-fragmentation-due-to-integrated-security"></a>Fragmentace fondu z důvodu integrovaného zabezpečení  
 Připojení jsou sdružená podle připojovacího řetězce plus identity uživatele. Proto pokud na webu používáte základní ověřování nebo ověřování systému Windows a integrované přihlášení zabezpečení, získáte jeden fond na uživatele. I když to zlepšuje výkon následných databázových požadavků pro jednoho uživatele, tento uživatel nemůže využívat připojení, která udělali jiní uživatelé. Také má za následek aspoň jedno připojení pro každého uživatele k databázovému serveru. Toto je vedlejší účinek konkrétní architektury webové aplikace, kterou vývojáři musí zvážit před požadavky na zabezpečení a auditování.  
  
### <a name="pool-fragmentation-due-to-many-databases"></a>Fragmentace fondu v důsledku mnoha databází  
 Mnoho poskytovatelů internetových služeb hostuje několik webů na jednom serveru. Můžou použít izolovanou databázi k potvrzení přihlášení k ověřování pomocí formulářů a pak otevřít připojení ke konkrétní databázi pro daného uživatele nebo skupinu uživatelů. Připojení k databázi ověřování je sdružené a používané všemi uživateli. Existuje však samostatný fond připojení ke každé databázi, který zvyšuje počet připojení k serveru.  
  
 To je také vedlejší efekt návrhu aplikace. Existuje poměrně jednoduchý způsob, jak zabránit tomuto vedlejšímu účinku, aniž by došlo k narušení zabezpečení při připojení k SQL Server. Namísto připojení k samostatné databázi pro každého uživatele nebo skupinu se připojte ke stejné databázi na serveru a potom spuštěním příkazu Transact-SQL použijte příkaz ke změně na požadovanou databázi. Následující fragment kódu ukazuje vytvoření počátečního připojení k `master` databázi a přechod na požadovanou databázi zadanou `databaseName` v řetězcové proměnné.  
  
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
  
## <a name="application-roles-and-connection-pooling"></a>Aplikační role a sdružování připojení  
 Po aktivaci role SQL Server aplikace voláním `sp_setapprole` systémové uložené procedury nelze obnovit kontext zabezpečení tohoto připojení. Pokud je ale povoleno sdružování do fondu, bude se připojení vracet do fondu a při opětovném použití sdruženého připojení dojde k chybě. Další informace najdete v článku znalostní báze "[chyby rolí aplikace SQL s OLE DB sdružování zdrojů](https://support.microsoft.com/default.aspx?scid=KB;EN-US;Q229564)."  
  
### <a name="application-role-alternatives"></a>Alternativy aplikační role  
 Doporučujeme, abyste využili výhod mechanismů zabezpečení, které můžete použít místo aplikačních rolí. Další informace najdete v tématu [vytváření aplikačních rolí v SQL Server](../../../../docs/framework/data/adonet/sql/creating-application-roles-in-sql-server.md).  
  
## <a name="see-also"></a>Viz také:

- [Sdružování připojení](../../../../docs/framework/data/adonet/connection-pooling.md)
- [SQL Server a ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)
- [Čítače výkonu](../../../../docs/framework/data/adonet/performance-counters.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
