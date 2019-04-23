---
title: Souběžné spouštění v ADO.NET
ms.date: 03/30/2017
ms.assetid: 9f9ba96d-9f89-4f65-bb2f-6860879f4393
ms.openlocfilehash: a8747d749ed7e751ba577a2cd29c2048065f2645
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136757"
---
# <a name="side-by-side-execution-in-adonet"></a>Souběžné spouštění v ADO.NET
Spuštění vedle sebe v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] je schopnost spouští aplikaci, která v počítači, který má více verzí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] nainstalovat, výhradně pomocí verze, pro kterou byla aplikace zkompilována. Podrobné informace o konfiguraci spuštění vedle sebe, naleznete v tématu [spuštění vedle sebe](../../../../docs/framework/deployment/side-by-side-execution.md).  
  
 Aplikace kompilované pomocí jedné verze [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] můžete spustit na jinou verzi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Doporučujeme však, že při kompilaci verze aplikace pro každou nainstalovanou verzi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]a spusťte je samostatně. V obou scénářích byste měli vědět o změnách v [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] mezi verzemi, které mohou ovlivnit kompatibilitu nebo zpětné kompatibility aplikace.  
  
## <a name="forward-compatibility-and-backward-compatibility"></a>Dopředná kompatibilita a zpětné kompatibility  
 Dopředná kompatibilita znamená, že aplikace může být zkompilován s starší verze [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], ale bude stále spuštěn úspěšně na novější verzi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] kód napsaný pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.1 není dopředně kompatibilní s novějšími verzemi.  
  
 Zpětná kompatibilita znamená, že aplikace je zkompilován novější verzi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], ale bude pokračovat ve starších verzích [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] bez ztráty funkčnosti. Samozřejmě to nebude v případě funkce v nové verzi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="the-net-framework-data-provider-for-odbc"></a>Zprostředkovatel dat .NET Framework pro ODBC  
 Od verze 1.1, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro ODBC (<xref:System.Data.Odbc>) je zahrnutý jako součást [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Zprostředkovatel dat rozhraní ODBC je k dispozici [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] stahování verze 1.0 vývojáři jako Web [středisko pro vývojáře úložiště a přístup k datům](https://go.microsoft.com/fwlink/?linkid=4173). Obor názvů pro na stažený [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] je zprostředkovatel dat pro ODBC **Microsoft.Data.Odbc**.  
  
 Pokud máte aplikace vyvinutá pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.0, který používá poskytovatele dat rozhraní ODBC pro připojení ke zdroji dat a chcete spustit tuto aplikaci na [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.1 nebo novější, je nutné aktualizovat obor názvů pro rozhraní ODBC Zprostředkovatel dat **System.Data.Odbc**. Je pak nutné ji znovu zkompilovat pro novější verzi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
 Pokud máte aplikace vyvinutá pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 2.0 nebo novější, který používá poskytovatele dat rozhraní ODBC pro připojení ke zdroji dat a chcete tuto aplikaci spouštět [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.0, je nutné stáhnout poskytovatele dat rozhraní ODBC a nainstalovat na [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] systému verze 1.0. Pak musíte změnit obor názvů pro zprostředkovatele dat rozhraní ODBC do **Microsoft.Data.Odbc**a znovu zkompilovat aplikaci pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.0.  
  
## <a name="the-net-framework-data-provider-for-oracle"></a>Zprostředkovatel dat .NET Framework pro Oracle  
 Počínaje verzí 1.1, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro Oracle (<xref:System.Data.OracleClient>) je zahrnutý jako součást [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Poskytovatel dat je k dispozici [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] stahování verze 1.0 vývojáři jako Web [středisko pro vývojáře úložiště a přístup k datům](https://go.microsoft.com/fwlink/?linkid=4173).  
  
 Pokud máte aplikace vyvinutá pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 2.0 nebo novější, který používá poskytovatele dat pro připojení ke zdroji dat a chcete tuto aplikaci spouštět [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.0, musíte si stáhnout poskytovatele dat a nainstalujte ho na < C4 > [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]  systému verze 1.0.  
  
## <a name="code-access-security"></a>Zabezpečení přístupu kódu  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatelé dat v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.0 (<xref:System.Data.SqlClient>, <xref:System.Data.OleDb>) jsou potřeba ke spouštění pomocí oprávnění FullTrust. Žádný pokus o použití [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat k z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.0 v zóně s méně než způsobí, že oprávnění FullTrust <xref:System.Security.SecurityException>.  
  
 Nicméně od verze [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 2.0, všechny [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatelů dat je možné v částečně důvěryhodné zóny. Kromě toho byla přidána nová funkce zabezpečení do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatelé dat v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.1. Tato funkce umožňuje omezit jaké připojovací řetězce lze použít v zóně s konkrétním zabezpečení. Můžete také zakázat použití prázdného hesla pro zabezpečení pro konkrétní zónu. Další informace najdete v tématu [zabezpečení přístupu kódu a ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md).  
  
 Protože každou instalaci aplikace [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] má samostatný soubor Security.config, nejsou žádné problémy s kompatibilitou s nastavením zabezpečení. Nicméně pokud vaše aplikace závisí na možnostech další bezpečnostní [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] součástí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.1 nebo novější, nebude možné distribuovat do systému verze 1.0.  
  
## <a name="sqlcommand-execution"></a>Provádění SqlCommand  
 Počínaje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.1, způsob, který <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> provede příkazy na data byla změněna zdroje.  
  
 V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.0, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> spuštění všech příkazů v kontextu **sp_executesql** uložené procedury. V důsledku toho příkazy, které mají vliv na stav připojení (například SET NOCOUNT ON), platí jen při spuštění aktuální příkaz. Stav připojení se nezmění pro všechny následné příkazy jsou provedeny v době připojení je otevřeno.  
  
 V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.1 nebo novější, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> pouze příkaz spustí v kontextu **sp_executesql** uloženou proceduru, pokud příkaz obsahuje parametry, což zvyšuje výkon. V důsledku toho pokud příkaz, které mají vliv stav připojení je součástí jiné parametry příkazu, změní stav připojení pro všechny následné příkazy jsou provedeny v době připojení je otevřeno.  
  
 Vezměte v úvahu následující dávkové příkazy spouštěné ve volání <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
```  
  
 V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.1 nebo novější, NOCOUNT zůstane na pro všechny následné příkazy jsou provedeny v době připojení je otevřeno. V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.0, NOCOUNT je pouze na aktuální spustitelný příkaz.  
  
 Tato změna může ovlivnit dopředné a zpětné kompatibility aplikace, pokud závisí na chování <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> pro kteroukoliv z verzí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
 Pro aplikace, které používají novější i starší verze [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], můžete napsat kód, abyste měli jistotu, že chování je stejné bez ohledu na verzi, kterou používáte na. Pokud chcete, aby se zajistilo, že příkaz změní stav připojení pro všechny následné příkazy, doporučujeme spustit příkaz pomocí <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>. Pokud chcete, aby se zajistilo, že příkaz neprovede žádné změny připojení pro všechny následné příkazy, doporučujeme, že složku zahrnujete příkazy resetovat stav připojení ve svých rukou. Příklad:  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
SET NOCOUNT OFF;  
```  
  
## <a name="see-also"></a>Viz také:

- [Přehled ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
