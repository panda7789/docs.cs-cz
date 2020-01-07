---
title: Nejčastější dotazy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 252ed666-0679-4eea-b71b-2f14117ef443
ms.openlocfilehash: 3cc879e97438138554f1d39cf588e01bfbba28a6
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634697"
---
# <a name="frequently-asked-questions"></a>Nejčastější dotazy

V následujících částech najdete odpovědi na některé běžné problémy, se kterými se můžete setkat při implementaci LINQ.

Další problémy jsou řešeny při [řešení potíží](troubleshooting.md).

## <a name="cannot-connect"></a>Nejde se připojit

Otázka: Nemůžu se připojit k databázi.

A. Ujistěte se, že je připojovací řetězec správný a že je spuštěná instance SQL Server. Všimněte si také, že [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vyžaduje, aby byl povolen protokol pojmenovaných kanálů. Další informace najdete v tématu [výukové postupy](learning-by-walkthroughs.md).

## <a name="changes-to-database-lost"></a>Změny databáze ztraceny

Otázka: Změnil (a) jsem data v databázi, ale při Reran své aplikace už tato změna neexistovala.

A. Ujistěte se, že zavoláte <xref:System.Data.Linq.DataContext.SubmitChanges%2A> k uložení výsledků do databáze.

## <a name="database-connection-open-how-long"></a>Připojení k databázi: jak dlouho chcete otevřít?

Otázka: Jak dlouho zůstane moje připojení k databázi otevřené?

A. Připojení obvykle zůstává otevřené, dokud nespotřebujete výsledky dotazu. Pokud očekáváte, že bude zpracování všech výsledků trvat déle a nejste proti výsledkům ukládání do mezipaměti, použijte pro dotaz <xref:System.Linq.Enumerable.ToList%2A>. V běžných scénářích, kdy se každý objekt zpracovává jenom jednou, je model streamování nadřazený v `DataReader` i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].

Přesné podrobnosti o využití připojení závisí na následujících informacích:

- Stav připojení, je-li <xref:System.Data.Linq.DataContext> vytvořen pomocí objektu připojení.

