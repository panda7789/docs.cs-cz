---
title: Mapování vlastních typů SQL a CLR
ms.date: 03/30/2017
ms.assetid: d916c7fb-4b56-4214-acbe-5e23365047b2
ms.openlocfilehash: 8901998533ec14e733ea072dd1a69b465e596328
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781082"
---
# <a name="sql-clr-custom-type-mappings"></a>Mapování vlastních typů SQL a CLR
Mapování typů mezi SQL Server a modulem CLR (Common Language Runtime) je automaticky zadáno při použití nástroje příkazového řádku SQLMetal Návrhář relací objektů (O/R Designer).  
  
 Pokud není provedeno žádné přizpůsobené mapování, tyto nástroje přiřadí výchozí mapování typů, jak je popsáno v [mapování typu SQL-CLR](sql-clr-type-mapping.md). Pokud chcete zadat mapování odlišně od těchto výchozích hodnot, je nutné provést některé vlastní nastavení mapování typů.  
  
 Při přizpůsobování mapování typů je doporučeným přístupem udělat změny v souboru. DBML. Přizpůsobený soubor DBML by pak měl být použit při vytváření kódu a mapování souborů pomocí návrháře SQLMetal nebo O/R.  
  
 Po vytvoření instance <xref:System.Data.Linq.DataContext> objektu z kódu a mapování souborů <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Metoda vytvoří databázi na základě mapování typů, které jsou zadány. Pokud v mapování nejsou zadány žádné atributy CLR `type` , budou použity výchozí mapování typů.  
  
## <a name="customization-with-sqlmetal-or-or-designer"></a>Přizpůsobení pomocí SQLMetal nebo O/R návrháře  
 Pomocí SQLMetal a O/R designeru můžete automaticky vytvořit objektový model, který obsahuje informace o mapování typů uvnitř nebo vně souboru kódu. Vzhledem k tomu, že jsou tyto soubory přepsány návrhářem SQLMetal nebo O/R, pokaždé, když znovu vytvoříte mapování, doporučený postup pro určení vlastního mapování typů je přizpůsobení souboru DBML.  
  
 Chcete-li přizpůsobit mapování typů pomocí SQLMetal nebo O/R návrháře, nejprve vygenerujte soubor DBML. Před vygenerováním souboru kódu nebo mapováním souboru upravte soubor DBML tak, aby identifikoval požadovaná mapování typů. Pomocí SQLMetal je nutné ručně změnit `Type` atributy a `DbType` v souboru DBML, aby bylo možné přizpůsobit mapování typů. Pomocí jazyka O/R Designer můžete provádět změny v návrháři. Další informace o použití návrháře O/R naleznete v tématu [nástroje LINQ to SQL v aplikaci Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
> [!NOTE]
> Některé mapování typů může způsobit přetečení nebo výjimky ztráty dat při převodu do nebo z databáze. Před provedením jakýchkoli úprav pečlivě zkontrolujte matrici chování mapování typů v [mapování typu SQL-CLR](sql-clr-type-mapping.md) .  
  
 Aby bylo přizpůsobení mapování typů rozpoznáno návrhářem SQLMetal nebo O/R, je nutné zajistit, aby tyto nástroje byly dodány s cestou k vlastnímu souboru DBML při generování souboru kódu nebo externího souboru mapování. I když není vyžadováno pro přizpůsobení mapování typů, je doporučeno vždy oddělit informace mapování typů ze souboru kódu a vytvořit další soubor mapování externího typu. Tím dojde k větší flexibilitě tím, že nebudete muset znovu kompilovat soubor kódu.  
  
## <a name="incorporating-database-changes"></a>Zahrnutí změn databáze  
 Když se databáze změní, budete muset aktualizovat svůj soubor DBML, aby odrážel tyto změny. Jedním ze způsobů, jak to provést, je automaticky vytvořit nový soubor DBML a pak znovu provést vlastní nastavení mapování typů. Alternativně můžete porovnat rozdíly mezi novým souborem DBML a vlastním souborem DBML a ručně aktualizovat vlastní soubor DBML, aby odrážel změnu databáze.  
  
## <a name="see-also"></a>Viz také:

- [Mapování typů SQL a CLR](sql-clr-type-mapping.md)
- [Generování kódu v LINQ to SQL](code-generation-in-linq-to-sql.md)
