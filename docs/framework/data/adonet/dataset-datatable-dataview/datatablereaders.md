---
title: DataTableReaders
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 1ff7868b59c6fdc4e6c443be1b831accc84f36a6
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203815"
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
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
