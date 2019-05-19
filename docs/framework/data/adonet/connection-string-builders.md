---
title: Tvůrci připojovacích řetězců
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8434b608-c4d3-43d3-8ae3-6d8c6b726759
ms.openlocfilehash: f0510b9e3f31686e22532f21989cb95905522286
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65879899"
---
# <a name="connection-string-builders"></a>Tvůrci připojovacích řetězců
V dřívějších verzích rozhraní ADO.NET, kompilace kontrolu připojovací řetězce s hodnotami zřetězených řetězců nedošlo, tak, aby v době běhu, vygeneruje nesprávná klíčové slovo <xref:System.ArgumentException>. Každý zprostředkovatele dat .NET Framework nepodporuje jinou syntaxi pro klíčová slova řetězec připojení, které vytváření platný připojovací řetězce obtížné, je-li provést ručně. Chcete-li tento problém vyřešit, ADO.NET 2.0 zavedeny nové tvůrci připojovacích řetězců pro každého poskytovatele dat .NET Framework. Každý poskytovatel dat zahrnuje třídu Tvůrce řetězec silného typu připojení, která dědí z <xref:System.Data.Common.DbConnectionStringBuilder>. Následující tabulka uvádí třídy tvůrce jejich přidružený připojovací řetězec a zprostředkovatele dat .NET Framework.  
  
|Poskytovatel|Třída ConnectionStringBuilder|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a>Útoky prostřednictvím injektáže připojovací řetězec  
 Útok prostřednictvím injektáže řetězec připojení může dojít, když dynamická zřetězení sloužící k vytvoření připojovací řetězce, které jsou založeny na vstup uživatele. Pokud řetězec není ověřená a škodlivý text nebo znaky nejsou uvozeny řídicími znaky, útočník můžou mít přístup k citlivým datům nebo další prostředky na serveru. Útočník může například připojte útoku zadáním středník a přidávání další hodnotu. Připojovací řetězec je analyzován pomocí algoritmu "posledním místě wins" a nebezpečný vstup je nahrazen legitimní hodnotu.  
  
 Třídy tvůrce řetězec připojení jsou navrženy tak, aby obsahoval jenom izolovat a chránit proti chyby syntaxe a ohrožení zabezpečení. Poskytuje metody a vlastnosti odpovídající dvojice klíč/hodnota známé od každého poskytovatele dat. Každá třída udržuje pevné kolekce synonym a může překládat z synonymum pro odpovídající dobře známý název klíče. Kontroly jsou prováděny pro páry klíč/hodnota platný a vyvolá výjimku, neplatný pár. Kromě toho jsou zpracovány vloženého hodnoty bezpečným způsobem.  
  
 Následující příklad ukazuje, jak <xref:System.Data.SqlClient.SqlConnectionStringBuilder> zpracovává vložený hodnotu navíc pro `Initial Catalog` nastavení.  
  
```vb  
Dim builder As New System.Data.SqlClient.SqlConnectionStringBuilder  
builder("Data Source") = "(local)"  
builder("Integrated Security") = True  
builder("Initial Catalog") = "AdventureWorks;NewValue=Bad"  
Console.WriteLine(builder.ConnectionString)  
```  
  
```csharp  
System.Data.SqlClient.SqlConnectionStringBuilder builder =  
  new System.Data.SqlClient.SqlConnectionStringBuilder();  
builder["Data Source"] = "(local)";  
builder["integrated Security"] = true;  
builder["Initial Catalog"] = "AdventureWorks;NewValue=Bad";  
Console.WriteLine(builder.ConnectionString);  
```  
  
 Výstup ukazuje, že <xref:System.Data.SqlClient.SqlConnectionStringBuilder> to správně zpracovat uvozovací znaky navíc hodnotu do dvojitých uvozovek místo připojování na připojovací řetězec jako nové dvojice klíč/hodnota.  
  
```  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a>Vytváření připojovacích řetězců z konfiguračních souborů  
 Pokud některé prvky připojovacího řetězce je znám předem, můžou být uložené v konfiguračním souboru a načíst za běhu a sestavit úplný připojovací řetězec. Název databáze může být například předem známé, ale ne názvu serveru. Nebo může být vhodné uživatele k zadání jména a hesla v době běhu aniž by bylo možné vložit další hodnoty do připojovacího řetězce.  
  
 Přijímá jednu z přetížených konstruktorů pro Tvůrce připojovacích řetězců <xref:System.String> jako argument, což vám umožní zadat částečné připojovací řetězec, který lze pak provést ze vstupu uživatele. Částečné připojovací řetězec můžete uložené v konfiguračním souboru a načíst za běhu.  
  
> [!NOTE]
>  <xref:System.Configuration> Obor názvů umožňuje programový přístup ke konfiguračním souborům, které používají <xref:System.Web.Configuration.WebConfigurationManager> pro webové aplikace a <xref:System.Configuration.ConfigurationManager> pro aplikace Windows. Další informace o práci s připojovací řetězce a konfigurační soubory, naleznete v tématu [připojovací řetězce a konfigurační soubory](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje načítání částečné připojovacího řetězce z konfiguračního souboru a jeho dokončení nastavením <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>, a <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> vlastnosti <xref:System.Data.SqlClient.SqlConnectionStringBuilder>. Konfigurační soubor je definovaná následujícím způsobem.  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"   
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
>  Je nutné nastavit odkaz na `System.Configuration.dll` ve vašem projektu pro spuštění kódu.  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Připojovací řetězce](../../../../docs/framework/data/adonet/connection-strings.md)
- [Ochrana osobních údajů a zabezpečení dat](../../../../docs/framework/data/adonet/privacy-and-data-security.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
