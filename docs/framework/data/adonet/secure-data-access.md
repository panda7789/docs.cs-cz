---
title: Zabezpečený přístup k datům
ms.date: 03/30/2017
ms.assetid: 473ebd69-21a3-4627-b95e-4e04d035c56f
ms.openlocfilehash: c08f41be67f5d87635021e86ba5a5b33af9304cd
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735276"
---
# <a name="secure-data-access"></a>Zabezpečený přístup k datům
Chcete-li napsat zabezpečený ADO.NET kód, musíte pochopit mechanismy zabezpečení, které jsou k dispozici v podkladovém úložišti dat nebo databázi. Také je nutné vzít v úvahu důsledky zabezpečení dalších funkcí nebo součástí, které vaše aplikace může obsahovat.  
  
## <a name="authentication-authorization-and-permissions"></a>Ověřování, autorizace a oprávnění  
 Při připojování k Microsoft SQL Server můžete použít ověřování systému Windows (označované také jako integrované zabezpečení), které místo předání ID uživatele a hesla používá identitu aktuálního aktivního uživatele systému Windows. Použití ověřování systému Windows se důrazně doporučuje, protože přihlašovací údaje uživatele nejsou zveřejněné v připojovacím řetězci. Pokud se k připojení k SQL Server nemůžete použít ověřování systému Windows, zvažte vytvoření připojovacích řetězců v době běhu pomocí <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  
  
 Přihlašovací údaje, které se používají pro ověřování, se musí zpracovat odlišně v závislosti na typu aplikace. Například v aplikaci model Windows Forms se uživateli zobrazí výzva k zadání ověřovacích informací nebo můžete použít přihlašovací údaje systému Windows uživatele. Nicméně webová aplikace často přistupuje k datům pomocí přihlašovacích údajů, které zadala samotná aplikace, a ne podle uživatele.  
  
 Po ověření uživatelů rozsah jejich akcí závisí na oprávněních, která jim byla udělena. Vždy postupujte podle principu nejnižší oprávnění a udělte pouze oprávnění, která jsou nezbytně nutná.  
  
 Další informace najdete v následujících zdrojích informací.  
  
|Partner|Popis|  
|--------------|-----------------|  
|[Ochrana informací o připojení](protecting-connection-information.md)|Popisuje osvědčené postupy a techniky zabezpečení pro ochranu informací o připojení, jako je například použití chráněné konfigurace k šifrování připojovacích řetězců.|  
|[Doporučení pro strategie přístupu k datům](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))|Poskytuje doporučení pro přístup k datům a provádění databázových operací.|  
|[Tvůrci připojovacích řetězců](connection-string-builders.md)|Popisuje, jak vytvořit připojovací řetězce z uživatelského vstupu za běhu.|  
|[Přehled zabezpečení SQL Serveru](./sql/overview-of-sql-server-security.md)|Popisuje architekturu zabezpečení SQL Server.|  
  
## <a name="parameterized-commands-and-sql-injection"></a>Parametrizované příkazy a injektáže SQL  
 Použití parametrizovaných příkazů pomáhá chránit před útoky prostřednictvím injektáže SQL, kdy útočník "Vloží příkaz do příkazu jazyka SQL, který ohrozí zabezpečení na serveru. Parametrizované příkazy Guard proti útoku prostřednictvím injektáže SQL zajišťuje, že hodnoty přijaté z externího zdroje jsou předávány pouze jako hodnoty a nikoli jako součást příkazu jazyka Transact-SQL. V důsledku toho příkazy jazyka Transact-SQL vložené do hodnoty nebudou provedeny ve zdroji dat. Místo toho jsou vyhodnocovány výhradně jako hodnota parametru. Kromě výhod zabezpečení poskytují parametrizované příkazy pohodlný způsob uspořádání hodnot předaných pomocí příkazu jazyka Transact-SQL nebo uložené procedury.  
  
 Další informace o použití parametrizovaných příkazů naleznete v následujících zdrojích informací.  
  
|Partner|Popis|  
|--------------|-----------------|  
|[Parametry adaptéru dat](dataadapter-parameters.md)|Popisuje, jak použít parametry s `DataAdapter`.|  
|[Úpravy dat pomocí uložených procedur](modifying-data-with-stored-procedures.md)|Popisuje, jak zadat parametry a získat návratovou hodnotu.|  
|[Správa oprávnění pomocí uložených procedur na SQL Serveru](./sql/managing-permissions-with-stored-procedures-in-sql-server.md)|Popisuje způsob použití SQL Server uložených procedur k zapouzdření přístupu k datům.|  
  
## <a name="script-exploits"></a>Zneužití skriptů  
 Zneužití skriptu je další forma injektáže, která používá škodlivé znaky vložené do webové stránky. Prohlížeč neověřuje vložené znaky a zpracuje je jako součást stránky.  
  
 Další informace najdete v následujících zdrojích informací.  
  
