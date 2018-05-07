---
title: Podpora SqlClient LocalDB
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 33368ca4b2dc5397087d29e515db6c1094e350bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="sqlclient-support-for-localdb"></a>Podpora SqlClient LocalDB
Od systému SQL Server s kódovým názvem Denali, bude k dispozici Odlehčená verze systému SQL Server, názvem databáze LocalDB. Toto téma popisuje, jak se připojit k databázi LocalDB.  
  
## <a name="remarks"></a>Poznámky  
 Další informace o LocalDB, včetně toho, jak k LocalDB instalaci a konfiguraci vaší instanci LocalDB, najdete v části SQL Server Books Online.  
  
 Chcete-li shrnout, co můžete dělat s LocalDB:  
  
-   Vytvořte a spusťte LocalDB instancí s sqllocaldb.exe nebo souboru app.config.  
  
-   Pomocí sqlcmd.exe přidání a změna databáze v instanci LocalDB. Například `sqlcmd -S (localdb)\myinst`.  
  
-   Použití `AttachDBFilename` klíčové slovo připojovacího řetězce pro přidání do databáze k vaší instanci LocalDB. Při použití `AttachDBFilename`, pokud není zadán název databáze s `Database` klíčové slovo připojovacího řetězce databáze bude odebrána z instanci LocalDB, až se aplikace zavře.  
  
-   V připojovacím řetězci zadejte instanci LocalDB. Například je název vaší instance `myInstance`, by mělo zahrnovat připojovací řetězec:  
  
    ```  
    server=(localdb)\\myInstance  
    ```  
  
 `User Instance=True` Při připojení k databázi LocalDB není povolen.  
  
 Můžete si stáhnout LocalDB z [Microsoft SQL Server 2012 Feature Pack](http://www.microsoft.com/download/en/details.aspx?id=29065). Pokud budete používat sqlcmd.exe ke změně dat ve vaší instanci LocalDB, budete potřebovat sqlcmd z SQL serveru 2012, který můžete získat z SQL Server 2012 Feature Pack.  
  
## <a name="programmatically-create-a-named-instance"></a>Vytváření pojmenovanou instanci prostřednictvím kódu programu  
 Aplikace můžete vytvořit pojmenovanou instanci a zadejte databázi, následujícím způsobem:  
  
-   Zadejte instance LocalDB vytvořit v souboru app.config takto.  Číslo verze instance by měla být stejná jako číslo verze instalace LocalDB.  
  
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
  
-   Zadejte název instance pomocí `server` klíčové slovo připojovacího řetězce.  Název instance zadané v `server` klíčové slovo připojovacího řetězce musí odpovídat názvu zadaná v souboru app.config.  
  
-   Použití `AttachDBFilename` klíčové slovo připojovacího řetězce k určení. Soubor MDF.  
  
## <a name="see-also"></a>Viz také  
 [Funkce SQL Serveru a ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
