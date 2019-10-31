---
title: Tato aplikace s jedinou instancí se nemohla připojit k původní instanci.
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
ms.openlocfilehash: 04ceec4839d07ba959c39af8c4f582c7abfe7d6b
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198126"
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a>Tato aplikace s jedinou instancí se nemohla připojit k původní instanci.
Tato aplikace s jedinou instancí se nemohla připojit k původní instanci. Mezi možné příčiny tohoto problému patří následující:  
  
- Původní instance přestala reagovat.  
  
- Aplikace nemá oprávnění k vytváření objektů jádra. Další informace o objektech jádra najdete v tématu [mutexy](../../standard/threading/mutexes.md).  
  
     Základní název objektů jádra pochází z zřetězení identifikátoru GUID sestavení, hlavní číslo verze a číslo dílčí verze. Základní název může být například `3639f15d-9547-43da-8145-60da347829915.1`.  
  
## <a name="to-correct-this-error-when-developing-the-application"></a>Oprava této chyby při vývoji aplikace  
  
1. Ověřte, zda aplikace nepřejde do stavu nereagující.  
  
2. Ověřte, zda má aplikace dostatečná oprávnění k vytváření objektů jádra.  
  
3. Restartujte původní instanci aplikace.  
  
4. Restartujte počítač a zrušte tak všechny procesy, které mohou používat prostředek, který je požadován pro připojení k původní instanci aplikace.  
  
5. Poznamenejte si okolnosti, za kterých došlo k chybě, a telefonní služby na produkty společnosti Microsoft.  
  
## <a name="see-also"></a>Viz také:

- [Základy ladicího programu](/visualstudio/debugger/debugger-feature-tour)
