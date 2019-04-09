---
title: Šifrování dat na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 83b992f7-b351-4678-b4b9-f4ffd58134cc
ms.openlocfilehash: 1acb720b8a4f8beb27bb1a5236efdb6f2bb44383
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102164"
---
# <a name="data-encryption-in-sql-server"></a>Šifrování dat na SQL Serveru
SQL Server poskytuje funkce pro šifrování a dešifrování dat pomocí certifikátu, asymetrického klíče nebo symetrický klíč. Spravuje všechny z nich najdete v úložišti vnitřní certifikát. Úložiště používá k šifrování hierarchii, která chrání vaše certifikáty a klíče na jedné úrovni vrstvy nad ním v hierarchii. Tato oblast funkce systému SQL Server se nazývá tajný klíč úložiště.  
  
 O nejrychlejší režim šifrování functions podporuje šifrování je šifrování se symetrickým klíčem. Tento režim je vhodný pro zpracování velkých objemů dat. Symetrické klíče mohou být šifrována pomocí certifikátů, hesla nebo dalších symetrické klíče.  
  
## <a name="keys-and-algorithms"></a>Klíče a algoritmy  
 SQL Server podporuje několik algoritmů šifrování se symetrickým klíčem, včetně DES, Triple DES, RC2, RC4, 128-bit RC4, DESX, 128bitový standard AES, 192 bitů AES a AES 256 bitů. Algoritmy jsou implementovány pomocí rozhraní Crypto API pro Windows.  
  
 V rámci oboru připojení k databázi systému SQL Server můžete udržovat více otevřít symetrické klíče. Otevřít klíč je načten z úložiště a je k dispozici pro dešifrování dat. Když se dešifrují část dat, není potřeba specifikovat symetrického klíče. Každý šifrovaná hodnota obsahuje klíč identifikátor (klíč GUID) klíč používaný k šifrování. Modul odpovídá datového proudu bajtů šifrovaného otevřít symetrický klíč, pokud správný klíč se dešifruje a je otevřen. Tento klíč je pak používá k dešifrování a vrátit data. Pokud se správným klíčem není otevřen, je vrácena hodnota NULL.  
  
 Příklad, který ukazuje, jak pracovat s šifrovaných dat v databázi, naleznete v tématu [šifrování sloupce dat](/sql/relational-databases/security/encryption/encrypt-a-column-of-data).
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace o šifrování dat najdete v následující prostředky.  
  
|Prostředek|Popis|  
|-|-|  
|[Šifrování SQL serveru](/sql/relational-databases/security/encryption/sql-server-encryption)|Přehled šifrování v systému SQL Server. Toto téma obsahuje odkazy na další články.|  
|[Šifrování hierarchie](/sql/relational-databases/security/encryption/encryption-hierarchy)|Přehled šifrování v systému SQL Server. Toto téma obsahuje odkazy na další články.|  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Ověřování v SQL Serveru](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)
- [Serverové a databázové role na SQL Serveru](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)
- [Vlastnictví a oddělení uživatelských schémat na SQL Serveru](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)
- [Autorizace a oprávnění na SQL Serveru](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
