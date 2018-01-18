---
title: Podpora SqlClient LocalDB
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
caps.latest.revision: "14"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a3d643ac386aebf51673f937b3f47e73c749b78f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="sqlclient-support-for-localdb"></a>Podpora SqlClient LocalDB
Počínaje [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] kódový název Denali, o odlehčenou verzi [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)], názvem databáze LocalDB, bude k dispozici. Toto téma popisuje, jak se připojit k databázi LocalDB.  
  
## <a name="remarks"></a>Poznámky  
 Další informace o LocalDB, včetně toho, jak LocalDB instalace a konfigurace vaší instanci LocalDB, najdete v části [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] na webu knihy Online.  
  
 Chcete-li shrnout, co můžete dělat s LocalDB:  
  
-   Vytvořte a spusťte LocalDB instancí s sqllocaldb.exe nebo souboru app.config.  
  
-   Pomocí sqlcmd.exe přidání a změna databáze v instanci LocalDB. Například `sqlcmd -S (localdb)\myinst`.  
  
-   Použití `AttachDBFilename` klíčové slovo připojovacího řetězce pro přidání do databáze k vaší instanci LocalDB. Při použití `AttachDBFilename`, pokud není zadán název databáze s `Database` klíčové slovo připojovacího řetězce databáze bude odebrána z instanci LocalDB, až se aplikace zavře.  
  
-   V připojovacím řetězci zadejte instanci LocalDB. Například je název vaší instance `myInstance`, by mělo zahrnovat připojovací řetězec:  
  
    ```  
    server=(localdb)\\myInstance  
    ```  
  
 `User Instance=True`Při připojení k databázi LocalDB není povolen.  
  
 Můžete si stáhnout LocalDB z [Microsoft SQL Server 2012 Feature Pack](http://www.microsoft.com/download/en/details.aspx?id=29065). Pokud budete používat sqlcmd.exe ke změně dat ve vaší instanci LocalDB, budete potřebovat sqlcmd z [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012, která můžete získat také z [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012 Feature Pack.  
  
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
