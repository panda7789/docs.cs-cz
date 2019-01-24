---
title: Nelze se připojit k původní instanci této aplikace s jedinou instancí
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
ms.openlocfilehash: 80c1ec0bf1aa4b6dbf885294c680b3bfe8897eac
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565706"
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a>Nelze se připojit k původní instanci této aplikace s jedinou instancí
Tato aplikace s jedinou instancí se nemohl připojit k původní instanci. Některé možné příčiny tohoto problému jsou následující:  
  
-   Původní instance přestala reagovat.  
  
-   Aplikace nemá oprávnění k vytváření objektů jádra. Další informace o objektech jádra najdete v tématu [mutexů](../../standard/threading/mutexes.md).  
  
     Základní název pro objekty jádra pochází z zřetězení identifikátor GUID, číslo hlavní verze a vedlejší číslo verze sestavení. Základní název může být například `3639f15d-9547-43da-8145-60da347829915.1`.  
  
## <a name="to-correct-this-error-when-developing-the-application"></a>Chcete-li opravit tuto chybu při vývoji aplikace  
  
1.  Zkontrolujte, jestli aplikace nepřešel do nereagujícího stavu.  
  
2.  Zkontrolujte, že aplikace má dostatečná oprávnění k vytváření objektů jádra.  
  
3.  Restartujte na původní instanci aplikace.  
  
4.  Restartujte počítač a zrušte všechny procesy, které může být na prostředek, který se nejde připojit k původní instanci aplikace.  
  
5.  Všimněte si okolnosti, kdy došlo k chybě a telefonní Microsoft Product Support Services.  
  
## <a name="see-also"></a>Viz také:
- [Základy ladicího programu](/visualstudio/debugger/debugger-basics)

