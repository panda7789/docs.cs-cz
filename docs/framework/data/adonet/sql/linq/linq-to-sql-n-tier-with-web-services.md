---
title: "Technologie LINQ to SQL N-vrstvá s webovými službami"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9cb10eb8-957f-4beb-a271-5f682016fed2
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a24b8fe5d0da4b3fa3a13db15bd91be83f102dcf
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="linq-to-sql-n-tier-with-web-services"></a>Technologie LINQ to SQL N-vrstvá s webovými službami
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]je určený pro použití na střední vrstvy v vrstva přístupu k datům volně vázány (DAL), třeba webové služby. Pokud prezentační vrstvou se webovou stránku ASP.NET, pak použijete <xref:System.Web.UI.WebControls.LinqDataSource> ovládacího prvku webového serveru ke správě přenosů dat mezi uživatelské rozhraní a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] na střední vrstvě. Pokud prezentační vrstvou není stránku ASP.NET, pak střední vrstvě a prezentační vrstvou musí používat ke správě serializace a deserializace dat některé další kroky.  
  
## <a name="setting-up-linq-to-sql-on-the-middle-tier"></a>Nastavení technologie LINQ to SQL na střední vrstvy  
 Ve webové služby nebo vícevrstvé aplikace bude prostřední vrstva obsahuje kontextu dat a tříd entit. Tyto třídy můžete vytvořit ručně nebo pomocí buď SQLMetal.exe nebo [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] jak je popsáno na jiném místě v dokumentaci. V době návrhu máte možnost provést serializovatelné třídy entity. Další informace najdete v tématu [postup: Zkontrolujte serializovatelný entity](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md). Další možností je vytvořit samostatnou sadu tříd, které zapouzdření serializaci dat, a poté projektu do těchto Serializovatelné typy po vrácení dat ve vašem [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] dotazy.  
  
 Potom definovat rozhraní s metody, které klienti zavolá načíst, insert a aktualizovat data. Metody rozhraní zabalení vaší [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] dotazy. Pro zpracování volání vzdálené metody a serializace dat můžete použít jakýkoli druh mechanismu serializace. Jediným požadavkem je, že pokud máte cyklická nebo obousměrné relace v objektu modelu, jako je například, že mezi zákazníci a objednávky v modelu objektu standardní Northwind, pak musíte použít serializátor, která ho podporuje. Windows Communication Foundation (WCF) <xref:System.Runtime.Serialization.DataContractSerializer> vztahů obousměrná podporuje, ale XmlSerializer, který se používá s WCF webové služby neexistuje. Pokud si zvolíte používání třídy XmlSerializer, pak je musí ověřit, objektový model nemá žádné cyklické relace.  
  
 Další informace o Windows Communication Foundation, najdete v části [služby Windows Communication Foundation a služby WCF Data Services v sadě Visual Studio](/visualstudio/data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio).  
  
 Implementovat obchodní pravidla nebo jiné specifické pro doménu logiky pomocí částečné třídy a metody na <xref:System.Data.Linq.DataContext> a tříd entit, připojí do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] události modulu runtime. Další informace najdete v tématu [implementace vícevrstvé obchodní logiky](../../../../../../docs/framework/data/adonet/sql/linq/implementing-business-logic-linq-to-sql.md).  
  
## <a name="defining-the-serializable-types"></a>Definování Serializovatelné typy  
 Klient nebo prezentační vrstva musí mít definic typů pro třídy, které bude moci přijmout ze střední vrstvy. Mohou být tyto typy tříd entit, sami nebo speciální třídy, které balí pouze určitá pole z tříd entit pro vzdálenou komunikaci. V každém případě [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] je zcela unconcerned o tom, jak prezentační vrstvou získá tyto definice typů. Například prezentační vrstvou využít WCF ke generování typy automaticky, nebo ho může mít kopie knihovny DLL, ve kterém jsou definovány tyto typy nebo jej může pouze definuje vlastní verzích typy.  
  
## <a name="retrieving-and-inserting-data"></a>Načítání a vkládání dat  
 Střední vrstva definuje rozhraní, které určuje, jak prezentační vrstvou přistupuje k datům. Například `GetProductByID(int productID)`, nebo `GetCustomers()`. Na střední vrstvy, metoda text obvykle vytvoří novou instanci třídy <xref:System.Data.Linq.DataContext>, provede dotaz na jeden nebo více jeho tabulky. Střední vrstva pak vrátí výsledek jako <xref:System.Collections.Generic.IEnumerable%601>, kde `T` třídu entity nebo jiný typ, který se používá pro serializaci. Prezentační vrstva nikdy odeslání nebo přijetí proměnné dotazu přímo do nebo z střední vrstvy. Hodnoty, objektů a kolekcí konkrétní dat systému exchange dvěma vrstvami. Po přijetí kolekci, můžete použít prezentační vrstvou [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] pro objekty, které chcete zadat dotaz v případě potřeby.  
  
 Při vkládání dat, můžete vytvořit nový objekt a odešle střední vrstva prezentační vrstvy, nebo může mít střední vrstvy vytvořit objekt založené na hodnotách, které poskytuje. Obecně platí načítání a vkládání dat do vícevrstvé aplikace není lišit od procesu aplikace vrstvy 2. Další informace najdete v tématu [dotazování databáze](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md) a [provádění a odeslání změn dat](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md).  
  
## <a name="tracking-changes-for-updates-and-deletes"></a>Sledování změn pro aktualizace a odstranění  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]podporuje optimistickou metodu souběžného založená na časová razítka (nazývaná také RowVersions) a na původní hodnoty. Pokud tabulky databáze, které mají časová razítka, pak aktualizace a odstranění vyžadují málo další práci na střední vrstvě nebo prezentační vrstvy. Ale pokud je nutné použít původní hodnoty pro optimistickou metodu souběžného kontroly, pak prezentační vrstvou zodpovídá za sledování tyto hodnoty a jejich odesláním zpět v případě, že umožňuje aktualizace. Je to proto, že nejsou ve střední vrstvě sledovat změny, které byly provedeny entity v prezentační vrstvě. Ve skutečnosti původní načtení entity a případné aktualizace provedené na ni se obvykle provádí dvě zcela samostatné instance <xref:System.Data.Linq.DataContext>.  
  
 Větší počet změn, které provede prezentační vrstvy, tím složitější bude sledovat tyto změny a balíček, který je zpět do střední vrstvy. Implementace mechanismus, který komunikuje změny je zcela až aplikace. Jediným požadavkem je, že [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] musí mít tyto původní hodnoty, které jsou požadovány pro optimistickou metodu souběžného kontroly.  
  
 Další informace najdete v tématu [operace vytvoření ve víceúrovňových aplikacích (technologie LINQ to SQL) a načítání dat ze](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md).  
  
## <a name="see-also"></a>Viz také  
 [N-vrstvé a vzdálené aplikace s LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)  
 [NIB: LinqDataSource webového serveru – Přehled ovládacího prvku](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136)
