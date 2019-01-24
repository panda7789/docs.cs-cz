---
title: Asynchronní operace
ms.date: 03/30/2017
ms.assetid: e7d32c3c-bf78-4bfc-a357-c9e82e4a4b3c
ms.openlocfilehash: b1c6646f666ca1d931ab8caa8cd0a2e0c6a6722f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538658"
---
# <a name="asynchronous-operations"></a>Asynchronní operace
Některé databázové operace, jako je například spuštění příkazu může trvat spoustu času k dokončení. V takovém případě musí aplikace s jedním vláknem blokování jiných operace a počkejte na dokončení předtím, než může i dál své vlastní operace příkazu. Naproti tomu nebudou moct přiřadit dlouho běžící operace ve vlákně na pozadí umožňuje vláknu popředí zůstanou aktivní v průběhu operace. V aplikaci Windows například delegování dlouho běžící operace ve vlákně na pozadí umožňuje vlákně uživatelského rozhraní nadále reagovat při provádění operace.  
  
 Rozhraní .NET Framework poskytuje několik standardních asynchronní vzory návrhu, které mohou vývojáři využít vláken na pozadí a bez uživatelského rozhraní a vlákna s vysokou prioritou k dokončení dalších operací. ADO.NET podporuje tyto stejné způsoby návrhu v jeho <xref:System.Data.SqlClient.SqlCommand> třídy. Konkrétně <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A>, a <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A> metody souřadnicí <xref:System.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.EndExecuteReader%2A>, a <xref:System.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A> metody, poskytujte asynchronní podporu.  
  
> [!NOTE]
>  Asynchronní programování je základní funkce rozhraní .NET Framework a ADO.NET plně využívá standardní návrhové vzory. Další informace o různých technikách asynchronní k dispozici pro vývojáře najdete v tématu [voláním synchronní metody asynchronně](../../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
 Ačkoli použití asynchronních metod pomocí ADO.NET funkce nepřidá žádná zvláštní opatření, je pravděpodobné, že další vývojáři použijí asynchronní funkce v ADO.NET než v jiných oblastech sady rozhraní .NET Framework. Je důležité znát výhody a nástrahy vytváření aplikací s více vlákny. Následující příklady v tomto bodě části si několik důležité problémy této vývojáři muset vzít v úvahu při sestavování aplikací zahrnujících různé funkce s více vlákny.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Aplikace Windows využívající zpětná volání](../../../../../docs/framework/data/adonet/sql/windows-applications-using-callbacks.md)  
 Poskytuje příklad ukazuje, jak bezpečně, provedení příkazu k asynchronní správné zpracování interakci s formuláři a jeho obsah v samostatném vlákně.  
  
 [Aplikace ASP.NET využívající obslužné rutiny čekání](../../../../../docs/framework/data/adonet/sql/aspnet-apps-using-wait-handles.md)  
 Poskytuje příklad ukazuje, jak provádět několik souběžných příkazy ze stránky ASP.NET, pomocí obslužné rutiny čekání ke správě operaci po dokončení všech příkazů.  
  
 [Dotazování v konzolových aplikacích](../../../../../docs/framework/data/adonet/sql/polling-in-console-applications.md)  
 Obsahuje příklad používání dotazování čekání na dokončení provádění asynchronního příkazu z konzolové aplikace. Tento postup platí také na knihovny tříd nebo v jiné aplikaci bez uživatelského rozhraní.  
  
## <a name="see-also"></a>Viz také:
- [SQL Server a ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [Asynchronní volání synchronních metod](../../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
