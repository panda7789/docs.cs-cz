---
title: Mapování vlastních typů SQL CLR
ms.date: 03/30/2017
ms.assetid: d916c7fb-4b56-4214-acbe-5e23365047b2
ms.openlocfilehash: ebbbaf4b90c289d4230bada210d3031a87ac4f36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359660"
---
# <a name="sql-clr-custom-type-mappings"></a>Mapování vlastních typů SQL CLR
Typ mapování mezi systému SQL Server a modul CLR (CLR) je zadána automaticky, pokud použijete na SQLMetal nástroj příkazového řádku, Návrhář relací objektů (Návrhář relací objektů).  
  
 Pokud žádné vlastní mapování provádí, tyto nástroje přiřadit výchozí mapování typů jak je popsáno v [mapování typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md). Pokud chcete zadat mapování jinak než tato výchozí nastavení, musíte udělat některé přizpůsobení mapování typů.  
  
 Při přizpůsobování mapování typů, provést změny v souboru DBML zprostředkující je doporučený postup. Upravený soubor DBML by pak použije při vytváření můžete kód a mapování souborů s SQLMetal nebo Návrhář relací objektů.  
  
 Jakmile instanci můžete vytvořit <xref:System.Data.Linq.DataContext> objekt z kódu a mapování souborů <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda vytvoří databázi na základě mapování typu, které jsou určené. Pokud neexistují žádné CLR `type` zadat atributy mapování, použije se výchozí typ mapování.  
  
## <a name="customization-with-sqlmetal-or-or-designer"></a>Přizpůsobení s SQLMetal nebo Návrhář relací objektů  
 SQLMetal a Návrhář relací objektů můžete automaticky vytvořit objektový model, který obsahuje informace o mapování typu uvnitř nebo vně souboru kódu. Protože tyto soubory jsou přepsány na SQLMetal nebo Návrhář relací objektů, pokaždé, když je znovu vytvořit mapování, doporučeným přístupem k určení vlastního typu mapování je k přizpůsobení souboru DBML.  
  
 Chcete-li přizpůsobit mapování typů s SQLMetal nebo Návrhář relací objektů, nejprve vygenerujte souboru DBML. Před generováním kód soubor nebo soubor mapování, upravte souboru DBML k identifikaci požadovaný typ mapování. S SQLMetal, budete muset ručně změnit `Type` a `DbType` atributy v souboru DBML mapování úpravy provádět vašeho typu. S Návrhář relací objektů můžete provést změny v návrháři. Další informace o používání Návrhář relací objektů najdete v tématu [technologie LINQ to SQL nástroje v sadě Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
> [!NOTE]
>  Některé mapování typů může vést k přetečení nebo data ztrátě výjimky při převodu do nebo z databáze. Pečlivě podívat se na matici chování mapování typu Run-time v [mapování typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) před provedením jakékoli úpravy.  
  
 Aby pro vlastní typ mapování rozpoznala SQLMetal nebo Návrhář relací objektů je nutné zajistit, že tyto nástroje se dodává s cesta k souboru vlastní DBML při generování kódu soubor nebo soubor externí mapování. Ačkoli to není požadováno pro typ mapování přizpůsobení, doporučujeme, abyste vždycky nezávislá souboru kódu na vaše informace o mapování typu a generovat soubor mapování další externí typ. Díky tomu ponechá určitou volnost tím, že nevyžaduje zopakovat souboru kódu.  
  
## <a name="incorporating-database-changes"></a>Zařadit změny v databázi  
 Pokud vaše změny v databázi, musíte aktualizovat soubor DBML tak, aby odrážela tyto změny. Jeden ze způsobů, jak provést toto je automaticky vytvořit nový soubor DBML a pak znovu proveďte vlastní nastavení mapování typu. Alternativně můžete porovnat rozdíly mezi nového souboru DBML a upravený soubor DBML a aktualizace vašeho vlastního souboru DBML ručně, aby odrážely změny databáze.  
  
## <a name="see-also"></a>Viz také  
 [Mapování typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [Generování kódu v LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
