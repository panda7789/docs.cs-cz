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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 70a83453eef990a03515a4860917f3c4d72599c3
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
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
