---
title: "Zabezpečení přístupu k datům"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 473ebd69-21a3-4627-b95e-4e04d035c56f
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c26854af585fc026ba9abee77bc3b8a95bcaba79
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="secure-data-access"></a>Zabezpečení přístupu k datům
Psaní kódu zabezpečené ADO.NET, musíte pochopit mechanismy zabezpečení, k dispozici v příslušné úložiště dat, nebo databáze. Také je potřeba zvážit důsledky zabezpečení jiných funkcích nebo součásti, které vaše aplikace může obsahovat.  
  
## <a name="authentication-authorization-and-permissions"></a>Ověřování, autorizaci a oprávnění  
 Při připojování k serveru Microsoft SQL Server, můžete použít ověřování systému Windows, označované také jako integrované zabezpečení, který se použije identita aktuálního aktivní uživatele systému Windows, nikoli předávání ID uživatele a heslo. Pomocí ověřování systému Windows je důrazně doporučujeme, protože přihlašovací údaje uživatele se nezobrazí v připojovacím řetězci. Pokud ověřování systému Windows nelze použít pro připojení k systému SQL Server, pak zvažte vytvoření připojovací řetězce za běhu pomocí <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  
  
 Přihlašovací údaje používané pro ověřování je nutné zacházet různě v závislosti na typu aplikace. Například v aplikaci Windows Forms uživatele můžete být vyzváni k zadání informace o ověřování nebo pověření uživatele systému Windows lze použít. Ale webové aplikace často přistupuje k dat pomocí pověření zadaná ve vlastní aplikace, a nikoli uživatele.  
  
 Jakmile po ověření uživatele, rozsah jejich akce závisí na kterým bylo uděleno oprávnění k nim. Vždy použijte Princip nejnižších nutných oprávnění a udělit pouze oprávnění, která jsou nezbytně nutné.  
  
 Další informace najdete v následujících zdrojích informací.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Ochrana informací o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md)|Popisuje osvědčené postupy zabezpečení a techniky pro ochranu informace o připojení, například pomocí chráněné konfigurace k zašifrování připojovací řetězce.|  
|[Doporučení pro strategií přístupu dat](http://msdn.microsoft.com/library/72411f32-d12a-4de8-b961-e54fca7faaf5)|Poskytuje doporučení pro přístup k datům a provádění databázových operací.|  
|[Tvůrci připojovacích řetězců](../../../../docs/framework/data/adonet/connection-string-builders.md)|Popisuje, jak vytvořit připojovací řetězce z vstup uživatele v době běhu.|  
|[Přehled zabezpečení SQL Serveru](../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)|Popisuje architekturu zabezpečení systému SQL Server.|  
  
## <a name="parameterized-commands-and-sql-injection"></a>Parametrizované příkazy a Injektáž SQL  
 Parametrizované příkazy pomáhá chránit před útoky prostřednictvím injektáže SQL, ve kterých útočník "vloží" příkaz do příkazu SQL tohoto ohrožení zabezpečení na serveru. Parametrizované příkazy chránit proti útok prostřednictvím injektáže SQL tím zajistí, že jsou hodnoty přijaté z externího zdroje předány jako pouze hodnoty a není součástí příkazu Transact-SQL. V důsledku toho nejsou ve zdroji dat spustit příkazy jazyka Transact-SQL vložit do hodnoty. Místo toho se vyhodnocují pouze jako hodnotu parametru. Kromě výhody zabezpečení parametrizované příkazy poskytují vhodnou metodu pro uspořádání hodnoty předané pomocí příkazu Transact-SQL nebo uloženou proceduru.  
  
 Další informace o používání parametrizované příkazy najdete v následujících materiálech.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Parametry adaptéru dat](../../../../docs/framework/data/adonet/dataadapter-parameters.md)|Popisuje, jak používat parametry s `DataAdapter`.|  
|[Úpravy dat pomocí uložených procedur](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)|Popisuje, jak určit parametry a získat návratovou hodnotu.|  
|[Správa oprávnění pomocí uložených procedur na SQL Serveru](../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)|Popisuje, jak zapouzdřit přístup k datům pomocí uložené procedury SQL serveru.|  
  
## <a name="script-exploits"></a>Zneužití skriptu  
 Zneužití skriptu je jinou formu vkládání používající škodlivý znaků, které jsou vloženy do webové stránky. V prohlížeči neověřuje vložené znaky a je v rámci stránky zpracuje.  
  
 Další informace najdete v následujících zdrojích informací.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Přehled zneužití skriptu](http://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07)|Popisuje, jak chránit proti skriptování a příkaz jazyka SQL zneužití.|  
  
## <a name="probing-attacks"></a>Zkušební fáze útoků  
 Útočníci často používají informace z výjimku, například název serveru, databáze nebo tabulka, připojit útok na systém. Protože výjimky mohou obsahovat konkrétní informace o vaší aplikace nebo zdroj dat, můžete pomoct chránit vaše aplikace a zdroj dat lépe chráněné pomocí pouze vystavení základní informace o klientovi.  
  
 Další informace najdete v následujících zdrojích informací.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Základy zpracování výjimek](../../../../docs/standard/exceptions/exception-handling-fundamentals.md)|Popisuje základní formy try/catch/finally – strukturované zpracování výjimek.|  
