---
title: Navigace v datových relacích
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
ms.openlocfilehash: 73523297454be37716acedad13498954ef9a89a0
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040351"
---
# <a name="navigating-datarelations"></a>Navigace v datových relacích
Jednou z primárních funkcí <xref:System.Data.DataRelation> je umožnění navigace z jednoho <xref:System.Data.DataTable> do druhé v rámci <xref:System.Data.DataSet>. To umožňuje načíst všechny související <xref:System.Data.DataRow> objekty v jednom **objektu DataTable** , pokud je předána jedna třída **DataRow** ze souvisejícího **objektu DataTable**. Například po vytvoření **datarelace** mezi tabulkou zákazníků a tabulkou objednávky můžete načíst všechny řádky objednávky pro konkrétní řádek zákazníka pomocí **Metoda GetChildRows**.  
  
 Následující příklad kódu vytvoří datovou **relaci** mezi tabulkou **Customers** a tabulkou **objednávky** **datové sady** a vrátí všechny objednávky pro každého zákazníka.  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 Následující příklad sestaví v předchozím příkladu se souvisejícími čtyřmi tabulkami a naviguje se na tyto vztahy. Jak je uvedeno v předchozím příkladu, pole **KódZákazníka** se týká tabulky **Customers** v tabulce **Orders** . Pro každého zákazníka v tabulce **Customers (zákazníci** ) se určí všechny podřízené řádky v tabulce **Orders** , aby bylo možné vrátit počet objednávek, které konkrétní zákazník má, a jejich hodnoty **ČísloObjednávky** .  
  
 Rozbalený příklad také vrátí hodnoty z tabulek **OrderDetails** a **Products** . Tabulka **Orders** se vztahuje k tabulce **OrderDetails** s využitím hodnoty **ČísloObjednávky** k určení, jaké produkty a množství byly objednány pro každé pořadí zákazníků. Protože tabulka **OrderDetails** obsahuje pouze **ProductID** objednaného produktu, **OrderDetails** se vztahuje k **produktům** , které používají **ProductID** za účelem vrácení **NázevVýrobku**. V této relaci je tabulka **Products** nadřazená a tabulka **Podrobnosti objednávky** je podřízená položka. Výsledkem je, že při iteraci v tabulce **OrderDetails** se volá **Metoda GetParentRow** , aby se načetla související hodnota **NázevVýrobku** .  
  
 Všimněte si, že při vytvoření **Datarelationu** pro tabulky **zákazníci** a **objednávky** není pro příznak **createConstraints** zadána žádná hodnota (výchozí hodnota je **true**). To předpokládá, že všechny řádky v tabulce **Orders** mají hodnotu **CustomerID** , která existuje v tabulce nadřazených **zákazníků** . Pokud existuje **KódZákazníka** v tabulce **Orders** , která v tabulce **Customers** neexistuje, <xref:System.Data.ForeignKeyConstraint> způsobí vyvolání výjimky.  
  
 Pokud podřízený sloupec může obsahovat hodnoty, které nadřazený sloupec neobsahuje, nastavte příznak **createConstraints** na **hodnotu false** při přidávání objektu **DataRelation**. V příkladu je příznak **createConstraints** nastaven na **hodnotu false** pro **DataRelation** mezi tabulkou **Orders** a tabulkou **OrderDetails** . To umožňuje aplikaci vracet všechny záznamy z tabulky **OrderDetails** a pouze podmnožinu záznamů z tabulky **Orders** , aniž by generovaly výjimku za běhu. Rozbalený vzorek generuje výstup v následujícím formátu.  
  
```output  
Customer ID: NORTS  
  Order ID: 10517  
        Order Date: 4/24/1997 12:00:00 AM  
           Product: Filo Mix  
          Quantity: 6  
           Product: Raclette Courdavault  
          Quantity: 4  
           Product: Outback Lager  
          Quantity: 6  
  Order ID: 11057  
        Order Date: 4/29/1998 12:00:00 AM  
           Product: Outback Lager  
          Quantity: 3  
```  
  
 Následující příklad kódu je rozbalený vzorek, ve kterém jsou vráceny hodnoty z tabulek **OrderDetails** a **Products** s vrácenou pouze podmnožinou záznamů v tabulce **Orders** .  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [Přehled ADO.NET](../ado-net-overview.md)
