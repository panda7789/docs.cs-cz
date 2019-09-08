---
title: Podpora dědičnosti
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: 034aa6e75ca304d98aa4d3e1f3023c1a6940b73c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781564"
---
# <a name="inheritance-support"></a>Podpora dědičnosti
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]podporuje *mapování s jednou tabulkou*. Jinými slovy, úplná Hierarchie dědičnosti je uložena v jedné tabulce databáze. Tabulka obsahuje shrnuté sjednocení všech možných sloupců dat pro celou hierarchii. (Sjednocení je výsledkem kombinování dvou tabulek do jedné tabulky, která obsahuje řádky, které byly přítomny v některé z původních tabulek.) Každý řádek má hodnoty null ve sloupcích, které neplatí pro typ instance reprezentované řádkem.  
  
 Strategie mapování s jednou tabulkou je nejjednodušší reprezentace dědičnosti a poskytuje dobré výkonnostní charakteristiky pro mnoho různých kategorií dotazů.  
  
 Chcete-li implementovat toto [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]mapování v nástroji, je nutné zadat atributy a vlastnosti atributu pro kořenovou třídu Hierarchie dědičnosti. Další informace najdete v tématu [jak: Mapování hierarchií](how-to-map-inheritance-hierarchies.md)dědičnosti.  
  
 Vývojáři, kteří používají Visual Studio, mohou také použít Návrhář relací objektů k mapování hierarchií dědičnosti.  
  
## <a name="see-also"></a>Viz také:

- [Základní informace](background-information.md)
