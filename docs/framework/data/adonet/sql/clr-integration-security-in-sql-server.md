---
title: Zabezpečení integrace CLR na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: 4756d13ff52a4c55b48c3ea56d26111029c8a7e4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794570"
---
# <a name="clr-integration-security-in-sql-server"></a>Zabezpečení integrace CLR na SQL Serveru
Microsoft SQL Server poskytuje integraci komponenty modulu CLR (Common Language Runtime) .NET Framework. Integrace CLR umožňuje psát uložené procedury, triggery, uživatelsky definované typy, uživatelsky definované funkce, uživatelsky definované agregace a streamovat funkce vracející tabulku pomocí libovolného .NET Framework jazyka, jako je Microsoft Visual Basic .NET nebo Microsoft. Vizuál C#.  
  
 CLR podporuje model zabezpečení, který se nazývá zabezpečení přístupu kódu (CAS) pro spravovaný kód. V tomto modelu jsou oprávnění udělena sestavením na základě legitimace poskytnuté kódem v metadatech. SQL Server integruje model zabezpečení založený na uživatelích SQL Server s modelem zabezpečení založeném na přístupu kódu CLR.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace o integraci modulu CLR s SQL Server naleznete v následujících zdrojích informací.  
  
|Resource|Popis|  
|--------------|-----------------|  
|[Zabezpečení přístupu kódu](../../../misc/code-access-security.md)|Obsahuje témata popisující certifikační autority v .NET Framework.|  
|[Zabezpečení integrace CLR](/sql/relational-databases/clr-integration/security/clr-integration-security)|Popisuje model zabezpečení pro spravovaný kód spouštěný uvnitř SQL Server.|  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../securing-ado-net-applications.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](application-security-scenarios-in-sql-server.md)
- [Integrace CLR (Common Language Runtime) na SQL Serveru](sql-server-common-language-runtime-integration.md)
- [Přehled ADO.NET](../ado-net-overview.md)
