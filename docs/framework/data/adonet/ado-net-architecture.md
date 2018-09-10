---
title: Architektura ADO.NET
ms.date: 03/30/2017
ms.assetid: fcd45b99-ae8f-45ab-8b97-d887beda734e
ms.openlocfilehash: 4c2299951202794112ea66c1f20025777c68e356
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195514"
---
# <a name="adonet-architecture"></a>Architektura ADO.NET
Zpracování dat tradičně spoléhalo především v rámci modelu založeného na připojení, dvě vrstvy. Zpracování dat stále používá vícevrstvé architektury, programátoři přepnutí na odpojeném přístup k poskytování lepšího škálování pro své aplikace.  
  
## <a name="adonet-components"></a>Komponenty technologie ADO.NET  
 Dvě hlavní součásti [!INCLUDE[ado_orcas_long](../../../../includes/ado-orcas-long-md.md)] pro přístup k a manipulaci s daty [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatelé dat a <xref:System.Data.DataSet>.  
  
### <a name="net-framework-data-providers"></a>Zprostředkovatelé dat .NET framework  
 Zprostředkovatelé dat .NET Framework jsou komponenty, které byly výslovně navrženy pro manipulaci s daty a rychlé, pouze vpřed, jen pro čtení přístup k datům. `Connection` Objekt, který poskytuje připojení ke zdroji dat. `Command` Objekt umožňuje přístup k příkazům databázi vrátit data, upravovat data, spuštění uložené procedury a odeslat nebo načíst informace o parametrech. `DataReader` Poskytuje vysoce výkonné datové proudy dat z datového zdroje. Nakonec `DataAdapter` představuje spojení mezi `DataSet` objektu a zdrojem dat. `DataAdapter` Používá `Command` objekty pro spuštění příkazů SQL ve zdroji dat pro obě zatížení `DataSet` s daty a sloučení změn provedených pro data v `DataSet` zpět do zdroje dat. Další informace najdete v tématu [zprostředkovatelé dat .NET Framework](../../../../docs/framework/data/adonet/data-providers.md) a [načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md).  
  
### <a name="the-dataset"></a>Datové sady  
 ADO.NET `DataSet` je vytvořené speciálně pro přístup k datům nezávislý ze všech zdrojů. V důsledku toho jde použít s více a data rozdílné zdrojů, používá s daty XML nebo použít ke správě dat místní aplikace. `DataSet` Obsahuje kolekci jednoho nebo více <xref:System.Data.DataTable> skládající se z řádků a sloupců dat a primární klíč, cizí klíče, omezení a relace informace o data v objekty `DataTable` objekty. Další informace najdete v tématu [datové sady, datové tabulky a zobrazení dat](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).  
  
 Následující diagram znázorňuje vztah mezi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] poskytovatele dat a `DataSet`.  
  
 ![ADO.Net – grafika](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
Architektura ADO.NET  
  
### <a name="choosing-a-datareader-or-a-dataset"></a>Výběr čtečky dat nebo datové sady  
 Při rozhodování, zda by měla vaše aplikace používat `DataReader` (naleznete v tématu [načítání dat pomocí čtečky dat](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)) nebo `DataSet` (naleznete v tématu [datové sady, datové tabulky a zobrazení dat](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)), vezměte v úvahu typ Funkce, které vaše aplikace vyžaduje. Použití `DataSet` můžete provádět následující:  
  
-   Mezipaměť dat místně ve vaší aplikaci tak, že jste s ním pracovat. Pokud potřebujete načíst výsledky dotazu, `DataReader` je lepší volbou.  
  
-   Vzdálená data mezi vrstvami nebo z webové služby XML.  
  
-   Práce s daty dynamicky jako je například vytvoření vazby ovládacího prvku Windows Forms nebo správné kombinování a související data z různých zdrojů.  
  
-   Proveďte rozsáhlé zpracování dat bez nutnosti otevřít připojení ke zdroji dat, díky čemuž nemusí připojení pro ostatní klienty.  
  
 Pokud nechcete, aby funkce poskytované službou `DataSet`, můžete zvýšit výkon vaší aplikace pomocí `DataReader` vrátit vaše data způsobem dopředné, jen pro čtení. I když `DataAdapter` používá `DataReader` tak, aby vyplnil obsah `DataSet` (naleznete v tématu [naplnění datové sady z adaptéru dat](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)), pomocí `DataReader`, můžete zvýšit výkon, protože se uloží paměti který by být využívány službou `DataSet`a vyhněte se zpracování, které je potřeba vytvořit a vyplnit obsah `DataSet`.  
  
## <a name="linq-to-dataset"></a>LINQ na DataSet  
 Technologie LINQ to DataSet poskytuje možnosti dotazů a kontrolu nad daty v mezipaměti v objektu datové sady typu za kompilace. Umožní vám psát dotazy v jednom z vývojový jazyk rozhraní .NET Framework, jako je C# nebo Visual Basic. Další informace najdete v tématu [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>Technologie LINQ to SQL  
 Technologie LINQ to SQL podporuje dotazy vůči objektovému modelu, který je namapovaný na datové struktury relační databáze bez použití zprostředkující koncepčního modelu. Každá tabulka je reprezentován samostatné třídy, pevné párování model objektu schématu relační databáze. Technologie LINQ to SQL integrovaný jazyk dotazů v objektovém modelu se přeloží do jazyka Transact-SQL a odesílá je do databáze pro spuštění. Výsledky návratu databáze technologie LINQ to SQL převádí výsledky zpět do objektů. Další informace najdete v tématu [technologie LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework  
 ADO.NET Entity Framework je určen k vývojářům umožňují vytvářet aplikace přistupující k datům programování v modelu koncepční aplikace namísto programování přímo proti schématu relační úložiště. Cílem je snížit množství kódu a údržba vyžaduje pro aplikace orientované na data. Další informace najdete v tématu [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).  
  
## <a name="wcf-data-services"></a>WCF Data Services  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] slouží k nasazení datových služeb na webu nebo intranetu. Strukturovaná data jako entitami a relacemi podle specifikace modelu Entity Data Model. Data nasazené na tento model je adresovat pomocí standardního protokolu HTTP. Další informace najdete v tématu [4.5 služby WCF Data](../../../../docs/framework/data/wcf/index.md).  
  
## <a name="xml-and-adonet"></a>XML a ADO.NET  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] využívá výkon XML k poskytování odpojené přístup k datům. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] byl navržený ručně spolupráce s třídami XML v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]; obě jsou součástí jedné architektury.  
  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] a třídy XML v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sloučit v `DataSet` objektu. `DataSet` Může být načtena data z XML použitého jako zdroj, ať už jde o souboru nebo datový proud XML. `DataSet` Lze zapsat jako kompatibilní s XML World Wide Web Consortium (W3C), který obsahuje schématem jako XML definice jazyk (XSD) schématu, bez ohledu na zdroj dat v `DataSet`. Z důvodu formát nativní serializace `DataSet` je XML, je skvělé médium pro přesun dat mezi vrstvami, což `DataSet` optimální volbou pro kontext dat a schématu vzdálené komunikace do a z webové služby XML. Další informace najdete v tématu [XML dokumenty a Data](../../../../docs/standard/data/xml/index.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
