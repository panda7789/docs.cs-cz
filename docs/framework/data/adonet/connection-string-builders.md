---
title: Tvůrci připojovacích řetězců
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8434b608-c4d3-43d3-8ae3-6d8c6b726759
ms.openlocfilehash: 8cadeac0bcbf301f7d973e93435885de82052603
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151660"
---
# <a name="connection-string-builders"></a>Tvůrci připojovacích řetězců
V dřívějších verzích ADO.NET nedocházelo ke kontrole připojovacích řetězců s hodnotami zřetězených řetězců, <xref:System.ArgumentException>takže za běhu vygenerovalo nesprávné klíčové slovo . Každý z poskytovatelů dat rozhraní .NET Framework podporoval jinou syntaxi pro klíčová slova připojovacího řetězce, což ztížilo vytváření platných připojovacích řetězců, pokud se provádí ručně. K vyřešení tohoto problému ADO.NET 2.0 zavedla nové tvůrce připojovacího řetězce pro každého zprostředkovatele dat rozhraní .NET Framework. Každý zprostředkovatel dat obsahuje třídu tvůrce připojovacího řetězce silného typu, která dědí z <xref:System.Data.Common.DbConnectionStringBuilder>. V následující tabulce jsou uvedeny zprostředkovatele dat rozhraní .NET Framework a jejich přidružené třídy tvůrce připojovacího řetězce.  
  
|Poskytovatel|Třída ConnectionStringBuilder|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a>Útoky injektáží řetězce připojení  
 K útoku injektáží připojovacího řetězce může dojít při zřetězení dynamického řetězce k vytvoření připojovacích řetězců, které jsou založeny na vstupu uživatele. Pokud řetězec není ověřen a škodlivý text nebo znaky nejsou uvozeny, útočník může potenciálně přistupovat k citlivým datům nebo jiným prostředkům na serveru. Útočník by například mohl připojit útok poskytnutím středníku a připojením další hodnoty. Připojovací řetězec je analyzován pomocí algoritmu "poslední vyhrává" a nepřátelský vstup je nahrazen legitimní hodnotu.  
  
 Třídy tvůrce připojovacího řetězce jsou navrženy tak, aby eliminovaly dohady a chránily před chybami syntaxe a chybami zabezpečení. Poskytují metody a vlastnosti odpovídající známé dvojice klíč/hodnota povolené jednotlivými zprostředkovateli dat. Každá třída udržuje pevnou kolekci synonym a lze přeložit ze synonyma na odpovídající známý název klíče. Kontroly jsou prováděny pro platné dvojice klíč/hodnota a neplatný pár vyvolá výjimku. Kromě toho jsou vstřikované hodnoty zpracovány bezpečným způsobem.  
  
 Následující příklad ukazuje, <xref:System.Data.SqlClient.SqlConnectionStringBuilder> jak zpracovává vložené extra `Initial Catalog` hodnotu pro nastavení.  
  
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
  
 Výstup ukazuje, <xref:System.Data.SqlClient.SqlConnectionStringBuilder> že zpracovány správně uvozením extra hodnotu v uvozovkách namísto připojení k připojovacířetězec jako nový klíč/hodnota dvojice.  
  
```output  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a>Vytváření připojovacích řetězců z konfiguračních souborů  
 Pokud jsou předem známy určité prvky připojovacího řetězce, mohou být uloženy v konfiguračním souboru a načteny za běhu, aby se vytvořil úplný připojovací řetězec. Například název databáze může být znám předem, ale ne název serveru. Nebo můžete chtít, aby uživatel zadat jméno a heslo za běhu, aniž by bylo možné vložit další hodnoty do připojovacího řetězce.  
  
 Jeden z přetížených konstruktorů pro tvůrce <xref:System.String> připojovacího řetězce přebírá jako argument, který umožňuje zadat částečný připojovací řetězec, který pak lze dokončit ze vstupu uživatele. Částečný připojovací řetězec lze uložit do konfiguračního souboru a načíst za běhu.  
  
> [!NOTE]
> Obor <xref:System.Configuration> názvů umožňuje programový přístup ke <xref:System.Web.Configuration.WebConfigurationManager> konfiguračním <xref:System.Configuration.ConfigurationManager> souborům, které používají pro webové aplikace a aplikace systému Windows. Další informace o práci s připojovacími řetězci a konfiguračními soubory naleznete [v tématu Connection Strings and Configuration Files](connection-strings-and-configuration-files.md).  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje načtení částečného připojovacího řetězce <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>z <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>konfiguračního souboru a jeho dokončení nastavením vlastností <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> <xref:System.Data.SqlClient.SqlConnectionStringBuilder>, a . Konfigurační soubor je definován následujícím způsobem.  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
> Je nutné nastavit odkaz `System.Configuration.dll` na v projektu pro spuštění kódu.  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také

- [Připojovací řetězce](connection-strings.md)
- [Ochrana osobních údajů a zabezpečení dat](privacy-and-data-security.md)
- [Přehled ADO.NET](ado-net-overview.md)
