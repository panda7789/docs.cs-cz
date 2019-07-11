---
title: Podpora dědičnosti
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: 576fa896364d603f2cdbb7b6532e3efc3cd6f674
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743069"
---
# <a name="inheritance-support"></a>Podpora dědičnosti
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje *jedné tabulky mapování*. Jinými slovy hierarchie dědičnosti dokončete je uložena v tabulce izolované databáze. Tabulka obsahuje sloučené sjednocení všechny možné datové sloupce pro celou hierarchii. (Sjednocení je výsledkem kombinace dvou tabulek do jedné tabulky, který má řádky, které byly k dispozici v některém z původní tabulky.) Každý řádek obsahuje hodnoty Null do sloupců, které se nevztahují na typ instance reprezentována řádku.  
  
 Strategie jedné tabulky mapování je nejjednodušší reprezentace dědění a poskytuje dobré výkonové charakteristiky pro mnoho různých kategorií dotazů.  
  
 Pro toto mapování v implementaci [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], je nutné zadat atributy a atribut vlastnosti ve třídě kořenové hierarchii dědičnosti. Další informace najdete v tématu [jak: Mapování hierarchií dědičnosti](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).  
  
 Vývojářům používajícím Visual Studio můžete také použít Návrhář relací objektů pro mapování hierarchií dědičnosti.  
  
## <a name="see-also"></a>Viz také:

- [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
