---
title: Tvůrci připojovacích řetězců
description: Přečtěte si o třídách Tvůrce připojovacích řetězců používaných pro různé poskytovatele v ADO.NET, z nichž všechny dědí z DbConnectionStringBuilder.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8434b608-c4d3-43d3-8ae3-6d8c6b726759
ms.openlocfilehash: e493140b4cf5a939e8ae8f42b617fb739ed09dec
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287061"
---
# <a name="connection-string-builders"></a>Tvůrci připojovacích řetězců
V dřívějších verzích ADO.NET se neobjevila kontrola připojovacích řetězců s zřetězenými řetězcovými hodnotami, takže v době běhu se nesprávné klíčové slovo vygenerovalo jako nesprávné <xref:System.ArgumentException> . Každé z zprostředkovatelů .NET Framework dat podporuje odlišnou syntaxi pro klíčová slova připojovacích řetězců, která vytvořila v případě ručního vytvoření platných připojovacích řetězců. Pro vyřešení tohoto problému ADO.NET 2,0 pro každého poskytovatele dat .NET Framework zavedla nové tvůrci připojovacích řetězců. Každý poskytovatel dat obsahuje třídu Tvůrce připojovacích řetězců silného typu, která dědí z <xref:System.Data.Common.DbConnectionStringBuilder> . V následující tabulce jsou uvedeny poskytovatelé dat .NET Framework a jejich přidružené třídy Tvůrce připojovacích řetězců.  
  
|Poskytovatel|ConnectionStringBuilder – třída|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a>Útoky prostřednictvím injektáže připojovacího řetězce  
 Útok injektáže připojovacího řetězce může nastat, pokud se k sestavení připojovacích řetězců, které jsou založeny na vstupu uživatele, používá dynamická zřetězení řetězců. Pokud není řetězec ověřený a škodlivý text nebo znaky nejsou uvozeny, útočník může potenciálně přistupovat k citlivým datům nebo jiným prostředkům na serveru. Útočník by například mohl připojit útok tím, že dodá středník a připojí další hodnotu. Připojovací řetězec je analyzován pomocí algoritmu "poslední jeden server WINS" a nepřátelský vstup je nahrazen legitimní hodnotou.  
  
 Třídy Tvůrce připojovacích řetězců jsou navržené tak, aby se vyloučila přibližná a chráněná proti chybám syntaxe a chybám zabezpečení. Poskytují metody a vlastnosti, které odpovídají známým dvojicím klíč/hodnota povolených každým poskytovatelem dat. Každá třída udržuje pevnou kolekci synonym a může překládat z synonyma na odpovídající název dobře známého klíče. Kontroly jsou prováděny pro platné páry klíč/hodnota a neplatný pár vyvolá výjimku. Vložené hodnoty jsou navíc zpracovávány bezpečným způsobem.  
  
 Následující příklad ukazuje, jak <xref:System.Data.SqlClient.SqlConnectionStringBuilder> zpracovává vloženou další hodnotu pro `Initial Catalog` nastavení.  
  
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
  
 Výstup ukazuje, že je <xref:System.Data.SqlClient.SqlConnectionStringBuilder> správně zpracován pomocí uvozovací hodnoty v uvozovkách místo připojení k připojovacímu řetězci jako nový pár klíč/hodnota.  
  
```output  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a>Sestavování připojovacích řetězců z konfiguračních souborů  
 Pokud jsou některé prvky připojovacího řetězce známy předem, mohou být uloženy do konfiguračního souboru a načteny v době běhu pro vytvoření kompletního připojovacího řetězce. Například název databáze může být známý předem, ale ne název serveru. Nebo můžete chtít, aby uživatel zadal jméno a heslo v době běhu, aniž by bylo možné do připojovacího řetězce vložit další hodnoty.  
  
 Jeden z přetížených konstruktorů pro Tvůrce připojovacích řetězců přijímá <xref:System.String> jako argument, který umožňuje zadat částečný připojovací řetězec, který lze následně dokončit ze vstupu uživatele. Částečný připojovací řetězec může být uložen do konfiguračního souboru a načten v době běhu.  
  
> [!NOTE]
> <xref:System.Configuration>Obor názvů umožňuje programový přístup ke konfiguračním souborům, které používají <xref:System.Web.Configuration.WebConfigurationManager> pro webové aplikace a <xref:System.Configuration.ConfigurationManager> aplikace systému Windows. Další informace o práci s připojovacími řetězci a konfiguračními soubory najdete v tématu [připojovací řetězce a konfigurační soubory](connection-strings-and-configuration-files.md).  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje načtení částečného připojovacího řetězce z konfiguračního souboru a jeho dokončení nastavením <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A> vlastností, a <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> <xref:System.Data.SqlClient.SqlConnectionStringBuilder> . Konfigurační soubor je definován následujícím způsobem.  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
> Chcete-li spustit kód, musíte nastavit odkaz na `System.Configuration.dll` v projektu.  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také

- [Připojovací řetězce](connection-strings.md)
- [Ochrana osobních údajů a zabezpečení dat](privacy-and-data-security.md)
- [Přehled ADO.NET](ado-net-overview.md)
