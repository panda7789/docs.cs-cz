---
title: Ukázka LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 5f39db9e-0e62-42c9-8c98-bb8b54cec98c
ms.openlocfilehash: 83dc8433459f64860baaca2e8309fbc85e2bb3a2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515365"
---
# <a name="linq-to-sql-sample"></a>Ukázka LINQ to SQL
Tento příklad ukazuje, jak vytvořit aktivitu použití LINQ na SQL dotazu entity z tabulky v databázích systému SQL Server.  
  
> [!IMPORTANT]
>  Ukázky WCF může již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\Samples\WCFWFCardspace`  
>   
>  Pokud tento adresář neexistuje, klikněte na odkaz ke stažení vzorku v horní části této stránky. Všimněte si, že tento odkaz stáhne a nainstaluje všechny komponenty nástroje [!INCLUDE[wf1](../../../../includes/wf1-md.md)], WCF, a [!INCLUDE[infocard](../../../../includes/infocard-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\Samples\WCFWFCardSpace\WF\Scenario\ActivityLibrary\Linq\LinqToSql`  
  
## <a name="activity-details-for-findinsqltable"></a>Podrobnosti o aktivitě pro FindInSqlTable  
 Tato aktivita umožňuje uživatelům na dotazu entity z tabulky v databázi pomocí LINQ to SQL. Aktivity uživatelů můžete také zadat predikát LINQ ve formě lambda výraz k filtrování výsledků. Pokud je k dispozici žádné predikátu, je vrácena celá tabulka. Následující tabulka uvádí vlastnosti a návratové hodnoty pro aktivitu.  
  
|Vlastnost nebo návratová hodnota|Popis|  
|------------------------------|-----------------|  
|`Collection` Vlastnost|Požadovaná vlastnost, která určuje zdrojovou kolekci.|  
|`Predicate` Vlastnost|Požadovaná vlastnost, která určuje filtr pro kolekce v podobě výrazu lambda.|  
|Návratová hodnota|Filtrované kolekce.|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a>Vzorový kód, který používá vlastní aktivity  
 Následující příklad kódu používá `FindInSqlTable` vlastní aktivity se najít všechny řádky v tabulce SQL serveru s názvem `Employee` kde `Role` sloupce je rovna `SDE`.  
  
```csharp  
new FindInSqlTable<Employee>   
{  
    ConnectionString = @"Data Source=.\SQLExpress;Initial Catalog=LinqToSqlSample;Integrated Security=True",                          
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(emp => emp.Role.Equals("SDE"))),  
    Result = new OutArgument<IList<Employee>>(employees)  
},  
```  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete příkazový řádek.  
  
2.  Přejděte do složky obsahující tuto ukázku.  
  
3.  Spuštění souboru příkazů Setup.cmd.  
  
    > [!NOTE]
    >  Skriptu Setup.cmd pokusu o instalaci ukázkové databáze v místním počítači systému SQL Server Express. Pokud chcete nainstalovat v jiné instance systému SQL server, upravte Setup.cmd.  
  
     Provádí následující akce skriptu Setup.cmd.:  
  
    -   Vytvoří databázi s názvem LinqToSqlSample.  
  
    -   Vytvoří tabulku role.  
  
    -   Vytvoří tabulku Zaměstnanci.  
  
    -   Vloží do tabulky. role 3 záznamy.  
  
    -   Vloží do tabulky Employees 12 záznamy.  
  
4.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení LinqToSQL.sln.  
  
5.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
6.  Abyste mohli spustit řešení, stiskněte klávesu F5.  
  
#### <a name="to-uninstall-the-linqtosql-sample-database"></a>Chcete-li odinstalovat LinqToSql ukázkové databáze  
  
1.  Otevřete příkazový řádek.  
  
2.  Přejděte do složky obsahující tuto ukázku.  
  
3.  Spusťte soubor Cleanup.cmd příkazu.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Liiinq\LinqToSql`  
  
## <a name="see-also"></a>Viz také  
 [LINQ to SQL](https://go.microsoft.com/fwlink/?LinkId=150376)  
 [Začínáme (LINQ to SQL)](https://go.microsoft.com/fwlink/?LinkId=150377)
