---
title: Souběžné spouštění v ADO.NET
ms.date: 03/30/2017
ms.assetid: 9f9ba96d-9f89-4f65-bb2f-6860879f4393
ms.openlocfilehash: 377af3c72b0a9a8eb26c8713d98f114803f08356
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583617"
---
# <a name="side-by-side-execution-in-adonet"></a>Souběžné spouštění v ADO.NET
Spuštění vedle sebe v rozhraní .NET Framework je schopnost spouští aplikaci, která v počítači, který má více verzí rozhraní .NET Framework nainstalované, výhradně pomocí verze, pro kterou byla aplikace zkompilována. Podrobné informace o konfiguraci spuštění vedle sebe, naleznete v tématu [spuštění vedle sebe](../../../../docs/framework/deployment/side-by-side-execution.md).  
  
 Aplikaci zkompilován pomocí jedné verze rozhraní .NET Framework lze spustit na jinou verzi rozhraní .NET Framework. Doporučujeme však kompilaci verze aplikace pro každou nainstalovanou verzi rozhraní .NET Framework a spouštět je samostatně. V obou scénářích byste měli vědět o změnách v [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] mezi verzemi, které mohou ovlivnit kompatibilitu nebo zpětné kompatibility aplikace.  
  
## <a name="forward-compatibility-and-backward-compatibility"></a>Dopředná kompatibilita a zpětné kompatibility  
 Dopředná kompatibilita znamená, že aplikace mohou být zkompilovány se starší verzí rozhraní .NET Framework, ale bude stále spuštěn úspěšně na novější verzi rozhraní .NET Framework. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] kód napsaný pro rozhraní .NET Framework verze 1.1 je dopředně kompatibilní s novějšími verzemi.  
  
 Zpětná kompatibilita znamená, že je zkompilován novější verzi rozhraní .NET Framework pro aplikace, ale bude pokračovat ve starších verzích rozhraní .NET Framework bez ztráty funkčnosti. Samozřejmě to nebude v případě funkce v nové verzi rozhraní .NET Framework.  
  
