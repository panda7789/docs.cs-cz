---
title: Použitelnost funkční transformace (C#)
desciption: Learn about functional transformation. See how this approach to LINQ and other processes where the focus is on transforming data from one form to another.
ms.date: 07/20/2015
ms.assetid: c78107bd-b006-4574-a3d4-bbf808388ff3
ms.openlocfilehash: b507e0ad5c09478c3427f87d32a21d8facf1b7a0
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105569"
---
# <a name="applicability-of-functional-transformation-c"></a>Použitelnost funkční transformace (C#)
Čistě funkční transformace jsou použitelné v nejrůznějších situacích.  
  
 Přístup k funkční transformaci je ideální pro dotazování a manipulaci se strukturovanými daty; Proto je vhodný pro technologie LINQ. Nicméně transformace funkcí má mnohem širší použitelnost než použití s LINQ. Každý proces, ve kterém se hlavní fokus provádí transformaci dat z jednoho formuláře na jiný, by měl být považován za kandidáta na funkční transformaci.  
  
 Tento přístup se vztahuje na mnoho problémů, které se nemusí zobrazit na první pohled na kandidáta. Při použití ve spojení se službou LINQ nebo nezávisle na nich by se měla funkční transformace považovat za následující oblasti:  
  
- Dokumenty založené na jazyce XML. Dobře vytvořená data jakéhokoli dialektu XML lze snadno manipulovat prostřednictvím funkční transformace. Další informace naleznete v tématu [funkční transformace jazyka XML (C#)](./functional-transformation-of-xml.md).  
  
- Jiné strukturované formáty souborů. Z Windows.ini souborů do dokumentů prostého textu má většina souborů určitou strukturu, která se sama zapůjčuje k analýze a transformaci.  
  
- Protokoly streamování dat. Data kódování a dekódování dat z komunikačních protokolů je často možné znázornit pomocí jednoduché transformace funkcí.  
  
- Data RDBMS a OODBMS. Relační a objektově orientované databáze, stejně jako XML, jsou široce používané strukturované zdroje dat.  
  
- Matematickýchá, statistická a vědecká řešení. Tato pole mají za následek zpracování rozsáhlých datových sad a pomáhají tak uživatelům v vizualizacích, odhadech nebo ve skutečnosti řešit netriviální problémy.  
  
 Jak je popsáno v tématu [refaktoring na čistě Functions (C#)](./refactoring-into-pure-functions.md), je použití čistě funkcí příkladem funkčního programování. Kromě okamžitých výhod díky čistě funkcím nabízí funkce čistého prostředí v úvahách o problémech z hlediska funkční transformace. Tento přístup může mít také významný dopad na návrh aplikace a třídy. To platí hlavně v případě, že se problém týká řešení transformace dat, jak je popsáno výše.  
  
 I když jsou nad rámec tohoto kurzu, návrhy, které jsou ovlivněné perspektivou pro transformaci, jsou v tom, že jsou na zpracování více než objekty jako aktéri, a výsledné řešení je implementováno jako série velkých transformací, nikoli individuální stav objektu.  
  
 Znovu nezapomeňte, že jazyk C# podporuje imperativní i funkční přístupy, takže nejlepší návrh aplikace může zahrnovat prvky obou.  
  
## <a name="see-also"></a>Viz také

- [Úvod do čistě funkčních transformací (C#)](./introduction-to-pure-functional-transformations.md)
- [Funkční transformace XML (C#)](./functional-transformation-of-xml.md)
- [Refaktoring do čistě funkcí (C#)](./refactoring-into-pure-functions.md)
