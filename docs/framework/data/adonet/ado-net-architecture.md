---
title: Architektura
description: 'Přečtěte si o architektuře ADO.NET, včetně dvou hlavních komponent pro přístup k datům a manipulaci s nimi: poskytovatelé dat .NET Framework a datovou sadu.'
ms.date: 03/30/2017
ms.assetid: fcd45b99-ae8f-45ab-8b97-d887beda734e
ms.openlocfilehash: 91e5b1e33ed1bc6e2acf6068a03bb8185324470d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287178"
---
# <a name="adonet-architecture"></a>Architektura ADO.NET
Zpracování dat se tradičně spoléhalo hlavně na vícevrstvý model založený na připojení. Protože zpracování dat stále používá vícevrstvé architektury, programátoři přepínají na odpojený přístup, aby zajistil lepší škálovatelnost svých aplikací.  
  
## <a name="adonet-components"></a>Součásti ADO.NET  
 Dvě hlavní součásti ADO.NET pro přístup k datům a manipulaci s nimi jsou poskytovatelé dat .NET Framework a <xref:System.Data.DataSet> .  
  
### <a name="net-framework-data-providers"></a>Zprostředkovatelé dat .NET Framework  
 Poskytovatelé dat .NET Framework jsou komponenty, které jsou explicitně navržené pro manipulaci s daty a umožňují rychlý přístup jen pro čtení k datům. `Connection`Objekt poskytuje připojení ke zdroji dat. `Command`Objekt umožňuje přístup k databázovým příkazům, vracet data, upravovat data, spouštět uložené procedury a odesílat nebo načítat informace o parametrech. `DataReader`Poskytuje vysoce výkonný datový proud dat ze zdroje dat. Nakonec `DataAdapter` poskytuje most mezi `DataSet` objektem a zdrojem dat. `DataAdapter`Používá `Command` objekty ke spouštění příkazů SQL ve zdroji dat, aby se načetly `DataSet` s daty a odsouhlasily změny provedené v datech v `DataSet` zpátky do zdroje dat. Další informace najdete v tématech [poskytovatelé dat .NET Framework](data-providers.md) a [načítání a úpravy dat v ADO.NET](retrieving-and-modifying-data.md).  
  
