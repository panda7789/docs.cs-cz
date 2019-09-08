---
title: N-vrstvé nastavení LINQ to SQL s webovými službami
ms.date: 03/30/2017
ms.assetid: 9cb10eb8-957f-4beb-a271-5f682016fed2
ms.openlocfilehash: 279907aeaaa83d6901621c03231068d61045ec5c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781324"
---
# <a name="linq-to-sql-n-tier-with-web-services"></a>N-vrstvé nastavení LINQ to SQL s webovými službami
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]je navržený hlavně pro použití na střední úrovni v volně oddělené vrstvě pro přístup k datům (DAL), jako je například webová služba. Pokud je prezentační vrstva webová stránka ASP.NET, pak pomocí <xref:System.Web.UI.WebControls.LinqDataSource> ovládacího prvku webového serveru můžete spravovat přenos dat mezi uživatelským rozhraním a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] střední vrstvou. Pokud prezentační vrstva není stránkou ASP.NET, pak musí být obě vrstvy i prezentační vrstva pro správu serializace a deserializace dat potřeba udělat ještě nějakou další práci.  
  
## <a name="setting-up-linq-to-sql-on-the-middle-tier"></a>Nastavení LINQ to SQL na střední úrovni  
 V rámci webové služby nebo n-vrstvé aplikace obsahuje střední vrstva kontext dat a třídy entit. Tyto třídy můžete vytvořit ručně nebo buď pomocí SQLMetal. exe, nebo Návrhář relací objektů, jak je popsáno jinde v dokumentaci. V době návrhu máte možnost nastavit, aby třídy entit byly serializovatelné. Další informace najdete v tématu [jak: Proveďte serializaci](how-to-make-entities-serializable.md)entit. Další možností je vytvořit samostatnou sadu tříd, které zapouzdřují data, která mají být serializována, a pak projektovat do těchto serializovatelných typů při vracení [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] dat do dotazů.  
  
 Pak definujete rozhraní s metodami, které budou klienti volat, aby načetli, vložili a aktualizovali data. Metody rozhraní zabalí vaše [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] dotazy. Pro zpracování volání vzdálených metod a serializace dat lze použít libovolný druh serializace mechanismu. Jediným požadavkem je, že pokud máte v objektovém modelu cyklické nebo obousměrné relace, například to, že mezi zákazníky a objednávkami v modelu standardního objektu Northwind, je nutné použít serializátor, který ho podporuje. Windows Communication Foundation (WCF) <xref:System.Runtime.Serialization.DataContractSerializer> podporuje obousměrné relace, ale XmlSerializer, který se používá s webovými službami non-WCF, ne. Pokud se rozhodnete použít XmlSerializer, je nutné zajistit, aby objektový model nemá žádné cyklické relace.  
  
 Další informace o Windows Communication Foundation naleznete v tématu [Windows Communication Foundation Services a WCF Data Services v aplikaci Visual Studio](/visualstudio/data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio).  
  
 Implementujte své obchodní pravidla nebo jinou logiku specifickou pro doménu pomocí dílčích tříd a metod <xref:System.Data.Linq.DataContext> tříd entit a, které se [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] připojí k běhovým událostem. Další informace najdete v tématu [implementace N-vrstvé obchodní logiky](implementing-business-logic-linq-to-sql.md).  
  
## <a name="defining-the-serializable-types"></a>Definování serializovatelných typů  
 Úroveň klienta nebo prezentace musí mít definice typu pro třídy, které bude přijímat ze střední vrstvy. Tyto typy mohou být samotné třídy entit nebo speciální třídy, které zabalí pouze určitá pole z tříd entit pro vzdálenou komunikaci. V žádném případě je [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zcela nedotčeno, jak prezentační vrstva získává tyto definice typů. Prezentační vrstva může například použít WCF k automatickému vygenerování typů nebo může mít kopii knihovny DLL, ve které jsou tyto typy definovány, nebo může pouze definovat vlastní verze typů.  
  
## <a name="retrieving-and-inserting-data"></a>Načítání a vkládání dat  
 Střední vrstva definuje rozhraní, které určuje, jak prezentační vrstva přistupuje k datům. Například `GetProductByID(int productID)`nebo `GetCustomers()`. Na střední úrovni tělo metody většinou vytvoří novou instanci <xref:System.Data.Linq.DataContext>, spustí dotaz na jednu nebo více jeho tabulek. Střední vrstva potom vrátí výsledek jako <xref:System.Collections.Generic.IEnumerable%601>, kde `T` je buď Třída entity, nebo jiný typ, který se používá pro serializaci. Prezentační vrstva nikdy neodesílá ani nepřijímá proměnné dotazu přímo do nebo ze střední vrstvy. Tyto dvě úrovně vyměňují hodnoty, objekty a kolekce konkrétních dat. Po přijetí kolekce může prezentační vrstva použít [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] k objektům dotazování v případě potřeby.  
  
 Při vkládání dat může prezentační vrstva vytvořit nový objekt a odeslat ho do prostřední vrstvy, nebo může mít prostřední vrstvu vytvořit objekt na základě hodnot, které poskytuje. Obecně platí, že načtení a vložení dat do n-vrstvých aplikací se neliší od procesu ve dvou vícevrstvých aplikacích. Další informace najdete v tématu [dotazování databáze](querying-the-database.md) a [provádění a odesílání změn dat](making-and-submitting-data-changes.md).  
  
## <a name="tracking-changes-for-updates-and-deletes"></a>Sledování změn aktualizací a odstranění  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]podporuje optimistickou souběžnost na základě časových razítek (také s názvem RowVersions) a na původní hodnoty. Pokud jsou v databázových tabulkách časová razítka, pak aktualizace a odstranění vyžadují poněkud další práci na úrovni střední vrstvy nebo prezentační vrstvy. Nicméně pokud je nutné použít původní hodnoty pro kontroly optimistického řízení souběžnosti, pak je prezentační vrstva zodpovědná za sledování těchto hodnot a jejich odeslání zpět, když provádí aktualizace. Důvodem je to, že změny provedené v entitách v prezentační vrstvě nejsou sledovány na střední úrovni. Ve skutečnosti je původní načtení entity a její případná aktualizace obvykle prováděna dvěma zcela oddělenými instancemi <xref:System.Data.Linq.DataContext>.  
  
 Čím větší je počet změn, které prezentační vrstva dělá, tím složitější je sledovat tyto změny a zabalit je zpátky do střední vrstvy. Implementace mechanismu pro sdělování změn je zcela až do aplikace. Jediným požadavkem je, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aby bylo nutné tyto původní hodnoty, které jsou požadovány pro kontroly optimistického řízení souběžnosti.  
  
 Další informace najdete v tématu [načtení dat a operace CUD v N-vrstvých aplikacích (LINQ to SQL)](data-retrieval-and-cud-operations-in-n-tier-applications.md).  
  
## <a name="see-also"></a>Viz také:

- [N-vrstvé a vzdálené aplikace s LINQ to SQL](n-tier-and-remote-applications-with-linq-to-sql.md)
- [Přehled ovládacího prvku webového serveru LinqDataSource](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))
