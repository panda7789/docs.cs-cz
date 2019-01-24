---
title: Typické postupy použití LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 9a88bd51-bd74-48f7-a9b1-f650e8d55a3e
ms.openlocfilehash: 32e81d08010f67b8eac19777a40826b18c440f83
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548008"
---
# <a name="typical-steps-for-using-linq-to-sql"></a>Typické postupy použití LINQ to SQL
K implementaci [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikace, podle postupu popsaného dále v tomto tématu. Všimněte si, že mnoho kroků jsou volitelné. Je velmi je to možné, že můžete použít objektový model ve svém výchozím stavu.  
  
 Pro velmi rychlý start, použijte [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] vytvoření objektového modelu a pusťte se do programování vaše dotazy.  
  
## <a name="creating-the-object-model"></a>Vytvoření objektového modelu  
 Prvním krokem je vytvoření objektového modelu z metadat stávající relační databáze. Objektový model představuje databázi podle programovacím jazyce vývojáře. Další informace najdete v tématu [The LINQ to SQL objektový Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).  
  
### <a name="1-select-a-tool-to-create-the-model"></a>1. Vyberte nástroj k vytváření modelu.  
 Tři nástroje jsou k dispozici pro vytváření modelu.  
  
-   Na [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]  
  
     Tento návrhář poskytuje bohaté možnosti uživatelského rozhraní pro vytvoření modelu objektu z existující databáze. Tento nástroj je součástí rozhraní IDE sady Visual Studio a je nejvhodnější pro malé a střední databáze.  
  
-   Nástroje pro generování kódu SQLMetal  
  
     Tento nástroj příkazového řádku poskytuje mírně odlišnou sadu možností [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]. Modelování velkých databází se nejlépe provádí pomocí tohoto nástroje. Další informace najdete v tématu [SqlMetal.exe (nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
-   Editor kódu  
  
     Můžete napsat vlastní kód pomocí editoru kódu sady Visual Studio nebo jiného editoru. Tento přístup, což může být náchylná k chybám, pokud máte existující databázi a můžete použít buď nedoporučujeme [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] nebo nástroji SQLMetal. Editor kódu však může být velmi cennou pomůckou pro upřesnění nebo upravovat kód, který již vytvořených pomocí jiných nástrojů. Další informace najdete v tématu [jak: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md).  
  
### <a name="2-select-the-kind-of-code-you-want-to-generate"></a>2. Vyberte typ kódu, který chcete vygenerovat.  
  
-   A C# nebo souboru zdrojového kódu jazyka Visual Basic pro mapování založených na atributech.  
  
     Potom zahrnutí souboru s tímto kódem do projektu sady Visual Studio. Další informace najdete v tématu [založených na atributech mapování](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
-   Soubor XML pro externí mapování.  
  
     Pomocí tohoto přístupu můžete zachovat metadata mapování z kódu aplikace. Další informace najdete v tématu [externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
    > [!NOTE]
    >  [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] Nepodporuje generování externí soubory mapování. Musíte použít nástroj SQLMetal k implementaci této funkce.  
  
-   Souboru DBML, kterou můžete upravit před generováním konečný kód souboru.  
  
     Jde o pokročilou funkci.  
  
### <a name="3-refine-the-code-file-to-reflect-the-needs-of-your-application"></a>3. Upravit soubor kódu tak, aby odrážely potřebám vaší aplikace.  
 K tomuto účelu můžete použít buď [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] nebo editoru kódu.  
  
## <a name="using-the-object-model"></a>Použití objektového modelu  
 Následující obrázek znázorňuje vztah mezi vývojáři a data ve scénáři dvouvrstvé. Další scénáře, naleznete v tématu [N-vrstvé a vzdálené aplikace s LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md).  
  
 ![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")  
  
 Teď, když máte model objektu, popište informace žádosti a manipulaci s daty v rámci tohoto modelu. Si myslíte, co se týče objektů a vlastností v objektovém modelu a nikoli z hlediska řádky a sloupce databáze. Není řešit přímo s databází.  
  
 Pokud dáte pokyn [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] buď spustit dotaz, který je popsán nebo volání `SubmitChanges()` na data, která mají manipulovat, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] komunikuje s databází v jazyce, který v databázi.  
  
 Následující příklad představuje typické postupy použití objektového modelu, který jste vytvořili.  
  
### <a name="1-create-queries-to-retrieve-information-from-the-database"></a>1. Vytváření dotazů k načtení informací z databáze.  
 Další informace najdete v tématu [koncepty dotazu](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md) a [Příklady dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md).  
  
### <a name="2-override-default-behaviors-for-insert-update-and-delete"></a>2. Změnit výchozí chování pro příkaz Insert, Update a odstranit.  
 Tento krok je volitelný. Další informace najdete v tématu [přizpůsobení Insert, Update a operace odstranění](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
  
### <a name="3-set-appropriate-options-to-detect-and-report-concurrency-conflicts"></a>3. Nastavit příslušné možnosti ke zjišťování a hlášení konfliktů souběžnosti.  
 Modelu můžete ponechat jeho výchozí hodnoty pro zpracování konfliktů souběžnosti, nebo můžete změnit tak, aby odpovídal vaší účely. Další informace najdete v tématu [jak: Zadejte, kteří členové jsou testovat na konflikty souběžnosti](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) a [jak: Zadejte mají objevit výjimky souběžnosti při](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md).  
  
### <a name="4-establish-an-inheritance-hierarchy"></a>4. Vytvoření hierarchie dědičnosti.  
 Tento krok je volitelný. Další informace najdete v tématu [podpora dědičnosti](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md).  
  
### <a name="5-provide-an-appropriate-user-interface"></a>5. Poskytnout příslušné uživatelské rozhraní.  
 Tento krok je volitelný a závisí na používání vaší aplikace.  
  
### <a name="6-debug-and-test-your-application"></a>6. Ladění a testování vaší aplikace.  
 Další informace najdete v tématu [podporu ladění](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md).  
  
## <a name="see-also"></a>Viz také:
- [Začínáme](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
- [Vytvoření objektového modelu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [Uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
