---
title: Podpora klienta SqlClient pro LocalDB
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: d02524cd5901adeca7bc36d6fd13c7abdc46c69b
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894400"
---
# <a name="sqlclient-support-for-localdb"></a>Podpora klienta SqlClient pro LocalDB
Počínaje SQL Server název kódu Denali bude k dispozici zjednodušená verze SQL Server s názvem LocalDB. Toto téma popisuje, jak se připojit k databázi LocalDB.  
  
## <a name="remarks"></a>Poznámky  
 Další informace o LocalDB, včetně toho, jak nainstalovat LocalDB a nakonfigurovat instanci LocalDB, najdete v tématu SQL Server Books Online.  
  
 Sumarizace toho, co můžete s LocalDB provádět:  
  
- Vytvořte a spusťte instance LocalDB pomocí sqllocaldb. exe nebo souboru App. config.  
  
- K přidávání a úpravám databází v instanci LocalDB použijte Sqlcmd. exe. Například, `sqlcmd -S (localdb)\myinst`.  
  
- K přidání databáze do instance LocalDB použijte klíčové slovo připojovacíhořetězce.`AttachDBFilename` Pokud při `AttachDBFilename`použití nezadáte název databáze `Database` pomocí klíčového slova připojovacího řetězce, databáze bude při zavření aplikace odebrána z instance LocalDB.  
  
- V připojovacím řetězci zadejte instanci LocalDB. Například název instance je `myInstance`, připojovací řetězec by měl obsahovat:  
  
    `server=(localdb)\\myInstance`  
  
 `User Instance=True`není povolený při připojování k databázi LocalDB.  
  
 LocalDB můžete stáhnout z [balíčku funkcí Microsoft SQL Server 2012](https://www.microsoft.com/download/en/details.aspx?id=29065). Pokud budete pomocí nástroje Sqlcmd. exe upravovat data v instanci LocalDB, budete potřebovat Sqlcmd z SQL Server 2012, který můžete také získat ze sady SQL Server 2012 Feature Pack.  
  
## <a name="programmatically-create-a-named-instance"></a>Programové vytvoření pojmenované instance  
 Aplikace může vytvořit pojmenovanou instanci a zadat databázi následujícím způsobem:  
  
- Následujícím způsobem zadejte instance LocalDB, které se mají vytvořit v souboru App. config.  Číslo verze instance by mělo být stejné jako číslo verze vaší instalace LocalDB.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <configSections>  
        <section  
        name="system.data.localdb"  
        type="System.Data.LocalDBConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>  
      </configSections>  
      <system.data.localdb>  
        <localdbinstances>  
          <add name="myInstance" version="11.0" />  
        </localdbinstances>  
      </system.data.localdb>  
    </configuration>  
    ```  
  
- Zadejte název instance pomocí `server` klíčového slova připojovacího řetězce.  Název instance zadaný v `server` klíčovém slově připojovacího řetězce se musí shodovat s názvem zadaným v souboru App. config.  
  
- Pomocí klíčového slova připojovacího řetězce určete. `AttachDBFilename` Soubor MDF.  
  
## <a name="see-also"></a>Viz také:

- [Funkce SQL Serveru a ADO.NET](sql-server-features-and-adonet.md)
- [Přehled ADO.NET](../ado-net-overview.md)
