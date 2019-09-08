---
title: Asynchronní operace
ms.date: 03/30/2017
ms.assetid: e7d32c3c-bf78-4bfc-a357-c9e82e4a4b3c
ms.openlocfilehash: 55cb9472c23f09b3f0f248a795dbad62af8ff37f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782601"
---
# <a name="asynchronous-operations"></a>Asynchronní operace
Některé databázové operace, například spuštění příkazu, mohou trvat poměrně dlouho. V takovém případě musí aplikace s jedním vláknem blokovat jiné operace a počkat na dokončení příkazu, aby mohli pokračovat v jejich vlastních operacích. Naproti tomu možnost přiřazení dlouhotrvající operace do vlákna na pozadí umožňuje, aby vlákno na popředí zůstalo aktivní v průběhu operace. V aplikaci systému Windows, například delegování dlouhotrvající operace do vlákna na pozadí umožňuje, aby vlákno uživatelského rozhraní zůstalo při provádění operace reagovat.  
  
 .NET Framework poskytuje několik standardních asynchronních vzorů návrhu, které mohou vývojáři využít k využití vláken na pozadí, k uvolnění uživatelského rozhraní nebo s vysokou prioritou k dokončení jiných operací. ADO.NET podporuje stejné vzory návrhu ve své <xref:System.Data.SqlClient.SqlCommand> třídě. <xref:System.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A> <xref:System.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A> <xref:System.Data.SqlClient.SqlCommand.EndExecuteReader%2A>Konkrétně metody, a<xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A> , které jsou spárovány s metodami, a, poskytují asynchronní podporu. <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A> <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A>  
  
> [!NOTE]
> Asynchronní programování je základní funkcí .NET Framework a ADO.NET plně využívá standardní vzory návrhu. Další informace o různých asynchronních technikách dostupných vývojářům naleznete v tématu [asynchronní volání synchronních metod](../../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
 I když použití asynchronních technik s funkcemi ADO.NET nepřidává žádné zvláštní požadavky, je pravděpodobnější, že více vývojářů bude používat asynchronní funkce v ADO.NET než v jiných oblastech .NET Framework. Je důležité si uvědomit, že výhody a nástrah vytváření vícevláknových aplikací. Příklady, které následují v této části, ukazují několik důležitých problémů, které můžou vývojáři vzít v úvahu při sestavování aplikací, které zahrnují funkce s více vlákny.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Aplikace Windows využívající zpětná volání](windows-applications-using-callbacks.md)  
 Obsahuje příklad demonstrující, jak bezpečně spustit asynchronní příkaz, který správně zpracovává interakci s formulářem a jeho obsahem z samostatného vlákna.  
  
 [Aplikace ASP.NET využívající obslužné rutiny čekání](aspnet-apps-using-wait-handles.md)  
 Poskytuje příklad demonstrující, jak spustit více souběžných příkazů ze stránky ASP.NET pomocí čekacích obslužných rutin ke správě operace při dokončování všech příkazů.  
  
 [Dotazování v konzolových aplikacích](polling-in-console-applications.md)  
 Poskytuje příklad demonstrující použití cyklického dotazování pro čekání na dokončení asynchronního příkazu z konzolové aplikace. Tato technika je také platná v knihovně tříd nebo jiné aplikaci bez uživatelského rozhraní.  
  
## <a name="see-also"></a>Viz také:

- [SQL Server a ADO.NET](index.md)
- [Asynchronní volání synchronních metod](../../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)
- [Přehled ADO.NET](../ado-net-overview.md)
