---
title: "Podpora dědičnosti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: c898d8448b39fc5da63e5eda2046d0747837509b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="inheritance-support"></a>Podpora dědičnosti
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]podporuje *mapování jedné tabulky*. Hierarchie dědičnosti dokončení je jinými slovy, uložené v tabulce jedné databáze. Tabulka obsahuje plochou sjednocení všechny možné datové sloupce pro celou hierarchii. (Spojení je výsledkem kombinace dvou tabulek do jedné tabulky, který má na řádky, které existovaly v některém z původní tabulky.) Každý řádek obsahuje hodnoty Null do sloupce, které se nevztahují na typ instance reprezentována řádek.  
  
 Strategie mapování jedné tabulky je nejjednodušší reprezentace dědičnosti a poskytuje charakteristiky dobrý výkon pro řadu různých kategorií dotazů.  
  
 K implementaci toto mapování v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], je nutné zadat atributy a vlastností atributu na kořenová třída hierarchie dědičnosti. Další informace najdete v tématu [postupy: mapování hierarchie dědičnosti](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).  
  
 Vývojáře, kteří používají [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] můžete použít také [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] k mapování hierarchie dědičnosti.  
  
## <a name="see-also"></a>Viz také  
 [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
