---
title: Použití příkazů pro změny dat
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: 34c73549f18cd4bebb8caf842b252828b7f0a185
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780563"
---
# <a name="using-commands-to-modify-data"></a>Použití příkazů pro změny dat
Pomocí poskytovatele .NET Framework dat můžete spustit uložené procedury nebo příkazy jazyka definice dat (například CREATE TABLE a ALTER COLUMN) a provádět tak manipulaci se schématem v databázi nebo katalogu. Tyto příkazy nevrací řádky jako dotaz, takže objekt **Command** poskytuje **ExecuteNonQuery** pro jejich zpracování.  
  
 Kromě použití **ExecuteNonQuery** ke změně schématu můžete také použít tuto metodu ke zpracování příkazů SQL, které mění data, ale nevrací řádky, jako je například vložení, aktualizace a odstranění.  
  
 I když řádky nejsou vraceny metodou **ExecuteNonQuery** , vstupní a výstupní parametry a návratové hodnoty mohou být předány a vráceny prostřednictvím kolekce **Parameters** objektu **příkazu** .  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Aktualizace dat ve zdroji dat](updating-data-in-a-data-source.md)  
 Popisuje, jak spustit příkazy nebo uložené procedury, které upravují data v databázi.  
  
 [Provádění operací katalogu](performing-catalog-operations.md)  
 Popisuje, jak provést příkazy, které mění schéma databáze.  
  
## <a name="see-also"></a>Viz také:

- [Načítání a úpravy dat v ADO.NET](retrieving-and-modifying-data.md)
- [Příkazy a parametry](commands-and-parameters.md)
- [Přehled ADO.NET](ado-net-overview.md)
