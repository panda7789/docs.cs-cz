---
title: DataTableReaders
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 1559cde9cb786ccb2baf920347064b8b28d472c3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785341"
---
# <a name="datatablereaders"></a>DataTableReaders
Zobrazí obsah <xref:System.Data.DataTable> nebo<xref:System.Data.DataSet> ve formě jedné nebo více sad výsledků pouze pro čtení, které jsou jen pro čtení. <xref:System.Data.DataTableReader>  
  
 Když vytvoříte **třídu DataTableReader** z **objektu DataTable**, výsledný objekt **DataTableReader** obsahuje jednu sadu výsledků se stejnými daty jako **objekt DataTable** , ze kterého byla vytvořena, s výjimkou řádků, které byly označeny jako odstraňování. Sloupce se zobrazí ve stejném pořadí jako v původním **objektu DataTable**.  
  
 **Třída DataTableReader** může obsahovat více sad výsledků, pokud byla vytvořena voláním <xref:System.Data.DataSet.CreateDataReader%2A>. Výsledky jsou ve stejném pořadí jako datové **tabulky** v <xref:System.Data.DataSet.Tables%2A> kolekci objektu **DataSet** .  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vytvoření čtečky dat](creating-a-datareader.md)  
 Popisuje, jak vytvořit objekt **DataTableReader** .  
  
 [Navigace v datových tabulkách](navigating-datatables.md)  
 Popisuje použití metody **Read** k přesunu obsahu pro **třídu DataTableReader**.  
  
## <a name="see-also"></a>Viz také:

- [Načítání a úpravy dat v ADO.NET](../retrieving-and-modifying-data.md)
- [Přehled ADO.NET](../ado-net-overview.md)
