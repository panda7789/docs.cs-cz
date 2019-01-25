---
title: Uživatelem definované typy CLR
ms.date: 03/30/2017
ms.assetid: 9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2
ms.openlocfilehash: b946a87e49d8bf496fb215eb95f9db9cb453c13c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681024"
---
# <a name="clr-user-defined-types"></a>Uživatelem definované typy CLR
Microsoft SQL Server poskytuje podporu pro uživatelem definované typy (UDT) implementuje pomocí rozhraní Microsoft .NET Framework common language runtime (CLR). Modul CLR je integrován do systému SQL Server a tento mechanismus umožňuje rozšířit systém typů databáze. Uživatelsky definované typy zajistí možnosti rozšíření uživatele systém typů dat serveru SQL Server a také možnost definovat komplexní typy structured.  
  
 Uživatelsky definovaný typ může poskytnout dvě klíčové výhody z hlediska architektury aplikace:  
  
-   Silné zapouzdření (i v klientovi a serveru) mezi vnitřní stav a externí chování.  
  
-   Hluboká integrace s jinými související funkce serveru. Jakmile definujete vlastní UDT, můžete ho ve všech kontextech kde můžete použít typ systému v systému SQL Server, včetně definice sloupců a jako proměnné, parametry, výsledky funkce, ukazatele, aktivační události a replikace.  
  
 Podrobnější informace najdete v článku [dokumentaci k SQL serveru](/sql) pro verzi systému SQL Server používáte.
  
 **Dokumentaci k SQL serveru**
  
1. [Uživatelem definované typy CLR](/sql/relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types)  
  
## <a name="see-also"></a>Viz také:

- [Přehled ADO.NET](../ado-net-overview.md)