- Nastavení připojovacího řetězce (například povolení více aktivních sad výsledků (MARS). Další informace najdete v tématu [několik aktivních sad výsledků dotazu (MARS)](../multiple-active-result-sets-mars.md).

## <a name="updating-without-querying"></a>Aktualizace bez dotazování

Otázka: Můžu aktualizovat data tabulky bez prvotního dotazování databáze?

A. I když [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nemá příkazy aktualizace založené na nastavení, můžete použít některý z následujících postupů k aktualizaci bez předchozího dotazování:

- K odeslání kódu SQL použijte <xref:System.Data.Linq.DataContext.ExecuteCommand%2A>.

- Vytvořte novou instanci objektu a inicializujte všechny aktuální hodnoty (pole), které mají vliv na aktualizaci. Pak objekt připojte k <xref:System.Data.Linq.DataContext> pomocí <xref:System.Data.Linq.Table%601.Attach%2A> a upravte pole, které chcete změnit.

## <a name="unexpected-query-results"></a>Neočekávané výsledky dotazu

Otázka: Dotaz vrací neočekávané výsledky. Jak se dá zkontrolovat, co se děje?

A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje několik nástrojů pro kontrolu kódu SQL, který generuje. Jedním z nejdůležitějších je <xref:System.Data.Linq.DataContext.Log%2A>. Další informace najdete v tématu [Podpora ladění](debugging-support.md).

## <a name="unexpected-stored-procedure-results"></a>Neočekávané výsledky uložených procedur

Otázka: Mám uloženou proceduru, jejíž návratová hodnota se počítá pomocí `MAX()`. Když přetáhnem uloženou proceduru na plochu návrháře O/R, návratová hodnota není správná.

A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje dva způsoby, jak vrátit hodnoty generované databází pomocí uložených procedur:

- Pojmenováním výsledku výstupu.

- Explicitním zadáním výstupního parametru.

Následuje příklad nesprávného výstupu. Vzhledem k tomu, že [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nemůže namapovat výsledky, vždy vrátí hodnotu 0:

```sql
create procedure proc2

as

begin

select max(i) from t where name like 'hello'

end
```

Následuje příklad správného výstupu pomocí parametru output:

```sql
create procedure proc2

@result int OUTPUT

as

select @result = MAX(i) from t where name like 'hello'

go
```

Následuje příklad správného výstupu pomocí pojmenování výsledku výstupu:

```sql
create procedure proc2

as

begin

select nax(i) AS MaxResult from t where name like 'hello'

end
```

Další informace najdete v tématu [přizpůsobení operací pomocí uložených procedur](customizing-operations-by-using-stored-procedures.md).

## <a name="serialization-errors"></a>Chyby serializace

Otázka: Při pokusu o serializaci se zobrazí následující chyba: "Type ' System. data. Linq. ChangeTracker + StandardChangeTracker '... není označen jako serializovatelný. "

A. Generování kódu v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje serializaci <xref:System.Runtime.Serialization.DataContractSerializer>. Nepodporuje <xref:System.Xml.Serialization.XmlSerializer> ani <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. Další informace naleznete v tématu [serializace](serialization.md).

## <a name="multiple-dbml-files"></a>Více souborů DBML

Otázka: Když mám více souborů DBML, které sdílejí některé tabulky běžně, zobrazí se chyba kompilátoru.

A. Nastavte **obor názvů kontextu** a vlastnosti **oboru názvů entit** z Návrhář relací objektů na jedinečnou hodnotu pro každý soubor DBML. Tento přístup eliminuje kolizi názvu nebo oboru názvů.

## <a name="avoiding-explicit-setting-of-database-generated-values-on-insert-or-update"></a>Zamezení explicitního nastavení hodnot generovaných databází při vkládání nebo aktualizaci

Otázka: Mám databázovou tabulku s `DateCreated`ovým sloupcem, ve kterém je výchozí nastavení SQL `Getdate()`. Při pokusu o vložení nového záznamu pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]je hodnota nastavena na `NULL`. Očekávalo se, že se má nastavit jako výchozí databáze.

A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zpracovává tuto situaci automaticky pro identitu (Automatický přírůstek) a ROWGUIDCOL (GUID vygenerované databáze) a sloupce časového razítka. V jiných případech byste měli ručně nastavit <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>=`true` a <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>=<xref:System.Data.Linq.Mapping.AutoSync.Always>/<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>/<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate> vlastnosti.

## <a name="multiple-dataloadoptions"></a>Několik DataLoadOptions

Otázka: Můžu zadat další možnosti načítání bez přepsání prvního?

A. Ano. První není přepsána, jako v následujícím příkladu:

```vb
Dim dlo As New DataLoadOptions()
dlo.LoadWith(Of Order)(Function(o As Order) o.Customer)
dlo.LoadWith(Of Order)(Function(o As Order) o.OrderDetails)
```

```csharp
DataLoadOptions dlo = new DataLoadOptions();
dlo.LoadWith<Order>(o => o.Customer);
dlo.LoadWith<Order>(o => o.OrderDetails);
```

## <a name="errors-using-sql-compact-35"></a>Chyby pomocí SQL Compact 3,5

Otázka: Při přetahování tabulek z databáze SQL Server Compact 3,5 se zobrazí chyba.

A. Návrhář relací objektů nepodporuje SQL Server Compact 3,5, i když modul runtime [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. V takovém případě je nutné vytvořit vlastní třídy entit a přidat příslušné atributy.

## <a name="errors-in-inheritance-relationships"></a>Chyby v relacích dědičnosti

Otázka: Použil (a) jsem obrazec dědičnosti panelu nástrojů v Návrhář relací objektů k propojení dvou entit, ale zobrazí se chyby.

A. Vytvoření relace není dostatečné. Musíte zadat informace, jako je sloupec diskriminátor, hodnota diskriminátoru základní třídy a hodnota diskriminátoru odvozené třídy.

## <a name="provider-model"></a>Model poskytovatele

Otázka: Je k dispozici model veřejného poskytovatele?

A. Není k dispozici žádný model veřejného poskytovatele. V tuto chvíli [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje jenom SQL Server a SQL Server Compact 3,5.

## <a name="sql-injection-attacks"></a>Útoky prostřednictvím injektáže SQL

Otázka: Jak se [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] chránit před útoky prostřednictvím injektáže SQL?

A. Injektáže SQL bylo významně rizikové pro tradiční dotazy SQL vytvořené zřetězením uživatelského vstupu. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se vyhnout takovému vložení pomocí <xref:System.Data.SqlClient.SqlParameter> v dotazech. Vstup uživatele je převeden do hodnot parametrů. Tento přístup zabraňuje použití škodlivých příkazů ze vstupu zákazníka.

## <a name="changing-read-only-flag-in-dbml-files"></a>Změna příznaku jen pro čtení v souborech DBML

Otázka: Při vytváření objektového modelu ze souboru DBML Návody eliminovat metody setter z některých vlastností?

A. V tomto pokročilém scénáři proveďte následující kroky:

1. V souboru. dbml upravte vlastnost změnou příznaku <xref:System.Data.Linq.ITable.IsReadOnly%2A> na `True`.

2. Přidejte částečnou třídu. Vytvořte konstruktor s parametry pro členy jen pro čtení.

3. Zkontrolujte výchozí hodnotu <xref:System.Data.Linq.Mapping.UpdateCheck> (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>), abyste zjistili, jestli je to správná hodnota pro vaši aplikaci.

    > [!CAUTION]
    > Pokud používáte Návrhář relací objektů v aplikaci Visual Studio, mohou být změny přepsány.

## <a name="aptca"></a>APTCA

Otázka: Je System. data. Linq označen pro použití částečně důvěryhodným kódem?

A. Ano, sestavení System. data. Linq. dll je mezi nimi .NET Framework sestavení označená atributem <xref:System.Security.AllowPartiallyTrustedCallersAttribute>. Bez tohoto označení jsou sestavení v .NET Framework určena pouze pro použití plně důvěryhodným kódem.

Hlavní scénář v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pro povolení částečně důvěryhodným volajícím je povolit přístup k [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sestavení z webových aplikací, kde je konfigurace *vztahu důvěryhodnosti* střední.

## <a name="mapping-data-from-multiple-tables"></a>Mapování dat z více tabulek

Otázka: Data v mé entitě pocházejí z více tabulek. Návody namapovat?

A. V databázi můžete vytvořit zobrazení a mapovat entitu na zobrazení. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje stejný SQL pro zobrazení v tabulkách.

> [!NOTE]
> Použití zobrazení v tomto scénáři má omezení. Tento přístup funguje nejvíce bezpečně, pokud jsou operace prováděné na <xref:System.Data.Linq.Table%601> podporovány podkladovým zobrazením. Pouze víte, které operace jsou určeny. Například většina aplikací je jen pro čtení a další výraznou číslo provádí `Create`/`Update`/`Delete`ch operací jenom pomocí uložených procedur pro zobrazení.

## <a name="connection-pooling"></a>Sdružování připojení

Otázka: Je k dispozici konstrukce, která může pomáhat s <xref:System.Data.Linq.DataContext> sdružováním?

A. Nepokoušejte se znovu použít instance <xref:System.Data.Linq.DataContext>. Každý <xref:System.Data.Linq.DataContext> udržuje stav (včetně mezipaměti identit) pro jednu konkrétní relaci úprav/dotazů. Chcete-li získat nové instance založené na aktuálním stavu databáze, použijte novou <xref:System.Data.Linq.DataContext>.

Můžete dál používat základní sdružování připojení ADO.NET. Další informace najdete v tématu věnovaném [sdružování připojení SQL Server (ADO.NET)](../../sql-server-connection-pooling.md).

## <a name="second-datacontext-is-not-updated"></a>Druhý kontext kontextu není aktualizován.

Otázka: Použil (a) jsem jednu instanci <xref:System.Data.Linq.DataContext> k uložení hodnot v databázi. Druhý <xref:System.Data.Linq.DataContext> ve stejné databázi ale neodráží aktualizované hodnoty. Druhá instance <xref:System.Data.Linq.DataContext> pravděpodobně vrátila hodnoty uložené v mezipaměti.

A. Toto chování je záměrné. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nadále vrací stejné instance nebo hodnoty, které jste viděli v první instanci. Při provádění aktualizací se používá Optimistická souběžnost. Původní data se používají ke kontrole stavu aktuální databáze a k vyhodnocení, že se ve skutečnosti stále nezměnila. Pokud došlo ke změně, dojde ke konfliktu a aplikace ji musí vyřešit. Jednou z možností aplikace je obnovit původní stav do stavu aktuální databáze a pokusit se o aktualizaci. Další informace najdete v tématu [How to: Manage Change konflikty](how-to-manage-change-conflicts.md).

Můžete také nastavit <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> na false, což vypne ukládání do mezipaměti a sledování změn. Pak můžete načíst nejnovější hodnoty pokaždé, když budete dotazováni.

## <a name="cannot-call-submitchanges-in-read-only-mode"></a>Nelze volat SubmitChanges v režimu jen pro čtení.

Otázka: Při pokusu o volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A> v režimu jen pro čtení se zobrazí chyba.

A. Režim jen pro čtení vypne schopnost kontextu sledovat změny.

## <a name="see-also"></a>Viz také:

- [Odkazy](reference.md)
- [Odstraňování potíží](troubleshooting.md)
- [Zabezpečení v LINQ to SQL](security-in-linq-to-sql.md)