## <a name="the-net-framework-data-provider-for-odbc"></a>Zprostředkovatel dat .NET Framework pro ODBC  
 Počínaje verzí 1.1, zprostředkovatele dat .NET Framework pro ODBC (<xref:System.Data.Odbc>) je součástí rozhraní .NET Framework. Zprostředkovatel dat rozhraní ODBC je k dispozici pro vývojáře v rozhraní .NET Framework verze 1.0 ke stažení na webu z [středisko pro vývojáře úložiště a přístup k datům](https://go.microsoft.com/fwlink/?linkid=4173). Obor názvů pro stažené zprostředkovatele dat .NET Framework pro ODBC je **Microsoft.Data.Odbc**.  
  
 Pokud máte aplikace vyvinutá pro rozhraní .NET Framework verze 1.0, používá zprostředkovatel dat rozhraní ODBC pro připojení ke zdroji dat a chcete tuto aplikaci spustit v rozhraní .NET Framework verze 1.1 nebo novější verze, je nutné aktualizovat obor názvů pro dat rozhraní ODBC zprostředkovatele, aby **System.Data.Odbc**. Je pak nutné ji znovu zkompilovat pro novější verzi rozhraní .NET Framework.  
  
 Pokud máte aplikace vyvinutá pro rozhraní .NET Framework verze 2.0 nebo novější, který používá poskytovatele dat rozhraní ODBC pro připojení ke zdroji dat a chcete tuto aplikaci spustit v rozhraní .NET Framework verze 1.0, je nutné stáhnout poskytovatele dat rozhraní ODBC a nainstalovat ji v rozhraní .NET Framework verze 1.0 systému. Pak musíte změnit obor názvů pro zprostředkovatele dat rozhraní ODBC do **Microsoft.Data.Odbc**a znovu zkompilovat aplikaci pro rozhraní .NET Framework verze 1.0.  
  
## <a name="the-net-framework-data-provider-for-oracle"></a>Zprostředkovatel dat .NET Framework pro Oracle  
 Počínaje verzí 1.1, zprostředkovatele dat .NET Framework pro Oracle (<xref:System.Data.OracleClient>) je součástí rozhraní .NET Framework. Poskytovatel dat je k dispozici pro vývojáře v rozhraní .NET Framework verze 1.0 ke stažení na webu z [středisko pro vývojáře úložiště a přístup k datům](https://go.microsoft.com/fwlink/?linkid=4173).  
  
 Pokud máte aplikace vyvinutá pro rozhraní .NET Framework verze 2.0 nebo novější, který používá poskytovatele dat pro připojení ke zdroji dat a chcete tuto aplikaci spustit v rozhraní .NET Framework verze 1.0, musíte stáhnout poskytovatele dat a nainstalovat .NE Systém T Framework verze 1.0.  
  
## <a name="code-access-security"></a>Zabezpečení přístupu kódu  
 Zprostředkovatelé dat .NET Framework v rozhraní .NET Framework verze 1.0 (<xref:System.Data.SqlClient>, <xref:System.Data.OleDb>) jsou potřeba ke spouštění pomocí oprávnění FullTrust. Žádný pokus o použití zprostředkovatele dat .NET Framework k z rozhraní .NET Framework verze 1.0 v zóně s méně než způsobí, že oprávnění FullTrust <xref:System.Security.SecurityException>.  
  
 Nicméně od verze rozhraní .NET Framework verze 2.0, všechny zprostředkovatele dat .NET Framework lze použít v částečně důvěryhodné zóny. Kromě toho novou funkci zabezpečení byl přidán do zprostředkovatele dat .NET Framework v rozhraní .NET Framework verze 1.1. Tato funkce umožňuje omezit jaké připojovací řetězce lze použít v zóně s konkrétním zabezpečení. Můžete také zakázat použití prázdného hesla pro zabezpečení pro konkrétní zónu. Další informace najdete v tématu [zabezpečení přístupu kódu a ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md).  
  
 Protože každý instalace rozhraní .NET Framework má samostatný soubor Security.config, nejsou žádné problémy s kompatibilitou s nastavením zabezpečení. Nicméně pokud vaše aplikace závisí na možnostech další bezpečnostní [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] zahrnuty v rozhraní .NET Framework verze 1.1 nebo novější, nebude možné ho distribuovat do systému verze 1.0.  
  
## <a name="sqlcommand-execution"></a>Provádění SqlCommand  
 Od verze rozhraní .NET Framework verze 1.1, způsob, který <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> provede příkazy na data byla změněna zdroje.  
  
 V rozhraní .NET Framework verze 1.0 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> spuštění všech příkazů v kontextu **sp_executesql** uložené procedury. V důsledku toho příkazy, které mají vliv na stav připojení (například SET NOCOUNT ON), platí jen při spuštění aktuální příkaz. Stav připojení se nezmění pro všechny následné příkazy jsou provedeny v době připojení je otevřeno.  
  
 V rozhraní .NET Framework verze 1.1 nebo novější <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> pouze příkaz spustí v kontextu **sp_executesql** uloženou proceduru, pokud příkaz obsahuje parametry, což zvyšuje výkon. V důsledku toho pokud příkaz, které mají vliv stav připojení je součástí jiné parametry příkazu, změní stav připojení pro všechny následné příkazy jsou provedeny v době připojení je otevřeno.  
  
 Vezměte v úvahu následující dávkové příkazy spouštěné ve volání <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
```  
  
 V rozhraní .NET Framework verze 1.1 nebo novější zůstane NOCOUNT na pro všechny následné příkazy jsou provedeny v době připojení je otevřeno. V rozhraní .NET Framework verze 1.0 je NOCOUNT pouze souvisejících s aktuálním provedení příkazu.  
  
 Tato změna může ovlivnit dopředné a zpětné kompatibility aplikace, pokud závisí na chování <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> buď verzi rozhraní .NET Framework.  
  
 Pro aplikace, které používají novější i starší verze rozhraní .NET Framework můžete napsat kód, abyste měli jistotu, že chování je stejné bez ohledu na verzi, které jsou spuštěné na. Pokud chcete, aby se zajistilo, že příkaz změní stav připojení pro všechny následné příkazy, doporučujeme spustit příkaz pomocí <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>. Pokud chcete, aby se zajistilo, že příkaz neprovede žádné změny připojení pro všechny následné příkazy, doporučujeme, že složku zahrnujete příkazy resetovat stav připojení ve svých rukou. Příklad:  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
SET NOCOUNT OFF;  
```  
  
## <a name="see-also"></a>Viz také:

- [Přehled ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
