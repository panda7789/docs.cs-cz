---
title: Podpora dědičnosti
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: 791cc68ce89ad8e56b8feeebe6bf84434c3e89c6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692675"
---
# <a name="inheritance-support"></a>Podpora dědičnosti
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje *jedné tabulky mapování*. Jinými slovy hierarchie dědičnosti dokončete je uložena v tabulce izolované databáze. Tabulka obsahuje sloučené sjednocení všechny možné datové sloupce pro celou hierarchii. (Sjednocení je výsledkem kombinace dvou tabulek do jedné tabulky, který má řádky, které byly k dispozici v některém z původní tabulky.) Každý řádek obsahuje hodnoty Null do sloupců, které se nevztahují na typ instance reprezentována řádku.  
  
 Strategie jedné tabulky mapování je nejjednodušší reprezentace dědění a poskytuje dobré výkonové charakteristiky pro mnoho různých kategorií dotazů.  
  
 Pro toto mapování v implementaci [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], je nutné zadat atributy a atribut vlastnosti ve třídě kořenové hierarchii dědičnosti. Další informace najdete v tématu [jak: Mapování hierarchií dědičnosti](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).  
  
 Vývojáři, kteří používají Visual Studio můžete také použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] mapování hierarchií dědičnosti.  
  
## <a name="see-also"></a>Viz také:
- [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
