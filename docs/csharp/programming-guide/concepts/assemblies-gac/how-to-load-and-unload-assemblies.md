---
title: 'Postupy: zavedení a uvolnění sestavení (C#)'
ms.date: 07/20/2015
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: 2934ff07026d520f52309e50eb7da24731608292
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43786582"
---
# <a name="how-to-load-and-unload-assemblies-c"></a>Postupy: zavedení a uvolnění sestavení (C#)
Sestavení odkazuje váš program bude automaticky načtených v okamžiku sestavení, ale je také možné načíst konkrétní sestavení do aktuální domény aplikace za běhu. Další informace najdete v tématu [postupy: načtení sestavení do domény aplikace](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
 Neexistuje žádný způsob, jak uvolnit jednotlivá sestavení bez uvolnění všech aplikačních domén, které je obsahují. I v případě, sestavení dostane mimo rozsah, zůstane soubor skutečné sestavení načteno, dokud jsou uvolněna, všechny aplikační domény, které obsahují.  
  
 Pokud chcete uvolnit, některá sestavení, ale ne pro jiné, zvažte vytvoření nové aplikační doméně, spouštění kódu v této doméně a pak uvolnění této domény aplikace. Další informace najdete v tématu [postupy: uvolnění domény aplikace](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>Načtení sestavení do domény aplikace  
  
1.  Použijte jednu z několik načíst metody obsažené v třídách <xref:System.AppDomain> a <xref:System.Reflection>. Další informace najdete v tématu [postupy: načtení sestavení do domény aplikace](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
### <a name="to-unload-an-application-domain"></a>K uvolnění domény aplikace  
  
1.  Neexistuje žádný způsob, jak uvolnit jednotlivá sestavení bez uvolnění všech aplikačních domén, které je obsahují. Použití `Unload` metodu z <xref:System.AppDomain> uvolnění domény aplikace. Další informace najdete v tématu [postupy: uvolnění domény aplikace](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../../csharp/programming-guide/index.md)  
- [Sestavení a globální mezipaměti sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
- [Postupy: Načtení sestavení do domény aplikace](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
