---
title: SQL Server Compact a LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: b5a1a12018bd85cf313c1841e6b67ab2edf67b4a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792533"
---
# <a name="sql-server-compact-and-linq-to-sql"></a>SQL Server Compact a LINQ to SQL
SQL Server Compact je výchozí databáze nainstalovaná se sadou Visual Studio. Další informace naleznete v tématu [Using SQL Server Compact (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).  
  
 Toto téma popisuje klíčové rozdíly v tématu použití, konfigurace, sady funkcí a rozsahu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podpory.  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a>Charakteristiky SQL Server Compact ve vztahu k LINQ to SQL  
 Ve výchozím nastavení je SQL Server Compact nainstalován pro všechny edice sady Visual Studio a je proto k dispozici ve vývojovém počítači pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]použití s nástrojem. Ale nasazení aplikace, která používá SQL Server Compact [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , se liší od aplikace SQL Server. SQL Server Compact není součástí .NET Framework a proto musí být zabalená do aplikace nebo stažena odděleně od webu společnosti Microsoft.  
  
 Všimněte si následujících vlastností:  
  
- SQL Server Compact je zabalen jako knihovna DLL, kterou lze použít přímo pro soubory databáze (přípona. sdf).  
  
- SQL Server Compact běží ve stejném procesu jako klientská aplikace. Efektivita komunikace s SQL Server Compact může být proto výrazně vyšší než komunikace s SQL Server. Na druhé straně SQL Server Compact vyžaduje interoperabilitu mezi spravovaným a nespravovaným kódem a jeho přidruženými náklady.  
  
- Velikost SQL Server Compact DLL je malá. Tato funkce zmenší celkovou velikost aplikace.  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Modul runtime a nástroj příkazového řádku SQLMetal podporují SQL Server Compact.  
  
- Návrhář relací objektů nepodporuje SQL Server Compact.  
  
## <a name="feature-set"></a>Sada funkcí  
 Sada funkcí SQL Server Compact je mnohem jednodušší než sada funkcí SQL Server následujícími způsoby, které mohou ovlivnit [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikace:  
  
- SQL Server Compact nepodporuje uložené procedury ani zobrazení.  
  
- SQL Server Compact podporuje pouze podmnožinu datových typů a funkcí SQL.  
  
- SQL Server Compact podporuje pouze podmnožinu konstrukcí SQL.  
  
- SQL Server Compact poskytuje jenom minimální Optimalizátor. Je možné, že některé dotazy můžou vyprší časový limit.  
  
- SQL Server Compact nepodporuje částečnou důvěryhodnost.  
  
## <a name="see-also"></a>Viz také:

- [Referenční informace](reference.md)
