---
title: "Spuštění vedle sebe v technologii ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f9ba96d-9f89-4f65-bb2f-6860879f4393
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ade4a0531ae11b3707115956ef0218c0d1c3349c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="side-by-side-execution-in-adonet"></a>Spuštění vedle sebe v technologii ADO.NET
Spuštění vedle sebe v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] je možnost spustit aplikaci na počítač, který má více verzí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] nainstalovaná, výhradně pomocí verze, pro které byl zpracován aplikace. Podrobné informace o konfiguraci spuštění vedle sebe najdete v tématu [spuštění vedle sebe](../../../../docs/framework/deployment/side-by-side-execution.md).  
  
 Aplikace, kompilovat s použitím jednu verzi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] můžete spustit na jinou verzi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Doporučujeme však kompilaci verzi aplikace pro každou nainstalovanou verzi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]a jejich spuštění samostatně. V obou těchto případech byste měli vědět o změnách v [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] mezi verzemi, které můžou ovlivnit dopřednou kompatibilitu nebo zpětné kompatibility vaší aplikace.  
  
## <a name="forward-compatibility-and-backward-compatibility"></a>Dopřednou kompatibilitu a zpětná kompatibilita  
 Dopřednou kompatibilitu znamená, že aplikace mohou být zkompilovány s dřívější verzi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], spustí se však stále úspěšně v novější verzi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]kód napsaný pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.1 není dopředně kompatibilní s novější verzí.  
  
 Zpětná kompatibilita znamená, že aplikace je zkompilovaném pro novější verze [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], ale bude pokračovat v dřívějších verzích [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] beze ztrát funkcí. Samozřejmě to nebude případ funkce byla zavedená v nové verzi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="the-net-framework-data-provider-for-odbc"></a>Zprostředkovatel dat .NET Framework pro rozhraní ODBC  
 Od verze 1.1, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro rozhraní ODBC (<xref:System.Data.Odbc>) je dodávána jako součást [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Zprostředkovatel dat rozhraní ODBC je k dispozici pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.0 vývojáři jako webové stáhnout z [přístup k datům a středisku pro vývojáře úložiště](http://go.microsoft.com/fwlink/?linkid=4173). Obor názvů pro stažené [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro rozhraní ODBC je **Microsoft.Data.Odbc**.  
  
 Pokud máte aplikace vyvinuté pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.0, který používá zprostředkovatele dat rozhraní ODBC připojit ke zdroji dat a chcete spustit tuto aplikaci [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.1 nebo novější, je nutné aktualizovat obor názvů pro rozhraní ODBC Zprostředkovatel dat k **System.Data.Odbc**. Je pak potřeba překompilovat ho pro novější verzi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
 Pokud máte aplikace vyvinuté pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 2.0 nebo novější, který používá zprostředkovatele dat rozhraní ODBC připojit ke zdroji dat a chcete spustit tuto aplikaci [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.0, je nutné stáhnout poskytovatele dat rozhraní ODBC a nainstalovat ho na [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] systému verze 1.0. Pak musíte změnit obor názvů pro zprostředkovatele dat rozhraní ODBC **Microsoft.Data.Odbc**a překompilování aplikace pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.0.  
  
## <a name="the-net-framework-data-provider-for-oracle"></a>Zprostředkovatel dat .NET Framework pro Oracle  
 Od verze 1.1, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro databázi Oracle (<xref:System.Data.OracleClient>) je dodávána jako součást [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Zprostředkovatel dat je k dispozici pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.0 vývojáři jako webové stáhnout z [přístup k datům a středisku pro vývojáře úložiště](http://go.microsoft.com/fwlink/?linkid=4173).  
  
 Pokud máte aplikace vyvinuté pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 2.0 nebo novější, který používá zprostředkovatele dat připojit ke zdroji dat a chcete spustit tuto aplikaci [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.0, musíte stáhnout zprostředkovatele dat a nainstalujte ji na < C4 > [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]  systému verze 1.0.  
  
## <a name="code-access-security"></a>Zabezpečení přístupu kódu  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatelé dat v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.0 (<xref:System.Data.SqlClient>, <xref:System.Data.OleDb>) jsou nutné ke spuštění s oprávnění FullTrust. Žádný pokus o použití [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tisíc zprostředkovatelé dat z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.0 v zóně s méně než příčiny oprávnění FullTrust <xref:System.Security.SecurityException>.  
  
 Ale začínající [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 2.0, všechny [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatelé dat mohou být používány částečně důvěryhodné zóny. Kromě toho nové funkce zabezpečení byl přidán do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatelé dat v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.1. Tato funkce umožňuje omezit jaké připojovací řetězce, je možné v zóně s konkrétní zabezpečení. Můžete také zakázat použití prázdná hesla pro zónu konkrétní zabezpečení. Další informace najdete v tématu [zabezpečení přístupu kódu a ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md).  
  
 Protože každé instalaci [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] má samostatný soubor Security.config, nejsou žádné problémy s kompatibilitou s nastavením zabezpečení. Ale pokud vaše aplikace závisí na možnostech další bezpečnostní [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] součástí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.1 nebo novější, nebude možné jej distribuovat do systému verze 1.0.  
  
## <a name="sqlcommand-execution"></a>Provádění SqlCommand  
 Od verze [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.1, způsob, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> spouští příkazy na data změnila zdroje.  
  
 V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.0, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> provést všechny příkazy v kontextu **sp_executesql** uložené procedury. V důsledku toho příkazy, které ovlivňují stav připojení (například SET NOCOUNT ON), platí pouze pro provádění aktuální příkaz. Stav připojení není upravit pro všechny následné příkazy provádět připojení je otevřeno.  
  
 V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.1 nebo novější, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> pouze příkaz spustí v kontextu **sp_executesql** uložené procedury, pokud příkaz obsahuje parametry, která poskytuje výhody výkonu. Výsledkem je Pokud příkaz, které mají vliv na stav připojení je zahrnutý v jiných parametry příkazu, upravuje stav připojení pro všechny následné příkazy provádět připojení je otevřeno.  
  
 Vezměte v úvahu následující dávku příkazy spouštěné v volání <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.  
  
```  
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
```  
  
 V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.1 nebo novější, NOCOUNT zůstane ON pro všechny následné příkazy provádět připojení je otevřeno. V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.0, NOCOUNT je pouze ON pro aktuální provedení příkazu.  
  
 Tato změna může ovlivnit vpřed a zpětné kompatibility aplikace, pokud závisí na chování <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> pro jednu z verzí nástroje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
 Pro aplikace, které běží na dřívější a novějších verzích [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], můžete napsat kód a ujistěte se, že její chování je stejné bez ohledu na verzi, kterou používáte na. Pokud chcete zajistit, že příkaz změní stav připojení pro všechny následné příkazy, doporučujeme spustit příkaz pomocí <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>. Pokud chcete zajistit, že příkaz neupravuje připojení pro všechny následné příkazy, doporučujeme vám, jestli jste zahrnuli příkazy resetovat stav připojení v příkazu. Příklad:  
  
```  
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
SET NOCOUNT OFF;  
```  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET – přehled](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [Načítání a upravovat Data v technologii ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
