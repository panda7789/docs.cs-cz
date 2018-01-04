---
title: "Příkazy ke změně dat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 5c574a5e880dd838397b35df48138079cb58e2cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-commands-to-modify-data"></a>Příkazy ke změně dat
Pomocí zprostředkovatele dat .NET Framework, můžete spustit uložené procedury nebo příkazy data definition language (například CREATE TABLE a ALTER COLUMN) k provedení manipulaci schématu v databázi nebo katalogu. Tyto příkazy nevrátí řádky jako dotaz způsobem, proto **příkaz** objekt poskytuje **ExecuteNonQuery** pro jejich zpracování.  
  
 Kromě používání **ExecuteNonQuery** k úpravě schématu, můžete také použít tuto metodu za účelem proces příkazy SQL, který měnit data, ale které nejsou vrátí řádky, jako je například vložení, aktualizace a odstranit.  
  
 I když nejsou vrácených řádků **ExecuteNonQuery** metoda, vstupní a výstupní parametry a návratové hodnoty můžete být předán a vrácených prostřednictvím **parametry** kolekce **příkaz**  objektu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Aktualizace dat ve zdroji dat](../../../../docs/framework/data/adonet/updating-data-in-a-data-source.md)  
 Popisuje, jak spustit příkazy nebo uložené procedury, které upravují data v databázi.  
  
 [Provádění operací katalogu](../../../../docs/framework/data/adonet/performing-catalog-operations.md)  
 Popisuje, jak provést příkazy, které upravují schématu databáze.  
  
## <a name="see-also"></a>Viz také  
 [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
