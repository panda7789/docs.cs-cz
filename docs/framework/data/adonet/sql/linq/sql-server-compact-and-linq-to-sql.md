---
title: SQL Server Compact a technologie LINQ to SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 24f620319cd469538cf4454be7caffececdf9213
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="sql-server-compact-and-linq-to-sql"></a>SQL Server Compact a technologie LINQ to SQL
Systém SQL Server Compact je databáze výchozí nainstalované s Visual Studio. Další informace najdete v tématu [PAVE přes pomocí systému SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/library/13320dd1-94e5-4077-bf76-8df253695ccc).  
  
 Toto téma popisuje hlavní rozdíly ve využití, konfiguraci, sady funkcí a oboru [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporovat.  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a>Vlastnosti systému SQL Server Compact ve vztahu k technologie LINQ to SQL  
 Ve výchozím nastavení, je pro všechny nainstalován systém SQL Server Compact [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] edice a proto je k dispozici na vývojovém počítači pro použití s [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Nasazení aplikace, která používá systém SQL Server Compact, ale a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se liší od pro [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] aplikace. Systém SQL Server Compact není součástí rozhraní .NET Framework a proto musí být zabalené aplikace nebo samostatně stáhnout z webu společnosti Microsoft.  
  
 Vezměte na vědomí následující vlastnosti:  
  
-   Systém SQL Server Compact je zabalené jako knihovnu DLL, kterou lze použít pro soubory databáze (rozšíření SDF) přímo.  
  
-   Systém SQL Server Compact běží v rámci jednoho procesu jako klientská aplikace. Efektivitu komunikace se službou SQL Server Compact proto může být výrazně vyšší než komunikaci s [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)]. Systém SQL Server Compact na druhé straně vyžadují spolupráci mezi spravovanými a nespravovanými kódu pomocí jeho náklady z toho plynoucí.  
  
-   Velikost je SQL Server Compact DLL je malá. Tato funkce snižuje velikost celkové aplikace.  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Runtime a nástroj příkazového řádku na SQLMetal podporují systém SQL Server Compact.  
  
-   [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Nepodporuje systém SQL Server Compact.  
  
## <a name="feature-set"></a>Sada funkcí  
 Systém SQL Server Compact sada funkcí je mnohem jednodušší než funkce sadu [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] následujícími způsoby, které můžou ovlivnit [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikace:  
  
-   Systém SQL Server Compact nepodporuje uložené procedury nebo zobrazení.  
  
-   Systém SQL Server Compact podporuje jenom podmnožinu funkcí SQL a datových typů.  
  
-   Systém SQL Server Compact podporuje pouze podmnožinu konstrukce SQL.  
  
-   Systém SQL Server Compact poskytuje jenom minimální pro optimalizaci. Je možné, že některé dotazy může vypršení časového limitu.  
  
-   Systém SQL Server Compact nepodporuje částečnou důvěryhodností.  
  
## <a name="see-also"></a>Viz také  
 [Referenční informace](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