### <a name="the-dataset"></a>Datová sada  
 ADO.NET `DataSet` je explicitně navržen pro přístup k datům nezávisle na jakémkoli zdroji dat. V důsledku toho je možné ho použít s více a různými zdroji dat, použitými s daty XML, nebo se používají ke správě dat místních do aplikace. `DataSet`Obsahuje kolekci jednoho nebo více <xref:System.Data.DataTable> objektů, které se skládají z řádků a sloupců dat, a také informace o primárních klíčích, cizích klíčích, omezeních a vzrelacích k datům v `DataTable` objektech. Další informace najdete v tématu [datové sady, datové tabulky a datazobrazení](./dataset-datatable-dataview/index.md).  
  
 Následující diagram znázorňuje vztah mezi .NET Framework poskytovatel dat a `DataSet` .  
  
 ![Obrázek ADO.Net](./media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
Architektura ADO.NET  
  
### <a name="choosing-a-datareader-or-a-dataset"></a>Výběr objektu DataReader nebo datové sady  
 Pokud se rozhodnete, jestli má aplikace používat `DataReader` (viz [načítání dat pomocí objektu DataReader](retrieving-data-using-a-datareader.md)) `DataSet` , nebo (viz datové [sady, datové tabulky a data zobrazení](./dataset-datatable-dataview/index.md)), zvažte typ funkčnosti, které vaše aplikace vyžaduje. Použijte `DataSet` k tomu následující postup:  
  
- Ukládat data do mezipaměti lokálně v aplikaci, abyste ji mohli manipulovat. Pokud potřebujete jenom číst výsledky dotazu, `DataReader` je lepší volbou.  
  
- Vzdálená data mezi vrstvami nebo z webové služby XML.  
  
- Můžete interaktivně pracovat s daty, jako jsou například vazby k ovládacímu prvku model Windows Forms nebo kombinování a související data z více zdrojů.  
  
- Provádění rozsáhlých zpracování dat bez nutnosti otevřeného připojení ke zdroji dat, který uvolňuje připojení používané jinými klienty.  
  
 Pokud nepotřebujete funkčnost poskytovanou nástrojem `DataSet` , můžete zvýšit výkon aplikace pomocí metody, `DataReader` aby se data načetla jen pro čtení. Přestože `DataAdapter` používá `DataReader` k naplnění obsahu a `DataSet` (viz [naplnění datové sady z DataAdapter](populating-a-dataset-from-a-dataadapter.md)) pomocí `DataReader` , můžete zvýšit výkon, protože ušetříte paměť, která by byla spotřebovaná, a nebudete se muset `DataSet` vyhnout zpracování, které je nutné k vytvoření a vyplnění obsahu `DataSet` .  
  
## <a name="linq-to-dataset"></a>LINQ na DataSet  
 LINQ to DataSet poskytuje možnosti dotazů a kontrolu typu při kompilaci nad daty uloženými v objektu DataSet. Umožňuje psát dotazy v jednom z .NET Framework vývojového jazyka, jako je například C# nebo Visual Basic. Další informace najdete v tématu [LINQ to DataSet](linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>Technologie LINQ to SQL  
 LINQ to SQL podporuje dotazy na objektovém modelu, který je namapován na datové struktury relační databáze bez použití zprostředkujícího koncepčního modelu. Každá tabulka je reprezentována samostatnou třídou, a to těsným propojením objektového modelu do schématu relační databáze. LINQ to SQL překládá dotazy integrované do jazyka v objektovém modelu do jazyka Transact-SQL a odesílá je do databáze pro provedení. Když databáze vrátí výsledky, LINQ to SQL přeloží výsledky zpět do objektů. Další informace najdete v tématu [LINQ to SQL](./sql/linq/index.md).  
  
## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework  
 Entity Framework ADO.NET je navržená tak, aby vývojářům umožnila vytvářet aplikace pro přístup k datům pomocí programování na koncepčním modelu aplikace namísto programování přímo proti schématu relačního úložiště. Cílem je snížit množství kódu a potřebnou údržbu pro aplikace orientované na data. Další informace najdete v tématu [ADO.NET Entity Framework](./ef/index.md).  
  
## <a name="wcf-data-services"></a>WCF Data Services  
 WCF Data Services slouží k nasazení datových služeb na webu nebo v intranetu. Data jsou strukturovaná jako entity a vztahy podle specifikací model EDM (Entity Data Model). Data nasazená v tomto modelu jsou adresovatelné pomocí standardního protokolu HTTP. Další informace najdete v tématu [WCF Data Services 4,5](../wcf/index.md).  
  
## <a name="xml-and-adonet"></a>XML a ADO.NET  
 ADO.NET využívá sílu XML k poskytování odpojeného přístupu k datům. ADO.NET byla navržena ručně s třídami XML v .NET Framework; Obě jsou komponenty jedné architektury.  
  
 ADO.NET a třídy XML v .NET Framework konvergují v `DataSet` objektu. `DataSet`Lze naplnit daty ze zdroje XML bez ohledu na to, zda se jedná o soubor nebo datový proud XML. `DataSet`Může být napsán jako XML kompatibilní s Web Consortium (W3C), který obsahuje schéma jako schéma XML Schema Definition Language (XSD), bez ohledu na zdroj dat v `DataSet` . Vzhledem k tomu, že formát nativní serializace `DataSet` je XML, je vynikajícím médiem pro přesouvání dat mezi vrstvami, což je `DataSet` optimální volba pro vzdálenou komunikaci dat a kontextu schématu do a z webové služby XML. Další informace najdete v tématu [dokumenty a data XML](../../../standard/data/xml/index.md).  
  
## <a name="see-also"></a>Viz také

- [Přehled ADO.NET](ado-net-overview.md)
