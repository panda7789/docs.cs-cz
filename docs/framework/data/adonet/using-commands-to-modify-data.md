---
title: Použití příkazů pro změny dat
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: f2e3d162bfbdcb79cfecefa4ddc8e6a0dc46ee3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61875950"
---
# <a name="using-commands-to-modify-data"></a>Použití příkazů pro změny dat
Pomocí zprostředkovatele dat .NET Framework, může spustit uložené procedury nebo příkazy data definition language (například CREATE TABLE a ALTER COLUMN), provádět manipulace s schématu databáze nebo katalogu. Tyto příkazy nevracejí řádky jako dotaz, takže **příkaz** objekt, který poskytuje **metodu ExecuteNonQuery** pro jejich zpracování.  
  
 Kromě použití **metodu ExecuteNonQuery** k úpravě schématu, můžete také použít tuto metodu za účelem procesu SQL příkazy, které mění data, ale který vracet řádky, jako jsou INSERT, UPDATE a odstranit.  
  
 I když nejsou řádků vrácených **metodu ExecuteNonQuery** metoda, vstupní a výstupní parametry a návratové hodnoty je možné předaný a vrácena prostřednictvím **parametry** kolekce **příkaz**  objektu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Aktualizace dat ve zdroji dat](../../../../docs/framework/data/adonet/updating-data-in-a-data-source.md)  
 Popisuje, jak spustit příkazy nebo uložené procedury, které mění data v databázi.  
  
 [Provádění operací katalogu](../../../../docs/framework/data/adonet/performing-catalog-operations.md)  
 Popisuje, jak spouštět příkazy, které upravují schéma databáze.  
  
## <a name="see-also"></a>Viz také:

- [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
