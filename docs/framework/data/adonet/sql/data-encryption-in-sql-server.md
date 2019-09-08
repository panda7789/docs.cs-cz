---
title: Šifrování dat na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 83b992f7-b351-4678-b4b9-f4ffd58134cc
ms.openlocfilehash: 1d185dd121336b62bd66a11bf0cc4253b45ae47e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794257"
---
# <a name="data-encryption-in-sql-server"></a>Šifrování dat na SQL Serveru
SQL Server poskytuje funkce pro šifrování a dešifrování dat pomocí certifikátu, asymetrického klíče nebo symetrického klíče. Spravuje je všechny z interního úložiště certifikátů. Úložiště používá hierarchii šifrování, která zabezpečuje certifikáty a klíče na jedné úrovni s vrstvou nad ní v hierarchii. Tato oblast funkcí SQL Server se nazývá tajné úložiště.  
  
 Nejrychlejší režim šifrování podporovaný funkcemi šifrování je šifrování symetrického klíče. Tento režim je vhodný pro zpracování velkých objemů dat. Symetrické klíče mohou být zašifrovány certifikáty, hesly nebo jinými symetrickými klíči.  
  
## <a name="keys-and-algorithms"></a>Klíče a algoritmy  
 SQL Server podporuje několik algoritmů šifrování symetrického klíče, včetně DES, Triple DES, RC2, RC4, 128 bitů RC4, DESX, 128 AES, 192-bit AES 256 a 16bitového AES. Algoritmy jsou implementovány pomocí rozhraní API pro šifrování systému Windows.  
  
 V rámci připojení k databázi SQL Server může spravovat více otevřených symetrických klíčů. Z úložiště se načte otevřený klíč, který je k dispozici pro dešifrování dat. Pokud je část dat dešifrována, není nutné určit symetrický klíč, který se má použít. Každá zašifrovaná hodnota obsahuje identifikátor klíče (GUID klíče) klíče použitého k jeho zašifrování. Modul odpovídá šifrovanému datovému proudu na otevřený symetrický klíč, pokud byl správný klíč dešifrován a je otevřen. Pomocí tohoto klíče se pak provede dešifrování a vrátí data. Pokud není správný klíč otevřený, vrátí se hodnota NULL.  
  
 Příklad, který ukazuje, jak pracovat s šifrovanými daty v databázi, najdete v tématu [šifrování sloupce dat](/sql/relational-databases/security/encryption/encrypt-a-column-of-data).
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace o šifrování dat najdete v následujících zdrojích informací.  
  
|Resource|Popis|  
|-|-|  
|[SQL Server šifrování](/sql/relational-databases/security/encryption/sql-server-encryption)|V této části najdete přehled šifrování v SQL Server. Toto téma obsahuje odkazy na další články.|  
|[Hierarchie šifrování](/sql/relational-databases/security/encryption/encryption-hierarchy)|V této části najdete přehled šifrování v SQL Server. Toto téma obsahuje odkazy na další články.|  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../securing-ado-net-applications.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](application-security-scenarios-in-sql-server.md)
- [Ověřování v SQL Serveru](authentication-in-sql-server.md)
- [Serverové a databázové role na SQL Serveru](server-and-database-roles-in-sql-server.md)
- [Vlastnictví a oddělení uživatelských schémat na SQL Serveru](ownership-and-user-schema-separation-in-sql-server.md)
- [Autorizace a oprávnění na SQL Serveru](authorization-and-permissions-in-sql-server.md)
- [Přehled ADO.NET](../ado-net-overview.md)
