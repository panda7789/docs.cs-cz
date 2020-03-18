---
title: Použitelnost funkční transformace (C#)
ms.date: 07/20/2015
ms.assetid: c78107bd-b006-4574-a3d4-bbf808388ff3
ms.openlocfilehash: bc2678354bb45f1ed0a4076f278f52d0ee7d350e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69594882"
---
# <a name="applicability-of-functional-transformation-c"></a>Použitelnost funkční transformace (C#)
Čistě funkční transformace jsou použitelné v široké škále situací.  
  
 Přístup k funkční transformaci je ideální pro dotazování a manipulaci se strukturovanými daty; proto dobře zapadá do technologií LINQ. Funkční transformace má však mnohem širší použitelnost než použití s LINQ. Každý proces, kde je hlavní důraz na transformaci dat z jednoho formuláře do druhého, by měl být pravděpodobně považován za kandidáta na funkční transformaci.  
  
 Tento přístup je použitelný pro mnoho problémů, které se nemusí na první pohled jevit jako kandidát. Používá se ve spojení s LINQ nebo odděleně od LINQ, funkční transformace by měla být zvážena pro následující oblasti:  
  
- dokumenty založené na jazyce XML. Dobře tvarovaná data libovolného dialektu XML lze snadno manipulovat pomocí funkční transformace. Další informace naleznete v [tématu Funkční transformace xml (C#)](./functional-transformation-of-xml.md).  
  
- Jiné formáty strukturovaných souborů. Od souborů Windows.ini až po dokumenty ve formátu prostého textu má většina souborů určitou strukturu, která se hodí k analýze a transformaci.  
  
- Protokoly datových proudů. Kódování dat do komunikačních protokolů a dekódování dat z nich může být často reprezentováno jednoduchou funkční transformací.  
  
- RDBMS a OODBMS. Relační a objektově orientované databáze, stejně jako XML, jsou široce používané strukturované zdroje dat.  
  
- Matematická, statistická a vědecká řešení. Tato pole mají tendenci manipulovat s velkými datovými sadami, aby pomohla uživateli vizualizovat, odhadovat nebo skutečně řešit netriviální problémy.  
  
 Jak je popsáno v [Refactoring into Pure Functions (C#)](./refactoring-into-pure-functions.md), pomocí čisté funkce je příkladem funkční programování. Kromě jejich okamžité výhody, pomocí čisté funkce poskytuje cenné zkušenosti s přemýšlením o problémech z hlediska funkční transformace. Tento přístup může mít také významný vliv na návrh programu a třídy. To platí zejména v případě, že problém se hodí k řešení transformace dat, jak je popsáno výše.  
  
 Přestože jsou nad rámec tohoto kurzu, návrhy, které jsou ovlivněny perspektivou funkční transformace, mají tendenci soustředit se na procesy více než na objekty jako objekty a výsledné řešení má tendenci být implementováno jako řada rozsáhlých transformace, spíše než změny stavu jednotlivých objektů.  
  
 Znovu pamatujte, že C# podporuje imperativní a funkční přístupy, takže nejlepší návrh pro vaši aplikaci může obsahovat prvky obou.  
  
## <a name="see-also"></a>Viz také

- [Úvod do čistě funkčních transformací (C#)](./introduction-to-pure-functional-transformations.md)
- [Funkční transformace XML (C#)](./functional-transformation-of-xml.md)
- [Refaktoring do čistých funkcí (C#)](./refactoring-into-pure-functions.md)
