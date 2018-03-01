---
title: "Nelze se připojit k původní instance této aplikace s jedinou instancí"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9cb8cef696ba93f922dfe0d92195a5fb5147b4cc
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a>Nelze se připojit k původní instance této aplikace s jedinou instancí
Tato aplikace s jedinou instancí se nemohl připojit k původní instance. Některé možné příčiny tohoto problému jsou následující:  
  
-   Na původní instanci přestala reagovat.  
  
-   Aplikace nemá oprávnění k vytváření objektů jádra. Další informace o objektech jádra najdete v tématu [mutex – třídy](../../standard/threading/mutexes.md).  
  
     Základní název pro objekty jádra pochází z zřetězení GUID je sestavení, hlavní číslo verze a číslo podverze. Například může být základní název `3639f15d-9547-43da-8145-60da347829915.1`.  
  
## <a name="to-correct-this-error-when-developing-the-application"></a>Chcete-li chybu při vývoji aplikace  
  
1.  Zkontrolujte, jestli aplikace nejde do stavu reagovat.  
  
2.  Zkontrolujte, že aplikace má dostatečná oprávnění k vytváření objektů jádra.  
  
3.  Restartujte původní instanci aplikace.  
  
4.  Restartujte počítač zrušte všechny procesy, které může být prostředek, který je požadován pro připojení k původní instance aplikace.  
  
5.  Poznámka: v případech, za kterých se stala chyba a telefonní služby Microsoft Product Support Services.  
  
## <a name="see-also"></a>Viz také  
 [Základy ladicího programu](/visualstudio/debugger/debugger-basics)  

