---
title: SQL-CLR Custom Type Mappings
ms.date: 03/30/2017
ms.assetid: d916c7fb-4b56-4214-acbe-5e23365047b2
ms.openlocfilehash: 36763be3cd4845fbbd027b448098d0dafb9e448a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622507"
---
# <a name="sql-clr-custom-type-mappings"></a>SQL-CLR Custom Type Mappings
Typ mapování mezi systému SQL Server a common language runtime (CLR) bylo automaticky zadáno při použití SQLMetal nástroj příkazového řádku, Návrhář relací objektů (O/R Designer).  
  
 Pokud žádné vlastní mapování se provádí, tyto nástroje přiřadit výchozí mapování typů jak je popsáno v [mapování typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md). Pokud chcete zadat mapování odlišně od tyto výchozí hodnoty, je potřeba některé přizpůsobení mapování typů.  
  
 Při přizpůsobování mapování typů, doporučuje provést změny v souboru DBML zprostředkující. Pak upravený soubor DBML by měl použít při vytváření kódu a souborů mapování SQLMetal nebo Návrháře relací objektů.  
  
 Jakmile vytvoříte instanci <xref:System.Data.Linq.DataContext> objekt z kódu a souborů mapování <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda vytvoří databázi podle mapování typů, které jsou uvedeny. Pokud neexistují žádné CLR `type` zadané atributy v mapování, použije se výchozí mapování typů.  
  
## <a name="customization-with-sqlmetal-or-or-designer"></a>Přizpůsobení s SQLMetal nebo Návrháře relací objektů  
 SQLMetal a O/R Designer můžete automaticky vytvořit objektový model, který obsahuje informace o mapování typu uvnitř nebo vně souboru kódu. Protože tyto soubory jsou přepsány SQLMetal nebo O/R Designer, pokaždé, když znovu vytvoříte mapování pracovního doporučený postup pro určení mapování vlastních typů je pro přizpůsobení souboru DBML.  
  
 Přizpůsobení mapování typů s SQLMetal nebo O/R Designer, nejprve generování souboru DBML. Před generováním kódu souboru nebo souboru mapování, upravte souboru DBML k identifikaci mapování požadovaného typu. S SQLMetal, budete muset ručně změnit `Type` a `DbType` atributy v souboru DBML, aby váš typ mapování přizpůsobení. Pomocí Návrháře relací objektů provedete změny v návrháři. Další informace o používání návrháře relací objektů naleznete v tématu [LINQ to SQL nástroje v sadě Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
> [!NOTE]
>  Některé mapování typu může vést ke ztrátě výjimky přetečení nebo dat při překladu do nebo z databáze. Pečlivě si prostudujte matice chování mapování typu za běhu v [mapování typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) před provedením jakékoli vlastní nastavení.  
  
 Aby vlastní typ mapování podle SQLMetal nebo O/R Designer budete muset Ujistěte se, že tyto nástroje jsou součástí cesty do vlastního souboru DBML při generování souboru kódu nebo externí mapování souboru. Ačkoli to není vyžadováno pro mapování typu vlastního nastavení, doporučujeme vám vždy oddělení vašich informací o mapování typ ze souboru s kódem a generovat soubor mapování další externí. Tím ponechá určitá flexibilita vyžadováním není třeba znovu zkompilovat soubor kódu.  
  
## <a name="incorporating-database-changes"></a>Zahrnutí změny databáze  
 Když změny databáze, je potřeba v souboru DBML odrážet provedené změny. Jeden ze způsobů, jak provést toto je pro automatické vytvoření nového souboru DBML a pak znovu proveďte vlastní typ mapování. Alternativně může porovnat rozdíly mezi nového souboru DBML a vaše přizpůsobené souboru DBML a aktualizace vašeho vlastního souboru DBML ručně tak, aby odrážely změny databáze.  
  
## <a name="see-also"></a>Viz také:
- [Mapování typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [Generování kódu v LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
