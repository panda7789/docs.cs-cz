---
title: Asynchronní operace
ms.date: 03/30/2017
ms.assetid: e7d32c3c-bf78-4bfc-a357-c9e82e4a4b3c
ms.openlocfilehash: 97564600f6f4fb9d4990398527dd2e45fcb9f015
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="asynchronous-operations"></a>Asynchronní operace
Některé operace databáze, například spuštění příkazu může trvat déle k dokončení. V takovém případě musíte aplikace blokovat dalších operací a počkejte na dokončení, než bude moci pokračovat své vlastní operace příkazu. Naproti tomu bude možné přiřadit operaci dlouho běžící vlákna na pozadí umožňuje vlákno popředí zůstala aktivní v průběhu operace. V aplikaci pro Windows například delegování dlouho běžící operace vlákna na pozadí umožňuje uživatelské rozhraní vlákno zůstat přizpůsobivý při provádí operaci.  
  
 Rozhraní .NET Framework poskytuje několik standardní asynchronní vzory návrhu, které mohou vývojáři využít výhod vlákna na pozadí a bez uživatelského rozhraní nebo s vysokou prioritou vláken na dokončení dalších operací. ADO.NET podporuje tyto stejné vzory návrhu v jeho <xref:System.Data.SqlClient.SqlCommand> třídy. Konkrétně <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A>, a <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A> metody, spárovaný s <xref:System.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.EndExecuteReader%2A>, a <xref:System.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A> způsoby, které podporují asynchronní.  
  
> [!NOTE]
>  Asynchronní programování je základní funkce rozhraní .NET Framework a ADO.NET plně využívá standardní vzory návrhu. Další informace o různých asynchronní techniky k dispozici pro vývojáře najdete v tématu [volání synchronních metod asynchronně](../../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
 Ačkoli použití asynchronní techniky s ADO.NET funkce nepřidá žádná zvláštní opatření, je pravděpodobné, že další vývojáři použije asynchronní funkce v ADO.NET než v jiných oblastech rozhraní .NET Framework. Je důležité si uvědomit výhody a nástrahy vytváření aplikací s více vlákny. Příklady, které následují v této části bodu na několik důležité problémy, že vývojáři nutné vzít v úvahu při vytváření aplikace, které začlenit funkce s více vlákny.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Aplikace Windows využívající zpětná volání](../../../../../docs/framework/data/adonet/sql/windows-applications-using-callbacks.md)  
 Poskytuje příklad, který ukazuje, jak provést příkaz asynchronní bezpečně, správně zpracování interakci s formuláři a její obsah z samostatné vlákna.  
  
 [Aplikace ASP.NET využívající obslužné rutiny čekání](../../../../../docs/framework/data/adonet/sql/aspnet-apps-using-wait-handles.md)  
 Představuje příklad, který ukazuje, jak provést více souběžných příkazů ze stránky ASP.NET, obslužné rutiny čekání na použití ke správě operaci dokončení všech příkazů.  
  
 [Dotazování v konzolových aplikacích](../../../../../docs/framework/data/adonet/sql/polling-in-console-applications.md)  
 Poskytuje příklad znázorňující používání dotazování počkejte na dokončení asynchronního příkaz spuštění z konzolové aplikace. Tento postup je taky platná v knihovny tříd nebo jiné aplikace bez uživatelského rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [SQL Server a ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [Asynchronní volání synchronních metod](../../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
