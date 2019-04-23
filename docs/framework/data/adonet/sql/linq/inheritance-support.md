---
title: Podpora dědičnosti
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: 668f4f1dd284550e644ce6b8a4491ca47105575e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59230912"
---
# <a name="inheritance-support"></a>Podpora dědičnosti
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje *jedné tabulky mapování*. Jinými slovy hierarchie dědičnosti dokončete je uložena v tabulce izolované databáze. Tabulka obsahuje sloučené sjednocení všechny možné datové sloupce pro celou hierarchii. (Sjednocení je výsledkem kombinace dvou tabulek do jedné tabulky, který má řádky, které byly k dispozici v některém z původní tabulky.) Každý řádek obsahuje hodnoty Null do sloupců, které se nevztahují na typ instance reprezentována řádku.  
  
 Strategie jedné tabulky mapování je nejjednodušší reprezentace dědění a poskytuje dobré výkonové charakteristiky pro mnoho různých kategorií dotazů.  
  
 Pro toto mapování v implementaci [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], je nutné zadat atributy a atribut vlastnosti ve třídě kořenové hierarchii dědičnosti. Další informace najdete v tématu [jak: Mapování hierarchií dědičnosti](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).  
  
 Vývojáři, kteří používají Visual Studio můžete také použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] mapování hierarchií dědičnosti.  
  
## <a name="see-also"></a>Viz také:

- [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
