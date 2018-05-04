---
title: Tvůrci řetězců pro připojení
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8434b608-c4d3-43d3-8ae3-6d8c6b726759
ms.openlocfilehash: 01bbf726ffa8d1c595b1ef53df420431bf28560f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="connection-string-builders"></a>Tvůrci řetězců pro připojení
V dřívějších verzích [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], kompilace kontrola připojovací řetězce s spojený řetězec hodnoty se neuskutečnilo, tak, aby v době běhu nesprávné – klíčové slovo generované <xref:System.ArgumentException>. Každý z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatelé dat podporována jinou syntaxi pro klíčová slova řetězec připojení, kterým vytváření obtížné platný připojovací řetězce, je-li provést ručně. Chcete-li vyřešit tento problém [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 zavedl nový Tvůrci řetězců pro připojení pro každou [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dat zprostředkovatele. Každý poskytovatel dat zahrnuje třídy tvůrce řetězec silného typu připojení, která dědí z <xref:System.Data.Common.DbConnectionStringBuilder>. Následující tabulka uvádí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatelé dat a jejich přidružené připojení řetězec Tvůrce třídy.  
  
|Zprostředkovatel|ConnectionStringBuilder – třída|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a>Prostřednictvím injektáže řetězec připojení  
 Útok prostřednictvím injektáže řetězec připojení může dojít, když dynamické zřetězení slouží k vytvoření připojovací řetězce, které jsou založeny na vstup uživatele. Pokud řetězec není ověřená a škodlivý text nebo znaky není řídicí sekvencí, útočník mají přístup k citlivým datům nebo jiným prostředkům na serveru. Například útočník může připojit útoku zadávání středník a připojením algoritmu další hodnotu. Připojovací řetězec je analyzován pomocí algoritmu "poslední jeden wins" a je nahrazena nepřátelských vstup pro hodnotu legitimní.  
  
 Připojovací řetězec Tvůrce třídy jsou navrženy pro vyloučení již nebudete muset odhadovat a chránit proti chyby syntaxe a ohrožení zabezpečení. Poskytuje metody a vlastnosti odpovídající páry známé klíč/hodnota, které jsou povolené každý poskytovatel dat. Každá třída udržuje pevné kolekci synonyma a může překládat z synonymum na odpovídající známý název klíče. Ověřování pro dvojice klíč/hodnota platná a vyvolá výjimku, dvojici neplatný. Kromě toho vloženého hodnoty jsou zpracovávány v nouzovém režimu.  
  
 Následující příklad ukazuje, jak <xref:System.Data.SqlClient.SqlConnectionStringBuilder> zpracovává vložené navíc hodnotu pro `Initial Catalog` nastavení.  
  
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
  
 Výstup ukazuje, že <xref:System.Data.SqlClient.SqlConnectionStringBuilder> to správně zpracovat uvozovací znaky navíc hodnotu do dvojitých uvozovek místo přidávání připojovací řetězec jako nový pár klíč/hodnota.  
  
```  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a>Vytváření připojovacích řetězců z konfiguračních souborů  
 Pokud některé prvky připojovacího řetězce jsou známé předem, může být uložené v konfiguračním souboru a načíst v době běhu vytvořit úplný připojovací řetězec. Název databáze může být například předem známé, ale není název serveru. Nebo můžete chtít uživatele k zadání jména a hesla v době běhu aniž by bylo možné vložit další hodnoty do připojovacího řetězce.  
  
 Jeden z přetížené konstruktory pro Tvůrce připojovacích řetězců trvá <xref:System.String> jako argument, který můžete zadat částečné připojovací řetězec, který je pak možné provést z vstup uživatele. Částečné připojovací řetězec lze uložené v konfiguračním souboru a načítat za běhu.  
  
> [!NOTE]
>  <xref:System.Configuration> Obor názvů umožňuje programový přístup ke konfiguračním souborům, které používají <xref:System.Web.Configuration.WebConfigurationManager> pro webové aplikace a <xref:System.Configuration.ConfigurationManager> pro aplikace pro Windows. Další informace o práci s připojovací řetězce a konfigurační soubory, najdete v části [připojovací řetězce a konfigurační soubory](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje načítání částečné připojovacího řetězce z konfiguračního souboru a dokončení nastavením <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>, a <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> vlastnosti <xref:System.Data.SqlClient.SqlConnectionStringBuilder>. Konfigurační soubor je definován následujícím způsobem.  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"   
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
>  Je nutné nastavit odkaz na `System.Configuration.dll` ve vašem projektu pro kód pro spuštění.  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Připojovací řetězce](../../../../docs/framework/data/adonet/connection-strings.md)  
 [Ochrana osobních údajů a zabezpečení dat](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
