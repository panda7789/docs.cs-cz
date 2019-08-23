---
title: Typické postupy použití LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 9a88bd51-bd74-48f7-a9b1-f650e8d55a3e
ms.openlocfilehash: 26b88e4d45365bbaac986ce8751e1d3b5383909b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946995"
---
# <a name="typical-steps-for-using-linq-to-sql"></a>Typické postupy použití LINQ to SQL
Chcete-li [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implementovat aplikaci, postupujte podle kroků popsaných dále v tomto tématu. Všimněte si, že řada kroků je volitelná. Je velmi možné, že svůj objektový model můžete použít ve svém výchozím stavu.  
  
 Pro skutečně rychlé zahájení použijte Návrhář relací objektů k vytvoření objektového modelu a zahájení kódování dotazů.  
  
## <a name="creating-the-object-model"></a>Vytvoření objektového modelu  
 Prvním krokem je vytvoření objektového modelu z metadat existující relační databáze. Objektový model představuje databázi podle programovacího jazyka vývojáře. Další informace najdete v tématu [model objektu LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).  
  
### <a name="1-select-a-tool-to-create-the-model"></a>1. Vyberte nástroj pro vytvoření modelu.  
 Pro vytvoření modelu jsou k dispozici tři nástroje.  
  
- Návrhář relací objektů  
  
     Tento návrhář poskytuje bohatě uživatelské rozhraní pro vytvoření objektového modelu z existující databáze. Tento nástroj je součástí integrovaného vývojového prostředí sady Visual Studio a je vhodný pro malé nebo střední databáze.  
  
- Nástroj pro generování kódu SQLMetal  
  
     Tento nástroj příkazového řádku poskytuje mírně odlišnou sadu možností z návrháře O/R. Vytváření modelů velkých databází se nejlépe provádí pomocí tohoto nástroje. Další informace naleznete v tématu [SqlMetal. exe (Nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
- Editor kódu  
  
     Vlastní kód můžete napsat buď pomocí editoru kódu sady Visual Studio, nebo jiného editoru. Tento přístup nedoporučujeme, což může být náchylné k chybám, pokud máte existující databázi a můžete použít buď návrháře v/R, nebo nástroj SQLMetal. Editor kódu však může být užitečný pro rafinaci nebo úpravu kódu, který již byl vygenerován pomocí jiných nástrojů. Další informace najdete v tématu [jak: Přizpůsobení tříd entit pomocí editoru](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)kódu.  
  
### <a name="2-select-the-kind-of-code-you-want-to-generate"></a>2. Vyberte druh kódu, který chcete vygenerovat.  
  
- Soubor C# zdrojového kódu nebo Visual Basic pro mapování na základě atributů.  
  
     Tento soubor kódu pak zahrnete do projektu sady Visual Studio. Další informace najdete v tématu [mapování na základě atributů](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
- Soubor XML pro externí mapování  
  
     Pomocí tohoto přístupu můžete zachovat mapování metadat z kódu vaší aplikace. Další informace najdete v tématu [externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
    > [!NOTE]
    > Návrhář O/R nepodporuje generování externích mapovacích souborů. K implementaci této funkce je nutné použít nástroj SQLMetal.  
  
- Soubor DBML, který lze upravit před vygenerováním finálního souboru s kódem.  
  
     Toto je pokročilá funkce.  
  
### <a name="3-refine-the-code-file-to-reflect-the-needs-of-your-application"></a>3. Upřesněte soubor kódu tak, aby odrážel potřeby vaší aplikace.  
 Pro tento účel můžete použít buď návrháře v/R, nebo Editor kódu.  
  
## <a name="using-the-object-model"></a>Použití objektového modelu  
 Následující ilustrace znázorňuje vztah mezi vývojářem a daty ve scénáři dvou vrstev. Další scénáře najdete v tématu [N-vrstvé a vzdálené aplikace s LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md).  
  
 ![Snímek obrazovky, který zobrazuje model objektu LINQ.](./media/the-linq-to-sql-object-model/linq-object-model-two-tier.png)  
  
 Teď, když máte objektový model, popíšete požadavky na informace a manipulujete s daty v tomto modelu. Uvažujte o objektech a vlastnostech v objektovém modelu a nemusíte být v souladu s řádky a sloupci databáze. Nechcete pracovat přímo s databází.  
  
 Když dáte pokyn [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] k provedení dotazu, který jste popsali nebo zavolali `SubmitChanges()` na data, která jste nastavili, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] komunikuje s databází v jazyce databáze.  
  
 Následující příklad představuje typické kroky pro použití objektového modelu, který jste vytvořili.  
  
### <a name="1-create-queries-to-retrieve-information-from-the-database"></a>1. Vytvořte dotazy pro načtení informací z databáze.  
 Další informace najdete v tématu [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md) a [příklady dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md).  
  
### <a name="2-override-default-behaviors-for-insert-update-and-delete"></a>2. Přepíše výchozí chování pro vložení, aktualizaci a odstranění.  
 Tento krok je volitelný. Další informace najdete v tématu [přizpůsobení operací vložení, aktualizace a odstranění](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
  
### <a name="3-set-appropriate-options-to-detect-and-report-concurrency-conflicts"></a>3. Nastavte vhodné možnosti pro detekci a nahlášení konfliktů souběžnosti.  
 Můžete ponechat svůj model s výchozími hodnotami pro zpracování konfliktů souběžnosti, nebo ho můžete změnit tak, aby vyhovoval vašim účelům. Další informace najdete v tématu [jak: Určete, kteří členové jsou testováni pro konflikty](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) souběžnosti a [postupy: Určete, kdy jsou vyvolány](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md)výjimky souběžnosti.  
  
### <a name="4-establish-an-inheritance-hierarchy"></a>4. Vytvořte hierarchii dědičnosti.  
 Tento krok je volitelný. Další informace najdete v tématu [Podpora dědičnosti](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md).  
  
### <a name="5-provide-an-appropriate-user-interface"></a>5. Poskytněte příslušné uživatelské rozhraní.  
 Tento krok je nepovinný a závisí na tom, jak se vaše aplikace použije.  
  
### <a name="6-debug-and-test-your-application"></a>6. Ladění a testování aplikace.  
 Další informace najdete v tématu [Podpora ladění](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md).  
  
## <a name="see-also"></a>Viz také:

- [Začínáme](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
- [Vytvoření objektového modelu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [Uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
