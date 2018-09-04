---
title: Zabezpečení integrace CLR na SQL serveru
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: 953982045574cc62b1da46c5d763693b9d9d89ff
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516190"
---
# <a name="clr-integration-security-in-sql-server"></a>Zabezpečení integrace CLR na SQL serveru
Microsoft SQL Server poskytuje integraci běžné součásti modulu runtime (CLR) jazyk rozhraní .NET Framework. Integrace modulu CLR umožňuje psát uložené procedury, aktivační události, uživatelem definovaných typů, uživatelem definované funkce, uživatelem definovaných agregacích a datových proudů funkce vracející tabulku, pomocí libovolného jazyka, rozhraní .NET Framework, jako je například Microsoft Visual Basic .NET nebo Microsoft Visual C#.  
  
 Modul CLR podporuje model zabezpečení pro spravovaný kód volá zabezpečení přístupu kódu (CAS). V tomto modelu jsou udělena oprávnění pro sestavení založená na důkaz, kód v metadatech. SQL Server integruje model zabezpečení založený na uživatele systému SQL Server s použitím modelu zabezpečení přístupu kódu modulu CLR.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace o integraci modulu CLR SQL serveru najdete v následující prostředky.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Zabezpečení přístupu kódu](https://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03)|Obsahuje témata popisující certifikační Autority v rozhraní .NET Framework.|  
|[Zabezpečení integrace CLR](https://go.microsoft.com/fwlink/?LinkId=59998)|Tento článek popisuje model zabezpečení pro spravovaný kód spuštění v rámci služby SQL Server.|  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Integrace CLR (Common Language Runtime) na SQL Serveru](../../../../../docs/framework/data/adonet/sql/sql-server-common-language-runtime-integration.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