|Partner|Popis|  
|--------------|-----------------|  
|[Přehled zneužití skriptů](https://docs.microsoft.com/previous-versions/aspnet/w1sw53ds(v=vs.100))|Popisuje, jak chránit před zneužitím skriptování a příkazů SQL.|  
  
## <a name="probing-attacks"></a>Útoky probingem  
 Útočníci často používají informace z výjimky, jako je název serveru, databáze nebo tabulky, pro připojení útoku do systému. Vzhledem k tomu, že výjimky mohou obsahovat konkrétní informace o vaší aplikaci nebo zdroji dat, můžete přispět k lepší ochraně vašich aplikací a zdrojů dat pouze tím, že klientovi vystavíte podstatné informace.  
  
 Další informace najdete v následujících zdrojích informací.  
  
|Partner|Popis|  
|--------------|-----------------|  
|[Zpracování a vyvolávání výjimek v rozhraní .NET](../../../standard/exceptions/index.md)|Popisuje základní formy zpracování strukturované výjimky try/catch/finally.|  
|[Doporučené postupy pro výjimky](../../../standard/exceptions/best-practices-for-exceptions.md)|Popisuje osvědčené postupy pro zpracování výjimek.|  
  
## <a name="protecting-microsoft-access-and-excel-data-sources"></a>Ochrana datových zdrojů aplikace Microsoft Access a Excelu  
 Microsoft Access a Microsoft Excel můžou fungovat jako úložiště dat pro ADO.NET aplikaci, pokud jsou požadavky na zabezpečení minimální nebo neexistující. Jejich funkce zabezpečení jsou platné pro Deterrence, ale neměly by se spoléhat na to, že by neinformovali uživatele o více než Zabraňte meddling. Fyzické datové soubory pro přístup a Excel existují v systému souborů a musí být přístupné pro všechny uživatele. Díky tomu je to zranitelné vůči útokům, které by mohly vést ke krádeži nebo ztrátě dat, protože soubory je možné snadno zkopírovat nebo změnit. Je-li vyžadováno robustní zabezpečení, použijte SQL Server nebo jinou databázi založenou na serveru, kde nelze přečíst fyzické datové soubory ze systému souborů.  
  
 Další informace o ochraně přístupu a dat aplikace Excel naleznete v následujících zdrojích informací.  
  
|Partner|Popis|  
|--------------|-----------------|  
|[Požadavky na zabezpečení a pokyny pro přístup 2007](https://go.microsoft.com/fwlink/?LinkId=98354)|Popisuje techniky zabezpečení pro přístup 2007 takovým šifrováním souborů, správě hesel, převádění databází do nových formátů ACCDB a ACCDE a používání dalších možností zabezpečení.|  
|[Princip role souborů s informacemi pracovní skupiny v zabezpečení přístupu](https://support.microsoft.com/kb/305542)|Vysvětluje roli a vztah souboru s informacemi pracovní skupiny v zabezpečení Access 2003.|  
|[Nejčastější dotazy týkající se zabezpečení Microsoft Accessu pro verze Microsoft Access 2,0 až 2000](https://go.microsoft.com/fwlink/?LinkId=47698)|Verze služby Microsoft Access pro zabezpečení služby ke stažení – Nejčastější dotazy.|  
## <a name="enterprise-services"></a>Podnikové služby  
 COM+ obsahuje svůj vlastní model zabezpečení, který spoléhá na účty systému Windows NT a proces/zosobnění vláken. Obor názvů <xref:System.EnterpriseServices> poskytuje obálky, které umožňují aplikacím .NET integraci spravovaného kódu se službami zabezpečení modelu COM+ prostřednictvím <xref:System.EnterpriseServices.ServicedComponent> třídy.  
  
 Další informace najdete v následujícím prostředku.  
  
|Partner|Popis|  
|--------------|-----------------|  
|[Zabezpečení na základě rolí](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/s6y8k15h(v=vs.71))|Popisuje, jak integrovat spravovaný kód se službami zabezpečení služby COM+.|  
  
## <a name="interoperating-with-unmanaged-code"></a>Spolupráce s nespravovaným kódem  
 .NET Framework poskytuje interakci s nespravovaným kódem, včetně komponent modelu COM, služeb modelu COM+, externích knihoven typů a mnoha služeb operačního systému. Práce s nespravovaným kódem zahrnuje mimo hranice zabezpečení pro spravovaný kód. Jak váš kód, tak i jakýkoli kód, který ho volá, musí mít oprávnění nespravovaného kódu (<xref:System.Security.Permissions.SecurityPermission> se zadaným příznakem <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>). Nespravovaný kód může do aplikace zavádět nezamýšlená ohrožení zabezpečení. Proto byste se měli vyhnout spolupráci s nespravovaným kódem, pokud to není nezbytně nutné.  
  
 Další informace najdete v následujících zdrojích informací.  
  
|Partner|Popis|  
|--------------|-----------------|  
|[Spolupráce s nespravovaným kódem](../../interop/index.md)|Obsahuje témata popisující, jak vystavit komponenty modelu COM .NET Framework a jak zpřístupnit komponenty .NET Framework modelu COM.|
|[Pokročilá interoperabilita modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))|Obsahuje Pokročilá témata, jako jsou primární spolupracující sestavení, dělení na vlákna a vlastní zařazování.|

## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](securing-ado-net-applications.md)
- [SQL Server – zabezpečení](./sql/sql-server-security.md)
- [Doporučení pro strategie přístupu k datům](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))
- [Ochrana informací o připojení](protecting-connection-information.md)
- [Tvůrci připojovacích řetězců](connection-string-builders.md)
- [Přehled ADO.NET](ado-net-overview.md)
