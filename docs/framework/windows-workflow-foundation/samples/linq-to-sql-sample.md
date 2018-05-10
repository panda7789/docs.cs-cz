---
title: Technologie LINQ to SQL ukázka
ms.date: 03/30/2017
ms.assetid: 5f39db9e-0e62-42c9-8c98-bb8b54cec98c
ms.openlocfilehash: 3cfcaf3de1a22b8bb5505083f127a9888b99dbd8
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="linq-to-sql-sample"></a>Technologie LINQ to SQL ukázka
Tento příklad znázorňuje postup vytvoření aktivity použití LINQ na entity dotazu SQL z tabulek v databáze systému SQL Server.  
  
> [!IMPORTANT]
>  Ukázky WCF mohou již být nainstalován na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\Samples\WCFWFCardspace`  
>   
>  Pokud tento adresář neexistuje, klikněte na odkaz ke stažení ukázkové v horní části této stránky. Všimněte si, že tento odkaz se stáhne a nainstaluje všechny [!INCLUDE[wf1](../../../../includes/wf1-md.md)], WCF, a [!INCLUDE[infocard](../../../../includes/infocard-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\Samples\WCFWFCardSpace\WF\Scenario\ActivityLibrary\Linq\LinqToSql`  
  
## <a name="activity-details-for-findinsqltable"></a>Podrobnosti o aktivitě pro FindInSqlTable  
 Tato aktivita umožňuje uživatelům dotaz entity z tabulek v databázi pomocí technologie LINQ to SQL. Uživatelé aktivity také zadat predikát LINQ ve formě výrazu lambda filtrování výsledků. Pokud je k dispozici žádné predikátu, je vrácena celou tabulku. V následující tabulce jsou hodnoty vlastností a vraťte se pro aktivitu.  
  
|Vlastnost nebo vrací hodnotu|Popis|  
|------------------------------|-----------------|  
|`Collection` Vlastnost|Povinnou vlastnost, která určuje zdrojové kolekci.|  
|`Predicate` Vlastnost|Povinnou vlastnost, která určuje filtr pro kolekce v podobě výrazu lambda.|  
|Návratová hodnota|Filtrované kolekce.|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a>Ukázka kódu, který používá vlastní aktivity  
 Následující příklad kódu používá `FindInSqlTable` vlastní aktivity najít všechny řádky v tabulce systému SQL Server s názvem `Employee` kde `Role` sloupec je rovno `SDE`.  
  
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
  
2.  Přejděte do složky, která obsahuje tato ukázka.  
  
3.  Spusťte soubor Setup.cmd příkaz.  
  
    > [!NOTE]
    >  Skript Setup.cmd pokusu o instalaci ukázkové databáze v místním počítači systému SQL Server Express. Pokud chcete nainstalujte ho do jiné instance systému SQL server, upravte Setup.cmd.  
  
     Setup.cmd skript provede následující akce.:  
  
    -   Vytvoří databázi názvem LinqToSqlSample.  
  
    -   Vytvoří tabulku role.  
  
    -   Vytvoří tabulku Zaměstnanci.  
  
    -   Vloží do tabulky role 3 záznamy.  
  
    -   Vloží do tabulky Zaměstnanci 12 záznamy.  
  
4.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení LinqToSQL.sln.  
  
5.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
6.  Pokud chcete spustit řešení, stisknutím klávesy F5.  
  
#### <a name="to-uninstall-the-linqtosql-sample-database"></a>Chcete-li odinstalovat LinqToSql ukázkové databáze  
  
1.  Otevřete příkazový řádek.  
  
2.  Přejděte do složky, která obsahuje tato ukázka.  
  
3.  Spusťte soubor Cleanup.cmd příkaz.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Liiinq\LinqToSql`  
  
## <a name="see-also"></a>Viz také  
 [LINQ to SQL](http://go.microsoft.com/fwlink/?LinkId=150376)  
 [Začínáme (technologie LINQ to SQL)](http://go.microsoft.com/fwlink/?LinkId=150377)