|[Doporučené postupy pro výjimky](../../../../docs/standard/exceptions/best-practices-for-exceptions.md)|Popisuje osvědčené postupy pro zpracování výjimek.|  
  
## <a name="protecting-microsoft-access-and-excel-data-sources"></a>Ochrana Microsoft Access a zdroje dat v aplikaci Excel  
 Aplikace Microsoft Access a aplikaci Microsoft Excel může fungovat jako úložiště dat pro aplikaci ADO.NET při požadavky na zabezpečení jsou minimální, nebo neexistuje. Platí pro dětí jejich funkce zabezpečení, ale nemělo by být spoléhat na více než bránit meddling uninformed uživatelé. Fyzické datové soubory pro přístup a Excel existovat v systému souborů a musí být přístupné pro všechny uživatele. Díky tomu je bude zranitelný vůči útokům, které může vést ke ztrátě odcizení nebo data, protože soubory můžete snadno zkopírovat ani změnit. Pokud je požadována robustní zabezpečení, použijte SQL Server nebo jiné databáze na serveru kde nejsou soubory fyzické čitelný ze systému souborů.  
  
 Další informace o ochraně dat přístup a Excel najdete v následujících zdrojích informací.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Důležité informace a pokyny pro Access 2007](http://go.microsoft.com/fwlink/?LinkId=98354)|Popisuje postupy zabezpečení pro Access 2007 takové šifrování souborů, Správa hesel, převod databáze do nového ACCDB a ACCDE formátů a pomocí jiné možnosti zabezpečení.|  
|[Pomáhá chránit databázi aplikace Access s zabezpečení individuální (MDB)](http://go.microsoft.com/fwlink/?LinkId=47697)|Platí pro přístup k 2003. Poskytuje pokyny pro implementaci zabezpečení na úrovni uživatele k ochraně dat v aplikaci Access 2003.|  
|[Principy Role informačními soubory v zabezpečení přístupu](http://support.microsoft.com/kb/305542)|Vysvětluje roli a vztah informačního souboru v zabezpečení 2003 přístup.|  
|[Často výzva otázky zabezpečení pro Microsoft Access verze 2.0 až 2000](http://go.microsoft.com/fwlink/?LinkId=47698)|Verze Microsoft Access Security – nejčastější dotazy ke stažení.|  
|[Řešení potíží s zabezpečení a ochrana](http://go.microsoft.com/fwlink/?LinkId=47703)|Uvede řešení běžných potíží se zabezpečením v aplikaci Excel 2003.|  
  
## <a name="enterprise-services"></a>Enterprise Services  
 Modelu COM + obsahuje vlastní model zabezpečení, které jsou závislé na účty systému Windows NT a proces/vlákno zosobnění. <xref:System.EnterpriseServices> Obor názvů obsahuje obálky, které umožňují aplikace .NET pro integraci zabezpečení služby COM + prostřednictvím spravovaného kódu <xref:System.EnterpriseServices.ServicedComponent> třídy.  
  
 Další informace najdete v následujícím zdroji.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Na základě rolí zabezpečení modelu COM + a rozhraní .NET Framework](http://msdn.microsoft.com/library/02ab22ef-e5e2-4d29-b33a-6e03d94c4981)|Popisuje postup pro integraci zabezpečení služby COM + spravovaného kódu.|  
  
## <a name="interoperating-with-unmanaged-code"></a>Spolupráce s nespravovaným kódem  
 Rozhraní .NET Framework poskytuje pro interakci s nespravovaným kódem, včetně COM komponenty modelu COM + služby, knihovny externích typů a mnoho služeb operačního systému. Práce s nespravovaným kódem zahrnuje předávány mimo hraniční zabezpečení pro spravovaný kód. Váš kód a kód, který volá ho musí mít nespravovaného kódu oprávnění (<xref:System.Security.Permissions.SecurityPermission> s <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> zadaného příznaku). Nespravovaný kód můžou vést k ohrožení zabezpečení nezamýšleným do vaší aplikace. Proto byste neměli spolupráce s nespravovaným kódem, pokud to není nezbytně nutné.  
  
 Další informace najdete v následujících zdrojích informací.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Spolupráce s nespravovaným kódem](../../../../docs/framework/interop/index.md)|Obsahuje témata popisující, jak k vystavení součástí COM v rozhraní .NET Framework a postup vystavení součástí .NET Framework do modelu COM.|  
|[Interoperabilita modelů COM Upřesnit](http://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb)|Obsahuje Pokročilá témata například primární spolupracující sestavení, vlákna a vlastní zařazování.|  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server – zabezpečení](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [Doporučení pro strategií přístupu dat](http://msdn.microsoft.com/library/72411f32-d12a-4de8-b961-e54fca7faaf5)  
 [Ochrana informací o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [Tvůrci připojovacích řetězců](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
