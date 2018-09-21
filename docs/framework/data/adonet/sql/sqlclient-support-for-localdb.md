---
title: Podpora klienta SqlClient pro LocalDB
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 1ef75def3f3de44b5e23cb1197a4410dcf6b547f
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46492636"
---
# <a name="sqlclient-support-for-localdb"></a>Podpora klienta SqlClient pro LocalDB
SQL Server s kódovým názvem Denali počínaje, bude k dispozici Odlehčená verze systému SQL Server LocalDB, volá. Toto téma popisuje, jak se připojit k databázi LocalDB.  
  
## <a name="remarks"></a>Poznámky  
 Další informace o databázi LocalDB, včetně LocalDB nainstalovat a nakonfigurovat instanci LocalDB, naleznete v tématu knihy Online SQL Server.  
  
 Slouží ke shrnutí, co můžete dělat s LocalDB:  
  
-   Vytvoření a spuštění instance LocalDB s sqllocaldb.exe nebo v souboru app.config.  
  
-   Pro přidání a úpravu databáze v instanci LocalDB pomocí sqlcmd.exe. Například `sqlcmd -S (localdb)\myinst`.  
  
-   Použití `AttachDBFilename` klíčové slovo připojovacího řetězce pro přidání databázi k instanci LocalDB. Při použití `AttachDBFilename`, pokud není zadán název databáze s `Database` klíčové slovo připojovacího řetězce databáze bude nebyla odebrána od LocalDB instance, až se aplikace zavře.  
  
-   V připojovacím řetězci zadejte instanci LocalDB. Například je název vaší instance `myInstance`, připojovací řetězec bude zahrnovat:  
  
    ```  
    server=(localdb)\\myInstance  
    ```  
  
 `User Instance=True` Při připojení k databázi LocalDB není povolen.  
  
 Můžete si stáhnout LocalDB z [Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/en/details.aspx?id=29065). Pokud použijete sqlcmd.exe upravovat data v instanci LocalDB, budete potřebovat sqlcmd ze systému SQL Server 2012, který můžete získat také z SQL Server 2012 Feature Pack.  
  
## <a name="programmatically-create-a-named-instance"></a>Prostřednictvím kódu programu vytvořit pojmenovanou instanci  
 Aplikace můžete vytvořit pojmenovanou instanci a zadejte databázi následujícím způsobem:  
  
-   Zadejte instance LocalDB následujícím způsobem vytvořte v souboru app.config.  Číslo verze instance by měla být stejná jako číslo verze instalace LocalDB.  
  
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
  
-   Zadejte název instance pomocí `server` klíčové slovo připojovacího řetězce.  Název instance zadané v `server` klíčové slovo připojovacího řetězce musí odpovídat názvu zadanému v souboru app.config.  
  
-   Použití `AttachDBFilename` klíčové slovo připojovacího řetězce k určení. Soubor MDF.  
  
## <a name="see-also"></a>Viz také  
 [Funkce SQL Serveru a ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
